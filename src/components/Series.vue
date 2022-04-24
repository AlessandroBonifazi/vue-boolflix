<template>
  <div class="container">
    <CardComponent
      v-for="(serie, index) in series"
      :key="index"
      :img="imgURL + serie.poster_path"
      :title="serie.name"
      :originalTitle="serie.original_name"
      :language="serie.original_language"
      :vote="serie.vote_average"
      :overview="serie.overview"
    />
  </div>
</template>

<script>
import CardComponent from "./Card.vue";

export default {
  name: "SeriesList",
  components: {
    CardComponent,
  },
  props: {
    series: Array,
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

