# Sitio web de Soda Stereo — Proyecto final Coderhouse

Proyecto estático construido con HTML, SASS (arquitectura 7‑1) y un poco de JS para interacción en la página de discografía. Proyecto final de Coderhouse con enfoque en accesibilidad, SEO y diseño responsivo.

## Requisitos

- Node.js y npm instalados
- Sass incluido como devDependency

## Iniciar desarrollo

1. Instalar dependencias (solo Sass ya está en `package.json`):

   ```bash
   npm install
   ```

2. Iniciar el watcher de SASS:

   ```bash
   npm run sass
   ```

3. Abrir `index.html` en el navegador o usar un servidor estático (por ejemplo, Live Server).

## Estructura del proyecto

- `index.html`: Página de inicio
- `pages/`: Páginas internas (`banda.html`, `contacto.html`, `discografia.html`)
- `scss/`: Estilos SASS siguiendo patrón 7‑1
  - `_variables.scss`: Colores, tipografías, tamaños, breakpoints
  - `_mixins.scss`: Mixins reutilizables (`respond-to`, `soft-shadow`, etc.)
  - `_base.scss`: Reset y estilos globales (tipografía, `skip-link`)
  - `_layout.scss`: Header, footers y héroes de páginas internas
  - `_components.scss`: Grillas, chips, badges, timeline
  - `_pages.scss`: Estilos específicos por página (hero del home, discografía, contacto)
  - `styles.scss`: Punto de entrada que importa todo
- `css/styles.css`: Archivo generado por Sass
- `img/`: Imágenes (portadas, favicons, logos)

## Responsivo (breakpoints)

- Mobile: `< 768px`
- Tablet: `768px – 1024px`
- Desktop: `> 1024px`

Los mixins `respond-to(mobile|tablet|desktop)` aplican ajustes en tipografías, grillas y espaciados.

## Accesibilidad

- `skip-link` para navegación por teclado
- `:focus-visible` para resaltar el foco
- `aria-label` en navs y `aria-expanded` en listas colapsables
- Contraste adecuado en textos y fondos

## SEO

- Meta description y title únicos por página
- `alt` descriptivo en todas las imágenes
- Canonical y Open Graph/Twitter en `discografia.html`
- JSON‑LD (`WebSite` en `index.html` y `CollectionPage` en `discografia.html`)

## Discografía: filtros y listas

- Filtros por década usando chips (`Todos`, `Años 80`, `Años 90`, `Años 2000`)
- Cada tarjeta usa `data-decade` para mostrarse/ocultarse
- Listas de canciones con `<details>/<summary>` y acordeón global (solo una abierta a la vez)

## Imágenes

- Portadas con `aspect-ratio: 1/1` y `object-fit: cover` para uniformidad
- `loading="lazy"` para mejorar rendimiento
- Preload del hero del home en `index.html` para mejorar LCP

## Cambiar imágenes de hero

- Home: `scss/_pages.scss` en el bloque `.hero` (`url("../img/soda_header.jpg")`)
- Páginas internas: `scss/_layout.scss` (`.page-hero--banda`, `--discografia`, `--contacto`)

## Scripts disponibles

- `npm run sass`: Ejecuta `sass --watch scss/styles.scss css/styles.css`

## Buenas prácticas del código

- BEM sencillo en clases
- Nesting moderado en SASS
- Variables y mixins para consistencia
- `@extend` con `%grid-3cols` para grillas reutilizables

## Créditos

- Contenidos y descripciones basados en Wikipedia (discografía y giras)
- Imágenes de portadas y recursos visuales en `img/`
