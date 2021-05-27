<template>

  <div class="container">

    <div class="search-bar">
      <input
        
        v-model="textToSearch"
        placeholder="Search movies..."
        type="text"
      >
      <!-- @keyup="$emit('startSearch', {text:textToSearch, type:'all'})" -->
    </div>
    
    <div class="search-btn">
      <button
        @click="$emit('startSearch', {text:textToSearch, type:'all'})"
      >
        Search All
      </button>
      <button
        @click="$emit('startSearch', {text:textToSearch, type:'movie'})"
      >
        Search Movies
      </button>
      <button
        @click="$emit('startSearch', {text:textToSearch, type:'tv'})"
      >
        Search Series
      </button>
    </div>
    
  </div>
  
</template>

<script>

export default {
  name: 'Head',
  data() {
    return {
      textToSearch: ''
    }
  }
}

</script>

<style lang="scss" scoped>

</style>