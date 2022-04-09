<template>
  <p v-show="score !== null">Reaction Time: {{ score }}ms</p>
  <p v-show="rank !== null">Rank: {{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja finger";
    } else if (this.score < 400) this.rank = "Rapid reflexes";
    else {
      this.rank = "Snail pace";
    }
  },
  methods: {},
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>