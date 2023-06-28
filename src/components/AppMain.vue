<script>
import { store } from '../store';
import { Icon } from '@iconify/vue';

export default {
  components:{
    Icon
  },
  data(){
    return{
      store,
    }
  }
}
</script>
<template lang="">
  <div>
    <div v-for="result in store.results" :key="result.id">
      <img :src="`https://image.tmdb.org/t/p/w500${result.poster_path}`" >
      <p>titolo: {{result.title}}</p>
      <p>titolo originale: {{result.original_title}}</p>  
      <Icon :icon="`flagpack:${result.original_language}`" />
      <p>voto: {{result.vote_average}}</p>
    </div>
  </div>
</template>
<style lang="">
  
</style>