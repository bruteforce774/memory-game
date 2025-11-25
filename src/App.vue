<script setup lang="ts">
import { ref } from 'vue'
import GameBoard from './components/GameBoard.vue'
import GameControls from './components/GameControls.vue'
import ScorePanel from './components/ScorePanel.vue'

const gameBoardRef = ref<InstanceType<typeof GameBoard> | null>(null)

const score1 = ref(0)
const score2 = ref(0)
const currentPlayer = ref(1)

// Update scores from GameBoard
const updateScores = () => {
  if (gameBoardRef.value) {
    score1.value = gameBoardRef.value.score1
    score2.value = gameBoardRef.value.score2
    currentPlayer.value = gameBoardRef.value.currentPlayer
  }
}

// Handle restart button click
const handleRestart = () => {
  if (gameBoardRef.value) {
    gameBoardRef.value.restartGame()
    updateScores()
  }
}

// Poll for score updates (simple approach)
setInterval(updateScores, 100)
</script>

<template>
  <div id="app">
    <h1>Memory Game</h1>
    <ScorePanel :score1="score1" :score2="score2" />
    <GameBoard ref="gameBoardRef" />
    <GameControls @restarted="handleRestart" />
  </div>
</template>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 2rem;
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

h1 {
  color: white;
  margin-bottom: 2rem;
  font-size: 3rem;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}
</style>
