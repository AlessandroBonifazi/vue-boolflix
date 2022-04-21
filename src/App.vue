<template>
  <div id="app">
    <Header @search="inputText" />
    <Main :seriesList="series" :moviesList="movies" />
  </div>
</template>

<script>
import axios from "axios";
// import apiKey from "@/apikey";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiURL: "https://api.themoviedb.org/3/search/",
      apiKey: "cb32b76d65a06b66bff56fd2212a7853",
      movies: [],
      series: [],
      query: "",
      searching: false,
    };
  },
  methods: {
    queryTv(inputText) {
      const params = {
        api_key: this.apiKey,
        query: inputText,
        language: "it-IT",
      };
      axios
        .get(this.apiURL + "tv", { params })
        .then(({ data }) => {
          this.series = data.results;
          this.searching = false;
          console.log("series", this.series);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    queryMovie(inputText) {
      const params = {
        api_key: this.apiKey,
        query: inputText,
        language: "it-IT",
      };
      axios
        .get(this.apiURL + "movie", { params })
        .then(({ data }) => {
          this.movies = data.results;
          this.searching = false;
          console.log("movies", this.movies);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    inputText(inputText) {
      if (!this.searching) {
        this.queryTv(inputText);
        this.queryMovie(inputText);
      }
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
