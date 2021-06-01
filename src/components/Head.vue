<template>

  <div class="header-wrap">

    <div class="header-container d-flex">

      <div class="logo">
        <img src="../assets/img/netflix.png" alt="">
      </div>

      <div class="search-bar">
        <input
          @keyup.enter="$emit('startSearch', {text:textToSearch, type:'all'})"
          v-model="textToSearch"
          placeholder="Search movies..."
          type="text"
        >
      </div>

      <!-- <div class="search-select">
        <select name="" id="">
          <option 
            value="all"
            @click="$emit(type = 'all')"
          >
            Tutto
          </option>
          <option 
            value="movie"
            @click="$emit('startSearch', {text:textToSearch, type:'movie'})"
          >
            Film
          </option>
          <option 
            value="tv"
            @click="$emit(type = 'tv')"
          >
            Serie TV
          </option>
        </select>
      </div> -->
      
      <div class="search-btn">
        <button
          @click="$emit('startSearch', {text:textToSearch, type:'all'})"
        >
          Cerca
        </button>
        <button
          @click="$emit('startSearch', {text:textToSearch, type:'movie'})"
        >
          Cerca Film
        </button>
        <button
          @click="$emit('startSearch', {text:textToSearch, type:'tv'})"
        >
          Cerca Serie TV
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
    background-color: black;
    
    .header-container {
      display: flex;
      justify-content: space-between;
      width: 90%;
      height: 100%;
      margin: auto;
      align-items: center;
    }
    .logo {
      width: 10%;
      img {
        height: 100px;
      }
    }
    .search-bar {
      width: 50%;
      max-width: 1000px;
      input {
        width: 100%;
        border: 0;
        padding: 10px;
        outline: none;
        background-color: black;
        color: white;
        border-bottom: 1px solid white;
      }
    }
    .search-btn {
      display: flex;
      justify-content: space-between;
      width: 20%;
      button {
        font-size: 10px;
        border: 0;
        border-radius: 999px;
        padding: 10px;
      }
    }
  }

</style>