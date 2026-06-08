Code Blue Navi
Mobile-optimized resuscitation timing and documentation tool for code blue navigation
UCI Health ALERT Team — Acute Care Rapid Response & Code Blue Response

Overview
Code Blue Navi is a Progressive Web App (PWA) built for real-time use during in-hospital cardiac arrest events. It was designed by and for the UCI Health ALERT Team to reduce decision latency, improve closed-loop communication, and support accurate GWTG-Resuscitation documentation during live code blue events.
The app runs entirely in the browser with no installation required and works offline after the first load. It is optimized for one-handed phone use under high-stress conditions.

Features
Timers

Code Duration — starts the moment the code begins
CPR Ring Timer — 2-minute compression cycle with visual countdown
Pre-charge alert — ring turns yellow at 1:45, prompting defibrillator pre-charge
Pulse/Rhythm Check — ring turns red and blinks at 2:00; continues counting elapsed time
Time-off-chest counter — tracks pause duration with color escalation at 10 seconds
Epinephrine timer — turns pink at 3 min (due), red at 5 min (overdue), with haptic alerts
Sub-run tracking — each CPR restart after ROSC is numbered and duration-stamped

Actions

One-tap epinephrine logging with dose count badge
Shock delivery logging (default 200J, editable, back-chartable)
Medication bottom sheet with dose count badges per drug
Rhythm identification (VF, pVT, PEA, Asystole, ROSC)
ROSC confirmation with post-arrest rhythm selection and CPR run duration stamp

Procedures & Interventions

Intubation with airway confirmation method (ETCO₂ waveform, numeric, color capnography, or pending)
Synchronized cardioversion with AHA joule presets and rhythm selection
Transcutaneous pacing with mA, rate, and underlying rhythm
Needle decompression, chest tube, IO, CVC, A-line, fingerstick
Custom free-text event entry

Documentation

Real-time event log with elapsed time and wall clock timestamps
GWTG-Resuscitation required measures flagged with ★ and cyan highlight
Warning events filtered from log to reduce noise
Copy-to-clipboard export formatted for pasting into Epic or any notes system
End Code confirmation modal with total duration stamp


GWTG-Resuscitation Alignment
The following events are automatically flagged as GWTG-required measures in the event log:

Code onset (start time)
First CPR compression (initial compressions)
Initial rhythm identification
All defibrillation events (time + joules)
All epinephrine administrations (dose, route, time)
Intubation (time + confirmation method)
ROSC (time + post-arrest rhythm + CPR run duration)
Code end (total duration)

This supports accurate and complete data submission for the GWTG-Resuscitation Bronze designation and Acute Response Committee reporting.

Installation — PWA (Recommended)
No app store required. Installs directly to the home screen as a native-feeling app.
iPhone (Safari only):

Open the app URL in Safari
Tap the Share button (box with arrow)
Tap "Add to Home Screen"
Tap "Add"

Android (Chrome):

Open the app URL in Chrome
Tap the three-dot menu
Tap "Add to Home Screen"
Tap "Add"

The app will appear on the home screen with a full-screen layout and no browser chrome. It works offline after the first load.

Deployment
This is a single-file HTML application. To deploy:

Place index.html in the root of this repository
Enable GitHub Pages: Settings → Pages → Deploy from branch → main → / (root)
The app will be live at https://your-username.github.io/code-blue-navi

No build process, no dependencies, no server required.

Project Context
Code Blue Navi was built as part of a broader resuscitation quality improvement initiative at UCI Health, including:

The Compress to Success PDSA project targeting chest compression fraction ≥25%
ZOLL CaseReview integration for post-event data analysis
A structured code blue debriefing program using the GAS model
Pursuit of GWTG-Resuscitation Bronze designation (Q4 2026 target)

The app was designed to complement — not replace — Epic Code Narrator documentation, serving as a real-time navigation and timing aid during the event itself.

Built By
Cristian Rosa — RN, MSN, CCRN
UCI Health ALERT Team
Clinical Nursing Leadership | Resuscitation QI

2026 Cristian Rosa. All rights reserved.
