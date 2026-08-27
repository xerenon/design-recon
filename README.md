# design-recon

**An agent skill for building interfaces that don't look like an AI made them.**

Ask any coding agent for a landing page and you get the same one: dark ground,
one neon accent, rounded cards at identical radius, a gradient glow behind the
hero, emoji standing in for icons. Ask it to "make it less generic" and you get
a different flavour of the same thing — because the model is still designing
from memory, and memory *is* the default.

This skill replaces designing-from-memory with a procedure: brief the user,
capture real sites, take one structural move from each, then verify by
measuring rather than by looking.

---

## The part most guides miss

There are **three** ways a design reads as AI-made, they need different fixes,
and picking the wrong one gets you rejected twice.

| | Looks like | Fix |
|---|---|---|
| **1. The generic AI aesthetic** | Dark + neon, uniform cards, gradient glow, emoji icons, symmetrical grid | Commit to a specific named direction and execute it precisely |
| **2. Your own house style** | Warm cream, terracotta accent, serif display — that is *Anthropic's* identity, not a neutral choice | Ask outright: does this look like the company that made me? |
| **3. Correct but flat** | Validated palette, clean type, and still lifeless — every element a flat rectangle in a tidy grid | The flourish catalogue: layering, tilt, texture, shaped edges |

**Number two is the one that will get you.** No generic-AI checklist catches it,
because it isn't generic — it's a real identity, just not the one you were
hired to build. A human spots it in a second.

---

## Install

Drop the folder into your agent's skills directory:

```bash
git clone https://github.com/xerenon/design-recon.git \
  ~/.claude/skills/design-recon
```

`~/.agents/skills/` also works and is recognised by Codex, Copilot CLI and
Gemini CLI. The skill loads itself when a design task comes up; you can also
invoke it by name.

**The bundled tool needs** [Bun](https://bun.sh) and any Chromium build (Chrome,
Chromium, Edge). It finds one automatically; `CHROME_PATH` overrides. Neither is
required to follow the method — the script just makes it faster and repeatable.

---

## The method

1. **Brief the user before looking at anything.** Forced choices, not open
   questions. "What feeling do you want?" returns "modern and clean" from
   everyone. Two answers — *what must it not look like* and *name a brand whose
   look you like* — go straight into the capture list.
2. **Capture real sites.** Six to ten: competitors, adjacent categories, and at
   least two from the target market's own culture. Look for what they have in
   common that your draft lacks.
3. **Synthesise, don't collage.** One structural move per reference, never a
   whole look. A move that can't be traced back to a line in the brief gets cut.
4. **Name the technique behind every decision.** "Warm and editorial" is a mood.
   *Clip an idiom*, *shift the register*, *stack two meanings* are decisions.
   If you can't name the operation, you picked from memory.
5. **Validate colour computationally.** A rose/green pair that looked fine
   failed colour-blind separation at ΔE 4.5 — the classic red/green trap,
   invisible until measured.
6. **Verify by rendering *and* measuring.** Screenshots alone produce false
   alarms; measurements alone miss visual collisions.

---

## The tool

Useful on its own, whether or not you use the skill:

```bash
# look at what everyone else is doing
bun capture.ts refs ./refs 1280 \
  "noom|https://www.noom.com/" "arc|https://arc.net/" "monzo|https://monzo.com/"

# audit your own page — layout report + full-page slices
bun capture.ts page http://localhost:3000/ ./out/page.png 430

# viewport-only at a scroll offset — the only honest way to see sticky elements
bun capture.ts shot http://localhost:3000/ ./out/nav.png 1280 900
```

`page` prints a report before it writes anything:

```json
{
 "viewport": 430,
 "scrollWidth": 430,
 "horizontalOverflow": false,
 "fontsLoaded": ["Anuphan", "Archivo"],
 "monoOnNonLatinText": []
}
```

That last field catches a bug you cannot see: a monospace face has no Thai,
Devanagari or CJK glyphs, so applying one to that text silently falls back to
something else and quietly breaks the type system.

Headless throughout. Nothing opens on screen, and your own browser session is
never touched.

---

## Four screenshot artefacts that look like bugs

Chasing these wastes an afternoon each. The skill lists them so you don't.

| Looks like | Actually |
|---|---|
| Font not loading | Shot taken before `document.fonts.ready` |
| Content overflowing | Wrong viewport, or decoration clipped on purpose by an `overflow:hidden` parent |
| Navbar floating mid-page | `captureBeyondViewport` + `position: sticky` |
| Whole sections blank | Scroll reveals never fired — walk the page first |

The horizontal-overflow test that means anything is
`document.documentElement.scrollWidth === innerWidth`. A bounding-box scan flags
every blurred wash and marquee track as a bug.

---

## Where this came from

One real project: a Thai-language landing page that went through **five rejected
directions** before it landed. In order: generic AI aesthetic → the model's own
house style → correct but flat → flourishes but a weak navbar → shipped.

Each rejection was a *different* failure mode. The skill is the write-up of what
separated them, plus the tooling that made the verification loop fast enough to
run after every change.

The typography rules are worked in Thai and generalise to any script that stacks
marks above and below the line.

## Limitations

- The method is documented from one project, not a controlled study.
- Some sites block headless browsers; the tool reports the failure rather than
  silently handing you a screenshot of an error page, but it can't get in.
- It does not judge whether a page converts. That is answered by traffic.

## License

MIT
