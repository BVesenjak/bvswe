<template>
  <section id="work" class="py-20 md:py-32 bg-white">
    <div class="container mx-auto px-4 lg:px-8">
      <div class="max-w-3xl mx-auto text-center mb-16">
        <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-neutral-900 mb-6">
          Live Gallery
        </h2>
        <p class="text-lg md:text-xl text-neutral-600 leading-relaxed">
          A selection of production websites and applications. Each screenshot cycles through 
          different pages to showcase the full experience.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <GalleryTile 
          v-for="project in projects" 
          :key="project.title"
          :images="project.images"
          :url="project.url"
          :title="project.title"
          :swap-count="3"
          :swap-interval-ms="3000"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import GalleryTile from './GalleryTile.vue'

// NOTE: Replace these with your actual project URLs
const projects = [
  {
    title: 'eCommerce Platform',
    url: 'https://example.com',
    images: [
      '/screens/screen1.jpg',
      '/screens/screen2.jpg',
      '/screens/screen3.jpg'
    ]
  },
  {
    title: 'SaaS Dashboard',
    url: 'https://example.com',
    images: [
      '/screens/screen2.jpg',
      '/screens/screen3.jpg',
      '/screens/screen4.jpg'
    ]
  },
  {
    title: 'Automation Tool',
    url: 'https://example.com',
    images: [
      '/screens/screen3.jpg',
      '/screens/screen4.jpg',
      '/screens/screen1.jpg'
    ]
  },
  {
    title: 'Multi-vendor Marketplace',
    url: 'https://example.com',
    images: [
      '/screens/screen4.jpg',
      '/screens/screen1.jpg',
      '/screens/screen2.jpg'
    ]
  },
  {
    title: 'Billing Integration',
    url: 'https://example.com',
    images: [
      '/screens/screen1.jpg',
      '/screens/screen3.jpg',
      '/screens/screen4.jpg'
    ]
  },
  {
    title: 'Internal Operations',
    url: 'https://example.com',
    images: [
      '/screens/screen2.jpg',
      '/screens/screen4.jpg',
      '/screens/screen1.jpg'
    ]
  }
]
</script>

