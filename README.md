# axiom-assets

Banco público de fuentes e iconos de la familia Axiom, para webs, PWA, landings y apps.

Solo contiene recursos de licencia libre; cada paquete conserva su licencia (carpeta `licenses/`). **Nunca se guardan aquí tokens, PIN, claves ni archivos privados de ningún proyecto.**

El índice general está en `catalog.json`.

## Contenido

<!-- PAQUETES:INICIO -->

| Paquete | Tipo | Versión | Licencia |
|---|---|---|---|
| Inter | Fuente | 4.1 | OFL 1.1 |
| JetBrains Mono | Fuente | 2.304 | OFL 1.1 |
| Lucide | Iconos SVG (2052) | descarga del repo, 2026-11 | ISC |
| Phosphor | Iconos SVG (1512 por peso, 6 pesos) | 2.1.1 | MIT |
| Heroicons | Iconos SVG (324 por peso, 2 pesos) | 2.2.0 | MIT |
| Outfit Fonts | Fuente | 1.1 | OFL 1.1 |
| Tabler Icons | Iconos SVG (5491 outline, 1054 filled) | 3.52.0 | MIT |
| Geist Font | Fuente | 1.9.2 | OFL 1.1 |
| Space Grotesk | Fuente | 2.000 | OFL 1.1 |
| Feather | Iconos SVG (287) | 4.29.2 | MIT |
| Iconoir | Iconos SVG (1383 regular, 288 solid) | 7.12.2 | MIT |
| Fraunces | Fuente | 1.000 | OFL 1.1 |

<!-- PAQUETES:FIN -->

## Estructura

<!-- ESTRUCTURA:INICIO -->

```
inter/             web/ (woff2 + inter.css) · variable/ · ttf/ · otf/
jetbrains-mono/    web/ (woff2) · variable/ · ttf/
outfit-fonts/      web/ (woff2) · variable/ · ttf/ · otf/
geist-font/        web/ (woff2) · variable/ · ttf/ · otf/
space-grotesk/     variable/ · ttf/
fraunces/          variable/ · ttf/
icons/
  lucide/          lucide-svg.zip · index.json
  phosphor/        phosphor-<peso>.zip (regular, bold, fill, light, thin, duotone) · index.json
  heroicons/       heroicons-<peso>.zip (outline, solid) · index.json
  tabler-icons/    tabler-icons-<peso>.zip (filled, outline) · index.json
  feather/         feather-svg.zip · index.json
  iconoir/         iconoir-<peso>.zip (regular, solid) · index.json
licenses/          licencias de cada paquete
catalog.json       índice general
_headers           CORS y caché para Cloudflare Pages
```

<!-- ESTRUCTURA:FIN -->

Inter: no se incluyen `Inter.ttc` ni `extras/woff-hinted` (son redundantes con el resto). Las fuentes variables de JetBrains Mono se renombraron sin corchetes (`JetBrainsMono-Variable.ttf`) para que las URL no necesiten codificación. `inter/web/inter.css` es el CSS oficial de Inter con todos los `@font-face` listos (usa rutas relativas).

## Cómo usarlo

**Fuente en una web** (copiando el archivo al proyecto, o sirviendo el repo con Cloudflare Pages):

```css
@font-face {
  font-family: 'Inter';
  src: url('/fonts/InterVariable.woff2') format('woff2');
  font-weight: 100 900;
  font-display: swap;
}
```

`raw.githubusercontent.com` sirve para que Claude o un script descarguen archivos, pero no está pensado como CDN y entrega el CSS como texto plano (el navegador no lo aplica como hoja de estilos). Para producción, copiar los archivos al proyecto o usar Pages.

**Iconos:** buscar el nombre en `icons/<paquete>/index.json` (tiene etiquetas y categorías), bajar el zip del paquete o peso y extraer solo los SVG necesarios. Para webs, lo mejor es copiar esos SVG al proyecto o incrustarlos.

```bash
curl -LO https://raw.githubusercontent.com/Shura404/axiom-assets/main/icons/lucide/lucide-svg.zip
unzip -j lucide-svg.zip 'lucide/house.svg' -d iconos/
```

## Cómo agregar más

1. Crear la carpeta del paquete (fuentes en la raíz, iconos dentro de `icons/`).
2. Guardar su licencia en `licenses/` y dentro de la carpeta.
3. Agregar el paquete a `catalog.json` y a la tabla de arriba.

Power By Axiom
