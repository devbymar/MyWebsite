<template>
    <section id="projects" class="relative w-11/12 px-16 mx-auto">
        <SectionHeader title="Mis Proyectos" :isDarkMode="isDarkMode" />

        <button :class="['swiper-prev absolute top-2/3  left-4 transform -translate-y 1/2 z-10 p-4 rounded-full', isDarkMode ? 'text-gray-200' : 'text-[#1E1A4D]']">
            <Icon icon="line-md:arrow-left" class="font-bold text-3xl" />
        </button>
        <button :class="['swiper-next absolute top-2/3  right-4 transform -translate-y 1/2 z-10 p-4 rounded-full', isDarkMode ? 'text-gray-200' : 'text-[#1E1A4D]']">
            <Icon icon="line-md:arrow-right" class="font-bold text-3xl" />
        </button>

        <swiper :effect="'coverflow'" grabCursor centeredSlides :slidesPerView="'auto'" :coverflowEffect="{rotate: 50, stretch: 0, depth: 100, modifier: 1, slideShadows: true}" pagination :modules="[EffectCoverflow, Navigation]" class="max-w-full mt-32" :navigation="navigationOptions" loop>
            <swiper-slide class="max-w-[300px]" v-for="(project,index) in projects" :key="index">
                <ProjectCard :isDarkMode="isDarkMode" :title="project.title" :description="project.description" :image="project.image" :tags="project.tags" :liveLink="project.liveLink" :codeLink="project.codeLink" />
            </swiper-slide>
        </swiper>
    </section>
</template>

<script setup>
import { ref } from 'vue'

import SectionHeader from '../UI/SectionHeader.vue';
import ProjectCard from '../UI/ProjectCard.vue';

import 'swiper/css'
import 'swiper/css/effect-coverflow'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { EffectCoverflow, Navigation } from 'swiper/modules'

import parallax from '../../assets/img/Parallax.png'
import weatherapp from '../../assets/img/weatherapp.png'
import vuetifyapp from '../../assets/img/vuetifyApp.png'
import rrss from '../../assets/img/rrss.png'
import portfolio from '../../assets/img/portfolio.png'

const props = defineProps({
    isDarkMode: {type: Boolean, required: true, default: true },
})

const navigationOptions = {
    prevEl: '.swiper-prev',
    nextEl: '.swiper-next'
}

const projects = ref([
    {
        title: 'Weather App',
        description: 'Proyecto realizado con Vue, Vite y typescript, que consiste en una aplicación para ver el tiempo en cualquier zona del mundo, consultando una API, un carro de la compra completamente funcional y un Expense tracker.',
        image: weatherapp,
        tags: ['TS', 'Vite', 'Vue.js'],
        liveLink: 'https://shoppingcart-weatherapp.netlify.app/#/about',
        codeLink: 'https://github.com/devbymar/shopping-cart---weather-app.git'
    },
    {
        title: 'RRSS App',
        description: 'Proyecto realizado con Vue 3 (typescript), que muestra un menú con un Porfolio, una red social, una galería de imagenes con diferentes opciones y algunos ejemplos de menú.',
        image: portfolio,
        tags: ['Vue.js', 'Vite', 'TS', 'Tailwind CSS'],
        liveLink: 'https://ts-vite-tailwind.netlify.app/#',
        codeLink: 'https://github.com/devbymar/miscellany.git'
    },
    {
        title: 'Parallax Project',
        description: 'Proyecto realizado integramente con Javascript Vanilla y algunas de sus librerías, HTML y CSS.',
        image: parallax,
        tags: ['JS', 'HTML', 'CSS'],
        liveLink: 'https://parallaxw.netlify.app/',
        codeLink: 'https://github.com/devbymar/parallax.git'
    },
    {
        title: 'Vuetify App',
        description: 'Proyecto realizado con Vuetify, que consiste en un log-in, TODO List, galería de imagenes (carrousel) y algunas cards que hacen uso de ciertas funcionalidades del framework.',
        image: vuetifyapp,
        tags: ['Vuetify', 'Vite', 'Vue.js'],
        liveLink: 'https://vuetifynetlifyapp.netlify.app/',
        codeLink: 'https://github.com/devbymar/vuetify.git'
    }
])
</script>

<style scoped>
.swipper-button-prev,
.swipper-button-next {
    cursor: pointer;
}

.swiper-slide{
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>