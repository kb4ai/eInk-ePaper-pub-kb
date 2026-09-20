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

* [ ] **Measure the lid cavity from Framework's published STEP files** — do not wait for a drawing.
      `FrameworkComputer/Framework-Laptop-13` carries `Framework Laptop 13 CAD.stp` (and a Pro
      variant) in its **base directory**, and the Laptop 16 repo carries system CAD too.
      ⚠ An earlier note in this repo implied Framework publishes only the eDP pinout — that came from
      reading the `Display/` subdirectory alone. The system CAD is in the base directory.
      ⇒ Open the STEP, measure the lid cavity: usable depth, bezel aperture, hinge and cable-exit
      geometry. That converts our envelope arithmetic into a real answer for both the 13 and the 16.
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

## ⭐ The build path, now that 3D printing is available

Greg confirmed 2026-09-20 that he can 3D print. ⇒ **Fabrication is no longer the blocker, and neither
is CAD data — both halves are already public.** What is missing is the design work joining them.

0. [ ] ⭐ **ASK CITTADHAMMO WHETHER THE LID DESIGN EXISTS.** He published the software half
       (`github.com/cittadhammo/omarchy-modos-eink`, MIT) but **no CAD of any kind**. His issue
       tracker is the appropriate public place to ask. ⇒ If he shares it, steps 1–3 collapse from
       "design it" to "print it", and this is by far the highest-value action on this list.
1. [ ] **Get the two CAD inputs.** Modos's 13.3" module case — **back plate, frame, buttons**, in
       **STL, STP and DWG** — from the Glider repo, and Framework's system STEP. ⭐ Modos's frame is
       the panel-mounting geometry *already solved* for exactly this panel, and STP/DWG are editable,
       not just mesh.
2. [ ] **Decide which laptop the shell targets**, because the part differs completely:
       * **Framework 13** → a custom **lid** (structural; the panel is 12.7 mm too tall for the stock
         opening). Higher risk, but it is the build that has been demonstrated.
       * **Framework 16** → a custom **bezel + panel carrier** inside a stock lid (the panel fits the
         opening with room). The bezel is magnetic, tool-free and sold separately, so this route
         looks **reversible** — refit the stock bezel and panel and the laptop is standard again.
3. [ ] **Print a fit-check part before buying anything.** The panel's outline is known; a printed
       blank at panel dimensions, offered up to a lid, answers the fit question for the cost of
       filament. ⇒ Do this before committing to a laptop model.
4. [ ] **Publish whatever comes out of it.** No laptop-lid design for this panel is public; the two
       inputs are. A published part would be the missing piece for everyone, not just for us.

## Repo housekeeping

* [ ] This repo sits inside the vestigial `hardware-2025-kb` wrapper. Promoting it to a top-level
      `hardware-kb/hw-eink-epaper-pub-kb/` is **with Greg, undecided** (survey item 3). ⇒ Until then,
      commit e-ink content here, never in the wrapper.
