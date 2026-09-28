# Code Blue Navi — Changelog
UCI Health ALERT

---

## Version 1.6 — September 2026

### New Features
- **End Code outcome prompt** — End Code now asks **ROSC** or **Pt expired** before anything locks, with a Cancel that returns to the code untouched (protects against accidental taps)
  - If ROSC was already logged from the Main page, it's preselected so it isn't entered twice
  - **Pt expired** — shows a warning that timers won't be available again until Reset All, runs the initial rhythm confirmation, logs "Code terminated — pt expired" (GWTG-marked), then stops all timers and locks the log
  - **ROSC** — runs the initial rhythm confirmation, then enters **post-ROSC mode**: CPR and epi timers stop, the code timer keeps running, events can still be logged, and the log can be exported at any time
  - **Re-arrest** — tapping Start CPR during post-ROSC starts a new CPR run, logs "Re-arrest — CPR restarted", resumes the epi timer from the last dose, and restores the End Code button
  - **Close Code** — replaces End Code during post-ROSC; shows the same timer warning, then stops the code timer and locks the log
- **Rhythm check review / back-charting** — after the outcome is chosen, a prompt offers to review every pulse/rhythm check (each CPR pause-to-resume window)
  - Walks through checks one at a time, showing pause time, time off chest, any shocks delivered during that check, and the logged rhythm (or "No rhythm logged")
  - Tapping VF / pVT / PEA / Asystole applies immediately: a missing rhythm is inserted as "Rhythm: X (late)" at that pause's timestamp (before any shock or CPR resume); an existing rhythm is silently overwritten
  - Also available any time after the outcome via a **Review Rhythm Checks** button on the Log tab, which shows how many checks are missing a rhythm
  - Gaps are flagged inline in the post-code log with a **+ Rhythm** button that opens just that check
  - Checks that ended in ROSC with no rhythm logged are skipped, since the ROSC entry documents them
- **Live rhythm chips** — while CPR is paused, a VF / pVT / PEA / Asys row appears under the pause bar if no rhythm has been logged since the pause; tapping one logs it normally and hides the row

### Improvements
- **ROSC rhythm picker** — two-column grid so all rhythms and the Confirm button fit on one screen without scrolling; Confirm/Cancel also stay pinned to the bottom of the sheet as a fallback on small phones
- Delete (✕) on log entries is now available in post-ROSC mode as well as after the code is locked

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
