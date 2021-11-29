<template>
  <div class="container">
    <div class="featured-container">
      <h1 class="featured">Featured Sample</h1>

      <ul class="featured-list">
        <div class="item-contain">
          <li
            class="featured-list-item"
            v-for="anime in animes"
            :key="anime.title"
          >
            <div class="img-container">
              <div class="img-content">
                <img :src="anime.image_url" alt="anime-cards" class="b-img" />
              </div>
            </div>

            <div class="b-text">
              <h3 class="featured-title">{{ anime.title }}</h3>
            </div>
          </li>
        </div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "FeaturedPage",

  data() {
    return {
      animes: [],
    };
  },

  created: function () {
    this.fetchAnime();
  },

  methods: {
    fetchAnime: async function () {
      try {
        const result = await fetch(
          "https://api.jikan.moe/v3/search/anime?order_by=score&limit=10"
        );
        const data = await result.json();
        this.animes = data.results;
        console.log(data);
      } catch (error) {
        alert(error);
      }
    },
  },
};
</script>

<style>
/* .container {
  display: flex;
  align-items: center;
  flex-direction: column;
  background-color: #f4f4f4;
}

.featured-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  width: 67.5rem;
  border-style: solid;
  background-color: black;
}

.featured-list-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: white;
  height: 15rem;
  width: 10.5rem;
  margin-top: 1rem;
  margin-bottom: 2rem;
  margin-right: 0.25rem;
  border-style: solid;
  padding: 1rem;
  padding-bottom: 2rem;
  font-size: 0.8rem;
}

.img {
  height: 15rem;
  width: 10.5rem;
  margin-bottom: 0.125rem;
}

.featured-container {
  border-style: solid;
} */

/* https://colorhunt.co/palette/b983ff94b3fd94daff99feff */

.container {
  display: flex;
  justify-content: center;
  /* background-color: lightcyan; */
}

.featured-container {
  width: 90vw;
  /* background-color: thistle; */
}

.featured-list {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  list-style-type: none;
  /* background-color: lightgreen; */
}

.featured-list-item {
  /* background-color: turquoise; */
  width: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.featured-title {
  color: var(--second-color);
  font-size: 15px;
  letter-spacing: 2px;
}

.b-img {
  width: 200px;
  height: 270px;
}

.b-text {
  background-color: rgb(241, 230, 248);
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  width: 200px;
}

.item-contain {
  width: 90%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.featured {
  color: var(--first-color);
  text-transform: uppercase;
  letter-spacing: 4px;
}
</style>
