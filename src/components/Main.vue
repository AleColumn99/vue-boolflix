<template>
  <div class="container">

    <h1>{{ titles[type] }}</h1>
    
    <Card
      v-for="card in list"
      :key="card.id"
      :card="card"
    />

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
        'movie': 'Movies found',
        'tv': 'TV Series found'
      }
    }
  }
}

</script>

<style lang="scss" scoped>

.container {
  margin-bottom: 100px;
  h1 {
    margin-top: 30px;
    margin-left: 50px;
  }
}

</style>