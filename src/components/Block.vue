<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Here!!!</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      score: 0,
      timer: null,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.score += 50;
      }, 50);
      this.$emit("showBlock");
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.score);
    },
  },
};
</script>

<style>
.block {
  background-color: aqua;
  width: 400px;
  height: 300px;
  margin: 20px auto;
  padding-top: 30px;
  color: black;
}
</style>
