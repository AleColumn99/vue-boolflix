<template>

  <div class="card-container">

    <div class="card">

      <div class="card-front">
        <p v-if="card.poster_path === null">
          <strong> {{ card.title || card.name }} </strong>
        </p>
        <img :src="`http://image.tmdb.org/t/p/original/${card.poster_path}`" v-else>
      </div>

      <div class="card-back">

        <p class="name"><strong> {{ card.title || card.name }} </strong></p>

        <p class="original-name"><i> {{ card.original_title || card.original_name }} </i></p>

        <span v-if="flags.includes(card.original_language)" class="lang">
          <img :src="require(`@/assets/img/${card.original_language}.png`)" :alt="card.original_language"> 
        </span>

        <span v-else>
          <h5>Lingua originale: </h5> {{ card.original_language }}
        </span>

        <div v-if="card.overview != ''" class="overview">
          <h5><strong>Trama: </strong></h5>
          <p> {{ card.overview }} </p>
        </div>

        <p class="vote">Media voto: </p>
        <div class="vote">
          <i
            v-for="index in voteToStars(card.vote_average)"
            :key="index"
            class="fas fa-star"
          ></i>
          <i
            v-for="index in (5 - voteToStars(card.vote_average))"
            :key="index"
            class="far fa-star"
          ></i>
        </div>
 
      </div>

    </div>

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

  .card-container {
    background-color: transparent;
    width: 250px;
    height: 350px;
    margin: 20px 10px;
    perspective: 1000px;
  }

  .card {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
    border: none;
  }

  .card-container:hover .card {
    transform: rotateY(180deg);
  }

  .card-front, .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }

  .card-front {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #101010;
    color: #FFFFFF;
    p {
      margin: 20px;
      font-size: 30px;
    }
    img {
      width: 100%;
      height: 100%;
    }
  }

  .card-back {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    text-align: left;
    padding: 20px;
    background-color: #111111;
    color: white;
    transform: rotateY(180deg);
    .name {
      font-size: 18px;
      margin-bottom: 2px;
    }
    .original-name {
      font-size: 12px;
      margin-bottom: 5px;
    }
    .lang {
      margin-bottom: 10px;
      img {
      width: 25px;
      }
    }
    .overview {
      font-size: 12px;
      h5 {
        margin-bottom: 2px;
      }
      p {
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 6;
        -webkit-box-orient: vertical;
      }
    }
    p.vote {
      font-size: 10px;
      margin-bottom: 2px;
    }
    div.vote {
      display: flex;
      justify-content: flex-start;
    }
  }

</style>