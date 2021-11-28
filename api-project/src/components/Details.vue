<template>
  <div class="details" v-show="detailShowing">
    <h1>these are details</h1>
    <div class="details-container">
      <h1>random text here</h1>
      <h1>{{ title }}</h1>
      <button @click="closeDetails()">close</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Details",
  props: {
    title: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      detailShowing: true,
    };
  },
  methods: {
    closeDetails() {
      this.detailShowing = false;
      location.reload();
    },
  },
};
</script>

<style>
.details-container {
  width: 80%;
  height: 80%;
  background-color: turquoise;
  position: fixed;
  z-index: 1;
  left: 10%;
  top: 10%;
}
</style>
