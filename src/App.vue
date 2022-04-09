<template>
  <h1>{{ title }}</h1>
  <p>Welcome</p>
  <br />
  <teleport to="#header" v-if="showModal1">
    <ModalWindow theme="" @close="toggleModal1">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Giveaway!</h1>
      <p>Half price!</p>
    </ModalWindow>
  </teleport>

  <teleport to=".footer" v-if="showModal2">
    <ModalWindow theme="sales" @close="toggleModal2">
      <h1>Coupons!</h1>
      <p>Half price!</p>
    </ModalWindow>
  </teleport>
  <br />

  <button @click.alt="toggleModal2" @click.exact="toggleModal1">
    open modal (alt for modal 2)
  </button>

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
      showModal1: false,
      showModal2: false,
    };
  },
  methods: {
    toggleModal1() {
      this.showModal1 = !this.showModal1;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
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
