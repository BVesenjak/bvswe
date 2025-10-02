<template>
  <transition
    appear
    @before-enter="onBeforeEnter"
    @enter="onEnter"
  >
    <div 
      class="ipad-container"
      :style="{ perspective: '1500px' }"
    >
      <div 
        class="ipad-device"
        :style="{
          transform: 'rotateY(-8deg) rotateX(2deg)',
          transformStyle: 'preserve-3d',
        }"
      >
        <!-- iPad Frame -->
        <div class="relative bg-neutral-900 rounded-2xl md:rounded-3xl p-3 md:p-4 shadow-2xl">
          <!-- Inner screen bezel -->
          <div class="relative bg-black rounded-xl md:rounded-2xl overflow-hidden" style="aspect-ratio: 3/4;">
            <!-- Screen content -->
            <div 
              ref="screenRef"
              class="screen-content absolute inset-0 bg-white"
              :style="{ transform: `translateY(${scrollOffset}%)` }"
            >
              <div 
                v-for="(image, index) in images" 
                :key="index"
                class="screen-image absolute inset-0 transition-opacity duration-500"
                :style="{ 
                  opacity: activeImageIndex === index ? 1 : 0,
                  pointerEvents: 'none'
                }"
              >
                <img 
                  :src="image" 
                  :alt="`Screenshot ${index + 1}`"
                  class="w-full h-full object-cover"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  images: {
    type: Array,
    required: true,
    default: () => ['/screens/screen1.jpg', '/screens/screen2.jpg', '/screens/screen3.jpg', '/screens/screen4.jpg']
  },
  scrollPauseMs: {
    type: Number,
    default: 1000
  },
  scrollDurationMs: {
    type: Number,
    default: 100
  },
  scrollStepPercent: {
    type: Number,
    default: 50
  }
})

const screenRef = ref(null)
const scrollOffset = ref(0)
const activeImageIndex = ref(0)
let animationId = null
let timeoutId = null
const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches

// Slide-in animation
const onBeforeEnter = (el) => {
  if (!prefersReducedMotion) {
    el.style.opacity = '0'
    el.style.transform = 'translateX(-40px)'
  }
}

const onEnter = (el, done) => {
  if (prefersReducedMotion) {
    done()
    return
  }
  
  const animation = el.animate([
    { opacity: '0', transform: 'translateX(-40px)' },
    { opacity: '1', transform: 'translateX(0)' }
  ], {
    duration: 800,
    easing: 'cubic-bezier(0.16, 1, 0.3, 1)',
    fill: 'forwards'
  })
  
  animation.onfinish = done
}

// Scroll loop animation
const startScrollAnimation = () => {
  if (prefersReducedMotion) return

  let state = 'idle'
  let stateStartTime = Date.now()
  let scrollStartOffset = 0
  let scrollTargetOffset = 0
  const maxScroll = props.scrollStepPercent * 3 // Total of 4 images, scroll 3 times

  const animate = () => {
    const now = Date.now()
    const elapsed = now - stateStartTime

    if (state === 'idle') {
      if (elapsed >= props.scrollPauseMs) {
        // Start scrolling
        state = 'scrolling'
        stateStartTime = now
        scrollStartOffset = scrollOffset.value
        scrollTargetOffset = scrollOffset.value + props.scrollStepPercent
        
        // Loop back to start
        if (scrollTargetOffset >= maxScroll + props.scrollStepPercent) {
          scrollTargetOffset = 0
          scrollStartOffset = maxScroll
          scrollOffset.value = maxScroll
        }
      }
    } else if (state === 'scrolling') {
      const progress = Math.min(elapsed / props.scrollDurationMs, 1)
      const eased = 1 - Math.pow(1 - progress, 3) // ease-out cubic
      
      scrollOffset.value = scrollStartOffset + (scrollTargetOffset - scrollStartOffset) * eased

      if (progress >= 1) {
        // Scrolling complete, back to idle
        state = 'idle'
        stateStartTime = now
        
        // Update active image based on scroll position
        const imageIndex = Math.round(scrollOffset.value / props.scrollStepPercent) % props.images.length
        activeImageIndex.value = imageIndex
      }
    }

    animationId = requestAnimationFrame(animate)
  }

  animationId = requestAnimationFrame(animate)
}

onMounted(() => {
  // Start scroll animation after a short delay
  timeoutId = setTimeout(() => {
    startScrollAnimation()
  }, 500)
})

onUnmounted(() => {
  if (animationId) {
    cancelAnimationFrame(animationId)
  }
  if (timeoutId) {
    clearTimeout(timeoutId)
  }
})
</script>

<style scoped>
.ipad-container {
  width: 100%;
  max-width: 400px;
  margin: 0 auto;
}

@media (prefers-reduced-motion: reduce) {
  .ipad-device {
    transform: none !important;
  }
}
</style>

