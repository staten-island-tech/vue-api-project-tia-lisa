<template>
  <div id="search">
    <!-- this is a form
    <form class="search">
      <input type="text" />
      <input type="button" @click="fetchData" value="submit" />
    </form> -->
    <form class="search">
      <input type="text" class="search-item" id="user-input" />
      <input
        type="button"
        value="submit"
        @click="fetchData"
        class="search-item"
        id="search-button"
      />
    </form>
    <p id="display-here"></p>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      name: "",
    };
  },
  methods: {
    fetchData: async function () {
      try {
        this.name = document.getElementById("user-input").value;
        const response = await fetch(
          `https://api.jikan.moe/v3/search/anime?q=${this.name}`
        );
        const data = await response.json();
        console.log(this.fullLink);
        console.log(data.results[0].synopsis);
        console.log(data.results[0].airing);
        document.getElementById("display-here").innerHTML =
          data.results[0].synopsis;
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
