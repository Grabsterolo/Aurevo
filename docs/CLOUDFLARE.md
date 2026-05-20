# Despliegue en Cloudflare Pages

Proyecto en producción: **https://aurevo-3nr.pages.dev**

El sitio publicable vive en la carpeta **`public/`**. Cloudflare debe usar esa carpeta como salida de build.

## Configuración de build en Cloudflare

| Campo | Valor |
|-------|--------|
| Framework preset | None |
| Build command | *(vacío)* |
| **Build output directory** | **`public`** |
| Rama | `main` |

`wrangler.toml` en la raíz del repo ya define `pages_build_output_dir = "public"`.

## Reconectar Git (si aparece “disconnected”)

1. [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → **aurevo-3nr**
2. **Settings** → **Builds** → **Connect to Git** / **Reconnect**
3. Repo `Grabsterolo/Aurevo`, rama `main`, salida **`public`**

## Deploy con GitHub Actions

Workflow: `.github/workflows/cloudflare-pages.yml` (publica el directorio `public/`).

Secrets en GitHub → **Settings** → **Secrets and variables** → **Actions**:

| Nombre | Valor |
|--------|--------|
| `CLOUDFLARE_API_TOKEN` | Token con permiso Pages → Edit |
| `CLOUDFLARE_ACCOUNT_ID` | Account ID del dashboard |

## Dominio personalizado (aurevo.studio)

1. Cloudflare → **Custom domains** → añade `aurevo.studio`
2. Actualiza URLs en `public/index.html`, `public/robots.txt` y `public/sitemap.xml`

## Despliegue manual con Wrangler

```bash
npm install -g wrangler
wrangler login
wrangler pages deploy public --project-name=aurevo-3nr
```

## Archivos en `public/`

| Archivo | Uso |
|---------|-----|
| `index.html` | Página principal |
| `404.html` | Error 404 |
| `_redirects` | Rutas → 404 personalizada |
| `_headers` | Seguridad y caché |
| `assets/` | Favicon e imágenes futuras |
