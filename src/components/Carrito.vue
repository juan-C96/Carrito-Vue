<script>
export default {
  name: 'Carrito',
  props: ['items'],
  computed: {
    total() {
      return this.items.reduce((acumulador, item) => acumulador + Number(item.precio), 0);
    }
  },
  methods: {
    removerItem(item) {
      this.$emit('remover-item', item);
    }
  }
}

</script>

<template>
  <div class="col-10 col-md-2">
    <table class="table">
      <thead>
      <tr>
        <th>Producto</th>
        <th>Precio</th>
      </tr>
      </thead>
      <tbody v-for="item in items" :key="item.id">
      <tr key={i}>
        <td>{{ item.titulo }}</td>
        <td>Precio: {{ item.precio }} €</td>
        <td>
          <button class="btn badge badge-danger float-right" @click="removerItem(item)">X</button>
        </td>
      </tr>
      </tbody>
      <tfoot>
      <br>
      <tr>
        <td>
          <div class="a">
            <h6>Total: {{ total }} €</h6></div>
        </td>
        <td>
          <button :disabled="items.length === 0" @click="$emit('vaciarCarro')" class="btn btn-danger form-control">Vaciar
          </button>
        </td>
        <td>
          <button :disabled="items.length === 0" @click="$emit('pagar')" class="btn btn-success form-control">Comprar
          </button>
        </td>
      </tr>
      </tfoot>
    </table>
  </div>


</template>


