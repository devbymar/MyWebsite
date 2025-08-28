<template>
    <div class="relative">
        <header
            class="absolute z-0 w-1/2 aspect-[16/5] -skew-x-12 rounded-full bg-gradient-to-r from-[#00c6cc] via-[#785ae4] to-[#1E1A4D] opacity-25 blur-[80px] left-10 top-0 hidden md:block">
        </header>

        <header
            class="absolute z-0 w-1/2 aspect-[16/5] -skew-x-12 rounded-full bg-gradient-to-r from-[#00c6cc] via-[#785ae4] to-[#1E1A4D] opacity-25 blur-[80px] right-10 bottom-0 hidden md:block">
        </header>

        <h6 :class="[
            'text-2xl md:text-3xl lg:text-6xl font-bold text-center stroke stroke-text',
            isDarkMode ? ' text-[#A3B3FF]' : 'text-[#00B8DB]'
        ]">
            {{ title }}
        </h6>
    </div>
</template>

<script setup>
const props = defineProps({
    isDarkMode: { type: Boolean, required: false },
    title: { type: String, required: true }
})
</script>