<script setup lang="ts">
</script>

<template>
  <section class="testimonials-section min-h-screen w-full flex flex-col items-center justify-center py-32 px-8 overflow-hidden relative">

    <h2 class="text-center mb-12 text-[clamp(2rem,6vw,5rem)] font-semibold tracking-tight text-white uppercase">CONFIANCE & RÉSULTATS</h2>
    <div class="testimonials-grid grid grid-cols-1 md:grid-cols-3 gap-8 w-full max-w-6xl">
      <div class="testimonial-card bg-white/5 border border-white/10 p-10 rounded-[20px] transition-all duration-300 hover:-translate-y-2 hover:border-accent">
        <p class="quote text-[1.1rem] leading-relaxed mb-8 italic text-gray-300">"Ninja Coder a transformé notre vision en une plateforme ultra-performante. Son approche du design est unique au monde."</p>
        <div class="author flex items-center gap-4">
          <div class="author-info text-left">
            <div class="author-name font-semibold text-accent">Alex MBIA</div>
            <div class="author-role text-[0.85rem] text-gray-500">CEO, TechAfrica</div>
          </div>
        </div>
      </div>
      <div class="testimonial-card bg-white/5 border border-white/10 p-10 rounded-[20px] transition-all duration-300 hover:-translate-y-2 hover:border-accent">
        <p class="quote text-[1.1rem] leading-relaxed mb-8 italic text-gray-300">"Une expertise rare qui allie marketing et code pur. Olivier ne livre pas juste un site, il livre une identité de marque."</p>
        <div class="author flex items-center gap-4">
          <div class="author-info text-left">
            <div class="author-name font-semibold text-accent">Sarah E.</div>
            <div class="author-role text-[0.85rem] text-gray-500">Directrice Marketing</div>
          </div>
        </div>
      </div>
      <div class="testimonial-card bg-white/5 border border-white/10 p-10 rounded-[20px] transition-all duration-300 hover:-translate-y-2 hover:border-accent">
        <p class="quote text-[1.1rem] leading-relaxed mb-8 italic text-gray-300">"Le Ninja Coder est l'architecte dont nous avions besoin. Rapide, précis et avec une vision artistique exceptionnelle."</p>
        <div class="author flex items-center gap-4">
          <div class="author-info text-left">
            <div class="author-name font-semibold text-accent">David L.</div>
            <div class="author-role text-[0.85rem] text-gray-500">Founder, Startup Hub</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
