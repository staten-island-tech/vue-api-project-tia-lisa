<template>
  <div id="app">
    <!-- title  -->

    <div class="nav">
      <div class="cosmos">
        <router-link to="/">
          <h1 class="nav-heading nav-section-text">cosmos</h1>
        </router-link>
      </div>

      <div class="sections">
        <div class="nav-section">
          <router-link to="/popular">
            <h1 class="nav-section-text">popular</h1>
          </router-link>
        </div>
        <div class="nav-section">
          <router-link to="/genres">
            <h1 class="nav-section-text">genres</h1>
          </router-link>
        </div>
        <div class="nav-section">
          <SearchReal class="search-real"></SearchReal>
        </div>
      </div>
    </div>
    <router-view />

    <FeaturedPage></FeaturedPage>
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
  font-family: var(--main-font);
}

.sections {
  display: flex;
  justify-content: space-around;
}

h1 {
  font-family: var(--main-font);
}

.cosmos {
  background-color: rgb(202, 220, 255);
  height: 100px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
/* .nav-heading{

} */
.nav-section {
  width: 300px;
  background-color: red;
}

.nav-section-text {
  font-size: 25px;
}

router-link {
  text-decoration: none;
}
</style>
