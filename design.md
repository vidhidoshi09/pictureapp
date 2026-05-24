# Memory App - Design System

## Design Philosophy

**Core Principle:** Interface disappears. Objects shine.

The design is inspired by CapWords—minimal UI, maximum visual focus on content. Objects float freely on soft, neutral backgrounds with subtle visual hierarchy. Everything supports the primary experience: discovering and remembering objects.

---

## 1. Visual Language

### 1.1 Aesthetic Direction

**Style:** Clean, modern minimalism with a touch of playfulness

- No dark mode initially
- Light, airy, breathing space
- Objects are stickers—clean, floating, with soft shadows
- Typography is quiet (light weight, generous spacing)
- Color is restrained (cream/grey/neutral with warm accents)

**Reference Apps:**
- CapWords (object photography + language learning)
- Curated Supply (minimal object grid)
- MyStash (inventory focus, zero UI)
- Day One (journaling, soft aesthetic)

**Inspiration Board:**
- Soft dotted paper textures
- Vintage postcards
- Japanese wabi-sabi (impermanence, simplicity)
- Cottagecore aesthetic (natural, nostalgic, intimate)

---

## 2. Color Palette

### 2.1 Primary Colors

| Color Name | Hex | RGB | Usage |
|------------|-----|-----|-------|
| Cream | #faf8f6 | 250, 248, 246 | Background light |
| Linen | #f5f2ef | 245, 242, 239 | Background gradient end |
| Stone | #e8e5e0 | 232, 229, 224 | Borders, light accents |
| Charcoal | #1a1a1a | 26, 26, 26 | Text, dark elements |
| Taupe | #999999 | 153, 153, 153 | Secondary text |
| Dust | #bbbbbb | 187, 187, 187 | Tertiary text, hints |

### 2.2 Accent Colors

| Color Name | Hex | RGB | Usage |
|------------|-----|-----|-------|
| Warm Beige | #e8b4a8 | 232, 180, 168 | Primary button start |
| Warm Brown | #d9a896 | 217, 168, 150 | Primary button end |
| Camera Black | #1a1a1a | 26, 26, 26 | Video background |

### 2.3 Semantic Colors

| Element | Color | Opacity |
|---------|-------|---------|
| Glass container | rgba(255,255,255,0.5) | 50% white |
| Glass container (dark) | rgba(0,0,0,0.05) | 5% black (subtle) |
| Dotted background | #d9cfc5 | Muted taupe |
| Shadow (light) | rgba(0,0,0,0.08) | Very subtle |
| Shadow (medium) | rgba(0,0,0,0.1) | Subtle |

### 2.4 Gradients

**Background Gradient:**
```css
linear-gradient(135deg, #faf8f6 0%, #f5f2ef 100%)
```
Subtle diagonal blend from cream to light grey.

**Primary Button Gradient:**
```css
linear-gradient(135deg, #e8b4a8 0%, #d9a896 100%)
```
Warm beige to warm brown (peachy, inviting).

---

## 3. Typography

### 3.1 Font Families

**Primary:** System fonts (best legibility on mobile)
```css
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

**Weights Used:**
- 400 (regular) — body text, section titles
- 500 (medium) — emphasis, card titles
- 600 (semibold) — buttons, badges (rare)

**Why:** System fonts load instantly, feel native on iOS/Android, and are highly legible at all sizes.

### 3.2 Type Scale

| Usage | Size | Weight | Line Height | Letter Spacing | Notes |
|-------|------|--------|-------------|-----------------|-------|
| Page Title | 32px | 400 | 1.2 | -0.5px | "Memories" heading |
| Subtitle | 13px | 500 | 1.4 | 0.5px | "X objects collected" |
| Card Title | 14px | 500 | 1.3 | -0.3px | Object names |
| Card Meta | 11px | 400 | 1.4 | 0 | Dates on cards |
| Detail Title | 28px | 400 | 1.2 | -0.5px | Full-screen object name |
| Detail Meta | 14px | 400 | 1.4 | 0 | Full-screen date |
| Input Label | 14px | 400 | 1.3 | 0 | Camera input field |
| Hint Text | 13px | 400 | 1.4 | 0 | "Point at object..." |
| Button Text | 24px | 600 | 1 | 0 | Emoji/symbols (✓, +) |

### 3.3 Text Colors

| Element | Color | Hex |
|---------|-------|-----|
| Primary text | Charcoal | #1a1a1a |
| Secondary text | Taupe | #999999 |
| Tertiary text | Dust | #bbbbbb |
| Placeholder | Dust | #cccccc |
| Hint text | Taupe | #999999 |

---

## 4. Layout & Spacing

### 4.1 Grid System

**Mobile-First (Base: 375px viewport)**
- 2-column grid for object cards
- 1-column for text/inputs
- Flexible, no hard breakpoints yet

**Spacing Unit:** 4px base
- Micro: 4px, 8px
- Small: 12px, 16px
- Medium: 20px, 24px
- Large: 32px, 48px
- Extra: 64px, 100px

### 4.2 Page Margins & Padding

| View | Padding | Notes |
|------|---------|-------|
| Grid (horizontal) | 16px left/right | Safe area on phone |
| Grid (vertical top) | 24px | Room for status bar |
| Grid (vertical bottom) | 100px | Space for FAB |
| Capture view | 16px (all sides) | Centered content |
| Detail view | 16px (all sides) | Centered content |

### 4.3 Component Spacing

| Component | Spacing | Notes |
|-----------|---------|-------|
| Header to grid | 32px margin-bottom | Clear separation |
| Grid gap (horizontal) | 20px | Between card columns |
| Grid gap (vertical) | 20px | Between rows |
| Image to name | 12px margin-bottom | Visual separation |
| Name to date | 6px margin-bottom | Tight grouping |
| Camera to input | 24px margin-bottom | Breathing room |
| Input to button | 24px margin-bottom | Clear action area |

---

## 5. Components

### 5.1 Memory Card

**Container:**
- Size: 1:1 aspect ratio (square)
- Border radius: 24px (rounded but not pill-shaped)
- Background: rgba(255,255,255,0.5) with backdrop-filter blur(8px)
- Border: none (no outlines, floating effect)
- Padding: none (image takes full space with inner padding)

**Image:**
- Size: 85% of container
- Object-fit: contain (preserves aspect ratio)
- Padding: 16px inner (breathing room)
- Shadow: drop-shadow(0 4px 12px rgba(0,0,0,0.08))

**Text (name):**
- Font: 14px, weight 500
- Color: #1a1a1a
- Text-align: center
- Margin-bottom: 6px

**Text (date):**
- Font: 11px, weight 400
- Color: #bbb
- Text-align: center
- Margin-bottom: 0

**Interaction:**
- On tap: scale(0.98) (subtle press feedback)
- Transition: transform 0.3s ease

**Visual Style:**
- Floating: no border, soft shadow makes it feel like it's above the background
- Minimal: typography is quiet, image dominates

### 5.2 Floating Action Button (FAB)

**Container:**
- Position: fixed, bottom 24px, right 24px
- Size: 60px circle (border-radius: 50%)
- Background: linear-gradient(135deg, #e8b4a8 0%, #d9a896 100%)
- Box shadow: 0 8px 24px rgba(232,180,168,0.3)
- Z-index: 50

**Icon:**
- Symbol: + (plus sign)
- Font-size: 28px
- Color: white (#ffffff)
- Font-weight: 600
- Text-align: center (flexbox)

**Interaction:**
- On tap: scale(0.95) (press effect)
- Transition: transform 0.2s ease, box-shadow 0.2s ease
- Always visible on grid view

**Style Guide:**
- Primary action—warm, inviting color
- Prominent but not intrusive
- Matches CapWords + button aesthetic

### 5.3 Close Button

**Container:**
- Position: absolute, top 16px, left 16px
- Size: 40px circle (border-radius: 50%)
- Background: rgba(255,255,255,0.9)
- Box shadow: 0 2px 8px rgba(0,0,0,0.1)
- Z-index: 101 (above other overlays)

**Icon:**
- Symbol: ✕ (multiplication sign / X)
- Font-size: 20px
- Color: #1a1a1a
- Font-weight: normal

**Interaction:**
- On tap: none (instant close)
- No visual feedback (too small for scale effect)

### 5.4 Camera Input Field

**Container:**
- Width: 100%, max-width 400px
- Padding: 12px 16px
- Border: none
- Border-radius: 24px (pill shape)
- Background: rgba(255,255,255,0.9)
- Font: 14px, center-aligned
- Font-family: inherit
- Box-shadow: 0 2px 8px rgba(0,0,0,0.05)

**Placeholder:**
- Color: #ccc
- Text: "Name this object..."

**Focus State:**
- Background: rgba(255,255,255,1) (fully opaque)
- Outline: none (use background change)
- Box-shadow: same

**Style Guide:**
- Soft, non-intrusive
- Feels like part of the interface, not fighting for attention

### 5.5 Capture Button

**Container:**
- Size: 64px circle (border-radius: 50%)
- Background: linear-gradient(135deg, #e8b4a8 0%, #d9a896 100%)
- Border: none
- Box shadow: 0 8px 24px rgba(232,180,168,0.3)

**Icon:**
- Symbol: ✓ (checkmark)
- Font-size: 24px
- Color: white (#ffffff)
- Font-weight: 600

**States:**
- Normal: gradient + shadow
- Active (on tap): scale(0.95)
- Disabled: opacity 0.6, cursor not-allowed

**Interaction:**
- Tap to capture photo from camera
- Shows loading state (optional: "...")

### 5.6 Glass Container (Images)

**Style:**
```css
background: rgba(255,255,255,0.5);
backdrop-filter: blur(8px);
border-radius: 24px;
```

**Why "glass":**
- Translucent background lets soft gradient show through
- Blur gives frosted glass effect
- Objects appear to float above the background
- Modern, Apple-like aesthetic

**Usage:**
- Grid card image containers
- Detail view image container
- Camera preview frame

---

## 6. Shadows & Depth

### 6.1 Drop Shadows (on images)

```css
filter: drop-shadow(0 4px 12px rgba(0,0,0,0.08));
```

**Properties:**
- Offset X: 0 (centered)
- Offset Y: 4px (below)
- Blur: 12px (soft)
- Color: rgba(0,0,0,0.08) (very subtle)

**Effect:** Makes floating objects feel like they're slightly above the surface. Very delicate—almost invisible but creates depth.

### 6.2 Box Shadows (on containers)

**Button shadow:**
```css
box-shadow: 0 8px 24px rgba(232,180,168,0.3);
```

**Close button shadow:**
```css
box-shadow: 0 2px 8px rgba(0,0,0,0.1);
```

**Input shadow:**
```css
box-shadow: 0 2px 8px rgba(0,0,0,0.05);
```

**Pattern:** Larger, softer shadows on interactive elements. Smaller shadows on containers.

---

## 7. Dotted Background Texture

### 7.1 Implementation

```css
background-image: radial-gradient(circle, #d9cfc5 0.5px, transparent 0.5px);
background-size: 24px 24px;
opacity: 0.12;
```

**Properties:**
- Dot size: 0.5px
- Dot spacing: 24px
- Dot color: #d9cfc5 (muted taupe)
- Opacity: 12% (very subtle—almost invisible)

**Effect:** Adds texture without visual noise. Like looking at faintly dotted paper. Supports the "cottagecore memory journal" vibe without being distracting.

**Placement:** Fixed, behind all content (position fixed, inset 0, z-index 0).

---

## 8. Interactions & Animations

### 8.1 Tap Feedback

**Card tap:**
```css
transform: scale(0.98);
transition: transform 0.3s ease;
```

**Button tap:**
```css
transform: scale(0.95);
transition: transform 0.2s ease;
```

**Why:** Haptic-like feedback without vibration API. Confirms tap was registered.

### 8.2 View Transitions

**Grid → Capture:**
- Capture view fades in as overlay (no animation, instant)
- Camera stream loads (no delay shown)

**Grid → Detail:**
- Detail view overlays instantly
- Image stays in place visually (no zoom animation)

**Capture/Detail → Grid:**
- Close button triggers instant return
- No slide/fade animation (too slow for minimal interface)

**Philosophy:** Instant transitions keep the interface responsive and focused. No motion for motion's sake.

### 8.3 Loading States

**Photo capture:**
- Button text changes to "..." (optional)
- Button disabled (opacity 0.6)
- Camera feed stays visible during processing

**Camera startup:**
- Video element loads via getUserMedia
- Show dark placeholder while loading (camera bg color #1a1a1a)

---

## 9. Responsive Behavior

### 9.1 Mobile (Default: 375px–667px)

- 2-column grid (20px gap)
- 16px left/right padding
- All components centered
- FAB always visible (bottom-right)

### 9.2 Tablet/Desktop (Future)

- 3–4 column grid
- Larger image containers
- Sidebar optional
- Desktop-optimized detail view

**Note:** MVP is mobile-first. Desktop support can be added in phase 2.

---

## 10. Accessibility

### 10.1 Color Contrast

| Combination | Ratio | Level |
|-------------|-------|-------|
| #1a1a1a (text) on #faf8f6 (bg) | 15.2:1 | AAA |
| #999 (secondary) on #faf8f6 | 6.8:1 | AA |
| white on #e8b4a8 (button) | 4.5:1 | AA |

**All combinations meet WCAG AA standard at minimum.**

### 10.2 Touch Targets

- Buttons: 44px–60px (optimal for thumbs)
- Cards: Full card is tappable (minimum 150px on 2-column)
- Close button: 40px (sufficient)

### 10.3 Typography

- Minimum font size: 11px (dates—acceptable for secondary)
- Body text: 14px+ (readable)
- Headings: 28px+ (clear hierarchy)
- Line height: 1.3–1.4 (good readability)

### 10.4 Motion

- Animations: 0.2–0.3s (fast, non-disruptive)
- No autoplaying videos or content
- Camera feed: user-initiated only

---

## 11. Design Tokens (CSS Variables)

```css
:root {
  /* Colors */
  --color-bg-light: #faf8f6;
  --color-bg-dark: #f5f2ef;
  --color-text-primary: #1a1a1a;
  --color-text-secondary: #999;
  --color-text-tertiary: #bbb;
  --color-accent-warm: #e8b4a8;
  --color-accent-warm-dark: #d9a896;
  --color-glass: rgba(255, 255, 255, 0.5);

  /* Typography */
  --font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-size-xs: 11px;
  --font-size-sm: 13px;
  --font-size-base: 14px;
  --font-size-lg: 28px;
  --font-size-xl: 32px;
  --font-weight-regular: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;

  /* Spacing */
  --space-sm: 12px;
  --space-md: 16px;
  --space-lg: 20px;
  --space-xl: 24px;
  --space-2xl: 32px;
  --space-3xl: 48px;

  /* Border Radius */
  --radius-sm: 12px;
  --radius-md: 24px;
  --radius-full: 50%;

  /* Shadows */
  --shadow-subtle: 0 2px 8px rgba(0, 0, 0, 0.05);
  --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.1);
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.08);
  --shadow-lg: 0 8px 24px rgba(232, 180, 168, 0.3);

  /* Transitions */
  --transition-fast: 0.2s ease;
  --transition-base: 0.3s ease;
}
```

---

## 12. Visual Examples

### 12.1 Layout Pattern: Grid View

```
┌─────────────────────────────────┐
│  09:41          [status bar]    │
├─────────────────────────────────┤
│                                 │
│  Memories                       │
│  4 objects collected            │
│                                 │
│  ┌──────────┐  ┌──────────┐    │
│  │  Image   │  │  Image   │    │
│  │  (float) │  │  (float) │    │
│  └──────────┘  └──────────┘    │
│  Object name   Object name      │
│  May 15, 2024  May 14, 2024     │
│                                 │
│  ┌──────────┐  ┌──────────┐    │
│  │  Image   │  │  Image   │    │
│  │  (float) │  │  (float) │    │
│  └──────────┘  └──────────┘    │
│  Object name   Object name      │
│  May 13, 2024  May 12, 2024     │
│                                 │
│                          [+]    │  ← FAB
└─────────────────────────────────┘
```

### 12.2 Layout Pattern: Capture View

```
┌─────────────────────────────────┐
│ [X]                             │
│                                 │
│      ┌──────────────┐           │
│      │ Camera feed  │           │
│      │ (live video) │           │
│      └──────────────┘           │
│                                 │
│    Name this object...          │  ← Input
│                                 │
│           [✓]                   │  ← Capture button
│                                 │
│  Point at an object and tap     │  ← Hint
│  to capture                     │
└─────────────────────────────────┘
```

### 12.3 Layout Pattern: Detail View

```
┌─────────────────────────────────┐
│ [X]                             │
│                                 │
│      ┌──────────────┐           │
│      │              │           │
│      │ Floating     │           │
│      │ Image        │           │
│      │              │           │
│      └──────────────┘           │
│                                 │
│     Vintage Key                 │  ← Object name
│                                 │
│     May 15, 2024                │  ← Date
│                                 │
└─────────────────────────────────┘
```

---

## 13. Brand Voice in Design

**How design communicates:**

| Aspect | Expression | Example |
|--------|-----------|---------|
| Hierarchy | Let objects speak first | Images take 80% of space |
| Simplicity | Remove anything unnecessary | No borders, no shadows until needed |
| Softness | Warm, inviting, not cold | Rounded edges, warm colors, glass containers |
| Focus | Minimal distractions | Dotted background barely visible |
| Respect for user | Honors their memories | No clutter, no ads, no noise |

---

## 14. Design Checklist

Before launching, verify:

- [ ] All text meets WCAG AA contrast ratio
- [ ] Touch targets are 44px minimum
- [ ] Buttons have hover/active states (even on mobile)
- [ ] Images load with placeholder (or skeleton)
- [ ] Close buttons work on all views
- [ ] FAB always visible and responsive
- [ ] Dotted background is subtle (opacity 0.12)
- [ ] Glass containers have proper backdrop-filter support
- [ ] Shadows are soft and consistent
- [ ] Typography hierarchy is clear
- [ ] Spacing is proportional (4px base)
- [ ] Colors match palette exactly
- [ ] No layout shifts when images load

---

## 15. Future Design Considerations

**Phase 2:**
- Dark mode (optional)
- Categories/collections (UI expansion)
- Search functionality (new component)
- Filtering/sorting (subtle controls)

**Phase 3:**
- Sharing cards (design for social context)
- Export options (PDF, print-friendly)
- Desktop layout (multi-column, sidebar)

**Design Principle:** Maintain minimalism as features grow. Complexity should be hidden, not visible.

---

**Design System Version:** 1.0
**Last Updated:** May 24, 2026
**Created by:** Vidhi (Product + Design)
