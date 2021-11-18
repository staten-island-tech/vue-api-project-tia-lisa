<template>
  <div>
    <div id="search">
      <form class="search">
        <input type="text" class="search-item" id="user-input" />
        <input
          type="button"
          value="submit"
          @click="animeData"
          class="search-item"
          id="search-button"
        />
      </form>
    </div>

    <div class="details">
      <p id="display-name"></p>
      <p id="display-summary"></p>
      <p id="display-airing"></p>
    </div>

    <div id="testing" v-for="data in topData" :key="data">
      <img src="" alt="" />
      <p>{{ data.title }}</p>
      <p>Rating: {{ data.score }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      name: "",
      topData: [],
    };
  },

  created: function () {
    this.fetchData();
  },
  methods: {
    fetchData: async function () {
      try {
        this.name = document.getElementById("user-input").value;
        const response = await fetch(
          `https://api.jikan.moe/v3/search/anime?q=&order_by=members&sort=desc&page=1`
        );
        const data = await response.json();
        console.log(data);
        this.topData = data.results;
      } catch (error) {
        console.log(error);
      }
    },
    animeData: async function () {
      try {
        this.name = document.getElementById("user-input").value;
        const response = await fetch(
          `https://api.jikan.moe/v3/search/anime?q=${this.name}`
        );
        const data = await response.json();
        console.log(this.fullLink);
        console.log(data.results[0].synopsis);
        console.log(data.results[0].airing);
        document.getElementById("display-name").innerHTML = this.name;
        document.getElementById("display-summary").innerHTML =
          data.results[0].synopsis;
        document.getElementById("display-airing").innerHTML =
          "Airing Status: " + data.results[0].airing;
      } catch (error) {
        console.log(error);
      }
    },
  },

  //   created: function () {
  //     this.fetchData();
  //   },
  //   methods: {
  //     fetchData: async function () {
  //       try {
  //         const response = await fetch(
  //           " https://api.jikan.moe/v3/search/anime?q=horimiya"
  //         );
  //         const data = await response.json();
  //         this.animes = data.results;
  //         console.log(data.results[0]);
  //         console.log(data.results[0].synopsis);
  //         console.log(data.results[0].airing);
  //       } catch (error) {
  //         console.log(error);
  //       }
  //     },
  //   },
};
</script>

<style scoped>
p {
  color: red;
}
#search {
  display: flex;
  justify-content: center;
}
.search {
  background: orange;
  height: 50px;
  width: 90vw;
  display: flex;
  justify-content: center;
}
.search-item {
  border-radius: 12px;
}

#user-input {
  background-color: blueviolet;
  width: 80vw;
}

#search-button {
  background-color: blue;
  width: 5vw;
}
</style>
