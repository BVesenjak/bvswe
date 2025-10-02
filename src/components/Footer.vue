<template>
  <footer id="about" class="bg-neutral-50 border-t border-neutral-200">
    <div class="container mx-auto px-4 lg:px-8 py-16">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
        <!-- Brand -->
        <div class="md:col-span-1">
          <h3 class="text-2xl font-bold text-brand-purple mb-4">Portfolio</h3>
          <p class="text-neutral-600 text-sm leading-relaxed">
            Building production-ready software that drives real business value.
          </p>
        </div>

        <!-- Sitemap -->
        <div>
          <h4 class="font-bold text-neutral-900 mb-4">Navigation</h4>
          <ul class="space-y-2">
            <li v-for="link in navLinks" :key="link.name">
              <a 
                :href="link.href" 
                class="text-neutral-600 hover:text-brand-purple transition-colors text-sm focus:outline-none focus:ring-2 focus:ring-brand-purple rounded-sm"
              >
                {{ link.name }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Contact -->
        <div>
          <h4 class="font-bold text-neutral-900 mb-4">Contact</h4>
          <ul class="space-y-2 text-sm text-neutral-600">
            <li>
              <a href="mailto:hello@example.com" class="hover:text-brand-purple transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple rounded-sm">
                hello@example.com
              </a>
            </li>
            <li>
              <a href="tel:+1234567890" class="hover:text-brand-purple transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple rounded-sm">
                +1 (234) 567-890
              </a>
            </li>
          </ul>
        </div>

        <!-- Social -->
        <div>
          <h4 class="font-bold text-neutral-900 mb-4">Follow</h4>
          <div class="flex space-x-4">
            <a 
              v-for="social in socials" 
              :key="social.name"
              :href="social.url" 
              target="_blank"
              rel="noopener noreferrer"
              class="w-10 h-10 bg-neutral-200 hover:bg-brand-purple rounded-lg flex items-center justify-center transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple group"
              :aria-label="social.name"
            >
              <svg class="w-5 h-5 text-neutral-700 group-hover:text-white transition-colors" fill="currentColor" viewBox="0 0 24 24">
                <path :d="social.icon"/>
              </svg>
            </a>
          </div>
        </div>
      </div>

      <!-- Bottom -->
      <div class="pt-8 border-t border-neutral-200">
        <div class="flex flex-col md:flex-row justify-between items-center space-y-4 md:space-y-0">
          <p class="text-sm text-neutral-600">
            &copy; {{ currentYear }} Portfolio. All rights reserved.
          </p>
          <div class="flex space-x-6 text-sm text-neutral-600">
            <a href="#" class="hover:text-brand-purple transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple rounded-sm">
              Privacy Policy
            </a>
            <a href="#" class="hover:text-brand-purple transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple rounded-sm">
              Terms of Service
            </a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

const currentYear = computed(() => new Date().getFullYear())

const navLinks = [
  { name: 'Platform', href: '#platform' },
  { name: 'Work', href: '#work' },
  { name: 'Pricing', href: '#pricing' },
  { name: 'About', href: '#about' },
]

const socials = [
  {
    name: 'Twitter',
    url: 'https://twitter.com',
    icon: 'M23 3a10.9 10.9 0 01-3.14 1.53 4.48 4.48 0 00-7.86 3v1A10.66 10.66 0 013 4s-4 9 5 13a11.64 11.64 0 01-7 2c9 5 20 0 20-11.5a4.5 4.5 0 00-.08-.83A7.72 7.72 0 0023 3z'
  },
  {
    name: 'GitHub',
    url: 'https://github.com',
    icon: 'M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z'
  },
  {
    name: 'LinkedIn',
    url: 'https://linkedin.com',
    icon: 'M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z'
  }
]
</script>

