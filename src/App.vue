<template>
  <div :class="['min-h-screen transition-colors duration-300', isDark ? 'bg-[#1F1F1F]' : 'bg-gray-200']">
    <NavBar :isDarkMode="isDark" @toggle-dark="toggleDark" />
    <Hero :isDarkMode="isDark" />
    <Counter :isDarkMode="isDark" />
    <Services :isDarkMode="isDark" />
    <Skills :isDarkMode="isDark" />
    <Whyme :isDarkMode="isDark" />
    <Projects :isDarkMode="isDark" />
    <Contact :isDarkMode="isDark" />
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import NavBar from '@/components/global/Navbar.vue'
import Hero from '@/components/global/Hero.vue'
import Counter from '@/components/global/Counter.vue'
import Services from './components/global/Services.vue'
import Skills from './components/global/Skills.vue'
import Whyme from './components/global/Whyme.vue'
import Projects from './components/global/Projects.vue'
import Contact from './components/global/Contact.vue'

const isDark = ref(true)

function toggleDark() {
  isDark.value = !isDark.value
}

watch(isDark, (newVal) => {
  if (newVal) {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
})
</script>
