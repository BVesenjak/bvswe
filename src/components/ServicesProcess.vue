<template>
  <section id="platform" class="py-20 md:py-32 bg-neutral-50">
    <div class="container mx-auto px-4 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-neutral-900 mb-6">
            Services & Process
          </h2>
          <p class="text-lg md:text-xl text-neutral-600 max-w-3xl mx-auto">
            From concept to production, I deliver end-to-end solutions with clear milestones and transparent communication.
          </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-16">
          <!-- What I Do -->
          <div class="bg-white rounded-2xl p-8 md:p-10 shadow-lg">
            <h3 class="text-2xl md:text-3xl font-bold text-neutral-900 mb-8">
              What I Do
            </h3>
            <div class="space-y-6">
              <div 
                v-for="service in services" 
                :key="service.title"
                class="flex items-start space-x-4"
              >
                <div class="flex-shrink-0 w-10 h-10 bg-brand-purple rounded-lg flex items-center justify-center">
                  <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                  </svg>
                </div>
                <div>
                  <h4 class="font-bold text-neutral-900 mb-1">{{ service.title }}</h4>
                  <p class="text-neutral-600 text-sm">{{ service.description }}</p>
                </div>
              </div>
            </div>
          </div>

          <!-- How I Work -->
          <div class="bg-white rounded-2xl p-8 md:p-10 shadow-lg">
            <h3 class="text-2xl md:text-3xl font-bold text-neutral-900 mb-8">
              How I Work
            </h3>
            <div class="space-y-8 relative">
              <!-- Timeline line -->
              <div class="absolute left-5 top-8 bottom-8 w-0.5 bg-brand-purple/20"></div>
              
              <div 
                v-for="(step, index) in process" 
                :key="step.title"
                class="relative flex items-start space-x-4"
              >
                <div class="flex-shrink-0 w-10 h-10 bg-brand-purple text-white rounded-full flex items-center justify-center font-bold z-10">
                  {{ index + 1 }}
                </div>
                <div class="flex-1 pt-1">
                  <h4 class="font-bold text-neutral-900 mb-1">{{ step.title }}</h4>
                  <p class="text-neutral-600 text-sm">{{ step.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- CTA -->
        <div class="mt-16 text-center">
          <button 
            @click="$emit('open-contact')"
            class="px-8 py-4 bg-brand-purple text-white rounded-lg font-bold text-lg hover:bg-brand-purple-dark transition-all focus:outline-none focus:ring-2 focus:ring-brand-purple focus:ring-offset-2 transform hover:scale-105"
          >
            Get a scoped, fixed-price quote
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineEmits(['open-contact'])

const services = [
  {
    title: 'Storefront Build & Optimization',
    description: 'High-performance eCommerce sites with conversion-focused UX'
  },
  {
    title: 'Micro-SaaS MVPs',
    description: 'Full-stack applications from auth to billing, shipped fast'
  },
  {
    title: 'Billing & Subscriptions',
    description: 'Stripe integrations, webhooks, tax compliance, and dunning'
  },
  {
    title: 'Automation & Agents',
    description: 'Queue-based workflows, API integrations, and intelligent automation'
  },
  {
    title: 'DX Tooling',
    description: 'Internal tools, admin panels, and developer experience improvements'
  }
]

const process = [
  {
    title: 'Discovery',
    description: 'Understand your goals, constraints, and success criteria'
  },
  {
    title: 'Specification',
    description: 'Clear scope, milestones, and fixed-price proposal'
  },
  {
    title: 'Build',
    description: 'Iterative development with regular demos and check-ins'
  },
  {
    title: 'Iterate',
    description: 'Refinement based on feedback, then ship to production'
  }
]
</script>

