<template>
  <div class="popular">
    <div class="top-sections">
      <div class="section-click">
        <div class="section">
          <h1 class="section-text" @click="updatePageA">ongoing</h1>
        </div>
        <div class="section">
          <h1 class="section-text" @click="updatePageB">upcoming</h1>
        </div>
      </div>
      <Ongoing name="airing" v-show="showingA"></Ongoing>
      <Completed name="upcoming" v-show="showingB"></Completed>
    </div>
    <!-- <div class="top-sections">
      <div class="ongoing">
        <h1>ongoing</h1>
        
      </div>
      <div class="completed">
        <h1 @click="updatePage">completed</h1>
        
      </div>
    </div> -->
  </div>
</template>

<script>
import Ongoing from "@/components/Ongoing.vue";
import Completed from "../components/Completed.vue";
export default {
  name: "Popular",
  components: {
    Ongoing,
    Completed,
  },
  data() {
    return {
      showingA: true,
      showingB: false,
      // ongoingClick: true,
      // completedClicked: false,
    };
  },
  methods: {
    updatePageB() {
      this.showingB = true;
      this.showingA = false;
    },
    updatePageA() {
      this.showingB = false;
      this.showingA = true;
    },
  },
};
</script>

<style>
.section-click {
  display: flex;
  justify-content: space-around;
}

/* .section {
  background-color: thistle;
} */

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
