# Hacker Terminal

A dark, green-on-black "hacker terminal" theme for CTFd with a pure-CSS neon
3D cyber grid background (perspective floor, glowing horizon, sky grid, CRT
scanlines, and a scan beam). No canvas, no JavaScript animation loops, no
external libraries — all effects are GPU-composited CSS transforms.

It is a minimal overlay theme: only `base.html` and one stylesheet are
provided; every other template and asset falls back to the built-in `core`
theme (requires `THEME_FALLBACK`, which is CTFd's default).

## Selecting the theme

Admin Panel → Config → Appearance → **Theme** → `hacker-terminal` → Update.

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

Further palette tweaks can be made without editing the theme by overriding the
CSS custom properties (`--ht-neon`, `--ht-bg`, …) in Config → Theme Header.

## Accessibility & readability

- Content sits on near-opaque cards above the background; grid line alphas are
  kept low so foreground text is never compromised.
- `prefers-reduced-motion: reduce` freezes the floor animation and removes the
  scan beam.
- Colors are authored in `oklch()` with hex fallbacks for older browsers.
