<script setup lang="ts">
import { onMounted } from 'vue'
import gsap from 'gsap'
import { Draggable } from 'gsap/Draggable'
import profilePhoto from '../../assets/photo_6043910273250299487_y.jpg'
import stylePhoto from '../../assets/photo_6043910273250299489_y.jpg'

gsap.registerPlugin(Draggable)

const emit = defineEmits(['openDetail'])

onMounted(() => {
  // Only enable draggable on desktop
  if (window.innerWidth > 768) {
    Draggable.create('.panel', {
      bounds: '.interest-section',
      inertia: true,
    })
  }
})
</script>

<template>
  <section class="interest-section min-h-screen w-full relative py-20 md:py-32 overflow-hidden px-6 md:px-8">
    <h2 class="text-center mb-12 text-[clamp(1.8rem,5vw,3.5rem)] font-semibold tracking-tight text-white uppercase italic">Curiosité & Expertise</h2>
    
    <div class="panel-container relative md:absolute md:inset-0 w-full md:h-full pointer-events-none flex flex-col md:block gap-8 items-center">
      <!-- Panel 1: Profile -->
      <div class="panel pointer-events-auto relative md:absolute bg-black/80 backdrop-blur-md border border-white/10 rounded-xl p-5 md:p-6 w-full max-w-[400px] md:w-[250px] shadow-2xl cursor-grab active:cursor-grabbing md:top-[5%] md:left-[10%]" @click="emit('openDetail', 'profile.jpg', '<h2>L\'Art du Détail</h2><p>Je soigne mes sites comme je soigne mon apparence : avec minutie et élégance. Ma vision est de propulser le génie camerounais vers un paroxysme de perfection technologique. Ensemble, redéfinissons les standards.</p>')">
        <div class="panel-header flex justify-between items-center mb-4 border-b border-white/10 pb-2">
          <div class="panel-dots flex gap-1.5 flex-none">
            <div class="dot w-2 h-2 rounded-full bg-[#ff5f56]"></div>
            <div class="dot w-2 h-2 rounded-full bg-[#ffbd2e]"></div>
            <div class="dot w-2 h-2 rounded-full bg-[#27c93f]"></div>
          </div>
          <div class="panel-title text-[0.7rem] md:text-[0.8rem] text-gray-400 font-mono">identite_visuelle.jpg</div>
        </div>
        <div class="panel-content">
          <img :src="profilePhoto" class="w-full rounded-md block mb-2" alt="Meva'a Olivier - Soigné" />
          <p class="text-[0.85rem] text-gray-400 italic">Lien entre élégance et code.</p>
        </div>
      </div>

      <!-- Panel 2: Technical Skills -->
      <div class="panel pointer-events-auto relative md:absolute bg-black/80 backdrop-blur-md border border-white/10 rounded-xl p-5 md:p-6 w-full max-w-[400px] md:w-[320px] shadow-2xl cursor-grab active:cursor-grabbing md:top-[30%] md:left-[42%]" @click="emit('openDetail', 'skills.log', '<h2>Maîtrise Technique</h2><p>Un arsenal technologique complet pour des projets sans limites. Du Front-End créatif au Back-End robuste, chaque couche est optimisée pour la performance.</p>')">
        <div class="panel-header flex justify-between items-center mb-4 border-b border-white/10 pb-2">
          <div class="panel-dots flex gap-1.5 flex-none"><div class="dot w-2 h-2 rounded-full bg-[#ff5f56]"></div><div class="dot w-2 h-2 rounded-full bg-[#ffbd2e]"></div><div class="dot w-2 h-2 rounded-full bg-[#27c93f]"></div></div>
          <div class="panel-title text-[0.7rem] md:text-[0.8rem] text-gray-400 font-mono">competences.log</div>
        </div>
        <div class="panel-content text-gray-300">
          <ul class="text-left space-y-2 text-[0.9rem] md:text-[0.95rem]">
            <li>🚀 <strong class="text-white">Front</strong>: Vue 3, React, GSAP, TS</li>
            <li>⚙️ <strong class="text-white">Back</strong>: Node.js, Python, Firebase</li>
            <li>🎨 <strong class="text-white">Design</strong>: UX/UI, Identité visuelle</li>
            <li>📢 <strong class="text-white">Digital</strong>: Marketing & Stratégie</li>
          </ul>
        </div>
      </div>

      <!-- Panel 3: Bio -->
      <div class="panel pointer-events-auto relative md:absolute bg-black/80 backdrop-blur-md border border-white/10 rounded-xl p-5 md:p-6 w-full max-w-[400px] md:w-[350px] shadow-2xl cursor-grab active:cursor-grabbing md:top-[60%] md:left-[5%]" @click="emit('openDetail', 'vision.md', '<h2>L\'Excellence Africaine</h2><p>Le développement technologique africain va bientôt atteindre son apogée. Je me positionne en tant qu\'architecte de cette ascension, en offrant une expertise locale capable de rivaliser avec les géants mondiaux. Le futur est ici.</p>')">
        <div class="panel-header flex justify-between items-center mb-4 border-b border-white/10 pb-2">
          <div class="panel-dots flex gap-1.5 flex-none"><div class="dot w-2 h-2 rounded-full bg-[#ff5f56]"></div><div class="dot w-2 h-2 rounded-full bg-[#ffbd2e]"></div><div class="dot w-2 h-2 rounded-full bg-[#27c93f]"></div></div>
          <div class="panel-title text-[0.7rem] md:text-[0.8rem] text-gray-400 font-mono">vision_afrique.md</div>
        </div>
        <div class="panel-content text-[0.9rem] md:text-[0.95rem] leading-relaxed text-gray-300">
          <p><strong class="text-white">Ninja Coder</strong> : une mission au service de l'excellence.</p>
          <p class="mt-4">Propulser le génie technologique au-delà de l'imaginable. C'est ma vision, c'est mon engagement.</p>
        </div>
      </div>

      <!-- Panel 4: Passions -->
      <div class="panel pointer-events-auto relative md:absolute bg-black/80 backdrop-blur-md border border-white/10 rounded-xl p-5 md:p-6 w-full max-w-[400px] md:w-[280px] shadow-2xl cursor-grab active:cursor-grabbing md:top-[15%] md:left-[70%]" @click="emit('openDetail', 'passions.log', '<h2>Équilibre & Foi</h2><p>Le code est ma langue, le football mon rythme, et ma foi mon socle inébranlable. C\'est cet équilibre qui nourrit ma créativité débordante.</p>')">
        <div class="panel-header flex justify-between items-center mb-4 border-b border-white/10 pb-2">
          <div class="panel-dots flex gap-1.5 flex-none"><div class="dot w-2 h-2 rounded-full bg-[#ff5f56]"></div><div class="dot w-2 h-2 rounded-full bg-[#ffbd2e]"></div><div class="dot w-2 h-2 rounded-full bg-[#27c93f]"></div></div>
          <div class="panel-title text-[0.7rem] md:text-[0.8rem] text-gray-400 font-mono">univers.log</div>
        </div>
        <div class="panel-content text-[0.9rem] md:text-[0.95rem] leading-relaxed text-gray-300 text-center">
          <img :src="stylePhoto" class="w-full rounded-md mb-4" alt="Ninja Style" />
          <ul class="flex flex-wrap justify-center gap-4 text-[0.8rem]">
            <li>⚽ Football</li>
            <li>💻 Code</li>
            <li>🙏 Foi</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>
