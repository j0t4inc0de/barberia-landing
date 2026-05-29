<script setup>
import { ref } from 'vue'
import ThemeToggle from './components/ThemeToggle.vue'
import HeroSection from './components/HeroSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import ReviewsSection from './components/ReviewsSection.vue'
import Footer from './components/Footer.vue'

// CONFIGURACIÓN CENTRALIZADA DEL NEGOCIO
// Cambia este número para pruebas (ej. el de tu amigo) o para producción (el de la barbería)
// Nota: Debe ir sin el signo "+" al inicio, solo números con código de país (ej: 56948991554)
const phoneNumber = ref('56993379963') 
const address = ref('Lautaro 738, Los Ángeles, Chile')
const scheduleText = ref('Lun - Sáb: 10:00 - 20:00')
</script>

<template>
  <ThemeToggle />
  <HeroSection 
    :phone-number="phoneNumber" 
    :address="address" 
    :schedule="scheduleText" 
  />
  <ServicesSection 
    :phone-number="phoneNumber" 
  />
  <ReviewsSection />
  <Footer 
    :phone-number="phoneNumber" 
    :address="address" 
  />
</template>

<style>
/* Estilos globales */
</style>
