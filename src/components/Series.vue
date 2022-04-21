<template>
  <div class="container">
    <div v-for="(serie, index) in series" :key="index" class="card">
      <img :src="imgURL + serie.poster_path" :alt="serie.name" />

      <h4>{{ serie.name }}</h4>
      <p>Titolo originale:{{ serie.original_name }}</p>
      <p>Lingua: {{ serie.original_language }}</p>
      <p>Voto: {{ voteToStar(serie.vote_average) }}</p>
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