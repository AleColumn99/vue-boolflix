<template>

  <div>

    <ul class="list-group">

      <li class="list-group-item">
        <h4>Titolo italiano: </h4> {{ card.title || card.name }}
      </li>
      <li class="list-group-item">
        <h4>Titolo originale: </h4> {{ card.original_title || card.original_name }}
      </li>

      <li v-if="flags.includes(card.original_language)" class="list-group-item lang">
        <h4>Lingua originale: </h4> <img :src="require(`@/assets/img/${card.original_language}.png`)" :alt="card.original_language">
      </li>
      <li v-else class="list-group-item">
        <h4>Lingua originale: </h4> {{ card.original_language }}
      </li>

      <li class="list-group-item">
        <h4>Media voto: </h4>
        <i
          v-for="index in voteToStars(card.vote_average)"
          :key="index"
          class="fas fa-star"
        ></i>
      </li>
      <li class="list-group-item">
        <img :src="`http://image.tmdb.org/t/p/w300/${card.poster_path}`" alt="">
      </li>

    </ul>

  </div>
  
</template>

<script>

export default {
  name: 'Card',
  data() {
    return {
      flags: ['it', 'en']
    }
  },
  props: {
    card: Object
  },
  methods: {
    voteToStars(vote) {
      return Math.ceil(vote / 2);
    }
  }
}

</script>

<style lang="scss" scoped>

  div {
    margin-top: 30px;
    .lang img {
      height: 15px;
    }
    li i {
      color: darkgoldenrod;
    }
  }


</style>