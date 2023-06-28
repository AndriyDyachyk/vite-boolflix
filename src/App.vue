<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js'
import axios from 'axios'
export default {
  components:{
    AppHeader,
    AppMain
  },
  data(){
    return{
      store
    }
  },
  mounted(){

  }
}
</script>
<template lang="">
  <div>
    <AppHeader/>
    <AppMain/>
  </div>
</template>
<style lang="scss">
  
</style>