# Community builds — e-ink in a laptop

Published work by people who have actually built e-ink laptop setups. Captured 2026-09-20.

⚠ **Scope discipline.** These are private individuals, not vendors or public creators. What is
archived here is their **published technical work** under its own licence, plus the public channel
you would use to ask them a question. ⛔ No personal details, contact harvesting, or profile-building.

## `cittadhammo-omarchy-modos-eink/`

The software half of the Framework 13 e-ink build that Modos amplified on 2026-09-17.

* **Upstream:** <https://github.com/cittadhammo/omarchy-modos-eink> — **MIT licence**, created
  2026-09-16, last push 2026-09-17 (the day of the Modos post). QML + Python.
* **What it is:** an Omarchy 4 (Quickshell) bar widget and service that drives the Modos Paper Dev
  Kit 13" through the Caster/Glider controller's **USB HID** interface — a refresh-mode picker and a
  force-redraw button.
* **Archived here:** `README.md`, `modosctl.py`, `modosctl`, `manifest.json`,
  `69-modos-glider.rules`, `LICENSE`. ⛔ Not archived: the QML UI files and screenshots — get them
  upstream if needed.

### ⭐ Why this matters beyond the software

It is the only first-hand technical account of a working build, and it settles questions our own
research could only speculate about:

* ⭐ **The video path is USB-C DisplayPort Alt Mode, not DVI.** His README states it directly:
  *"USB-C DisplayPort Alt Mode remains the video path; the HID interface is a separate control
  path."* ⚠ This **contradicts** our earlier inference — see the correction note in
  `hw-interfaces-pub-kb/edp-displayport-laptop-panel-hacking/README.md`. The builder's own account
  beats our reading of a schematic.
* **Control is a second, independent channel** over USB HID — so an in-lid build needs USB data to
  the board, not merely video and power.
* **Device identity:** USB VID `0x1209`, PID `0xae86`, panel geometry 1600 × 1200.
* **Non-root access needs a udev rule** for the raw HID node — archived here as
  `69-modos-glider.rules`.
* **The six usable `Mode` enum values**, and the fact that the device's own four on-screen presets
  (Browsing / Typing / Reading / Watching) are *firmware-level combinations* with **no authoritative
  enum-to-preset mapping** published by Modos:

  | `Mode` | intended use |
  |---|---|
  | `FastMonoNoDither` | fastest hard black/white, sharpest text, most stable |
  | `FastMonoBayer` | fast mono, ordered dithering — motion and games |
  | `FastMonoBlueNoise` | fast mono, smoother dithering |
  | `FastGrey` | 4-level greyscale, tuned for text editing |
  | `AutoNoDither` | binary while changing, greyscale once settled |
  | `AutoErrorDiffusion` | hybrid with Floyd–Steinberg-style diffusion when settled |

* ⚠ **API limits, confirmed by him against `src/lib.rs` and the generated header:** no contrast,
  brightness, gamma or front-light control, and **no mode getter** — the mode cannot be read back
  from the device, only remembered locally. The 13" mono kit has no front light anyway.
* The Dev Kit has a **third physical button** that forces a full-screen redraw to clear ghosting.

### ⛔ What is NOT published — the thing we actually wanted

**No lid, bezel, chassis or CAD file of any kind.** The repo is software only. As of 2026-09-20 the
mechanical design of the Framework 13 e-ink lid remains unpublished anywhere we can find.

⇒ **That is the single highest-value question to ask him**, and his repo's issue tracker is the
appropriate public place to ask it.

## Provenance note on the video

The demonstration video (`ZSxYI14JdMM`, "Modos Framework 13", 2:25, 2026-09-17) is on **his own**
channel, not Modos's, and its metadata reports `availability: unlisted` with a 10-subscriber channel.
⇒ It reached a wide audience only because Modos linked it. Treat it as a semi-private upload that was
publicly shared by a third party, not as published content. It carries **no subtitles**, so no
transcript exists to archive. Capture details and checksums:
`../2026-09-20-Is-An-eInk-Framework-Lid-Just-A-Shell-Problem.md`.
