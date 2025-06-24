<script setup>
const { handleClick } = defineProps(['handleClick']);
</script>

<template>
  <button @click="handleClick" class="slide-button">
    <slot> Change Slide </slot>
  </button>
</template>

<style scoped>
.slide-button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  transition: background-color 0.3s ease;
}

.slide-button:hover {
  background-color: rgba(0, 0, 0, 0.1);
}
</style>
