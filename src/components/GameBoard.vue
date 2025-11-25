<script setup lang="ts">
import { ref, computed } from 'vue'
import Card from './Card.vue'

interface CardType {
  id: number
  emoji: string
  isOpen: boolean
  matched: boolean
}

// Shuffle helper function
function shuffleArray<T>(array: T[]): T[] {
  const shuffled = [...array]
  for (let i = shuffled.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]]
  }
  return shuffled
}

// Initial card setup
const initialCards: CardType[] = [
  { id: 1, emoji: '🎈', isOpen: false, matched: false },
  { id: 2, emoji: '🍎', isOpen: false, matched: false },
  { id: 3, emoji: '🍋', isOpen: false, matched: false },
  { id: 4, emoji: '🍉', isOpen: false, matched: false },
  { id: 5, emoji: '🍉', isOpen: false, matched: false },
  { id: 6, emoji: '🍇', isOpen: false, matched: false },
  { id: 7, emoji: '🥝', isOpen: false, matched: false },
  { id: 8, emoji: '🍋', isOpen: false, matched: false },
  { id: 9, emoji: '🍎', isOpen: false, matched: false },
  { id: 10, emoji: '🥝', isOpen: false, matched: false },
  { id: 11, emoji: '🍇', isOpen: false, matched: false },
  { id: 12, emoji: '🎈', isOpen: false, matched: false },
]

const cards = ref<CardType[]>(shuffleArray([...initialCards]))
const score1 = ref(0)
const score2 = ref(0)
const currentPlayer = ref(1)

// Check if game is finished
const isFinished = computed(() => {
  return cards.value.every(card => card.matched)
})

function handleCardOpened(id: number) {
  const openCards = cards.value.filter(c => c.isOpen && !c.matched)

  if (openCards.length === 2 && openCards[0] && openCards[1]) {
    if (openCards[0].emoji === openCards[1].emoji) {
      // Match! Mark as matched and add to current player's score
      openCards[0].matched = true
      openCards[1].matched = true

      if (currentPlayer.value === 1) {
        score1.value++
      } else {
        score2.value++
      }

      // Keep same player's turn on match
      return
    } else {
      // No match - close them and switch player
      openCards[0].isOpen = false
      openCards[1].isOpen = false
      currentPlayer.value = currentPlayer.value === 1 ? 2 : 1
    }
  }

  const card = cards.value.find(c => c.id === id)
  if (card && !card.matched) {
    card.isOpen = true
  }
}

function restartGame() {
  // Reset all cards and shuffle
  cards.value = shuffleArray([...initialCards].map(card => ({
    ...card,
    isOpen: false,
    matched: false
  })))

  // Reset scores and player
  score1.value = 0
  score2.value = 0
  currentPlayer.value = 1
}

// Expose data and methods to parent
defineExpose({
  restartGame,
  score1,
  score2,
  currentPlayer
})
</script>

<template>
  <div class="game-board-container">
    <div v-if="isFinished" class="game-over">
      <h2>🎉 Game Over! 🎉</h2>
      <p v-if="score1 > score2">Player 1 wins with {{ score1 }} pairs!</p>
      <p v-else-if="score2 > score1">Player 2 wins with {{ score2 }} pairs!</p>
      <p v-else>It's a tie! Both players found {{ score1 }} pairs!</p>
    </div>

    <div class="current-player">
      Current Player: <span class="player-indicator">Player {{ currentPlayer }}</span>
    </div>

    <div class="game-board">
      <Card
        v-for="card in cards"
        :key="card.id"
        :emoji="card.emoji"
        :is-open="card.isOpen"
        @opened="handleCardOpened(card.id)"
      />
    </div>
  </div>
</template>

<style scoped>
.game-board-container {
  position: relative;
}

.current-player {
  text-align: center;
  font-size: 1.2rem;
  font-weight: bold;
  margin-bottom: 1rem;
  color: #333;
}

.player-indicator {
  color: #42b983;
  padding: 0.25rem 0.75rem;
  background: #e3f2fd;
  border-radius: 4px;
}

.game-board {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  padding: 2rem;
  max-width: 400px;
  margin: 0 auto;
}

.game-over {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 2rem 3rem;
  border-radius: 12px;
  box-shadow: 0 8px 24px rgba(0,0,0,0.3);
  text-align: center;
  z-index: 10;
  border: 3px solid #42b983;
}

.game-over h2 {
  margin: 0 0 1rem 0;
  color: #42b983;
  font-size: 2rem;
}

.game-over p {
  font-size: 1.3rem;
  margin: 0;
  color: #333;
  font-weight: bold;
}
</style>
