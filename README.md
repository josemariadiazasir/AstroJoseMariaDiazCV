# CV — José María Díaz Moreno

Página de CV en **Astro + Tailwind CSS**, de una sola página (`/`), con navbar flotante, modo claro/oscuro persistente y animaciones de aparición al hacer scroll.

🔗 Secciones: **Inicio · Sobre mí · Experiencia · Educación · Tecnologías · Contacto**

## Stack

- [Astro](https://astro.build) 5 (salida estática)
- [Tailwind CSS](https://tailwindcss.com) 3
- Tipografía: [Space Grotesk](https://fontsource.org/fonts/space-grotesk-variable) (títulos/cuerpo) + [JetBrains Mono](https://fontsource.org/fonts/jetbrains-mono) (fechas y etiquetas)
- Iconos: SVG propios (estilo _tabler_) + badges _devicon_ para tecnologías (React, TypeScript, Node.js, MongoDB, Docker, HTML, CSS)

## Cómo ejecutarlo en local

```bash
npm install
npm run dev
```

Abre [http://localhost:4321](http://localhost:4321)

## Build de producción

```bash
npm run build   # genera dist/
npm run preview # sirve dist/ en local para comprobarlo
```

`dist/` es 100% estático: se puede desplegar en Vercel, Netlify, Cloudflare Pages, GitHub Pages, etc.

## Estructura

```
src/
  components/
    Hero.astro            # Foto, título, stats, botón "Descargar CV", redes
    About.astro            # Bio + foto secundaria + iconos de stack (Node.js/MongoDB primero)
    Experience.astro       # Datos de los 5 puestos (timeline)
    ExperienceItem.astro   # Item individual de la línea de tiempo
    Education.astro        # Formación reglada + complementaria
    Technologies.astro     # Skills agrupados por categoría (Lenguajes, Frontend, Backend...)
    Extras.astro           # Idiomas, aptitudes, otra información
    Contact.astro          # Enlaces directos (email, teléfono, LinkedIn, GitHub)
    Navbar.astro / Footer.astro
    SectionContainer.astro / TitleSection.astro   # wrappers de sección
    Badge.astro / SocialPill.astro / SkillPill.astro   # piezas de UI reutilizables
    ThemeSwitcher.astro    # toggle claro/oscuro (persistido en localStorage)
    icons/                 # SVGs (navegación, contacto) + badges devicon de tecnologías
  layouts/
    Layout.astro           # HTML base, variables de color, fondo, fuentes, animaciones globales
  pages/
    index.astro             # ensambla todas las secciones

public/
  profile.webp                     # foto (solo para meta og:image)
  cv-jose-maria-diaz-moreno.pdf    # CV descargable (botón del Hero)

src/assets/
  profile.webp            # misma foto, usada por <Image> (optimización de Astro)
```

## Personalización rápida

| Qué cambiar                                          | Dónde                                                                                                                                                                                               |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Colores** (`--red`, `--dark-blue`, `--light-blue`) | `src/layouts/Layout.astro` (`:root`) — ⚠️ hay algunos valores en `rgba()` sueltos en `SkillPill.astro`, `Education.astro` y `ExperienceItem.astro` que no siguen la variable y hay que tocar a mano |
| **Fondo** (degradado radial)                         | `src/layouts/Layout.astro`, busca `radial-gradient`                                                                                                                                                 |
| **Tipografía**                                       | Import en `Layout.astro` + paquete en `package.json` + `tailwind.config.mjs` (para `font-mono`)                                                                                                     |
| **Experiencia laboral**                              | `src/components/Experience.astro` (array `jobs`)                                                                                                                                                    |
| **Educación**                                        | `src/components/Education.astro`                                                                                                                                                                    |
| **Tecnologías / skills**                             | `src/components/Technologies.astro` (array `categories`)                                                                                                                                            |
| **Foto de perfil**                                   | Reemplaza `src/assets/profile.webp` **y** `public/profile.webp` (cuadrada, 600×600 recomendado)                                                                                                     |
| **CV descargable**                                   | Reemplaza `public/cv-jose-maria-diaz-moreno.pdf`                                                                                                                                                    |
| **Enlaces sociales**                                 | `src/components/Hero.astro`, `Footer.astro`, `Contact.astro`                                                                                                                                        |

## Notas

- No incluye formulario de contacto con backend (requeriría API/claves de correo tipo Resend); el contacto es directo vía `mailto:` / `tel:` / LinkedIn / GitHub.
- El proyecto ignora `node_modules/`, `dist/`, `.astro/` y variables de entorno vía `.gitignore`.
