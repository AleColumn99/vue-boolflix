<template>

  <div id="app">

    <Search 
      @startSearch="startSearch"
      :movies="movies" 
    />

    <Main 
      movieToSearch="movieToSearch"
      @onMovies="getMovies"
    />

  </div>

</template>

<script>
import Search from "./components/Search";
import Main from "./components/Main";

export default {
  name: 'App',
  components: {
    Search,
    Main
  },
  data() {
    return {
      movies: [],
      movieToSearch: ''
    }
  },
  methods: {
    getMovies(movies){
      this.movies = movies;
    },
    startSearch(movieToSearch) {
      this.movieToSearch = movieToSearch;
    }
  }
}

</script>

<style lang="scss">

</style>
