<script setup>
const { image, alt } = defineProps(['image', 'alt']);
</script>

<template>
  <div class="slide">
    <img :src="image" :alt="alt" />
  </div>
</template>

<style scoped>
.slide {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: black; /* to fill the space when the image is smaller */
}

.slide img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}
</style>
