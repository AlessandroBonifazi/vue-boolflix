<template>
  <div class="container">
    <div v-for="(serie, index) in series" :key="index" class="card">
      <img :src="imgURL + serie.poster_path" :alt="serie.name" />

      <h4>{{ serie.name }}</h4>
      <span>Titolo originale:{{ serie.original_name }}</span>
      <span>Lingua: {{ serie.original_language }}</span>
      <span>
        Voto:
        <!-- {{ voteToStar(serie.vote_average) }} -->
        <font-awesome-icon
          v-for="vote in voteToStar(serie.vote_average)"
          :key="vote"
          icon="fa-solid fa-star"
        />
        <font-awesome-icon
          v-for="vote in 5 - voteToStar(serie.vote_average)"
          :key="vote"
          icon="fa-regular fa-star"
        />
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "SeriesList",
  props: {
    series: Array,
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
    width: 25%;
    margin: 10px;
    padding: 5px;
  }
}
</style>