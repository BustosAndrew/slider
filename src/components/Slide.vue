<script setup>
import { ref, watch } from 'vue';

const { src, alt } = defineProps(['src', 'alt']);
const isLoading = ref(true);

function handleImageLoad() {
  isLoading.value = false;
}

function handleImageError() {
  isLoading.value = false;
}

// Show loading state when src changes
watch(
  () => src,
  () => {
    isLoading.value = true;
  },
);
</script>

<template>
  <div class="slide-container">
    <div v-if="isLoading" class="loading">Loading...</div>
    <img
      :src="src"
      :alt="alt"
      @load="handleImageLoad"
      @error="handleImageError"
      :style="{ opacity: isLoading ? 0 : 1 }"
    />
  </div>
</template>

<style scoped>
.slide-container {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.loading {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 1.2rem;
  font-weight: bold;
  z-index: 2;
}

img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transition: opacity 0.3s ease;
}
</style>
