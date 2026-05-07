<script setup lang="ts">
import HeroSection from './sections/HeroSection.vue'
import AboutSection from './sections/AboutSection.vue'
import ServicesSection from './sections/ServicesSection.vue'
import TestimonialsSection from './sections/TestimonialsSection.vue'
import ContactSection from './sections/ContactSection.vue'

const emit = defineEmits(['openDetail'])

const handleOpenDetail = (title: string, content: string) => {
  emit('openDetail', title, content)
}
</script>

<template>
  <div class="landing-wrapper">
    <HeroSection />
    <AboutSection @openDetail="handleOpenDetail" />
    <ServicesSection />
    <TestimonialsSection />
    <ContactSection />
  </div>
</template>
