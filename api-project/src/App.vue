<template>
  <div id="app">

    <FeaturedPage></FeaturedPage>
  </div>
</template>

<script>
import FeaturedPage from "./components/FeaturedPage.vue"

export default {
  name: "App",
  components: {
    FeaturedPage
  },
  data() {
    return{
        };
  },
}
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
