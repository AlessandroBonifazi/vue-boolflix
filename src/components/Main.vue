<template>
  <main>
    <h2>Series</h2>
    <Series :series="seriesList" :imgURL="imgURL" />
    <h2>Movies</h2>
    <Movies :movies="moviesList" :imgURL="imgURL" />
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
  height: calc(100% - 100px);
}
</style>