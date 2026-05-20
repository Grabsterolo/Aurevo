# Aurevo

Landing page del estudio **Aurevo** — diseño y desarrollo web orientado a conversión.

**Producción (Cloudflare Pages):** https://aurevo-3nr.pages.dev

## Estructura del repositorio

```
├── public/                 # Sitio web (lo que se publica)
│   ├── index.html          # Página principal
│   ├── 404.html
│   ├── robots.txt
│   ├── sitemap.xml
│   ├── _redirects          # Reglas Cloudflare/Netlify
│   ├── _headers            # Cabeceras HTTP
│   └── assets/
│       └── favicon.svg
├── docs/
│   └── CLOUDFLARE.md       # Guía de despliegue
├── .github/workflows/      # CI (Cloudflare Pages)
├── wrangler.toml           # Config Cloudflare
├── package.json            # Scripts de desarrollo local
└── README.md
```

## Desarrollo local

```bash
npm install
npm run dev
```

Abre [http://localhost:3000](http://localhost:3000). El servidor sirve la carpeta `public/`.

## Personalizar el sitio

Edita `public/index.html`:

| Elemento | Ubicación aproximada |
|----------|----------------------|
| Enlace de Calendly | `#contact` |
| WhatsApp | `#contact` |
| Email | footer |
| SEO / dominio | `<head>` y `public/robots.txt`, `public/sitemap.xml` |

## Despliegue (Cloudflare Pages)

| Ajuste en Cloudflare | Valor |
|----------------------|--------|
| Framework preset | None |
| Build command | *(vacío)* |
| **Build output directory** | **`public`** |
| Rama | `main` |

Guía detallada: **[docs/CLOUDFLARE.md](./docs/CLOUDFLARE.md)**

También compatible con Netlify (`netlify.toml`) y Vercel (`vercel.json`).

## Licencia

Todos los derechos reservados © Aurevo.
