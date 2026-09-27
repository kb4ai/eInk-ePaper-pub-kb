# The Framework 13 e-ink build is published — what changed

**Researched 2026-09-28.** Supersedes the central open question in this repo's earlier documents:
*"no lid, bezel, chassis or CAD file of any kind has been published"*. ⇒ **That is no longer true.**

⚠ **Verification status is uneven and is marked per claim.** The originating summary was
LLM-generated, so nothing here inherits its authority.

## ⭐ What changed

The builder announced a **finished** Framework 13 → e-ink conversion, and states that the **3D-printed
chassis files, operating-system notes, bill of materials and reference material are on a Thingiverse
page**.

| claim | status |
|---|---|
| A Thingiverse page for this build exists at `thingiverse.com/thing:7413807` | ⚠ **Corroborated, not confirmed** — see below |
| It contains chassis files + BOM + OS info + references | ⚠ **Reported by the builder's announcement; contents not read** |
| The build runs Hyprland / Omarchy | ⚠ reported; consistent with the builder's published plugin |
| Framework's account and DHH responded positively | ⛔ **Not verified** — the source post could not be retrieved |

### ⚠ Why "corroborated, not confirmed"

⛔ **Do not treat an HTTP 200 from Thingiverse as proof a listing exists.** Measured 2026-09-28:
`thing:7413807`, `thing:999999999` (nonexistent) and `thing:1` **all return HTTP 200** with a
~25.9 KB single-page-app shell and the generic title *"Thingiverse - The community for Open
Hardware"*. The page renders client-side; the API returns **401** without a token. ⇒ A status code
here is not evidence of content.

What *does* corroborate it: an independent third-party repost (2026-09-27) of the builder's
announcement carries the same `thing:7413807` URL in its own body. That is a different source from
the one that first produced the ID. ⇒ **The reference is real; the page contents remain unread.**

## Consequences for this repo

1. ⭐ **The mechanical design is no longer the missing piece.** Earlier documents here treat "nobody
   has published a laptop-lid design" as the blocking gap and the highest-value question to ask.
   **Retire that framing.** The remaining work for a would-be builder is to *read and follow* a
   published design, not to derive one.
2. **The software half was already public** and is captured in `community-builds/` — the builder's
   MIT-licensed Omarchy plugin, with the USB HID control path, device IDs and udev rule.
3. **Nothing changes about the display-only route.** The kit remains an ordinary USB-C DP Alt Mode
   monitor needing no driver, with Mini-HDMI as an alternative video path and separate USB-C power.

## Purchasability, re-verified 2026-09-28

Live fetch of the order section, not the on-page comparison tables:

* **13" Paper Dev Kit — $699**, free US shipping, **In stock**
* **6" Paper Dev Kit — $249**
* page header: `$249 - $699`

⚠ **The comparison tables on that same page still show $599 / $199** — stale campaign prices. An
automated summary quoted $599 again on 2026-09-28, citing that page. ⇒ This is the **second** time
that table has produced a wrong price in this repo. **Read the order section, never the tables.**

## ⛔ What was NOT verified

* **The Thingiverse page contents** — chassis files, BOM, OS notes, licence. Not readable without
  rendering JS or an API token. ⇒ **Everything about what the listing contains is second-hand.**
* **Its licence**, which matters before anything from it is mirrored here.
* **The X announcement post** — not retrievable; the endorsement claims rest on it alone.
* **The ~1.4 W vs ~0.3 W power comparison** — a builder's own measurement, method unstated.
* **Whether the published chassis fits the current Dev Kit revision.**

## Sources

* Independent repost carrying the Thingiverse URL, 2026-09-27 —
  <https://www.17pw.com/thread-148762-1-1.html>
* Builder's published software (MIT) — <https://github.com/cittadhammo/omarchy-modos-eink>
* Modos Paper Dev Kit, order section fetched 2026-09-28 —
  <https://www.crowdsupply.com/modos-tech/modos-paper-monitor>
* Reported build page (⚠ unread) — <https://www.thingiverse.com/thing:7413807>
