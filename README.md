# wally-brand

The shared design system for Wally's tools. One palette, one set of
components, one icon style — so every tool feels like family.

This repo is the **source of truth**. Tools vendor it; they don't fork it.

## What's inside

```
brand/
  brand.css        # design tokens + components (the whole system)
  shell.html       # page shell with {{PLACEHOLDERS}} for serve modes
  icons/
    compass.svg      # the Wally mark (header + footer)
    decide.svg
    wallypedia.svg
    trendwatch.svg
    receiptchain.svg
    walboard.svg
index.html         # living preview of the system (open in a browser)
```

## Design tokens

Warm charcoal + amber. Cream text. System fonts.

| token | value | use |
|---|---|---|
| `--wb-bg` | `#161210` | page background |
| `--wb-surface` | `#26201a` | cards |
| `--wb-amber` | `#f0a832` | primary actions, accents |
| `--wb-cream` | `#f3e9d7` | body text |
| `--wb-muted` | `#a49176` | secondary text |
| `--wb-green` / `--wb-red` / `--wb-blue` | status colors | badges, results |

Full component list (buttons, forms, terminal blocks, distribution bars,
badges, key/value, header/footer, responsive rules): open `index.html`.

## Plugging it into a tool

1. Copy `brand/` into your repo (e.g. `cp -r brand ./brand`).
2. In your `serve` mode:
   - Serve `brand/brand.css` at `/brand.css`
   - Serve `brand/icons/*.svg` at `/icons/*.svg`
   - Render pages from `brand/shell.html`, replacing:
     - `{{PAGE_TITLE}}`, `{{TOOL_NAME}}`, `{{TOOL_TAGLINE}}`
     - `{{COMPASS_SVG}}` — inline contents of `icons/compass.svg`
     - `{{CONTENT}}` — your page body (use the component classes)
     - `{{HEADER_EXTRA}}` / `{{FOOTER_EXTRA}}` — optional
3. Conventions every serve mode follows:
   - `serve --port 8080` (default 8080, overridable)
   - `GET /healthz` → `ok`
   - Same header (compass mark + tool name + tagline), same footer
     ("Built by Wally · wally-dk24").

## Updating

Change it here, then re-vendor into each tool and rebuild. Never edit a
tool's vendored copy directly — the next sync would wipe it.
