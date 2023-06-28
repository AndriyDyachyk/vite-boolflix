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
    const options = {
    method: 'GET',
    url: `https://api.themoviedb.org/3/search/movie?query=${query}&language=en-US&page=1`,
        headers: {
            accept: 'application/json',
            Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIyZWFhNDE4NDM1ZjRmMDkyMWM0Yzc5ZmEzOGFkODQ5MSIsInN1YiI6IjY0OWE5YTFmYTZkZGNiMDBjNjllYjI0YyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.U3IDVk8qcXcPPzYt7cq-3iNNcQxMukQJsEMvM7n-8fA'
        }
    };
    axios.request(options).then(response => { store.results = response.data.results})
     console.log(store.results)
     console.log(query)
  }
 }
}
</script>
<template>
    <div class="search">
        <input type='text' v-model='query' @keyup='getResult(query)'>
    </div>
</template>