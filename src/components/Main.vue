<template>
  <main>
    <div class="container">
      <h2>Series</h2>
      <div v-for="(series, index) in seriesList" :key="index" class="card">
        <h4>{{ series.name }}</h4>
        <p>{{ series.original_name }}</p>
        <p>{{ series.original_language }}</p>
        <p>{{ series.vote_average }}</p>
      </div>
    </div>

    <div class="container">
      <h2>Movies</h2>
      <div v-for="(movies, index) in moviesList" :key="index" class="card">
        <h4>{{ movies.title }}</h4>
        <p>{{ movies.original_title }}</p>
        <p>{{ movies.original_language }}</p>
        <p>{{ movies.vote_average }}</p>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainComponent",
  props: {
    seriesList: Array,
    moviesList: Array,
  },
};
</script>

<style scoped lang="scss">
main {
  height: calc(100% - 100px);
  .container {
    display: flex;
    flex-wrap: wrap;
    .card {
      margin: 20px;
      padding: 10px;
      border: 2px solid black;
    }
  }
}
</style>