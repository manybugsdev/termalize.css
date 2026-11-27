# termalize.css

Classless CSS for a retro phosphor-terminal look, built on [modern-normalize](https://github.com/sindresorhus/modern-normalize).
Write plain semantic HTML — no classes needed.

**Demo:** https://manybugsdev.github.io/termalize.css/

## Usage

Add one line to your `<head>`:

<!-- x-release-please-start-version -->
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@manybugsdev/termalize.css@0.2.0/dist/termalize.min.css">
```
<!-- x-release-please-end -->

Or install from npm:

```sh
npm install @manybugsdev/termalize.css
```

modern-normalize is bundled into `dist/`, so one stylesheet is all you need.

## Customize

Set `color` and `background-color` on `html`. Every other color
(dim text, borders, accent, glow, highlights) is derived from `currentColor`.

```css
html {
  color: #ffb000;              /* amber */
  background-color: #0d0800;
}
```

### Light and dark

By default termalize.css follows the OS setting (`color-scheme: light dark`):
green-on-black in dark mode, dark green on paper in light mode.
Use `light-dark()` to set your own pair, or pin one scheme with `color-scheme`:

```css
html {
  color: light-dark(#7a4a00, #ffb000);
  background-color: light-dark(#f5efe2, #0d0800);
}

html {
  color-scheme: dark;          /* always dark */
}
```

If you set plain (non-`light-dark()`) colors, also set `color-scheme` to
match them, since accents and glow are tuned per scheme.

Other custom properties:

```css
:root {
  --term-width: 80ch;          /* max content width */
  --term-scanline-opacity: 0.12;
  --term-font: ui-monospace, monospace;
}
```

## Fonts

termalize.css does not name any web font: it uses the system monospace font
unless you set `--term-font`. Load a font yourself and put it first:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=VT323&display=swap">
<style>
  :root { --term-font: 'VT323', ui-monospace, monospace; }
</style>
```

Set it on `:root` (not `html`) so it overrides the default token.

Recommended fonts:

| Font | Style | Scripts |
| --- | --- | --- |
| [VT323](https://fonts.google.com/specimen/VT323) | Pixel, DEC VT320 terminal | Latin |
| [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono) | Clean monospace | Latin |
| [DotGothic16](https://fonts.google.com/specimen/DotGothic16) | Pixel | Latin + Japanese |
| [M PLUS 1 Code](https://fonts.google.com/specimen/M+PLUS+1+Code) | Monospace | Latin + Japanese |

For Japanese text, use a font that covers both scripts (DotGothic16 or M PLUS 1 Code)
so half-width Latin and full-width Japanese line up on one grid.
Pairing a Latin-only font with a Japanese fallback mixes two designs and sizes.

All of these are also available from [Fontsource](https://fontsource.org/)
for self-hosting, e.g. `npm install @fontsource/dotgothic16`.

## Features

- Light and dark schemes (follows the OS by default)
- CRT scanlines, vignette, glow and subtle flicker (disabled with `prefers-reduced-motion`)
- Markdown-style heading prefixes (`#`, `##`, `###`, …)
- `[link]`-style nav, `[+]/[-]` details, `>` blockquotes
- Shell prompt: `<pre><kbd>cmd</kbd></pre>` renders as `$ cmd`
- Forms, tables, progress bars, dialogs
- Images shown in grayscale
- Print styles without CRT effects

## Development

```sh
npm install
npm run build   # src/termalize.css + modern-normalize -> dist/
```

Open `index.html` for a demo.

## License

MIT. Includes [modern-normalize](https://github.com/sindresorhus/modern-normalize) (MIT, © Sindre Sorhus).
