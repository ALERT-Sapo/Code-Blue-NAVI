[CHANGELOG (2).md](https://github.com/user-attachments/files/29944114/CHANGELOG.2.md)
# Code Blue Navi — Changelog
UCI Health ALERT

---

## Version 1.5 — July 2026

### New Features
- **"Copy for Haiku" button** — a second option on the Log tab, next to Share/Export Log, that copies a plain-ASCII version of the log straight to the clipboard
  - Converts the in-app display characters (★ GWTG marker, · bullets, — em dashes, ═/─ separator lines, × in dose counts, ₂ in ETCO₂) to plain equivalents (`*`, `-`, `x`, `2`) — fixes pastes silently failing into restricted fields (e.g. Epic Haiku messages) that reject non-ASCII input
  - The original Share/Export Log button is unchanged and still sends the fully-formatted version — useful when sending to a personal phone or elsewhere formatting isn't an issue

---

## Version 1.4 — July 2026

### Improvements
- **Global tap feedback** — every button, tile, and option across the app now gives a brief visual pulse (brightened glow) on press, a short haptic tick where the device supports it, and a quiet low tone
  - Haptic tick uses the Vibration API (`navigator.vibrate`), same as existing shock/epi/pause alerts — works on Android, silently does nothing on iOS Safari since the API isn't implemented there
  - Audio tone is a short, quiet low-pitched tick, distinct from the app's existing rhythm-check/epi/shock alert tones so it won't be mistaken for one
  - Feedback is suppressed if the touch moves more than ~12px before release, so scrolling through a button (e.g. on the Log tab) doesn't trigger it
  - Implemented as a single global tap listener rather than per-button code, so it applies uniformly and needs no changes if new buttons are added later

---

## Version 1.3 — 2026

### New Features
- **Wake Lock** — requests the Screen Wake Lock API when a code starts, keeping the screen from sleeping/dimming during active use; re-requests on tab visibility change and releases on End Code

---

## Version 1.2 — June 2026

### New Features
- **Initial Rhythm Confirmation on End Code** — tapping End Code now prompts confirmation of the initial rhythm before locking the log
  - If an initial rhythm was logged: confirm it's correct, or select the true rhythm — logs `Initial rhythm corrected: X [initial]` as a GWTG measure, strips `[initial]` from the original entry, and inserts the correction at the top of the log timestamped to code start
  - If no initial rhythm was logged: prompts to add one as a late entry, also GWTG-marked and inserted at the top
  - Both paths include a Skip option to proceed without changes

### Improvements
- **CPR cycle recalculation on delete** — deleting a cycle entry from the post-code log now correctly renumbers remaining cycles and updates the Run · Cycle counter on the panel

---

## Version 1.1 — June 2026

### New Features
- **Insulin** — added to the Medications sheet with a units input popup; logs as "Insulin X units IV"
- **ECMO** — replaces Fingerstick in the Events tab; tap to select from three options: Team Activated, Cannulation Successful, or Cannulation Failed
- **Airway Confirmation** — new button in Events tab for patients already intubated prior to the code blue; prompts for ETCO₂ confirmation method (sub-label: "If intubated prior to CB")
- **CPR Cycle Counter** — CPR panel now displays both Run # and Cycle # in real time (e.g. "Run 1 · Cycle 3"); Run tracks loss-of-pulse events, Cycle tracks compressor rotations within a run
- **Post-Code Log Editing** — after End Code is confirmed, a ✕ button appears on every log entry allowing deletion of accidental entries
- **Smart Delete** — deleting a log entry recalculates and renumbers all affected counts (shocks, epi doses, CPR runs, med badges) so no gaps or mismatches remain

### Improvements
- **Log export** now uses the native iOS share sheet; falls back to clipboard copy, then manual copy — resolves Epic Haiku paste failures on iPhone; button reads "📤 Share / Export Log"
- **Exported log** includes a Totals Summary section: shock count, epi doses, CPR runs, all medication counts, and a list of interventions
- **Bullet separators** added to all entries in the mini log and full event log
- **Unsuccessful Intubation** added as a second option inside the Intubation modal
- Removed **Needle Decompression** from Events grid to restore button alignment

### Bug Fixes
- Fixed delete confirmation modal staying open and firing multiple deletions on repeated taps — modal now closes and nulls the index before any DOM re-render

---

## Version 1.0 — 2026

Initial launch.
