<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">click me</button>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "[This is a title]",
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
