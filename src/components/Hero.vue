<template>
  <section class="relative bg-brand-purple overflow-hidden">
    <div class="container mx-auto px-4 lg:px-8 py-16 md:py-24 lg:py-32">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-16 items-center">
        <!-- Left Column: Text -->
        <div class="text-white space-y-8 order-2 lg:order-1">
          <h1 class="text-4xl md:text-5xl lg:text-6xl xl:text-7xl font-bold leading-tight">
            Software, eCommerce & Automation that ships revenue.
          </h1>
          
          <p class="text-lg md:text-xl text-white/90 leading-relaxed max-w-2xl">
            I design and ship production-ready storefronts, micro-SaaS, and agentic automations. 
            Proven in real-world stacks—without the drama.
          </p>

          <!-- CTAs -->
          <div class="flex flex-col sm:flex-row gap-4">
            <button 
              @click="$emit('open-contact')"
              class="px-8 py-4 bg-white text-brand-purple rounded-lg font-bold text-lg hover:bg-neutral-100 transition-all focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-brand-purple transform hover:scale-105"
            >
              Hire Me
            </button>
            <button 
              @click="$emit('open-contact')"
              class="px-8 py-4 bg-transparent text-white border-2 border-white rounded-lg font-bold text-lg hover:bg-white/10 transition-all focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-brand-purple"
            >
              Book a 15-min Call
            </button>
          </div>

          <!-- Trust Badges -->
          <div class="pt-8 border-t border-white/20">
            <p class="text-sm text-white/70 mb-4 uppercase tracking-wider">Trusted By Teams At</p>
            <div class="flex flex-wrap gap-6 items-center">
              <div 
                v-for="badge in trustBadges" 
                :key="badge"
                class="px-4 py-2 bg-white/10 rounded-lg text-white/80 text-sm font-medium backdrop-blur-sm"
              >
                {{ badge }}
              </div>
            </div>
          </div>
        </div>

        <!-- Right Column: iPad Animation -->
        <div class="order-1 lg:order-2">
          <IPadShowcase :images="showcaseImages" />
        </div>
      </div>
    </div>

    <!-- Decorative gradient -->
    <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-white/10 to-transparent pointer-events-none"></div>
  </section>
</template>

<script setup>
import IPadShowcase from './IPadShowcase.vue'

defineEmits(['open-contact'])

const showcaseImages = [
  '/screens/screen1.jpg',
  '/screens/screen2.jpg',
  '/screens/screen3.jpg',
  '/screens/screen4.jpg'
]

const trustBadges = [
  'Tech Startups',
  'eCommerce',
  'B2B SaaS',
  'Automation'
]
</script>

