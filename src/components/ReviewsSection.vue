<script setup>
import { ref } from 'vue'

const reviews = ref([
  {
    id: 1,
    author: 'Pedro Gómez',
    avatar: 'PG',
    rating: 5,
    text: 'Excelente servicio, el degradado quedó impecable y la atención es súper profesional. El ambiente de la barbería tiene muchísimo estilo.',
    date: 'Hace 1 semana'
  },
  {
    id: 2,
    author: 'Matías Contreras',
    avatar: 'MC',
    rating: 5,
    text: 'La atención es de primer nivel. El ritual de toalla caliente para la barba es increíble. Definitivamente la mejor barbería en Los Ángeles.',
    date: 'Hace 3 días'
  },
  {
    id: 3,
    author: 'Sebastián Muñoz',
    avatar: 'SM',
    rating: 5,
    text: 'Muy profesionales. Cumplen los horarios de las citas a la perfección y la música y onda del local te hacen sentir muy cómodo.',
    date: 'Hace 2 semanas'
  }
])
</script>

<template>
  <section id="opiniones" class="reviews-section">
    <div class="container">
      <div class="section-header">
        <span class="section-tag">Social Proof</span>
        <h2 class="section-title">La Opinión de la Calle</h2>
        <p class="section-subtitle">
          Nuestros clientes avalan la calidad. Esto es lo que dicen sobre su experiencia en Talento Urbano.
        </p>
      </div>

      <!-- Google Maps Rating Summary Badge -->
      <div class="google-badge glass-panel">
        <div class="badge-logo">
          <svg class="google-logo" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z" fill="#4285F4"/>
            <path d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z" fill="#34A853"/>
            <path d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.06H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.94l2.85-2.22.81-.63z" fill="#FBBC05"/>
            <path d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.06l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z" fill="#EA4335"/>
          </svg>
          <div class="badge-info">
            <span class="badge-source">Google Reviews</span>
            <span class="badge-count">4.9 / 5 estrellas (120+ opiniones)</span>
          </div>
        </div>
        <div class="stars-row">
          <svg v-for="n in 5" :key="n" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="star-icon">
            <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
          </svg>
        </div>
      </div>

      <div class="reviews-grid">
        <div 
          v-for="review in reviews" 
          :key="review.id" 
          class="review-card glass-panel"
        >
          <div class="review-header">
            <div class="avatar">{{ review.avatar }}</div>
            <div class="author-details">
              <h3 class="author-name">{{ review.author }}</h3>
              <span class="review-date">{{ review.date }}</span>
            </div>
            <div class="google-badge-small">
              <svg class="google-icon-sm" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z" fill="#4285F4"/>
                <path d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z" fill="#34A853"/>
                <path d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.06H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.94l2.85-2.22.81-.63z" fill="#FBBC05"/>
                <path d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.06l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z" fill="#EA4335"/>
              </svg>
            </div>
          </div>

          <div class="review-stars">
            <svg v-for="n in review.rating" :key="n" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="star-icon-small">
              <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
            </svg>
          </div>

          <p class="review-text">"{{ review.text }}"</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.reviews-section {
  background-color: var(--bg-primary);
  transition: var(--transition-theme);
  position: relative;
}

.section-header {
  text-align: center;
  max-width: 600px;
  margin: 0 auto 40px;
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

.google-badge {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 500px;
  margin: 0 auto 60px;
  padding: 16px 28px;
  flex-wrap: wrap;
  gap: 16px;
}

.badge-logo {
  display: flex;
  align-items: center;
  gap: 14px;
}

.google-logo {
  width: 32px;
  height: 32px;
}

.badge-info {
  display: flex;
  flex-direction: column;
}

.badge-source {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.5px;
  color: var(--text-secondary);
  text-transform: uppercase;
}

.badge-count {
  font-size: 0.95rem;
  font-weight: 600;
}

.stars-row {
  display: flex;
  gap: 4px;
}

.star-icon {
  width: 20px;
  height: 20px;
  color: #ffb800;
}

.reviews-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.review-card {
  padding: 32px;
  display: flex;
  flex-direction: column;
  position: relative;
  transition: transform 0.3s cubic-bezier(0.165, 0.84, 0.44, 1), 
              border-color 0.3s ease,
              background-color 0.5s ease;
}

.review-card:hover {
  transform: scale(1.02);
  border-color: rgba(var(--accent-rgb), 0.25);
}

.review-header {
  display: flex;
  align-items: center;
  margin-bottom: 16px;
  position: relative;
}

.avatar {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: var(--bg-tertiary);
  color: var(--accent);
  font-family: var(--font-heading);
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  border: 1px solid var(--border-color);
  transition: var(--transition-theme);
}

.author-details {
  margin-left: 12px;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.author-name {
  font-size: 1.05rem;
  font-weight: 600;
  line-height: 1.2;
  transition: var(--transition-theme);
}

.review-date {
  font-size: 0.8rem;
  color: var(--text-secondary);
  transition: var(--transition-theme);
}

.google-badge-small {
  align-self: flex-start;
}

.google-icon-sm {
  width: 18px;
  height: 18px;
}

.review-stars {
  display: flex;
  gap: 2px;
  margin-bottom: 16px;
}

.star-icon-small {
  width: 16px;
  height: 16px;
  color: #ffb800;
}

.review-text {
  color: var(--text-secondary);
  font-size: 0.95rem;
  line-height: 1.6;
  font-style: italic;
  transition: var(--transition-theme);
}

@media (max-width: 576px) {
  .google-badge {
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 20px;
  }
  .badge-logo {
    flex-direction: column;
    gap: 8px;
  }
}
</style>
