<template>
  <header class="fixed w-full z-50 bg-white/90 border-b border-gray-100 backdrop-blur-md dark:bg-slate-950/90 dark:border-slate-800">
    <div class="container mx-auto px-6 py-4 flex items-center justify-between">
      <!-- Logo -->
      <div class="flex items-center gap-2 cursor-pointer" @click="scrollToTop">
        <div class="w-10 h-10 gradient-bg rounded-lg flex items-center justify-center text-white shadow-lg">
          <Layers class="w-5 h-5" />
        </div>
        <span class="text-2xl font-extrabold tracking-tighter italic dark:text-white">STEPLINE</span>
      </div>

      <!-- Nav -->
      <nav class="hidden md:flex items-center gap-8 font-semibold text-sm uppercase tracking-wider">
        <a href="#" class="hover:text-blue-600 dark:hover:text-blue-400 transition">Home</a>
        <a href="#about" class="hover:text-blue-600 dark:hover:text-blue-400 transition">About Us</a>
        <a href="#catalog" class="hover:text-blue-600 dark:hover:text-blue-400 transition">Catalog</a>
        <a href="#contact" class="hover:text-blue-600 dark:hover:text-blue-400 transition">Contact</a>
      </nav>

      <!-- Actions -->
      <div class="flex items-center gap-2">
        <!-- Search -->
        <div class="search-container relative flex items-center group">
          <input
            type="text"
            v-model="searchQuery"
            placeholder="Cari model..."
            autocomplete="off"
            class="h-10 bg-gray-100 dark:bg-slate-800 rounded-full text-sm outline-none focus:ring-2 focus:ring-blue-500/50"
            @input="onSearch"
            @blur="hideSearchDelayed"
          >
          <button class="absolute right-0 p-2 text-gray-600 hover:text-blue-600 dark:text-gray-400 dark:hover:text-blue-400 transition">
            <Search class="w-5 h-5" />
          </button>
          <div
            v-if="searchResults.length > 0 && showResults"
            class="absolute top-12 right-0 w-[280px] bg-white dark:bg-slate-900 border border-gray-100 dark:border-slate-800 rounded-2xl shadow-2xl overflow-hidden"
          >
            <div
              v-for="p in searchResults"
              :key="p.id"
              class="flex items-center gap-3 p-3 hover:bg-blue-50 dark:hover:bg-slate-800 cursor-pointer border-b border-gray-50 dark:border-slate-800 last:border-0"
              @mousedown.prevent="selectResult(p.id)"
            >
              <img :src="p.images[0] + '?auto=format&fit=crop&w=100'" class="w-10 h-10 object-contain bg-gray-50 dark:bg-slate-700 rounded-lg">
              <div>
                <p class="text-xs font-black text-blue-600">{{ p.brand }}</p>
                <p class="text-sm font-bold truncate w-40 dark:text-white">{{ p.title }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Theme Toggle -->
        <button @click="$emit('toggle-theme')" class="p-2 text-gray-600 hover:text-blue-600 dark:text-gray-400 dark:hover:text-blue-400 transition">
          <Moon v-if="!isDark" class="w-5 h-5" />
          <Sun v-else class="w-5 h-5" />
        </button>

        <button class="p-2 text-gray-600 hover:text-blue-600 dark:text-gray-400 dark:hover:text-blue-400">
          <ShoppingBag class="w-5 h-5" />
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, computed } from 'vue'
import { Layers, Search, Sun, Moon, ShoppingBag } from 'lucide-vue-next'
import { productsData } from '../data/products.js'

const props = defineProps({
  isDark: Boolean
})

const emit = defineEmits(['toggle-theme', 'open-product'])

const searchQuery = ref('')
const showResults = ref(false)

const searchResults = computed(() => {
  const query = searchQuery.value.toLowerCase().trim()
  if (!query) return []
  return productsData.filter(
    p => p.title.toLowerCase().includes(query) || p.brand.toLowerCase().includes(query)
  )
})

function onSearch() {
  showResults.value = searchQuery.value.trim().length > 0
}

function hideSearchDelayed() {
  setTimeout(() => {
    showResults.value = false
  }, 200)
}

function selectResult(id) {
  emit('open-product', id)
  searchQuery.value = ''
  showResults.value = false
}

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>
