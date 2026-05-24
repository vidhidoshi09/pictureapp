# Memory Collectibles App - Product Requirements Document

## 1. Product Overview

**Product Name:** Memories (working title)

**Vision:** A minimal, object-focused memory storage app where users capture and preserve everyday objects that matter to them. The interface disappears—you're looking at your memories, not an app.

**Core Concept:** Inspired by CapWords (language learning via object photography) but designed for personal memory collection. Users snap photos of objects from their life—vintage keys, blue teapots, croissants, rubber ducks, anything meaningful—and the app stores these as a digital archive of collectibles and memories.

**Target User:** People who collect memories through objects. Designers, creative types, people who appreciate aesthetics and personal curation. Ages 18–40. Initial MVP is solo use (no sharing, no social).

---

## 2. Core User Stories (V1)

**User Story 1: See My Collection**
- As a user, I want to see all my collected objects in a clean grid
- So that I can reminisce and browse my memories
- AC: Grid shows all objects, newest first; count visible; scrollable

**User Story 2: Capture New Object**
- As a user, I want to snap a photo of an object and save it
- So that I can add memories to my collection
- AC: Camera works, can name object (optional), photo saves instantly, appears in grid

**User Story 3: View Object Detail**
- As a user, I want to see a full-screen view of an object
- So that I can appreciate it in detail without UI clutter
- AC: Tap object → full-screen view; close button works; returns to grid

**User Story 4: Track My Collection**
- As a user, I want to know how many objects I've collected
- So that I can see my collection grow
- AC: Header shows "X objects collected" and updates when photo added

---

## 3. Feature Specifications

### 3.1 Grid View (Home Screen)

**Layout:**
- Safe area padding: 24px horizontal, 24px top
- Bottom padding: 100px (for FAB)
- Header section:
  - Title: "Memories" (32px, font-weight 400, letter-spacing -0.5px)
  - Subtitle: "X objects collected" (13px, color #999)
  - Margin bottom: 32px

**Grid:**
- 2 columns
- Gap: 20px
- Grid item (memory card):
  - Image container: aspect ratio 1:1, rounded 24px
  - Background: rgba(255,255,255,0.5) with backdrop-filter blur(8px)
  - Image: 85% of container size, object-fit contain, drop-shadow(0 4px 12px rgba(0,0,0,0.08))
  - Name: 14px, font-weight 500, centered, margin-top 12px
  - Date: 11px, color #bbb, centered, margin-top 6px

**Interaction:**
- Tap any card → detail view
- Visual feedback: scale(0.98) on tap

---

### 3.2 Capture View

**Layout:**
- Full screen overlay (position fixed, inset 0)
- Flexbox centered (align-items center, justify-content center)
- Close button: top-left, 40px circle, white bg, rgba(255,255,255,0.9)

**Camera Section:**
- Container: max-width 400px, aspect ratio 1:1, rounded 24px, background #1a1a1a
- Video element: 100% width/height, object-fit cover
- Margin bottom: 24px

**Input Section:**
- Text input for object name
- Max-width 400px, padding 12px 16px, rounded 24px
- Background: rgba(255,255,255,0.9)
- Font: 14px, center-aligned
- Placeholder: "Name this object..."
- Margin bottom: 24px

**Capture Button:**
- 64px circle (border-radius 50%)
- Gradient background: linear-gradient(#e8b4a8, #d9a896)
- White text: checkmark (✓)
- Box shadow: 0 8px 24px rgba(232,180,168,0.3)
- On tap: scale(0.95)
- On disabled: opacity 0.6

**Hint Text:**
- "Point at an object and tap to capture"
- 13px, color #999, centered
- Position: absolute bottom 48px

---

### 3.3 Detail View

**Layout:**
- Full screen overlay (position fixed, inset 0)
- Flexbox centered
- Close button: top-left, 40px circle (same as capture)

**Image Section:**
- Container: max-width 400px, aspect ratio 1:1, rounded 24px
- Background: rgba(255,255,255,0.5) with backdrop-filter blur(8px)
- Image: 90% of container, object-fit contain, drop-shadow(0 4px 12px rgba(0,0,0,0.08))
- Margin bottom: 48px

**Metadata Section:**
- Name: 28px, font-weight 400, color #1a1a1a, centered, margin-bottom 8px
- Date: 14px, color #999, centered, font-weight 400

---

### 3.4 Floating Action Button (FAB)

**Spec:**
- Position: fixed, bottom 24px, right 24px
- Size: 60px circle
- Background: linear-gradient(#e8b4a8, #d9a896)
- Icon: + (white, 28px)
- Box shadow: 0 8px 24px rgba(232,180,168,0.3)
- On tap: scale(0.95)
- Z-index: 50

**Interaction:**
- Tap → open capture view
- Always visible on grid view
- Hidden on detail/capture views (or visible behind overlay)

---

## 4. Design System

### 4.1 Colors

| Color | Hex | Usage |
|-------|-----|-------|
| Background (light) | #faf8f6 | Primary background |
| Background (dark) | #f5f2ef | Gradient end |
| Text primary | #1a1a1a | Headings, labels |
| Text secondary | #999 | Dates, hints |
| Text tertiary | #bbb | Dimmed text |
| Glass overlay | rgba(255,255,255,0.5) | Image containers |
| Primary button | #e8b4a8 → #d9a896 | FAB, capture button |
| Camera bg | #1a1a1a | Video background |

### 4.2 Typography

| Element | Size | Weight | Letter Spacing | Usage |
|---------|------|--------|-----------------|-------|
| Page title | 32px | 400 | -0.5px | "Memories" header |
| Subtitle | 13px | 500 | 0.5px | "X objects collected" |
| Object name | 14px | 500 | -0.3px | Grid card titles |
| Object date | 11px | 400 | 0 | Grid card dates |
| Detail name | 28px | 400 | -0.5px | Full-screen object name |
| Detail date | 14px | 400 | 0 | Full-screen date |
| Input text | 14px | 400 | 0 | Camera input field |
| Hint text | 13px | 400 | 0 | Camera hint |

**Font Family:** -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif (system fonts)

### 4.3 Spacing

| Element | Value | Usage |
|---------|-------|-------|
| Grid gap | 20px | Space between cards |
| Header margin-bottom | 32px | Below "Memories" heading |
| Page padding horizontal | 16px | Left/right margin |
| Page padding vertical | 24px | Top, plus 100px bottom |
| Border radius (containers) | 24px | Image containers, buttons |
| Border radius (buttons) | 50% | FAB, close button |

### 4.4 Effects

| Effect | Spec | Usage |
|--------|------|-------|
| Backdrop blur | blur(8px) | Glass containers |
| Drop shadow | drop-shadow(0 4px 12px rgba(0,0,0,0.08)) | Floating images |
| Box shadow | 0 8px 24px rgba(232,180,168,0.3) | Buttons |
| Button shadow | 0 2px 8px rgba(0,0,0,0.1) | Close button |
| Dotted background | radial-gradient(0.5px) at 24px spacing, opacity 0.12 | Subtle texture |

### 4.5 Interactions

| Action | Feedback |
|--------|----------|
| Tap card | scale(0.98) |
| Tap button | scale(0.95) |
| Tap + capture | Button disabled, shows "..." |
| Camera stream | Loads via getUserMedia API |

---

## 5. Technical Specifications (V1)

### 5.1 Technology Stack

**Frontend:**
- HTML5 (semantic markup)
- CSS3 (flexbox, grid, backdrop-filter)
- Vanilla JavaScript (ES6+) OR React 18+ with Tailwind
- No external dependencies (camera, storage are native APIs)

**Storage:**
- Browser localStorage only (device-local, single user)
- No backend, no database, no authentication

**Deployment:**
- Vercel (free tier)
- HTTPS (required for camera access on iOS)
- No custom domain required (vercel.app is fine)

**Browser Support:**
- iOS Safari 14+
- Chrome/Firefox 90+ (Android)
- Modern browsers only (ES6, API support)

### 5.2 Data Model

**Memory Object (localStorage format):**
```javascript
{
  id: number,           // timestamp (e.g., 1716576789001)
  name: string,         // user-entered or auto-generated
  date: string,         // formatted: "May 15, 2024"
  image: string         // base64 data URL (PNG or JPEG)
}
```

**Storage Key:** `memories_collection`

**Storage Format:** JSON array of Memory objects

**Max Size:** ~5MB localStorage limit (hundreds of images per device)

### 5.3 Core APIs Used

**Camera:**
```javascript
navigator.mediaDevices.getUserMedia({ video: { facingMode: 'environment' } })
```

**Photo Capture:**
```javascript
canvas.toDataURL('image/jpeg', 0.9)  // Canvas API
```

**Storage:**
```javascript
localStorage.setItem('memories_collection', JSON.stringify(array))
localStorage.getItem('memories_collection')
```

### 5.4 Constraints & Assumptions

**V1 Constraints:**
- Single user per device (no multi-user support)
- Device-local storage only (no sync, no backup)
- Mobile-first design (375px–667px viewport)
- Camera must be permitted by user (app will prompt)
- Photos stored as base64 (impacts storage size)
- No background removal (accept photos as-is)
- No metadata (EXIF) preservation

**Assumptions:**
- User has camera access (phone, tablet)
- User has modern browser (Safari 14+, Chrome 90+)
- User accepts localStorage privacy (device-only data)
- Connection required only for initial app load (works offline after)

---

## 6. V1 Scope (MVP Only)

### 6.1 In Scope (V1)

✅ Grid view with 4 hardcoded sample objects (Key, Teapot, Croissant, Duck)
✅ Real camera capture with live feed
✅ Object name input (optional, auto-generates if blank)
✅ Photo saves to localStorage (device-only)
✅ Detail view (full-screen object view)
✅ Close/back navigation between views
✅ Mobile-first responsive design (375px+)
✅ Soft UI with frosted glass aesthetic (CapWords style)
✅ FAB (+) button for capturing new objects
✅ Object count display (dynamic)
✅ No backgrounds on images (white/light removed visually)
✅ Floating object effect (soft shadows, glass containers)

### 6.2 Explicitly Out of Scope (V1)

❌ Backend/cloud storage (localStorage only)
❌ User authentication (single user, device-local)
❌ Sharing/collaboration (personal use only)
❌ AI background removal (manual cleanup acceptable)
❌ Categories/tagging (flat collection)
❌ Search/filtering (grid only)
❌ Export/download (view only)
❌ Desktop/tablet responsive (mobile 375px–667px only)
❌ Dark mode
❌ Settings/preferences
❌ Undo/delete functionality
❌ Image editing
❌ Offline sync
❌ Multiple devices

---

## 7. Success Metrics (V1)

| Metric | Target | How to Measure |
|--------|--------|-----------------|
| Camera permission granted | 85%+ | Analytics or user testing |
| Photo saves successfully | 100% | localStorage verification |
| App load time | < 1.5s on 4G | Lighthouse report |
| Time to first capture | < 1 minute | User testing |
| Mobile usability | Works iOS + Android | Manual testing |
| No console errors | 0 errors | DevTools check |
| Lighthouse score | 80+ | PageSpeed Insights |
| User feedback | 4/5 stars | Post-launch survey |

---

## 8. Primary User Persona (V1)

### Designer/Creative (Ages 25–35)

**Profile:**
- Location: India (Mumbai, Bangalore)
- Device: iPhone or Android
- Browser: Safari or Chrome
- Interests: Design, aesthetics, personal curation, minimalism

**Goals:**
- Capture and preserve memories of everyday objects
- Build a curated digital collection
- Experience a beautiful, minimal app

**Pain Points:**
- Phone photo library is disorganized
- No app focuses on object collecting (not photo albums, not scrapbooks)
- Wants interface to disappear (just see the objects)

**Motivation:**
- Create a meaningful archive of personal artifacts
- Enjoy beautiful design
- Share app with others (later, in V2)

**Devices Used:**
- iPhone (primary)
- Occasional Android

**App Usage:**
- Daily browsing of collection
- Weekly adding new objects
- Shares photos occasionally with friends via direct link (manual, not built-in)

---

## 9. Acceptance Criteria (V1)

**Functional:**
- [ ] App loads in < 1.5 seconds on 4G
- [ ] Camera opens within 2 taps from grid
- [ ] Photo captures and displays in grid within 2 seconds
- [ ] Grid shows all objects, scrollable if needed
- [ ] Detail view displays full-screen image without distortion
- [ ] Close (X) buttons work on capture and detail views
- [ ] localStorage persists objects across browser refresh
- [ ] Count updates when new photo captured
- [ ] Can return to grid from any view
- [ ] Camera permission request handled (allow/deny)

**Design:**
- [ ] UI is minimal (no visible menus, toolbars, clutter)
- [ ] Objects appear to "float" (soft shadows, glass containers)
- [ ] Dotted background is subtle (barely visible)
- [ ] Grid is 2 columns on 375px+ width
- [ ] All text meets WCAG AA contrast ratio
- [ ] Touch targets are 44px+ minimum
- [ ] No layout shifts when images load
- [ ] FAB is always visible and accessible
- [ ] Transitions feel instant (no delays)
- [ ] Objects display with proper aspect ratio (no stretching)

**Performance:**
- [ ] Lighthouse performance score > 80
- [ ] No console errors
- [ ] Camera feed is smooth (30fps+)
- [ ] App is responsive (< 100ms interaction delay)

---

## 10. Document Info

**Version:** 1.0 (V1 Only)
**Scope:** MVP - single user, device-local, web app only
**Last Updated:** May 24, 2026
**Owner:** Vidhi (Product + Design)

**What This Document Covers:**
- ✅ Everything needed to ship V1
- ❌ Future phases (V2+) are out of scope and not documented here
