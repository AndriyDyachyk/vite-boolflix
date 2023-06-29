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
  },
  /*
  methods:{
    mouseOver: function(){
      const element=document.querySelector('.card_content');
      element.classList.toggle('display_none');
      element.classList.toggle('display_inline_flex');
    }
  }*/
}
</script>
<template lang="">
  <main>
    <div class="card" v-for="result in store.results" :key="result.id">
      <img :src="`https://image.tmdb.org/t/p/${store.w342}${result.poster_path}`" v-if="result.poster_path !== null" v-on:mouseover="mouseOver" v-on:mouseleave="mouseOver">
      <img src="/no_poster.jpg" v-if="result.poster_path == null" class="no_poster" @mouseover="mouseOver" >
      <div class="card_content display">
        <div class="content">
          <p>Titolo:<br><strong>{{result.title}}</strong></p>
          <p>Titolo originale:<br>{{result.original_title}}</p>  
          <!-- bandiera lingua -->
          <span v-if="result.original_language !== 'en' && result.original_language !== 'ja' && result.original_language !== 'ko' && result.original_language !== 'hi' && result.original_language !== 'te'">
            <Icon :icon="`flagpack:${result.original_language}`"/>
          </span>
          <span v-if="result.original_language == 'en'"><Icon icon="flagpack:gb-ukm"/></span>
          <span v-if="result.original_language == 'ja'"><Icon icon="flagpack:jp"/></span>
          <span v-if="result.original_language == 'ko'"><Icon icon="flagpack:kr"/></span>
          <span v-if="result.original_language == 'hi' || result.original_language == 'te'"><Icon icon="flagpack:in"/></span>
          <!-- fine bandiera lingua -->
          <p>Voto: 
            <font-awesome-icon :icon="['fas', 'star']" v-for="n in Math.floor(result.vote_average /2)" style="color:#FFDF00;" />
            <font-awesome-icon :icon="['far', 'star']" v-for="n in (5-(Math.floor(result.vote_average /2)))" />
          </p>
          <p v-if="result.overview !== '' " class="descrizione"><strong>Overview: </strong>{{result.overview}}</p>
        </div>
      </div>
    </div>
  </main>
</template>
<style lang="scss" scoped>
 main{
    margin: 50px auto 0px;
    padding: 30px;
    background-color: #141414;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .no_poster{
    width: 342px;
}
  .card{
    width: 342px;
    height: 500px;
    overflow-y:hidden;
    position: relative;
    margin-bottom: 20px;
  }
  .card_content{
    position: absolute;
    width: 100%;
    bottom: 0px;
    right: 0px;
  }
  .content{
    position: relative;
    width: 100%;
    bottom: 0px;
    right: 0px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-end;
    color: white;
    text-align: center;
    padding: 10px;
    background: rgb(255,255,255);
    background: -moz-linear-gradient(180deg, rgba(255,255,255,0) 9%, rgba(0,0,0,1) 87%);
    background: -webkit-linear-gradient(180deg, rgba(255,255,255,0) 9%, rgba(0,0,0,1) 87%);
    background: linear-gradient(180deg, rgba(255,255,255,0) 9%, rgba(0,0,0,1) 87%);
  }
  p strong{
    font-size: 20px;
  }

  .content p:last-of-type{
    font-size: 14px;
  }

  .display{
    display: none;
  }
  .card:hover img{
    opacity: 0.3;
  }
  .card:hover .display{
    display: block;
  }
  .descrizione{
    text-align: left;
    max-height: 200px;
    overflow-y: scroll;
    -ms-overflow-style: none;  /* IE e Edge */
    scrollbar-width: none;  /* Firefox */
  }
  .descrizione::-webkit-scrollbar {
  display: none; /*Chrome, Safari e Opera */
}
</style>