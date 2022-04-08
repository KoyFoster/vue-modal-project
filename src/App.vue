<template>
  <h1>{{ title }}</h1>
  <ModalWindow :header="header" text="Get thing for half price" :data="[1, 2, 3]" theme="sale" />
  <!-- <input type="text" ref="name" />
  <button @click="handleClick">click me</button> -->
</template>

<script>
// import
import ModalWindow from "./components/modal-window.vue";

export default {
  name: "App",
  components: { ModalWindow },
  data() {
    return {
      title: "[This is a title]",
      header: "Sign up for giveaway",
    };
  },
  methods: {
    handleClick() {
      const nameRef = this.$refs.name;
      console.warn({ nameRef });
      nameRef.classList.add("active");
      nameRef.focus();
    },
  },
  computed: {},
};
</script>

<!-- Is global to the entire page, not just this component file -->
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
