<template>
    <section class="p-16">
        <header class="text-center">
            <h3 :class="['text-4xl font-bold text-[#1E1A4D]', isDarkMode ? 'text-white' : 'text-[#1E1A4D]']">Experiencia</h3>
        </header>
        <ul class="mt-10 space-y-8 y-8">
            <li :class="['w-full rounded-xl shadow-lg border border-white/20 bg-transparent', isDarkMode ? 'text-white' : 'text-[#1E1A4D]']" v-for="(item,index) in Experience" :key="index">
                <article class="flex flex-col lg:flex-row items-center lg:items-start rounded-[12px] bg-transparent mt-[3px] mx-[3px] p-6 md:p-8 lg:p-10">
                    <figure class="w-full lg:w-1/4 flex justify-center lg:justify-start mb-4 lg:mb-0">
                        <Icon icon="material-symbols-light:work" class="text-4xl md:text-6xl lg:text-7xl" />
                    </figure>

                    <section class="w-full lg:w-3/4 lg:pl-4 text-center lg:text-left">
                        <header>
                            <h3 class="text-xl md:text-2xl font-semibold uppercase">{{ item.title }}</h3>
                        </header>
                        <p class="text-sm font-semibold md:text-base">{{ item.company }}</p>
                        <p class="text-sm md:text-base">{{ item.duration }}</p>
                    </section>
                </article>
            </li>
        </ul>
    </section>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
    isDarkMode: Boolean
})

const Experience = ref([
    { duration: '2023-2025', company: 'Dinamic Area Software', title: 'Desarrollador Frontend' },
    { duration: '2023', company: 'Guadaltel S.A', title: 'Desarrollador Web' },
    { duration: '2016-2017', company: 'Escuela Sevillana de ajedrez', title: 'Profesora de ajedrez' },
    //{ duration: '2018-2021', company: 'Varios', title: 'Empleada de ventas' },
])

</script>