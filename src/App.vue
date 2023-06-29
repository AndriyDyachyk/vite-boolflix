<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js'
import axios from 'axios'
import general from './style/general.scss'
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
  <AppHeader/>
  <AppMain/>
</template>
<style lang="scss">
  
</style>