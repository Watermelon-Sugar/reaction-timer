<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @ended="gameEnded" />
  <Results v-if="showResult" :score="score"/>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',

  components: { Block , Results },

  data() {
    return {
      isPlaying: false,
      delay: null, 
      score: null,
      showResult: false
    }
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    }, 
    gameEnded(time) {
      this.score = time
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(211, 152, 41);
  margin-top: 60px;
}

button {
  padding: 8px 16px;
  margin: 15px;
  cursor: pointer;
  font-size: 16px;
  letter-spacing: 1.5px;
  border-radius: 10px;
  border: none;
  background: rgb(220, 17, 199);
  color: #ddd;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
