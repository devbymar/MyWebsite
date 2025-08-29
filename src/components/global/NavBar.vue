<template>
<!-- HEADER -->
<header :class="[
  'fixed top-0 w-full z-50 transition-all duration-300 backdrop-blur-xl',
  isScrolled 
    ? (isDarkMode ? 'bg-black/40 shadow-md py-3' : 'bg-white/40 shadow-md py-3') 
    : 'py-8'
]">

  <div class="flex flex-col md:flex-row justify-between items-center lg:px-12 px-6">
    <!-- LOGO + Botón menú -->
    <div class="flex w-full justify-between items-center">
      <!-- LOGO -->
      <div :class="['text-3xl font-bold', isDarkMode ? 'text-white' : '']">
        <a href="#" @click.prevent="scrollToItem('#hero')" class="flex items-center">
          <img :src="logo" class="w-30 h-auto" alt="Logo" />
        </a>
      </div>

      <!-- Botón hamburguesa SOLO en móvil -->
      <div class="md:hidden z-30">
        <button class="block focus:outline-none" @click="isMenuOpen = !isMenuOpen">
          <span v-if="isMenuOpen" :class="['text-5xl', isDarkMode ? ' text-white': 'text-[#1E1A4D]']">
            <Icon icon="material-symbols:close" />
          </span>
          <span v-else :class="['text-5xl', isDarkMode ? ' text-white': 'text-[#1E1A4D]']">
            <Icon icon="material-symbols:menu" />
          </span>
        </button>
      </div>
    </div>

    <!-- NAV -->
    <nav :class="[
      'transition-colors duration-300 w-full md:w-auto md:flex md:flex-row md:justify-between md:items-center',
      isDarkMode ? 'text-white' : 'text-cyan-900',
      isMenuOpen ? 'flex flex-col items-center mt-6 space-y-5 md:mt-0 md:space-y-0' : 'hidden md:flex'
    ]">
      <ul class="flex flex-col items-center space-y-5 md:flex-row md:space-x-5 md:space-y-0">
        <li v-for="item in Menu" :key="item.name">
          <a :href="item.link"
  :class="[
    'block whitespace-nowrap transition ease-linear md:text-lg lg:text-xl font-bold',
    isDarkMode ? 'hover:text-indigo-300' : 'hover:text-cyan-500'
  ]"
  @click="scrollToItem(item.link)">
  {{ item.name }}
</a>
        </li>
      </ul>

      <!-- Toggle Dark Mode -->
      <button @click="$emit('toggle-dark')" 
              class="text-white ml-6 mt-6 md:mt-0 md:ml-20 z-10"
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
