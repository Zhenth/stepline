<template>
  <section id="catalog" class="py-12 bg-gray-50 dark:bg-slate-900 transition-colors border-t border-gray-100 dark:border-slate-800 overflow-hidden">
    <div class="container mx-auto px-6">
      <div class="flex flex-col md:flex-row justify-between items-end mb-12 gap-6">
        <div>
          <h2 class="text-3xl font-bold mb-2 uppercase tracking-tighter dark:text-white">Premium Collection</h2>
          <p class="text-gray-500 dark:text-gray-400">Jelajahi koleksi material terbaik kami.</p>
        </div>
        <div class="flex gap-2 bg-white p-1.5 rounded-2xl border border-gray-200 shadow-sm overflow-x-auto max-w-full dark:bg-slate-800 dark:border-slate-700">
          <button
            v-for="brand in brands"
            :key="brand"
            @click="filterBrand(brand)"
            class="px-6 py-2 rounded-xl text-sm font-bold transition whitespace-nowrap"
            :class="activeBrand === brand
              ? 'bg-blue-600 text-white shadow-md'
              : 'text-gray-500 hover:bg-gray-100 dark:text-gray-400 dark:hover:bg-slate-700'"
          >
            {{ brandLabels[brand] }}
          </button>
        </div>
      </div>

      <!-- Slider Wrapper -->
      <div class="relative group">
        <!-- Navigation -->
        <button
          @click="scrollCatalog(-1)"
          class="absolute left-0 top-1/2 -translate-y-1/2 -translate-x-4 z-20 w-12 h-12 bg-white dark:bg-slate-800 rounded-full shadow-xl flex items-center justify-center text-gray-800 dark:text-white opacity-0 group-hover:opacity-100 group-hover:translate-x-2 transition-all duration-300 border border-gray-100 dark:border-slate-700"
        >
          <ChevronLeft />
        </button>
        <button
          @click="scrollCatalog(1)"
          class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-4 z-20 w-12 h-12 bg-white dark:bg-slate-800 rounded-full shadow-xl flex items-center justify-center text-gray-800 dark:text-white opacity-0 group-hover:opacity-100 group-hover:-translate-x-2 transition-all duration-300 border border-gray-100 dark:border-slate-700"
        >
          <ChevronRight />
        </button>

        <div ref="productGridRef" class="flex gap-8 overflow-x-auto no-scrollbar scroll-smooth pb-8 px-2">
          <ProductCard
            v-for="product in filteredProducts"
            :key="product.id"
            :product="product"
            @select="(id) => $emit('open-product', id)"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { ChevronLeft, ChevronRight } from 'lucide-vue-next'
import { productsData, brands, brandLabels } from '../data/products.js'
import ProductCard from './ProductCard.vue'

const emit = defineEmits(['open-product'])

const activeBrand = ref('ALL')
const productGridRef = ref(null)

const filteredProducts = computed(() => {
  if (activeBrand.value === 'ALL') return productsData
  return productsData.filter(p => p.brand === activeBrand.value)
})

function filterBrand(brand) {
  activeBrand.value = brand
  if (productGridRef.value) {
    productGridRef.value.scrollTo({ left: 0 })
  }
}

function scrollCatalog(dir) {
  if (productGridRef.value) {
    productGridRef.value.scrollBy({ left: dir * 352, behavior: 'smooth' })
  }
}
</script>
