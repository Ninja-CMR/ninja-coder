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
  <div ref="preloader" class="fixed inset-0 bg-black z-[20000] flex flex-col justify-center items-center text-[#a3ff00] font-sans overflow-hidden">
    <!-- Local Smoke Effect for Preloader -->
    <div class="absolute inset-0 opacity-40 pointer-events-none">
      <svg width="100%" height="100%" class="filter-svg">
        <filter id="preloader-smoke">
          <feTurbulence type="fractalNoise" baseFrequency="0.02" numOctaves="4" seed="5">
            <animate attributeName="seed" from="1" to="100" dur="20s" repeatCount="indefinite" />
          </feTurbulence>
          <feDisplacementMap in="SourceGraphic" scale="80" />
        </filter>
        <rect width="100%" height="100%" fill="#050505" filter="url(#preloader-smoke)" />
      </svg>
    </div>

    <div class="relative z-10 flex flex-col items-center">
      <div class="ninja-icon-container mb-8 relative">
        <img src="/favicon.png" alt="Ninja Coder" class="ninja-icon w-32 h-32 md:w-48 md:h-48 object-contain" />
        <div class="glow-overlay absolute inset-0 rounded-full mix-blend-screen opacity-0"></div>
      </div>
      
      <div class="loader-info text-center w-[300px]">
        <div class="w-full h-[1px] bg-white/5 mb-4 overflow-hidden relative">
          <div class="h-full bg-accent transition-all duration-100 ease-linear shadow-[0_0_10px_#a3ff00]" :style="{ width: percent + '%' }"></div>
        </div>
        <div class="text-[0.7rem] font-mono tracking-widest opacity-50 uppercase">Loading System... {{ percent }}%</div>
      </div>
    </div>

    <div class="absolute bottom-10 left-10 font-mono text-[0.6rem] opacity-20 uppercase tracking-[0.5em] hidden md:block">
      Hostile environment detected // sequence_init
    </div>
  </div>
</template>

<style scoped>
.ninja-icon {
  filter: drop-shadow(0 0 5px rgba(163, 255, 0, 0.2));
  animation: breathe 3s ease-in-out infinite, eye-glow 2s ease-in-out infinite alternate;
}

@keyframes breathe {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

@keyframes eye-glow {
  0% { filter: drop-shadow(0 0 5px rgba(163, 255, 0, 0.3)); }
  100% { filter: drop-shadow(0 0 25px rgba(163, 255, 0, 0.8)); }
}

.filter-svg {
  width: 100%;
  height: 100%;
}
</style>
