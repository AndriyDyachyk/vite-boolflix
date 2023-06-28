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
 methods: {
  getResult(query) {
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
    axios.all([axios.request(optionMovies),axios.request(optionMovies)]).then(axios.spread((movieResponse, tvResponse) => { store.results = (movieResponse.data.results, tvResponse.data.results)}))
     console.log(store.results)
  }
 }
}
</script>
<template>
    <div class="search">
        <input type='text' v-model='query' @keyup='getResult(query)'>
    </div>
</template>