<template>
  <div class="min-h-screen">
    <Navbar @open-contact="showContactModal = true" />
    <Hero @open-contact="showContactModal = true" />
    <ProvenSection />
    <Gallery />
    <ServicesProcess @open-contact="showContactModal = true" />
    <StackGuarantees @open-contact="showContactModal = true" />
    <Footer />
    <ContactModal :show="showContactModal" @close="showContactModal = false" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import ProvenSection from './components/ProvenSection.vue'
import Gallery from './components/Gallery.vue'
import ServicesProcess from './components/ServicesProcess.vue'
import StackGuarantees from './components/StackGuarantees.vue'
import Footer from './components/Footer.vue'
import ContactModal from './components/ContactModal.vue'

const showContactModal = ref(false)
</script>

