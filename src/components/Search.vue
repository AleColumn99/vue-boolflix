<template>

  <div class="search-bar">
    <input
      @keyup="$emit('searchMovies', movieToSearch)"
      v-model="movieToSearch"
      placeholder="Search movies..."
      type="text"
    >
    <button
      @click.prevent="$emit('searchMovies', movieToSearch)"
    >
      Search
    </button>
  </div>
  
</template>

<script>

export default {
  name: 'Search',
  props: {
    movies: Array
  },
  data() {
    return {
      movieToSearch: ''
    }
  },
  methods: {
    /* startSearch() {
      this.$emit('searchMovies', this.movieToSearch);
    } */
  }
}

</script>

<style>

</style>