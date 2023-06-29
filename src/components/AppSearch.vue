<script>
import axios from 'axios'
import { store } from '../store';
export default {
 name: 'search',
 data () {
 return {
  query: '',
  activeSearch: 'false',
}
 },
 mounted() {
    this.getHome()
 }, 

 methods: {
  getResult(query) {
    if(query !== '' ){
    const optionMovies = {
    method: 'GET',
    url: `https://api.themoviedb.org/3/search/movie?query=${query}&language=it-IT&page=1`,
        headers: {
            accept: 'application/json',
            Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIyZWFhNDE4NDM1ZjRmMDkyMWM0Yzc5ZmEzOGFkODQ5MSIsInN1YiI6IjY0OWE5YTFmYTZkZGNiMDBjNjllYjI0YyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.U3IDVk8qcXcPPzYt7cq-3iNNcQxMukQJsEMvM7n-8fA'
        }
    };
    const optionTv = {
    method: 'GET',
    url: `https://api.themoviedb.org/3/search/movie?query=${query}&language=it-IT&page=1`,
        headers: {
            accept: 'application/json',
            Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIyZWFhNDE4NDM1ZjRmMDkyMWM0Yzc5ZmEzOGFkODQ5MSIsInN1YiI6IjY0OWE5YTFmYTZkZGNiMDBjNjllYjI0YyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.U3IDVk8qcXcPPzYt7cq-3iNNcQxMukQJsEMvM7n-8fA'
        }
    };
    axios.all([axios.request(optionMovies),axios.request(optionTv)]).then(axios.spread((movieResponse, tvResponse) => { store.results = (movieResponse.data.results, tvResponse.data.results)}))
     console.log(store.results);
    }else{
        this.getHome()
    }
  },
  getHome(){
    const optionPopular = {
    method: 'GET',
    url: `https://api.themoviedb.org/3/discover/movie?include_adult=false&include_video=false&language=it-IT&page=1&sort_by=popularity.desc`,
        headers: {
            accept: 'application/json',
            Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIyZWFhNDE4NDM1ZjRmMDkyMWM0Yzc5ZmEzOGFkODQ5MSIsInN1YiI6IjY0OWE5YTFmYTZkZGNiMDBjNjllYjI0YyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.U3IDVk8qcXcPPzYt7cq-3iNNcQxMukQJsEMvM7n-8fA'
        }
    };
    axios.request(optionPopular).then(popularResponse => { store.results = popularResponse.data.results})
     console.log(store.results);
     
  },
  transform(){
    if(this.activeSearch== 'false'){
      document.getElementById("search_bar").classList.toggle('transform');
      document.getElementById("search_bar").classList.toggle('transform-active');
    } else{
      document.getElementById("search_bar").classList.toggle('transform');
      document.getElementById("search_bar").classList.toggle('transform-active');
    }
    console.log(this.activeSearch)
  }
 }
}
</script>
<template>
    <div class="search_button" v-on:click="transform()">
        <font-awesome-icon :icon="['fas', 'magnifying-glass']" style="color: #ffffff;" />
    </div>
    <div class="search">
        <input type='text' id="search_bar" v-model='query' @keyup.enter='getResult(query)' class="transform">
    </div>
</template>
<style lang="scss" scoped> 
  .search_button{
    width: 30px;
    height: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .search_button:hover{
    border: 1px solid white;
  }
  .transform {
    height: 30px;
    width: 0px;
    border: none;
    -webkit-transition: all 1s ease;  
    -moz-transition: all 1s ease;  
    -o-transition: all 1s ease;  
    -ms-transition: all 1s ease;  
    transition: all 1s ease;
 }
 .transform-active {
    width: 200px;
    height: 30px;
    -webkit-transition: all 1s ease;  
    -moz-transition: all 1s ease;  
    -o-transition: all 1s ease;  
    -ms-transition: all 1s ease;  
    transition: all 1s ease;
  }
</style>