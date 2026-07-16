# Red Terminal

The hacker-terminal cyber grid background (3D perspective floor, glowing
horizon, sky grid, CRT scanlines, scan beam — all pure CSS, no JS animation
loops), restyled with the **sigsegv2** theme's identity:

- Colors: near-black `#0a0a0a` background, gray `#9e9e9e` body text, pure red
  `#ff0000` accents, black panels, square corners everywhere.
- Fonts: **AerxTablets** for headings/nav/brand, **Lato** for body text (font
  files bundled in `static/css/vendor/`, same as sigsegv2).

Like hacker-terminal, it is a minimal overlay theme: only `base.html` and its
stylesheets are provided; everything else falls back to the built-in `core`
theme (requires `THEME_FALLBACK`, CTFd's default).

## Selecting the theme

Admin Panel → Config → Appearance → **Theme** → `red-terminal` → Update.

## Configuring from the admin page

Use the **Theme Settings** JSON box on the same Appearance page. All keys are
optional; everything is enabled by default:

```json
{
  "grid_floor": true,
  "sky_grid": true,
  "horizon": true,
  "glow": true,
  "scanlines": true,
  "scan_beam": true,
  "background": true,
  "floor_speed": 2,
  "beam_speed": 14
}
```

- Set any effect key to `false` to disable that layer (`background` kills the
  entire background at once).
- `floor_speed` — seconds per grid cell for the scrolling floor (default 2).
- `beam_speed` — seconds per full scan-beam sweep (default 14).

Palette tweaks work without editing the theme: override the CSS custom
properties (`--rt-neon`, `--rt-bg`, …) in Config → Theme Header.

## Accessibility & readability

- Content sits on opaque black cards above the background; grid line alphas
  are kept low.
- `prefers-reduced-motion: reduce` freezes the floor animation and removes the
  scan beam.
