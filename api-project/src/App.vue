<template>
  <div id="app">
    <h1>this is lisa's branch</h1>
    <Search></Search>
  </div>
</template>

<script>
import Search from "./components/Search.vue";

export default {
  name: "App",
  components: {
    Search,
  },
  data() {
    return {};
  },
  methods: {},
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
