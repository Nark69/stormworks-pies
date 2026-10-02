# PIES — Paintable Indicator Editor for Stormworks

A free, open-source pixel editor for designing paintable sign mosaics in Stormworks: Build and Rescue. 14 tools including pencil, fill, eyedropper, line, rectangle, circle/ellipse, text (4 bitmap fonts), select with cut/copy/paste, lock, undo/redo, and more. Paint on a real 9×9-per-block canvas, import/export vehicle XML with auto-wired microcontrollers, and share your designs as one-click vehicle files. Single HTML file, runs in any browser.

## Features

### Stormworks-Specific

- Canvas measured in blocks (9×9 pixels each), up to 100×100 blocks
- Export produces a vehicle XML you can paste straight into the workbench
- Microcontroller block auto-placed and auto-wired to every sign with logic links
- Supports both sign (indicator, with glow layer + logic slots) and sign_na output
- Imports remember the original orientation and placement — walls stay walls after re-export
- Locked tiles for non-paintable blocks; paintable tiles unlocked on demand

### Editing Tools

- Pencil, flood fill, eyedropper
- Line, rectangle, circle/ellipse shapes (Shift constrains, Alt fills)
- Text with four bitmap fonts and adjustable letter spacing
- Select with cut, copy, paste, delete
- Lock/unlock tiles
- Checker fill toggle for pattern fills (fill tool + shape fills)
- Ctrl+click color picker with any tool active

### Layers & Preview

- Separate background and glow layers
- Additive "both" preview
- Glow brightness darkening for better in-game contrast

### Transform

- Move (wrap-around shift), 90° rotate
- Mirror left-right / top-bottom
- Shift+line snaps to 45° angles
- Circle preview shows crosshair when shape is a perfect circle

### History & Shortcuts

- 500-step undo/redo
- Full keyboard shortcuts (see below)

### Convenience

- Live XML preview panel, one-click copy, file download
- PNG snapshot of the canvas
- Projects save/load as JSON files
- Automatic browser save (localStorage)

## Getting Started

1. Download `pies.html` from this repository
2. Open it in any browser — no install, no server required
3. Paint or import, then copy the XML from the right-hand panel and paste it into your vehicle in the workbench

Single HTML file, MIT licensed.

## Importing

Load any vehicle XML containing paintable sign or indicator blocks. Block positions, rotations, background and glow pixel data are reconstructed so the picture matches exactly what you see in-game. Non-paintable blocks and empty spots become locked tiles (red-tinted) — they cannot be painted by accident and are skipped on export, so your vehicle keeps its original shape.

## Keyboard Shortcuts

| Key | Tool | Key | Tool |
|-----|------|-----|------|
| `P` | Pencil | `[` | Background layer |
| `F` | Fill | `]` | Glow layer |
| `I` | Eyedropper | `=` | Both layers |
| `L` | Line | `Z` | Zoom in |
| `R` | Rectangle | `Q` | Zoom out |
| `C` | Circle/Ellipse | `G` | Toggle glow preview |
| `S` | Select | `1-5` | Recent colors |
| `T` | Text | `Ctrl+Z` | Undo |
| `K` | Lock | `Ctrl+Y` | Redo |
| `X` | Swap colors | `Ctrl+A` | Select all |
| `Delete` | Clear selection | `Ctrl+C` / `Ctrl+V` / `Ctrl+X` | Copy / Paste / Cut |
| `Shift` | Snap line to 45° | `Alt` | Fill shape (release to apply) |
| `Ctrl+click` | Pick color | | |

## License

MIT License — see [LICENSE](LICENSE) for details.
