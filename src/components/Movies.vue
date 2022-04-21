<template>
  <div class="container">
    <div v-for="(movie, index) in movies" :key="index" class="card">
      <img :src="imgURL + movie.poster_path" :alt="movie.title" />
      <h4>{{ movie.title }}</h4>
      <p>Titolo originale: {{ movie.original_title }}</p>
      <p>Lingua: {{ movie.original_language }}</p>
      <p>Voto: {{ voteToStar(movie.vote_average) }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesList",
  props: {
    movies: Array,
    imgURL: String,
  },
  methods: {
    voteToStar(x) {
      const vote = Math.ceil(x / 2);
      return vote;
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
    width: 25%;
    margin: 10px;
    padding: 5px;
  }
}
</style>