eInk / ePaper displays. Monitors, panels, controllers, and the devices built from them.

⚠ **This repo is PUBLIC on GitHub** (`kb4ai/eInk-ePaper-pub-kb`). ⛔ No hostnames, MACs, IPs, serials,
account names or absolute local paths — those belong in a `*-our-devices-local` repo. Routing added
2026-09-18.

⚠ **Location caveat:** this repo sits *inside* `hardware-2025-kb/`, a wrapper repo that tracks one
staged-deleted file and does **not** track this directory. ⇒ Commit e-ink content **here**, never in
the wrapper. Promoting this repo to a top-level `hardware-kb/hw-eink-epaper-pub-kb/` is proposed and
undecided as of 2026-09-18; the history travels with the repo either way.

## Where things go

• `<YYYY-MM-DD>-<topic>.md` (repo root) → a research document on one question. Newest:
  `2026-09-19-Framework-Configurations-For-An-eInk-Build.md` (what to buy, in what order, and what
  staging costs), `2026-09-19-Laptops-With-eInk-Displays-Compatibility-Survey.md` (which laptops can
  host e-ink at all) and `2026-09-18-eInk-Laptop-Modos-Paper-Dev-Kit-on-Framework-13.md` (the
  Framework 13 build and its blockers).
• `TODO.md` (repo root) → open items, so gaps are visible rather than buried in prose. Read it before
  starting e-ink work; it records what we deliberately are NOT doing, with reasons.
• `<Vendor>-<model>.<Tool>.DeepResearch.md` (repo root) → raw deep-research output, tool named in the
  filename. Present: Dasung Paperlike 25.3", Onyx Boox Mira Pro 25.3", eInk phone-size comparison.
• `web/<device-slug>/` → archived sources for one device or product family, with
  `official-pages/`, `research-sources/`, `reviews/`, `specs/`, `manuals/` and a `directory-index.md`
  that says what was captured AND what was not. One slug per product line.

## Current `web/` slugs

* `modos-paper-dev-kit/` — Modos Paper Dev Kit, Glider controller, Modos Flow, plus the Framework
  Laptop 13 display documentation. Captured 2026-09-18 with `exa-ai-search`.
* `dasung-paperlike-25.3/` · `dasung-revolutionary-37hz-13/` — Dasung monitors
* `onyx-boox-mira-13/` · `onyx-boox-mira-pro-25.3/` · `onyx-boox-mira-pro-monochrome/` ·
  `onyx-boox-mira-pro-color-2024-2025/` — Onyx Boox monitors

⚠ The older `web/` dirs were captured with `jina.ai_reader` (`.content.txt`, `.title.txt`,
`.links.json`, …); `modos-paper-dev-kit/` was captured with `exa-ai-search` (`.json` + `.url`). Both
shapes are in use — say which you used in the slug's `directory-index.md`.

## What does NOT belong here

* **Whole-machine laptop knowledge** (mainboards, chassis, Linux support for a specific model) →
  `hardware-kb/hw-computers/`, as `hw-computers-${model}-${tier}-kb`. This repo records only as much
  host detail as a display question needs.
* **Connectors, buses and protocols in general** (eDP, DisplayPort Alt Mode, HDMI) →
  `hardware-kb/hw-interfaces-pub-kb/`.
* **Our own units** — what we bought, what it cost us, how it is wired, measured wear →
  a `*-our-devices-local` repo. ⛔ Never here.
* **E-reader tablets as devices** (Boox Tab, settings and tweaks) → `hardware-kb/device-settings-shared-kb/`.

## Conventions

* Record every source with its **URL and access date**; put dated claims (price, stock, ship date) in
  a table marked as-measured, and archive the page under `web/<slug>/` so a later reader can tell
  whether the figure changed or was wrong.
* When a claim is genuinely disputed, record **both positions and what evidence would settle it**
  rather than picking a side. See the panel-lifetime section of the 2026-09-18 document.
* Mark derived numbers as derived. Geometry is not a datasheet.

See `../../DEVICE_RESEARCH_METHODOLOGY.md` for the tree-wide research process. ⚠ That file lives
outside every repo and is unversioned, so this link does not resolve on GitHub.
