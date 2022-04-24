<template>
  <div class="card">
    <!-- poster -->
    <img :src="img" :alt="title" />
    <!-- titles -->
    <h4>{{ title }}</h4>
    <span>Titolo originale: {{ originalTitle }}</span>
    <!-- language -->
    <div>
      <span>Lingua:</span>
      <span v-if="language === 'en'">
        {{ language }}
        <img id="en-flag" src="@/assets/en_flag.png" alt="en flag" />
      </span>
      <span v-else>
        {{ language }}
        <country-flag :country="language" size="small" />
      </span>
    </div>
    <!-- ratings -->
    <span>
      Voto:
      <font-awesome-icon
        v-for="vote in voteToStar(vote)"
        :key="vote"
        icon="fa-solid fa-star"
        class="star"
      />
      <font-awesome-icon
        v-for="vote in 5 - voteToStar(vote)"
        :key="'E' + vote"
        icon="fa-regular fa-star"
      />
    </span>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: {
    img: String,
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
    overview: String,
  },
  methods: {
    voteToStar(x) {
      return Math.ceil(x / 2);
    },
  },
};
</script>

<style scoped lang="scss">
.card {
  display: flex;
  flex-direction: column;
  align-content: space-between;
  width: 20%;
  margin: 10px;
  padding: 5px;
  .star {
    color: gold;
  }
  #en-flag {
    height: 20px;
  }
}
</style>