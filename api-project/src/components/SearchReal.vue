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
        <div id="results-item" v-for="data in totalData" :key="data">
          <div class="results-image-contain">
            <img class="results-image" :src="data.image_url" alt="image here" />
          </div>

          <div class="results-details">
            <p class="results-title">{{ data.title }}</p>
            <p class="results-rating">Rating: {{ data.score }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchReal",
  data() {
    return {
      totalData: [],
      userInput: "",
    };
  },
  // created: function () {
  //   this.fetchData();
  // },
  methods: {
    fetchData: async function () {
      try {
        // const response = await fetch(
        //   `https://api.jikan.moe/v3/search/anime?q=&order_by=members&sort=desc&page=1&limit=3`
        // );

        const response = await fetch(
          `https://api.jikan.moe/v3/search/anime?q=${this.userInput}&limit=3`
        );
        const data = await response.json();
        console.log(data);
        this.totalData = data.results;
        if (this.totalData === 0) {
          console.log("things are loading");
        }
      } catch (error) {
        console.log(error);
      }
    },
    searching() {
      console.log(this.userInput);
    },
  },
};
</script>

<style>
:root {
  --image-height: 100px;
  --image-width: 70px;
  --width-all: 20vw;
}

input {
  text-align: center;
}
.search {
  background-color: lightpink;
  max-width: var(--width-all);
  display: flex;
  flex-direction: column;
  width: 300px;
}
#searchBar-div {
  background-color: lightblue;
}
#searchBar {
  background-color: peachpuff;
  width: 100%;
  padding: 0;
  height: 25px;
  border-radius: 12px;
}
.results-list {
  background-color: rgb(240, 186, 147);
  position: absolute;
  transform: translateY(30px);
  width: 300px;
}
#results-item {
  background-color: lavender;
  display: flex;
}
.results-image {
  height: var(--image-height);
  width: var(--image-width);
}
.results-details {
  width: 100vw;
}
</style>
