<script setup>
import 'vue3-carousel/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

const props = defineProps({
  images: Array
})

const config = {
//   height: 500,
  itemsToShow: 1,
  gap: 5,
  mouseWheel: true,
  wrapAround: true,

  breakpointMode: 'carousel',

  // Breakpoints are mobile-first
  // Any settings not specified will fall back to the carousel's default settings
  breakpoints: {
    // 300px and up
    500: {
      itemsToShow: 1,
      snapAlign: 'center',
    },
    // 400px and up
    1000: {
      itemsToShow: 5,
      snapAlign: 'start',
    },
    // 500px and up
    // 500: {
    //   itemsToShow: ,
    // //   snapAlign: 'start',
    // },
  },
}
</script>

<template>
  <Carousel v-bind="config">
    <Slide v-for="image in props.images" :key="image.id">
      <img :src="image.url" alt="image" class=" rounded-lg"/>
    </Slide>

    <template #addons>
      <Navigation />
      <Pagination />
    </template>
  </Carousel>
</template>

<style>
/* :root {
  background-color: #242424;
} */

.carousel {
  --vc-pgn-background-color: rgba(255, 255, 255, 0.7);
  --vc-pgn-active-color: rgba(255, 255, 255, 1);
  --vc-nav-background: rgba(255, 255, 255, 0.7);
  --vc-nav-border-radius: 100%;
}

/* img {
  border-radius: 8px;
  width: 100%;
  height: 100%;
  object-fit: cover;
} */
</style>
