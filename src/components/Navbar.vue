<template>
  <nav 
    class="sticky top-0 z-50 backdrop-blur-glass bg-white/80 border-b border-neutral-200/50"
    role="navigation"
    aria-label="Main navigation"
  >
    <div class="container mx-auto px-4 lg:px-8">
      <div class="flex items-center justify-between h-16 md:h-20">
        <!-- Logo -->
        <div class="flex-shrink-0">
          <a href="#" class="text-xl md:text-2xl font-bold text-brand-purple hover:text-brand-purple-dark transition-colors">
            Portfolio
          </a>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center space-x-8">
          <a 
            v-for="link in navLinks" 
            :key="link.name"
            :href="link.href" 
            class="text-neutral-700 hover:text-brand-purple transition-colors font-medium focus:outline-none focus:ring-2 focus:ring-brand-purple focus:ring-offset-2 rounded-sm px-1"
          >
            {{ link.name }}
          </a>
        </div>

        <!-- Right Side: CTA + Avatar -->
        <div class="flex items-center space-x-4">
          <button 
            @click="$emit('open-contact')"
            class="hidden sm:inline-flex px-4 md:px-6 py-2 bg-brand-purple text-white rounded-lg font-semibold hover:bg-brand-purple-dark transition-all focus:outline-none focus:ring-2 focus:ring-brand-purple focus:ring-offset-2 transform hover:scale-105"
          >
            Hire Me
          </button>

          <!-- Status Avatar -->
          <div 
            class="relative w-8 h-8 flex-shrink-0"
            role="img"
            aria-label="Available for new projects"
          >
            <div class="absolute inset-0 rounded-full bg-neutral-300 overflow-hidden">
              <!-- Placeholder avatar - replace with real image -->
              <div class="w-full h-full bg-gradient-to-br from-brand-purple to-brand-purple-light flex items-center justify-center text-white text-sm font-bold">
                P
              </div>
            </div>
            <!-- Animated green ring -->
            <div class="absolute inset-0 rounded-full border-2 border-green-500 animate-pulse-ring"></div>
          </div>

          <!-- Mobile Menu Button -->
          <button 
            @click="mobileMenuOpen = !mobileMenuOpen"
            class="md:hidden p-2 rounded-lg text-neutral-700 hover:bg-neutral-100 focus:outline-none focus:ring-2 focus:ring-brand-purple transition-colors"
            :aria-expanded="mobileMenuOpen"
            aria-label="Toggle menu"
          >
            <svg 
              class="w-6 h-6" 
              fill="none" 
              stroke="currentColor" 
              viewBox="0 0 24 24"
            >
              <path 
                v-if="!mobileMenuOpen"
                stroke-linecap="round" 
                stroke-linejoin="round" 
                stroke-width="2" 
                d="M4 6h16M4 12h16M4 18h16"
              />
              <path 
                v-else
                stroke-linecap="round" 
                stroke-linejoin="round" 
                stroke-width="2" 
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>

      <!-- Mobile Menu -->
      <transition
        enter-active-class="transition ease-out duration-200"
        enter-from-class="opacity-0 -translate-y-4"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition ease-in duration-150"
        leave-from-class="opacity-100 translate-y-0"
        leave-to-class="opacity-0 -translate-y-4"
      >
        <div 
          v-if="mobileMenuOpen" 
          class="md:hidden py-4 border-t border-neutral-200"
        >
          <div class="flex flex-col space-y-3">
            <a 
              v-for="link in navLinks" 
              :key="link.name"
              :href="link.href" 
              class="px-4 py-2 text-neutral-700 hover:bg-neutral-100 hover:text-brand-purple rounded-lg transition-colors font-medium focus:outline-none focus:ring-2 focus:ring-brand-purple"
              @click="mobileMenuOpen = false"
            >
              {{ link.name }}
            </a>
            <button 
              @click="$emit('open-contact'); mobileMenuOpen = false"
              class="sm:hidden mx-4 px-4 py-3 bg-brand-purple text-white rounded-lg font-semibold hover:bg-brand-purple-dark transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple"
            >
              Hire Me
            </button>
          </div>
        </div>
      </transition>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

defineEmits(['open-contact'])

const mobileMenuOpen = ref(false)

const navLinks = [
  { name: 'Platform', href: '#platform' },
  { name: 'Work', href: '#work' },
  { name: 'Pricing', href: '#pricing' },
  { name: 'About', href: '#about' },
]
</script>

<style scoped>
@keyframes pulse-ring {
  0%, 100% {
    opacity: 1;
    transform: scale(1);
  }
  50% {
    opacity: 0.6;
    transform: scale(1.1);
  }
}

.animate-pulse-ring {
  animation: pulse-ring 2s ease-in-out infinite;
}

@media (prefers-reduced-motion: reduce) {
  .animate-pulse-ring {
    animation: none;
    opacity: 1;
    transform: scale(1);
  }
}
</style>

