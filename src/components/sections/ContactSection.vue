<script setup lang="ts">
import { onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  gsap.from('.action-btn', {
    scrollTrigger: {
      trigger: '.action-section',
      start: 'top 90%',
    },
    scale: 0.5,
    opacity: 0,
    duration: 1,
    ease: 'back.out(1.7)',
  })
})
</script>

<template>
  <section class="action-section min-h-screen w-full flex flex-col items-center justify-center py-40 px-8">
    <h2 class="text-center mb-12 text-[clamp(2rem,6vw,5rem)] font-semibold tracking-tight text-white uppercase">PRÊT À DEVENIR UNIQUE ?</h2>
    <a href="https://wa.me/2376XXXXXXXXX" target="_blank" class="action-btn inline-block px-16 py-6 bg-accent text-black font-bold text-2xl rounded-full transition-all duration-300 transform hover:scale-105 hover:shadow-[0_0_30px_#a3ff0066]">
      LET'S INNOVATE
    </a>
    
    <div class="social-links mt-16 flex flex-wrap gap-8 justify-center items-center">
      <a href="https://www.facebook.com/share/1Cb7Y1bnzW/" target="_blank" class="hover:text-accent transition-colors">Facebook</a>
      <a href="https://www.instagram.com/oliee__wathkings" target="_blank" class="hover:text-accent transition-colors">Instagram</a>
      <a href="https://www.tiktok.com/@ninja_coder05" target="_blank" class="hover:text-accent transition-colors">TikTok</a>
      <a href="https://www.linkedin.com/in/olivier-mevaa-150391380" target="_blank" class="hover:text-accent transition-colors">LinkedIn</a>
      <a href="https://t.me/ninja_coder" target="_blank" class="text-accent hover:underline font-semibold">Telegram</a>
    </div>

    <div class="footer-info mt-16 text-gray-500 text-sm flex flex-col items-center gap-2">
      <p>Douala, Cameroun</p>
      <p>Local Time {{ new Date().toLocaleTimeString('fr-FR', { hour: '2-digit', minute: '2-digit' }) }}</p>
      <p class="mt-4 opacity-30 text-[0.7rem] uppercase tracking-[0.3em]">Ninja Coder Portfolio © 2026</p>
    </div>
  </section>
</template>
