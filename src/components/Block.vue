<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props:["delay"],
  data () {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      },10)        
    },
    stopTimer() {
      clearInterval(this.timer)
      console.log(this.reactionTime)
      this.$emit("end",this.reactionTime)
    }
  },
  updated() {
    console.log("component updated")
  },
  unmounted() {
    console.log("component unmounted")
  }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: rgb(81, 161, 88);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
    button {
      background: green;
      color: white;
      padding: 8px 16px;
      font-size: 16px;
      cursor: pointer;
      margin: 10px;
      border: none;
      border-radius: 4px;
    }
    button[disabled] {
      opacity: 0.2;
      cursor: not-allowed;
    }
</style>