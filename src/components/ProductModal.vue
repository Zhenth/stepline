<template>
  <div v-if="visible && product" class="fixed inset-0 z-[60] overflow-y-auto">
    <div class="modal-overlay absolute inset-0 transition-opacity" @click="$emit('close')"></div>
    <div class="relative min-h-screen flex items-center justify-center p-4">
      <div class="bg-white dark:bg-slate-950 w-full max-w-6xl rounded-[40px] shadow-2xl relative overflow-hidden flex flex-col lg:flex-row">
        <!-- Close Button -->
        <button @click="$emit('close')" class="absolute top-6 right-6 z-20 w-10 h-10 bg-gray-100 dark:bg-slate-800 rounded-full flex items-center justify-center hover:bg-gray-200 transition">
          <X />
        </button>

        <!-- Left: Image Gallery -->
        <div class="lg:w-3/5 p-8 lg:p-12 bg-gray-50 border-r border-gray-100 dark:bg-slate-900 dark:border-slate-800">
          <div class="mb-8">
            <h2 class="text-4xl font-extrabold mb-2 uppercase italic dark:text-white">{{ product.title }}</h2>
            <span class="text-blue-500 font-bold uppercase tracking-widest text-sm">{{ product.brand }}</span>
          </div>
          <div class="relative h-[350px] flex items-center justify-center bg-white dark:bg-slate-800 rounded-3xl shadow-inner overflow-hidden">
            <img
              :src="activeImage"
              :alt="product.title"
              class="max-h-[85%] max-w-[85%] drop-shadow-2xl transition-all duration-500"
            >
          </div>
          <div class="mt-8 grid grid-cols-3 gap-2">
            <button
              v-for="(img, i) in product.images"
              :key="i"
              @click="activeAngle = i"
              class="angle-btn p-2 border-2 border-transparent rounded-xl bg-gray-100 dark:bg-slate-800 transition"
              :class="{ active: activeAngle === i }"
            >
              <img :src="img + '?auto=format&fit=crop&w=200'" class="w-full h-12 object-contain">
            </button>
          </div>
        </div>

        <!-- Right: Details -->
        <div class="lg:w-2/5 p-8 lg:p-12">
          <h3 class="text-xl font-bold mb-8 uppercase tracking-tighter dark:text-white border-b border-gray-100 dark:border-slate-800 pb-4">Material Analysis</h3>
          <div class="space-y-8">
            <div>
              <h4 class="text-blue-600 text-xs font-black uppercase mb-1">Toe Box</h4>
              <p class="text-sm font-bold">{{ product.toe }}</p>
            </div>
            <div>
              <h4 class="text-gray-400 text-xs font-black uppercase mb-1">Sole & Outsole</h4>
              <p class="text-sm font-bold">{{ product.sole }}</p>
            </div>
          </div>
          <div class="mt-12 pt-8 border-t border-gray-100 dark:border-slate-800">
            <p class="text-3xl font-black italic mb-6 dark:text-white">{{ product.price }}</p>
            <button class="w-full gradient-bg text-white py-5 rounded-2xl font-extrabold text-lg shadow-lg hover:opacity-90 transition flex items-center justify-center gap-3">
              BELI SEKARANG <ArrowRight />
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, computed } from 'vue'
import { X, ArrowRight } from 'lucide-vue-next'

const props = defineProps({
  product: Object,
  visible: Boolean
})

defineEmits(['close'])

const activeAngle = ref(0)

const activeImage = computed(() => {
  if (!props.product) return ''
  return props.product.images[activeAngle.value] + '?auto=format&fit=crop&w=1000'
})

// Reset angle when product changes
watch(() => props.product, () => {
  activeAngle.value = 0
})
</script>
