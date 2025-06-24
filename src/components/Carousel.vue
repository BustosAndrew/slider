<script setup>
import { ref } from 'vue';

const currentIndex = ref(0);
const slides = ref([
  { image: './assets/slide1.jpg', alt: 'Slide 1' },
  { image: './assets/slide2.jpg', alt: 'Slide 2' },
  { image: './assets/slide3.jpg', alt: 'Slide 3' },
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
      :image="slides[currentIndex].image"
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
  width: 100%;
  height: 100%;
}

.controls {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  gap: 1rem;
}
</style>
