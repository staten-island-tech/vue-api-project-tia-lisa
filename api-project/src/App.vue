<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      <h1 @click="fetchData">this is lisa's branchcd</h1>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      anime: [],
    };
  },
  methods: {
    fetchData: async function () {
      try {
        const response = await fetch(
          " https://api.jikan.moe/v3/search/anime?q=naruto"
        );
        const data = await response.json();
        this.anime = data.results;
        console.log("link works");
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
