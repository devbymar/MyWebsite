<template>
    <section :class="[
        'relative flex justify-center items-center min-h-screen mt-20 lg:mt-0',
        isDarkMode ? 'text-white bg-[#1F1F1F]' : 'text-cyan-500 bg-gray-200'
    ]">
        <header
            class="absolute z-0 w-1/2 aspect-[16/5] -skew-x-12 rounded-full bg-gradient-to-r from-[#00c6cc] via-[#785ae4] to-[#1E1A4D] opacity-25 blur-[80px] left-10 top-0 hidden md:block">
        </header>

        <header
            class="absolute z-0 w-1/2 aspect-[16/5] -skew-x-12 rounded-full bg-gradient-to-r from-[#00c6cc] via-[#785ae4] to-[#1E1A4D] opacity-25 blur-[80px] right-10 bottom-0 hidden md:block">
        </header>

  <main
  class="relative z-10 flex flex-col lg:flex-row justify-between items-center w-full max-w-7xl p-4 lg:p-12"
>
  <!-- TEXTO (alineado a la izquierda en desktop) -->
  <header class="text-center lg:text-left flex-1">
    <h1
      :class="[
        'mb-6 text-2xl md:text-3xl lg:text-4xl font-bold',
        isDarkMode ? '' : 'text-[#1E1A4D]'
      ]"
    >
      Marina Terán Gallardo
      <p
        :class="[
          'stroke-base',
          isDarkMode ? 'stroke-dark' : 'stroke-light'
        ]"
      >
        Front-End Developer
      </p>
    </h1>

    <p
      :class="[
        'max-w-xl mx-auto lg:mx-0 font-semibold',
        isDarkMode ? '' : 'text-[#1E1A4D]'
      ]"
    >
      Soy desarrolladora de aplicaciones web, con experiencia principalmente
      en VueJS (versiones 2 y 3), Quasar framework, javascript, typescript,
      HTML5 y CSS3 y me encanta el diseño web.
    </p>

    <div class="mt-6 flex justify-center lg:justify-start">
      <Button :isDarkMode="isDarkMode" label="Contacto" />
      <a
        href=""
        :class="[
          'font-semibold text-lg w-[10rem] h-[55px] rounded-full ml-2 flex justify-center items-center',
          isDarkMode ? 'text-[#A3B3FF]' : 'bg-gray-200 text-cyan-500'
        ]"
      >
        <Icon icon="line-md:download-loop" class="text-3xl" />
        <span
          :class="['ml-1', isDarkMode ? 'text-gray-200' : 'text-[#1E1A4D]']"
          >CV</span
        >
      </a>
    </div>
  </header>

  <!-- IMAGEN (alineada al final/derecha en desktop) -->
  <aside
    class="container flex justify-center lg:justify-end mt-12 lg:mt-0 flex-1"
  >
    <figure
      :class="[
        'card relative m-[30px] md:w-[420px] md:h-[420px] md:before:w-[450px] md:before:h-[450px] w-[280px] h-[350px] before:w-[300px] before:h:[300px] before:border-[25px]',
        isDarkMode ? 'before:border-[#A3B3FF]' : 'before:border-cyan-500'
      ]"
    >
      <div
        class="relative w-full h-full bg-cover transform translate-x-[25px] translate-y-[30px]"
      >
        <img :src="image" alt="Hero image" class="max-w-1/2" loading="lazy" />
      </div>
    </figure>
  </aside>
</main>


        <svg class="hidden">
            <filter id="wavy1">
                <feTurbulence x="0" y="0" baseFrequency="0.2" numOctaves="5" seed="" />
                <feDisplacementMap in="SourceGraphic" scale="30" />
            </filter>
        </svg>

    </section>
</template>

<script setup>
import Button from '../UI/Button.vue';
import image from '../../assets/img/profile.jpg'
const props = defineProps({
    isDarkMode: Boolean,
})
</script>

<style scoped>
.stroke-base {
    -webkit-text-fill-color: transparent;
}

.stroke-light {
    -webkit-text-stroke-color: #00B8DB;
    -webkit-text-stroke-width: 2px;
}

.stroke-dark {
    -webkit-text-stroke-color: #A3B3FF;
    -webkit-text-stroke-width: 1.4px;
}

.container .card:before{
    content:'';
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    background:transparent;
    width: 250px;
  height: 330px;

}

.container .card:nth-of-type(1)::before{
    filter: url(#wavy1);
}

@media (max-width: 767px) { /* xs y sm */
  .container .card > div {

    transform: none !important;       /* elimina translate-x/y */
    width: 420px !important;          /* mismo ancho que md */
    height: 420px !important;         /* mismo alto que md */
    bottom: 70px;
  }

  .container .card > div img {
    width: 100% !important;           /* ocupa todo el contenedor */
    height: 100% !important;
    object-fit: contain !important;   /* mantiene proporciones */
  }
}




</style>
