# Court Society — Landing público

Sitio público de Court Society. Una sola página estática, sin formulario, sin dependencias.

- **Dominio:** `courtsociety.org`
- **Tipo:** estático (HTML + CSS + JS inline)
- **Build:** ninguno
- **Hosting recomendado:** Vercel

El formulario de aplicación vive en un repo aparte, desplegado en `app.courtsociety.org`.

## Estructura

```
courtsociety-landing/
├── index.html       Landing (única página)
├── vercel.json      Headers de seguridad y caching
├── robots.txt       Permite indexación
├── sitemap.xml      Una sola URL
├── .gitignore       Vercel + macOS + editores
└── README.md        Este archivo
```

## Deploy en 3 pasos

```bash
# 1. Crear el repo en GitHub (vacío, sin README)
# 2. Subirlo
cd courtsociety-landing
git init
git add .
git commit -m "Court Society — landing v1"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/courtsociety-landing.git
git push -u origin main

# 3. Importar en Vercel (vercel.com → Add New Project → Import → este repo)
#    Framework: Other  ·  Build command: (vacío)  ·  Output: ./
```

## Conectar el dominio

En Vercel → el proyecto → **Settings → Domains** → agregar:
- `courtsociety.org` (apex)
- `www.courtsociety.org`

Vercel te muestra los registros DNS exactos. En el registrador del dominio:

| Tipo  | Nombre | Valor                   |
|-------|--------|-------------------------|
| A     | `@`    | `76.76.21.21`           |
| CNAME | `www`  | `cname.vercel-dns.com`  |

SSL se emite solo en ~60 segundos.

## Notas

- Todos los CTA de "Apply for Membership" apuntan a `https://app.courtsociety.org` por URL absoluta. Cuando despliegues el subdominio del app, ya quedan conectados.
- El landing no tiene JS de tracking. Si querés Plausible o similar, agregar antes del `</head>`.
- `vercel.json` ya incluye un redirect amigable: `/apply` y `/membership` → `https://app.courtsociety.org`.
