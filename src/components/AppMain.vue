<script>
import { store } from '../store';
import { Icon } from '@iconify/vue'

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
      <img :src="`https://image.tmdb.org/t/p/${store.w500}${result.poster_path}`" v-if="result.poster_path !== null" >
      <img src="/no_poster.jpg" v-if="result.poster_path == null" class="no_poster">
      <p>titolo: {{result.title}}</p>
      <p>titolo originale: {{result.original_title}}</p>  
      <p>{{result.original_language}}</p>
      <span v-if="result.original_language !== 'en' && result.original_language !== 'ja' && result.original_language !== 'ko' && result.original_language !== 'hi' && result.original_language !== 'te'">
        <Icon :icon="`flagpack:${result.original_language}`"/>
      </span>
      <span v-if="result.original_language == 'en'"><Icon icon="flagpack:gb-ukm"/></span>
      <span v-if="result.original_language == 'ja'"><Icon icon="flagpack:jp"/></span>
      <span v-if="result.original_language == 'ko'"><Icon icon="flagpack:kr"/></span>
      <span v-if="result.original_language == 'hi' || result.original_language == 'te'"><Icon icon="flagpack:in"/></span>
      <p>voto: 
        <font-awesome-icon :icon="['fas', 'star']" v-for="n in Math.floor(result.vote_average /2)" style="color:#FFDF00;" />
        <font-awesome-icon :icon="['far', 'star']" v-for="n in (5-(Math.floor(result.vote_average /2)))" />
      </p>
    </div>
  </div>
</template>
<style lang="scss" scoped>
  .no_poster{
    width: 500px;
}
</style>