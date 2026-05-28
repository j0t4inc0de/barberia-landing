<template>
  <footer class="footer-section">
    <div class="container">
      <div class="footer-grid">
        <!-- Brand Area -->
        <div class="footer-col brand-col">
          <div class="footer-logo">
            <span class="logo-accent">TALENTO</span>
            <span class="logo-main">URBANO</span>
          </div>
          <p class="brand-tagline">
            Tu estilo define quién eres. En Talento Urbano nos encargamos de proyectar tu mejor versión.
          </p>
          <div class="social-links">
            <a href="#" class="social-link glass-panel" aria-label="Siguenos en Instagram">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="social-icon">
                <rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect>
                <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
                <line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line>
              </svg>
            </a>
            <a href="#" class="social-link glass-panel" aria-label="Siguenos en TikTok">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="social-icon">
                <path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 0 5 5"></path>
              </svg>
            </a>
          </div>
        </div>

        <!-- Schedule Area -->
        <div class="footer-col">
          <h3 class="footer-title">Horarios</h3>
          <ul class="schedule-list">
            <li class="schedule-item">
              <span class="day">Lunes</span>
              <span class="hours">10:00 - 20:00</span>
            </li>
            <li class="schedule-item">
              <span class="day">Martes</span>
              <span class="hours">10:00 - 20:00</span>
            </li>
            <li class="schedule-item">
              <span class="day">Miércoles</span>
              <span class="hours">10:00 - 20:00</span>
            </li>
            <li class="schedule-item">
              <span class="day">Jueves</span>
              <span class="hours">10:00 - 20:00</span>
            </li>
            <li class="schedule-item">
              <span class="day">Viernes</span>
              <span class="hours">10:00 - 20:00</span>
            </li>
            <li class="schedule-item">
              <span class="day">Sábado</span>
              <span class="hours">10:00 - 20:00</span>
            </li>
            <li class="schedule-item closed">
              <span class="day">Domingo</span>
              <span class="hours">Cerrado</span>
            </li>
          </ul>
        </div>

        <!-- Location Area -->
        <div class="footer-col location-col">
          <h3 class="footer-title">Encuéntranos</h3>
          <div class="contact-info">
            <a 
              href="https://www.google.com/maps/search/?api=1&query=Lautaro+738%2C+Los+Angeles%2C+Chile" 
              target="_blank" 
              rel="noopener noreferrer" 
              class="contact-link"
            >
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="contact-icon">
                <path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"></path>
                <circle cx="12" cy="10" r="3"></circle>
              </svg>
              <span>Lautaro 738, Los Ángeles, Chile</span>
            </a>
            
            <a href="tel:+56948991554" class="contact-link">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="contact-icon">
                <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
              </svg>
              <span>+56 9 4899 1554</span>
            </a>
          </div>

          <div class="map-card glass-panel">
            <div class="map-placeholder">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="map-globe">
                <polygon points="1 6 1 22 8 18 16 22 23 18 23 2 16 6 8 2 1 6"></polygon>
                <line x1="8" y1="2" x2="8" y2="18"></line>
                <line x1="16" y1="6" x2="16" y2="22"></line>
              </svg>
              <a 
                href="https://www.google.com/maps/search/?api=1&query=Lautaro+738%2C+Los+Angeles%2C+Chile" 
                target="_blank" 
                rel="noopener noreferrer" 
                class="btn-map"
              >
                Ver en Google Maps
              </a>
            </div>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; {{ new Date().getFullYear() }} Talento Urbano. Todos los derechos reservados.</p>
        <p class="credits">Diseñado para la automatización digital.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer-section {
  background-color: var(--bg-tertiary);
  border-top: 1px solid var(--border-color);
  padding: 80px 0 30px;
  transition: var(--transition-theme);
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 50px;
  margin-bottom: 60px;
}

.footer-col {
  display: flex;
  flex-direction: column;
}

.footer-logo {
  display: flex;
  flex-direction: column;
  line-height: 0.9;
  margin-bottom: 20px;
  font-family: var(--font-heading);
}

.logo-accent {
  font-size: 1rem;
  letter-spacing: 5px;
  color: var(--accent);
  font-weight: 500;
}

.logo-main {
  font-size: 2.2rem;
  font-weight: 900;
  letter-spacing: 1.5px;
  color: var(--text-primary);
  transition: var(--transition-theme);
}

.brand-tagline {
  color: var(--text-secondary);
  font-size: 0.95rem;
  margin-bottom: 24px;
  max-width: 300px;
  transition: var(--transition-theme);
}

.social-links {
  display: flex;
  gap: 12px;
}

.social-link {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-primary);
  transition: var(--transition-theme), transform 0.3s ease;
}

.social-link:hover {
  transform: translateY(-3px);
  border-color: var(--accent);
  color: var(--accent);
}

.social-icon {
  width: 18px;
  height: 18px;
}

.footer-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 24px;
  position: relative;
  padding-bottom: 10px;
  font-family: var(--font-heading);
  transition: var(--transition-theme);
}

.footer-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 30px;
  height: 2px;
  background-color: var(--accent);
}

.schedule-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.schedule-item {
  display: flex;
  justify-content: space-between;
  font-size: 0.95rem;
  color: var(--text-secondary);
  border-bottom: 1px dashed var(--border-color);
  padding-bottom: 8px;
  transition: var(--transition-theme);
}

.schedule-item.closed {
  color: #ef4444;
}

.schedule-item.closed .hours {
  font-weight: 600;
}

.day {
  font-weight: 500;
}

.hours {
  font-family: var(--font-heading);
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin-bottom: 20px;
}

.contact-link {
  display: flex;
  align-items: center;
  gap: 12px;
  color: var(--text-secondary);
  font-size: 0.95rem;
  transition: var(--transition-theme), color 0.3s ease;
}

.contact-link:hover {
  color: var(--accent);
}

.contact-icon {
  width: 18px;
  height: 18px;
  color: var(--accent);
  flex-shrink: 0;
}

.map-card {
  height: 120px;
  overflow: hidden;
  position: relative;
}

.map-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  background: linear-gradient(135deg, var(--bg-secondary) 0%, var(--bg-primary) 100%);
  color: var(--text-secondary);
  transition: var(--transition-theme);
}

.map-globe {
  width: 24px;
  height: 24px;
  color: var(--accent);
}

.btn-map {
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--text-primary);
  background: var(--bg-tertiary);
  border: 1px solid var(--border-color);
  padding: 6px 14px;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.btn-map:hover {
  background: var(--accent);
  color: #000000;
  border-color: var(--accent);
}

.footer-bottom {
  border-top: 1px solid var(--border-color);
  padding-top: 30px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
  font-size: 0.85rem;
  color: var(--text-secondary);
  transition: var(--transition-theme);
}

.credits {
  font-weight: 500;
}

@media (max-width: 768px) {
  .footer-grid {
    gap: 40px;
  }
  .footer-bottom {
    flex-direction: column;
    text-align: center;
  }
}
</style>
