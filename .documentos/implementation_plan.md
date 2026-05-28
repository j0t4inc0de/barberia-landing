# Construcción de Landing Page "Barbería Premium - Talento Urbano"

Este es el plan de implementación técnica para desarrollar la página web de aterrizaje (Landing Page) para la barbería **Talento Urbano**. Utilizaremos Vue 3 y una estructura optimizada para dispositivos móviles con transiciones premium y soporte de temas (Claro / Oscuro).

## User Review Required

> [!IMPORTANT]
> **Configuración de Red Docker y Cloudflare:**
> En tu `jota-server` tienes un contenedor llamado `cloudflare-tunnel` o `cloudflare` que gestiona el tráfico. Para que el túnel redirija el subdominio de la barbería a nuestro nuevo contenedor, este debe estar en la misma red de Docker (Docker Network) que el túnel de Cloudflare. 
> En el archivo `docker-compose.yml` propuesto, usaremos una red llamada `cloudflare_net` por defecto, pero deberás cambiarla por el nombre real de tu red si es diferente (puedes verificarla con `docker network ls` en tu servidor).

## Proposed Changes (Fase 2: Dockerización y Despliegue)

Añadiremos los archivos necesarios para empaquetar la aplicación en un contenedor Docker ligero con Nginx.

### [NEW] [Dockerfile](file:///D:/Proyectos/Paginas/Ficheros%20Vue.js/barberia-landing/Dockerfile)
- Configura una compilación multi-etapa (multi-stage build).
- **Etapa 1 (Build):** Usa Node.js Alpine para instalar dependencias y compilar la carpeta `dist`.
- **Etapa 2 (Production):** Usa Nginx Alpine para servir la carpeta estática final en el puerto 80, manteniéndolo ligero y rápido.

### [NEW] [docker-compose.yml](file:///D:/Proyectos/Paginas/Ficheros%20Vue.js/barberia-landing/docker-compose.yml)
- Orquesta el contenedor de la landing page.
- Lo asocia a la red externa para que Cloudflare pueda enrutar el subdominio hacia él.

### [NEW] [.dockerignore](file:///D:/Proyectos/Paginas/Ficheros%20Vue.js/barberia-landing/.dockerignore)
- Evita copiar archivos innecesarios como `node_modules` y `.git` al contexto de construcción de Docker, acelerando la compilación.

---

## Estructura de Archivos a Crear

### 1. Dockerfile
```dockerfile
# Stage 1: Build the Vue application
FROM node:20-alpine as build-stage
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve the application with Nginx
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### 2. docker-compose.yml
```yaml
version: '3.8'

services:
  talento-urbano-landing:
    build: .
    container_name: talento-urbano-landing
    restart: always
    expose:
      - "80"
    networks:
      - cloudflare_net

networks:
  cloudflare_net:
    external: true
```

### 3. .dockerignore
```
node_modules
dist
.git
.gitignore
.documentos
.antigravitycli
README.md
```

## Verification Plan

### Manual Verification
- Construiremos localmente la imagen de Docker para asegurar que el proceso de compilación de Nginx termine correctamente.
- Levantaremos el contenedor local en el puerto `8085` para verificar que la página se sirve adecuadamente desde Nginx.
- Te indicaré cómo copiar esta estructura a tu servidor `jota-server` en `~/projects/talento-urbano-landing` y conectarla a tu Cloudflare Tunnel.
