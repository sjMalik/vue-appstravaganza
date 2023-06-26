<template>
  <div id="app" class="container">
    <h1 class="text-center">Player Score Count</h1>
    <div class="card">
      <div class="card-body text-center">
        <h3>Player I</h3>
        <button @click="incrementCounter(player1)" type="button" class="btn btn-success">Up</button>
        <span class="player-score p-2">{{ player1.score }}</span>
        <button @click="decrementCounter(player1)" type="button" class="btn btn-danger">Down</button>
      </div>
      <div class="card-body text-center">
        <h3>Player II</h3>
        <button @click="incrementCounter(player2)" type="button" class="btn btn-success">Up</button>
        <span class="player-score p-2">{{ player2.score }}</span>
        <button @click="decrementCounter(player2)" type="button" class="btn btn-danger">Down</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      player1: {
        score: 0
      },
      player2: {
        score: 0
      }
    }
  },
  methods: {
    incrementCounter(player){
      player.score++;
    },
    decrementCounter(player){
      if(player.score > 0){
        player.score--;
      }
    }
  }
}
</script>

<style scoped>
.player-score {
  font-size: 1.5rem;
}
</style>

