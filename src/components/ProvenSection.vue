<template>
  <section class="py-20 md:py-32 bg-neutral-50">
    <div class="container mx-auto px-4 lg:px-8">
      <div class="max-w-3xl mx-auto text-center mb-16">
        <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-neutral-900 mb-6">
          Proven in eCommerce, B2B SaaS, and Ops Automation.
        </h2>
        <p class="text-lg md:text-xl text-neutral-600 leading-relaxed">
          I cannot disclose specific company names, but the work spans industry-grade stacks: 
          telecom workflows, multi-vendor Shopify operations, internal micro-SaaS with auth, 
          billing, and webhooks, plus agentic automations on queues. Here are case-like results 
          from real production environments.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 md:gap-8">
        <StatCard 
          v-for="stat in stats" 
          :key="stat.label"
          :stat="stat.stat"
          :label="stat.label"
          :description="stat.description"
        />
      </div>

      <div class="mt-12 text-center">
        <p class="text-sm text-neutral-500 italic">
          * Case-like results from production implementations
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import StatCard from './StatCard.vue'

const stats = [
  {
    stat: '+38%',
    label: 'Checkout Speed',
    description: 'Optimized payment flow reduced cart abandonment'
  },
  {
    stat: '<100ms',
    label: 'API P95',
    description: 'Sub-100ms response times at 95th percentile'
  },
  {
    stat: '5x',
    label: 'Faster Ops',
    description: 'Automation eliminated manual data entry'
  },
  {
    stat: '100%',
    label: 'VAT Compliance',
    description: 'Handled complex tax flows across EU regions'
  }
]
</script>

