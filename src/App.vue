<template>
  <h1>Reaction Timer</h1>
  <button
    @click="
      start();
      squareLocation();
    "
    type="button"
    :disabled="isPlaying"
  >
    play
  </button>
  <Results :score="score" v-if="showResult" />
  <Block v-if="isPlaying" :delay="delay" @end="endGame" :x="x" :y="y" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
      x: 0,
      y: 0,
    };
  },
  components: {
    Block,
    Results,
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.isPlaying = false;
      this.score = reactionTime;
      this.showResult = true;
    },
    squareLocation() {
      this.x = Math.floor(Math.random() * window.innerWidth - 100);
      this.y = Math.floor(Math.random() * window.innerHeight - 100);
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
button {
  background-color: #0faf87;
  color: #fff;
  border: none;
  padding: 9px 20px;
  border-radius: 5px;
  font-size: 1.2em;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
