<script setup lang="ts">
import GameBoard from './components/GameBoard.vue';
import GameControls from './components/GameControls.vue';
import ScorePanel from './components/ScorePanel.vue';
</script>

<template>
  <div id="app">
    <h1>Memory Game</h1>
    <ScorePanel :score1="0" :score2="0" />
    <GameBoard />
    <GameControls />
  </div>
</template>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 2rem;
}

h1 {
  color: #42b983;
  margin-bottom: 2rem;
}
</style>
