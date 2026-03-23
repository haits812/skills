---
name: monotone-slide-designer
description: Generates monochrome presentation slides as .pptx files. Use when the user asks to create slides, presentations, or decks with a clean black-and-white design. Produces title slides, section dividers, and content slides using Montserrat and Noto Sans JP fonts via pptxgenjs.
---

# Monotone Slide Designer

Generate 16:9 monochrome presentations using pptxgenjs + HTML preview.

## Workflow

1. Plan slide outline (type + content for each slide)
2. Read the relevant design reference from `templates/` for layout specs
3. Generate **2 files** from a single script (or 2 scripts sharing the same slide data):
   - `output/*.pptx` — pptxgenjs で生成。納品用
   - `output/preview.html` — 同じデザイントークン・レイアウトを CSS で再現。VSCode Live Preview で確認用
4. Run QA per the [pptx skill](/mnt/skills/public/pptx/SKILL.md)

## Design References

| Type | File | Use |
|------|------|-----|
| Title | [templates/TITLE.md](templates/TITLE.md) | First slide — title, subtitle, speaker |
| Section | [templates/SECTION.md](templates/SECTION.md) | Dividers — dark bg, large letter |
| Content | [templates/CONTENT.md](templates/CONTENT.md) | Body slides — header, key message, list/grid |

## Rules

- **Palette**: `000000`, `FFFFFF`, grays only (`1A1A1A`, `333333`, `4A4A4A`, `888888`, `CCCCCC`, `E0E0E0`, `F0F0F0`, `F9F9F9`)
- **Fonts**: `Montserrat` for headings, `Noto Sans JP` for body
- **Output**: 必ず .pptx と preview.html の **両方** を生成する。片方だけで完了にしない
- **HTML preview**: 960×540px のスライドカードを縦に並べる。デザイントークン・線・余白は pptxgenjs 版と一致させる。Google Fonts で Montserrat / Noto Sans JP を読み込む
- **No `#` prefix** on hex colors — pptxgenjs requirement（HTML 側は `#` 付き）
