<template> 
<div class="leaderBoard"> 
<ul>
  <li v-for="(score, key) in leaderBoard" key="key" >
    <p>{{ score.topScore }}</p>
    <p>{{ score.score }}</p>
  </li>
</ul>
</div>

</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
    leaderBoard: [
      {topScore: 'Topscore', score: 10000},
    ]
    }
  }, 
  mounted() { 
      if(this.score < this.leaderBoard[0].score) {
        this.leaderBoard[0].score = this.score
      }
      },
}
</script>

<style scoped>
.leaderBoard {
  padding: 0;
  width: 200px;
  height: 100px;
  border: 1px solid grey;
  border-radius: 5px;
  background: #0faf87;
  color: white;
  text-align: center;
  margin: 40px auto;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
} 
p {
  margin-top: 10px
}
</style>