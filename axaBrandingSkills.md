---
name: axa-pptx-branding
description: "Use this skill whenever creating a PowerPoint presentation for AXA or in the AXA brand style. This skill defines the AXA brand identity — colors, typography, layout patterns, logo placement, and slide structure — ensuring every deck looks consistent, professional, and on-brand. Trigger when the user mentions 'AXA', 'AXA Group', 'AXA Insurance', or asks to create a branded presentation matching AXA's corporate style. Also trigger for any insurance-related presentation that should follow the AXA look and feel. Always use this skill IN COMBINATION with the core pptx skill (read /mnt/skills/public/pptx/SKILL.md and /mnt/skills/public/pptx/pptxgenjs.md first for technical guidance)."
---

# AXA — PowerPoint Branding Skill

## Prerequisites

**Always read the core PPTX skill first:**
```
/mnt/skills/public/pptx/SKILL.md
/mnt/skills/public/pptx/pptxgenjs.md
```
This branding skill supplements the core skill with AXA-specific design rules.

---

## Brand Identity

### Company Info
- **Name**: AXA (stylized: **AXA** — all caps, always)
- **Industry**: Insurance, Financial Services, Asset Management
- **Headquarters**: Paris, France
- **Website**: www.axa.com
- **Tagline**: "Know You Can" (global) / "Réinventons notre métier" (France)

### Logo

The AXA logo is located at: **`/mnt/skills/user/axa-pptx-branding/assets/axa-logo.png`**

- Logo: White "AXA" wordmark on dark blue background with a red diagonal line (upper right)
- **Original image size**: 250 × 250 px — **aspect ratio = 1:1** (square)
- ⚠️ **CRITICAL**: Always maintain the 1:1 square aspect ratio. Never stretch or distort.
- The logo includes its own dark blue background — place it directly on slides without extra background shapes.
- **Content slides**: **0.55" × 0.55"** at position x: 0.3, y: 0.15
- **Title slides**: **1.2" × 1.2"** at position x: 0.4, y: 0.3
- Slide titles on content slides should start at **x: 1.0** to leave room for the logo

If the logo file is not found at the skill path, check `/mnt/user-data/uploads/` for any AXA logo file.

---

## Color Palette

This is the **definitive AXA color palette**. Do not deviate.

| Role | Color | Hex | Usage |
|------|-------|-----|-------|
| **AXA Blue (primary)** | Dark blue | `00008F` | Logo background, primary brand color, headers, key elements |
| **AXA Blue Dark** | Deep navy | `000078` | Darker variant, title slide backgrounds, premium sections |
| **AXA Red** | Vivid red | `FF1721` | Accent only — red diagonal line, CTAs, highlights, alerts |
| **White** | Pure white | `FFFFFF` | Primary text on dark backgrounds, slide backgrounds (light mode) |
| **Light Gray** | Soft gray | `F5F5F5` | Alternate light slide backgrounds, content cards |
| **Medium Gray** | Neutral gray | `999999` | Subtitles, captions, secondary text |
| **Dark Gray** | Charcoal | `333333` | Primary body text on light backgrounds |
| **Text Muted** | Light gray text | `767676` | Footnotes, less important info |
| **Ocean Blue** | Teal accent | `014750` | Secondary accent for variety, data viz |
| **Burnt Sienna** | Warm accent | `F07662` | Secondary accent for charts, warm highlights, buttons |
| **AXA Blue Light** | Pale blue tint | `E5E5F0` | Light blue backgrounds, subtle tinted sections |
| **Table Header** | AXA Blue | `00008F` | Table header backgrounds with white text |
| **Table Row Alt** | Very light blue | `F0F0F8` | Alternating table row background |
| **Border** | Light blue | `CCCCEE` | Subtle borders on light backgrounds |
| **Success** | Green | `1CC54E` | Positive indicators, checkmarks |
| **Warning** | Amber | `F5A623` | Caution, in-progress indicators |
| **Error** | Red | `D63B3B` | Errors, negative indicators (different from AXA Red) |

### Color Usage Rules

1. **White backgrounds are default** — AXA brand is professional and clean. Most content slides use white or `F5F5F5` backgrounds.
2. **AXA Blue for impact** — Use `00008F` for title slides, headers, key section backgrounds, and accents. It's the dominant brand color.
3. **AXA Red is ACCENT ONLY** — Use `FF1721` sparingly for: the red diagonal line decoration, call-to-action elements, and key highlights. Never as a background.
4. **Dark text on light backgrounds** — Body text is `333333` on white/light gray backgrounds.
5. **White text on blue backgrounds** — When using AXA Blue backgrounds, all text must be white.
6. **No other primary colors** — Stick to the blue/red/white/gray palette. Use Ocean Blue and Burnt Sienna only for charts and data visualization.
7. **The red diagonal line** — This is AXA's signature visual element. Use it as a decorative accent on title and section divider slides.

---

## Typography

| Element | Font | Size | Weight | Color |
|---------|------|------|--------|-------|
| **Slide title (dark bg)** | Arial Black | 36–44pt | Bold | `FFFFFF` (white) |
| **Slide title (light bg)** | Arial Black | 36–44pt | Bold | `00008F` (AXA Blue) |
| **Section header** | Arial | 24–28pt | Bold | `00008F` (AXA Blue) |
| **Card/box title** | Arial | 18–20pt | Bold | `00008F` or `FFFFFF` |
| **Body text (light bg)** | Arial | 13–15pt | Regular | `333333` |
| **Body text (dark bg)** | Arial | 13–15pt | Regular | `FFFFFF` |
| **Caption/footnote** | Arial | 10–11pt | Regular | `767676` |
| **Large stat number** | Arial Black | 60–72pt | Bold | `00008F` or `FF1721` |
| **Website footer** | Arial | 9pt | Regular | `999999` |

### Typography Rules

1. **Title slides**: Large, bold white text on AXA Blue background. Can highlight a keyword in AXA Red.
2. **Content slides**: AXA Blue titles on white background. Body in dark gray.
3. **Mixed-emphasis titles**: Highlight key terms in AXA Red within an otherwise blue or white title:
   ```javascript
   slide.addText([
     { text: "OUR ", options: { color: "00008F", bold: true } },
     { text: "COMMITMENT", options: { color: "FF1721", bold: true } },
     { text: " TO YOU", options: { color: "00008F", bold: true } }
   ], { fontFace: "Arial Black", fontSize: 40 });
   ```
4. **Left-align** all body text. Center only title slide titles.
5. **Don't mix more than 2 fonts** — Arial Black for headers, Arial for body.

---

## The AXA Red Diagonal Line

The signature AXA visual element is a **red diagonal line** that appears in the logo. Replicate this as a decorative element on key slides.

```javascript
// AXA signature red diagonal line (top-right corner)
// Use a thin red shape rotated diagonally
slide.addShape(pres.shapes.LINE, {
  x: 7.5, y: -0.5, w: 3.5, h: 3.5,
  line: { color: "FF1721", width: 3.5 },
  rotate: -45
});
```

**Alternative approach** — draw a red rectangle rotated as a diagonal stripe:
```javascript
// Red diagonal accent stripe (top-right area)
slide.addShape(pres.shapes.RECTANGLE, {
  x: 8.0, y: -1.5, w: 0.06, h: 4.5,
  fill: { color: "FF1721" },
  rotate: -50
});
```

Use the diagonal line on:
- Title slide (prominent)
- Section divider slides (subtle)
- Closing slide (prominent)

---

## Slide Layouts

### Layout 1: Title Slide (Dark)
```
┌──────────────────────────────────────────┐
│ ██████████████████████████████ AXA Blue   │
│                                    /     │
│  [AXA Logo]                       / red  │
│                                  / line  │
│  MAIN TITLE                     /        │
│  Keyword (red accent)                    │
│                                          │
│  Subtitle text in white                  │
│                                          │
│  www.axa.com              Date / Event   │
└──────────████████████████████████████████┘
Background: 00008F (AXA Blue)
```

**Implementation notes:**
- Full AXA Blue background (`00008F`)
- Logo at top-left, 1.2" × 1.2"
- Title in massive bold white text (44pt+), optional keyword in red
- Subtitle below in lighter/smaller white
- Red diagonal line accent in top-right area
- Footer with website URL bottom-left, date bottom-right
- Optional: client logo top-right (before the red line)

### Layout 2: Section Divider
```
┌──────────────────────────────────────────┐
│ ██████████████████████████████████████████│
│  [Logo]                            /     │
│                                   / red  │
│         SECTION TITLE            /       │
│         Section subtitle                 │
│                                          │
│                                          │
│  www.axa.com                   01 / 04   │
└──────────████████████████████████████████┘
Background: 000078 (AXA Blue Dark)
```

### Layout 3: Content — Two-Column Cards
```
┌──────────────────────────────────────────┐
│  [Logo]  SLIDE TITLE (blue)              │
│  Subtitle line (gray)                    │
│ ┌─────────────────┐ ┌─────────────────┐  │
│ │ Card Title      │ │ Card Title      │  │
│ │ (blue header)   │ │ (blue header)   │  │
│ │                 │ │                 │  │
│ │ • Item 1        │ │ • Item 1        │  │
│ │ • Item 2        │ │ • Item 2        │  │
│ └─────────────────┘ └─────────────────┘  │
│                              www.axa.com │
└──────────────────────────────────────────┘
Background: FFFFFF (white)
Cards: F5F5F5 with left blue border accent
```

**Implementation notes:**
- White background, AXA Blue title
- Two light gray cards with a left blue border (4px `00008F`)
- Card title in AXA Blue bold, body in dark gray
- Cards positioned at y: 1.8, each ~4.2" wide, ~3.2" tall

### Layout 4: Content with Table
```
┌──────────────────────────────────────────┐
│  [Logo]  SLIDE TITLE (blue)              │
│                                          │
│  ┌──────┬──────┬──────┬──────┐           │
│  │ Head │ Head │ Head │ Head │ (00008F)  │
│  ├──────┼──────┼──────┼──────┤           │
│  │      │      │      │      │ (FFFFFF)  │
│  │      │      │      │      │ (F0F0F8)  │
│  └──────┴──────┴──────┴──────┘           │
│                              www.axa.com │
└──────────────────────────────────────────┘
```

**Implementation notes:**
- Table header: AXA Blue (`00008F`), white bold text
- Alternating rows: white (`FFFFFF`) and pale blue (`F0F0F8`)
- Border: light blue (`CCCCEE`) thin lines
- Text: dark gray `333333`, 12–13pt

### Layout 5: Three-Column Info Cards
```
┌──────────────────────────────────────────┐
│  [Logo]  SLIDE TITLE (blue)              │
│ ┌────────────┐┌────────────┐┌────────────┐
│ │  [Icon]    ││  [Icon]    ││  [Icon]    │
│ │ Card Title ││ Card Title ││ Card Title │
│ │            ││            ││            │
│ │ Body text  ││ Body text  ││ Body text  │
│ │            ││            ││            │
│ └────────────┘└────────────┘└────────────┘
│                              www.axa.com │
└──────────────────────────────────────────┘
Cards: F5F5F5 with top blue border
```

### Layout 6: Key Stats / Big Numbers
```
┌──────────────────────────────────────────┐
│  [Logo]  SLIDE TITLE (blue)              │
│                                          │
│    72%          €4.2B          #1         │
│   label         label        label       │
│  (blue)      (red accent)   (blue)       │
│                                          │
│  Description text spanning the width     │
│                              www.axa.com │
└──────────────────────────────────────────┘
```

### Layout 7: Closing / Thank You
```
┌──────────────────────────────────────────┐
│ ██████████████████████████████████████████│
│  [Logo large]                      /     │
│                                   / red  │
│         MERCI / THANK YOU        /       │
│         tagline text                     │
│                                          │
│         🌐 www.axa.com                   │
│         ✉  contact@axa.com               │
│                                          │
└──────████████████████████████████████████┘
Background: 00008F
```

---

## Reusable Code Snippets

### Footer (every content slide)
```javascript
slide.addText("www.axa.com", {
  x: 7.5, y: 5.2, w: 2, h: 0.3,
  fontSize: 9, fontFace: "Arial", color: "999999", align: "right"
});
```

### Footer (every dark slide)
```javascript
slide.addText("www.axa.com", {
  x: 7.5, y: 5.2, w: 2, h: 0.3,
  fontSize: 9, fontFace: "Arial", color: "FFFFFF", align: "right",
  transparency: 50
});
```

### Logo placement (every slide)
```javascript
// Content slides (1:1 aspect ratio — always square)
slide.addImage({
  path: logoPath,  // path to axa-logo.png
  x: 0.3, y: 0.15, w: 0.55, h: 0.55
});

// Title slides (larger)
slide.addImage({
  path: logoPath,
  x: 0.4, y: 0.3, w: 1.2, h: 1.2
});
```

### Slide backgrounds
```javascript
// Light content slide (default)
slide.background = { color: "FFFFFF" };

// AXA Blue slide (title/section/closing)
slide.background = { color: "00008F" };

// AXA Blue Dark (alternate dark)
slide.background = { color: "000078" };

// Light gray alternate
slide.background = { color: "F5F5F5" };
```

### AXA Red diagonal accent line
```javascript
// Signature red diagonal line decoration (for title/section slides)
function addAxaDiagonalLine(slide, pres) {
  slide.addShape(pres.shapes.RECTANGLE, {
    x: 8.2, y: -1.8, w: 0.07, h: 5.0,
    fill: { color: "FF1721" },
    rotate: -50
  });
}
```

### Content card with left blue border
```javascript
function addAxaCard(slide, pres, { x, y, w, h, title, items }) {
  // Card background
  slide.addShape(pres.shapes.ROUNDED_RECTANGLE, {
    x, y, w, h,
    fill: { color: "F5F5F5" },
    rectRadius: 0.08
  });

  // Left blue accent border
  slide.addShape(pres.shapes.RECTANGLE, {
    x: x, y: y + 0.1, w: 0.05, h: h - 0.2,
    fill: { color: "00008F" }
  });

  // Card title (AXA Blue)
  slide.addText(title, {
    x: x + 0.25, y: y + 0.2, w: w - 0.5, h: 0.4,
    fontSize: 18, fontFace: "Arial", bold: true,
    color: "00008F", margin: 0
  });

  // Card items
  if (items && items.length > 0) {
    const textItems = items.map((item, i) => ({
      text: item.text || item,
      options: {
        bullet: true,
        breakLine: i < items.length - 1,
        fontSize: 13,
        color: "333333"
      }
    }));
    slide.addText(textItems, {
      x: x + 0.25, y: y + 0.7, w: w - 0.5, h: h - 0.9,
      fontFace: "Arial", valign: "top", margin: 0
    });
  }
}
```

### Blue header card (for key stats or highlights)
```javascript
function addAxaBlueCard(slide, pres, { x, y, w, h, stat, label }) {
  // Blue card background
  slide.addShape(pres.shapes.ROUNDED_RECTANGLE, {
    x, y, w, h,
    fill: { color: "00008F" },
    rectRadius: 0.1
  });

  // Big stat number
  slide.addText(stat, {
    x: x + 0.1, y: y + 0.3, w: w - 0.2, h: 0.8,
    fontSize: 48, fontFace: "Arial Black", bold: true,
    color: "FFFFFF", align: "center", margin: 0
  });

  // Label
  slide.addText(label, {
    x: x + 0.1, y: y + 1.2, w: w - 0.2, h: 0.5,
    fontSize: 13, fontFace: "Arial",
    color: "FFFFFF", align: "center", margin: 0,
    transparency: 30
  });
}
```

### Status indicators
```javascript
// ✓ Success (green)
{ text: "✓ ", options: { color: "1CC54E", bold: true } }
// ✗ Error (red)
{ text: "✗ ", options: { color: "D63B3B", bold: true } }
// ⚠ Warning (amber)
{ text: "⚠ ", options: { color: "F5A623", bold: true } }
```

---

## Slide Master Definition

```javascript
const logoPath = "/path/to/axa-logo.png"; // Adjust to actual path

// Light content master
pres.defineSlideMaster({
  title: "AXA_CONTENT",
  background: { color: "FFFFFF" },
  objects: [
    // Logo top-left (1:1 square ratio)
    { image: { path: logoPath, x: 0.3, y: 0.15, w: 0.55, h: 0.55 } },
    // Footer URL
    { text: {
      text: "www.axa.com",
      options: {
        x: 7.5, y: 5.2, w: 2, h: 0.3,
        fontSize: 9, fontFace: "Arial", color: "999999", align: "right"
      }
    }}
  ]
});

// Dark title/section master
pres.defineSlideMaster({
  title: "AXA_DARK",
  background: { color: "00008F" },
  objects: [
    { image: { path: logoPath, x: 0.4, y: 0.3, w: 1.2, h: 1.2 } },
    { text: {
      text: "www.axa.com",
      options: {
        x: 7.5, y: 5.2, w: 2, h: 0.3,
        fontSize: 9, fontFace: "Arial", color: "FFFFFF", align: "right",
        transparency: 50
      }
    }}
  ]
});
```

---

## Complete Example: Building an AXA Presentation

```javascript
const pptxgen = require("pptxgenjs");
const pres = new pptxgen();
pres.layout = "LAYOUT_16x9";
pres.author = "AXA";
pres.title = "Presentation Title";

const COLORS = {
  axaBlue: "00008F",
  axaBlueDark: "000078",
  axaRed: "FF1721",
  white: "FFFFFF",
  lightGray: "F5F5F5",
  medGray: "999999",
  darkGray: "333333",
  muted: "767676",
  blueLight: "E5E5F0",
  oceanBlue: "014750",
  sienna: "F07662",
  tableRowAlt: "F0F0F8",
  border: "CCCCEE",
  success: "1CC54E",
  warning: "F5A623",
  error: "D63B3B"
};

const logoPath = "./axa-logo.png";

// Helper: AXA red diagonal line
function addDiagonal(slide) {
  slide.addShape(pres.shapes.RECTANGLE, {
    x: 8.2, y: -1.8, w: 0.07, h: 5.0,
    fill: { color: COLORS.axaRed },
    rotate: -50
  });
}

// ── Slide 1: Title ──
let s1 = pres.addSlide();
s1.background = { color: COLORS.axaBlue };
s1.addImage({ path: logoPath, x: 0.4, y: 0.3, w: 1.2, h: 1.2 });
addDiagonal(s1);
s1.addText([
  { text: "PRESENTATION ", options: { color: COLORS.white, bold: true } },
  { text: "TITLE", options: { color: COLORS.axaRed, bold: true } }
], { x: 0.5, y: 2.0, w: 7.5, h: 1.2, fontSize: 44, fontFace: "Arial Black" });
s1.addText("Subtitle description goes here", {
  x: 0.5, y: 3.2, w: 7.5, h: 0.5, fontSize: 18, fontFace: "Arial", color: COLORS.white
});
s1.addText("www.axa.com", {
  x: 0.5, y: 5.1, w: 3, h: 0.3, fontSize: 9, fontFace: "Arial", color: COLORS.white,
  transparency: 50
});

// ── Slide 2: Content with Two Cards ──
let s2 = pres.addSlide();
s2.background = { color: COLORS.white };
s2.addImage({ path: logoPath, x: 0.3, y: 0.15, w: 0.55, h: 0.55 });
s2.addText("SLIDE TITLE", {
  x: 1.0, y: 0.15, w: 8.5, h: 0.55, fontSize: 32, fontFace: "Arial Black",
  color: COLORS.axaBlue, bold: true, margin: 0
});

// Left card
s2.addShape(pres.shapes.ROUNDED_RECTANGLE, {
  x: 0.4, y: 1.3, w: 4.3, h: 3.5, fill: { color: COLORS.lightGray }, rectRadius: 0.08
});
s2.addShape(pres.shapes.RECTANGLE, {
  x: 0.4, y: 1.4, w: 0.05, h: 3.3, fill: { color: COLORS.axaBlue }
});
s2.addText("Card Title", {
  x: 0.7, y: 1.5, w: 3.7, h: 0.4, fontSize: 18, fontFace: "Arial",
  bold: true, color: COLORS.axaBlue, margin: 0
});

// Right card
s2.addShape(pres.shapes.ROUNDED_RECTANGLE, {
  x: 5.3, y: 1.3, w: 4.3, h: 3.5, fill: { color: COLORS.lightGray }, rectRadius: 0.08
});
s2.addShape(pres.shapes.RECTANGLE, {
  x: 5.3, y: 1.4, w: 0.05, h: 3.3, fill: { color: COLORS.axaBlue }
});
s2.addText("Card Title", {
  x: 5.6, y: 1.5, w: 3.7, h: 0.4, fontSize: 18, fontFace: "Arial",
  bold: true, color: COLORS.axaBlue, margin: 0
});

// Footer
s2.addText("www.axa.com", {
  x: 7.5, y: 5.2, w: 2, h: 0.3, fontSize: 9, fontFace: "Arial",
  color: COLORS.medGray, align: "right"
});

// ── Slide 3: Key Stats ──
let s3 = pres.addSlide();
s3.background = { color: COLORS.white };
s3.addImage({ path: logoPath, x: 0.3, y: 0.15, w: 0.55, h: 0.55 });
s3.addText("KEY FIGURES", {
  x: 1.0, y: 0.15, w: 8.5, h: 0.55, fontSize: 32, fontFace: "Arial Black",
  color: COLORS.axaBlue, bold: true, margin: 0
});

// Stat cards
const stats = [
  { stat: "105M", label: "Clients worldwide", x: 0.5 },
  { stat: "€102B", label: "Revenue", x: 3.5 },
  { stat: "54", label: "Countries", x: 6.5 }
];
stats.forEach(s => {
  s3.addShape(pres.shapes.ROUNDED_RECTANGLE, {
    x: s.x, y: 1.5, w: 2.8, h: 2.5, fill: { color: COLORS.axaBlue }, rectRadius: 0.1
  });
  s3.addText(s.stat, {
    x: s.x, y: 1.8, w: 2.8, h: 1.0, fontSize: 48, fontFace: "Arial Black",
    bold: true, color: COLORS.white, align: "center", margin: 0
  });
  s3.addText(s.label, {
    x: s.x, y: 2.9, w: 2.8, h: 0.5, fontSize: 14, fontFace: "Arial",
    color: COLORS.white, align: "center", transparency: 25, margin: 0
  });
});
s3.addText("www.axa.com", {
  x: 7.5, y: 5.2, w: 2, h: 0.3, fontSize: 9, fontFace: "Arial",
  color: COLORS.medGray, align: "right"
});

// ── Slide 4: Closing ──
let s4 = pres.addSlide();
s4.background = { color: COLORS.axaBlue };
s4.addImage({ path: logoPath, x: 4.15, y: 0.5, w: 1.7, h: 1.7 });
addDiagonal(s4);
s4.addText("MERCI", {
  x: 0.5, y: 2.5, w: 9, h: 0.9, fontSize: 52, fontFace: "Arial Black",
  color: COLORS.white, bold: true, align: "center"
});
s4.addText("Know You Can", {
  x: 0.5, y: 3.4, w: 9, h: 0.5, fontSize: 20, fontFace: "Arial",
  color: COLORS.white, align: "center", italic: true, transparency: 30
});
s4.addText("🌐 www.axa.com", {
  x: 3.0, y: 4.3, w: 4, h: 0.3, fontSize: 13, fontFace: "Arial",
  color: COLORS.white, align: "center"
});

pres.writeFile({ fileName: "output.pptx" });
```

---

## Decorative Elements (Optional)

1. **Red diagonal line**: The #1 brand element. Use on dark slides. See code snippet above.
2. **Blue gradient overlays**: When using background images, overlay with AXA Blue at 60–70% opacity.
3. **Thin blue top/bottom bars**: A 0.04" high blue rectangle spanning the full width at the very top or bottom of content slides adds subtle branding.
4. **Left blue accent borders**: On cards and content boxes, a thin blue left border echoes the AXA brand without being heavy.

```javascript
// Blue gradient overlay on background image
slide.addShape(pres.shapes.RECTANGLE, {
  x: 0, y: 0, w: 10, h: 5.625,
  fill: { color: "00008F", transparency: 35 }
});

// Thin blue bar at top of content slides
slide.addShape(pres.shapes.RECTANGLE, {
  x: 0, y: 0, w: 10, h: 0.04,
  fill: { color: "00008F" }
});
```

---

## Checklist Before Delivery

Before finalizing any AXA presentation:

- [ ] **White or AXA Blue backgrounds only** — no random colors
- [ ] **Logo present** on every slide (top-left, **1:1 square aspect ratio**)
- [ ] **Footer URL** (`www.axa.com`) on every slide
- [ ] **AXA Blue** (`00008F`) used for titles and headers
- [ ] **AXA Red** (`FF1721`) used sparingly as accent only
- [ ] **Red diagonal line** on title and closing slides
- [ ] **No other primary colors** — only the AXA palette
- [ ] **Font consistency**: Arial Black for titles, Arial for body
- [ ] **Dark text on light bg** / **White text on dark bg** — proper contrast
- [ ] **Title slide** has AXA Blue background with white text
- [ ] **Closing slide** has AXA Blue background with "MERCI" or "THANK YOU"
- [ ] **Cards use light gray** (`F5F5F5`) with blue left border accent
- [ ] Run QA as per the core PPTX skill (thumbnails, visual inspection)
