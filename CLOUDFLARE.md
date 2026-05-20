# Despliegue en Cloudflare Pages

Proyecto en producción: **https://aurevo-3nr.pages.dev**

## Por qué aparece “disconnected from Git”

Cloudflare perdió la conexión con tu cuenta de GitHub (permisos revocados, token caducado, etc.). El sitio puede seguir en línea, pero los pushes **no** despliegan solos hasta reconectar o usar el workflow de GitHub Actions de este repo.

## Opción A — Reconectar Git en Cloudflare (recomendado si quieres deploy nativo)

1. [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → proyecto **aurevo-3nr**
2. **Settings** → **Builds** → **Connect to Git** / **Reconnect**
3. Autoriza GitHub y elige el repo `Grabsterolo/Aurevo`, rama `main`
4. Configuración de build:
   - **Framework preset:** None
   - **Build command:** *(vacío)*
   - **Build output directory:** `.` (raíz)
5. Guarda. El aviso azul debería desaparecer.

Si activas esta opción **y** el workflow de GitHub Actions, tendrás dos despliegues por push. Desactiva uno: en Cloudflare desmarca “Automatic deployments” o elimina el workflow.

## Opción B — Deploy con GitHub Actions (funciona aunque Git esté desconectado)

Este repo incluye `.github/workflows/cloudflare-pages.yml`.

### 1. Crear API token en Cloudflare

1. Dashboard → icono de perfil → **My Profile** → **API Tokens**
2. **Create Token** → plantilla **Edit Cloudflare Workers** (incluye Pages)
3. Permisos: **Account** → **Cloudflare Pages** → **Edit**
4. Copia el token (solo se muestra una vez)

### 2. Obtener Account ID

Dashboard → **Workers & Pages** → columna derecha **Account ID** (o en la URL de Overview).

### 3. Añadir secrets en GitHub

Repo `Grabsterolo/Aurevo` → **Settings** → **Secrets and variables** → **Actions** → **New repository secret**:

| Nombre | Valor |
|--------|--------|
| `CLOUDFLARE_API_TOKEN` | Token del paso 1 |
| `CLOUDFLARE_ACCOUNT_ID` | Account ID del paso 2 |

### 4. Desplegar

Haz push a `main` o en GitHub → **Actions** → **Deploy to Cloudflare Pages** → **Run workflow**.

En Cloudflare puedes **desactivar** “Automatic deployments” del Git roto para evitar duplicados.

## Dominio personalizado (aurevo.studio)

1. Cloudflare → proyecto → **Custom domains** → **Set up a custom domain**
2. Añade `aurevo.studio` (y `www` si quieres)
3. Actualiza en el repo las URLs en `index.html`, `robots.txt` y `sitemap.xml` de `aurevo-3nr.pages.dev` a `https://aurevo.studio/`

## Despliegue manual (opcional)

Con [Node.js](https://nodejs.org/) y Wrangler:

```bash
npm install -g wrangler
wrangler login
wrangler pages deploy . --project-name=aurevo-3nr
```

## Archivos de configuración

| Archivo | Uso |
|---------|-----|
| `wrangler.toml` | Nombre del proyecto y directorio de salida |
| `_redirects` | Página 404 personalizada |
| `_headers` | Cabeceras de seguridad y caché |
