<template>
  <section id="pricing" class="py-20 md:py-32 bg-white">
    <div class="container mx-auto px-4 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-neutral-900 mb-6">
            Tech Stack & Guarantees
          </h2>
          <p class="text-lg md:text-xl text-neutral-600 max-w-3xl mx-auto">
            Modern, battle-tested technologies paired with reliability you can count on.
          </p>
        </div>

        <!-- Tech Stack -->
        <div class="bg-neutral-50 rounded-2xl p-8 md:p-12 mb-12">
          <h3 class="text-2xl font-bold text-neutral-900 mb-8 text-center">
            Technologies I Use
          </h3>
          <div class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-8 gap-6">
            <div 
              v-for="tech in techStack" 
              :key="tech"
              class="flex flex-col items-center justify-center p-4 bg-white rounded-xl shadow-sm hover:shadow-md transition-shadow"
            >
              <div class="w-12 h-12 bg-brand-purple/10 rounded-lg flex items-center justify-center mb-3">
                <div class="w-6 h-6 bg-brand-purple rounded"></div>
              </div>
              <span class="text-sm font-medium text-neutral-700 text-center">{{ tech }}</span>
            </div>
          </div>
        </div>

        <!-- Guarantees -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-12">
          <div 
            v-for="guarantee in guarantees" 
            :key="guarantee.title"
            class="bg-neutral-50 rounded-2xl p-8"
          >
            <div class="flex items-start space-x-4">
              <div class="flex-shrink-0 w-12 h-12 bg-brand-purple rounded-xl flex items-center justify-center">
                <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
                </svg>
              </div>
              <div>
                <h4 class="text-xl font-bold text-neutral-900 mb-2">{{ guarantee.title }}</h4>
                <p class="text-neutral-600">{{ guarantee.description }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- CTA -->
        <div class="text-center">
          <button 
            @click="$emit('open-contact')"
            class="px-8 py-4 bg-white text-brand-purple border-2 border-brand-purple rounded-lg font-bold text-lg hover:bg-brand-purple hover:text-white transition-all focus:outline-none focus:ring-2 focus:ring-brand-purple focus:ring-offset-2 transform hover:scale-105"
          >
            Book a 15-min Call
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineEmits(['open-contact'])

const techStack = [
  'Vue.js',
  'React',
  'Vite',
  'Tailwind',
  'Node.js',
  'Python',
  'Docker',
  'Webhooks'
]

const guarantees = [
  {
    title: 'Reliable Communication',
    description: 'Clear status updates, responsive to messages, and transparent about timelines and blockers.'
  },
  {
    title: 'Small Milestones',
    description: 'Break work into demoable increments so you see progress every few days, not weeks.'
  },
  {
    title: 'Transparent Changelogs',
    description: 'Detailed commit messages and documentation so you know exactly what changed and why.'
  },
  {
    title: 'Demoable Increments',
    description: 'Every milestone includes a working demo you can test, providing confidence at each step.'
  }
]
</script>

