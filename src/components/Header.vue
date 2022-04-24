<template>
  <header>
    <div class="logo">
      <h2>BOOLFLIX</h2>
    </div>
    <div>
      <input class="searchInput" type="text" v-model="textToSearch" />
      <button @click="search">SEARCH</button>
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
  background-color: black;
  .searchInput {
    padding: 7px;
    margin: 15px;
    background-color: lightgray;
  }
  button {
    padding: 6px;
    font-size: 14px;
    font-weight: 600;
    color: white;
    background-color: black;
    border: 2px solid lightgray;
    border-radius: 5px;
  }
  button:hover {
    background-color: rgba(94, 92, 92, 0.575);
    cursor: pointer;
  }
  .logo {
    h2 {
      font-size: 50px;
      color: red;
      font-weight: 700;
    }
  }
}
</style>
