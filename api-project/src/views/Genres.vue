<template>
  <div class="genres">
    <div class="genre-sections">
      <div class="section-click">
        <div class="section">
          <h1 class="section-text" @click="updatePageA">action</h1>
        </div>
        <div class="section">
          <h1 class="section-text" @click="updatePageB">romance</h1>
        </div>
        <div class="section">
          <h1 class="section-text" @click="updatePageC">comedy</h1>
        </div>
      </div>
      <GenreOne name="action" v-show="showingA"></GenreOne>
      <GenreTwo name="romance" v-show="showingB"></GenreTwo>
      <GenreThree name="comedy" v-show="showingC"></GenreThree>
    </div>

    <!-- <Ongoing name="airing" v-show="showingA"></Ongoing>
      <Completed name="upcoming" v-show="showingB"></Completed> -->
  </div>
</template>

<script>
import GenreOne from "@/components/GenreOne.vue";
import GenreTwo from "@/components/GenreTwo.vue";
import GenreThree from "@/components/GenreThree.vue";
export default {
  name: "Genres",
  components: {
    GenreOne,
    GenreTwo,
    GenreThree,
  },
  data() {
    return {
      showingA: true,
      showingB: false,
      showingC: false,
    };
  },
  methods: {
    updatePageA() {
      this.showingA = true;
      this.showingB = false;
      this.showingC = false;
    },
    updatePageB() {
      this.showingA = false;
      this.showingB = true;
      this.showingC = false;
    },
    updatePageC() {
      this.showingA = false;
      this.showingB = false;
      this.showingC = true;
    },
  },
};
</script>

<style>
.section-click {
  display: flex;
  justify-content: space-around;
}

.section-text {
  font-size: 25px;
  color: var(--second-color);
  font-size: 1.5rem;
  letter-spacing: 3px;
}
.section-text:hover {
  cursor: pointer;
  text-decoration: underline;
  text-decoration-color: var(--second-color);
}
</style>
