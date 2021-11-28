<template>
  <div id="ongoing">
    <h1 class="heading">{{ name }}</h1>

    <!-- displaying ongoing content -->
    <div class="ongoing-container">
      <div class="ongoing-list">
        <div
          class="ongoing-item"
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
                <p id="details-text">Number of Episodes: {{ aEpisodes }}</p>
                <p id="details-text">Rated {{ aScore }}/10</p>
                <p id="details-text">Ranked {{ aRank }} in Comedy Anime</p>
                <p id="details-text">{{ aSummary }} ...</p>
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
  name: "Ongoing",
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
      aSummary: "",
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
          `https://api.jikan.moe/v3/genre/anime/4/${this.limit}`
        );
        const data = await result.json();
        this.animes = data.anime;
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
      this.aRank = index + 1;

      let fullSummary = this.animes[index].synopsis;
      let maxlength = 100;
      this.aSummary = fullSummary.substring(0, maxlength);
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
