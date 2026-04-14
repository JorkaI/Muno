# Muno — Project Brief

## What is this
Muno is a radically simple flashcard app. Words + definitions only. No tags, flags, gamification, or complexity. The philosophy is: if a feature doesn't help someone learn a word, it doesn't exist.

## Design system
- Dark theme: bg #0A0A0A, surfaces #161616/#1E1E1E, text #F5F5F3/#BFBFBA/#6B6B66
- Font: DM Sans (400, 500, 600)
- Green #4ADE80 = positive/know, Red #F87171 = negative/don't know
- White buttons/FAB on dark bg. Rounded corners (12-16px).
- Minimal — no icons where text works, no decoration

## Screens and flows

### Home
- Logo "muno" top left, nothing else in header
- Stats: words learned count, day streak count
- CTA banner (white): "Begin practice" → opens practice with Inbox folder
- "All folders" section with Edit toggle
- Each folder shows: name, word preview, play button, add button
- Inbox folder is highlighted (border) with "default" badge, cannot be deleted
- Edit mode: red X delete on left, drag grip on right per folder
- FAB bottom-right: opens Add Word modal

### Folder open
- Back arrow, folder name, three-dots menu (rename / delete folder)
- Practice + Edit buttons bar
- Word list: term + definition per row
- Tap word → Edit Word modal
- Edit mode: red X delete button appears on each word
- FAB bottom-right: opens Add Word modal pre-set to this folder

### Practice
- Folder selector dropdown (top-left), Close X (top-right)
- Progress bar (thin, white)
- Counter "3 of 8"
- Flashcard: shows word, tap to flip (shows definition), tap again flips back
- Flip icon at bottom of card (rotates when flipped)
- "Don't know" (red) / "I know" (green) buttons
- If not flipped and button pressed → auto-flips first
- Done screen: checkmark + "All done!" + Back button
- Close returns to folder if opened from one, otherwise home

### Add Word modal (bottom sheet)
- Word input, Definition input, Folder picker (chip buttons)
- Save button (disabled until both fields filled)

### Edit Word modal (same sheet)
- Pre-filled fields + folder picker
- Save + Delete word buttons

### Rename Folder modal
- Single input + Save

## Data model
- Folder: { name, inbox (bool), words[] }
- Word: { t (term), d (definition) }
- Streak: { count, last (date string) }
- Spaced repetition: future feature, keep data model extensible

## Technical decisions
- PWA first (current), React Native later for App Store
- localStorage for persistence
- No backend, no auth, no cloud sync (MVP)
- Offline-first via service worker

## File structure (current PWA)
```
muno-pwa/
├── index.html      ← Full app, all screens
├── manifest.json   ← PWA install config
├── sw.js           ← Service worker (offline)
├── icon-192.png    ← App icon
├── icon-512.png    ← App icon large
└── CLAUDE.md       ← This file
```
