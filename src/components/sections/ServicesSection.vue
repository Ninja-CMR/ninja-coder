<script setup lang="ts">
import { onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  gsap.from('.desire-text p', {
    scrollTrigger: {
      trigger: '.desire-section',
      start: 'top 80%',
      end: 'top 20%',
      scrub: 1,
    },
    opacity: 0.1,
    stagger: 0.1,
  })
})
</script>

<template>
  <section class="desire-section min-h-screen w-full flex flex-col items-center justify-center py-40 px-8">
    <div class="desire-container max-w-4xl text-center">
      <h2 class="text-accent mb-12 text-[clamp(1.8rem,5vw,3.5rem)] font-semibold tracking-tight uppercase italic">VOTRE VISION, MON IDENTITÉ.</h2>
      <div class="desire-text text-3xl md:text-5xl font-semibold leading-tight text-white">
        <p>Je ne construis pas que des sites.</p>
        <p>Je bâtis des empires numériques.</p>
        <p>Des applications <span class="text-accent">utiles</span>, <span class="text-accent">performantes</span> et <span class="text-accent">uniques</span> au monde.</p>
        <p class="mt-12 text-lg text-gray-500 font-normal">Expert UX/UI Designer & Architecte Logicielle.</p>
      </div>
    </div>
  </section>
</template>
