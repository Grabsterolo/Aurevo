# Aurevo

Sitio web del estudio **Aurevo** — diseño y desarrollo orientado a conversión.

**En vivo:** https://aurevo-3nr.pages.dev

## Estructura

```
public/           Sitio publicado en Cloudflare Pages
├── index.html    Página principal (editar aquí)
├── 404.html
├── robots.txt
├── sitemap.xml
├── _headers      Seguridad y caché
├── _redirects    Página 404 para rutas inexistentes
└── assets/
    └── favicon.svg
wrangler.toml     Configuración Cloudflare (salida: public/)
```

## Editar el sitio

Abre `public/index.html` y actualiza:

- **Calendly** y **WhatsApp** → sección `#contact`
- **Email** → footer
- **SEO** → `<head>`, `public/robots.txt`, `public/sitemap.xml`

## Vista local

Abre `public/index.html` en el navegador, o:

```bash
npx serve public
```

## Cloudflare Pages

| Campo | Valor |
|-------|--------|
| Build command | *(vacío)* |
| Build output directory | `public` |
| Rama | `main` |

Despliegue automático al hacer push a `main` (Git conectado en Cloudflare).

**Dominio propio:** en Cloudflare → Custom domains, luego actualiza las URLs en `public/index.html`, `robots.txt` y `sitemap.xml`.
