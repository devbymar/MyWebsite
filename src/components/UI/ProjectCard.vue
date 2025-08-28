<template>
    <article class="['max-w-sm overflow-hidden shadow-lg rounded border border-gray-200', isDarkMode ? 'bg-[#93A8F3]' : 'bg-[#00B8DB]']">
        <figure>
            <img :src="image" alt="title" class="w-full h-48 object-cover">
        </figure>

        <section class="px-6 py-4">
            <header>
                <h3 class="font-bold text-xl mn-2 text-[#245B66]">
                    {{ title }}
                </h3>
            </header>
            <p :class="['text-sm', isDarkMode ? 'text-gray-200' : 'text-[#1E1A4D]']">{{ description }}</p>
        </section>

        <footer class="px-6 pt-4 pb-2">
            <ul class="flex flex-wrap gap-2">
                <li v-for="(tag, index) in tags" :key="index" class="inline-block rounded-full px-3 py-1 text-sm font-semibold text-[#2D4F61]">#{{ tag }}</li>
            </ul>
        </footer>

        <div class="px-6 pb-4 flex justify-between items-center">
            <a :href="liveLink" v-if="liveLink" :class="['font-semibold hover:underline text-sm', isDarkMode ? 'text-[#A3B3FF]' : 'text-cyan-500']" target="_blank" rel="noopener noreferrer">Live Demo</a>
            <a :href="codeLink" v-if="codeLink" :class="['font-semibold hover:underline text-sm', isDarkMode ? 'text-[#A3B3FF]' : 'text-cyan-500']" target="_blank" rel="noopener noreferrer">Ver código</a>
        </div>
    </article>
</template>

<script setup>

const props = defineProps({
    isDarkMode: {type: Boolean, required: true, default: true },
    title: {type: String, required: true, default: 'Project title' },
    description: {type: String, required: true, default: 'Project description' },
    image: {type: String, required: true, default: '/' },
    tags: {type: Array, required: false, default: () => ['Vue.js', 'Tailwind css'] },
    liveLink: { type: String, required: false, default: null },
    codeLink: { type: String, required: false, default: null }
})

</script>