<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const preloader = ref<HTMLElement | null>(null)
const percent = ref(0)

onMounted(() => {
  const tl = gsap.timeline({
    onComplete: () => {
      gsap.to(preloader.value, {
        yPercent: -100,
        duration: 1,
        ease: 'power4.inOut',
        delay: 0.5,
      })
    }
  })

  // Simulate loading
  const obj = { val: 0 }
  tl.to(obj, {
    val: 100,
    duration: 2,
    ease: 'power2.inOut',
    onUpdate: () => {
      percent.value = Math.floor(obj.val)
    }
  })
})
</script>

<template>
  <div ref="preloader" class="fixed inset-0 bg-black z-[20000] flex justify-center items-center text-[#a3ff00] font-sans">
    <div class="text-center w-[300px]">
      <div class="text-2xl tracking-[0.5em] mb-8 font-bold uppercase">NINJA CODER</div>
      <div class="w-full h-[2px] bg-white/10 mb-4 overflow-hidden relative">
        <div class="h-full bg-[#a3ff00] transition-all duration-100 ease-linear" :style="{ width: percent + '%' }"></div>
      </div>
      <div class="text-[0.8rem] font-mono">{{ percent }}%</div>
    </div>
  </div>
</template>
