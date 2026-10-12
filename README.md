# Sitio web de ACL Engineering

Sitio estático (HTML + CSS, sin build ni dependencias) pensado para presencia digital y SEO local en Los Cabos y La Paz, B.C.S.

## Archivos
- `index.html` — inicio en español: servicios, zonas, proyectos, cómo trabajamos, FAQ y contacto. Contiene el JSON-LD de `LocalBusiness`, `WebSite` y `FAQPage`.
- `automatizacion-residencial-los-cabos.html`, `control-de-iluminacion-lutron.html`, `audio-y-video.html`, `redes-y-seguridad.html` — una página por servicio / palabra clave, cada una con `Service`, `BreadcrumbList` y `FAQPage`.
- `la-paz.html` — página de zona para La Paz.
- `en/index.html` — portada en inglés (propietarios extranjeros), enlazada con `hreflang`.
- `styles.css`, `img/logo-acl.png`, `404.html`.
- `sitemap.xml`, `robots.txt` — para Google/Bing. `llms.txt` — resumen para asistentes de IA (ChatGPT, Claude, Perplexity…).

Cada página repite su propio `<header>` y `<footer>`; si cambias el menú, cámbialo en los 7 HTML. El teléfono (+52 624 155 8139) y el correo (acl.ingenieria@outlook.com) aparecen en todas las páginas: búscalos y reemplázalos si cambian.

## Dominio
Todas las URLs absolutas usan `https://www.aclengineering.com`. Si el dominio comprado en GoDaddy es otro, reemplázalo en todos los archivos:

```bash
cd acl-web && grep -rl "www.aclengineering.com" . | xargs sed -i '' 's|www.aclengineering.com|TU-DOMINIO.com|g'
```

## Probar en local
```bash
python3 -m http.server 8080 --directory acl-web
```
y abre http://localhost:8080

## Publicar
Opción A — **Hosting de GoDaddy (cPanel)**: entra a cPanel → Administrador de archivos → `public_html` y sube el contenido de `acl-web/` (los archivos, no la carpeta). Activa el certificado SSL gratuito en GoDaddy.

Opción B (recomendada, gratis y más rápida) — **Cloudflare Pages / Netlify / Vercel**: arrastra la carpeta `acl-web/` al panel del servicio, obtén la URL y en GoDaddy → DNS crea un registro `CNAME` de `www` apuntando a esa URL y redirige el dominio raíz a `www`. Si el proyecto está en GitHub, conéctalo para que cada cambio se publique solo.

## Después de publicar (SEO local)
1. Google Search Console: verifica el dominio y envía `sitemap.xml`.
2. Perfil de Negocio de Google (Google Maps) con el mismo nombre, teléfono y categoría "Instalador de sistemas de automatización del hogar"; agrega el sitio web y fotos de proyectos.
3. Bing Webmaster Tools (importa desde Search Console).
4. Pide reseñas a clientes y constructoras; las reseñas pesan mucho en búsquedas locales.
5. Agrega fotos reales de proyectos en `img/` y en las páginas (con `alt` descriptivo: "Keypad Lutron Alisse en villa de Chileno Bay").
