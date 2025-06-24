<script setup>
const { src, alt } = defineProps(['src', 'alt']);
</script>

<template>
  <img :src="src" :alt="alt" />
</template>

<style scoped>
img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
</style>
