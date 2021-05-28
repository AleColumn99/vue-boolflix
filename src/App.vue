<template>

  <div id="app">

    <Head
      @startSearch="startSearch"
    />

    <h1 v-if="results.movie.length === 0 && results.tv.length === 0">
      Nessun risultato trovato
    </h1>

    <Main 
      v-if="results.movie.length > 0"
      type="movie"
      :list="results.movie"
    />

    <Main
      v-if="results.tv.length > 0"
      type="tv"
      :list="results.tv"
    />

  </div>

</template>

<script>
import axios from 'axios';
import Head from "./components/Head";
import Main from "./components/Main";

export default {
  name: 'App',

  components: {
    Head,
    Main
  },

  data() {
    return {
      apiURL: 'https://api.themoviedb.org/3/search/',
      apiKey: 'ea3d53e89e59031f2303c47df2769812',
      results: {
        'movie': [],
        'tv': []
      }

    }
  },

  methods: {

    startSearch(obj) {
      this.resetResults();
      if(obj.type === 'all') {
        this.getApi(obj.text, 'movie');
        this.getApi(obj.text, 'tv');
      } else {
        this.getApi(obj.text, obj.type);
      }
    },

    resetResults() {
      this.results.movie = [],
      this.results.tv = []
    },

    getApi(query, type) {

      if (query !== '') {

        axios.get(this.apiURL+type, {
          params: {
            api_key: this.apiKey,
            query: query,
            language: 'it-IT'
          }
        })
        .then(res => {
          this.results[type] = res.data.results;
        })
        .catch(err => {
          console.log(err);
        })

      }
      
    }

  }
  
}

</script>

<style lang="scss">

@import './assets/styles/general';

h1 {
  margin-top: 30px;
  margin-left: 50px;
}

</style>
