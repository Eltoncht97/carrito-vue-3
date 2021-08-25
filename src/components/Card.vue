<template>
  <div class="col-12 col-sm-4 col-md-3 col-lg-2 mb-3 mt-3">
    <div class="card">
      <img :src="producto.thumbnailUrl" :alt="producto.title" class="card-img-top" />
      <div class="card-body">
        <h5>{{producto.title}}</h5>
        <p>$ <span>{{producto.precio}}</span></p>
        <button class="btn btn-dark" @click="agregar(producto)">Comprar</button>
      </div>
    </div>
  </div>
</template>

<script>
import {useStore} from 'vuex'
export default {
  props: ['producto'],
  setup(){
    const store = useStore()
    const agregar = producto => {
      store.dispatch('agregarAlCarro', producto)
    }

    return {
      agregar
    }
  }
};
</script>

<style>
</style>