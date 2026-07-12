# Niara Studio — Portfolio

Landing page de una sola página para **Niara Studio** (Ingrid Marco, AI Creative Producer).
**Sin frameworks ni librerías**: HTML + CSS vanilla + un pequeño script propio.

## Estructura

```
niara-portfolio/
├── index.html        # marcado semántico
├── styles.css        # todo el CSS (design tokens en :root)
├── assets/img/*.webp # imágenes locales optimizadas
└── README.md
```

## Cómo verla

Abre `index.html` en el navegador (doble clic) o sírvela en local:

```bash
cd niara-portfolio
python3 -m http.server 8000   # http://localhost:8000
```

## Dependencias externas

- **Ninguna librería/framework.** Se eliminó Tailwind CDN (~3 MB de JS) y la fuente
  de iconos Material Symbols; los iconos ahora son **SVG inline**.
- Solo queda **Google Fonts** (Montserrat / Inter / Geist), que es el núcleo de la
  estética. Se puede self-hostear para quitar también esa dependencia (ver abajo).

## Optimizaciones ya aplicadas

- ✅ **Imágenes locales + WebP** — descargadas de las URLs temporales de Google
  (que caducan) y convertidas: **~1.3 MB PNG → ~92 KB WebP** (las 5 juntas).
- ✅ **Fondo del hero sin imagen** — la que había daba 403; sustituida por un
  **gradiente CSS** (menos peso, un asset menos, misma estética sakura).
- ✅ **Tailwind → CSS vanilla** — tokens de diseño en `:root`, clases semánticas.
- ✅ **Material Symbols → SVG inline** — una dependencia externa menos.
- ✅ Bugs del original arreglados: `glass-card`/`sakura-glow` sin definir, `<script>`
  cortado a media función, scroll-reveal que dejaba secciones invisibles.
- ✅ SEO (title, description, Open Graph, favicon), accesibilidad (skip-link,
  `label for`, `aria-*`, `prefers-reduced-motion`), menú móvil, `loading="lazy"`,
  `width`/`height` en imágenes (evita saltos de layout / CLS).

## Recomendaciones pendientes (para producción)

1. **Backend del formulario** — El `mailto:` es solo un fallback. Usa un servicio
   (Formspree, Basin, Netlify Forms) o un endpoint propio + validación anti-spam.
2. **Fuentes self-hosted** — Alojar Montserrat/Inter/Geist localmente (woff2)
   elimina la última dependencia externa y mejora privacidad y velocidad.
3. **Imágenes reales del portfolio** — Las actuales son placeholders generados;
   sustitúyelas por obra real (mantén WebP y las dimensiones para no romper el layout).
4. **Enlaces sociales reales** — LinkedIn/Instagram/YouTube/Twitter apuntan a `#`.
5. **Datos estructurados** — Añadir JSON-LD (`Person`/`Organization`) para SEO.
6. **Despliegue** — Ideal en Netlify, Vercel o GitHub Pages (sitio estático).
