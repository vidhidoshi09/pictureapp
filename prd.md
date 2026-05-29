# collectobjects — Product Requirements Document

**Version:** 2.0
**Last updated:** May 2026
**Owner:** Vidhi Doshi

---

## Why This Exists

Most photo apps capture moments — people, places, events. This app captures *things.*

The coffee you ordered that looked perfect. The mirror you spotted at Miniso. The book sitting on your desk. The phone case you saved up for. Objects carry meaning too — but your camera roll doesn't know the difference between a trash photo and something you genuinely love.

collectobjects does.

---

## Mission

Give the objects you love a beautiful, intentional home.

---

## Vision

A personal sticker collection of everything you've ever found beautiful. Photograph it, keep it, revisit it. No background noise — just the thing itself, floating clean.

---

## The Differentiator

Everywhere else you save a photo. Here you save the *object.*

Background removal isn't a feature. It's the thesis. The object becomes a sticker — yours, clean, intentional. That's different from a screenshot.

---

## User Persona

**Name:** Ananya (but honestly, it's Vidhi — and everyone like her)

**Age:** 22–30

**Where she lives:** Urban India — Bangalore, Mumbai, Delhi, Pune

**What she's like:**
She has opinions about her phone case. She watches "things I got this month" videos not for the haul but for the objects themselves. She takes photos of her coffee, her reading glasses, the lamp in a café she liked. Her Instagram saved folder is a mood board. She knows what Daily Objects is, and she's bought from them at least once.

She doesn't call herself a collector. But she is one.

**What she wants:**
A place that treats her things with the same care she gives them. Not a camera roll dump. Not a Pinterest board full of other people's things. Her things. Beautiful. Kept.

**Why she'd use collectobjects:**
She sees the app, photographs one thing, watches the background disappear and the object float clean — and she immediately understands. She doesn't need to be sold. She just needs to see it once.

**Why she'd show it to someone:**
Because the collection itself looks good. And she likes showing things that look good.

---

## What Success Looks Like (V1)

Ananya photographs one object, sees it become a sticker, saves it, and feels like the app *gets* her. That's the whole bar.

Secondary: a hiring manager or designer sees the portfolio link, looks at the app, and thinks — "I don't use this, but I understand exactly who does, and this person built it well."

---

## What We Are Not Building (V1)

- Cloud sync or accounts
- Social sharing
- Categories or tagging
- Search
- Dark mode
- Tablet or desktop layout
- Monetisation of any kind

These are not forever-nos. They are not-now-yeses.

---

## The Core Loop

```
Photograph it → it becomes a sticker → name it → keep it
```

Every design and engineering decision should protect this loop. If it adds steps, adds friction, or adds noise — it doesn't ship.

---

## Epics

### Epic 1 — Capture
The moment you take a photo and something beautiful comes out the other end.

- Open camera via FAB
- Live camera preview, shutter button
- Background removal processing with satisfying animation
- Object appears clean with white stroke (sticker effect)
- Option to name it
- Save to collection

**Done when:** Someone captures an object and the result feels worth keeping.

---

### Epic 2 — Collection (Read)
Your objects, displayed beautifully. The home screen should feel like a gallery, not a list.

- 2-column grid, newest first
- Objects float on warm background — no containers, no borders
- Object name + date below each
- Object count in header

**Done when:** Looking at the grid feels satisfying even with just 4 objects.

---

### Epic 3 — Object Detail + Rename (Read + Update)
Tap any object and see it properly. Give it a better name if you want.

- Full-screen overlay with the object large and centered
- Name is editable inline — tap to edit, Enter or dismiss to save
- Close/back returns to grid

**Done when:** A user can open an object and fix a typo in the name without friction.

---

### Epic 4 — Delete
Objects should be removable. Mistakes happen.

- Delete option accessible from the detail view
- One confirmation step to prevent accidents
- Grid updates immediately after

**Done when:** A user can delete something they don't want, without drama.

---

### Epic 5 — Polish
The small things that make it feel like a real product, not a prototype.

- Processing animation that feels premium (not fake-busy)
- Object "arrival" animation on the review screen — it should feel like the sticker is being born
- Smooth transitions between all states
- Seed data with relative dates, not hardcoded ones
- Nothing broken on iOS Safari

**Done when:** Someone watching a screen recording thinks it looks finished.

---

### Epic 6 — Onboarding (First-Time Experience)
The app should tell its own story in the first 5 seconds.

- Short, visual — not a tutorial
- Shows who this is for ("for people who collect the things they love")
- Demonstrates the mechanic (photo → sticker) before the user has to do anything
- One screen, maybe two — then straight into the app

**Done when:** A person who's never heard of the app understands it immediately without anyone explaining it.

---

## Technical Constraints (V1)

- Vanilla HTML/CSS/JS — no framework, no build step
- localStorage only — no backend, no accounts
- Mobile-first: 375px–430px
- Single file: `index.html`
- Must run over HTTPS (required for camera API on iOS)

---

## Open Questions

1. What's the processing animation? (Three options proposed — Option A scan, B spotlight, C dots+reveal — decision needed)
2. Does background removal stay disabled (DEV_SKIP_BG) or do we wire up client-side ML?
3. What happens when localStorage fills up — user needs a warning before silent data loss

---

## What's Definitely Later

- Reason to return (daily surfaced object, streak, something)
- Multiple images per object
- Notes per object
- Export / share as sticker image
- Long-press multi-select delete
