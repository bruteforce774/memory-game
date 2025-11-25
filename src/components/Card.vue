<script setup lang="ts">
const props = defineProps<{
  emoji: string;
  isOpen: boolean;
}>();

const emit = defineEmits<{
  (e: 'opened'): void;
}>();

const handleClick = () => {
  if (!props.isOpen) {
    emit('opened')
  }
};
</script>

<template>
  <div
    class="card"
    :class="{ isOpen: props.isOpen }"
    @click="handleClick"
  >
    <span class="emoji" v-if="props.isOpen">{{ props.emoji }}</span>
    <span v-else>?</span>
  </div>
</template>

<style scoped>
.card {
  width: 100px;
  height: 100px;
  border: 2px solid #333;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  background: #fff;
  font-size: 2rem;
  transition: transform 0.2s;
}

.card:hover {
  transform: scale(1.05);
}

.card.isOpen {
  background: #e3f2fd;
}
</style>
