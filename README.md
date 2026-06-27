# 👾 Maintenance Page — 80s Arcade Edition

A single-file HTML maintenance page styled as a retro 80s arcade game. No build tools, no dependencies beyond a Google Fonts request.

## Preview

Drop `index.html` in any web server root (or just open it directly in a browser) and it works immediately.

## Features

| Effect | How it works |
|---|---|
| Perspective grid floor | CSS `transform: perspective rotateX` on a repeating-linear-gradient |
| Twinkling stars | JS-generated `div` elements with randomised CSS animation durations |
| CRT scanlines + vignette | Fixed `::` overlay divs using `repeating-linear-gradient` and `radial-gradient` |
| Screen flicker | Keyframe animation that fires a quick opacity spike every ~8 seconds |
| Neon glow title | Layered `text-shadow` with a pulsing keyframe |
| Animated divider | `background-position` slide on a gradient stripe |
| Fake restore progress bar | CSS `@keyframes` with `steps(1)` to simulate chunky arcade loading |
| Live counters | Vanilla JS `setInterval` — high score, elapsed time, tickets crushed |
| Floating aliens | CSS `animation: float` with per-element `--fd` custom property for stagger |

## Customisation

**Change the message** — edit the `<p class="msg-line">` block inside `.msgbox`.

**Change the estimated return time** — find `SOON™` and replace it with a real date/time string.

**Swap the color palette** — all colors are CSS custom properties at the top of `<style>`:

```css
:root {
  --cyan:    #00ffff;
  --magenta: #ff00ff;
  --yellow:  #ffff00;
  --green:   #39ff14;
  --orange:  #ff6600;
  --bg:      #0a0010;
}
```

**Disable the Google Fonts request** (offline/intranet use) — remove the `<link>` tag and add a local fallback:

```css
font-family: 'Courier New', monospace;
```

## Deployment

The page is fully self-contained (one `.html` file). Serve it from any static host, CDN, or directly from your web server's document root while the real app is down.

Nginx example:

```nginx
error_page 503 /maintenance.html;
location = /maintenance.html {
    root /var/www/maintenance;
    internal;
}
```

Apache example:

```apache
ErrorDocument 503 /maintenance.html
```

## Browser support

Works in all modern browsers. The `Press Start 2P` font requires a network request to Google Fonts; everything else is pure CSS/JS with no external dependencies.
