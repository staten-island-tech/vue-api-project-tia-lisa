<template>
  <div class="footer">
    <h1 class="footer-heading">- {{ description }} -</h1>
    <p class="footer-text">{{ date }} • {{ api }}</p>
    <p class="footer-text">Lisa Li-Liang • Tia Zheng</p>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    description: {
      type: String,
      required: true,
    },
    api: {
      type: String,
      required: true,
    },
    date: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.footer {
  color: var(--first-color);
}

.footer-heading {
  font-size: 25px;
  text-transform: uppercase;
}
</style>
