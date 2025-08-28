<template>
    <section id="skills" class="relative text-white mt-32">
        <SectionHeader title="Tecnologías" :isDarkMode="isDarkMode" />

                <div
            class="mt-5 py-8 xl:px-16 px-4 sm:py-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3">
            <article v-for="tech in tecnologies" :key="tech.id" class="px-4" data-aos="fade-up"
                :data-aos-delay="tech.id * 100">
                <div
                    class="relative flex flex-col justify-center text-center shadow-md hover:shadow-lg transition-shadow duration-300 rounded-[30px] overflow-hidden">
                    <div class="mt-8 flex justify-center items-center relative">
                        <div class="p-5 flex items-center justify-center">
                            <img :src="tech.icon" :alt="tech.name" class="h-[40px] w-[40px] relative z-[10]" />
                        </div>
                    </div>
                    <div class="p-6">
                        <h3 :class="[
                            'uppercase font-semibold text-base',
                            isDarkMode ? 'text-gray-200' : 'text-[#1E1A4D]'
                        ]">
                            {{ tech.name }}
                        </h3>
                    </div>
                </div>
            </article>
        </div>
    </section>
</template>


<script setup>
import { ref } from 'vue'
import SectionHeader from '../UI/SectionHeader.vue'

import js from '../../assets/icons/javascript.png'
import ts from '../../assets/icons/typescript.png'
import git from '../../assets/icons/git.png'
import html from '../../assets/icons/html.png'
import css from '../../assets/icons/css.png'
import vue from '../../assets/icons/vue.png'
import nuxt from '../../assets/icons/Nuxt.png'
import vite from '../../assets/icons/Vite.png'
import webpack from '../../assets/icons/Webpack.png'
import mas from '../../assets/icons/mas.png'


const props = defineProps({
    isDarkMode: { type: Boolean, required: false }
})

const tecnologies = ref([
    {
        id: 1,
        icon: js,
        name: 'Javascript',
    },
    {
        id: 2,
        icon: ts,
        name: 'Typescript',
    },
    {
        id: 3,
        icon: git,
        name: 'GIT',
    },
    {
        id: 4,
        icon: html,
        name: 'HTML',
    },
    {
        id: 5,
        icon: css,
        name: 'CSS',
    },
    {
        id: 6,
        icon: vue,
        name: 'Vue JS',
    },
    {
        id: 7,
        icon: nuxt,
        name: 'Nuxt',
    },
    {
        id: 8,
        icon: vite,
        name: 'Vite',
    },
    {
        id: 9,
        icon: webpack,
        name: 'Webpack',
    }
])
</script>