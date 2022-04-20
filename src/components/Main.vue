<template>
  <header>
    <h3>series</h3>
    <span>{{ seriesList }}</span>
    <h3>movies</h3>
    <span>{{ moviesList }}</span>
  </header>
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
header {
  height: 100px;
}
</style>