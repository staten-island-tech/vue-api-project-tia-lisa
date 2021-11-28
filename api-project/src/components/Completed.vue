<template>
  <div id="completed">
    <h1 class="heading">{{ name }}</h1>

    <!-- displaying upcoming content -->
    <div class="completed-container">
      <div class="completed-list">
        <div
          class="completed-item"
          v-for="(anime, index) in animes"
          :key="anime"
          @click="detailShow(index)"
        >
          <!-- making zoom effect -->
          <div class="img-container">
            <div class="img-content">
              <img class="anime-img" :src="anime.image_url" alt="anime-img" />
            </div>
          </div>

          <p>{{ anime.title }}</p>
        </div>

        <!-- popup goes here -->
        <div class="details-container" v-show="details">
          <h1 class="details-heading">{{ aTitle }} ({{ aType }})</h1>
          <div class="details-content">
            <!-- making zoom effect -->
            <div class="img-container">
              <div class="img-content">
                <img class="details-img" :src="aImg" alt="details image" />
              </div>
            </div>

            <div class="details-text">
              <div class="dTwo">
                <p id="details-text">Number of Episodes: {{ aScore }}</p>
                <p id="details-text">Rating Unavailable</p>
                <p id="details-text">Ranked {{ aRank }} in Upcoming Anime</p>
                <a id="details-text" :href="aMore" target="_blank"
                  >Click For More</a
                >
              </div>
            </div>
          </div>

          <button class="close" @click="closeDetails()">close</button>
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
      details: false,
      aTitle: "",
      aImg: "",
      aType: "",
      aEpisodes: "",
      aMore: "",
      aScore: "",
      aRank: "",
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
    detailShow(index) {
      console.log(this.animes[index]);
      this.details = true;
      this.aTitle = this.animes[index].title;
      this.aImg = this.animes[index].image_url;
      this.aType = this.animes[index].type;
      this.aEpisodes = this.animes[index].episodes;
      this.aMore = this.animes[index].url;
      this.aScore = this.animes[index].score;
      this.aRank = this.animes[index].rank;
      if (this.aScore === 0) {
        this.aScore = "TBD";
      }
    },
    closeDetails() {
      this.details = false;
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
  cursor: pointer;
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
