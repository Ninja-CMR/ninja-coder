<script setup lang="ts">
// Smoke Atmosphere Component
// Uses SVG filters to create a dynamic, subtle fog/smoke effect
</script>

<template>
  <div class="smoke-container pointer-events-none fixed inset-0 z-[9997] opacity-20">
    <svg width="100%" height="100%" class="filter-svg">
      <filter id="smoke-filter">
        <feTurbulence type="fractalNoise" baseFrequency="0.015" numOctaves="3" seed="1">
          <animate attributeName="seed" from="1" to="100" dur="60s" repeatCount="indefinite" />
        </feTurbulence>
        <feDisplacementMap in="SourceGraphic" scale="50" />
      </filter>
      <rect width="100%" height="100%" fill="#0a0a0a" filter="url(#smoke-filter)" />
    </svg>
  </div>
</template>

<style scoped>
.smoke-container {
  mix-blend-mode: screen;
  filter: blur(4px);
}

.filter-svg {
  width: 100vw;
  height: 100vh;
}
</style>
