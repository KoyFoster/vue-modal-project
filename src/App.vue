<template>
  <h1>{{ title }}</h1>
  <p>Welcome</p>
  <br />
  <div v-if="showModal">
    <ModalWindow :data="[1, 2, 3]" theme="" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Giveaway!</h1>
      <p>Half price!</p>
    </ModalWindow>
  </div>
  <br />
  <button @click.alt="toggleModal">open modal (alt)</button>
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
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      const nameRef = this.$refs.name;
      console.warn({ nameRef });
      nameRef.classList.add("active");
      nameRef.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
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
