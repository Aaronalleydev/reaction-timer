<template>
<LeaderBoard v-if="!isPlaying" :score="score" />
  <h1>Ninja reaction timer</h1>
  <p>The name of the game is simple, click play, as soon as the box appears click on it as fast as you can!</p>
  <button @click="start" @randomPos="randomPos" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/results.vue'
import LeaderBoard from './components/LeaderBoard.vue'

export default {
  name: 'App',
  components: { Block, Result, LeaderBoard },
  data() {
    return {
    isPlaying: false,
    delay: null,
    score: null,
    showResults: false,
    leaderBoard: [0, 0, 0],
    }
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
  },
  updateLeader(score) {
    if(this.score < this.leaderBoard[key].score) {
        this.key.score = this.score
      }
  },
  randomPos(randomX, randomY) {

    randomX = Math.round(Math.random() * 1000)
    randomY = Math.round(Math.random() * 1000)

    // Block.style.top = randomX
    // Block.style.left = randomY

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
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
