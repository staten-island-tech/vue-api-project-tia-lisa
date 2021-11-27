<template>
  <div id="ongoing">
    <h1 class="heading">{{ name }}</h1>
    <Details v-show="details"></Details>
    <!-- displaying ongoing content -->
    <div class="ongoing-container">
      <div class="ongoing-list">
        <div
          class="ongoing-item"
          v-for="anime in animes"
          :key="anime"
          @click="detailShow"
        >
          <img class="anime-img" :src="anime.image_url" alt="anime-img" />
          <p>{{ anime.title }}</p>
        </div>
      </div>
    </div>
    <button class="load-more" @click="addLoad">Load Next</button>
  </div>
</template>

<script>
import Details from "./Details.vue";

export default {
  name: "Ongoing",
  props: ["name"],
  components: {
    Details,
  },
  created: function () {
    this.fetchAnime();
  },
  data() {
    return {
      animes: [],
      limit: 1,
      details: false,
    };
  },
  methods: {
    addLoad() {
      this.limit = this.limit + 1;
      this.fetchAnime();
    },
    fetchAnime: async function () {
      try {
        const result = await fetch(
          `https://api.jikan.moe/v3/top/anime/${this.limit}/airing`
        );
        const data = await result.json();
        this.animes = data.top;
        console.log(data);
      } catch (error) {
        alert(error);
      }
    },
  },
  detailShow() {
    this.details = true;
  },
};
</script>

<style>
p {
  letter-spacing: 2px;
  color: var(--first-color);
}

.ongoing-container {
  display: flex;
  justify-content: center;
}
.ongoing-list {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  width: 90vw;
}

.ongoing-item {
  width: 200px;
  padding: 15px;
}

.anime-img {
  width: 200px;
  height: 300px;
}

.ongoing-item:hover {
  background-color: var(--third-color);
}

.load-more {
  border: none;
  width: 200px;
  height: 40px;
  border-radius: 5px;
  font-family: var(--main-font);
  background-color: var(--third-color);
  color: var(--first-color);
  letter-spacing: 3px;
  text-transform: uppercase;
}

.load-more:hover {
  cursor: pointer;
}
.heading {
  font-size: 25px;
  color: var(--first-color);
  font-size: 1.5rem;
  letter-spacing: 15px;
}
</style>
