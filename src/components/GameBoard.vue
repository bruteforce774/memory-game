<script setup lang="ts">
import { ref } from 'vue'
import Card from './Card.vue'

const cards = ref([
  { id: 1, emoji: '🎈', isOpen: false },
  { id: 2, emoji: '🍎', isOpen: false },
  { id: 3, emoji: '🍋', isOpen: false },
  { id: 4, emoji: '🍓', isOpen: false },
  { id: 5, emoji: '🍉', isOpen: false },
  { id: 6, emoji: '🍇', isOpen: false },
  { id: 7, emoji: '🍒', isOpen: false },
  { id: 8, emoji: '🥝', isOpen: false },
  { id: 9, emoji: '🍌', isOpen: false }
])

function handleCardOpened(id: number) {
  console.log('Card opened:', id)
}
</script>

<template>
  <div class="game-board">
    <Card
      v-for="card in cards"
      :key="card.id"
      :emoji="card.emoji"
      :is-open="card.isOpen"
      @opened="handleCardOpened(card.id)"
    />
  </div>
</template>

<style scoped>
.game-board {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  padding: 2rem;
  max-width: 400px;
  margin: 0 auto;
}
</style>
