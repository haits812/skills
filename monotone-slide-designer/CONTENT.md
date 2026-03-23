# Content Slide Spec

## Layout (10" × 5.625")

```
┌─────────────────────────────────────────┐
│  PAGE TITLE                         03  │
│─────────────────────────────────────────│ ← 3pt black line
│  ██ LABEL                               │
│  Key Message Text (large)               │
│                                         │
│─────────────────────────────────────────│ ← 1.5pt black line
│  01  Item Title                         │
│      Item description                   │
│ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ │ ← 0.75pt CCCCCC
│  02  Item Title                         │
│      Item description                   │
│─────────────────────────────────────────│ ← 1.5pt black line
└─────────────────────────────────────────┘
```

## pptxgenjs Implementation — Numbered List

```javascript
slide.background = { color: "FFFFFF" };

// --- Header ---
slide.addText("PAGE TITLE", {
  x: 0.8, y: 0.4, w: 7.0, h: 0.5,
  fontFace: "Montserrat", fontSize: 26, bold: true,
  color: "000000", charSpacing: 2, margin: 0
});
slide.addText("03", {
  x: 8.0, y: 0.4, w: 1.2, h: 0.5,
  fontFace: "Montserrat", fontSize: 20, bold: true,
  color: "888888", align: "right", margin: 0
});
slide.addShape(pres.shapes.LINE, {
  x: 0.8, y: 0.95, w: 8.4, h: 0,
  line: { color: "000000", width: 3 }
});

// --- Key Message ---
// Label tag (black bg, white text)
slide.addShape(pres.shapes.RECTANGLE, {
  x: 0.8, y: 1.15, w: 1.2, h: 0.32,
  fill: { color: "000000" }
});
slide.addText("LABEL", {
  x: 0.8, y: 1.15, w: 1.2, h: 0.32,
  fontFace: "Noto Sans JP", fontSize: 14, bold: true,
  color: "FFFFFF", align: "center", valign: "middle", margin: 0
});

slide.addText("Key Message Text", {
  x: 0.8, y: 1.55, w: 8.4, h: 0.8,
  fontFace: "Noto Sans JP", fontSize: 32, bold: true,
  color: "000000", margin: 0
});

// --- Content list ---
// Top border
slide.addShape(pres.shapes.LINE, {
  x: 0.8, y: 2.5, w: 8.4, h: 0,
  line: { color: "000000", width: 1.5 }
});

// Item 1
slide.addText("01", {
  x: 0.8, y: 2.6, w: 0.8, h: 0.7,
  fontFace: "Montserrat", fontSize: 36, bold: true,
  color: "000000", margin: 0
});
slide.addText("Item Title", {
  x: 1.7, y: 2.6, w: 7.5, h: 0.35,
  fontFace: "Noto Sans JP", fontSize: 22, bold: true,
  color: "000000", margin: 0
});
slide.addText("Item description text goes here.", {
  x: 1.7, y: 2.95, w: 7.5, h: 0.35,
  fontFace: "Noto Sans JP", fontSize: 16, color: "4A4A4A", margin: 0
});

// Separator
slide.addShape(pres.shapes.LINE, {
  x: 0.8, y: 3.45, w: 8.4, h: 0,
  line: { color: "CCCCCC", width: 0.75 }
});

// Item 2 (repeat pattern, y += 0.95)
// Item 3 (repeat pattern, y += 0.95)

// Bottom border
slide.addShape(pres.shapes.LINE, {
  x: 0.8, y: 5.3, w: 8.4, h: 0,
  line: { color: "000000", width: 1.5 }
});
```

## Layout Variants

### Two-Column
- Left column: x=0.8, w=4.0
- Right column: x=5.2, w=4.0
- Keep header + key message structure, split only content area

### Three-Column
- Col 1: x=0.8, w=2.6
- Col 2: x=3.6, w=2.6
- Col 3: x=6.4, w=2.6

### Table
Use `slide.addTable()` below the key message area:
- x=0.8, y=2.5, w=8.4
- Header row: fill `000000`, text `FFFFFF`
- Body rows: alternating `FFFFFF` / `F9F9F9`
- Border: `CCCCCC`, 0.75pt

### Large Centered Text
For single-message impact slides:
- Remove content list area
- Single text block: x=0.8, y=1.8, w=8.4, h=3.0, fontSize=48, align="center"
