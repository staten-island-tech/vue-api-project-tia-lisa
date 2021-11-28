<template>
  <div class="home" id="home">
    <div class="home-one">
      <router-link class="router one-router" to="/popular"
        ><div class="one-heading">
          <h1 class="one-text">browse anime</h1>
        </div>
      </router-link>
    </div>
    <br />

    <div class="home-two">
      <router-link class="router one-router" to="/genres">
        <h1 class="one-text two-text">browse genres</h1>
      </router-link>
      <div class="genre-two">
        <div class="genre genre-a">
          <div class="img-container">
            <div class="img-content">
              <img class="genre-img" src="@/assets/gojo.jpg" alt="" />
            </div>
          </div>

          <div class="z-text">
            <h3>action</h3>
          </div>
        </div>
        <div class="genre genre-b">
          <div class="img-container">
            <div class="img-content">
              <img class="genre-img" src="@/assets/name.jpg" alt="" />>
            </div>
          </div>

          <div class="z-text">
            <h3>romance</h3>
          </div>
        </div>
        <div class="genre genre-c">
          <div class="img-container">
            <div class="img-content">
              <img class="genre-img" src="@/assets/punch.png" alt="" />
            </div>
          </div>
          <div class="z-text">
            <h3>comedy</h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
};
</script>

<style>
/* h1 {
  color: var(--first-color);
  text-transform: uppercase;
} */
h3 {
  color: var(--second-color);
  font-size: 23px;
  letter-spacing: 5px;
}
/* home filler */
.home-one {
  background-image: url("https://images.unsplash.com/photo-1496167117681-944f702be1f4?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2232&q=80");
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.one-heading {
  background-color: rgb(220, 241, 255);
  color: var(--second-color);
  font-size: 25px;
  letter-spacing: 6px;
  text-transform: uppercase;
  width: 600px;
  height: 100px;
  border-radius: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.one-heading:hover {
  background-color: rgb(218, 230, 255);
  cursor: pointer;
  color: var(--first-color);
}

.one-text {
  font-size: 40px;
}

.one-router:hover {
  text-decoration: none;
}

.genre-two {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

.genre-img {
  width: 350px;
  height: 250px;
  border-radius: 10px;
}

.z-text {
  background-color: rgb(255, 230, 255);
  transform: translateY(-20px);
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}

/* zoom */
.img-container {
  overflow: hidden;
  position: relative;
  border-radius: 10px;
}
.img-content {
  transition: all 1s;
}
.img-content:hover {
  transform: scale(1.1);
}

.two-text {
  color: var(--first-color);
  text-transform: uppercase;
  letter-spacing: 4px;
}

.two-text:hover {
  color: var(--second-color);
}
</style>
