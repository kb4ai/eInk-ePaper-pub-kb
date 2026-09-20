# What Modos actually sells, and what they open-source

**Researched 2026-09-20.** Deeper pass on the Modos product line after a first pass
(`2026-09-18-...-Framework-13.md`) under-researched it. The question behind this document: *does
Modos sell a product you can use to give a Framework laptop an e-ink screen?*

## ⭐ Short answer: yes — they sell the whole electronics half, and open-source more than that

**The 13" Paper Dev Kit IS the product.** Panel + Glider FPGA driver board + Glider Mega Adapter, in
stock, $599. That is everything electronic needed to put e-ink on a laptop. It is not a
laptop-shaped part, and Modos has never claimed it was — but "they don't sell a product for this" is
the wrong summary. They sell the hard part.

What they do **not** sell is a laptop **lid**. Nobody does, for any laptop.

## What you can buy (2026-09-20)

| Product | Contents | Status | Price |
|---|---|---|---|
| **13" Paper Dev Kit** | 13.3" 1600×1200 E Ink panel (ED133UT3 class, Carta 1000, 150 PPI), Glider driver board, Glider Mega Adapter | In stock | **$599** |
| **6" Paper Dev Kit** | 1448×1072 panel, same controller and adapter | In stock | **$199** |
| **Modos Flow** | Finished 13.3" 3200×2400 (300 PPI) monitor, touch, Carta 1300 or Kaleido 3 | Pre-order, ships target 2026-12-10 | **$699** B&W / **$799** colour |

⚠ **Correction carried from the first pass:** the kits are **$599 / $199**, not the $699 / $249 that
circulated with Modos's 2026-09-17 post. $699 is the *Flow* price. Evidence archived in
`web/modos-paper-dev-kit/`.

## ⭐ What Modos open-sources — this is the part the first pass missed

Modos is an open-hardware project, not merely a vendor. The design is public and extensive.

| Component | What it is | Where |
|---|---|---|
| **Glider** | The driver board: **KiCad** PCB source, schematics, firmware (C) | `github.com/Modos-Labs/Glider` — a mirror of the canonical `gitlab.com/zephray/glider` |
| **Caster** | The FPGA gateware (the EPD controller itself) — a **separate** repo | `gitlab.com/zephray/Caster/` |
| ⭐ **Case designs** | **3D-printable enclosures in STL, STP and DWG**, organised by screen size — **6" and 13.3"** — comprising **back plate, frame and buttons** | in the Glider repo |
| **Panel compatibility list** | Which e-paper panels the board drives, by connector pitch | Glider README |

The Glider README is also, deliberately, a **general e-ink technical reference** — the author states
it contains "pretty much everything I know about Eink" because the information is hard to gather
online. It covers controller theory, waveforms, dithering, greyscale modes, and the
with-controller/without-controller split across panel sizes. ⇒ Worth reading on its own merits, quite
apart from buying anything.

Scale and liveness as of 2026-09-20: **2,159 stars, 75 forks, 4 contributors, last push 2026-03-20**.
Principal author **Wenting Zhang (zephray)**; Flow is described as the result of roughly four years
of development, with its designs also open-sourced.

## ⇒ What this changes for a laptop build

The first pass framed the mechanical problem as "you are on your own". That was too pessimistic.
**Both halves of the CAD you would need already exist in public:**

* **Modos publishes a 13.3" module frame** — the part that holds *this panel* — in STL/STP/DWG.
  It is designed for a monitor housing, not a laptop lid, but it is the panel-mounting geometry,
  already solved and in an editable format (STP and DWG, not only mesh).
* **Framework publishes full-system 3D CAD** — `Framework Laptop 13 CAD.stp` and
  `Framework Laptop 13 Pro CAD.stp` in the base of `FrameworkComputer/Framework-Laptop-13`, plus 2D
  drawings. The Laptop 16 repository carries system CAD too.
* **The community has gone further**: `Captain-Pumpkinhead/Framework-13-Vanilla-Reconstruction`
  exists to "reconstruct every physical part of the Framework laptop … so that this repo can be used
  as a resource to begin mods from". There is also a 3D-printable FW13 lower-chassis design
  (2026-01) and a FW13-to-tablet conversion (2026-08), whose author found it "surprisingly easy with
  all the resources that are available".

⚠ **Correction to an earlier claim made in this repo and to Greg on 2026-09-19:** it was stated that
"Framework doesn't publish mechanical drawings — only the eDP pinout". **That is wrong.** It was
based on reading only the repository's `Display/` subdirectory, which indeed contains just a pinout,
and generalising from it to the whole repository. The system STEP files are in the **base
directory**. ⇒ The correct statement is: *Framework publishes system-level CAD; what is absent is a
dimensioned drawing of the lid cavity specifically.*

⇒ **Nobody needs to email anyone for CAD.** What is missing is not data but **design work**: no one
has published a laptop-lid part that marries the two. That is a modelling job on top of two public
inputs, not a request to a vendor.

## What remains genuinely unsolved

* **No published laptop-lid design.** Cittadhammo's Framework 13 build — the one in Modos's post — has
  no public design files found as of 2026-09-20. Their GitHub account exists (42 public repos) with
  nothing e-ink-related surfaced. ⇒ Ask in the Modos Discord rather than assuming it is unpublished.
* **Glider board dimensions are not documented in text.** The PCB is KiCad source, so the number is
  obtainable by opening the file — but nobody has written it down, and it decides whether the board
  can live inside a lid.
* **150 PPI ceiling.** Flow's 300 PPI panel is not available to the kit. This is the limitation most
  likely to disappoint, and no roadmap for a denser kit panel was found.

## Sources

All accessed **2026-09-20** unless noted.

* Modos Paper Monitor / Dev Kit — <https://www.crowdsupply.com/modos-tech/modos-paper-monitor/>
* Modos Flow — <https://www.crowdsupply.com/modos-tech/modos-flow>
* Glider (hardware, firmware, case designs) — <https://github.com/Modos-Labs/Glider/>
* Glider canonical upstream — <https://gitlab.com/zephray/glider>
* Caster EPD controller gateware — <https://gitlab.com/zephray/Caster/>
* Framework Laptop 13 system CAD and docs — <https://github.com/FrameworkComputer/Framework-Laptop-13>
* Framework Laptop 16 repository — <https://github.com/FrameworkComputer/Framework-Laptop-16>
* Community part reconstruction — <https://github.com/Captain-Pumpkinhead/Framework-13-Vanilla-Reconstruction>
* 3D-printable FW13 chassis design, 2026-01 — <https://community.frame.work/t/3d-printable-framework-13-chassis-design/79715>
* FW13 tablet conversion, 2026-08 — <https://community.frame.work/t/framework-13-tablet/84457>
* Modos Discord — <https://discord.gg/6ktE6VxSyh>
