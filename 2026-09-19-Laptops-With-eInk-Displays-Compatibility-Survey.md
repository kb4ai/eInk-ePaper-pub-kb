# Which laptops work with an e-ink display?

**Researched 2026-09-19.** Companion to
`2026-09-18-eInk-Laptop-Modos-Paper-Dev-Kit-on-Framework-13.md`, which covers the Framework 13 build
in depth. That document deferred this question ("worth a separate comparison document"); this is it.

## The short answer

**Exactly one laptop was ever mass-produced with an integrated e-ink screen, and you can no longer
buy it new.** Everything else is either (a) not a laptop, (b) not E Ink, (c) a DIY host driving an
external e-ink panel, or (d) never shipped. The four categories below are worth keeping separate,
because press coverage routinely blurs them.

## 1. Ships with an integrated E Ink display

| Laptop | E-ink panel | Main screen | Status 2026-09-19 |
|---|---|---|---|
| **Lenovo ThinkBook Plus Gen 4** ("Twist") | **12" colour E Ink, 2560×1600, 12 Hz max, 100 nits, frontlit** | 13.3" OLED | ⛔ **Discontinued** — no longer sold by Lenovo |

That is the entire category. A twisting hinge rotates the lid to present either the OLED or the
E Ink face. **Lenovo has released no Gen 5 or later with E Ink.**

⚠ **The 12 Hz ceiling is the point of comparison.** The Modos dev kit runs its panel at up to 75 Hz
and Flow at 60 Hz. The only shipping e-ink laptop ran its at **12 Hz** — which is why reviewers
concluded the second screen "solves no real issues". ⇒ *Integrated* has historically meant *slow*;
the fast e-ink is in the external/DIY route, not in any finished laptop.

## 2. Not a laptop, or not E Ink — the three things most often miscited

* **Daylight DC-1** — a **tablet**, and its "LivePaper" display is **not E Ink**: the vendor
  describes it as "like E Ink, but faster… 60fps", i.e. a reflective backlit LCD. ⚠ Vendor framing,
  not an independent measurement. Do not put it in an E Ink comparison without that caveat.
* **Bigme B1051 Ultra** — 10.3" colour Kaleido 3 **Android** device marketed as an "office notebook".
  Android tablet with a keyboard, not an x86 laptop.
* **Lenovo thinkplus AI Smart Ink Screen A510** — 10.3" colour e-ink office device, same shape of
  thing as the Bigme, same exclusion.

## 3. DIY hosts — a laptop *driving* an e-ink panel

This is the category that actually works today, and it splits in two.

**As an external monitor: essentially any modern laptop qualifies.** The Modos kit and Flow take
**USB-C DisplayPort Alt Mode** (the kit also takes DVI over micro-HDMI). Any laptop with a DP Alt
Mode-capable USB-C port drives them. There is no compatibility list to consult — the requirement is
a port, not a model. Linux, macOS and Windows are all supported.

**As an internal integration (panel in the lid): only open, modular chassis are realistic.**

| Candidate | Why it is a candidate | Status |
|---|---|---|
| **Framework Laptop 13** | Published CAD and display documentation; the build in the 2026-09-17 Modos post | ⭐ The only demonstrated build. Needs a custom lid — see the companion document for the two blockers |
| **MNT Reform** | Open hardware, and designed from the start with a **detachable display housing** meant to be swapped | ⚠ **No e-ink option has ever shipped.** Discussed by the project lead publicly since 2021, never productised |

⛔ **A conventional laptop is not a candidate.** The blockers from the companion document are general,
not Framework-specific: the driver board wants **DisplayPort in**, while a laptop lid header carries
**eDP out** — they do not connect — and a 13.3" 4:3 e-ink panel does not fit a lid cut for a 16:10 or
3:2 LCD. Without published mechanical drawings and a replaceable lid, neither is solvable.

## 4. Announced, never shipped

* **Modos Paper Laptop** — announced early 2022, teased repeatedly, **never released**. The company
  pivoted in early 2024 to the Paper Monitor, and now sells the dev kits and Flow. Modos still talks
  about a laptop; nothing is for sale.

⚠ **Trap — a "review" of a product that does not exist.** A page dated 2026-04-18 presents itself as a
*"Modos Paper Laptop UK Review 2026 | Buying from US Guide"*, complete with a first-person account of
using one. **There is no Modos Paper Laptop to review.** Treat affiliate/reshipping sites reviewing
unreleased hardware as fabricated. Verify against the vendor's own storefront — Modos sells kits and
a monitor, and no laptop.

## What this means in practice

1. **Want e-ink with a laptop today, no hardware work?** Any laptop you already own, plus a 13" Paper
   Dev Kit ($699) or a Flow ($699/$799). The laptop is not the constraint.
2. **Want e-ink *in* the lid?** Framework Laptop 13 plus a custom lid, accepting 150 PPI. The only
   route with a demonstrated example.
3. **Want to buy a finished e-ink laptop?** You cannot. The one that existed is discontinued and ran
   at 12 Hz.

## Open questions

* Is the ThinkBook Plus Gen 4 worth buying **used** as an e-ink laptop? Not assessed — needs pricing,
  Linux support for the twist hinge and the E Ink panel, and whether the 12 Hz panel is usable for
  Greg's workload (terminal, text, PDFs). ⇒ the obvious next piece of research.
* Does MNT Reform's detachable display housing have published mechanical drawings sufficient for an
  e-ink swap, and what panel interface does its display board expose?
* Framework Laptop 16: larger lid, same modularity — does its lid geometry suit a 13.3" 4:3 panel
  better than the 13's? Not examined.

## Sources

All accessed **2026-09-19**.

* Lenovo ThinkBook Plus Gen 4 product page — <https://www.lenovo.com/us/en/model/laptops/thinkbook/thinkbook-plus/lenovo-thinkbook-plus-gen-4-13-inch-intel/len101b0031>
* Lenovo PSREF spec sheet (E Ink panel figures) — <https://psref.lenovo.com/syspool/Sys/PDF/ThinkBook/ThinkBook_Plus_G4_IRU/ThinkBook_Plus_G4_IRU_Spec.pdf>
* Notebookcheck review, ThinkBook Plus Twist Gen 4 — <https://www.notebookcheck.net/Lenovo-ThinkBook-Plus-Twist-Gen-4-convertible-review-E-Ink-and-OLED-hybrid.745202.0.html>
* Windows Central review ("solves no real issues") — <https://www.windowscentral.com/hardware/laptops/lenovo-thinkbook-plus-gen-4-review>
* "What Happened To The Modos Paper Laptop and Paper Monitor?", ePaper Industry Alliance, 2025-05-11 — <https://en.epaperia.com/News/504.html>
* MNT Reform, "How about an e-paper display?", community thread — <https://community.mnt.re/t/how-about-an-e-paper-display/851>
* "Challenges Building an Open-Source E Ink Laptop", HN, with the MNT project lead's comment, 2021 — <https://news.ycombinator.com/item?id=26901757>
* MNT Reform hardware handbook (detachable display housing) — <https://mntre.com/documentation/reform-handbook/hardware.html>
* Daylight DC-1 — <https://daylightcomputer.com/>
* Bigme B1051 Ultra coverage — <https://www.notebookcheck.net/Bigme-launches-Android-office-notebook-with-10-3-inch-color-E-Ink-display-and-Dimensity-1080.1368954.0.html>
