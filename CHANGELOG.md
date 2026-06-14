# Code Blue Navi — Changelog
UCI Health ALERT

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
