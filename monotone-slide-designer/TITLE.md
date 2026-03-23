# Title Slide Spec

## Layout (10" × 5.625")

```
┌─────────────────────────────────────────┐
│██████████████████████████████████████████│ ← 0.15" black bar at top
│                                         │
│  [EYEBROW TEXT]          32pt 4A4A4A    │
│  [MAIN TITLE]            60pt 000000    │
│  ▌[SUBTITLE]             28pt 333333    │
│                                         │
│─────────────────────────────────────────│ ← 3pt black line
│  [Name] @handle   [Title/Credentials]   │
└─────────────────────────────────────────┘
```

## pptxgenjs Implementation

```javascript
// Background
slide.background = { color: "FFFFFF" };

// Top black bar
slide.addShape(pres.shapes.RECTANGLE, {
  x: 0, y: 0, w: 10, h: 0.15,
  fill: { color: "000000" }
});

// Eyebrow
slide.addText("EYEBROW TEXT", {
  x: 0.8, y: 1.0, w: 8.4, h: 0.5,
  fontFace: "Noto Sans JP", fontSize: 26, bold: true,
  color: "4A4A4A", charSpacing: 2, margin: 0
});

// Main title
slide.addText("MAIN TITLE", {
  x: 0.8, y: 1.5, w: 8.4, h: 1.4,
  fontFace: "Montserrat", fontSize: 60, bold: true,
  color: "000000", margin: 0
});

// Subtitle with left border
slide.addShape(pres.shapes.RECTANGLE, {
  x: 0.8, y: 3.05, w: 0.06, h: 0.65,
  fill: { color: "000000" }
});
slide.addText("Subtitle text here", {
  x: 1.05, y: 3.0, w: 7.5, h: 0.7,
  fontFace: "Noto Sans JP", fontSize: 28,
  color: "333333", margin: 0
});

// Divider line
slide.addShape(pres.shapes.LINE, {
  x: 0.8, y: 4.2, w: 8.4, h: 0,
  line: { color: "000000", width: 3 }
});

// Speaker info
slide.addText([
  { text: "Speaker Name ", options: { fontFace: "Noto Sans JP", fontSize: 22, bold: true, color: "000000" } },
  { text: "@handle", options: { fontFace: "Montserrat", fontSize: 22, color: "888888" } }
], { x: 0.8, y: 4.45, w: 8.4, h: 0.4, margin: 0 });

slide.addText("Title / Credentials", {
  x: 0.8, y: 4.85, w: 8.4, h: 0.35,
  fontFace: "Noto Sans JP", fontSize: 16, color: "4A4A4A", margin: 0
});
```
