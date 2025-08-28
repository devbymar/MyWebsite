<template>
    <section :class="['mt-20 lg:mt-0 w-full relative flex justify-center', isDarkMode ? 'text-white' : 'text-dark']">
        <header
            class="absolute z-0 w-1/2 aspect-[16/5] -skew-x-12 rounded-full bg-gradient-to-r from-[#00c6cc] via-[#785ae4] to-[#1E1A4D] opacity-25 blur-[80px] left-10 top-0 hidden md:block">
        </header>

        <header
            class="absolute z-0 w-1/2 aspect-[16/5] -skew-x-12 rounded-full bg-gradient-to-r from-[#00c6cc] via-[#785ae4] to-[#1E1A4D] opacity-25 blur-[80px] right-10 bottom-0 hidden md:block">
        </header>

        <ul ref="statsSection" 
        :class="['relative z-1 p-6 mx-auto w-11/12 lg:mx-0 rounded-3xl border shadow-lg md:divide-x grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-8 lg:gap-12 border-gray-200', isDarkMode ? 'text-white bg-[#1F1F1F]' : 'text-cyan-500 bg-gray-200 divide-gray-200']">
            <li class="text-center" v-for="element in numbers" :key="element.id">
                <h2 class="font-semibold flex justify-center text-xl sm:text-2xl md:text-4xl w-full">
                    + <Countup v-if="hasIntersected" :endVal="element.number" />
                </h2>
                <p class="mt-2">{{ element.title }}</p>
            </li>
        </ul>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
    isDarkMode: Boolean,
})

const numbers = ref([
    { 
        id: 1,
        number: 15,
        title: 'Proyectos creados'
    },
    { 
        id: 2,
        number: 30,
        title: 'Proyectos'
    },
    { 
        id: 3,
        number: 2,
        title: 'Años de experiencia'
    },
    { 
        id: 4,
        number: 50,
        title: 'Tecnologías'
    }
])

const statsSection = ref(null)
const hasIntersected = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry])=>{
        if(entry.isIntersecting){
            hasIntersected.value=true
            observer.disconnect()
        }
    },
    {threshold: 0.5}
  )

  if(statsSection.value){
    observer.observe(statsSection.value)
  }
})
</script>