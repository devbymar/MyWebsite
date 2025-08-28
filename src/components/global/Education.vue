<template>
    <section class="p-16">
        <header class="text-center">
            <h3 :class="['text-4xl font-bold text-[#1E1A4D]', isDarkMode ? 'text-white' : 'text-[#1E1A4D]']">Formación
            </h3>
        </header>
        <ul class="mt-10 space-y-8">
            <li :class="['w-full rounded-xl shadow-lg border border-white/20 bg-gradient-to-t from-[#00c6cc]/40 via-[#4b6cb7]/40 to-[#1E1A4D]/40', isDarkMode ? 'text-white' : 'text-[#1E1A4D]']" v-for="(item, index) in Education" :key="index">
                <article
                    class="flex flex-col lg:flex-row items-center lg:items-start rounded-[12px] bg-transparent mt-[3px] mx-[3px] p-6 md:p-8 lg:p-10">
                    <figure class="w-full lg:w-1/4 flex justify-center lg:justify-start mb-4 lg:mb-0">
                        <Icon icon="hugeicons:university" class="text-4xl md:text-6xl lg:text-7xl" />
                    </figure>

                    <section class="w-full lg:w-3/4 lg:pl-4 text-center lg:text-left">
                        <header>
                            <h3 class="text-xl md:text-2xl font-semibold uppercase">{{ item.school }}</h3>
                        </header>
                        <p class="text-sm font-semibold md:text-base">{{ item.degree }}</p>
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

const Education = ref([
    { duration: '09/2021-06/2023', school: 'IES Polígono Sur', degree: 'CFGS Desarrollo de aplicaciones web' },
    { duration: '2016', school: 'IAFA', degree: 'Instructor de ajedrez FADA' },
    { duration: '09/2013-06/2015', school: 'IES Salvador Távora', degree: 'CFGS Integración Social' },
    { duration: '09/2011-06/2013', school: 'IES Martinez Montañés', degree: 'Bachillerato' },
])

</script>