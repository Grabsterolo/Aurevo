# Aurevo

Landing page del estudio **Aurevo** — diseño y desarrollo web orientado a conversión.

**Producción (Cloudflare Pages):** https://aurevo-3nr.pages.dev

## Requisitos

- [Node.js](https://nodejs.org/) 18+ (opcional, solo para servidor local)

## Desarrollo local

```bash
npm install
npm run dev
```

Abre [http://localhost:3000](http://localhost:3000).

## Personalizar antes de publicar

Edita `index.html` y actualiza:

| Elemento | Ubicación aproximada |
|----------|----------------------|
| Enlace de Calendly | `#contact` → `https://calendly.com/...` |
| WhatsApp | `#contact` → `https://wa.me/...` |
| Email | footer → `hello@aurevo.studio` |
| Dominio en SEO | Tras conectar dominio propio, ver [CLOUDFLARE.md](./CLOUDFLARE.md) |

## Despliegue en Cloudflare Pages

El sitio está pensado para **Cloudflare Pages** (HTML estático, sin build real).

Guía completa (reconectar Git, secrets de GitHub Actions, dominio propio): **[CLOUDFLARE.md](./CLOUDFLARE.md)**

Resumen rápido:

| Ajuste en Cloudflare | Valor |
|----------------------|--------|
| Framework preset | None |
| Build command | *(vacío)* |
| Build output directory | `.` |
| Rama | `main` |

Archivos clave: `wrangler.toml`, `_redirects`, `_headers`, workflow `.github/workflows/cloudflare-pages.yml`.

### Si Git aparece “disconnected” en Cloudflare

1. **Reconectar** en Cloudflare → Settings → Builds, **o**
2. Usar el **workflow de GitHub Actions** con `CLOUDFLARE_API_TOKEN` y `CLOUDFLARE_ACCOUNT_ID` (instrucciones en `CLOUDFLARE.md`).

## Otros hosts

También compatibles: Netlify (`netlify.toml`), Vercel (`vercel.json`).

## Estructura

```
├── index.html
├── 404.html
├── favicon.svg
├── wrangler.toml       # Cloudflare Pages
├── _redirects          # 404 en Cloudflare
├── _headers            # Seguridad y caché
├── robots.txt
├── sitemap.xml
├── CLOUDFLARE.md       # Guía de despliegue
└── .github/workflows/cloudflare-pages.yml
```

## Licencia

Todos los derechos reservados © Aurevo.
