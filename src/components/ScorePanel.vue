<script setup lang="ts">
const props = defineProps<{
  score1: number;
  score2: number;
}>();
</script>

<template>
  <div class="score-panel">
    <div class="score player1">
      <div class="player-name">Player 1</div>
      <div class="player-score">{{ score1 }}</div>
    </div>
    <div class="score player2">
      <div class="player-name">Player 2</div>
      <div class="player-score">{{ score2 }}</div>
    </div>
  </div>
</template>

<style scoped>
.score-panel {
  display: flex;
  gap: 2rem;
  justify-content: center;
  padding: 1rem;
  margin-bottom: 1rem;
}

.score {
  background: white;
  padding: 1rem 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  min-width: 120px;
}

.player-name {
  font-size: 1rem;
  color: #666;
  margin-bottom: 0.5rem;
}

.player-score {
  font-size: 2.5rem;
  font-weight: bold;
  color: #42b983;
}
</style>
