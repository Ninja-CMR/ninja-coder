<script setup lang="ts">
import { onMounted } from 'vue'
import gsap from 'gsap'

onMounted(() => {
  const tl = gsap.timeline({ delay: 2.5 })
  tl.from('.hero-window', {
    scale: 0.8,
    opacity: 0,
    duration: 1.5,
    ease: 'power4.out',
  })
  .from('.hero-line span', {
    y: 100,
    opacity: 0,
    duration: 1.2,
    stagger: 0.2,
    ease: 'power4.out',
  }, "-=1")
  .from('.hero-sub', {
    opacity: 0,
    y: 20,
    duration: 1,
    ease: 'power3.out',
  }, "-=0.5")
})
</script>

<template>
  <section class="min-h-screen w-full flex flex-col items-center justify-center relative overflow-hidden px-4 sm:px-8 py-10 md:py-16">
    <div class="hero-window max-w-[1100px] w-full mx-auto bg-white/5 border border-white/10 rounded-[20px] overflow-hidden backdrop-blur-xl shadow-2xl">
      <div class="panel-header flex justify-between items-center bg-white/5 px-4 md:px-6 py-4 border-b border-white/10">
        <div class="panel-dots flex gap-2">
          <div class="dot w-2.5 h-2.5 md:w-3 md:h-3 rounded-full bg-[#ff5f56]"></div>
          <div class="dot w-2.5 h-2.5 md:w-3 md:h-3 rounded-full bg-[#ffbd2e]"></div>
          <div class="dot w-2.5 h-2.5 md:w-3 md:h-3 rounded-full bg-[#27c93f]"></div>
        </div>
        <div class="panel-title text-[0.7rem] md:text-[0.8rem] text-gray-400 font-mono">ninja_coder.exe</div>
      </div>
      <div class="hero-content py-16 md:py-32 px-6 md:px-12 text-center bg-transparent">
        <div class="hero-line overflow-hidden mb-2">
          <h1 class="text-[clamp(2.5rem,14vw,7rem)] font-bold leading-[0.95] tracking-tighter uppercase text-white">
            <span>Ninja</span>
          </h1>
        </div>
        <div class="hero-line overflow-hidden">
          <h1 class="text-[clamp(2.5rem,14vw,7rem)] font-bold leading-[0.95] tracking-tighter uppercase text-accent">
            <span>Coder</span>
          </h1>
        </div>
        <div class="hero-sub mt-8 md:mt-10 mx-auto max-w-[700px] text-[clamp(0.85rem,2.5vw,1.35rem)] text-gray-400 leading-relaxed font-light px-4">
          Meva'a Olivier • Douala, Cameroun <br/>
          <span class="text-white/60">Je conçois l'identité de marque unique de demain.</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Extra styles for text reveal effect that are hard for pure Tailwind Utility */
.hero-line span {
  display: inline-block;
}
</style>
