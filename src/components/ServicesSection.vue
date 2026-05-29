<script setup>
import { ref } from 'vue'

defineProps({
  phoneNumber: {
    type: String,
    required: true
  }
})

const services = ref([
  {
    id: 1,
    name: 'Corte Talento',
    price: '$10.000',
    duration: '40 min',
    description: 'Corte de cabello clásico o moderno (Fade/Degradado) personalizado según tu fisonomía. Incluye lavado y peinado con producto premium.',
    icon: 'scissors'
  },
  {
    id: 2,
    name: 'Perfilado de Barba',
    price: '$8.000',
    duration: '30 min',
    description: 'Diseño y afeitado de barba con navaja tradicional, toalla caliente para abrir poros, aceites hidratantes y masaje relajante.',
    icon: 'razor'
  },
  {
    id: 3,
    name: 'Combo Urbano',
    price: '$16.000',
    duration: '60 min',
    description: 'El servicio completo definitivo. Corte de cabello a elección + perfilado de barba completo con ritual de toalla caliente y lavado.',
    icon: 'star'
  },
  {
    id: 4,
    name: 'Cejas y Detalles',
    price: '$4.000',
    duration: '15 min',
    description: 'Perfilado de cejas con navaja y limpieza de vello facial sobrante en pómulos u orejas para un acabado impecable.',
    icon: 'sparkles'
  }
])
</script>

<template>
  <section id="servicios" class="services-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">Nuestras Tarifas</span>
        <h2 class="section-title">Servicios de Autor</h2>
        <p class="section-subtitle">
          Combinamos técnicas tradicionales con las últimas tendencias urbanas para ofrecerte resultados excepcionales.
        </p>
      </div>

      <div class="services-grid">
        <div 
          v-for="service in services" 
          :key="service.id" 
          class="service-card glass-panel"
        >
          <div class="card-icon-container">
            <!-- Scissors Icon -->
            <svg v-if="service.icon === 'scissors'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="card-icon">
              <circle cx="6" cy="6" r="3"></circle>
              <circle cx="6" cy="18" r="3"></circle>
              <line x1="9.8" y1="8.2" x2="20" y2="17"></line>
              <line x1="9.8" y1="15.8" x2="20" y2="7"></line>
            </svg>
            <!-- Razor/Knife Icon alternative -->
            <svg v-else-if="service.icon === 'razor'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="card-icon">
              <path d="M3 21h18"></path>
              <path d="M5 17V7a3 3 0 0 1 3-3h8a3 3 0 0 1 3 3v10"></path>
              <path d="M9 12h6"></path>
            </svg>
            <!-- Star (Combo) Icon -->
            <svg v-else-if="service.icon === 'star'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="card-icon special-icon">
              <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
            </svg>
            <!-- Sparkles (Details) Icon -->
            <svg v-else xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="card-icon">
              <path d="m12 3-1.912 5.813a2 2 0 0 1-1.275 1.275L3 12l5.813 1.912a2 2 0 0 1 1.275 1.275L12 21l1.912-5.813a2 2 0 0 1 1.275-1.275L21 12l-5.813-1.912a2 2 0 0 1-1.275-1.275L12 3Z"></path>
            </svg>
          </div>

          <div class="card-header">
            <h3 class="service-name">{{ service.name }}</h3>
            <span class="service-price">{{ service.price }}</span>
          </div>

          <div class="service-meta">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="meta-icon">
              <circle cx="12" cy="12" r="10"></circle>
              <polyline points="12 6 12 12 16 14"></polyline>
            </svg>
            <span>{{ service.duration }} de duración</span>
          </div>

          <p class="service-desc">{{ service.description }}</p>

          <div class="card-action">
            <a 
              :href="`https://wa.me/${phoneNumber}?text=Hola%20Talento%20Urbano%2C%20quiero%20agendar%20el%20servicio%3A%20${encodeURIComponent(service.name)}`" 
              target="_blank" 
              rel="noopener noreferrer" 
              class="btn-card-booking"
            >
              <span>Agendar Servicio</span>
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="arrow-icon">
                <line x1="5" y1="12" x2="19" y2="12"></line>
                <polyline points="12 5 19 12 12 19"></polyline>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-section {
  background-color: var(--bg-secondary);
  transition: var(--transition-theme);
  border-top: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
}

.section-header {
  text-align: center;
  max-width: 600px;
  margin: 0 auto 60px;
}

.section-tag {
  font-family: var(--font-heading);
  font-size: 0.85rem;
  font-weight: 700;
  letter-spacing: 2px;
  color: var(--accent);
  text-transform: uppercase;
  display: inline-block;
  margin-bottom: 12px;
}

.section-title {
  font-size: clamp(2rem, 4vw, 2.75rem);
  margin-bottom: 16px;
  transition: var(--transition-theme);
}

.section-subtitle {
  color: var(--text-secondary);
  font-size: 1.05rem;
  transition: var(--transition-theme);
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
}

.service-card {
  padding: 32px;
  display: flex;
  flex-direction: column;
  height: 100%;
  position: relative;
  overflow: hidden;
  transition: transform 0.4s cubic-bezier(0.165, 0.84, 0.44, 1), 
              border-color 0.4s ease, 
              box-shadow 0.4s ease,
              background-color 0.5s ease;
}

.service-card:hover {
  transform: translateY(-8px);
  border-color: rgba(var(--accent-rgb), 0.3);
  box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.8),
              0 0 25px rgba(var(--accent-rgb), 0.05);
}

.light-theme .service-card:hover {
  box-shadow: 0 20px 40px -15px rgba(148, 163, 184, 0.25),
              0 0 25px rgba(var(--accent-rgb), 0.05);
}

.card-icon-container {
  width: 54px;
  height: 54px;
  background: var(--bg-tertiary);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 24px;
  color: var(--accent);
  transition: var(--transition-theme);
}

.card-icon {
  width: 24px;
  height: 24px;
}

.special-icon {
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-4px) rotate(5deg); }
  100% { transform: translateY(0px) rotate(0deg); }
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 8px;
  gap: 12px;
}

.service-name {
  font-size: 1.35rem;
  font-weight: 700;
  transition: var(--transition-theme);
}

.service-price {
  font-family: var(--font-heading);
  font-size: 1.4rem;
  font-weight: 800;
  color: var(--accent);
}

.service-meta {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 0.85rem;
  color: var(--text-secondary);
  margin-bottom: 16px;
  font-weight: 500;
  transition: var(--transition-theme);
}

.meta-icon {
  width: 14px;
  height: 14px;
}

.service-desc {
  color: var(--text-secondary);
  font-size: 0.95rem;
  line-height: 1.5;
  margin-bottom: 28px;
  flex-grow: 1;
  transition: var(--transition-theme);
}

.card-action {
  border-top: 1px solid var(--border-color);
  padding-top: 20px;
  margin-top: auto;
  transition: var(--transition-theme);
}

.btn-card-booking {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  color: var(--text-primary);
  font-family: var(--font-heading);
  font-weight: 600;
  font-size: 0.95rem;
  cursor: pointer;
  transition: color 0.3s ease;
}

.arrow-icon {
  width: 16px;
  height: 16px;
  transition: transform 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.btn-card-booking:hover {
  color: var(--accent);
}

.btn-card-booking:hover .arrow-icon {
  transform: translateX(6px);
}

@media (max-width: 768px) {
  .section-header {
    margin-bottom: 40px;
  }
}
</style>
