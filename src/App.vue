<template>
  <h1>Tapeo :)</h1>
  <button class="btn-start" :disabled="isPlaying" @click="start">Alefa ;)</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <ResultsTime v-if="showResults" :score="score" />
</template>

<script>
import '../src/assets/css/global.css';
import Block from './components/BlockTape.vue';
import ResultsTime from './components/ResultsTime.vue';

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  components: {
    Block,
    ResultsTime
},
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
  color: white;
  margin-top: 60px;
}

.btn-start {
  background-color: rgb(120, 219, 120);
  border: none;
  border-radius: 20px;
  color: white;
  cursor: pointer;
  font-size: 1.2em;
  padding: 12px 20px;
}

.btn-start:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
