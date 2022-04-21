<template>
  <div class="container">
    <div v-for="(movie, index) in movies" :key="index" class="card">
      <img :src="imgURL + movie.poster_path" :alt="movie.title" />
      <h4>{{ movie.title }}</h4>
      <p>{{ movie.original_title }}</p>
      <p>{{ movie.original_language }}</p>
      <p>{{ movie.vote_average }}</p>
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
};
</script>

<style scoped lang="scss">
.container {
  width: 80%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  .card {
    margin: 20px;
    padding: 10px;
    border: 2px solid black;
  }
}
</style>