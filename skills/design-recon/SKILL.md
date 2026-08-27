---
name: design-recon
description: Use when building or redesigning a landing page, marketing site, or product UI, or when someone says a design looks generic, templated, corporate, flat, or "like AI made it"
---

# Design Recon

## Overview

You cannot design your way out of your own defaults from memory. Thinking harder
produces the same aesthetic, because the thing you reach for *is* the default.

**Brief the user first, look at real work second, design third — and check the
result against your own house style, not only against the generic one.**

Doing it in any other order means designing from taste, and the only taste
available is the default one.

## The three failure modes

They are different problems and they need different fixes. Diagnose before
redesigning, or you will fix the wrong one and be rejected again.

### 1. The generic AI aesthetic

Dark ground + one neon accent · every element a rounded card with identical
padding and radius · a radial gradient glow behind the hero · emoji standing in
for icons · a symmetrical three-column feature grid · Inter · the same fade-in
on every element.

**Fix:** commit to a specific, named direction and execute it precisely.

### 2. Your own house style — the one you will miss

Avoiding the generic default often lands on *your own* brand palette instead.
Warm cream ground, terracotta accent, serif display is Anthropic's identity, not
a neutral choice.

**Ask explicitly: does this look like the company that made me?** Nothing in the
generic-AI checklist catches this; a human catches it instantly.

### 3. Correct but flat

Disciplined palette, validated contrast, clean type — and still reads as
generated, because every element is a flat rectangle in a tidy grid. Restraint
alone is not craft.

**Fix:** the flourish catalogue below. Usually the last 20%.

## The method

### 1. Run a brief before you look at anything

Skip this and you will capture references matching *your* taste rather than the
product's, and everything downstream inherits that bias.

**Ask in forced choices, not open questions.** "What feeling do you want?"
returns "modern and clean" from everyone. Give two poles and make them pick —
use a multiple-choice prompt (`AskUserQuestion` on Claude Code), not a paragraph
of questions in chat.

| Ask | Poles | What it settles |
|---|---|---|
| Who arrives, and from where? | cold social traffic ↔ searched for you or was referred | how much the page must explain before it can sell |
| Register | talks like a friend ↔ talks like an expert | type weight, colour saturation, copy voice |
| How much strange can this afford? | must feel safe and familiar ↔ must be remembered | whether to break the grid at all |
| What must it **not** look like? | *(ask open)* | the fastest constraint you will get |
| Name a brand whose look you like | *(ask open)* | seeds the reference list directly |

The last two answers go straight into the capture list. "Not like a hospital"
tells you more in four words than a paragraph about brand values.

Ask all of it in one pass. A brief delivered as five separate questions gets
abandoned halfway.

### 2. Capture real sites before deciding anything

Not a trends article — the sites themselves. Use `capture.ts` in this directory.

**Needs:** [Bun](https://bun.sh) and any Chromium build (Chrome, Chromium, Edge).
It finds one automatically; `CHROME_PATH` overrides. It drives that browser
headlessly — nothing opens on screen and no existing browser session is touched.

```bash
bun capture.ts refs ./refs 1280 \
  "noom|https://www.noom.com/" "arc|https://arc.net/" "monzo|https://monzo.com/"
```

No Bun or no Chromium? The method still holds — open the sites yourself and
compare them side by side. The script only makes it faster and repeatable.

Pick 6–10: competitors, adjacent categories, and at least two from the target
market's own culture — local references show what the audience already reads as
normal.

Look for what they *have in common* that your draft lacks. A single site tells
you nothing.

### 3. Synthesise — do not collage

Take **one structural move** from each reference, never a whole look. Six sites
contributing one move each reads as a point of view; two sites contributing
everything reads as a copy.

Write the attribution down before building:

```
layering / floating chips   ← LINE MAN
section edges               ← Arc
per-card colour + tilt      ← Headspace
rotated badges              ← Monzo
surface texture             ← Oatly
```

Then check each move against the brief. **A move that cannot be traced to a line
in the brief gets cut** — that is how six references become one design instead
of a mood board.

### 4. Name the technique behind every decision

"Warm and editorial" is a mood, not a decision. Name the operation:

| Technique | Example |
|---|---|
| Clip an idiom | `เงาตามตัว` (inseparable, like a shadow) → `เงาตาม` |
| Shift the register | `จี้` (nagging, irritating) → `ตื๊อ` (persistent, endearing) |
| Two meanings stacked | `ไหว` = "can manage" · romanised `WAI` = the greeting |
| Borrowed structure | `หมอชาวบ้าน` (a long-running Thai health magazine) → category + "of the people" |

If you cannot name the operation, you picked from memory.

### 5. Validate colour computationally, never by eye

Use the `dataviz` skill's validator for any colour carrying data. It catches
what eyes do not: a rose/green pair that looked fine failed CVD separation at
ΔE 4.5 — the classic red/green trap, invisible until measured.

Every mark needs validating **against the surface it actually sits on**. A
colour that passes on cream fails on indigo; dark blocks need their own step
off the same ramp.

### 6. Verify by rendering and measuring

See "Verification" below. Not optional polish — in one session it caught four
real bugs and stopped three false alarms from being "fixed".

## The flourish catalogue

What "hand-made" actually consists of. Each of these is cheap; the absence of
all of them is what reads as generated.

| Move | Where it comes from |
|---|---|
| Elements overlap, tilt, and float outside their container | LINE MAN floats food tiles around a phone |
| Cards each get their own colour and their own rotation | Headspace |
| Circular badges rotated onto the artwork, not aligned to it | Monzo |
| Section edges cut as a zigzag instead of a straight rule | Arc |
| A marquee of real domain words | Arc |
| Faint halftone dot texture on solid blocks | Oatly |
| More than three colours | Duolingo, Headspace |
| Thick outlines with hard offset shadows, not soft blur | — |
| Buttons that visibly depress on `:active` | — |

**Where photography is unavailable:** do not substitute stock. Render the
product's own output as the imagery — a real conversation, a month of logged
days, a weight line. It is more convincing than a stock plate of food and a
competitor cannot lift it.

## Non-Latin typography

Worked in Thai; the principle generalises to any script with stacked marks.

- **A monospace face has no Thai glyphs.** Applying one to Thai text silently
  falls back and breaks the type system. Use mono only where the content is
  digits or Latin.
- **Letter-spacing pulls Thai apart from its tone marks.** Cap at ~0.03em; a
  short rule beside the label does the job tracking was reaching for.
- **Line-height tuned for Latin will collide.** Thai stacks marks above *and*
  below. Display text needs ~1.3+, and more again if an inline element with a
  border sits on one line while a tone mark reaches up from the next.

## Verification

Render it and measure it. Both halves matter — screenshots alone produce false
alarms, and measurements alone miss visual collisions.

**Measure, don't eyeball:** `document.documentElement.scrollWidth === innerWidth`
is the horizontal-overflow test. Elements extending past the viewport inside an
`overflow:hidden` parent are *fine* — a bounding-box scan flags them as bugs.

```bash
bun capture.ts page http://localhost:3000/ ./out/page.png 430   # audit + slices
bun capture.ts shot http://localhost:3000/ ./out/nav.png 1280 900  # sticky/fixed
```

**Screenshot artefacts that look like bugs:**

| Looks like | Actually |
|---|---|
| Font not loading | Screenshot taken before `document.fonts.ready` |
| Content overflowing | Wrong viewport, or intentional clipped decoration |
| Navbar floating mid-page | `captureBeyondViewport` + `position:sticky` |
| Whole sections blank | Scroll reveals never fired; walk the page first |

Check sticky and fixed elements with a **viewport-only** shot at a scroll
offset. Full-page captures cannot render them honestly.

## Common mistakes

| Mistake | Fix |
|---|---|
| Designing from trend articles | Capture the sites; articles describe, screenshots show |
| Removing all rounding to escape "AI look" | Overcorrection. Soft radii on *surfaces*, sharp rules and type |
| Three flat colours, calling it disciplined | Range comes from tonal steps and tinted grounds, not fewer hues |
| Emoji as interface icons | Draw an inline SVG, or use numerals and rules |
| One uniform reveal animation everywhere | Vary by content type; a wipe for printed blocks, a rise for lines |
| Shipping after the first screenshot looks right | Check 380 / 430 / 1280 and re-check after every copy change |

## Red flags

- You started capturing references without asking the user anything
- You picked the palette before looking at a single real site
- A reference contributed more than one move
- The accent is neon on near-black, or terracotta on cream
- Every block is the same width with the same padding
- You cannot name the operation behind the headline treatment
- You have not rendered it at 380px
- You are about to say "it looks fine" without having measured `scrollWidth`

## Real-world impact

Five directions rejected before one landed, in order: generic AI aesthetic → the
model's own house style → correct but flat → flourishes but a weak navbar →
shipped. Each was a *different* failure mode. Diagnosing which one you have is
most of the work.
