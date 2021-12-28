<template>
<div class="blockContainer">
  <div class="block" :style="{marginTop: randomY + 'px', marginLeft: randomX + 'px'}" v-if="showBlock" @click="stopTimer"> 
    Click Me
  </div>
 </div> 
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null, 
      reactionTime: 0,
      randomX:  Math.round(Math.random() * window.innerWidth),
      randomY: Math.round(Math.random() * window.innerHeight),

    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    },
     
  },
  computed: {
    randomPosition() {
      this.$emit('randomPos', this.randomX, this.randomY)
    }
  }
}
</script>

<style>
  .blockContainer {
    width: 100vw;
    height: 100vh;
    background-color: grey;
  }
  .block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    /* text-align: center; */
    padding: 100px 0;
    float: left;
  }
</style>