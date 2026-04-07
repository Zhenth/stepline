<template>
  <section id="home" class="hero-banner relative pt-32 pb-12 overflow-hidden dark:bg-slate-950">
    <div class="container mx-auto px-6 flex flex-col md:flex-row items-center relative z-10">
      <div class="md:w-1/2 z-10 text-center md:text-left mb-12 md:mb-0">
        <div class="inline-block px-3 py-1 bg-red-600 text-white text-[10px] font-black rounded mb-4 tracking-widest uppercase shadow-lg">
          Koleksi Eksklusif 2024
        </div>
        <h1 class="text-5xl md:text-7xl font-extrabold leading-tight mb-6">
          Step into <br><span class="gradient-text">Perfection.</span>
        </h1>
        <p class="text-gray-600 text-lg mb-8 max-w-md mx-auto md:mx-0 font-medium dark:text-gray-400">
          Katalog premium dengan rincian material yang jujur. Temukan kenyamanan terbaik untuk setiap langkah Anda.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start">
          <a href="#catalog" class="gradient-bg text-white px-8 py-4 rounded-xl font-bold text-lg shadow-xl hover:opacity-90 transition transform hover:-translate-y-1 text-center">
            Eksplorasi Katalog
          </a>
        </div>
      </div>
      <div class="md:w-1/2 relative flex flex-col items-center">
        <div class="relative z-10 h-[300px] md:h-[400px] flex items-center justify-center">
          <img
            :src="currentImage"
            alt="Hero Shoe"
            class="max-h-full w-auto drop-shadow-2xl hero-image-transition"
            :style="{ opacity: imageOpacity }"
          >
        </div>
        <div class="flex gap-2 mt-8 justify-center z-20">
          <div
            v-for="(_, i) in heroProducts"
            :key="i"
            class="dot-indicator h-2 w-2 rounded-full bg-gray-300"
            :class="{ active: i === heroIdx }"
            @click="goToHero(i)"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { productsData } from '../data/products.js'

defineProps({
  isDark: Boolean
})

const heroProducts = computed(() => productsData.slice(0, 3))
const heroIdx = ref(0)
const imageOpacity = ref(1)

const currentImage = computed(() =>
  heroProducts.value[heroIdx.value].images[0] + '?auto=format&fit=crop&w=1000'
)

let intervalId = null

function goToHero(idx) {
  imageOpacity.value = 0
  setTimeout(() => {
    heroIdx.value = idx
    imageOpacity.value = 1
  }, 400)
}

onMounted(() => {
  intervalId = setInterval(() => {
    goToHero((heroIdx.value + 1) % heroProducts.value.length)
  }, 10000)
})

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId)
})
</script>
