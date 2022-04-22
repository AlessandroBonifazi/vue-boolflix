<template>
  <div class="container">
    <div v-for="(movie, index) in movies" :key="index" class="card">
      <!-- poster -->
      <img :src="imgURL + movie.poster_path" :alt="movie.title" />
      <!-- titles -->
      <h4>{{ movie.title }}</h4>
      <span>Titolo originale: {{ movie.original_title }}</span>
      <!-- language -->
      <div>
        <span>Lingua:</span>
        <span v-if="movie.original_language === 'en'">
          <img id="en-flag" src="@/assets/en_flag.png" alt="en flag" />
        </span>
        <span v-else>
          <country-flag :country="movie.original_language" size="small" />
        </span>
      </div>
      <!-- ratings -->
      <span>
        Voto:
        <!-- {{ voteToStar(movie.vote_average) }} -->
        <font-awesome-icon
          v-for="vote in voteToStar(movie.vote_average)"
          :key="vote"
          icon="fa-solid fa-star"
          class="star"
        />
        <font-awesome-icon
          v-for="vote in 5 - voteToStar(movie.vote_average)"
          :key="vote"
          icon="fa-regular fa-star"
        />
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesList",
  data() {
    return {};
  },
  props: {
    movies: Array,
    imgURL: String,
  },
  methods: {
    voteToStar(x) {
      return Math.ceil(x / 2);
    },
  },
};
</script>

<style scoped lang="scss">
.container {
  width: 80%;
  margin: auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  .card {
    display: flex;
    flex-direction: column;
    align-content: space-between;
    width: 20%;
    margin: 10px;
    padding: 5px;
    .star {
      color: gold;
    }
    #en-flag {
      height: 20px;
    }
  }
}
</style>