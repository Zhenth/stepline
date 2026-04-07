<template>
  <div>
    <AppHeader
      :isDark="isDark"
      @toggle-theme="toggleTheme"
      @open-product="openProduct"
    />

    <HeroSection :isDark="isDark" />

    <AboutSection />

    <CatalogSection @open-product="openProduct" />

    <ProductModal
      :product="selectedProduct"
      :visible="modalVisible"
      @close="closeModal"
    />

    <AppFooter />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { productsData } from './data/products.js'
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import CatalogSection from './components/CatalogSection.vue'
import ProductModal from './components/ProductModal.vue'
import AppFooter from './components/AppFooter.vue'

const isDark = ref(false)
const modalVisible = ref(false)
const selectedProduct = ref(null)

onMounted(() => {
  if (localStorage.getItem('theme') === 'dark') {
    isDark.value = true
    document.documentElement.classList.add('dark')
  }
})

function toggleTheme() {
  isDark.value = !isDark.value
  document.documentElement.classList.toggle('dark', isDark.value)
  localStorage.setItem('theme', isDark.value ? 'dark' : 'light')
}

function openProduct(id) {
  selectedProduct.value = productsData.find(p => p.id === id)
  modalVisible.value = true
  document.body.style.overflow = 'hidden'
}

function closeModal() {
  modalVisible.value = false
  selectedProduct.value = null
  document.body.style.overflow = 'auto'
}
</script>
