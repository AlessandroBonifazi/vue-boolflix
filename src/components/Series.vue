<template>
  <div class="container">
    <div v-for="(serie, index) in series" :key="index" class="card">
      <img :src="imgURL + serie.poster_path" :alt="serie.name" />

      <h4>{{ serie.name }}</h4>
      <p>{{ serie.original_name }}</p>
      <p>{{ serie.original_language }}</p>
      <p>{{ serie.vote_average }}</p>
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