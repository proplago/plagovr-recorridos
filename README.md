# PLAGO VR · Recorridos web

Sitio estático publicado en **Cloudflare Pages** con el dominio **apps.plagovr.com**.
Cada `git push` a `main` publica solo (Cloudflare construye desde este repo; no hay paso de build).

## Ligas oficiales (las únicas que se comparten)

| Proyecto | Liga | Para |
|---|---|---|
| El Jalisciense · piso 29 (GOOD / BEST) | https://apps.plagovr.com/el-jalisciense/ | Steelcase → cliente |
| MEGAEMPEÑOS | https://apps.plagovr.com/megaempenos/ | Steelcase → cliente |
| Ware Malcomb · piso 10 | https://apps.plagovr.com/ware-malcomb/ | Steelcase → cliente |

- La portada (`apps.plagovr.com`) **no lista proyectos**: cada cliente solo conoce su liga.
- Todo lleva `noindex` (meta + cabecera `X-Robots-Tag` + `robots.txt`).
- Respaldo: `https://plagovr-recorridos.pages.dev/<proyecto>/` (mismo contenido, dominio de Cloudflare).

## Ligas retiradas (ya no funcionan, no usar)

- `https://proplago.github.io/plagovr-recorridos/…` — GitHub Pages apagado (7-oct-2026).
- `…/el-jalisciense-dev/` — la versión dev pasó a ser la oficial; redirige a `/el-jalisciense/`.
- `…/prueba/` — eliminada.

## Estructura

- `<proyecto>/index.html` + `app.js` (visor three.js 0.170 empaquetado con esbuild, sin CDN externos)
- `<proyecto>/models/*.glb`, `data/`, `renders/`, `brand/`, `draco/` (decodificador local)
- `_headers`, `_redirects`, `404.html`, `robots.txt`: configuración de Cloudflare Pages.

## Por qué Cloudflare y no GitHub Pages

En datos móviles (Telcel, iPhone) GitHub Pages con dominio propio fallaba (IPv6/AAAA y certificado).
Cloudflare sirve el dominio desde su propia red con certificado propio y responde bien por IPv4 e IPv6.

## Agregar un proyecto nuevo

1. Copiar la carpeta del visor a `/<nombre-proyecto>/` (minúsculas, guiones).
2. `git add -A && git commit -m "..." && git push`.
3. Compartir `https://apps.plagovr.com/<nombre-proyecto>/` solo con ese cliente.
