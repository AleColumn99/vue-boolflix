<template>
  <div class="container">
    <ul
      v-for="(movie, index) in filteredMovies"
      :key="index"
      :movie="movie"
    >
      <li>
       Titolo: {{ movie.title }}
      </li>
      <li>
       Titolo originale: {{ movie.original_title }}
      </li>
      <li>
       Lingua originale: {{ movie.original_language }}
      </li>
      <li>
       Media voto: {{ movie.vote_average }}
      </li>
      <li>
        banana
      </li>
    </ul>
  </div>
</template>

<script>

import axios from 'axios';

export default {
  name: 'Main',
  props: {
    movieToSearch: String
  },
  computed: {
    filteredMovies() {
       if(this.movieToSearch === '') {
         return this.movies;
       }
       return this.movies.filter(movie => movie.title === this.movieToSearch)
    }
  },
  data() {
    return {
      axios,
      apiURL: 'https://api.themoviedb.org/3/search/movie',
      apiKey: 'ea3d53e89e59031f2303c47df2769812',
      query: '',
      movies: [],
    }
  },
  created() {
    axios.get(this.apiURL, {
      params: {
        api_key: this.apiKey,
        query: this.query,
        language: 'it-IT'
      }
    })
    .then(resp => {
      this.movies = resp.data.results;
      this.$emit('onMovies', this.movies);
    })
    .catch(err => {
      console.log(err);
    })
  }
}

</script>

<style>

</style>