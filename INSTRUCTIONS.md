# PIES — Paintable Indicator Editor for Stormworks

A free, open-source pixel editor for designing paintable sign mosaics in Stormworks: Build and Rescue. 14 tools including pencil, fill, eyedropper, line, rectangle, circle/ellipse, text (4 bitmap fonts), select with cut/copy/paste, lock, undo/redo, and more. Paint on a real 9×9-per-block canvas, import/export vehicle XML with auto-wired microcontrollers, and share your designs as one-click vehicle files. Single HTML file, runs in any browser.

## Getting Started

1. Download `pies.html` from this repository
2. Open it in any browser — no install, no server required
3. Paint or import, then copy the XML from the right-hand panel and paste it into your vehicle in the workbench

### Using the Export in-Game

1. Place the exported `.xml` file in `%appdata%/Stormworks/data/vehicles/`
2. Load it in Stormworks as a vehicle
3. Copy the blocks with the in-game selection tool

---

## Interface Overview

The editor has four main areas:

- **Left toolbar** — drawing and selection tools
- **Center** — the pixel canvas
- **Right toolbar** — lock, undo/redo, grid, rotate, mirror, move, clear
- **Right panel** — project, import, dimensions, color palette, layers, text, and export settings

---

## Drawing Tools

### Pencil (P)
Paint pixels. Left click uses the primary color, right click the secondary color. Drag to paint a continuous line.

### Fill (F)
Flood fill the connected region of the clicked pixel with the chosen color. When checker pattern fill is active, the fill alternates between primary and secondary colors in a checkerboard pattern.

### Eyedropper (I)
Pick a color from the canvas: left click sets the primary color, right click the secondary. Switches back to the Pencil tool afterwards.

### Quick Pick (Ctrl + click)
Pick a color from the canvas with any tool active, without switching tools. Left click sets the primary color, right click the secondary.

### Line (L)
Click and drag to draw a straight line. Hold **Shift** to snap the angle to 45° increments.

### Rectangle (R)
Click and drag to draw a rectangle outline. Hold **Alt** to fill the shape. Checker pattern fill is respected when active.

### Circle (C)
Click and drag to draw an ellipse. Hold **Shift** to constrain to a perfect circle (crosshair preview shown). Hold **Alt** to fill the shape. Checker pattern fill is respected when active.

### Text (T)
Type your text in the Text panel, pick a font and spacing, then click on the canvas to place it. Left click uses the primary color, right click the secondary. Newlines place lines below each other.

### Select (S)
Drag to select a region, then use Cut / Copy / Paste. Right click deselects.

### Lock (K)
Click (or drag over) tiles to lock or unlock them. Locked tiles are shown with a red tint, cannot be painted and are skipped on XML export.

### Grid (G)
Toggle the pixel grid and the 9-pixel block guide.

---

## Editing

- **Undo / Redo** (`Ctrl+Z` / `Ctrl+Y`) — every stroke or action is one undo step.
- **Cut / Copy / Paste** (`Ctrl+X` / `Ctrl+C` / `Ctrl+V`) — operate on the current selection; paste inserts the copied region.
- **Clear all** — empties both the Background and the Glow layer.
- **Move** — the arrow buttons shift the active layer by one pixel, wrapping around the edges.
- **Rotate** — the rotate buttons turn the whole canvas by 90° clockwise or counter-clockwise.
- **Mirror** — the mirror buttons flip the canvas left-right or top-bottom.

---

## Colors

- **Primary** (left click) and **Secondary** (right click) colors; switch them with **Swap** (`X`).
- **Checker fill toggle** (⊞) — when active, flood fill and shape fills alternate between primary and secondary colors in a checkerboard pattern.
- **Palette**: left click a swatch to make it the primary color, right click to make it the secondary. Double-left-click sets the swatch itself to the current primary color, double-right-click sets it to the secondary color.
- **Highlighting**: hovering a swatch tints every canvas pixel of that color; hovering the canvas outlines the matching palette swatches.
- **Readout**: below the palette shows the swatch, hex value, and x/y coordinates of the hovered pixel — or of the primary color when the cursor is not over the canvas.

---

## Glow (Layers)

- **Background (off)** and **Glow (on)** select the active drawing layer; **Show both** blends both layers additively for visualization (it does not change the layer you draw on).
- **Background → Glow** / **Glow → Background** copy one layer onto the other.
- Keyboard shortcuts: `[` for Background, `]` for Glow, `=` for Both.

---

## Text

Pick one of the four bundled 8×8 pixel fonts, adjust the letter spacing (px), type your text and place it with the Text tool. The text preview box on the canvas shows the occupied area before you click.

**Fonts:**
- **8x8 Standard** — IBM PC / VGA font
- **8x8 Spectrum** — ZX Spectrum 48K system font
- **8x8 Micro** — compact variant
- **8x8 Classic** — another classic variant

---

## Dimensions

Width and Height are measured in blocks (1 block = 9×9 pixels). **Apply** resizes the canvas; existing pixels stay at the top-left and new space is added as black. Each side is limited to 100 blocks (900 pixels).

---

## Import

### Image Import
Paints a picture onto the active layer (Background or Glow). Choose between:
- **Stretch to canvas** — fits the image to the whole project
- **Expand canvas to fit** — grows the project in whole blocks from the top-left (warns if the result exceeds 100×100 blocks)

Any format your browser can decode works (PNG, JPEG, GIF, WebP, BMP, AVIF); GIFs use the first frame. After an import the palette is rebuilt from the image's most frequent, distinct colors.

### XML Import
Rebuilds the project from a Stormworks vehicle XML that contains paintable sign or indicator blocks. It reads the block positions, the `gc` (background) and `gca` (glow) pixel data, and applies each block's rotation (`r`) so the imported image matches how it is displayed in-game.

- Non-paintable blocks and empty spots become locked tiles (red); unlock them with the Lock tool to paint there
- The original orientation (wall, ceiling or floor) and placement are remembered and reproduced on export
- Rotating, mirroring or resizing the canvas afterwards returns to a centered floor mosaic

---

## Export

### Export Options
- **Paintable Sign (bg only)** — exports only the Background layer
- **Paintable Indicator (bg + glow)** — also exports the Glow layer
- Locked tiles are skipped — no sign block is generated for them

### Microcontroller
- **Add control microcontroller** (indicators only) wires the blocks to a group-switch microcontroller

### Glow Settings
- **Darken glow** and the **Glow brightness** slider make the glow layer match the game's dimmed glow rendering

### Export Actions
- **Export XML** — saves `pies_out-WxH.xml`
- **Generate & Copy** — fills the text field and copies it to the clipboard
- **PNG** — exports the current canvas as an image file

---

## Project

- **Save** stores the project in the browser and downloads a `.json` file
- **Load** restores from a file. The last saved project is restored automatically when the page opens
- **Debug: Reset** clears the saved data and reloads the editor

---

## View

The status bar shows the project size in blocks and pixels and the size of the generated XML. **Zoom** (− / dropdown / +) adjusts the canvas display size between 12.5% and 400%; the **mouse wheel** anywhere in the middle area zooms as well. **1:1** shows every pixel at its exact size without the grid. Above 100%, drag with the **middle mouse button** to pan the canvas.

---

## Keyboard Shortcuts

| Key | Action | Key | Action |
|-----|--------|-----|--------|
| `P` | Pencil | `[` | Background layer |
| `F` | Fill | `]` | Glow layer |
| `I` | Eyedropper | `=` | Both layers |
| `L` | Line | `Z` | Zoom in |
| `R` | Rectangle | `Q` | Zoom out |
| `C` | Circle/Ellipse | `G` | Toggle grid |
| `S` | Select | `1-5` | Recent colors |
| `T` | Text | `Ctrl+Z` | Undo |
| `K` | Lock | `Ctrl+Y` | Redo |
| `X` | Swap colors | `Ctrl+A` | Select all |
| `Delete` | Clear selection | `Ctrl+C` / `Ctrl+V` / `Ctrl+X` | Copy / Paste / Cut |
| `Shift` | Snap line to 45° | `Alt` | Fill shape (release to apply) |
| `Ctrl+click` | Pick color | | |

---

## License

MIT License — see [LICENSE](LICENSE) for details.
