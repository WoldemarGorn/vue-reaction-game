<template>
  <h1>Reaction Game</h1>
  <button @click="startPlaing" :disabled="isPlaing">play</button>
  <TargetBlock v-if="isPlaing" :delay="delay" @end="endGame" />
  <Result v-if="isShowScore" :score="score"/>
</template>

<script>

import TargetBlock from './components/TargetBlock.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: { TargetBlock, Result },
  data() {
    return {
      isPlaing: false,
      isShowScore: false,
      delay: null,
      score: 0
    }
  },
  methods: {
    startPlaing() {
      this.isPlaing = !this.isPlaing
      this.delay = 2000 + Math.random() * 5000
      this.isShowScore = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaing = false
      this.isShowScore = true
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
button {
  background: #296e10;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
