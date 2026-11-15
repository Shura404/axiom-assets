# themes

Plantillas de estilo para PWA y apps. Cada tema ya trae decididos los colores (fondos, superficies, bordes, texto, acento y estados), las fuentes, los radios y las sombras, en versión oscura y clara. Se aplican sin inventar nada: el cambio de color deja de ser una prueba y error.

Los colores de texto cumplen contraste WCAG AA (texto principal 7:1 o más; texto suave, acento como texto y estados 4,5:1 o más). La revisión se hizo con un script al generar los temas.

## Temas

| Tema | Pensado para | Modo por defecto | Fuentes (paquetes del repo) |
|---|---|---|---|
| `esmeralda-noche` | Finanzas y ahorro con calma: jade sobre tinta verdosa, dorado para destacar. | oscuro | outfit-fonts, inter, jetbrains-mono |
| `tinta-ultramar` | Productividad y paneles claros: papel frío, tinta azul y ultramar. | claro | geist-font |
| `calavera` | Humor con personalidad: berenjena oscura, cempasúchil y rosa mexicano. | oscuro | fraunces, inter, jetbrains-mono |
| `arcade-neon` | Gamer y neón: violeta casi negro, cian eléctrico y rosa. | oscuro | jetbrains-mono, inter |
| `grafito-ambar` | Herramientas técnicas: grafito con ámbar de señal (línea Axiom). | oscuro | space-grotesk, inter, jetbrains-mono |
| `oceano-coral` | Seguridad y confianza: azul marino profundo con coral. | oscuro | outfit-fonts, geist-font |
| `vino-rosado` | Elegante y premium: vino oscuro, rosa y champán. | oscuro | fraunces, geist-font |
| `mono-hielo` | Minimalismo monocromo: blanco o negro; el acento es el contraste. | claro | inter, jetbrains-mono |

## Cómo aplicarlo

1. Copia `themes/<tema>.css` al proyecto y enlázalo. Opcional: `themes/base.css` (arranque con botones, tarjetas, campos y etiquetas).
2. En la etiqueta `<html>`:

```html
<html lang="es" data-theme="calavera" data-mode="dark">
```

`data-mode` puede ser `dark`, `light` o `auto` (sigue al sistema). Sin `data-mode`, usa el modo por defecto del tema.

3. En tu CSS usa solo variables, nunca hex sueltos:

```css
.card { background: var(--ax-surface); border: 1px solid var(--ax-border); border-radius: var(--ax-radius-lg); }
.btn  { background: var(--ax-accent); color: var(--ax-accent-fg); }
.btn:hover { background: var(--ax-accent-hover); }
```

Para cambiar de tema basta cambiar el valor de `data-theme`.

## Variables

- Fondos: `--ax-bg`, `--ax-surface`, `--ax-surface-2`, `--ax-border`
- Texto: `--ax-text`, `--ax-muted`
- Acento: `--ax-accent` (rellenos y bordes), `--ax-accent-fg` (texto encima del acento), `--ax-accent-hover`, `--ax-accent-soft` (fondo suave), `--ax-accent-ink` (acento como texto o ícono pequeño), `--ax-accent2` (segundo color de apoyo)
- Estados: `--ax-success`, `--ax-warning`, `--ax-danger`, `--ax-info`, cada uno con su `-soft` para el fondo
- Otros: `--ax-focus`, `--ax-overlay`, `--ax-shadow-sm`, `--ax-shadow-md`, `--ax-theme-color` (para `<meta name="theme-color">`)
- Tipografía: `--ax-font-display`, `--ax-font-body`, `--ax-font-mono`, `--ax-display-weight`, `--ax-display-tracking`, `--ax-display-vs`
- Formas: `--ax-radius-sm`, `--ax-radius-md`, `--ax-radius-lg`, `--ax-radius-pill`

Los mismos valores están en `themes-catalog.json` (raíz del repo), para leerlos de una vez.

## Pedírselo a Claude

> Aplica el tema `calavera` (modo oscuro) de Shura404/axiom-assets a esta PWA. Lee `themes-catalog.json` y `themes/calavera.css`, reemplaza todos los colores fijos por variables `--ax-*`, usa las fuentes del tema y no inventes colores.

## Vista previa

`themes/preview.html` muestra cada tema en claro y oscuro. Necesita que el repo se sirva por web (por ejemplo con Cloudflare Pages), porque carga las fuentes con rutas relativas. Se puede abrir directo en un tema: `preview.html#vino-rosado/light`.

## Fuentes

`themes/fonts.css` declara las fuentes con rutas relativas a este repo (solo sirve si lo publicas tal cual). En un proyecto, copia los archivos `web/` de cada paquete y ajusta las rutas. Fraunces está en `fraunces/variable/` (archivos `.ttf` variables).
