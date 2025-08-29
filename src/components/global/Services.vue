<template>
    <section id="services" class="relative text-white mt-32">

        <SectionHeader title="Conocimientos y aptitudes" :isDarkMode="isDarkMode" />

        <div
            class="mt-5 py-8 xl:px-16 px-4 sm:py-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3">
            <article class="px-[12px] mb-[24px]" v-for="element in services" :key="element.id">
                <div class="mt-[30px] relative flex flex-col justify-center text-center rounded-[30px] "
                    data-aos="fade-up" :data-aos-delay="element.id * 100">
                    <div class="mt-[30px] flex justify-center relative">
                        <div class="mt-[-7px] p-[20px] relative">
                            <img :src="element.icon" alt="services" class="h-[80px] w-[80px] relative z-[1] mx-auto" />
                        </div>
                    </div>
                    <div class="p-[30px]">
                        <h3 :class="[
                            'uppercase font-semibold text-base',
                            isDarkMode ? 'text-[#A3B3FF]' : 'text-[#00B8DB]'
                        ]">
                            {{ element.name }}
                        </h3>
                        <p
                            :class="['text-[14px] leading-[20px] tracking-[0.03rem]', isDarkMode ? 'text-white' : 'text-black']">
                            {{ element.description }}
                        </p>
                    </div>
                </div>
            </article>
        </div>
    </section>
</template>


<script setup>
import { ref } from 'vue'

import SectionHeader from '../UI/SectionHeader.vue'

import development from '../../assets/icons/development.png'
import mobile from '../../assets/icons/telefono-inteligente.png'
import design from '../../assets/icons/diseno-web.png'


const props = defineProps({
    isDarkMode: { type: Boolean, required: false }
})

const services = ref([
    {
        id: 1,
        icon: development,
        name: 'Web development',
        description: 'Creación, desarrollo y mantenimiento de diferentes proyectos web, con diversas tecnologías.'
    },
    {
        id: 2,
        icon: mobile,
        name: 'Mobile app development',
        description: 'Desarrollo de aplicaciones móbiles, principalmente con ionic.'
    },
    {
        id: 3,
        icon: design,
        name: 'Web design',
        description: 'Diseño web con HTML y CSS, Grid y Flex, asi como diversos frameworks: Quasar, Tailwind, Bootstrap...'
    }
])

</script>