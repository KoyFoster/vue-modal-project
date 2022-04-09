<template>
  <p>Ninja Reaction Timer</p>
  <button @click="start" :disabled="isPlaying">Play</button>
  <RBlock v-if="isPlaying" :delay="delay" />
</template>

<script>
import RBlock from "./components/r-block.vue";
// import RResults from "./components/r-results.vue";

export default {
  name: "App",
  components: { RBlock },
  data() {
    return {
      delay: null,
      isPlaying: false,
    };
  },
  methods: {
    start() {
      if (this.isPlaying) return;
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log("delay:", this.delay);
    },
  },
  computed: {},
};
</script>

<!-- Is global to the entire page, not just this component file -->
<style>
#app,
#header,
.footer {
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
