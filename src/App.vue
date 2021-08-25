<template>
  <div class="container">
    <h1>Carrito</h1>
    <hr>
    <div class="row">
      <Card 
        v-for="producto of productos" :key="producto.id"
        :producto="producto"
      />
    </div>
    <Carrito />
  </div>
</template>

<script>
import { useStore } from 'vuex'
import { computed, onMounted } from '@vue/runtime-core'
import Card from './components/Card.vue'
import Carrito from './components/Carrito.vue'

export default {
  name: 'App',
  components: {
    Card,
    Carrito
  },
  setup() {
    const store = useStore()
    onMounted(() => {
      store.dispatch('fetchData')
    })
    const productos = computed(() => store.state.productos)

    return {
      productos
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
