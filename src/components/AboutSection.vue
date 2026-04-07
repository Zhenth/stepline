<template>
  <section id="about" class="py-20 bg-white dark:bg-slate-950 transition-colors">
    <div class="container mx-auto px-6">
      <div class="flex flex-col lg:flex-row items-center gap-16">
        <div class="lg:w-1/2 text-center lg:text-left">
          <h2 class="text-4xl md:text-5xl font-extrabold mb-8 leading-tight dark:text-white">
            Dedikasi Kami Terhadap <br><span class="text-red-600">Kualitas Produk</span>
          </h2>
          <p class="text-gray-600 text-lg mb-6 leading-relaxed dark:text-gray-400">
            StepLine memberikan gambaran yang paling jujur tentang sepatu branded kepada konsumen. Kami percaya setiap butiran material menentukan performa dan kenyamanan Anda.
          </p>
          <div class="grid grid-cols-2 gap-8 mt-10 max-w-sm mx-auto lg:mx-0">
            <div>
              <h4 class="text-3xl font-black text-blue-600 mb-2 italic">100%</h4>
              <p class="text-[10px] font-bold text-gray-400 uppercase tracking-wider dark:text-gray-500">Kualitas Material</p>
            </div>
            <div>
              <h4 class="text-3xl font-black text-red-600 mb-2 italic">100%</h4>
              <p class="text-[10px] font-bold text-gray-400 uppercase tracking-wider dark:text-gray-500">Keaslian Produk</p>
            </div>
          </div>
        </div>
        <div class="lg:w-1/2 grid grid-cols-2 gap-4 hidden sm:grid">
          <div class="space-y-4">
            <img src="https://images.unsplash.com/photo-1552346154-21d32810aba3?auto=format&fit=crop&w=400&q=80" alt="About 1" class="rounded-3xl shadow-lg w-full h-64 object-cover">
            <div class="p-8 bg-blue-600 rounded-3xl text-white">
              <ShieldCheck class="w-10 h-10 mb-4" />
              <h5 class="font-bold text-xl mb-2 italic">Kualitas Terjamin</h5>
              <p class="text-blue-100 text-sm font-medium">Hanya material gred tinggi.</p>
            </div>
          </div>
          <div class="space-y-4 pt-12">
            <div class="p-8 bg-gray-900 rounded-3xl text-white dark:bg-slate-800">
              <Microscope class="w-10 h-10 mb-4 text-red-500" />
              <h5 class="font-bold text-xl mb-2 italic">Analisis Anatomi</h5>
              <p class="text-gray-400 text-sm font-medium">Bedah detail komponen.</p>
            </div>
            <img src="https://images.unsplash.com/photo-1514989940723-e8e51635b782?auto=format&fit=crop&w=400&q=80" alt="About 2" class="rounded-3xl shadow-lg w-full h-64 object-cover">
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ShieldCheck, Microscope } from 'lucide-vue-next'
</script>
