<template>
  <header :class="[
    'fixed w-full z-50 transition-all duration-300 backdrop-blur-md bg-opacity-70',
    isScrolled ? 'bg-transparent py-3 shadow-md' : 'py-8'
  ]">
    <div class="flex justify-between items-center lg:px-12 px-6">
      <!-- LOGO -->
<div class="text-3xl font-bold dark:text-white">
  <a href="#" @click.prevent="scrollToItem('#hero')" class="flex items-center">
    <img :src="logo" class="w-30 h-auto" alt="Logo" />
  </a>
</div>


      <!-- Mobile Toggle -->
      <div class="md:hidden z-30">
        <button class="block focus:outline-none" @click="isMenuOpen = !isMenuOpen">
          <span v-if="isMenuOpen" class="text-5xl text-white">
            <Icon icon="material-symbols:close" />
          </span>
          <span v-else class="text-5xl text-white">
            <Icon icon="material-symbols:menu" />
          </span>
        </button>
      </div>

      <!-- Navigation -->
      <nav :class="[
        'transition-colors duration-300 md:flex md:flex-row md:justify-between md:items-center',
        isDarkMode ? 'text-white' : 'text-cyan-500',
        'md:relative',
        (isMenuOpen || isScrolled) ? 'fixed inset-0 flex flex-col items-center justify-center bg-transparent backdrop-blur-md' : 'hidden md:flex'
      ]">
        <ul class="flex flex-col items-center space-y-5 md:flex-row md:space-x-5 md:space-y-0">
          <li v-for="item in Menu" :key="item.name">
            <a :href="item.link"
              class="block transition ease-linear md:text-lg lg:text-xl font-bold hover:text-indigo-400 dark:hover:text-indigo-300"
              @click="scrollToItem(item.link)">
              {{ item.name }}
            </a>
          </li>
        </ul>

        <!-- Toggle Mode -->
        <button @click="$emit('toggle-dark')" class="text-white ml-6 mt-6 md:mt-0 md:ml-20 z-10"
          aria-label="Toggle Dark Mode">
          <Icon v-if="!isDarkMode" icon="line-md:moon-filled" class="text-4xl text-indigo-950" />
          <Icon v-else icon="line-md:sunny-outline" class="text-4xl text-yellow-400" />
        </button>
      </nav>
    </div>
  </header>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logo from '@/assets/img/logo.png'
import { Icon } from '@iconify/vue'

const props = defineProps({
  isDarkMode: Boolean
})

const isMenuOpen = ref(false)
const isScrolled = ref(false) // indica si nos alejamos de #hero

const Menu = ref([
  { name: 'Conocimientos', link: '#services' },
  { name: 'Tecnologías', link: '#skills' },
  { name: 'Sobre mi', link: '#aboutme' },
  { name: 'Proyectos', link: '#projects' },
  { name: 'Contacto', link: '#contact' },
])

const scrollToItem = (link) => {
  isMenuOpen.value = false;
  const element = document.querySelector(link);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

// Detectar scroll
const handleScroll = () => {
  const hero = document.querySelector('#hero');
  if (!hero) return;
  // Si la parte superior del viewport pasa la altura de hero, comprimimos
  isScrolled.value = window.scrollY > hero.offsetHeight;
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  handleScroll();
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
})
</script>

<style scoped>
nav {
  transition: background-color 0.3s ease;
}
</style>
