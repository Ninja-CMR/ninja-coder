<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const props = defineProps<{
  title: string
  content: string
  isOpen: boolean
}>()

const emit = defineEmits(['close'])

const container = ref<HTMLElement | null>(null)

onMounted(() => {
  gsap.from('.detail-header', {
    y: -30,
    opacity: 0,
    duration: 0.6,
    ease: 'power3.out'
  })
  gsap.from('.detail-body', {
    y: 30,
    opacity: 0,
    duration: 0.6,
    delay: 0.1,
    ease: 'power3.out'
  })
})

const close = () => {
  gsap.to(container.value, {
    opacity: 0,
    duration: 0.4,
    onComplete: () => emit('close')
  })
}
</script>

<template>
  <div v-if="isOpen" ref="container" class="fixed inset-0 w-full h-full bg-black/95 backdrop-blur-[20px] z-[15000] flex justify-center items-center p-4 md:p-8">
    <div class="detail-view w-full max-w-[900px] max-h-[90vh] bg-[#111] border border-white/10 rounded-[20px] overflow-hidden shadow-[0_40px_100px_rgba(0,0,0,0.8)] flex flex-col">
      <div class="detail-header bg-[#1a1a1a] px-6 md:px-8 py-4 flex justify-between items-center border-b border-white/10 flex-none">
        <div class="window-controls flex gap-2">
          <div class="dot w-3 h-3 rounded-full bg-[#ff5f56] cursor-pointer" @click="close"></div>
          <div class="dot w-3 h-3 rounded-full bg-[#ffbd2e]"></div>
          <div class="dot w-3 h-3 rounded-full bg-[#27c93f]"></div>
        </div>
        <div class="detail-title font-mono text-gray-500 text-[0.75rem] md:text-[0.9rem] uppercase tracking-wider truncate ml-4">{{ title }}</div>
      </div>
      <div class="detail-body px-6 md:px-12 py-10 md:py-16 text-center overflow-y-auto">
        <div class="detail-content text-gray-300 [&>h2]:text-[clamp(1.5rem,6vw,2.5rem)] [&>h2]:mb-6 [&>h2]:text-accent [&>h2]:font-bold [&>p]:text-[clamp(0.95rem,2vw,1.15rem)] [&>p]:leading-relaxed [&>p]:max-w-[650px] [&>p]:mx-auto [&>p]:mb-8" v-html="content"></div>
        <button class="back-btn bg-transparent border border-accent text-accent px-8 py-3 rounded-full font-semibold cursor-pointer transition-all duration-300 hover:bg-accent hover:text-black uppercase tracking-tight text-sm md:text-base mt-4" @click="close">
          Return to explorer
        </button>
      </div>
    </div>
  </div>
</template>
