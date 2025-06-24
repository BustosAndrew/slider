<script setup>
import { ref } from 'vue';
import Slide from './Slide.vue';
import SlideButton from './SlideButton.vue';

const currentIndex = ref(0);
const slides = ref([
  {
    src: 'https://picsum.photos/id/600/600/400',
    alt: 'Forest',
  },
  {
    src: 'https://picsum.photos/id/100/600/400',
    alt: 'Beach',
  },
  {
    src: 'https://picsum.photos/id/200/600/400',
    alt: 'Yak',
  },
  {
    src: 'https://picsum.photos/id/300/600/400',
    alt: 'Hay',
  },
  {
    src: 'https://picsum.photos/id/400/600/400',
    alt: 'Plants',
  },
  {
    src: 'https://picsum.photos/id/500/600/400',
    alt: 'Building',
  },
]);

function nextSlide() {
  currentIndex.value = (currentIndex.value + 1) % slides.value.length;
}

function prevSlide() {
  currentIndex.value =
    (currentIndex.value - 1 + slides.value.length) % slides.value.length;
}
</script>

<template>
  <div class="carousel">
    <Slide
      v-if="slides[currentIndex]"
      :src="slides[currentIndex].src"
      :alt="slides[currentIndex].alt"
    />
    <div class="controls">
      <SlideButton @click="prevSlide">Previous</SlideButton>
      <SlideButton @click="nextSlide">Next</SlideButton>
    </div>
  </div>
</template>

<style scoped>
.carousel {
  position: relative;
  max-width: 600px;
  max-height: 400px;
  width: 100%;
  height: 100%;
  background-color: black; /* to fill the space when the image is smaller */
}

.controls {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  justify-content: space-between;
  width: 90%;
}
</style>
