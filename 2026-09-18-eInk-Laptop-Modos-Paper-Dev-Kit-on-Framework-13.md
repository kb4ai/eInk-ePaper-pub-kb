# E-ink laptop: Modos Paper Dev Kit on a Framework Laptop 13

**Researched 2026-09-18.** Trigger: Modos (@Modostech) posted a 60 Hz e-ink panel running on a
Framework Laptop 13, driven by their Paper Dev Kit, on 2026-09-17. This document works out what is
actually buyable, what physically fits, and which configurations are worth building — with the
strongest host and panel options identified.

⚠ **Prices, stock and ship dates below are as measured on 2026-09-18** and rot fast. Every one is
sourced at the bottom with its URL. Re-check before spending money.

## TL;DR

* **There is no e-ink Framework laptop you can buy.** The tweet is a community build by
  **Cittadhammo**, not a Modos or Framework product. Modos's own "Paper Laptop" is on hold.
* **The display mod and the CPU choice are independent.** The e-ink work is entirely display-side, so
  you can specify the *strongest* Framework 13 mainboard without it affecting the build at all. Pick
  the **Ryzen AI 9 HX 370** and stop thinking about it.
* **The panel does not fit a stock Framework lid, and the signal path does not connect.** Two separate
  blockers, both requiring custom work — see "Why this is not a display-kit swap".
* **Cheapest useful step is not a laptop at all**: the 13" Dev Kit or a Flow on the desk, $599–$799.

## What you can actually buy (2026-09-18)

| Product | What it is | Status | Price | Source |
|---|---|---|---|---|
| **13" Paper Dev Kit** | 13.3" 1600×1200 E Ink panel + Glider FPGA driver board + Glider Mega Adapter | In stock ("limited items") | **$599** | Crowd Supply |
| **6" Paper Dev Kit** | 1448×1072 panel, same controller | In stock | **$199** | Crowd Supply |
| **Modos Flow** | Finished 13.3" 3200×2400 portable e-ink **monitor**, touch | Pre-order; ships target **2026-12-10** | **$699** B&W / **$799** colour | Crowd Supply |

⚠ **Correction to the figures circulating with the tweet:** the dev kits are **$599 / $199**, not
$699 / $249. Both Crowd Supply comparison tables (the Paper Monitor page and the Flow page) agree on
$599 and $199, and an independent answer-with-citations check returned the same. The $699 figure is
the **Flow B&W** price, which is a different product.

Shipping is real, not promised: as of the 2026-04-01 campaign update Modos had shipped **260× 13"
kits and 215× 6" kits**.

## Why this is not a display-kit swap

Two independent blockers. Either one alone would force a custom lid.

### 1. The signal path does not connect

* The Framework 13 lid is **eDP**. The connector is an **IPEX 20455-040E**, 40-pin, on the BOE
  NE135FBM-N41 (and NE135A1M-NY1 for the 2.8k). Framework publishes the full pinout.
* The Glider board's video **inputs** are **USB-C DisplayPort Alt Mode** (via an on-board PTN3460) and
  **DVI over micro-HDMI** (via an ADV7611). It has no eDP input.
* ⇒ **You cannot wire the lid's eDP header into Glider.** eDP is what the mainboard *emits* to a panel;
  Glider wants DisplayPort *as a monitor would receive it*.

⚠ A widely-repeated claim in the DIY Perks build thread — *"it should be as trivial as hooking up the
internal laptop display header to the driver board"* — is **wrong for this reason**. The workable path
is to feed Glider from a **USB-C port in DP Alt Mode**, which on a Framework 13 means consuming an
expansion-card bay (or routing internally from a mainboard USB-C), and finding somewhere in the
chassis for the driver board.

### 2. The panel does not fit the lid

| | active area | aspect | diagonal |
|---|---|---|---|
| Framework 13 lid (BOE NE135FBM-N41) | **284.933 × 189.955 mm** | 3:2 | 13.5" |
| 13.3" 4:3 E Ink panel (ED133UT3 class) | **≈270.3 × 202.7 mm** | 4:3 | 13.3" |

⇒ The e-ink panel is about **15 mm narrower and 13 mm taller** than the opening. It does not drop in.
A **custom lid / chassis** is required — which is exactly what the community thread concluded, with
3D-printed-then-metal prototyping floated as the route.

⚠ The Framework figure is vendor-quoted. The e-ink figure is **derived from geometry** (13.3"
diagonal at 4:3 → 270.26 × 202.69 mm), not read off a datasheet — E Ink's own datasheet value should
be confirmed before anyone cuts material.

## The panels Glider can drive

The kit ships with the **Glider Mega Adapter**, which covers 4.3"–13.3". The 13.3" family sits on the
**39-pin 0.3 mm pitch** connector:

* **ED133UT3** — 1600×1200, 150 PPI, Carta 1000, monochrome. The panel in the 13" kit.
* **ES133UTx / ED133UTx** — same 1600×1200 13.3" class.
* **EC133UJ1** — 13.3" **colour** (Kaleido-class), 1600×1200. ⇒ a colour e-ink laptop is on the table.

Other pitches on the same adapter: 33-pin 0.5 mm (9.7" ED097xxx), 0.5 mm 7.8"–10.3", 34-pin 0.5 mm
(6.0" ED060xxx), 50-pin 0.5 mm (11.3" ED113TCx).

⚠ **Flow's 3200×2400 300 PPI panel is not available as a kit panel.** Flow is a sealed monitor with
its own controller (an AMD Zynq 7000 SoC per third-party coverage, not the Spartan-6 Glider). If you
want 300 PPI e-ink today, you buy a Flow and use it as a monitor — you cannot put that panel in a lid.
This is the single biggest limitation of the DIY route: **the buildable panel is 150 PPI.**

## Controller capability

* **Glider / Caster**, Xilinx Spartan-6 LX16 + DDR3-800 framebuffer, STM32H750 for USB/firmware.
* Up to **75 Hz** on the dev kit; Caster is specified to drive e-paper at up to 60 Hz.
* Processing delay **< 20 µs**; 133 MP/s with error-diffusion dithering on, 200 MP/s off.
* Binary, 4-level and 16-level greyscale; hybrid auto binary→16-level mode; regional updates and
  runtime mode switching via a C API.
* E-paper supply provides **±15 V at up to 1 A peak** — large panels need this; budget for it.

## Strongest host: Framework Laptop 13 mainboards (2026-09-18)

Because the mod is display-side, **choose the strongest board freely.**

| Board | Cores | Notes |
|---|---|---|
| **AMD Ryzen AI 9 HX 370** | **12C / 24T** | ⭐ **Strongest option on the platform.** Radeon 890M graphics |
| AMD Ryzen AI 7 350 | — | mid |
| AMD Ryzen AI 5 340 | — | entry |
| Intel Core Ultra 7 165H | — | ⭐ strongest Intel (Core Ultra Series 1 / Meteor Lake) |
| Intel Core Ultra 7 155H · Ultra 5 125H | — | below it |

⚠ Mainboard generations move roughly annually; re-check the Framework marketplace before ordering.
Core counts beyond the HX 370's 12C/24T were not verified per-SKU here.

## Configurations worth considering

### A. Desk monitor — no modification (recommended first step)

13" Dev Kit ($599) or Flow ($699/$799) on USB-C, laptop untouched. **Flow is the better display**
(3200×2400 vs 1600×1200, touch, frontlight on the colour model) — but note Flow runs at **40 Hz on
bus power alone and reaches its full 60 Hz only with additional power**, so a portable-only setup is
a 40 Hz setup.

### B. Framework 13 + Dev Kit in a custom lid — the Cittadhammo route

The actual build from the tweet. Requires: 13" Dev Kit, a custom lid/chassis (3D print → metal),
internal USB-C routing in DP Alt Mode, space and power for the Glider board. **Accept 150 PPI.**
Entry point for details is the Modos Discord and the DIY Perks thread.

### C. Hybrid — keep the LCD lid, carry the e-ink

Strongest Framework 13 as normal + Dev Kit or Flow as a portable second screen. All of the e-ink
benefit, none of the chassis work, and the LCD stays available for anything e-ink is bad at.

### D. Buy a finished e-ink-ish laptop instead

Not researched in depth here; named in the community thread as prior art: **Lenovo ThinkBook Plus
Gen 4** (hybrid LCD/colour-e-ink), and **MNT Reform** as the open-hardware chassis precedent. ⇒ worth
a separate comparison document.

## Parts list for configuration B

1. Framework Laptop 13, DIY edition, **Ryzen AI 9 HX 370** mainboard
2. Modos **13" Paper Dev Kit** — $599 (panel + Glider board + Mega Adapter)
3. Custom lid/chassis — 3D print for prototyping, metal print (e.g. JLCPCB) for the final
4. Internal USB-C → Glider cabling in DP Alt Mode, plus a bay or internal route
5. Power provision for Glider's ±15 V rail
6. ⚠ Not yet specified: hinge, bezel retention, panel-to-lid bonding, and whether the lid can close
   on the panel's thickness

## ⚠ Contested: panel lifetime under fast refresh

Genuinely unresolved, and it decides whether configuration B is sane. **Both positions recorded, not
adjudicated:**

* **Against** (community, 2025-08-19): E Ink panels have a finite refresh budget, "ballpark
  10,000,000 refreshes per pixel"; at 60 Hz that is ~50 hours of continuous full-rate refresh. Partial
  refreshes may be worse. Commercial e-paper monitors reportedly degrade after 2–5 years at 30–40 Hz.
* **For** (Modos, and their Flow page, 2026): the E Ink *material* is long-lived and the driving
  *electronics* are the stress point; their approach "does not increase the total number of refresh
  cycles", it starts responding sooner. In their testing, physical damage, pressure, heat and moisture
  dominate failures, not fast refresh.
* **Field reports** (community, 2025-08-21): several e-ink devices used heavily for years, including
  video and scrolling, with no visible degradation.

⭐ **What would settle it:** the ED133UT3 datasheet's own refresh-endurance figure, and a
Modos-published cycle count. Neither was obtained on 2026-09-18. Until then, treat "60 Hz all day for
years" as unproven in both directions — and note that the *usage that matters* (terminal, text, PDFs,
reading) refreshes far less than 60 Hz continuously.

## Open questions

* ED133UT3 datasheet: exact active area, and the vendor refresh-endurance number.
* Does the Framework 13 lid physically close over a Glider-driven panel, or does the build need a
  thicker lid?
* Can Glider be powered from the laptop's own rails rather than a separate supply?
* Is there a documented internal USB-C tap on the Framework 13 mainboard, or must an expansion bay be
  consumed?
* Flow's controller: third-party coverage says AMD Zynq 7000; unconfirmed against Modos's own docs.

## Sources

All accessed **2026-09-18** unless noted.

* Modos tweet (the trigger), 2026-09-17 — <https://x.com/Modostech/status/2100673674302918780>
* Video short — <https://www.youtube.com/shorts/ZSxYI14JdMM>
* Modos Paper Monitor / Dev Kit, Crowd Supply — <https://www.crowdsupply.com/modos-tech/modos-paper-monitor/>
* Shipping-progress update, 2026-04-01 — <https://www.crowdsupply.com/modos-tech/modos-paper-monitor/updates/progress-on-shipping-cases-and-firmware>
* Modos Flow, Crowd Supply — <https://www.crowdsupply.com/modos-tech/modos-flow>
* Glider open hardware — <https://github.com/Modos-Labs/Glider>
* Framework Laptop 13 display pinout and panel part numbers — <https://github.com/FrameworkComputer/Framework-Laptop-13/tree/main/Display>
* Framework 13 mainboard line-up — <https://frame.work/marketplace/mainboards>
* "Building a e-ink Laptop", DIY Perks forum, thread opened by cittadhammo 2025-08-18 — <https://forum.diyperks.com/general-general/building-a-e-ink-laptop/>
* BOE NE135FBM-N41 panel data — <https://www.panelook.com/NE135FBM-N41_BOE_13.5_LCM_invitemdetail_271103.html>
* E Ink ED133UT3 — <https://www.panelook.com/ED133UT3_E_Ink_13.3_EPD_overview_54559.html>
* Modos Discord (community entry point for the build) — <https://discord.gg/6ktE6VxSyh>
* "Building an E-Ink Laptop", alexsoto.dev — <https://alexsoto.dev/building-an-e-ink-laptop.html>

## Routing note

Whole-machine Framework Laptop 13 knowledge (mainboard generations, chassis, Linux support) is
**laptop-model** material and belongs in `hardware-kb/hw-computers/` as
`hw-computers-framework-13-*-kb` if that repo is ever created — not here. This document stays in the
e-ink repo because its subject is the **display and its controller**; it records only as much
Framework detail as the display question needs. Connector and DP-Alt-Mode background belongs in
`hardware-kb/hw-interfaces-pub-kb/`.
