# collectobjects — Product Requirements Document

**Version:** 2.0
**Last updated:** May 2026
**Owner:** Vidhi Doshi

---

## Why This Exists

Most photo apps are built around moments — people, places, events. This app is built around *things.*

The coffee that looked perfect. The mirror spotted at Miniso. The book on the desk. The phone case saved up for. Objects carry meaning, but a camera roll treats them the same as everything else — no curation, no context, no care.

collectobjects is the space that takes them seriously.

---

## Mission

Give the objects people love a beautiful, intentional home on their phone.

---

## Vision

A personal collection of everything the user has ever found beautiful or meaningful — photographed, cut clean, and kept. Private, considered, and entirely their own.

---

## The Core Differentiator

Other apps save a photo. This app saves the *object.*

Background removal is not a feature. It is the product's central proposition. Once the background is gone, what remains is the object itself — clean, floating, catalogued. That is a fundamentally different thing from a screenshot or a saved image.

---

## User Persona

**Name:** Khushi

**Age:** 22–30

**Location:** Urban India — Bangalore, Mumbai, Delhi, Pune

**Who she is:**
Khushi has opinions about her phone case. She watches "things I got this month" videos not for the haul, but for the objects themselves. She photographs her coffee, her reading glasses, the lamp in a café she liked. Her Instagram saved folder is effectively a mood board. She knows what Daily Objects is, and she has bought from them.

She does not call herself a collector. But she is one.

**What she is looking for:**
A space that treats her things with the same care she gives them. Not a camera roll dump. Not a Pinterest board of other people's objects. Her things — presented beautifully, kept privately.

**Why she would use collectobjects:**
She photographs one object, watches the background disappear, and the object appears clean and centred. She understands the product immediately. She does not need to be sold on it. She just needs to see it once.

**Why she would share it:**
Because the collection itself looks good. And she notices when things look good.

---

## What Success Looks Like (V1)

Khushi photographs one object, sees it appear clean in her collection, and feels the app understands her. That is the full measure for V1.

Secondary objective: a hiring manager or designer views the portfolio link and thinks — "this is not for me, but I can see exactly who it is for, and it has been built with care."

---

## Out of Scope for V1

The following will not be built in this version. They are future considerations, not rejected ideas.

- Cloud sync or user accounts
- Social sharing or export
- Categories and tagging
- Search or filtering
- Dark mode
- Tablet or desktop layout
- Monetisation

---

## The Core Loop

```
Photograph it → object appears clean → name it → keep it
```

Every product and engineering decision should protect this loop. Anything that adds steps, friction, or noise does not ship.

---

## Epics

### Epic 1 — Capture
The experience of taking a photo and having something beautiful come out the other end.

- Open camera via FAB
- Live camera preview with shutter button
- Background removal with a considered processing animation
- Object appears clean with white outline
- Option to name the object
- Save to collection

**Definition of done:** A user captures an object and the result feels worth keeping.

---

### Epic 2 — Collection
The home screen. Should feel like a personal gallery, not a list.

- 2-column grid, most recent first
- Objects float directly on the background — no card containers, no borders
- Object name and date displayed below each
- Object count shown in the header

**Definition of done:** The grid feels satisfying to look at with four objects in it.

---

### Epic 3 — Object Detail and Rename
Tap any object to view it properly and rename it if needed.

- Full-screen view with the object large and centred
- Name is editable inline — tap to edit, confirm on Enter or dismiss
- Back button returns to the collection

**Definition of done:** A user can open an object and correct the name without friction.

---

### Epic 4 — Delete
Objects must be removable. Mistakes happen and the collection should remain accurate.

- Delete option available from the detail view
- A single confirmation step to prevent accidental deletion
- Grid refreshes immediately after

**Definition of done:** A user can remove an unwanted object cleanly, without drama.

---

### Epic 5 — Polish
The details that separate a prototype from a product.

- Processing animation that feels considered, not artificially busy
- Object arrival animation on the review screen — the moment the object appears should feel intentional
- Smooth transitions between all states
- Seed data with dates relative to today, not hardcoded
- Fully functional on iOS Safari

**Definition of done:** Someone watching a screen recording of the app assumes it is a finished product.

---

### Epic 6 — Onboarding
The app should communicate its purpose within the first few seconds, without instruction.

- Visual, not text-heavy — one or two screens at most
- Communicates who the app is for
- Demonstrates the core mechanic before the user has to do anything
- Leads directly into the app — no gates, no sign-up

**Definition of done:** A first-time user understands the app without anyone explaining it to them.

---

## Technical Constraints (V1)

- Vanilla HTML, CSS, and JavaScript — no framework, no build step
- localStorage only — no backend, no user accounts
- Mobile-first: 375px–430px viewport
- Single file: `index.html`
- HTTPS required (camera API dependency on iOS)

---

## Open Questions

1. **Processing animation** — three directions have been proposed (scan, spotlight, dots + reveal). Decision required before Epic 5 begins.
2. **Background removal** — currently disabled in development (DEV_SKIP_BG). Decision needed on whether to enable client-side ML or keep deferred.
3. **Storage limits** — localStorage has a hard cap. A user warning before silent data loss is needed, approach not yet defined.

---

## Planned for Later Versions

- A reason to return — daily surfaced object, streak, or similar
- Multiple images per object
- Notes attached to an object
- Long-press multi-select for bulk delete
- Export or share functionality
