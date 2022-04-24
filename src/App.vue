<template>
  <div id="app">
    <Header @search="textToSearch" />
    <Main :seriesList="series" :moviesList="movies" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import { apiKey } from "./apikey";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiURL: "https://api.themoviedb.org/3/search/",
      apiKey: apiKey,
      movies: [],
      series: [],
      query: "",
      searching: false,
    };
  },
  methods: {
    queryTv(textToSearch) {
      const params = {
        api_key: this.apiKey,
        query: textToSearch,
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
    queryMovie(textToSearch) {
      const params = {
        api_key: this.apiKey,
        query: textToSearch,
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
    textToSearch(textToSearch) {
      if (!this.searching) {
        this.queryTv(textToSearch);
        this.queryMovie(textToSearch);
      }
    },
  },
};
</script>

<style lang="scss">
@import "@/style/general.scss";
@import url("https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap");
</style>
