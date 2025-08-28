<template>
  <header>
    <div class="flex justify-between items-center p-8 lg:px-12 relative z-20">
      <!-- LOGO -->
      <div class="text-3xl font-bold dark:text-white">
        <img :src="logo" class="w-30 h-auto" alt="Logo" />
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
      <nav
  :class="[
    'transition-colors duration-300',
    'fixed inset-0 z-20 flex flex-col items-center justify-center',
    isDarkMode ? 'bg-[#1F1F1F]' : 'bg-gray-200',
    'md:relative md:flex md:flex-row md:justify-between md:items-center',
    isMenuOpen ? 'block' : 'hidden'
  ]"
>
  <!-- Links -->
  <ul class="flex flex-col items-center space-y-5 md:flex-row md:space-x-5 md:space-y-0">
    <li v-for="item in Menu" :key="item.name">
      <a
        :href="item.link"
        :class="[
          'block transition ease-linear md:text-lg lg:text-xl font-bold hover:text-indigo-400 dark:hover:text-indigo-300',
          isDarkMode ? 'text-white' : 'text-cyan-500'
        ]"
        @click="scrollToItem(item.link)"
      >
        {{ item.name }}
      </a>
    </li>
  </ul>

  <!-- Toggle Mode -->
  <button
    @click="$emit('toggle-dark')"
    class="text-white ml-6 mt-6 md:mt-0 md:ml-20 z-10"
    aria-label="Toggle Dark Mode"
  >
    <Icon
      v-if="!isDarkMode"
      icon="line-md:moon-filled"
      class="text-4xl text-indigo-950"
    />
    <Icon
      v-else
      icon="line-md:sunny-outline"
      class="text-4xl text-yellow-400"
    />
  </button>
</nav>

    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import logo from '@/assets/img/logo.png'
import { Icon } from '@iconify/vue'

const props = defineProps({
  isDarkMode: Boolean
})

const isMenuOpen = ref(false)

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

</script>

<style scoped>
nav {
  transition: background-color 0.3s ease;
}
</style>
