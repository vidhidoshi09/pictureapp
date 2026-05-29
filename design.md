# collectobjects — Design System
**Version:** 4.0 | Last updated: May 2026 | Owner: Vidhi Doshi

Single source of truth. Any agent or developer implementing UI must follow this exactly.

---

## 1. Design Principles

- **Objects are the hero.** The UI exists to frame them, not compete with them.
- **One accent. One grid. Consistent type.** No decoration for its own sake.
- **Nunito is reserved.** It only appears on object names — nowhere else.
- **Every screen has one job.** Camera captures. Review confirms. Grid displays. Detail views and edits.

---

## 2. Color System

### 2.1 Neutral Scale

The foundation of the entire UI. Use these tokens — do not hardcode hex values directly.

| Token | Hex | Common Use |
|-------|-----|------------|
| `--neutral-0` | `#FFFFFF` | White — surfaces, close buttons |
| `--neutral-50` | `#F6F6F6` | App background |
| `--neutral-100` | `#E2E2E2` | Dot texture, card surfaces, input bg |
| `--neutral-200` | `#D4D4D4` | Dividers, borders |
| `--neutral-300` | `#C0C0C0` | Disabled borders, secondary button border |
| `--neutral-400` | `#B4B4B4` | Placeholder text |
| `--neutral-500` | `#A1A1A1` | Tertiary text, dimmed labels |
| `--neutral-600` | `#939393` | Secondary text (dates, counts) |
| `--neutral-700` | `#727272` | Body text, supporting labels |
| `--neutral-800` | `#595959` | Strong body text |
| `--neutral-900` | `#444444` | Near-black text |
| `--neutral-1000` | `#141414` | Primary text, near-black |

### 2.2 Accent — Orange

Single primary action color. Used only on FAB, confirm button, active states, and input focus.

| Token | Hex | Use |
|-------|-----|-----|
| `--orange-accent` | `#f5a742` | FAB, confirm button, focus ring |
| `--orange-accent-dark` | `#e8962e` | Pressed / active state |
| `--orange-accent-glow` | `rgba(245,167,66,0.30)` | FAB shadow |
| `--orange-subtle` | `#FFF7F0` | Light orange tint — future use |

### 2.3 Semantic Tokens

Map all component styles to semantic tokens, not raw hex values.

```css
/* Backgrounds */
--color-bg:             var(--neutral-50);      /* #F6F6F6 */
--color-dot:            var(--neutral-100);     /* #E2E2E2 */
--color-surface:        var(--neutral-100);     /* #E2E2E2 */
--color-white:          var(--neutral-0);       /* #FFFFFF */

/* Text */
--color-text-primary:   var(--neutral-1000);   /* #141414 */
--color-text-secondary: var(--neutral-600);    /* #939393 */
--color-text-tertiary:  var(--neutral-400);    /* #B4B4B4 */
--color-text-disabled:  var(--neutral-300);    /* #C0C0C0 */

/* Actions */
--color-accent:         #f5a742;
--color-accent-dark:    #e8962e;
--color-accent-glow:    rgba(245,167,66,0.30);

/* Utility */
--color-camera-bg:      var(--neutral-1000);   /* #141414 */
--color-border:         var(--neutral-200);    /* #D4D4D4 */
--color-border-subtle:  var(--neutral-100);    /* #E2E2E2 */
```

### 2.4 Dot Texture

```css
background-image: radial-gradient(circle, var(--color-dot) 1px, transparent 1px);
background-size: 28px 28px;
```

Applied to the **scrollable container** (`#home`) — dots scroll with content, they are not a fixed layer.

---

## 3. Typography

### 3.1 Fonts

**Two fonts. Strictly separated.**

| Font | Where Used |
|------|-----------|
| Inter / SF Pro | **Everything** — headings, body, buttons, labels, inputs, all UI |
| Nunito | **Only** object names on cards and in the detail view — nowhere else |

**UI Font:** Inter is the web equivalent of SF Pro. On Apple devices, `-apple-system` resolves to SF Pro natively. On all other devices, Inter is loaded from Google Fonts. The result is SF Pro on iPhone (where this app lives) and Inter everywhere else — both clean, geometric, and designed for screens.

```css
--font-ui:      -apple-system, BlinkMacSystemFont, 'Inter', sans-serif;
--font-object:  'Nunito', -apple-system, BlinkMacSystemFont, sans-serif;
```

Both fonts loaded from Google Fonts (Inter as explicit fallback, Nunito for cards):
```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Nunito:wght@700;800&display=swap" rel="stylesheet" />
```

Nunito weights 700 and 800 only — it is exclusively for object names on cards and the detail/review view.

---

### 3.2 Heading Scale

Used for titles, section headers, screen names.

| Style | Size | Weight | Line Height | Letter Spacing | Usage |
|-------|------|--------|-------------|----------------|-------|
| `heading-xl` | `28px` | `800` | `1.2` | `-0.5px` | App title ("collectobjects") |
| `heading-lg` | `22px` | `700` | `1.3` | `-0.3px` | Detail view object name, section title |
| `heading-md` | `18px` | `700` | `1.3` | `-0.2px` | Modal headings |
| `heading-sm` | `15px` | `600` | `1.4` | `0` | Card name (system font version if needed) |
| `heading-xs` | `13px` | `600` | `1.4` | `0` | Sub-section labels |

---

### 3.3 Body Scale

Used for descriptions, hints, secondary content.

| Style | Size | Weight | Line Height | Letter Spacing | Usage |
|-------|------|--------|-------------|----------------|-------|
| `body-lg` | `16px` | `400` | `1.6` | `0` | Primary readable content |
| `body-md` | `14px` | `400` | `1.6` | `0` | Standard body, input text |
| `body-sm` | `13px` | `400` | `1.5` | `0` | Hints, sub-labels, counts |
| `body-xs` | `11px` | `400` | `1.5` | `0` | Object dates in grid, fine print |

---

### 3.4 Label Scale

Used for button text, tags, metadata.

| Style | Size | Weight | Line Height | Letter Spacing | Usage |
|-------|------|--------|-------------|----------------|-------|
| `label-lg` | `14px` | `500` | `1` | `0.1px` | Button text M/L |
| `label-md` | `12px` | `500` | `1` | `0.1px` | Button text S, tags |
| `label-sm` | `11px` | `500` | `1` | `0.2px` | Button text XS, tiny labels |

---

### 3.5 Nunito — Object Names Only

| Style | Font | Size | Weight | Letter Spacing | Where |
|-------|------|------|--------|----------------|-------|
| `object-name-grid` | Nunito | `15px` | `700` | `-0.2px` | Card name in grid |
| `object-name-detail` | Nunito | `22px` | `700` | `-0.3px` | Name in detail / review view |

**Nunito must not be used anywhere else.** Not in buttons, not in headers, not in inputs.

---

## 4. Spacing

4px base unit.

| Token | Value | Usage |
|-------|-------|-------|
| `--sp-xs` | `4px` | Micro gaps |
| `--sp-sm` | `8px` | Tight pairs (name → date) |
| `--sp-md` | `12px` | Component internals |
| `--sp-lg` | `16px` | Page margins, grid column gap |
| `--sp-xl` | `20px` | Section gaps |
| `--sp-2xl` | `24px` | Major spacing, grid row gap |
| `--sp-3xl` | `32px` | Header bottom margin |
| `--sp-4xl` | `48px` | Large whitespace |

---

## 5. Buttons

### 5.1 Variants

Three variants. Applied as CSS classes: `.btn-primary`, `.btn-secondary`, `.btn-tertiary`.

| Variant | Background | Border | Text Color | Use |
|---------|-----------|--------|------------|-----|
| **Primary** | `--color-accent` (#f5a742) | none | `#FFFFFF` | Main CTA — save, confirm |
| **Secondary** | `transparent` | `1.5px solid var(--neutral-300)` | `var(--neutral-900)` | Secondary action — retake, cancel |
| **Tertiary** | `transparent` | none | `var(--neutral-700)` | Ghost — delete, dismiss |

All buttons:
- `font-family: var(--font-ui)`
- `border-radius: 100px` (pill)
- `cursor: pointer`
- `transition: transform 0.15s ease, opacity 0.15s ease`
- Active state: `transform: scale(0.95)`, `opacity: 0.9`

---

### 5.2 Sizes

| Size | Height | Padding | Font Style | Icon Size |
|------|--------|---------|------------|-----------|
| `btn-xs` | `28px` | `0 10px` | `label-sm` (11px/500) | 14px |
| `btn-s` | `32px` | `0 14px` | `label-md` (12px/500) | 16px |
| `btn-m` | `40px` | `0 18px` | `label-lg` (14px/500) | 18px |
| `btn-l` | `48px` | `0 24px` | `15px / 500` | 20px |
| `btn-xl` | `56px` | `0 32px` | `16px / 600` | 22px |

Default size is **M** unless specified.

---

### 5.3 Circle Buttons (Review Screen Only)

The review screen uses circle buttons, not standard pills. These are a special case, not part of the button library.

| Button | Size | Background | Icon | Font |
|--------|------|-----------|------|------|
| Retake (↺) | `56px` circle | `var(--neutral-100)` | ↺, 22px, `--neutral-800` | — |
| Confirm (✓) | `64px` circle | `--color-accent` | ✓, 26px, white | — |
| Discard (✕) | `56px` circle | `var(--neutral-100)` | ✕, 22px, `--neutral-800` | — |

Row: `display: flex; gap: 24px; align-items: center; justify-content: center`

---

## 6. Components

### 6.1 Object Card (Grid)

```
  [  object image  ]   ← no container, just image + shadow
   Object Name          ← Nunito, 15px, 700 (object-name-grid)
   May 19, 2026         ← body-xs, --color-text-tertiary
```

**Image treatment:**
- Container: `width: 100%; aspect-ratio: 1`
- Image: `width: 90%; height: 90%; object-fit: contain; mix-blend-mode: multiply`
- White outline (isolation effect via stacked drop-shadows):
  ```css
  filter:
    drop-shadow( 2px  0   0 #fff)
    drop-shadow(-2px  0   0 #fff)
    drop-shadow( 0    2px 0 #fff)
    drop-shadow( 0   -2px 0 #fff)
    drop-shadow( 1.5px  1.5px 0 #fff)
    drop-shadow(-1.5px  1.5px 0 #fff)
    drop-shadow( 1.5px -1.5px 0 #fff)
    drop-shadow(-1.5px -1.5px 0 #fff)
    drop-shadow(0 6px 18px rgba(0,0,0,0.12));
  ```

**Object scaling:** Objects must visually fill the card. `object-fit: contain` achieves this once bg removal returns a tight-cropped image with no surrounding whitespace.

**Tap state:** `transform: scale(0.97)`, `0.2s ease`

---

### 6.2 FAB

| Property | Value |
|----------|-------|
| Size | `58px` circle |
| Background | `--color-accent` |
| Shadow | `var(--sh-fab)` |
| Icon | Camera SVG (Material Icons), white, 24px |
| Position | Fixed, bottom 24px + safe-area, right 20px |
| Tap state | `scale(0.95)`, `0.15s ease` |

Icon is a camera. Not `+`.

---

### 6.3 Close Button

Consistent across all overlays.

| Property | Value |
|----------|-------|
| Size | `44px` circle |
| Background | `rgba(255,255,255,0.92)` |
| Shadow | `0 1px 6px rgba(0,0,0,0.12)` |
| Icon | `✕`, 18px, `--neutral-800` |
| Position | `top: 16px + safe-area-inset-top`, `left: 16px` |

---

### 6.4 Name Input

```css
font-family: var(--font-ui);
font-size: 22px;
font-weight: 600;
text-align: center;
color: var(--color-text-primary);
background: transparent;
border: none;
border-bottom: 2px solid var(--color-border-subtle);
padding: 8px 4px 10px;
outline: none;
```

- Placeholder: `--color-text-tertiary`, text "Name this object…"
- Focus: `border-bottom-color: var(--color-accent)`
- **Do not auto-focus on screen load.** User should see the object first.

---

### 6.5 Detail View

Full-screen overlay. Opened by tapping any grid card.

```
┌─────────────────────────────────┐
│  [✕]                            │
│                                 │
│       [   object image   ]      │  ← 80% width, centered
│                                 │
│          Object Name            │  ← Nunito, object-name-detail, tappable
│          May 19, 2026           │  ← body-sm, --color-text-secondary
│                                 │
│          [ Delete ]             │  ← btn-tertiary, btn-s
└─────────────────────────────────┘
```

**Rename:** Tapping the name replaces it with an input field. Enter or blur confirms. Escape cancels.

**Delete:**
- Default: tertiary ghost button, grey
- First tap → background `#e53e3e`, text "Sure? Tap to delete" (red state)
- Auto-resets after 3 seconds
- Second tap → deletes, closes overlay, re-renders grid

---

### 6.6 Processing Overlay

```
┌─────────────────────────────────┐
│                                 │
│       ┌─────────────┐           │
│       │ ✂ - - - - - │           │
│       │   [photo]   │           │
│       └─────────────┘           │
│                                 │
│       Cutting background…       │  ← heading-sm, --color-text-primary
│         Just a moment           │  ← body-sm, --color-text-secondary
│                                 │
└─────────────────────────────────┘
```

Animation: TBD (three options proposed — scan / spotlight / dots+reveal).

---

### 6.7 Camera Overlay

- Background: `var(--color-camera-bg)` (#141414)
- Full-screen video, `transform: scaleX(-1)` (mirror front/rear)
- Shutter: 72px white circle, centered, `box-shadow: 0 0 0 4px rgba(255,255,255,0.25), 0 0 0 7px rgba(255,255,255,0.1)`
- Close button: top-left, white (see 6.3)

---

## 7. Screen Layouts

### 7.1 Home / Grid

```
┌─────────────────────────────────┐
│                                 │
│  collectobjects                 │  ← heading-xl
│  4 objects                      │  ← body-sm, --color-text-secondary
│                                 │
│  [duck]         [croissant]     │
│  Rubber Duck    Croissant       │  ← Nunito
│  May 13         May 16          │  ← body-xs
│                                 │
│  [teapot]       [key]           │
│  Blue Teapot    Vintage Key     │
│  May 19         May 21          │
│                                 │
│                          [cam]  │
└─────────────────────────────────┘
```

- No date above the title
- Grid: `1fr 1fr`, `column-gap: 16px`, `row-gap: 24px`
- Bottom padding: `90px` (FAB clearance)
- Dots scroll with page

### 7.2 Review

```
┌─────────────────────────────────┐
│  [✕]                            │
│                                 │
│       [  object image  ]        │  ← 72% width
│                                 │
│       Name this object…         │  ← 22px input
│                                 │
│      [↺]     [✓]     [✕]       │
│                                 │
└─────────────────────────────────┘
```

---

## 8. Shadows & Depth

| Token | Value | Usage |
|-------|-------|-------|
| `--sh-object` | `drop-shadow(0 6px 18px rgba(0,0,0,0.14))` | Grid images |
| `--sh-object-lg` | `drop-shadow(0 8px 22px rgba(0,0,0,0.16))` | Detail / review |
| `--sh-fab` | `0 6px 20px rgba(245,167,66,0.35)` | FAB |
| `--sh-close` | `0 1px 6px rgba(0,0,0,0.12)` | Close button |

---

## 9. Interactions

| Element | Transform | Duration |
|---------|-----------|----------|
| Grid card | `scale(0.97)` | `0.2s ease` |
| FAB | `scale(0.95)` | `0.15s ease` |
| Confirm ✓ | `scale(0.93)` | `0.15s ease` |
| Retake / Discard | `scale(0.95)` | `0.15s ease` |
| Primary button | `scale(0.96)` | `0.15s ease` |
| Secondary / Tertiary | `scale(0.97)` | `0.15s ease` |

---

## 10. Accessibility

### Touch Targets (minimum 44px)

| Element | Size |
|---------|------|
| FAB | 58px ✓ |
| Close button | 44px ✓ |
| Confirm ✓ | 64px ✓ |
| Retake / Discard | 56px ✓ |
| btn-xs | 28px ⚠️ — use only for non-critical actions |
| Grid card | ~160px+ ✓ |

### Contrast

| Pair | WCAG |
|------|------|
| `#141414` on `#F6F6F6` | AAA |
| `#939393` on `#F6F6F6` | AA |
| `#FFFFFF` on `#f5a742` | AA (bold) |

---

## 11. Full CSS Token Reference

```css
:root {
  /* ── Neutral Scale ─────────────────────────────── */
  --neutral-0:    #FFFFFF;
  --neutral-50:   #F6F6F6;
  --neutral-100:  #E2E2E2;
  --neutral-200:  #D4D4D4;
  --neutral-300:  #C0C0C0;
  --neutral-400:  #B4B4B4;
  --neutral-500:  #A1A1A1;
  --neutral-600:  #939393;
  --neutral-700:  #727272;
  --neutral-800:  #595959;
  --neutral-900:  #444444;
  --neutral-1000: #141414;

  /* ── Orange Accent ─────────────────────────────── */
  --orange-accent:      #f5a742;
  --orange-accent-dark: #e8962e;
  --orange-accent-glow: rgba(245,167,66,0.30);
  --orange-subtle:      #FFF7F0;

  /* ── Semantic Colors ───────────────────────────── */
  --color-bg:             var(--neutral-50);
  --color-dot:            var(--neutral-100);
  --color-surface:        var(--neutral-100);
  --color-white:          var(--neutral-0);
  --color-text-primary:   var(--neutral-1000);
  --color-text-secondary: var(--neutral-600);
  --color-text-tertiary:  var(--neutral-400);
  --color-text-disabled:  var(--neutral-300);
  --color-accent:         var(--orange-accent);
  --color-accent-dark:    var(--orange-accent-dark);
  --color-accent-glow:    var(--orange-accent-glow);
  --color-camera-bg:      var(--neutral-1000);
  --color-border:         var(--neutral-200);
  --color-border-subtle:  var(--neutral-100);

  /* ── Fonts ─────────────────────────────────────── */
  --font-ui:     -apple-system, BlinkMacSystemFont, 'Inter', sans-serif;
  --font-object: 'Nunito', -apple-system, BlinkMacSystemFont, sans-serif;

  /* ── Font Sizes ────────────────────────────────── */
  --fs-xs:   11px;
  --fs-sm:   13px;
  --fs-base: 14px;
  --fs-md:   15px;
  --fs-lg:   18px;
  --fs-xl:   22px;
  --fs-2xl:  28px;

  /* ── Font Weights ──────────────────────────────── */
  --fw-reg:   400;
  --fw-med:   500;
  --fw-semi:  600;
  --fw-bold:  700;
  --fw-black: 800;

  /* ── Spacing ───────────────────────────────────── */
  --sp-xs:  4px;
  --sp-sm:  8px;
  --sp-md:  12px;
  --sp-lg:  16px;
  --sp-xl:  20px;
  --sp-2xl: 24px;
  --sp-3xl: 32px;
  --sp-4xl: 48px;

  /* ── Radii ─────────────────────────────────────── */
  --r-sm:   12px;
  --r-md:   20px;
  --r-pill: 100px;
  --r-full: 50%;

  /* ── Shadows ───────────────────────────────────── */
  --sh-object:    drop-shadow(0 6px 18px rgba(0,0,0,0.14));
  --sh-object-lg: drop-shadow(0 8px 22px rgba(0,0,0,0.16));
  --sh-fab:       0 6px 20px rgba(245,167,66,0.35);
  --sh-close:     0 1px 6px rgba(0,0,0,0.12);

  /* ── Transitions ───────────────────────────────── */
  --tx-fast: 0.15s ease;
  --tx-base: 0.2s ease;
  --tx-slow: 0.3s ease;
}
```

---

## 12. Out of Scope (Future Versions)

Not to be implemented until explicitly planned:

- Tab bar navigation
- Circular progress ring
- Category tiles
- Dark mode (dark hex values in the neutral scale exist but are unused)
- Cloud sync or accounts
- Social sharing / export
