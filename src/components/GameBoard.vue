<script setup lang="ts">
import { ref } from 'vue'
import Card from './Card.vue'

const cards = ref([
  { id: 1, emoji: '🎈', isOpen: false, matched: false },
  { id: 2, emoji: '🍎', isOpen: false, matched: false },
  { id: 3, emoji: '🍋', isOpen: false, matched: false },
  { id: 4, emoji: '🍉', isOpen: false, matched: false },
  { id: 5, emoji: '🍉', isOpen: false, matched: false },
  { id: 6, emoji: '🍇', isOpen: false, matched: false },
  { id: 7, emoji: '🥝', isOpen: false, matched: false },
  { id: 8, emoji: '🍋', isOpen: false, matched: false },
  { id: 9, emoji: '🍎', isOpen: false, matched: false },
  { id: 10, emoji: '🥝', isOpen: false, matched: false},
  { id: 11, emoji: '🍇', isOpen: false, matched: false},
  { id: 12, emoji: '🎈', isOpen: false, matched: false},
])

const cardsOpened = ref(0);

const score = ref(0);

function handleCardOpened(id: number) {
  // Only count unmatched open cards
  const openCards = cards.value.filter(c => c.isOpen && !c.matched)
  
  // TypeScript-safe check: ensure we have exactly 2 cards AND they exist
  if (openCards.length === 2 && openCards[0] && openCards[1]) {
    if (openCards[0].emoji === openCards[1].emoji) {
      // Match! Mark as matched and add to score
      openCards[0].matched = true
      openCards[1].matched = true
      score.value++
    } else {
      // No match - close them
      openCards[0].isOpen = false
      openCards[1].isOpen = false
    }
  }
  
  const card = cards.value.find(c => c.id === id)
  if (card && !card.matched) {
    card.isOpen = true
  }
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
