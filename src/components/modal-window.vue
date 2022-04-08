<template>
  <div
    class="backdrop"
    @click.self="handleClickBackdrop"
    v-if="show1stModel || show2ndModel"
  >
    <div class="modal" :class="{ sale: theme === 'sale' }" v-if="show1stModel">
      <!-- Children -->
      <slot>Default Slot</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
    <div class="modal" :class="{ sale: theme === 'sale' }" v-if="show2ndModel">
      <!-- Children -->
      Second Modal
    </div>
  </div>
</template>

<script>
export default {
  props: ["theme", "show1stModel", "show2ndModel"],

  methods: {
    handleClick1stModal() {
      this.$emit("click1stModal");
    },
    handleClick2ndModal() {
      this.$emit("click2ndModal");
    },
    handleClickBackdrop() {
      this.$emit("clickBackdrop");
    },
  },
};
</script>


<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: #12b40c;
  border: none;
  padding: 0px;
}
.modal p {
  font-style: normal;
}
.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
  color: #333;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
.modal.sale {
  background: red;
  color: white;
}
.modal.sale h1 {
  color: white;
}
.modal.sale .actions {
  color: white;
}
.modal.sale .actions a {
  color: white;
}
</style>