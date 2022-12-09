<template>
  <h1>Tapeo :)</h1>
  <button class="btn-start" :disabled="isPlaying" @click="start">Alefa ;)</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p v-if="showResults">Reaction time: {{ score }} ms</p>
</template>

<script>
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
  color: #1565b6;
  margin-top: 60px;
}

.btn-start {
  background-color: rgb(120, 219, 120);
  border: none;
  border-radius: 20px;
  color: white;
  font-size: 1.2em;
  padding: 12px 20px;
}

.btn-start:disabled {
  opacity: 0.5;
}
</style>
