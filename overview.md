# Spaced — Overview

**"Can you remember space?"**
An interactive browser prototype that tests a user's ability to recall and reproduce typographic spacing values.

---

## Concept

Players observe a spacing gap between two typographic elements, memorize it, and then reconstruct it from memory. The game measures how accurately a designer can internalize and reproduce spacing — a core skill in layout and UI design.

---

## Game Flow

1. **Start Screen** — Intro with a visual demo showing what a "gap" looks like, styled as a design spec annotation.
2. **Observation Phase** — The specimen (two text elements with a measured gap) is shown for **3.5 seconds**. A progress bar counts down.
3. **Input Phase** — The gap is hidden. The player uses a slider (4–80px range) or types a value directly to reconstruct the spacing.
4. **Result Phase** — Scored immediately. A comparison bar shows "Design Spec" vs. "Implementation" values. Scoring:
   - ≥ 8.0 → Good (green)
   - ≥ 5.0 → OK (blue)
   - < 5.0 → Off (red)
5. **Final Screen** — Total score out of 50, per-round breakdown, and a verdict message.

---

## Rounds

5 rounds total, each pairing a typographic label with a spacing value. Gap values are drawn from a fixed set — `[8, 16, 24, 32, 48]px` — shuffled randomly each game. Round pairs:

| Round | Top Text   | Bottom Text    | Gap Label  |
|-------|-----------|----------------|------------|
| 1     | Headline  | Body text      | tight      |
| 2     | Chapter I | Introduction   | generous   |
| 3     | Title     | Subheading     | standard   |
| 4     | Heading   | Caption text   | open       |
| 5     | Display   | Label          | medium     |

---

## Scoring

```
diff = |guess − target|
score = max(0, 10 − (diff / 76) × 10)   → rounded to 1 decimal
```

Max score per round: **10.0**
Max total score: **50.0**

Verdicts:
- 45+ → "Pixel Perfect Alignment."
- 35+ → "Clean spacing. Minor deviations."
- 25+ → "Draft quality. Review constraints."
- 15+ → "Broken layout."
- 0+  → "CSS has crashed."

---

## Visual Design

The UI is styled as a Figma-like design environment:

- **Canvas** — light grey (`#F5F5F5`) with a dot-grid background
- **Artboards** — white cards with subtle border/shadow, labeled `# Frame 1`
- **Typography** — DM Mono (UI/labels) + Playfair Display (specimen text)
- **Accent** — `#0D99FF` blue for active states, selection highlights, and gap visualization
- **Controls panel** — styled as a Figma "Properties" inspector
- **Result panel** — styled as a "Inspection" panel with horizontal comparison bars

---

## Tech

- Single HTML file, no dependencies
- Pure vanilla JS + CSS
- Fonts loaded from Google Fonts (DM Mono, Playfair Display)
- No build step, runs directly in any browser
