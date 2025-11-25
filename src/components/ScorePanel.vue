<script setup lang="ts">
const props = defineProps<{
  score1: number;
  score2: number;
}>();
</script>

<template>
  <div class="score-panel">
    <div class="score">Player 1: {{ score1 }}</div>
    <div class="score">Player 2: {{ score2 }}</div>
  </div>
</template>

<style scoped>
.score-panel {
  display: flex;
  gap: 2rem;
  justify-content: center;
  padding: 1rem;
  font-size: 1.2rem;
  font-weight: bold;
}
</style>
