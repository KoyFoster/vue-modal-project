<template>
  <div ref="block" class="outline" @click="handleClick">
    {{
      showBlock
        ? "Click me"
        : reactionTime === null
        ? "|"
        : "Click to play again"
    }}
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: null,
      running: false,
    };
  },
  mounted() {
    // start delay on mount
    this.start();
  },
  methods: {
    start() {
      if (this.running) return;
      this.running = true;

      console.warn("start");
      clearInterval(this.timer);
      this.timer = null;
      this.showBlock = false;
      this.reactionTime = null;
      this.$emit("gameEnd", this.reactionTime);

      this.$refs.block.classList.remove("block");
      this.$refs.block.classList.remove("clicked");

      setTimeout(() => {
        this.showBlock = true;
        this.startTimer();
      }, this.delay);
    },

    startTimer() {
      this.$refs.block.classList.add("block");

      this.reactionTime = 0;
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },

    handleClick() {
      // don't run when not shown
      if (!this.showBlock) {
        this.start();
      } else {
        this.stopTimer();
      }
    },

    stopTimer() {
      clearInterval(this.timer);
      this.timer = null;
      this.$emit("gameEnd", this.reactionTime);
      this.showBlock = false;

      this.$refs.block.classList.remove("block");
      this.$refs.block.classList.add("clicked");
      this.running = false;
    },
  },
};
</script>

<style>
.block {
  background: #0faf87;
}
.outline {
  width: 400px;
  border-radius: 20px;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
  border-color: #036b51;
  border-width: 4px;
  border-style: dashed;
}
.clicked {
  background: #036b51;
}
</style>
