<template>
  <div class="bg-white rounded-2xl p-6 md:p-8 shadow-lg border border-neutral-200 hover:shadow-xl transition-shadow">
    <div class="flex items-start space-x-4">
      <div class="flex-shrink-0 w-12 h-12 bg-brand-purple/10 rounded-xl flex items-center justify-center">
        <div class="w-6 h-6 bg-brand-purple rounded-md"></div>
      </div>
      <div class="flex-1">
        <div class="text-3xl md:text-4xl font-bold text-brand-purple mb-2">
          {{ stat }}
        </div>
        <div class="text-neutral-900 font-semibold mb-1">
          {{ label }}
        </div>
        <div class="text-sm text-neutral-600">
          {{ description }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  stat: {
    type: String,
    required: true
  },
  label: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  }
})
</script>

