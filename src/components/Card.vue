<script setup lang="ts">
const props = defineProps<{
  id: number,
  emoji: string,
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