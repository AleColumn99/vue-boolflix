<template>

  <div class="header-wrap">

    <div class="header-container d-flex">

      <div class="search-bar">
        <input
          @keyup.enter="$emit('startSearch', {text:textToSearch, type:'all'})"
          v-model="textToSearch"
          placeholder="Search movies..."
          type="text"
        >
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

  .header-wrap {
    width: 100%;
    height: 100px;
    margin: 0;
    background-color: darkslategrey;
    .header-container {
      height: 100%;
      align-items: center;
    }
    .search-bar {
      margin-left: 100px;
      width: 70%;
      max-width: 1000px;
      input {
        width: 100%;
        border: 0;
        border-radius: 999px;
        padding: 10px;
      }
    }
    .search-btn {
      button {
        margin-left: 50px;
        border: 0;
        border-radius: 999px;
        padding: 10px;
      }
    }
  }

</style>