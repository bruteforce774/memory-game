<script setup lang="ts">
import { ref } from 'vue'
import Card from './Card.vue'

// Create the cards array as internal state
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

// Handle when a card is clicked
function handleCardOpened(id: number) {
  // Game logic will go here later
  console.log('Card opened:', id)
}
</script>

<template>
  <Card v-for="card in cards" :key="card.id" :emoji="card.emoji" :is-open="card.isOpen"
    @opened="handleCardOpened(card.id)" />
</template>