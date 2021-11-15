<template>
  <div>
    <!-- this is a form
    <form class="search">
      <input type="text" />
      <input type="button" @click="fetchData" value="submit" />
    </form> -->
    <form class="search">
      <input type="text" id="user-input" />
      <input type="button" value="submit" @click="display" />
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
      targetUrl: " https://api.jikan.moe/v3/search/anime?q=",
    };
  },

  methods: {
    display() {
      this.name = document.getElementById("user-input").value;
      console.log(this.targetUrl + this.name);
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
