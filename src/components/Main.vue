<template>
  <div class="container">

    <h1>{{ titles[type] }}</h1>

    <div class="cards-container">
   
      <Card
        v-for="card in list"
        :key="card.id"
        :card="card"
      />

    </div>
 
  </div>
</template>

<script>
import Card from '../components/Card'

export default {
  name: 'Main',
  components: {
    Card
  },
  props: {
    type: String,
    list: Array
  },
  data() {
    return {
      titles: {
        'movie': 'Film',
        'tv': 'Serie TV'
      }
    }
  }
}

</script>

<style lang="scss" scoped>

.container {
  .cards-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 100px;
  }
  h1 {
    margin-top: 30px;
    margin-left: 50px;
  }
}

</style>