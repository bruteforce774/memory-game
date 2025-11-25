<script setup lang="ts">
const props = defineProps<{
  emoji: string;
  isOpen: boolean;
}>();

const emit = defineEmits<{
  (e: 'opened'): void;
}>();
</script>

<template>
  <div
    class="card"
    :class="{ isOpen: props.isOpen }"
    @click="!props.isOpen && emit('opened')"
  >
    <span class="emoji" v-if="props.isOpen">{{ props.emoji }}</span>
    <span v-else>?</span>
  </div>
</template>