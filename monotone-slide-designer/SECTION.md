# Section Divider Slide Spec

## Layout (10" × 5.625")

```
┌─────────────────────────────────────────┐
│                                         │
│   A        │  SECTION                   │  ← dark bg 1A1A1A
│   (huge)   │  Section Title             │
│   333333   │  • Topic 1                 │
│            │  • Topic 2                 │
│            │  • Topic 3                 │
│                                         │
└─────────────────────────────────────────┘
```

## pptxgenjs Implementation

```javascript
// Dark background
slide.background = { color: "1A1A1A" };

// Large background letter
slide.addText("A", {
  x: 0.2, y: -0.3, w: 4.5, h: 6.2,
  fontFace: "Montserrat", fontSize: 280, bold: true,
  color: "333333", margin: 0
});

// White vertical divider
slide.addShape(pres.shapes.RECTANGLE, {
  x: 4.5, y: 0.8, w: 0.06, h: 4.0,
  fill: { color: "FFFFFF" }
});

// Section label
slide.addText("SECTION", {
  x: 5.0, y: 0.8, w: 4.5, h: 0.5,
  fontFace: "Montserrat", fontSize: 24, bold: true,
  color: "888888", charSpacing: 4, margin: 0
});

// Section title
slide.addText("Section Title", {
  x: 5.0, y: 1.4, w: 4.5, h: 1.6,
  fontFace: "Noto Sans JP", fontSize: 44, bold: true,
  color: "FFFFFF", margin: 0
});

// Topic list
slide.addText([
  { text: "■ Topic 1", options: { breakLine: true, fontSize: 20, color: "FFFFFF" } },
  { text: "■ Topic 2", options: { breakLine: true, fontSize: 20, color: "FFFFFF" } },
  { text: "■ Topic 3", options: { fontSize: 20, color: "FFFFFF" } }
], {
  x: 5.0, y: 3.2, w: 4.5, h: 1.8,
  fontFace: "Noto Sans JP", paraSpaceAfter: 8, margin: 0
});
```

## Notes
- Change the letter (A, B, C...) per section
- Letter color `333333` creates subtle contrast on `1A1A1A` bg
- Use `■` (U+25A0) for bullet markers in white
