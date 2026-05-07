<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'
import gsap from 'gsap'

const cursor = ref<HTMLElement | null>(null)
const follower = ref<HTMLElement | null>(null)

const onMouseMove = (e: MouseEvent) => {
  gsap.to(cursor.value, {
    x: e.clientX,
    y: e.clientY,
    duration: 0,
  })
  gsap.to(follower.value, {
    x: e.clientX,
    y: e.clientY,
    duration: 0.15,
    ease: 'power2.out',
  })
}

onMounted(() => {
  window.addEventListener('mousemove', onMouseMove)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', onMouseMove)
})
</script>

<template>
  <div ref="cursor" class="fixed w-[10px] h-[10px] bg-accent rounded-full top-0 left-0 pointer-events-none z-[10000] -translate-x-1/2 -translate-y-1/2"></div>
  <div ref="follower" class="fixed w-[40px] h-[40px] border border-accent rounded-full top-0 left-0 pointer-events-none z-[9999] -translate-x-1/2 -translate-y-1/2"></div>
</template>
