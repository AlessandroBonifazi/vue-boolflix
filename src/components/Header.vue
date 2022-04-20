<template>
  <main>
    <div>
      <input type="text" v-model="inputText" />
      <button @click="$emit('search', inputText)">Search</button>
    </div>
  </main>
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
main {
  height: calc(100% - 100px);
}
</style>
