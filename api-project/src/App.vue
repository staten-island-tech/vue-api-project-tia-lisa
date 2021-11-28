<template>
  <div id="app">
    <div class="nav">
      <div class="nav-heading">
        <router-link class="router" to="/">
          <h1 class="nav-heading-text">cosmos</h1>
        </router-link>
      </div>

      <div class="sections">
        <div class="nav-section">
          <router-link class="router" to="/popular">
            <h1 class="nav-section-text">popular</h1>
          </router-link>
        </div>
        <div class="nav-section">
          <router-link class="router" to="/genres">
            <h1 class="nav-section-text">genres</h1>
          </router-link>
        </div>
        <div class="nav-section nav-search">
          <SearchReal class="search-real"></SearchReal>
        </div>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
import SearchReal from "./components/SearchReal.vue";

export default {
  name: "App",
  components: {
    SearchReal,
  },
  data() {
    return {};
  },

  methods: {},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Serif:wght@700&display=swap");

:root {
  --main-font: "IBM Plex Serif", serif;
  --first-color: #b983ff;
  --second-color: #94b3fd;
  --third-color: #94daff;
  --fourth-color: #99feff;
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

/* filler home */
.filler-img {
  width: 90vw;
}

/* style nav heading */
.nav-heading {
  height: 70px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  /* background-color: violet; */
}

.nav-heading-text {
  letter-spacing: 15px;
  color: var(--second-color);
  font-size: 35spx;
}

/* style nav sections */
.nav-section {
  width: 300px;
  /* background-color: lightpink; */
}

.nav-section-text {
  font-size: 25px;
  color: var(--first-color);
  font-size: 1.2rem;
  letter-spacing: 3px;
}

/* style nav search */
.nav-search {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 300px;
  z-index: 1;
}

/* style router links */
.router {
  text-decoration: none;
}

.router:hover {
  text-decoration: underline;
  text-decoration-color: var(--second-color);
}
</style>
