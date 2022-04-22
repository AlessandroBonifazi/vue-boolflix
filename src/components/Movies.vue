<template>
  <div class="container">
    <div v-for="(movie, index) in movies" :key="index" class="card">
      <img :src="imgURL + movie.poster_path" :alt="movie.title" />
      <h4>{{ movie.title }}</h4>
      <span>Titolo originale: {{ movie.original_title }}</span>
      <span> Lingua: {{ movie.original_language }} </span>
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
  }
}
</style>