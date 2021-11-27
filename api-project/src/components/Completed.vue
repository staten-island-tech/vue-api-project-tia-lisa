<template>
  <div id="completed">
    <h1 class="heading">{{ name }}</h1>

    <!-- displaying completed content -->
    <div class="completed-container">
      <div class="completed-list">
        <div class="completed-item" v-for="anime in animes" :key="anime">
          <img class="anime-img" :src="anime.image_url" alt="anime-img" />
          <p>{{ anime.title }}</p>
        </div>
      </div>
    </div>
    <button class="load-more" @click="addLoad">Load Next</button>
  </div>
</template>

<script>
export default {
  name: "Completed",
  props: ["name"],
  created: function () {
    this.fetchAnime();
  },
  data() {
    return {
      animes: [],
      limit: 1,
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
          `https://api.jikan.moe/v3/top/anime/${this.limit}/upcoming`
        );
        const data = await result.json();
        this.animes = data.top;
        console.log(data);
      } catch (error) {
        alert(error);
      }
    },
  },
};
</script>

<style>
p {
  letter-spacing: 2px;
  color: var(--first-color);
}
.completed-container {
  display: flex;
  justify-content: center;
}
.completed-list {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  width: 90vw;
}

.completed-item {
  width: 200px;
  padding: 15px;
}

.anime-img {
  width: 200px;
  height: 300px;
}

.completed-item:hover {
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

.heading {
  font-size: 25px;
  color: var(--first-color);
  font-size: 1.5rem;
  letter-spacing: 7px;
}
</style>
