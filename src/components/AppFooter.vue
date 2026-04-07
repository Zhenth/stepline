<template>
  <footer id="contact" class="bg-gray-900 text-white py-16 relative dark:bg-black">
    <div class="container mx-auto px-6 grid grid-cols-1 md:grid-cols-4 gap-12">
      <div>
        <div class="flex items-center gap-2 mb-6">
          <div class="w-10 h-10 gradient-bg rounded-lg flex items-center justify-center">
            <Layers class="w-5 h-5" />
          </div>
          <span class="text-2xl font-extrabold tracking-tighter italic">STEPLINE</span>
        </div>
        <p class="text-gray-400 text-sm">Platform katalog sepatu paling transparan.</p>
      </div>
      <div>
        <h4 class="font-bold mb-6 text-xs tracking-widest text-blue-500 uppercase">Contact</h4>
        <p class="text-gray-400 text-sm mb-2">hello@stepline.com</p>
        <p class="text-gray-400 text-sm">+62 895 3369 43182</p>
      </div>
      <div>
        <h4 class="font-bold mb-6 text-xs tracking-widest text-white uppercase">Alamat</h4>
        <p class="text-gray-400 text-sm leading-relaxed">Perum TNI-AL M6/21, Candi, Sidoarjo, Jawa Timur.</p>
      </div>
      <div>
        <h4 class="font-bold mb-6 text-xs tracking-widest text-red-500 uppercase">Ikuti Kami</h4>
        <div class="flex gap-4">
          <a href="https://facebook.com/ari.samsul.9/" target="_blank" rel="noopener noreferrer">
            <Facebook class="w-5 h-5 cursor-pointer hover:text-blue-500 transition" />
          </a>
          <a href="" target="_blank" rel="noopener noreferrer">
            <Instagram class="w-5 h-5 cursor-pointer hover:text-red-500 transition" />
          </a>
          <a href="">
            <Twitter class="w-5 h-5 cursor-pointer hover:text-blue-400 transition" />
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { Layers, Facebook, Instagram, Twitter } from 'lucide-vue-next'
</script>
