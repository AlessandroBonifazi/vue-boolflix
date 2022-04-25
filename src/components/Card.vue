<template>
  <div class="card" @mouseenter="hover = true" @mouseleave="hover = false">
    <!-- poster -->
    <div v-if="!hover">
      <img :src="img" :alt="title" />
    </div>

    <div v-else class="details">
      <!-- titles -->
      <h3>{{ title }}</h3>
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
      <!-- overview -->
      <p class="overview">{{ overview }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  data() {
    return {
      hover: false,
    };
  },
  props: {
    // info: Object,
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
  height: 450px;
  width: 15%;
  margin: 10px;
  padding: 5px;
  cursor: pointer;
  overflow-y: hidden;

  img {
    width: 100%;
    border: 2px solid lightgrey;
    padding: 3px;
    border-radius: 5px;
  }
  .star {
    color: gold;
  }
  #en-flag {
    height: 20px;
  }
  .details {
    color: white;
    .overview {
      font-size: 14px;
      font-family: Arial, Helvetica, sans-serif;
    }
  }
}
</style>