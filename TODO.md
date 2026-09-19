# TODO — e-ink / ePaper

Open items for this repo. ⭐ Filed here so they are **visible as gaps**, not buried as clauses inside
documents that answer something else — see `uberclaude-gw:kb/research-source-traps.md`, "The general
form". Opened 2026-09-19.

## Blocking a real decision

* [ ] **Ask Modos: Glider board dimensions and mounting.** Will the driver board fit inside a laptop
      lid or lid cavity, or must it sit in an expansion bay / externally? ⇒ This is the actual
      integration constraint for any in-lid build and we do not have the number. Entry point: Modos
      Discord, <https://discord.gg/6ktE6VxSyh>.
* [ ] **Ask Modos: is a higher-density kit-drivable panel planned?** Flow's 300 PPI Carta 1300 panel
      is not available to the dev kit, so a DIY build is capped at **150 PPI**. ⭐ This is the ceiling
      on the whole project and it matters more than any laptop choice — a 300 PPI kit panel would
      change the recommendation.
* [ ] **Ask Modos: can Glider's ±15 V rail run off laptop-internal power**, or does it always need a
      separate supply?
* [ ] **Obtain the ED133UT3 datasheet.** Needed for two numbers we currently do not have: the panel's
      **exact active area** (ours is derived from geometry — nobody should cut material on it) and
      its **vendor refresh-endurance figure**, which is the only thing that would settle the
      contested lifetime question in `2026-09-18-...-Framework-13.md`.

## Worth doing, not blocking

* [ ] **Confirm the Framework 16 lid envelope against real drawings.** Our figure is computed from
      16" at 16:10 and compared on active areas only — it ignores bezel, hinge, cable routing and
      lid-cavity depth. If it survives contact with Framework's published CAD, the stronger laptop is
      also the easier mechanical target, which is a significant result.
* [ ] **Ask the community whether an FW16 lid design exists or is wanted**, given the above.
* [ ] **Verify DisplayPort Alt Mode on whichever host will drive the panel.** Vendor spec sheets
      list it on many older ThinkPads (the E595 among them), but spec-sheet presence is not a tested
      output. ⚠ Not blocking — the kit also takes DVI over micro-HDMI — but worth closing before a
      purchase depends on it.
      ⛔ Per-unit results are local-tier: record them in the `*-our-devices-local` repo, not here.
* [ ] **Is a used ThinkBook Plus Gen 4 ("Twist") worth buying** as the only e-ink laptop ever made?
      Needs: used pricing, Linux support for the twist hinge and the E Ink panel, and a judgement on
      whether its **12 Hz** panel suits terminal/text/PDF work. ⇒ It is discontinued, so this is a
      second-hand question only.
* [ ] **Framework 16 second NVMe slot** is M.2 **2230**, not 2280 — check what capacities are
      actually available in 2230 before counting on it for bulk storage.

## Deliberately not doing

* ⛔ **Do not ask Modos to "adjust the kit" for another laptop.** The kit is host-agnostic — any USB-C
  DP Alt Mode port drives it. What is laptop-specific is the lid, which is not a Modos product. See
  §5 of `2026-09-19-Framework-Configurations-For-An-eInk-Build.md`.
* ⛔ **Do not stage the CPU purchase.** Costs $20–110 for optionality on a question that is not in
  doubt; Stage 0 (kit on an existing machine) removes the real uncertainty for free.

## Repo housekeeping

* [ ] This repo sits inside the vestigial `hardware-2025-kb` wrapper. Promoting it to a top-level
      `hardware-kb/hw-eink-epaper-pub-kb/` is **with Greg, undecided** (survey item 3). ⇒ Until then,
      commit e-ink content here, never in the wrapper.
