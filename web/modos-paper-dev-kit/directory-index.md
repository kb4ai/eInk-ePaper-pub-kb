# Modos Paper Dev Kit / Glider / Modos Flow — Research Directory Index

Captured **2026-09-18**. Companion to the analysis in
`../../2026-09-18-eInk-Laptop-Modos-Paper-Dev-Kit-on-Framework-13.md`.

## Directory Structure Overview

```
web/modos-paper-dev-kit/
├── directory-index.md
├── official-pages/
└── research-sources/
```

## Why these captures exist

Every price, stock state and ship date in the companion analysis rots. These captures are the
**evidence as it stood on 2026-09-18**, so a later reader can tell whether a figure changed or was
wrong to begin with. Both Crowd Supply captures contain the string `$599`, which is the dev-kit price
the analysis cites *against* the $699 figure that circulated with Modos's 2026-09-17 post.

## Official Pages (`official-pages/`)

1. **Modos Paper Monitor / Paper Dev Kit** — `www_crowdsupply_com_modos-tech_modos-paper-monitor.*`
   Campaign page: Glider driver-board reference design, Caster gateware capabilities, the Glider Mega
   Adapter's supported panel list by connector pitch, and the comparison table carrying the $599 /
   $199 kit prices.
2. **Modos Flow** — `www_crowdsupply_com_modos-tech_modos-flow.*`
   Finished 13.3" 3200×2400 monitor: specifications, the 40 Hz-on-bus-power vs 60 Hz-with-extra-power
   distinction, Modos's own position on panel longevity under fast refresh, and the $699 / $799
   pricing.

## Research Sources (`research-sources/`)

1. **"Building a e-ink Laptop", DIY Perks forum** —
   `forum_diyperks_com_general-general_building-a-e-ink-laptop.*`
   Thread opened 2025-08-18 by **cittadhammo**, the community member Modos credited for the Framework
   build. Contains the chassis discussion, and both sides of the **contested panel-lifetime question**
   (the "~10,000,000 refreshes per pixel" claim and the counter-reports). ⚠ Also contains the
   *incorrect* claim that the build is "as trivial as hooking up the internal laptop display header to
   the driver board" — see the companion analysis for why the eDP/DisplayPort direction rules that out.
2. **Framework Laptop 13 display documentation (GitHub)** —
   `github_com_FrameworkComputer_Framework-Laptop-13_tree_main_Display.*`
   Full 40-pin eDP pinout, connector part number **IPEX 20455-040E**, and the panel part numbers
   (BOE NE135FBM-N41, NE135A1M-NY1 for the 2.8k). This is the primary evidence for the signal-path
   blocker.

## File Format Guide

Captured with `exa-ai-search --contents <url> --full --json` (not jina.ai_reader, unlike the older
`web/` directories in this repo):

* **`.json`** — the retrieved page content as returned by the fetch
* **`.url`** — the original URL

⚠ These are **content extractions, not archival snapshots**: no images, no styling, and the extractor
may drop page regions.
⛔ **They may also be CACHED rather than live.** Re-fetching the Paper Monitor page on 2026-09-20
returned a byte-identical result to the 2026-09-18 capture (same "Limited items in stock", same 436
backers) while a search index the same day reported 479 backers and "ships within three business
days". ⇒ A capture dates the *index*, not the fetch. Never cite one as the current state of a page. For the dev kit's live order section in particular, the extraction did not
include the order widget — the prices cited come from the on-page comparison tables, cross-checked
against an independent citation-backed query.

## Coverage

* ✅ Controller and gateware specifications (Glider / Caster)
* ✅ Supported panel families by connector pitch
* ✅ Pricing and stock state, with the correction to the circulating figures
* ✅ Framework 13 display connector and panel part numbers
* ✅ The community build thread and its lifetime debate
* ⚠ **ED133UT3 datasheet not captured** — active area is derived from geometry, and the vendor
  refresh-endurance figure is still missing. This is the top gap.
* ⚠ Flow's controller (reported as AMD Zynq 7000 by third parties) unconfirmed against Modos docs
* ⚠ No manuals; no teardown of the Framework lid to confirm closure over a Glider-driven panel
