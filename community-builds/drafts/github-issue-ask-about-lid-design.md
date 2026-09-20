# DRAFT — not posted

**Target:** <https://github.com/cittadhammo/omarchy-modos-eink/issues/new>
**Title:** `Is the Framework 13 lid/enclosure design published anywhere?`
**Status:** ⛔ **draft only — do not post without Greg's say-so.** Drafted 2026-09-20.

---

Hi — thanks for publishing this. The notes in your README are the most useful thing I've found
anywhere on driving the Glider: the VID/PID, the udev rule, the six `Mode` values, and especially
being explicit that there's no mode getter and no contrast/brightness/front-light control rather than
letting people assume otherwise. The point that DisplayPort Alt Mode stays the video path while HID
is a separate control channel cleared up something I had wrong.

I'm looking at doing the same thing — a Modos 13" Dev Kit in a Framework laptop lid — and the
software side now looks well covered by your work. What I can't find anywhere is the **mechanical**
side.

**The question: is the lid/enclosure design published anywhere, in any form?** Even rough STLs, a
STEP file, a sketch, or "I modified Modos' `case/133` frame" would save a lot of re-derivation. I've
checked this repo, your other repos, and the DIY Perks thread, and haven't found it — so I'm assuming
it simply wasn't published rather than that I missed it.

If it isn't published and you'd rather it stayed that way, no problem at all — a "no" is a complete
answer and I won't ask again. If you'd be happy for it to exist publicly but haven't had time to
package it, I'm glad to do that work: clean it up, document it, and publish it under whatever licence
and attribution you want.

Two smaller things, only if you happen to know off the top of your head:

* Where does the Glider board physically live in the build — inside the lid, or in the base?
* Does it run off the laptop, or does it need its own supply for the ±15 V rail?

Either way, thanks for the plugin and for writing the README as carefully as you did.

---

## Notes for Greg before posting

* **Voice:** written as you, first person. ⚠ Your standing rule is that AI-written GitHub comments
  open with `AI Assistant:`. This is drafted by Claude but posted by you as your own question — if
  you want the rule applied literally, prepend that line; if you'd rather it read as a person asking
  a person, post as-is. Your call, flagged rather than decided.
* **Why this shape:** it leads with something specific from his README (proof it was actually read,
  which is what gets answers), asks exactly one question, gives him an easy and face-saving "no",
  and offers labour rather than asking for a favour.
* **Why GitHub and not YouTube:** the video is *unlisted* on a 10-subscriber channel. The repo is
  something he deliberately published, MIT-licensed, with zero issues so far.
* ⛔ **Do not send the same text to several channels at once.** One question, one place. If there's
  no reply in a couple of weeks, the Modos Discord is the next one, not a second ping here.
