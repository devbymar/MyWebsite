<template>
  <button
    @click="onClick"
    class="relative overflow-hidden rounded-full w-[180px] h-[60px] flex justify-center items-center p-[3px]"
  >
    <!-- borde -->
    <div
      :class="['absolute inset-0 rounded-full', isDarkMode ? 'bg-gradient-to-r from-[#00c6cc] via-[#785ae4] to-[#1E1A4D] animate-rotate' : 'bg-gradient-to-r from-[#00eaff] via-cyan-500 to-[#00c6ff] animate-rotate']"
    ></div>

    <!-- contenido interior -->
    <div
      :class="[
        'relative z-10 w-full h-full rounded-full flex justify-center items-center text-lg font-semibold transition-colors duration-300',
        isDarkMode
          ? 'bg-gray-700 text-[#A3B3FF] border border-[#A3B3FF]'
          : 'bg-gray-200 text-[#1E1A4D] border border-cyan-500'
      ]"
    >
      {{ label }}
    </div>
  </button>
</template>

<script setup>
const props = defineProps({
  isDarkMode: { type: Boolean },
  label: { type: String, default: 'Button' },
  onClick: { type: Function, default: () => {} }
})
</script>

<style scoped>
@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.animate-rotate {
  animation: rotate 4s linear infinite;
}
</style>
