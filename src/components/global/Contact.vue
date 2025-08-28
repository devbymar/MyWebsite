<template>
    <section class="mt-32" id="contact">
        <SectionHeader title="Contacto" :isDarkMode="isDarkMode" />

<footer
  class="w-full mt-10 py-12 px-6 transition-colors"
  :class="isDarkMode ? 'text-gray-200' : 'text-gray-900'"
>
  <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8 max-w-6xl mx-auto">
    
    <article
      class="relative flex flex-col justify-center items-center text-center shadow-md hover:shadow-lg transition-shadow duration-300 rounded-[30px] overflow-hidden p-6"
    >
      <figure class="w-12 flex justify-center mb-2">
        <Icon icon="material-symbols:mail-outline" class="text-5xl text-primary" />
      </figure>
      <span>marinaterangallardo@gmail.com</span>
    </article>

    <article
      class="relative flex flex-col justify-center text-center shadow-md hover:shadow-lg transition-shadow duration-300 rounded-[30px] overflow-hidden p-6"
    >
      <a
        href="https://www.linkedin.com/in/marina-terán-gallardo-41b245b9"
        target="_blank"
        class="flex flex-col items-center gap-2 hover:text-primary transition"
      >
        <figure class="w-12 flex justify-center">
          <Icon icon="mdi:linkedin" class="text-5xl text-secondary" />
        </figure>
        <span :class="['underline', isDarkMode ? 'text-[#A3B3FF]' : 'text-cyan-500']">LinkedIn</span>
      </a>
    </article>

    <article
      class="relative flex flex-col justify-center text-center shadow-md hover:shadow-lg transition-shadow duration-300 rounded-[30px] overflow-hidden p-6"
    >
      <a
        href="https://github.com/devbymar"
        target="_blank"
        class="flex flex-col items-center gap-2 hover:text-primary transition"
      >
        <figure class="w-12 flex justify-center">
          <Icon icon="mdi:github" class="text-5xl text-secondary" />
        </figure>
        <span :class="['underline', isDarkMode ? 'text-[#A3B3FF]' : 'text-cyan-500']">GitHub</span>
      </a>
    </article>

  </div>

  <div class="mt-8 flex items-center justify-center gap-2">
    <figure class="w-12 h-12 flex justify-center items-center">
      <img :src="logo" alt="Logo" class="w-12 h-12 object-contain" />
    </figure>
    <span>© {{ currentYear }} devbymar <span class="text-sm text-gray-500 dark:text-gray-400">All rights reserved</span></span>
  </div>
</footer>

    </section>
</template>

<script setup>
import { ref } from 'vue'
import logo from '../../assets/img/logo.png'

import SectionHeader from '../UI/SectionHeader.vue';

const props = defineProps({
    isDarkMode: Boolean
})

const currentYear = new Date().getFullYear()
</script>