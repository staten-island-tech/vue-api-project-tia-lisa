<template>
  <div>
    <input
      type="text"
      id="myInput"
      v-model="userInput"
      v-on:keyup="myFunction"
      placeholder="Search for names.."
    />

    <ul id="myUL">
      <li>Adele</li>
      <li>Chris</li>
      <li>Ben</li>
      <li>Hansum</li>
      <li>OchinChin</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TestingOne",
  data() {
    return {
      userInput: "",
    };
  },
  methods: {
    myFunction() {
      let input = this.userInput;
      console.log(input);
    },
  },
};
</script>
