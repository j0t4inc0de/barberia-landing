# Walkthrough - Landing Page Talento Urbano 💈

¡Hemos completado con éxito la construcción y verificación de la Landing Page premium para la barbería! A continuación, se detalla todo el trabajo realizado.

## Resumen de Cambios

### 1. Sistema de Estilos y Paleta Global (`style.css`)
- **Variables CSS Nativas:** Definimos una paleta de colores limpia y moderna. El color por defecto es un **Dark Mode Premium** (fondos en gris carbón y acentos en **Dorado `#d4af37`**).
- **Tema Claro:** Se configuró la clase `.light-theme` que redefine las variables del sistema (fondos claros y dorados oscuros para contraste).
- **Transiciones y Tipografía:** Importamos *Outfit* e *Inter* desde Google Fonts. Añadimos transiciones fluidas de color y escala para todos los botones e interactivos.

### 2. Componente de Selección de Tema (`ThemeToggle.vue`)
- Creamos un selector flotante flotando a la derecha que conmuta entre modo oscuro y claro de forma interactiva.
- Implementamos una **animación de transición vistosa:** los iconos de sol y luna rotan y cambian de tamaño de forma elástica mediante transiciones CSS.
- **Persistencia:** Almacena la preferencia del usuario en `localStorage` para recordar el tema en futuras visitas.

### 3. Sección Hero (`HeroSection.vue`)
- **Encabezado Impactante:** Se colocó el nombre oficial **Talento Urbano** en un formato elegante.
- **Imagen de Fondo:** Añadimos una imagen de fondo de alta calidad generada por IA para ambientar el local.
- **Llamados a la Acción (CTA):** Botón flotante/pulsante que abre WhatsApp con el mensaje predefinido para agendar citas al número `+56948991554` y un botón secundario para ver servicios.
- **Bloqueo de Tema Oscuro:** El Hero se configuró para permanecer siempre oscuro, ignorando el selector de modo claro/oscuro. Esto preserva el aspecto premium inicial de entrada mientras que el resto de la página ("Nuestras Tarifas", "Reseñas" y "Footer") sí se adapta al modo claro si el usuario lo activa.

### 4. Sección de Servicios de Autor (`ServicesSection.vue`)
- Tarjetas con estilo *Glassmorphism* que albergan las tarifas en pesos chilenos (CLP) y duración de los servicios.
- Cada tarjeta contiene un enlace dinámico a WhatsApp que añade automáticamente el nombre del servicio al mensaje (ej: *"Hola Talento Urbano, quiero agendar el servicio: Combo Urbano"*).
- Efecto *hover* que eleva la tarjeta y le añade un brillo perimetral dorado.

### 5. Sección de Reseñas de Clientes (`ReviewsSection.vue`)
- Un badge interactivo imitando la valoración de Google Maps (4.9 / 5 estrellas).
- Tarjetas con comentarios reales de ejemplo destacando la experiencia, el ambiente y el agendamiento.

### 6. Pie de Página (`Footer.vue`)
- Horarios de atención estructurados por día de la semana.
- Datos de contacto y ubicación en **Lautaro 738, Los Ángeles, Chile**.
- Un mapa interactivo simulado con un botón directo a Google Maps.

---

## Imagen de Fondo Generada para la Demo
A continuación se muestra el fondo que generamos y configuramos en la cabecera:

![Interior Premium de Barbería](C:\Users\jeric\.gemini\antigravity-cli\brain\31090bfa-ee97-4f8b-99aa-9e8fb9c8edf1\barber_hero_1780007967048.png)

---

## Verificación de Compilación y Calidad

Ejecutamos los procesos de construcción del proyecto utilizando Vite para asegurar que todo compile sin errores:

```bash
> npm run build
vite v8.0.14 building client environment for production...
transforming...✓ 23 modules transformed.
rendering chunks...
computing gzip size...
dist/index.html                  1.47 kB │ gzip:  0.68 kB
dist/assets/index-CP65ewvG.css  18.40 kB │ gzip:  3.87 kB
dist/assets/index-CbM-UYxc.js   78.33 kB │ gzip: 29.27 kB

✓ built in 316ms
```

La compilación finalizó de forma exitosa sin advertencias ni errores en tan solo **316 milisegundos**.

---

## Guía de Despliegue en `jota-server` y Configuración del Subdominio

Sigue estos pasos para poner la Landing Page en línea usando tu infraestructura actual de Docker y Cloudflare.

### Paso 1: Copiar el proyecto al servidor
1. Sube o clona la carpeta de este proyecto a tu servidor local `jota-server` dentro de la ruta:
   `~/projects/talento-urbano-landing`

### Paso 2: Verificar la Red Docker de Cloudflare
El contenedor de la landing page necesita estar en la misma red que tu contenedor `cloudflare-tunnel` (el cual aparece como `cloudflare-tunnel` en tu listado de `docker ps`).
1. Para averiguar a qué red pertenece tu túnel, ejecuta en el servidor:
   ```bash
   docker inspect cloudflare-tunnel --format='{{join .NetworkSettings.Networks " "}}'
   ```
2. Si la red es diferente de `cloudflare_net`, edita el archivo `docker-compose.yml` en la última línea y cambia `cloudflare_net` por la red real:
   ```bash
   nano ~/projects/talento-urbano-landing/docker-compose.yml
   ```

### Paso 3: Levantar el Contenedor
1. Muévete al directorio del proyecto:
   ```bash
   cd ~/projects/talento-urbano-landing
   ```
2. Construye e inicia el contenedor en segundo plano:
   ```bash
   docker compose up -d --build
   ```
3. Verifica que esté corriendo ejecutando `docker ps`. Verás el contenedor `talento-urbano-landing` activo en el puerto `80/tcp`.

### Paso 4: Crear el Subdominio en Cloudflare
Dependiendo de cómo gestiones tu túnel de Cloudflare, elige **uno** de estos dos métodos:

#### Método A: Si gestionas el túnel desde el Dashboard Web (Recomendado)
1. Inicia sesión en el [Dashboard de Cloudflare Zero Trust](https://one.dash.cloudflare.com).
2. Ve a **Networks** ➡️ **Tunnels**.
3. Selecciona tu túnel activo y haz clic en **Edit**.
4. Dirígete a la pestaña **Public Hostname** y haz clic en **Add a public hostname**.
5. Rellena los datos:
   - **Subdomain:** Elige el subdominio (ej: `talentourbano` o `barberia`).
   - **Domain:** Selecciona tu dominio registrado en Cloudflare.
   - **Type:** Selecciona `HTTP`.
   - **URL:** Escribe `talento-urbano-landing:80` (gracias a que están en la misma red de Docker, Cloudflare resolverá el nombre del contenedor de forma interna).
6. Haz clic en **Save hostname**. ¡Listo! Cloudflare creará el registro DNS CNAME y el SSL automáticamente.

#### Método B: Si gestionas el túnel mediante archivo local (`config.yml`)
1. Abre tu archivo de configuración del túnel en el servidor (normalmente en `~/.cloudflared/config.yml` o similar):
   ```bash
   nano ~/cloudflare/config.yml
   ```
2. Añade la regla de entrada (Ingress Rule) arriba del catch-all (`service: http_status:404`):
   ```yaml
   - hostname: talentourbano.tudominio.com
     service: http://talento-urbano-landing:80
   ```
3. Guarda el archivo y reinicia el contenedor de Cloudflare:
   ```bash
   docker restart cloudflare-tunnel
   ```
4. Ve al Dashboard DNS de Cloudflare de tu dominio y crea un registro **CNAME** apuntando `talentourbano` a tu dirección del túnel (ej. `<id-del-tunel>.cfargotunnel.com`).

