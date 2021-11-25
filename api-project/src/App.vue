<template>
  <div id="app">
    <div class="logo">
      <h1 class="logo-text">cosmos</h1>
    </div>
    <SearchReal class="search-real"></SearchReal>
    <FeaturedPage></FeaturedPage>
    <!-- <div class="nav"> 
    <div class="featured">
      <h1>featured</h1>
  <div>
    <h1>ongoing</h1>
    <h1>completed</h1>
  </div>
    </div>
    

    <div class="genre">
    <div>
        <h1>action</h1>
        <h1>romance</h1>
        <h1>comedy</h1>
      </div>
    </div>
  </div> -->
  </div>
</template>

<script>
import FeaturedPage from "./components/FeaturedPage.vue";
import SearchReal from "./components/SearchReal.vue";

export default {
  name: "App",
  components: {
    SearchReal,
    FeaturedPage,
  },
  data() {
    return {};
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Serif:wght@700&display=swap");

:root {
  --main-font: "IBM Plex Serif", serif;
}
#app {
  margin: 0;
  padding: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: rgb(215, 239, 255);
}

.nav {
  display: flex;
  justify-content: space-around;
}

h1 {
  font-family: var(--main-font);
}

.logo {
  background-color: #94b3fd;
  height: 100px;
}
.logo-text {
  color: #99feff;
}
</style>
