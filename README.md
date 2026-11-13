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

<!-- PAQUETES:FIN -->

## Estructura

<!-- ESTRUCTURA:INICIO -->

```
inter/             web/ (woff2 + inter.css) · variable/ · ttf/ · otf/
jetbrains-mono/    web/ (woff2) · variable/ · ttf/
icons/
  lucide/          lucide-svg.zip · index.json
  phosphor/        phosphor-<peso>.zip (regular, bold, fill, light, thin, duotone) · index.json
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
