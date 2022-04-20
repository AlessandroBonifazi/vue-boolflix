<template>
  <header>
    <div>
      <input type="text" v-model="inputText" />
      <button @click="$emit('search', inputText)">Search</button>
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
};
</script>

<style scoped lang="scss">
header {
  height: 100px;
}
</style>
