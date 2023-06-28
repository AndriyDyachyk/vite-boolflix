<script>
import axios from 'axios'
import { store } from '../store';
export default {
 name: 'search',
 data () {
 return {
  query: '',
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
  }

 }
}
</script>
<template>
    <div class="search">
        <input type='text' v-model='query' @keyup='getResult(query)'>
    </div>
</template>