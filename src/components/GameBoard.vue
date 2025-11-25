<script setup lang="ts">
import { ref } from 'vue'
import Card from './Card.vue'

// Create the cards array as internal state
const cards = ref([
  { id: 1, emoji: '🎈', isOpen: false },
  { id: 2, emoji: '🍎', isOpen: false },
  // ... more cards
])

// Handle when a card is clicked
function handleCardOpened(id: number) {
  // Game logic will go here later
  console.log('Card opened:', id)
}
</script>
