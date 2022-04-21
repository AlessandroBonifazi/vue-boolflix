<template>
  <header>
    <div>
      <input type="text" v-model="inputText" />
      <button @click="search">Search</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      inputText: "",
    };
  },
  methods: {
    search() {
      this.$emit("search", this.inputText);
    },
  },
};
</script>

<style scoped lang="scss">
header {
  height: 100px;
}
</style>
