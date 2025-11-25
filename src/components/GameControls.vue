<script setup lang="ts">
const emit = defineEmits<{
  (e: 'restarted'): void;
}>();
</script>

<template>
  <div class="game-controls">
    <button @click="emit('restarted')">Restart Game</button>
  </div>
</template>

<style scoped>
.game-controls {
  display: flex;
  justify-content: center;
  padding: 1rem;
}

button {
  padding: 0.5rem 2rem;
  font-size: 1rem;
  border: none;
  border-radius: 4px;
  background: #42b983;
  color: white;
  cursor: pointer;
  font-weight: bold;
}

button:hover {
  background: #369970;
}
</style>
