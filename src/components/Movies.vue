<template>
  <div class="container">
    <CardComponent
      v-for="(movie, index) in movies"
      :key="index"
      :img="imgURL + movie.poster_path"
      :title="movie.title"
      :originalTitle="movie.original_title"
      :language="movie.original_language"
      :vote="movie.vote_average"
      :overview="movie.overview"
    />
  </div>
</template>

<script>
import CardComponent from "./Card.vue";

export default {
  name: "MoviesList",
  components: {
    CardComponent,
  },
  props: {
    movies: Array,
    imgURL: String,
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
}
</style>