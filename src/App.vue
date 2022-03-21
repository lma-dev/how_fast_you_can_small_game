<template>
  <h1>How fast can you catch me?</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <h4 @showBlock="changeText">{{ Text }}</h4>
  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame" />
  </div>
  <div v-if="end">
    <Result :score="score" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      end: false,
      Text: null,
    };
  },
  methods: {
    start() {
      this.Text = "Loading ......";
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
    },
    changeText() {
      this.Text = "Catch Now!!!";
    },
    endGame(score) {
      this.score = score;
      this.isPlaying = false;
      this.end = true;
      this.Text = "";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
