<template>
  <div
    class="product-card flex-shrink-0 w-80 group bg-white dark:bg-slate-800 rounded-3xl p-6 shadow-sm hover:shadow-2xl transition-all duration-500 cursor-pointer overflow-hidden flex flex-col"
    @click="$emit('select', product.id)"
  >
    <div class="relative h-64 flex items-center justify-center bg-gray-50 dark:bg-slate-700 rounded-2xl p-4">
      <img
        :src="product.images[0] + '?auto=format&fit=crop&w=600'"
        :alt="product.title"
        class="max-h-full w-auto transform group-hover:scale-110 transition-all duration-500"
      >
    </div>
    <div class="mt-4 flex flex-col flex-grow">
      <div class="flex items-center gap-3 mb-2">
        <div class="w-8 h-8 rounded-full bg-blue-100 dark:bg-blue-900 flex items-center justify-center text-blue-600 dark:text-blue-300">
          <Zap class="w-4 h-4" />
        </div>
        <span class="bg-blue-600 text-white text-[10px] font-black px-2 py-0.5 rounded tracking-tighter">{{ product.brand }}</span>
        <span class="h-[1px] flex-grow bg-gray-100 dark:bg-slate-700"></span>
      </div>
      <h3 class="font-bold text-lg text-gray-800 dark:text-white group-hover:text-blue-600 truncate">{{ product.title }}</h3>
      <div class="mt-2 flex justify-end">
        <p class="font-extrabold text-xl text-gray-900 dark:text-gray-100 tracking-tighter">{{ product.price }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Zap } from 'lucide-vue-next'

defineProps({
  product: {
    type: Object,
    required: true
  }
})

defineEmits(['select'])
</script>
