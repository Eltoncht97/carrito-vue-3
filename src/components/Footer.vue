<template>
  <th scope="row" colspan="2">Total productos</th>
    <td>{{totalCantidad}}</td>
    <td>
        <button class="btn btn-danger btn-sm" id="vaciar-carrito" @click="resetCarrito">
            vaciar todo
        </button>
    </td>
    <td class="font-weight-bold">$ <span>{{totalPrecio}}</span></td>
</template>

<script>
import { computed } from '@vue/reactivity'
import { useStore } from 'vuex'
export default {
  setup(){
    const store = useStore()
    const totalCantidad = computed(() => store.getters.totalCantidad)
    const totalPrecio = computed(() => store.getters.totalPrecio)
    const resetCarrito = () => {store.commit('resetCarrito')}

    return {
      totalCantidad,
      totalPrecio,
      resetCarrito
    }
  }
}
</script>

<style>

</style>