<template>
  <h1>Reaction Timer App</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <p v-if='showResult'>Reaction Time: {{score}}ms</p>
  <Results :result="score" v-if="showResult"/>
</template>

<script>

import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  components: {Block, Results},
  data() {
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
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
  color: #2c3e50;
  margin-top: 60px;
}

button{
  background-color: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  border-radius: 4px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
