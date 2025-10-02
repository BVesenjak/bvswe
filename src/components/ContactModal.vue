<template>
  <Teleport to="body">
    <transition
      enter-active-class="transition ease-out duration-300"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition ease-in duration-200"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div 
        v-if="show" 
        class="fixed inset-0 z-50 overflow-y-auto"
        @click.self="$emit('close')"
      >
        <!-- Backdrop -->
        <div class="fixed inset-0 bg-black/50 backdrop-blur-sm" @click="$emit('close')"></div>

        <!-- Modal -->
        <div class="flex min-h-full items-center justify-center p-4">
          <transition
            enter-active-class="transition ease-out duration-300"
            enter-from-class="opacity-0 scale-95"
            enter-to-class="opacity-100 scale-100"
            leave-active-class="transition ease-in duration-200"
            leave-from-class="opacity-100 scale-100"
            leave-to-class="opacity-0 scale-95"
          >
            <div 
              v-if="show"
              class="relative bg-white rounded-2xl shadow-2xl max-w-lg w-full p-8 md:p-10"
              @click.stop
            >
              <!-- Close button -->
              <button 
                @click="$emit('close')"
                class="absolute top-6 right-6 w-10 h-10 flex items-center justify-center rounded-lg text-neutral-400 hover:text-neutral-600 hover:bg-neutral-100 transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple"
                aria-label="Close modal"
              >
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                </svg>
              </button>

              <!-- Header -->
              <div class="mb-8">
                <h2 class="text-3xl font-bold text-neutral-900 mb-2">Get in Touch</h2>
                <p class="text-neutral-600">Let's discuss your project and see how I can help.</p>
              </div>

              <!-- Form -->
              <form @submit.prevent="handleSubmit" class="space-y-6">
                <div>
                  <label for="name" class="block text-sm font-semibold text-neutral-900 mb-2">
                    Your Name
                  </label>
                  <input 
                    id="name"
                    v-model="formData.name"
                    type="text" 
                    required
                    class="w-full px-4 py-3 border border-neutral-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-brand-purple focus:border-transparent transition-shadow"
                    placeholder="John Doe"
                  />
                </div>

                <div>
                  <label for="email" class="block text-sm font-semibold text-neutral-900 mb-2">
                    Email Address
                  </label>
                  <input 
                    id="email"
                    v-model="formData.email"
                    type="email" 
                    required
                    class="w-full px-4 py-3 border border-neutral-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-brand-purple focus:border-transparent transition-shadow"
                    placeholder="john@example.com"
                  />
                </div>

                <div>
                  <label for="message" class="block text-sm font-semibold text-neutral-900 mb-2">
                    Message
                  </label>
                  <textarea 
                    id="message"
                    v-model="formData.message"
                    rows="5"
                    required
                    class="w-full px-4 py-3 border border-neutral-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-brand-purple focus:border-transparent transition-shadow resize-none"
                    placeholder="Tell me about your project..."
                  ></textarea>
                </div>

                <div class="flex flex-col sm:flex-row gap-3">
                  <button 
                    type="submit"
                    class="flex-1 px-6 py-3 bg-brand-purple text-white rounded-lg font-semibold hover:bg-brand-purple-dark transition-colors focus:outline-none focus:ring-2 focus:ring-brand-purple focus:ring-offset-2"
                  >
                    Send Message
                  </button>
                  <button 
                    type="button"
                    @click="$emit('close')"
                    class="px-6 py-3 bg-neutral-100 text-neutral-700 rounded-lg font-semibold hover:bg-neutral-200 transition-colors focus:outline-none focus:ring-2 focus:ring-neutral-400 focus:ring-offset-2"
                  >
                    Cancel
                  </button>
                </div>
              </form>

              <!-- Note -->
              <p class="mt-6 text-sm text-neutral-500 text-center">
                This will open your email client. No backend required.
              </p>
            </div>
          </transition>
        </div>
      </div>
    </transition>
  </Teleport>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  show: {
    type: Boolean,
    required: true
  }
})

defineEmits(['close'])

const formData = ref({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  const subject = encodeURIComponent(`Portfolio Inquiry from ${formData.value.name}`)
  const body = encodeURIComponent(
    `Name: ${formData.value.name}\nEmail: ${formData.value.email}\n\nMessage:\n${formData.value.message}`
  )
  
  // NOTE: Replace with your actual email address
  window.location.href = `mailto:hello@example.com?subject=${subject}&body=${body}`
}

// Reset form when modal closes
watch(() => props.show, (newVal) => {
  if (!newVal) {
    formData.value = {
      name: '',
      email: '',
      message: ''
    }
  }
})
</script>

