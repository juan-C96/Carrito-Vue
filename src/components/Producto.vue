<script>
export default {
  name: 'Producto',
  props: ['producto', 'estaEnCarrito'],
  methods: {
    agregarCarro(producto) {
      if (producto.stock != 0) {
        this.$emit('agregar-carro', producto);
        producto.stock = producto.stock - 1;
      } else {
        alert("No hay productos disponibles");
      }
    }
  }
}
</script>

<template>
  <div class="producto-p">
    <div class="item shadow mb-4">
      <img :src="producto.imagen" class="item-image">
      <div>
        <h5 class="item-title">{{ producto.titulo }}</h5>
        <p class="item-codigo">Código: {{ producto.codigo }}</p>
      </div>
      <div class="item-details">
        <p class="description-p"><b>Descripción: </b>{{ producto.descripcion }}</p>
        <p>Stock:
        <p class="item-stock" id="text1">{{ producto.stock }}</p>
      </div>
      <div class="item-details">
        <h4 class="item-price">{{ Number(producto.precio) }} €</h4>
        <button @click="agregarCarro(producto)" class="btn btn-primary form-control">
          {{ estaEnCarrito ? 'Añadido' : 'Añadir al Carrito' }}
        </button>
      </div>
    </div>
  </div>
</template>

<style>
@import '../assets/style.css';
</style>