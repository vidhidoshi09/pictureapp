# Memory App — Design System
**Source of truth. Based on CapWords visual reference (May 2026).**

---

## Design Philosophy

**Core Principle:** Interface disappears. Objects shine.

Directly inspired by CapWords. The background is pure white — nothing competes with the object. Cards have no visible container in the grid; images simply float with a soft drop shadow. Color lives in categories and accents, not the background. Typography is confident (heavy names, quiet metadata).

---

## 1. Visual Language

### 1.1 Aesthetic Direction

- **Background:** Pure white. Not cream, not grey — `#ffffff`.
- **Objects:** Float directly on white. No card border, no glassmorphism in the grid.
- **Typography:** Bold object names (weight 700). Quiet metadata. Clear hierarchy.
- **Accent:** Warm orange (matches CapWords Capture tab + confirm button).
- **Category tiles:** Muted pastel blocks — each category has its own identity color.
- **Glow:** Object images get a warm radial glow on the review/detail screen.

**What was removed from the old spec:**
- ❌ Cream/linen background gradient
- ❌ Dotted background texture
- ❌ Glassmorphism card containers in the grid
- ❌ Peachy button gradient (#e8b4a8 → #d9a896)

**What was added from CapWords reference:**
- ✅ White background
- ✅ Warm orange accent
- ✅ Bold object names
- ✅ Object glow on detail/review screens
- ✅ Three-button review row (↺ / ✓ / ✕)
- ✅ Tab bar navigation
- ✅ Circular progress ring
- ✅ Category tile cards

---

## 2. Color Palette

### 2.1 Base Colors

| Token | Hex | RGB | Usage |
|-------|-----|-----|-------|
| White | `#ffffff` | 255, 255, 255 | **Primary background (all screens)** |
| Off-white | `#f7f7f7` | 247, 247, 247 | Secondary surfaces, tab bar bg |
| Text primary | `#1a1a1a` | 26, 26, 26 | Object names, headings |
| Text secondary | `#999999` | 153, 153, 153 | Dates, subtitles, hints |
| Text tertiary | `#bbbbbb` | 187, 187, 187 | Placeholder, dimmed labels |
| Divider | `#eeeeee` | 238, 238, 238 | Hairline separators |

### 2.2 Accent — Warm Orange

The single primary action color. Used for: active tab, confirm button, FAB.

| Token | Hex | Usage |
|-------|-----|-------|
| Orange | `#f5a742` | Active tab icon, confirm (✓) button fill |
| Orange dark | `#e8962e` | Button pressed state |
| Orange glow | `rgba(245,167,66,0.15)` | FAB shadow |

### 2.3 Category Tile Colors

Each category has a fixed muted pastel. Used as solid tile backgrounds with white text.

| Category | Hex | RGB | Appearance |
|----------|-----|-----|------------|
| Food & Drinks | `#9585bf` | 149, 133, 191 | Dusty purple |
| People & Family | `#7fa0c0` | 127, 160, 192 | Muted blue |
| Body & Health | `#9a7aaa` | 154, 122, 170 | Soft plum |
| Animals & Nature | `#8a9a64` | 138, 154, 100 | Olive green |
| Home & Furniture | `#b07882` | 176, 120, 130 | Dusty rose |
| School & Study | `#a89060` | 168, 144, 96 | Warm tan |

### 2.4 Functional Colors

| Element | Color | Notes |
|---------|-------|-------|
| Camera background | `#1a1a1a` | Video preview bg |
| Review glow | `rgba(255, 220, 100, 0.35)` | Warm yellow radial glow behind object |
| Replay button | `#efefef` | Light grey circle |
| Reject button (✕) | `#efefef` | Light grey circle |
| Confirm button (✓) | `#f5a742` | Orange fill, white icon |
| Tab bar background | `#ffffff` | + top border `#eeeeee` |

---

## 3. Typography

### 3.1 Font Family

System fonts only — loads instantly, feels native.

```css
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

### 3.2 Type Scale

| Role | Size | Weight | Letter-spacing | Color | Notes |
|------|------|--------|----------------|-------|-------|
| Page greeting | 28px | 400 | -0.3px | `#1a1a1a` | "Good Morning" / "Memories" |
| Date label | 13px | 400 | 0 | `#999` | "May 19" above greeting |
| Greeting sub | 15px | 400 | 0 | `#999` | "Awesome! You've snapped 2 words!" |
| **Grid object name** | **15px** | **700** | **-0.2px** | **`#1a1a1a`** | **Bold — most visible text in grid** |
| Grid date | 11px | 400 | 0 | `#bbb` | Below object name |
| Review name | 22px | 700 | -0.3px | `#1a1a1a` | Object name on review screen |
| Review subtitle | 14px | 400 | 0 | `#999` | Date or secondary label |
| Category tile name | 17px | 600 | 0 | `#ffffff` | Inside colored tile |
| Category word count | 12px | 400 | 0 | `rgba(255,255,255,0.8)` | "3 Words" |
| Tab label | 11px | 400 | 0 | `#999` (inactive) / `#f5a742` (active) | |
| Input text | 14px | 400 | 0 | `#1a1a1a` | Name input field |
| Hint text | 13px | 400 | 0 | `#999` | "Not what you expected?" |

### 3.3 Key Typography Rule

> Object names are **bold (700)** — this is the single biggest change from the original spec.
> The name must be immediately readable at a glance. No medium/500 for primary labels.

---

## 4. Layout & Spacing

### 4.1 Spacing Scale (4px base)

| Token | Value | Usage |
|-------|-------|-------|
| `--sp-xs` | 4px | Micro gaps |
| `--sp-sm` | 8px | Tight pairs |
| `--sp-md` | 12px | Component internals |
| `--sp-lg` | 16px | Page margins |
| `--sp-xl` | 20px | Grid gaps, section gaps |
| `--sp-2xl` | 24px | Major section spacing |
| `--sp-3xl` | 32px | Header bottom margin |
| `--sp-4xl` | 48px | Large whitespace |

### 4.2 Page Padding

| Screen | Padding | Notes |
|--------|---------|-------|
| Grid view | 16px h, 20px top, 80px bottom | 80px bottom = tab bar height |
| Capture view | 16px all | Camera-focused layout |
| Review screen | 16px h, 24px top | Centered object + buttons |
| Detail view | 16px all | Centered object |

### 4.3 Component Spacing

| Component | Spacing | Notes |
|-----------|---------|-------|
| Header to grid | 24px | After greeting block |
| Grid gap | 16px h × 24px v | Slightly tighter horizontal |
| Object image to name | 10px | Tight grouping |
| Name to date | 4px | Very tight, secondary info |
| Camera to input | 20px | |
| Input to review buttons | 24px | |
| Tab bar height | 56px + safe area | Fixed at bottom |

---

## 5. Components

### 5.1 Memory Card (Grid)

Objects float **directly on the white page** — no container box, no border, no glass.

```
  [  object image  ]   ← no container, just image + shadow
    Object Name         ← 15px bold, centered
    May 19, 2026        ← 11px, #bbb, centered
```

**Image:**
- Width/height: fills ~85% of grid column width
- Object-fit: contain
- Filter: `drop-shadow(0 6px 16px rgba(0,0,0,0.12))`
- No background box behind image

**Name:**
- 15px, weight **700**, `#1a1a1a`, centered
- Margin-top: 10px

**Date:**
- 11px, weight 400, `#bbb`, centered
- Margin-top: 4px

**Tap state:**
- `transform: scale(0.97)`
- `transition: transform 0.2s ease`

> **Critical difference from old spec:** No glass/frosted container in the grid.
> Cards are card-less — it's just an image floating on white.

### 5.2 Object Glow (Detail / Review Screen)

Used when an object is displayed full-size (detail view, capture review).

```css
/* Behind the object image */
background: radial-gradient(
  ellipse 70% 60% at 50% 55%,
  rgba(255, 220, 100, 0.35) 0%,
  transparent 70%
);
```

- Warm yellow radial glow, centered below the object
- Gives objects a "spotlit" feel on white
- Does NOT appear in the grid (grid = no bg effect)
- Contained in the image wrapper div

### 5.3 Three-Button Review Row

Appears on the capture review screen after a photo is taken.

```
  [↺]   [✓]   [✕]
```

| Button | Size | Background | Icon | Color |
|--------|------|-----------|------|-------|
| Replay (↺) | 52px circle | `#efefef` | ↺ | `#666` |
| Confirm (✓) | 60px circle | `#f5a742` | ✓ | `#ffffff` |
| Reject (✕) | 52px circle | `#efefef` | ✕ | `#666` |

- Confirm button is visually dominant (larger, orange)
- All three are circles (`border-radius: 50%`)
- Arranged in a row with `gap: 20px`, centered
- Confirm tap: `scale(0.95)`, `transition: 0.15s ease`
- Hint text below: `"Not what you expected? Tap to adjust"` — 13px, `#999`

### 5.4 FAB (Floating Action Button)

Now uses warm orange to match the accent system.

**Container:**
- Size: 58px circle
- Background: `#f5a742`
- Box shadow: `0 6px 20px rgba(245,167,66,0.35)`
- Position: fixed, bottom 24px + safe area, right 20px
- Z-index: 50

**Icon:** `+`, 26px, white, weight 600

**Tap state:** `scale(0.95)`, `transition: 0.2s ease`

### 5.5 Tab Bar

Bottom navigation — always visible on home/grid screen.

```
┌─────────────────────────────────┐
│  [📷]      [🔖]      [👤]       │
│ Capture    Vocab    Profile     │
└─────────────────────────────────┘
```

**Container:**
- Position: fixed, bottom 0, full width
- Height: 56px + `env(safe-area-inset-bottom)`
- Background: `#ffffff`
- Border-top: `1px solid #eeeeee`
- Z-index: 40

**Tab item:**
- Flex: 1 (equal thirds)
- Icon: 24px
- Label: 11px, weight 400
- Active state: icon + label both `#f5a742`
- Inactive state: icon + label `#bbbbbb`
- Tap: no animation (instant)

**V1 note:** Only "Capture" tab is functional. Vocab and Profile show empty states.

### 5.6 Circular Progress Ring

Multicolored segmented ring — shows daily/total capture progress.

```
     ╭──────╮
    /  [    ] \
    \  [    ] /
     ╰──────╯
   Segment colors rotate:
   yellow → green → teal → blue → purple → pink
```

**Spec:**
- Size: 120px diameter
- Stroke width: 6px
- Gap between segments: ~4deg
- Segment colors (in order): `#f5d742`, `#7ec87e`, `#52c5c5`, `#6699ee`, `#9b77dd`, `#ee77aa`
- Background track: `#eeeeee` (full ring, unfilled portion)
- Implementation: SVG `<circle>` with `stroke-dasharray`
- Center: empty (white)

**Usage:** Home screen between the greeting and the categories section.

### 5.7 Category Tile Card

2-column grid of colored category cards.

**Container:**
- Aspect ratio: 1:1
- Border-radius: 20px
- Background: category color (solid, muted pastel)
- Padding: 16px
- Overflow: hidden
- No border

**Content layout:**
```
┌──────────────────┐
│ Category Name    │
│ X Words          │
│                  │
│            [img] │  ← object floats bottom-right
└──────────────────┘
```

**Category name:** 17px, weight 600, white
**Word count:** 12px, weight 400, `rgba(255,255,255,0.8)`
**Object image:** 60px, absolute bottom-right, object-fit contain, no shadow

**Tap state:** `scale(0.97)`, `0.2s ease`

### 5.8 Close / Back Button

Used on capture and detail overlays.

- Size: 36px circle
- Background: `rgba(255,255,255,0.92)`
- Box shadow: `0 1px 6px rgba(0,0,0,0.10)`
- Icon: `‹` (chevron) OR `✕` depending on context
- Position: absolute, top 16px + safe area, left 16px
- Z-index: 101

### 5.9 Name Input Field

```css
width: 100%;
max-width: 360px;
padding: 12px 16px;
border: none;
border-radius: 20px;
background: #f5f5f5;      /* light grey, NOT white on white */
font-size: 14px;
text-align: center;
color: #1a1a1a;
outline: none;
```

- Placeholder: `#ccc`, text "Name this object..."
- Focus: background → `#efefef` (slightly darker, no outline)
- No box shadow (flat, inset feel)

---

## 6. Screens

### 6.1 Home / Grid Screen

```
┌─────────────────────────────────┐
│  09:01       [status bar]       │
├─────────────────────────────────┤
│                                 │
│  May 19                         │  ← 13px, #999
│  Good Morning                   │  ← 28px, weight 400
│  Awesome! You've snapped 2...   │  ← 15px, #999
│                                 │
│         (progress ring)         │  ← 120px circular ring
│                                 │
│  Collections                    │  ← 17px, weight 600
│                                 │
│  ┌──────────┐  ┌──────────┐    │
│  │ Food &   │  │ People & │    │  ← category tiles
│  │ Drinks   │  │ Family   │    │
│  │ 1 Word   │  │ 0 Words  │    │
│  └──────────┘  └──────────┘    │
│                                 │
├─────────────────────────────────┤
│  [📷]        [🔖]       [👤]   │  ← tab bar
└─────────────────────────────────┘
```

### 6.2 Collection / Object Grid (tapping a category)

```
┌─────────────────────────────────┐
│  ‹  May 19                      │
│     2 Words                     │
│                                 │
│  [image]        [image]         │  ← objects float on white
│  Object Name    Object Name     │  ← 15px bold
│  May 19, 2026   May 18, 2026    │  ← 11px, #bbb
│                                 │
│         (progress ring)         │
│                                 │
├─────────────────────────────────┤
│  [📷]        [🔖]       [👤]   │
└─────────────────────────────────┘
```

### 6.3 Capture Screen (camera live)

```
┌─────────────────────────────────┐
│  ✕                              │
│                                 │
│  ┌──────────────────────────┐   │
│  │                          │   │
│  │      [live camera]       │   │
│  │                          │   │
│  └──────────────────────────┘   │
│                                 │
│  [ Name this object...     ]    │
│                                 │
│         [↺]  [✓]  [✕]          │  ← only ✓ active while filming
│                                 │
│  Point at an object and tap ✓   │
└─────────────────────────────────┘
```

### 6.4 Review Screen (after photo taken)

```
┌─────────────────────────────────┐
│  ‹  Categories                  │
│                                 │
│         ~~~ glow ~~~            │
│        [  object img  ]         │  ← centered, ~220px
│         ~~~ glow ~~~            │
│                                 │
│      Object Name  🔊            │  ← 22px bold + speaker icon
│      May 19, 2026               │  ← 14px, #999
│                                 │
│      [↺]    [  ✓  ]    [✕]     │  ← three-button row
│                                 │
│  Not what you expected?         │
│  Tap to adjust                  │
└─────────────────────────────────┘
```

### 6.5 Detail View

```
┌─────────────────────────────────┐
│  ✕                              │
│                                 │
│         ~~~ glow ~~~            │
│       [   object img   ]        │  ← 80% screen width
│         ~~~ glow ~~~            │
│                                 │
│       Object Name               │  ← 22px bold, centered
│       May 19, 2026              │  ← 14px, #999, centered
│                                 │
└─────────────────────────────────┘
```

---

## 7. Shadows & Depth

### 7.1 Object Drop Shadow (grid)

```css
filter: drop-shadow(0 6px 16px rgba(0,0,0,0.12));
```

Slightly more visible than before — white bg means shadow is the only depth cue.

### 7.2 Object Drop Shadow (review/detail)

```css
filter: drop-shadow(0 8px 20px rgba(0,0,0,0.15));
```

Deeper shadow on white + glow background.

### 7.3 Button Shadows

```css
/* FAB */
box-shadow: 0 6px 20px rgba(245,167,66,0.35);

/* Close/back button */
box-shadow: 0 1px 6px rgba(0,0,0,0.10);
```

No shadow on input fields (flat grey bg does the job).

---

## 8. Interactions & Animations

### 8.1 Tap States

| Element | Transform | Duration |
|---------|-----------|----------|
| Grid card | scale(0.97) | 0.2s ease |
| FAB | scale(0.95) | 0.15s ease |
| Confirm button (✓) | scale(0.93) | 0.15s ease |
| Replay / Reject | scale(0.95) | 0.15s ease |
| Category tile | scale(0.97) | 0.2s ease |
| Tab item | none | instant |

### 8.2 View Transitions

| Transition | Animation | Duration |
|------------|-----------|----------|
| Grid → Capture | slide up from bottom | 0.3s ease |
| Grid → Detail | fade in overlay | 0.2s ease |
| Review → Grid (confirm) | quick fade out | 0.2s ease |
| Review → Grid (reject) | instant | — |
| Any → Grid (back/close) | reverse of open | 0.2s ease |

### 8.3 Loading States

- **Photo capture:** Confirm button disabled, shows spinner or `…`
- **Camera startup:** Dark `#1a1a1a` bg while stream loads
- **Image in grid:** No placeholder (images load from localStorage, near-instant)

---

## 9. Responsive Behavior

### 9.1 Mobile (375px–667px) — MVP target

- 2-column object grid, 16px gap
- Tab bar always fixed at bottom
- FAB above tab bar (bottom: 72px)
- All overlays are full-screen

### 9.2 Larger phones (390px–430px)

- Grid cards grow proportionally (grid is `1fr 1fr`, inherits width)
- No layout changes needed

### 9.3 Tablet/Desktop — Future

Out of scope for V1. Not designed.

---

## 10. Accessibility

### 10.1 Color Contrast

| Pair | Ratio | WCAG |
|------|-------|------|
| `#1a1a1a` on `#ffffff` | 16.1:1 | AAA |
| `#999` on `#ffffff` | 3.9:1 | AA (large text) |
| `#ffffff` on `#f5a742` | 3.1:1 | AA (large/bold) |
| `#ffffff` on `#9585bf` | 4.6:1 | AA |
| `#ffffff` on `#8a9a64` | 3.5:1 | AA (large/bold) |

### 10.2 Touch Targets

| Element | Size |
|---------|------|
| FAB | 58px ✓ |
| Tab bar item | full 1/3 width × 56px ✓ |
| Confirm button | 60px ✓ |
| Replay / Reject | 52px ✓ |
| Back / close | 36px ⚠️ (borderline — ensure tap area is padded to 44px) |
| Grid card | ~160px+ ✓ |

### 10.3 Motion

- All animations 0.15–0.3s, no looping, no autoplay

---

## 11. Design Tokens (CSS Variables)

```css
:root {
  /* Background */
  --color-bg:             #ffffff;
  --color-surface:        #f7f7f7;
  --color-divider:        #eeeeee;

  /* Text */
  --color-text-primary:   #1a1a1a;
  --color-text-secondary: #999999;
  --color-text-tertiary:  #bbbbbb;

  /* Accent */
  --color-accent:         #f5a742;
  --color-accent-dark:    #e8962e;
  --color-accent-glow:    rgba(245,167,66,0.35);

  /* Category tiles */
  --color-cat-food:       #9585bf;
  --color-cat-people:     #7fa0c0;
  --color-cat-body:       #9a7aaa;
  --color-cat-nature:     #8a9a64;
  --color-cat-home:       #b07882;
  --color-cat-school:     #a89060;

  /* Functional */
  --color-camera-bg:      #1a1a1a;
  --color-btn-neutral:    #efefef;

  /* Typography */
  --font:         -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --fs-xs:        11px;
  --fs-sm:        13px;
  --fs-base:      14px;
  --fs-md:        15px;
  --fs-lg:        17px;
  --fs-xl:        22px;
  --fs-2xl:       28px;
  --fw-regular:   400;
  --fw-semibold:  600;
  --fw-bold:      700;   /* ← object names */

  /* Spacing */
  --sp-xs:   4px;
  --sp-sm:   8px;
  --sp-md:   12px;
  --sp-lg:   16px;
  --sp-xl:   20px;
  --sp-2xl:  24px;
  --sp-3xl:  32px;
  --sp-4xl:  48px;

  /* Radii */
  --r-sm:    12px;
  --r-md:    20px;
  --r-lg:    24px;
  --r-full:  50%;

  /* Shadows */
  --sh-object:    drop-shadow(0 6px 16px rgba(0,0,0,0.12));
  --sh-object-lg: drop-shadow(0 8px 20px rgba(0,0,0,0.15));
  --sh-fab:       0 6px 20px rgba(245,167,66,0.35);
  --sh-close:     0 1px 6px rgba(0,0,0,0.10);

  /* Transitions */
  --tx-fast:  0.15s ease;
  --tx-base:  0.2s ease;
  --tx-slow:  0.3s ease;
}
```

---

## 12. What Changed from v1.0 (Change Log)

| Area | Old | New |
|------|-----|-----|
| Background | `#faf8f6` cream gradient | `#ffffff` white |
| Grid cards | Glass container (rgba white, blur) | No container — image floats on white |
| Object name weight | 500 (medium) | **700 (bold)** |
| Accent color | `#e8b4a8` peachy beige | `#f5a742` warm orange |
| Dotted texture | Yes (opacity 0.12) | **Removed** |
| Button gradient | Peach-to-brown | Solid orange |
| Detail screen | Glass container | White bg + radial glow behind image |
| Navigation | FAB only | Tab bar + FAB |
| New: Review screen | Not in spec | Added (3-button row) |
| New: Progress ring | Not in spec | Added (multicolor SVG) |
| New: Category tiles | Not in spec | Added (6 muted pastel colors) |

---

## 13. Design Checklist (Updated)

- [ ] Background is pure white on all screens
- [ ] Grid objects float with no card container
- [ ] Object names are bold (weight 700)
- [ ] Orange accent (`#f5a742`) used for FAB, confirm button, active tab
- [ ] Tab bar is fixed at bottom with safe area padding
- [ ] Category tiles use correct muted pastel colors
- [ ] Warm glow appears behind objects on detail/review screens
- [ ] Three-button review row is properly sized (Confirm > Replay/Reject)
- [ ] All text meets WCAG AA contrast
- [ ] Touch targets 44px minimum (pad close button tap area)
- [ ] Drop shadows are the only depth cue in the grid
- [ ] No gradients on backgrounds (solid white only)

---

**Design System Version:** 2.0
**Last Updated:** May 24, 2026
**Updated by:** Vidhi × Claude (based on CapWords visual reference)
**Breaking changes from v1.0:** See Section 12
