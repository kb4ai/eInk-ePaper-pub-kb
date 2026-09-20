# Framework configurations for an e-ink build — what to buy, in what order

**Researched 2026-09-19.** Answers five questions: strongest buildable machine, whether you can start
cheap and upgrade, the most reasonable staged path, what that staging costs versus buying maxed, and
whether a stronger Framework exists worth asking Modos about.

Companions: `2026-09-18-eInk-Laptop-Modos-Paper-Dev-Kit-on-Framework-13.md` (the build and its
blockers) and `2026-09-19-Laptops-With-eInk-Displays-Compatibility-Survey.md` (which laptops qualify
at all). ⚠ Prices as measured **2026-09-19**; they rot.

## ⭐ The reframe that changes all five answers

**The kit constrains nothing about the computer.** The Modos Paper Dev Kit is a *monitor*: it takes
USB-C DisplayPort Alt Mode, or DVI over micro-HDMI. It does not care what CPU, how much RAM, which
GPU or how many SSDs are behind that port.

⇒ *"What is the strongest laptop I can build with this kit?"* has no kit-specific answer. It is just
*"what is the strongest laptop"*, and the kit rides along. The two questions are **independent**, and
that independence is what makes the staging question easy.

## 1. The strongest machine

| | Framework Laptop 13 | **Framework Laptop 16** | Framework Desktop |
|---|---|---|---|
| CPU | Ryzen AI 9 HX 370 (12C/24T) | **Ryzen AI 9 HX 370 (12C/24T)** | Ryzen AI Max+ 395 |
| GPU | Radeon 890M integrated only | **RTX 5070 Laptop 12 GB GDDR7** (or Radeon RX 7700S 2nd gen) | integrated (Max+ 395) |
| RAM | 96 GB DDR5-5600, 2× SO-DIMM | **96 GB DDR5-5600, 2× SO-DIMM** | 128 GB LPDDR5X ⛔ **soldered** |
| NVMe | **1×** M.2 2280 (to 8 TB) | **2×** — M.2 2280 + M.2 2230 | — |
| Laptop? | yes | yes | ⛔ no |

⇒ **Strongest laptop: Framework Laptop 16 — HX 370 + RTX 5070 12 GB + 96 GB + 8 TB (2280) and a
second 2230 drive.** The Framework Desktop beats it on raw memory (128 GB) but is not portable and
its RAM is soldered, so it is not upgradeable in the way you are asking about.

⚠ The RTX 5070 is the only real gap between 13 and 16. If you never want a discrete GPU, the 13 gives
you the identical CPU, the identical 96 GB, and one fewer SSD.

## 2. Can you start cheap and upgrade later?

**Yes — this is the entire design thesis of the platform.** But the components differ sharply in how
freely they upgrade, and one boundary is a trap.

| Part | Upgradeable later? | Notes |
|---|---|---|
| **RAM** | ⭐ trivially | 2 SO-DIMM slots, standard DDR5-5600, resellable |
| **NVMe** | ⭐ trivially | standard M.2, resellable or moved to another machine |
| **CPU** | ✅ yes — swap the whole mainboard | $449 → $999; the old board resells |
| **GPU (FW16)** | ✅ yes — expansion bay module | FW16 only |
| **GPU (FW13)** | ⛔ **never** | no discrete option has ever existed for the 13 |

⛔ **The trap: Framework 13 → Framework 16 is NOT an upgrade path.** Different chassis, different
mainboard form factor. Going from a 13 to a 16 is buying a second laptop, not swapping a board. ⇒ If
there is a real chance you will want a discrete GPU, **that decision has to be made at purchase**,
and it is the only one that does.

## 3. The most reasonable staged path

⭐ **Stage on the uncertainty, and the uncertainty is not the CPU — it is whether you like e-ink.**
A staged CPU plan tests the wrong variable. The right first stage costs no laptop money at all.

### Stage 0 — test e-ink on a machine you already own. **$699, no laptop purchase.**

The kit is an external monitor, so plug it into an existing ThinkPad and use it for weeks on real
work — terminal, PDFs, code, long reading — before deciding anything.

⚠ **Check the host's USB-C before assuming, and know the fallback.** A USB-C port is not
automatically a DisplayPort output. On an older ThinkPad — a Lenovo E595, for instance — the single
USB-C is USB 3.1 Gen 1 with DisplayPort Alt Mode per the vendor spec sheet, but **a spec sheet is not
a measurement**: DP-over-USB-C output is one of those things that is frequently untested on a given
unit until the day you need it.

⇒ **The fallback removes the risk entirely:** the dev kit also accepts **DVI over micro-HDMI**. Any
host with a working HDMI output can drive the panel even if its USB-C DP Alt Mode turns out not to
work. ⇒ Before buying, confirm one of the two outputs on the specific machine you plan to use.

⇒ Stage 0 has no hardware risk and no laptop spend. If e-ink disappoints, you stop here, out the cost
of a kit that resells.

### Stage 1 — buy the laptop, on its own merits

Only now, and decided by what you want from a *computer*, not by the e-ink. Buy the **DIY edition**
so you supply your own RAM and SSD.

### Stage 2 — the lid build, if you still want the panel *inside*

⚠ The genuinely risky stage: custom lid, no drop-in, 150 PPI, and two blockers documented in the
companion file. Nothing about stages 0–1 commits you to it.

## 4. What the staging actually costs

Only the **CPU** is worth costing, because RAM and NVMe are swapped so freely that staging them costs
essentially nothing (you resell or repurpose the parts).

FW13 mainboards, 2026-09-19: **AI 5 340 $449 · AI 7 350 $699 · AI 9 HX 370 $999**.
Framework's own refurbished prices are a consistent **~75.5 %** of new ($339 / $509 / $719), which is
a defensible floor for what a used board is worth. The Framework Community Market has done better:
an AI 7 350 sold at **$675** (97 % of new), an HX 370 at **$700** and **$900**.

| Route | Buy now | Buy later | Recover on resale | Total | **Premium vs maxed now** |
|---|---|---|---|---|---|
| **A — maxed immediately** | HX 370 $999 | — | — | **$999** | — |
| **B — cheapest, then max** | AI 5 340 $449 | HX 370 $999 | −$339 (floor) … −$430 (market) | **$1,018 – $1,109** | **+$19 to +$110** |
| **C — middle, then max** | AI 7 350 $699 | HX 370 $999 | −$509 (floor) … −$675 (market) | **$1,023 – $1,189** | **+$24 to +$190** |

⇒ **Staging the CPU costs somewhere between about $20 and $110.** That is a small premium for the
option to change your mind — roughly 2–11 % — and it buys real optionality given the resale market is
active.

⚠ **But it is optionality on the wrong question.** Stage 0 already removes the e-ink risk for free,
and the CPU is not in doubt. ⇒ **Recommendation: do not stage the CPU.** Once you have decided to buy
the laptop at all, buy the mainboard you actually want, and spend the staging effort on RAM and NVMe,
where it is free.

⚠ Non-money costs of staging: two teardowns, two rebuilds, and a second purchase decision later.

## 5. Stronger Frameworks, and what to actually ask Modos

Yes: the **Framework Laptop 16** (dGPU, second NVMe) is stronger than the 13, and the **Framework
Desktop** (Ryzen AI Max+ 395, 128 GB) is stronger still but is not a laptop.

### ⭐ And the stronger laptop looks like the *easier* mechanical target

Envelope comparison of the 13.3" 4:3 e-ink panel against each lid:

| | lid active area | 13.3" 4:3 panel (270.3 × 202.7 mm) |
|---|---|---|
| Framework 13 (13.5", 3:2) | 284.9 × 190.0 mm | ⛔ **12.7 mm too tall** |
| Framework 16 (16", 16:10) | 344.6 × 215.4 mm | ✅ fits, with ~74 mm spare width and **12.7 mm** spare height |

The two lids differ in height by exactly 25.4 mm — one inch — and the panel sits precisely between
them: 12.7 mm too tall for the 13, 12.7 mm of headroom in the 16.

⚠ **Derived, not vendor-confirmed.** The FW13 figure is vendor-quoted; the FW16 figure is computed
from 16" at 16:10; the panel figure is computed from 13.3" at 4:3. This is envelope maths on *active
areas only* — it ignores bezel, hinge, cable routing and the depth available inside the lid. It says
"worth measuring", not "it fits". ⇒ A 13.3" panel in a 16" lid also leaves ~74 mm of dead width, so
the result would look deliberate only with a designed bezel.

### ⚠ The premise to correct before writing to Modos

**The kit does not need adjusting for a different laptop.** It is host-agnostic — any USB-C DP Alt
Mode port drives it. What is laptop-specific is the **lid and chassis**, and that is *not a Modos
product*: the Framework 13 lid was community work (Cittadhammo). Asking Modos to "adjust the kit for
the Framework 16" would be asking them for something the kit does not lack.

⇒ **The questions actually worth asking them** (see `TODO.md`):

1. **Glider board dimensions and mounting** — will it fit inside a laptop lid or lid cavity, or must
   it live in an expansion bay or externally? This is the real integration constraint and we do not
   have the number.
2. **Panel roadmap** — Flow's 300 PPI Carta 1300 panel is *not* available to the kit, so a DIY build
   is stuck at 150 PPI. Is a higher-density kit-drivable panel planned? ⭐ **This matters more than
   any laptop choice**: it is the ceiling on the whole project.
3. **Power** — can Glider's ±15 V rail be fed from laptop-internal power rather than a separate supply?
4. **Community CAD** — given the FW16 geometry above, does anyone have or want a 16 lid design?

## Open items

See `TODO.md` in this repo.
