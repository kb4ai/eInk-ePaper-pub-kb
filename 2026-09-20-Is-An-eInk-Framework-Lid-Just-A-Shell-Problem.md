# Is an e-ink Framework lid "just a shell problem"? — and what Framework's newest hardware is

**Researched 2026-09-20** by a seven-dimension parallel sweep with adversarial verification.
⚠ Several earlier conclusions in this repo are **corrected** below. Deep connector/signal analysis and
the archived primary documents live in
`hardware-kb/hw-interfaces-pub-kb/edp-displayport-laptop-panel-hacking/`.

## ⭐ Answers, shortest first

**Is it just a matter of printing a shell for a Framework 16? — No, but it is closer than it looked.**
Three things must be true, and only one of them is a shell:

1. the panel must physically fit the lid — **marginal on the 16, impossible on the 13** (see below);
2. video must reach the Glider board in the lid — **solved, and more simply than first thought**;
3. the Glider board (90 × 80 mm) must live somewhere, with its ±15 V supply.

**Does the FW13/FW16 display connector question matter? — No.** They are nearly the same connector
(same mainboard-side I-PEX 20879-040E; FW16 adds four pins: DDS SCL/SDA, PSR_EN#, OD_EN). It makes no
difference, because **eDP cannot feed Glider in either machine.** eDP is a *source* output; Glider is
a *sink*. No off-the-shelf eDP-source → DP-Alt-Mode adapter exists.

**Can we ask Modos to make it? — You can ask, but they have already answered in public.** Modos has
never offered to sell, design or support a laptop lid. Under their own post showing the build they
replied only *"Credit goes to community member Cittadhammo"*, and left the *"take my money / where
can I buy this lid"* replies unanswered. Their Crowd Supply **Hacking Guide** (2026-07-01) says:
*"Integrate it into something else, like maybe a laptop or a cyberdeck? (Glider is the best fit…)"* —
encouragement, not a product. Their own Paper Laptop has been shelved since 2022.

## ⚠ Correction: the panel does not fit a Framework 13, and barely fits a 16

This repo previously compared the panel's **active area** to the lid's **active area** and reported
~12.7 mm of headroom in a Framework 16. That was the wrong comparison — what has to fit is the panel's
**outline**.

| | dimension | vs FW13 opening (284.93 × 189.96) | vs FW16 opening (344.6 × 215.4) |
|---|---|---|---|
| ED133UT3 **outline** | **285.80 × 213.65 × 0.78 mm** | ⛔ **~23.7 mm too tall, ~0.9 mm too wide** | ✅ fits — by only **~1.75 mm** in height |
| (its active area) | 270.40 × 202.80 mm, 4 mm bezel, 96 g | — | — |

⇒ **A Framework 13 lid cannot take this panel at all** — not "needs a custom lid", but *the panel is
larger than the lid's whole window*. Any 13-based build is a new, larger lid, not a re-bezel.
⇒ **A Framework 16 has ~1.75 mm of margin.** Positive, but thin enough that the lid **cavity depth**
— not the opening — is now the deciding number, and the panel's folded source-driver COFs thicken it
locally in a band along the tail edge.

⚠ Also note **Glider tops out at 13.3" panels**. A "16-inch e-ink laptop" is not on the table; this is
a 13.3" panel in a 16" lid, leaving ~59 mm of dead width to design around.

## ⭐ Correction: the video path is simpler than DisplayPort Alt Mode

First analysis led with Glider's USB-C DP Alt Mode chain — FUSB302B PD PHY → CBTL02043A lane mux →
PTN3460 — which only works after USB-PD negotiation. **That is not the only input.**

Glider also takes **DVI over Mini-HDMI through an ADV7611**: a plain TMDS sink, **no PD, no CC lines,
no Alt-Mode mux**. Modos's own `USAGE.md` instructs exactly this: *"use two cables: USB-C for power
and USB, plus a Mini-HDMI video cable for video."* Maximum pixel rate over DVI is **165 MP/s**, far
above what 1600×1200 needs.

⇒ **The realistic wiring is: HDMI for video + USB-C for power**, both from base to lid. That is two
ordinary cables, not a PD-negotiation problem — and it is very likely what the demonstrated build did.

## Framework's newest hardware, and the "flat-mounted RAM"

⭐ **The flat-mounted memory you were thinking of is LPCAMM2** — LPDDR5X packages that would otherwise
be soldered, moved onto a module held by a high-density compression interposer (Dell's CAMM →
JEDEC CAMM2/LPCAMM2).

⚠ **It ships on exactly one Framework, and it is not the 16.**

| Model | Announced | Memory | Notes |
|---|---|---|---|
| **Framework Laptop 13 Pro** | 2026-04-21, shipped June 2026 | ⭐ **LPCAMM2 / LPDDR5X**, 1 module, 16/32/64 GB sold (96 GB architecturally) | Intel Core Ultra Series 3; CNC 6063 aluminium; 13.5" 3:2 2880×1920 120 Hz touch; 74.45 Wh; from **$1,199** DIY |
| Framework Laptop 12 | announced 2026-08-18, ships Oct 2026 | 1× SO-DIMM | Intel Core Series 3, **$549** DIY |
| Framework Laptop 16 | 2nd gen Nov 2025; refreshed 2026-04-21 | 2× DDR5-5600 SO-DIMM, 96 GB | Ryzen AI 5 340 / 7 350 / 9 HX 370; RX 7700S or RTX 5070 8/12 GB; DIY **$1,249 / $1,499 / $1,799** |
| Framework Laptop 13 | 2025 | 2× SO-DIMM | Ryzen AI 300 |
| Framework Desktop | 2025 | soldered LPDDR5X-8000, up to 128 GB (192 GB teased) | not a laptop |

⚠ LPCAMM2 on the 13 Pro is rated LPDDR5X-8533 but runs at **6800 MT/s** (Core Ultra 5 325) or
**7467 MT/s** (X7 358H / X9 388H) — Framework says a faster mainboard PCB process would be
"wildly expensive". Framework publicly corrected an earlier 7467 claim for the Ultra 5.

⇒ **For an e-ink build none of this matters**, since the panel is driven over HDMI/USB-C and the CPU
is irrelevant to it. The 13 Pro is the newest *platform*; the 16 remains the strongest *laptop*
(discrete GPU, two NVMe). But ⛔ the 13 Pro is a **13** — its lid cannot take this panel either.

## Precedent: custom bezels are routinely printed; e-ink lids are not

* The bezel is **magnetically attached on both the 13 and the 16**, and sold separately ($39–49 for
  the 13, $49–69 for the 16).
* Multiple people have successfully 3D-printed replacement bezels — **Ingegneus** and **edna** for the
  FW13; **Mapou Trautman** for the FW16, printed in clear photopolymer by Xometry (it fits, but *bows
  at the bottom and needs added magnets*).
* ⛔ **No e-ink Framework lid design has ever been published.** The 2025 DIY Perks thread where
  someone announced intent to build one "this winter" was never followed up. Cittadhammo's build,
  demonstrated 2026-09-17, has no published files found.

## The video of the build, archived

Cittadhammo's own upload — *not* a Modos video — captured 2026-09-20 with `yt-dlp-priv.py`:

* **"Modos Framework 13"**, 2:25, uploaded 2026-09-17, by **Cittadhammo Bhikkhu**
  (`@CittadhammoBhikkhu`) — <https://www.youtube.com/watch?v=ZSxYI14JdMM>
* No subtitles are published, so no transcript exists to archive.

| profile | actual resolution | size | sha256 (first 16) |
|---|---|---|---|
| `2160p` | 2160×3840 | 83,061,634 B | `a880b1e350ff205c` |
| `1440p` | 1440×2560 | 30,168,896 B | `4fc175375c7f096f` |
| `1080p` | 1080×1920 | 9,666,028 B | `79ac6acdf29fd58e` |
| `720p` | 720×1280 | 7,322,894 B | `577c398f6465f7a8` |
| `480p` | 608×1080 | 5,162,854 B | `aeda6604aba35441` |
| `360p` | 360×640 | 3,515,854 B | `c1f64357a9c1e88b` |

⛔ **The files themselves are deliberately NOT committed**: they are someone else's copyrighted video,
this repo is public, and 133 MB of binaries does not belong in it. They are in the local media archive
under the uploader's name. Resolutions above are **`ffprobe`-verified, not inferred from filenames** —
a first attempt mislabelled them because the video is *vertical*, so a `height<=N` filter selects by
the long side and yields roughly one step down.

## Sources

Archived primary documents, with per-file licences, are in
`hw-interfaces-pub-kb/edp-displayport-laptop-panel-hacking/refs/SOURCES.md` — including Framework's
FW13/FW16 Display and Mainboard READMEs and two CC BY 4.0 PDFs, and Modos's Glider `README.md`
(~1,400 lines, an e-ink reference in its own right) and `USAGE.md`.

* Modos Hacking Guide, 2026-07-01 — <https://www.crowdsupply.com/modos-tech/modos-paper-monitor/updates>
* Glider — <https://github.com/Modos-Labs/Glider/> · host SDK — <https://github.com/Modos-Labs/glider-api>
* Caster gateware — <https://gitlab.com/zephray/Caster/>
* Framework Laptop 13 Pro LPCAMM2 deep dive — <https://frame.work/blog/framework-laptop-13-pro-deep-dive-lpcamm2>
* Framework Laptop 16 — <https://frame.work/laptop16?tab=specs>
