<template>
  <a 
    :href="url" 
    target="_blank"
    rel="noopener noreferrer"
    class="group relative block rounded-2xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-brand-purple focus:ring-offset-4"
    :aria-label="`View ${title} project`"
  >
    <div class="aspect-video bg-neutral-200 relative overflow-hidden">
      <!-- Image swap container -->
      <div 
        v-for="(image, index) in images" 
        :key="index"
        class="absolute inset-0 transition-opacity duration-500"
        :style="{ opacity: currentImageIndex === index ? 1 : 0 }"
      >
        <img 
          :src="image" 
          :alt="`${title} screenshot ${index + 1}`"
          class="w-full h-full object-cover"
        />
      </div>

      <!-- Hover overlay -->
      <div class="absolute inset-0 bg-brand-purple/90 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
        <div class="text-center text-white p-6">
          <h3 class="text-2xl font-bold mb-2">{{ title }}</h3>
          <p class="text-white/90 flex items-center justify-center gap-2">
            Open site 
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
            </svg>
          </p>
        </div>
      </div>
    </div>
  </a>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  images: {
    type: Array,
    required: true
  },
  url: {
    type: String,
    required: true
  },
  title: {
    type: String,
    required: true
  },
  swapCount: {
    type: Number,
    default: 3
  },
  swapIntervalMs: {
    type: Number,
    default: 3000
  }
})

const currentImageIndex = ref(0)
const swapsPerformed = ref(0)
let intervalId = null
const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches

onMounted(() => {
  if (prefersReducedMotion || props.images.length <= 1) return

  intervalId = setInterval(() => {
    if (swapsPerformed.value < props.swapCount) {
      currentImageIndex.value = (currentImageIndex.value + 1) % props.images.length
      swapsPerformed.value++
    } else {
      // Stop after swapCount swaps
      clearInterval(intervalId)
    }
  }, props.swapIntervalMs)
})

onUnmounted(() => {
  if (intervalId) {
    clearInterval(intervalId)
  }
})
</script>

