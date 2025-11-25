<script setup lang="ts">
const emit = defineEmits<{
  (e: 'restarted'): void;
}>();
</script>

<template>
  <div class="game-controls">
    <button @click="emit('restarted')">🔄 Restart Game</button>
  </div>
</template>

<style scoped>
.game-controls {
  display: flex;
  justify-content: center;
  padding: 1rem;
}

button {
  padding: 0.75rem 2.5rem;
  font-size: 1.1rem;
  border: none;
  border-radius: 8px;
  background: white;
  color: #42b983;
  cursor: pointer;
  font-weight: bold;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  transition: all 0.3s ease;
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.3);
  background: #f0f0f0;
}

button:active {
  transform: translateY(0);
}
</style>
