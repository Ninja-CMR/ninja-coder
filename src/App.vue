<script setup lang="ts">
import { ref, onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import Lenis from 'lenis'

import NoiseBg from './components/NoiseBg.vue'
import CustomCursor from './components/CustomCursor.vue'
import Preloader from './components/Preloader.vue'
import DetailView from './components/DetailView.vue'
import Landing from './components/Landing.vue'

gsap.registerPlugin(ScrollTrigger)

const activeDetail = ref<{ title: string, content: string } | null>(null)

const openDetail = (title: string, content: string) => {
  activeDetail.value = { title, content }
}

onMounted(() => {
  // Initialize Lenis
  const lenis = new Lenis()
  lenis.on('scroll', ScrollTrigger.update)
  gsap.ticker.add((time) => {
    lenis.raf(time * 1000)
  })
  gsap.ticker.lagSmoothing(0)

  // Global Background Blobs Animation
  gsap.to('.blob-1', { x: '20vw', y: '10vh', duration: 10, repeat: -1, yoyo: true, ease: 'sine.inOut' })
  gsap.to('.blob-2', { x: '-10vw', y: '-20vh', duration: 15, repeat: -1, yoyo: true, ease: 'sine.inOut' })
  gsap.to('.blob-3', { x: '10vw', y: '15vh', duration: 12, repeat: -1, yoyo: true, ease: 'sine.inOut' })
})
</script>

<template>
  <div class="bg-black text-white selection:bg-accent selection:text-black min-h-screen">
    <Preloader />
    <NoiseBg />
    <CustomCursor />
    
    <DetailView 
      v-if="activeDetail"
      :isOpen="!!activeDetail"
      :title="activeDetail.title"
      :content="activeDetail.content"
      @close="activeDetail = null"
    />

    <div class="bg-blobs fixed inset-0 z-[-1] overflow-hidden pointer-events-none">
      <div class="blob-1 absolute w-[600px] h-[600px] rounded-full bg-[#a3ff00] blur-[150px] opacity-15 top-[-10%] left-[-5%] mix-blend-screen"></div>
      <div class="blob-2 absolute w-[600px] h-[600px] rounded-full bg-[#00f2ff] blur-[150px] opacity-15 bottom-0 right-[-5%] mix-blend-screen"></div>
      <div class="blob-3 absolute w-[400px] h-[400px] rounded-full bg-[#ff00ea] blur-[150px] opacity-15 top-[40%] left-[40%] mix-blend-screen"></div>
    </div>

    <main class="w-full h-full">
      <Landing @openDetail="(title, content) => openDetail(title, content)" />
    </main>
  </div>
</template>

<style>
/* Global overrides if necessary */
body {
  cursor: none;
  overflow-x: hidden;
  background-color: black;
}
</style>
