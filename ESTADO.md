# Estado del proyecto: axiom-assets

Última actualización: 2026-11-15 por Claude (con Guille)

> Antes de trabajar, lee `REGLAS.md` del repo `Reglas-Generales`.
> Comprueba la cuenta activa (sección 1.1 de `REGLAS.md`) antes de crear o borrar nada.
> Este archivo se actualiza cambiando solo las líneas que cambian y se sube con `[CI Skip] docs: actualizar estado`.

## Qué es
Banco público de recursos para las PWA y apps de la familia Axiom: fuentes (Inter, JetBrains Mono, Outfit, Geist, Space Grotesk, Fraunces), iconos (Lucide, Phosphor, Heroicons, Tabler, Feather, Iconoir) y 8 temas de estilo listos para aplicar. Se sirve con Cloudflare Pages.

## Hecho
- Banco de fuentes e iconos cargado con licencias y `catalog.json` (13-nov).
- Publicado en Cloudflare Pages: proyecto `axiom-assets`, rama `main`, sin comando de build, directorio de salida la raíz.
- Carpeta `themes/` con 8 temas, cada uno en claro y oscuro: `esmeralda-noche`, `tinta-ultramar`, `calavera`, `arcade-neon`, `grafito-ambar`, `oceano-coral`, `vino-rosado`, `mono-hielo`.
  - Archivos: `themes/<id>.css`, `all.css` (todos juntos), `base.css` (arranque con componentes), `fonts.css` (@font-face con rutas del repo), `preview.html` y `README.md`.
  - Índice de todos los valores en `themes-catalog.json`, en la raíz del repo.
  - Variables con prefijo `--ax-*`; se aplican con `<html data-theme="<id>" data-mode="dark|light|auto">`.
- Contraste revisado con script (WCAG AA): texto principal 7:1 o más; texto suave, acento como texto y estados 4,5:1 o más. Vista previa comprobada en móvil (360, 390 y 820 px) sin desbordes.
- Rutas de Fraunces corregidas a `fraunces/variable/` en `fonts.css`, README y catálogo (commit `13b5779`). Desplegado a mano en Cloudflare (1 build).
- Vista previa abierta desde el móvil: `axiom-assets.pages.dev/themes/preview.html` (se puede abrir un tema directo, por ejemplo `#calavera/dark`).
- Acceso de GitHub a Cloudflare Pages resuelto y verificado: el push `dd9b145` llegó a Pages como `github:push` y se omitió por `[CI Skip]`, sin gastar build.

## En curso
- Nada abierto.

## Siguiente paso
1. **Confirmar el primer build automático.** El aviso de GitHub ya llega a Pages; falta ver que un commit con `deploy:` construya solo. Hasta ahora los únicos builds son manuales (`ad_hoc`). Si no construye, revisar el proyecto en Cloudflare.
2. **Desactivar las vistas previas del proyecto Pages** (Settings → Builds → Branch control → Preview branch: None), como pide `GUIA-CLOUDFLARE.md` §4.2. Hoy están en "todas las ramas".
3. **Listar `themes/` en el README del repo** (tabla y estructura, entre los marcadores que regenera Asset Dock) y decidir si `catalog.json` también los menciona.
4. **Theme Dock** (propuesto, falta confirmar que se construye): tercera herramienta de Axiom Deck, junto a Asset Dock y Repo Dock, para crear temas nuevos sin depender de Claude. Flujo: escribir un nombre y pegar 3 o 4 colores (fondo, acento, acento 2) o importar una paleta libre (Catppuccin, Rosé Pine, Nord, Tokyo Night, Radix), generar claro y oscuro, corregir solos los contrastes por debajo de 4,5:1, añadir el tema a `themes-catalog.json` sin tocar los demás y entregar un ZIP para Repo Dock. La lógica de contraste y de generación existe en un script de Python que **no está guardado en ningún repo**; hay que portarlo a JS o subirlo antes de empezar.

## Pendientes por verificar
- Que un commit `deploy:` construye solo (el aviso de GitHub ya llega; ver Siguiente paso 1).
- Que Fraunces sigue cargando en Calavera y Vino rosado tras el cambio de ruta (despliegue `29c1f849`).
- Que `_headers` cubre también `themes/` (CORS y caché), si los CSS se van a usar desde otro dominio.

## Datos útiles
- Repo: `Shura404/axiom-assets` (público), rama `main`.
- Dominio: `axiom-assets.pages.dev`.
- Cuenta de Cloudflare: clave activa en AxiomHub que termina en `…sset`, ID de cuenta que termina en `…b504` (comprobar con `check_account`). En esa cuenta hay 3 proyectos de Pages (`axiom-assets`, `shura-axiom`, `reservas-canchas`); el máximo es 8.
- Base D1: ninguna (sitio estático).
- Descarga desde el sandbox de Claude: `https://raw.githubusercontent.com/Shura404/axiom-assets/main/` (probado; la API de GitHub sin autenticar da 403).
- Subida de archivos: Claude entrega un ZIP descargable; Guille lo sube con Repo Dock (Axiom Deck) con **Sincronizar desmarcado**. Asset Dock solo procesa fuentes e iconos, no temas.
- Commits: los intermedios con `[CI Skip]`; el final de una entrega con `deploy:`. Cada commit sin marca gasta un build (límite gratuito: 500 al mes).
- Frase para pedirle un tema a Claude: «Aplica el tema `calavera` (modo oscuro) de Shura404/axiom-assets a esta PWA. Lee `themes-catalog.json` y `themes/calavera.css`, reemplaza todos los colores fijos por variables `--ax-*`, usa las fuentes del tema y no inventes colores.»
