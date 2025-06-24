<script setup>
const emit = defineEmits(['click']);

function handleClick() {
  emit('click');
}
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
  color: black;
  background-color: white;
  border: 1px solid #000;
}
</style>
