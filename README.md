# Aurevo

Landing page del estudio **Aurevo** — diseño y desarrollo web orientado a conversión.

## Requisitos

- [Node.js](https://nodejs.org/) 18+ (solo para el servidor local de desarrollo)

## Desarrollo local

```bash
npm install
npm run dev
```

Abre [http://localhost:3000](http://localhost:3000).

También puedes abrir `index.html` directamente en el navegador, aunque un servidor local evita problemas con rutas absolutas (favicon, 404).

## Personalizar antes de publicar

Edita `index.html` y actualiza:

| Elemento | Ubicación aproximada |
|----------|----------------------|
| Enlace de Calendly | `#contact` → `https://calendly.com/...` |
| WhatsApp | `#contact` → `https://wa.me/...` |
| Email | footer → `hello@aurevo.studio` |
| Dominio en SEO | meta `canonical`, `og:url`, `robots.txt`, `sitemap.xml` |

## Despliegue

El sitio es **estático** (HTML, CSS y JS en un solo archivo). Opciones:

### GitHub Pages

1. En el repositorio: **Settings → Pages → Build and deployment → GitHub Actions**
2. Haz push a `main`: el workflow `.github/workflows/pages.yml` publica automáticamente

### Netlify / Vercel

- Conecta el repo; no hace falta comando de build
- Directorio de publicación: raíz del proyecto (`.`)
- `netlify.toml` y `vercel.json` ya están configurados

## Estructura

```
├── index.html          # Página principal
├── 404.html            # Página de error
├── favicon.svg         # Icono del sitio
├── robots.txt
├── sitemap.xml
├── package.json        # Scripts de desarrollo
└── .github/workflows/  # CI para GitHub Pages
```

## Licencia

Todos los derechos reservados © Aurevo.
