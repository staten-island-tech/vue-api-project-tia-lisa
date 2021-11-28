<template>
  <div id="seach-real">
    <div class="search">
      <div id="searchBar-div">
        <input
          type="text"
          name="search-bar"
          id="searchBar"
          placeholder="search"
          v-on:keyup="fetchData"
          v-model="userInput"
        />
      </div>

      <div class="results-list">
        <div
          id="results-item"
          v-for="(data, index) in totalData"
          :key="data"
          @click="detailShow(index)"
        >
          <div class="results-image-contain">
            <img class="results-image" :src="data.image_url" alt="image here" />
          </div>

          <div class="results-details">
            <p class="results-title">{{ data.title }}</p>
            <p class="results-rating">Rating: {{ data.score }}</p>
          </div>
        </div>
        <div class="search-info" v-show="searchDetails">
          <a id="details-text" :href="aLink" target="_blank">{{ aTitle }}</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchReal",
  components: {},
  data() {
    return {
      totalData: [],
      userInput: "",
      searchDetails: false,
      aLink: "",
      aTitle: "",
    };
  },
  methods: {
    fetchData: async function () {
      try {
        const response = await fetch(
          `https://api.jikan.moe/v3/search/anime?q=${this.userInput}&limit=3`
        );
        const data = await response.json();
        console.log(data);
        this.totalData = data.results;
        if (this.userInput.length === 0) {
          this.searchDetails = false;
        }
      } catch (error) {
        console.log(error);
      }
    },
    searching() {
      console.log(this.userInput);
    },
    detailShow(index) {
      console.log(this.totalData[index]);
      this.searchDetails = true;
      this.aLink = this.totalData[index].url;
      this.aTitle = this.totalData[index].title;
    },
  },
};
</script>

<style>
#search-real {
  z-index: 1;
}
:root {
  --image-height: 100px;
  --image-width: 70px;
  --width-all: 20vw;
}

input {
  text-align: center;
  font: var(--main-font);
  letter-spacing: 3px;
  color: var(--second-color);
  border-color: var(--first-color);
  border-style: solid;
  background-color: rgb(223, 223, 253);
}

::placeholder {
  color: var(--first-color);
}

input:focus {
  background-color: rgb(241, 215, 255);
  outline: none;
}
.search {
  max-width: var(--width-all);
  display: flex;
  flex-direction: column;
  width: 300px;
}
/* #searchBar-div {
  background-color: lightblue;
} */
#searchBar {
  width: 100%;
  padding: 0;
  height: 25px;
  border-radius: 12px;
}
.results-list {
  background-color: rgb(199, 233, 255);
  position: absolute;
  transform: translateY(30px) translateX(5px);
  width: 290px;
}
#results-item {
  display: flex;
}
#results-item:hover {
  background-color: rgb(183, 226, 255);
  cursor: pointer;
}
.results-image {
  height: var(--image-height);
  width: var(--image-width);
}
.results-details {
  width: 100vw;
  color: var(--first-color);
}
.results-title {
  font-size: 15px;
  letter-spacing: 3px;
}

.results-rating {
  font-size: 14px;
  letter-spacing: 2px;
}
</style>
