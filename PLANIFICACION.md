# 📋 Planificación de Segmentación Modular - Zenyx Landing Page

## 📁 Estructura de Carpetas

```
/
├── index.html                    # HTML principal (entrada)
├── /assets/
│   ├── /css/
│   │   ├── global.css           # Estilos globales y Tailwind config
│   │   ├── components.css       # Estilos específicos de componentes
│   │   └── utilities.css        # Utilidades y variables CSS
│   ├── /js/
│   │   ├── main.js              # JS principal (inicialización)
│   │   ├── navbar.js            # Lógica del navbar
│   │   ├── mobile-menu.js       # Menú móvil
│   │   ├── theme-toggle.js      # Dark/Light mode
│   │   └── animations.js        # Animaciones y efectos
│   └── /templates/
│       ├── navbar.html          # Componente: Navegación
│       ├── hero.html            # Sección: Hero/Principal
│       ├── about.html           # Sección: Sobre Zenyx
│       ├── testimonials.html    # Sección: Casos de éxito
│       ├── processes.html       # Sección: 4 Procesos
│       ├── why-zenyx.html       # Sección: Por qué Zenyx
│       ├── cta-final.html       # Sección: CTA Final
│       └── footer.html          # Componente: Footer
```

---

## 🎯 Segmentación por Secciones

### 1. **Navbar** (`/templates/navbar.html`)
**Descripción:** Navegación principal sticky
- Logo con icono
- Links de navegación (Desktop)
- Dropdown "Recursos"
- Botones: Campus, Contacto
- Menu hamburguesa (Mobile)

**Dependencias:**
- `navbar.js` - Toggle menu mobile, dropdown interactions
- `theme-toggle.js` - Cambiar tema dark/light
- Global CSS

---

### 2. **Hero Section** (`/templates/hero.html`)
**[IMPLEMENTADO]** Sección principal con CTA y video
- Heading principal "Hola"
- Grid de estadísticas (1M+, +35%, +20h)
- Video thumbnail con play button
- Glassmorphism card con CTA
- Efectos blur decorativos

**Dependencias:**
- `hero.js` - Carga dinámica y eventos (play video)
- `components.css` - Estilos específicos del hero
- Global CSS

---

### 3. **About Section** (`/templates/about.html`)
**Descripción:** Sobre Zenyx con 3 cards
- Heading + descripción
- 3 cards con:
  - Línea de acento animada
  - Título
  - Descripción
  - Link con icono

**Dependencias:**
- `animations.js` - Hover animations (línea que se expande)
- `components.css`
- Global CSS

---

### 4. **Testimonials Section** (`/templates/testimonials.html`)
**Descripción:** Casos de éxito / Testimonios
- Heading + descripción
- Grid mixto:
  - 1 card grande (md:col-span-2) con imagen y video play
  - 2 cards pequeñas con gradientes
- Estructura flexible para agregar más casos

**Dependencias:**
- `animations.js` - Scale on hover
- `components.css` - Grid layout y card styles
- Global CSS

---

### 5. **4 Procesos Section** (`/templates/processes.html`)
**Descripción:** Los 4 procesos clave para escalar
- Heading principal
- Grid de 4 cards numeradas
  - Esquina decorativa animada
  - Número de proceso
- CTA final con descripción

**Dependencias:**
- `animations.js` - Hover effects en esquina
- `components.css` - Card styles
- Global CSS

---

### 6. **Why Zenyx Section** (`/templates/why-zenyx.html`)
**Descripción:** Diferenciadores de Zenyx
- Grid 2 columnas:
  - Columna 1: Imagen
  - Columna 2: Heading + texto con highlight
- Responsive (mobile apila)

**Dependencias:**
- `components.css`
- Global CSS

---

### 7. **CTA Final Section** (`/templates/cta-final.html`)
**Descripción:** Llamada a acción final
- Fondo teal con efecto blur
- Heading principal
- Descripción
- Botón CTA
- Efectos visuales (blur background)

**Dependencias:**
- `animations.js` - Hover effects en botón
- `components.css`
- Global CSS

---

### 8. **Footer** (`/templates/footer.html`)
**Descripción:** Pie de página
- Grid de links (5 columnas)
- Información de contacto
- Links a redes sociales
- SVG logo con animación

**Dependencias:**
- Global CSS

---

## 🎨 Estilos

### `assets/css/global.css`
```
- Import Tailwind CSS
- Tailwind Config (darkMode, colors, fonts, etc.)
- Google Fonts links
- Material Icons link
- Reset de estilos globales
- Body y estilos base
- Smooth scroll
```

### `assets/css/components.css`
```
- Componentes reutilizables:
  * Botones (primary, secondary, variants)
  * Cards
  * Badges
  * Glassmorphism elements
  * Efectos hover
- Clases utilidad adicionales
```

### `assets/css/utilities.css`
```
- Variables CSS customizadas
- Colores personalizados
- Sombras
- Espaciamientos
- Animaciones keyframes
```

---

## ⚙️ JavaScript

### `assets/js/main.js`
```javascript
// Importar y inicializar todos los módulos
import navbar from './navbar.js';
import mobileMenu from './mobile-menu.js';
import themeToggle from './theme-toggle.js';
import animations from './animations.js';

// Inicialización
document.addEventListener('DOMContentLoaded', () => {
  navbar.init();
  mobileMenu.init();
  themeToggle.init();
  animations.init();
});
```

### `assets/js/navbar.js`
- Toggle dropdown "Recursos"
- Agregar clase active a links según scroll
- Sticky behavior

### `assets/js/mobile-menu.js`
- Toggle hamburger menu
- Cerrar al hacer click en un link
- Tema dark/light toggle en mobile

### `assets/js/theme-toggle.js`
- Detectar preferencia del sistema
- Guardar en localStorage
- Toggle manual dark/light

### `assets/js/animations.js`
- Intersection Observer para animaciones on scroll
- Hover effects
- Parallax effects
- Transiciones suaves

---

## 📄 `index.html` Principal

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Zenyx Agency Accelerator Landing Page</title>
    
    <!-- Estilos -->
    <link rel="stylesheet" href="assets/css/global.css">
    <link rel="stylesheet" href="assets/css/components.css">
    <link rel="stylesheet" href="assets/css/utilities.css">
</head>
<body>
    <!-- Navbar -->
    <div id="navbar-container"></div>
    
    <!-- Hero -->
    <div id="hero-container"></div>
    
    <!-- About -->
    <div id="about-container"></div>
    
    <!-- Testimonials -->
    <div id="testimonials-container"></div>
    
    <!-- Processes -->
    <div id="processes-container"></div>
    
    <!-- Why Zenyx -->
    <div id="why-zenyx-container"></div>
    
    <!-- CTA Final -->
    <div id="cta-final-container"></div>
    
    <!-- Footer -->
    <div id="footer-container"></div>
    
    <!-- Scripts -->
    <script type="module" src="assets/js/main.js"></script>
</body>
</html>
```

---

## 🔄 Sistema de Carga de Templates

### Opción 1: Template Strings (Sin servidor)
```javascript
// navbar.js
const navbarTemplate = `
  <nav class="...">
    <!-- Contenido del navbar -->
  </nav>
`;

export function init() {
  document.getElementById('navbar-container').innerHTML = navbarTemplate;
  // Agregar event listeners
}
```

### Opción 2: Fetch Templates
```javascript
async function loadTemplate(path) {
  const response = await fetch(path);
  return response.text();
}

async function init() {
  const template = await loadTemplate('templates/navbar.html');
  document.getElementById('navbar-container').innerHTML = template;
}
```

### Opción 3: Web Components (Avanzado)
```javascript
class ZenyxNavbar extends HTMLElement {
  connectedCallback() {
    this.render();
  }
  render() {
    this.innerHTML = `<!-- template aquí -->`;
  }
}
customElements.define('zenyx-navbar', ZenyxNavbar);
```

---

## ✅ Beneficios de esta Arquitectura

| Beneficio | Descripción |
|-----------|-------------|
| **Modularidad** | Cada sección es independiente y reutilizable |
| **Mantenibilidad** | Cambios en una sección no afectan otras |
| **Escalabilidad** | Fácil agregar nuevas secciones |
| **Reutilización** | Componentes compartidos (botones, cards) |
| **Organización** | Estructura clara de carpetas |
| **Performance** | CSS y JS organizados por responsabilidad |
| **Dark Mode** | Sistema tema completamente integrado |
| **Responsive** | Breakpoints consistentes Tailwind |

---

## 🚀 Implementación (Pasos)

1. **Crear estructura de carpetas** (`/assets`, `/templates`, etc.)
2. **Extraer CSS** a archivos dedicados (`global.css`, `components.css`)
3. **Extraer JS** a módulos (`navbar.js`, `animations.js`, etc.)
4. **Crear templates HTML** para cada sección
5. **Implementar sistema de carga** (fetch o template strings)
6. **Integrar estilos** y scripts en `index.html`
7. **Probar responsividad** y dark mode
8. **Optimizar y minificar** (opcional)

---

## 📝 Ejemplo de Componente Modular

### `assets/templates/hero.html`
```html
<section class="relative pt-20 pb-24 lg:pt-32 lg:pb-32 overflow-hidden bg-[#D1DFE8] dark:bg-gray-900 transition-colors duration-300">
  <!-- Contenido del hero -->
</section>
```

### `assets/js/hero.js`
```javascript
export async function init() {
  const template = await fetch('../templates/hero.html').then(r => r.text());
  document.getElementById('hero-container').innerHTML = template;
  
  // Inicializar event listeners específicos
  const playBtn = document.querySelector('.hero-play-btn');
  playBtn?.addEventListener('click', handleVideoClick);
}

function handleVideoClick(e) {
  // Lógica del video modal
}
```

---

## 🎯 Variables CSS Customizadas

En `assets/css/utilities.css`:
```css
:root {
  --primary: #FF6B52;
  --brand-teal: #0F3242;
  --brand-teal-light: #154257;
  --background-light: #F2F5F8;
  --background-dark: #0B212E;
  --brand-gray: #D8E1E8;
  
  --transition-default: 300ms ease-in-out;
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}
```

---

## 📱 Puntos de Ruptura

Usar consistentemente los breakpoints de Tailwind:
- `sm`: 640px
- `md`: 768px
- `lg`: 1024px
- `xl`: 1280px
- `2xl`: 1536px

---

## 🔐 Convenciones de Código

- **Nombres de archivos**: kebab-case (`navbar.js`, `mobile-menu.js`)
- **IDs de contenedores**: kebab-case con sufijo `-container` (`#navbar-container`)
- **Clases CSS**: Tailwind + customizadas con prefijo del módulo
- **Variables JS**: camelCase
- **Funciones**: camelCase, verb como prefijo (`initNavbar`, `handleClick`)

---

## 📦 Próximos Pasos (Opcional)

- Agregar bundler (Vite, Webpack)
- Crear sistema de build automatizado
- Agregar pre-processors CSS (SCSS)
- Implementar testing
- Optimizar imágenes
- Agregar PWA features
- SEO optimización

