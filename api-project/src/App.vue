<template>
  <div id="app">

  <SearchReal class="search-real"></SearchReal>
  <div class="nav"> 
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
  </div>
    <FeaturedPage></FeaturedPage>
  
  </div>
</template>

<script>
import FeaturedPage from "./components/FeaturedPage.vue"
import SearchReal from "./components/SearchReal.vue";

export default {
  name: "App",
  components: { 
    SearchReal,
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

/* #nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
} */

.nav{
  display: flex;
  justify-content: space-around;
}
</style>
