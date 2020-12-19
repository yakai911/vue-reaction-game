<template>
  <h1>测试你的反应时间</h1>
  <button @click="start" :disabled="isPlaying">开始测试</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results :score="score" v-if="showResults" />
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results";
export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  -webkit-font-smoothing: antialiased;
  color: #444;
  margin-top: 60px;
}
button {
  background: #0faf97;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
