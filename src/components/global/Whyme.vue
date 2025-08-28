<template>
    <section id="aboutme" class="mt-32">
        <SectionHeader title="Sobre mi" :isDarkMode="isDarkMode" />
        <div class="grid grid-cols-1 lg:grid-cols-2 p-12 overflow-hidden">
            <Education :isDarkMode="isDarkMode" data-aos="fade-left" />
            <Experience :isDarkMode="isDarkMode" data-aos="fade-right" />
        </div>
    </section>
</template>

<script setup>
import SectionHeader from '../UI/SectionHeader.vue';
import Education from './Education.vue';
import Experience from './Experience.vue';

const props = defineProps({
    isDarkMode: { type: Boolean, required: false }
})
</script>