<template>
  <div id="ongoing">
    <h1 class="heading">{{ name }}</h1>
    <!-- <Details v-show="details"></Details> -->
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
          <div class="img-container pg-img">
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
            <div class="img-div">
              <div class="img-container">
                <div class="img-content">
                  <img class="details-img" :src="aImg" alt="details image" />
                </div>
              </div>
            </div>

            <div class="details-text">
              <div class="dTwo">
                <p id="details-text">Number of Episodes: {{ aEpisodes }}</p>
                <p id="details-text">Rated {{ aScore }}/10</p>
                <p id="details-text">Ranked {{ aRank }} in Airing Anime</p>
                <p id="details-text">{{ aStart }} - {{ aEnd }}</p>
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
// import Details from "./Details.vue";

export default {
  name: "Ongoing",
  props: ["name"],
  components: {
    // Details,
  },
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
      aStart: "",
      aEnd: "",
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
      this.aStart = this.animes[index].start_date;
      this.aEnd = this.animes[index].end_date;
      if (this.aEnd === null) {
        this.aEnd = "TBD";
      }
      if (this.aEpisodes === null) {
        this.aEpisodes = "TBD";
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

.details-container {
  width: 80%;
  height: 80%;
  background-image: url("https://images.unsplash.com/photo-1506269996138-4c6d92fbd8a5?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2350&q=80");
  position: fixed;
  z-index: 1;
  left: 10%;
  top: 10%;
  border-radius: 15px;
}

.details-content {
  /* background-color: blue; */
  display: flex;
  justify-content: space-evenly;
  width: 100%;
  height: 70%;
  align-items: center;
}

.details-text {
  background-color: rgb(206, 217, 247);
  width: 500px;
  word-wrap: break-word;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 14px;
}

#details-text {
  font-size: 20px;
  color: var(--first-color);
}

.details-img {
  width: 340px;
  height: 90%;
}

.dTwo {
  width: 400px;
}
.details-heading {
  color: var(--first-color);
}

.close {
  border: none;
  width: 200px;
  height: 40px;
  border-radius: 5px;
  font-family: var(--main-font);
  color: var(--first-color);
  letter-spacing: 3px;
  text-transform: uppercase;
  font-size: 20px;
}

.close:hover {
  cursor: pointer;
  background-color: var(--second-color);
}

/* zoom */
.img-container {
  overflow: hidden;
  position: relative;
}
.img-content {
  transition: all 1s;
}
.img-content:hover {
  transform: scale(1.1);
}
</style>
