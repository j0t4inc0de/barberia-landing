<template>
  <header class="hero-section">
    <div class="hero-bg" :style="{ backgroundImage: `url('/barber_hero.png')` }"></div>
    <div class="hero-overlay"></div>
    
    <div class="container hero-content">
      <div class="logo-area">
        <span class="logo-accent">TALENTO</span>
        <span class="logo-main">URBANO</span>
      </div>
      
      <div class="badge">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="badge-icon">
          <circle cx="12" cy="12" r="10"></circle>
          <path d="m9 12 2 2 4-4"></path>
        </svg>
        <span>Estilo, Precisión y Tendencia</span>
      </div>
      
      <h1 class="hero-title">
        Eleva tu Imagen al <br>
        <span class="gradient-text">Siguiente Nivel</span>
      </h1>
      
      <p class="hero-description">
        Descubre el verdadero arte del detalle en el corazón de Los Ángeles. Degradados perfectos, perfilado de barba premium y un ambiente diseñado para ti.
      </p>
      
      <div class="hero-actions">
        <a 
          href="https://wa.me/56948991554?text=Hola%20Talento%20Urbano%2C%20me%20gustar%C3%ADa%20agendar%20una%20cita" 
          target="_blank" 
          rel="noopener noreferrer" 
          class="btn btn-whatsapp pulse-btn"
        >
          <svg class="wsp-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12.012 2c-5.506 0-9.989 4.478-9.99 9.984a9.96 9.96 0 0 0 1.335 4.963L2 22l5.233-1.372a9.948 9.948 0 0 0 4.777 1.218h.004c5.505 0 9.988-4.478 9.989-9.984 0-2.669-1.037-5.176-2.922-7.062A9.925 9.925 0 0 0 12.012 2zm5.835 14.165c-.244.688-1.22 1.259-1.672 1.312-.41.048-.947.078-2.695-.644-2.233-.923-3.673-3.197-3.784-3.346-.111-.148-.905-1.202-.905-2.294a2.43 2.43 0 0 1 .74-1.785c.245-.245.534-.306.702-.306.168 0 .336.002.481.009.15.007.351-.057.553.428.204.493.699 1.7.759 1.821.06.121.1.261.019.421-.08.16-.121.261-.242.401-.121.14-.253.313-.362.42-.121.121-.248.254-.107.493.14.24.626 1.026 1.344 1.666.924.821 1.701 1.077 1.942 1.197.241.12.381.1.522-.06.14-.16.602-.702.762-.942.16-.24.321-.201.542-.121.22.08 1.4.661 1.64.781.24.12.4.18.46.281.06.1.06.58-.18 1.268z"/>
          </svg>
          Agendar Cita por WhatsApp
        </a>
        <a href="#servicios" class="btn btn-outline">
          Ver Servicios & Precios
        </a>
      </div>
      
      <div class="hero-info">
        <div class="info-item">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="info-icon">
            <path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"></path>
            <circle cx="12" cy="10" r="3"></circle>
          </svg>
          <span>Lautaro 738, Los Ángeles</span>
        </div>
        <div class="info-item">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="info-icon">
            <circle cx="12" cy="12" r="10"></circle>
            <polyline points="12 6 12 12 16 14"></polyline>
          </svg>
          <span>Lun - Sáb: 10:00 - 20:00</span>
        </div>
      </div>
    </div>
    
    <div class="scroll-indicator">
      <div class="mouse">
        <div class="wheel"></div>
      </div>
      <span class="scroll-text">Deslizar para explorar</span>
    </div>
  </header>
</template>

<style scoped>
.hero-section {
  /* Lock variables to Dark Theme values (Hero is always dark) */
  --bg-primary: #090a0f;
  --bg-secondary: #111319;
  --bg-tertiary: #191c24;
  --accent: #d4af37;
  --accent-rgb: 212, 175, 55;
  --accent-glow: rgba(212, 175, 55, 0.15);
  --text-primary: #ffffff;
  --text-secondary: #94a3b8;
  --border-color: rgba(255, 255, 255, 0.08);
  --glass-bg: rgba(17, 19, 25, 0.75);
  --glass-border: rgba(255, 255, 255, 0.05);
  --shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.7);

  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 100px;
  padding-bottom: 80px;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  z-index: 1;
  transition: transform 0.8s ease;
}

.hero-section:hover .hero-bg {
  transform: scale(1.03);
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    to bottom,
    rgba(9, 10, 15, 0.4) 0%,
    var(--bg-primary) 92%
  );
  z-index: 2;
  transition: var(--transition-theme);
}

.hero-content {
  position: relative;
  z-index: 3;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 800px;
}

.logo-area {
  display: flex;
  flex-direction: column;
  line-height: 0.9;
  margin-bottom: 24px;
  font-family: var(--font-heading);
}

.logo-accent {
  font-size: 1.2rem;
  letter-spacing: 6px;
  color: var(--accent);
  font-weight: 500;
}

.logo-main {
  font-size: 2.8rem;
  font-weight: 900;
  letter-spacing: 2px;
  color: var(--text-primary);
  text-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  transition: var(--transition-theme);
}

.badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--glass-bg);
  border: 1px solid var(--glass-border);
  padding: 8px 16px;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--accent);
  margin-bottom: 24px;
  box-shadow: var(--shadow);
  transition: var(--transition-theme);
}

.badge-icon {
  width: 16px;
  height: 16px;
}

.hero-title {
  font-size: clamp(2.5rem, 6vw, 4.5rem);
  font-weight: 800;
  margin-bottom: 20px;
  letter-spacing: -1px;
  text-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
  transition: var(--transition-theme);
}

.gradient-text {
  background: linear-gradient(135deg, var(--accent) 0%, #ffffff 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}



.hero-description {
  font-size: clamp(1rem, 2vw, 1.15rem);
  color: var(--text-secondary);
  max-width: 600px;
  margin-bottom: 40px;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.4);
  transition: var(--transition-theme);
}

.hero-actions {
  display: flex;
  gap: 16px;
  margin-bottom: 48px;
  flex-wrap: wrap;
  justify-content: center;
}

.wsp-icon {
  width: 20px;
  height: 20px;
}

.btn-outline {
  background: transparent;
  color: var(--text-primary);
  border: 2px solid var(--border-color);
}

.btn-outline:hover {
  background: var(--bg-tertiary);
  border-color: var(--accent);
  transform: translateY(-2px);
}

.hero-info {
  display: flex;
  gap: 32px;
  color: var(--text-secondary);
  font-size: 0.9rem;
  font-weight: 500;
  transition: var(--transition-theme);
}

.info-item {
  display: flex;
  align-items: center;
  gap: 8px;
}

.info-icon {
  width: 18px;
  height: 18px;
  color: var(--accent);
}

/* Scroll indicator animation */
.scroll-indicator {
  position: absolute;
  bottom: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  z-index: 3;
  color: var(--text-secondary);
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  transition: var(--transition-theme);
}

.mouse {
  width: 24px;
  height: 38px;
  border: 2px solid var(--border-color);
  border-radius: 20px;
  display: flex;
  justify-content: center;
  padding-top: 6px;
  transition: var(--transition-theme);
}

.wheel {
  width: 4px;
  height: 8px;
  background-color: var(--accent);
  border-radius: 2px;
  animation: scroll-wheel 1.5s infinite;
}

@keyframes scroll-wheel {
  0% {
    transform: translateY(0);
    opacity: 1;
  }
  50% {
    transform: translateY(6px);
    opacity: 0.3;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

@media (max-width: 768px) {
  .hero-section {
    padding-top: 80px;
    padding-bottom: 60px;
  }
  .logo-main {
    font-size: 2.2rem;
  }
  .hero-actions {
    flex-direction: column;
    width: 100%;
    padding: 0 20px;
  }
  .btn {
    width: 100%;
  }
  .hero-info {
    flex-direction: column;
    gap: 16px;
    align-items: center;
  }
  .scroll-indicator {
    display: none;
  }
}
</style>
