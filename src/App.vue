<script>
import productos from "./json/items-tv.json";
import productos2 from "./json/items-movil.json";
import productos3 from "./json/items-pc.json";
import Producto from "./components/Producto.vue";
import Carrito from "./components/Carrito.vue";
import './js/accordion.js';

export default {
  name: "App",
  components: {
    Producto,
    Carrito,
  },
  data() {
    return {
      productos,
      productos2,
      productos3,
      carrito: [],
    };
  },
  methods: {
    agregarCarro(producto) {
      this.carrito.push(producto);
    },
    estaEnCarrito(producto) {
      const item = this.carrito.find((item) => item.id === producto.id);
      if (item) {
        return true;
      } else {
        return false;
      }
    },
    removerProducto(producto) {
      this.carrito = this.carrito.filter(item => item.id != producto.id);
    },
    pagar() {
      this.carrito = [],
          alert("Gracias por su compra, pronto recibirá su pedido");
    },
    vaciarCarro() {
      alert("Carro vacío"),
      window.location.replace('');
    }
  }
};
</script>

<template>
  <div id="app">
    <nav className="navbar navbar-dark bg-dark">
    </nav>
    <div class="container">
      <h1 class="text-center">Mi tienda con Vue</h1>
      <hr>
    </div>
    <div class="block-store">
      <h1 class="text-center">Productos</h1>
      <hr>
      <section class="store">
        <div class="container">
          <div class="items">
            <div id="container-main">
              <div class="accordion-container">
                <a href="#" class="accordion-titulo">TV, vídeo y home cinema<span
                    class="toggle-icon"></span></a>
                <div class="accordion-content">
                  <div class="items1">
                    <div class='row'>
                      <div class="col-12 col-md-6" v-for="i in productos" :key="i.id">
                        <producto
                            :producto="i"
                            v-on:agregar-carro="agregarCarro"
                            :estaEnCarrito="estaEnCarrito(i)"
                        />
                      </div>
                    </div>
                  </div>
                </div>
              </div>


              <div class="accordion-container">
                <a href="#" class="accordion-titulo">Telefonía<span
                    class="toggle-icon"></span></a>
                <div class="accordion-content">
                  <div class="items1">
                    <div class='row'>
                      <div class="col-12 col-md-6" v-for="i in productos2" :key="i.id">
                        <producto
                            :producto="i"
                            v-on:agregar-carro="agregarCarro"
                            :estaEnCarrito="estaEnCarrito(i)"
                        />
                      </div>
                    </div>
                  </div>
                </div>
              </div>


              <div class="accordion-container">
                <a href="#" class="accordion-titulo">Informática<span
                    class="toggle-icon"></span></a>
                <div class="accordion-content">
                  <div class="items1">
                    <div class='row'>
                      <div class="col-12 col-md-6" v-for="i in productos3" :key="i.id">
                        <producto
                            :producto="i"
                            v-on:agregar-carro="agregarCarro"
                            :estaEnCarrito="estaEnCarrito(i)"
                        />
                      </div>
                    </div>
                  </div>
                </div>
              </div>


            </div>
          </div>
        </div>
      </section>
    </div>
    <div className="block-section">
      <h1 className="text-center">CARRITO</h1>
      <hr>
      <section className="shopping-cart">
        <div className="container">
          <div class="row">
            <div class="col-6">
              <carrito :items="carrito" v-on:remover-item="removerProducto" v-on:pagar="pagar" v-on:vaciarCarro="vaciarCarro"/>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<style>
@import './assets/style.css';
</style>
