<template>
  <div id="search">
    <!-- this is a form
    <form class="search">
      <input type="text" />
      <input type="button" @click="fetchData" value="submit" />
    </form> -->
    <p>search test</p>
    <form class="search">
      <input type="text" id="user-input" />
      <input type="button" value="submit" @click="fetchData" />
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
input {
  background-color: blueviolet;
  width: 200px;
}
</style>
