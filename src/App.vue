<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <BlockTimer :delay="delay" v-if="isPlaying" @end="endGame"/>
  <ResultsTimer  v-if="showResults" :score="score" />
</template>

<script>
import BlockTimer from './components/BlockTimer.vue';
import ResultsTimer from './components/ResultsTimer.vue';

export default {
  name: 'App',
  components: { BlockTimer, ResultsTimer },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.isPlaying = false;
      this.score = reactionTime;
      this.showResults = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 1.2em;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button:disabled {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
