<template>
  <main>
    <div class="container">
      <h2>Series</h2>
      <font-awesome-icon icon="fa-solid fa-chevron-down" class="chevron" />
      <Series :series="seriesList" :imgURL="imgURL" />
    </div>

    <div class="container">
      <h2>Movies</h2>
      <font-awesome-icon icon="fa-solid fa-chevron-down" class="chevron" />
      <Movies :movies="moviesList" :imgURL="imgURL" />
    </div>
  </main>
</template>

<script>
import Movies from "@/components/Movies.vue";
import Series from "@/components/Series.vue";
export default {
  name: "MainComponent",
  components: {
    Movies,
    Series,
  },
  props: {
    seriesList: Array,
    moviesList: Array,
  },
  data() {
    return {
      imgURL: "https://image.tmdb.org/t/p/w342",
    };
  },
};
</script>

<style scoped lang="scss">
main {
  h2 {
    padding: 20px 0px 20px 150px;
    color: rgba(255, 255, 255, 0.918);
    display: inline-block;
  }
  .chevron {
    color: red;
    margin: 0px 10px;
    height: 20px;
  }
}
</style>