# Memories — Product Requirements Document

**Version:** 2.0
**Last updated:** May 2026
**Owner:** Vidhi Doshi

---

## Why This Exists

Most photo apps capture moments — people, places, events. This app captures *things.*

The vintage key from your first apartment. The mug your grandmother left behind. The toy you've carried since childhood. Objects hold stories too. But they don't get the same treatment — no album, no journal, no beautiful place to put them.

Memories is that place.

---

## Mission

Give everyday objects the care they deserve — a beautiful, private home that lives on your phone.

---

## Vision

A personal object museum in your pocket. Every thing you've loved, found, or kept — documented as a clean floating sticker, yours to keep forever.

---

## Who This Is For

Someone who notices things. Who holds onto a concert ticket stub, a weird rock, a broken watch they still love. They don't need a productivity tool. They need a place that treats their things as meaningful.

Not a power user. Not someone who will pay for cloud sync on day one. Just someone who sees the app and thinks — *yes, I want this.*

---

## What Success Looks Like (V1)

A person opens the app, captures one object, sees it float beautifully in their collection, and feels something. That's it. That's the whole bar.

Secondary: someone who sees the app on a portfolio or link thinks — "this person can build and has taste."

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
Capture → See it beautifully → Name it → Keep it
```

Every design and engineering decision should protect this loop. If it adds steps, adds friction, or adds noise — it doesn't ship.

---

## Epics

### Epic 1 — Capture
The moment you take a photo and something beautiful comes out the other end.

- Open camera via FAB
- Live camera preview, shutter button
- Background removal processing with animation
- Object appears clean, with white stroke (sticker effect)
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

### Epic 3 — Object Detail + Edit (Read + Update)
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

**Done when:** A user can delete an object they don't want, without drama.

---

### Epic 5 — Polish
The small things that make it feel like a real product, not a prototype.

- Processing animation that feels premium (not fake-busy)
- Smooth transitions between states
- Object "arrival" animation when entering the review screen
- Seed data with relative dates, not hardcoded ones
- Nothing broken on iOS Safari

**Done when:** Someone watching a screen recording of the app thinks it looks finished.

---

## Technical Constraints (V1)

- Vanilla HTML/CSS/JS — no framework, no build step
- localStorage only — no backend, no accounts
- Mobile-first: 375px–430px
- Single file: `index.html`
- Must run over HTTPS (required for camera API on iOS)

---

## Open Questions

1. What's the processing animation? (Three options exist — decision needed)
2. Does background removal stay disabled (DEV_SKIP_BG) or do we wire up client-side ML?
3. What happens when localStorage fills up? (User needs a warning before data loss)

---

## What's Definitely Later

- Reason to return (daily surfaced memory, streak, something)
- Multiple images per object (to show context/scale)
- Notes or tags per object
- Export / share as sticker image
