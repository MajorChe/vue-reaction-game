<template>
  <p>Reaction time: {{ score }} ms</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null
    };
  },
  mounted() {
    if(this.score < 250) {
      this.rank = "Super fast pace"
    } else if (this.score < 400) {
      this.rank = "fast enough"
    } else {
      this.rank = "slow pace"
    }
  }
};
</script>

<style>
  .rank {
    color: rgb(140, 180, 80);
    font-size: 1.4rem;
    font-weight: bold;
  }
</style>
