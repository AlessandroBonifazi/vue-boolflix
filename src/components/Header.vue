<template>
  <header>
    <div class="logo">
      <h2>Boolflix</h2>
    </div>
    <div>
      <input type="text" v-model="textToSearch" />
      <button @click="search">Search</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      textToSearch: "",
    };
  },
  methods: {
    search() {
      this.$emit("search", this.textToSearch);
    },
  },
};
</script>

<style scoped lang="scss">
header {
  height: 100px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
</style>
