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

### 2. An inherited house style — the one you will miss

Avoiding the generic default often lands on *someone's* brand instead. Warm
cream ground, terracotta accent, serif display is Anthropic's identity, not a
neutral choice.

The same trap has a second mouth: **the examples in whatever guide you are
following, including this one.** If the page resembles the last page you built,
or the worked examples in a document you just read, you inherited a look rather
than choosing one. It will be coherent, confident, and wrong for this client.

**Ask explicitly: does this look like the company that made me, or like the last
thing I made?** Nothing in the generic-AI checklist catches either; a human
catches both instantly.

### 3. Correct but flat

Disciplined palette, validated contrast, clean type — and still reads as
generated, because every element is a flat rectangle in a tidy grid. Restraint
alone is not craft.

**Fix:** go back to the captures and find what they do that your draft does not.

## The method

### 1. Run a brief before you look at anything

Skip this and you will capture references matching *your* taste rather than the
page's, and everything downstream inherits that bias.

**Ask in forced choices, not open questions.** "What feeling do you want?"
returns "modern and clean" from everyone. Give two poles and make them pick —
use a multiple-choice prompt (`AskUserQuestion` on Claude Code), not a paragraph
of questions in chat.

| Ask | Poles | What it settles |
|---|---|---|
| Who is it for, and where are they? | *(ask open)* | the fourth capture bucket, and which script the page is set in |
| How do they arrive? | cold social traffic ↔ searched for you or was referred | how much the page must explain before it can do its job |
| Register | talks like a friend ↔ talks like an expert | type weight, colour saturation, copy voice |
| How much strange can this afford? | must feel safe and familiar ↔ must be remembered | whether to break the grid at all |
| What must it **not** look like? | *(ask open)* | the fastest constraint you will get |
| Which 2–3 sites do you lose people to? | *(ask open)* | the competitor bucket, named by the person who actually knows |
| Name something unrelated that you find beautiful — a shop, a magazine, a game, a car | *(ask open)* | the outside-category bucket, and the single largest source of difference between one project and the next |

**The open answers are the reference list.** "Not like a hospital" tells you more
in four words than a paragraph about brand values, and the last two questions
hand you two of the four capture buckets outright.

That last question is doing more work than it looks. Left to yourself you will
name the same admired sites for every brief in a category, because you are
drawing them from the same memory each time — and everyone who runs this skill
gets that same list. What a particular person finds beautiful is the one input
no two projects share.

Ask all of it in one pass. A brief delivered as separate questions gets abandoned
halfway.

**Never infer the audience from the language this conversation is happening in.**
Someone briefing you in Thai may be building for the whole internet; someone
briefing you in English may be building for Osaka. Guess, and the fourth bucket
fills with references from a culture nobody asked for and the page quietly
becomes about the wrong people. It is one open question — ask it.

If the answer is that there is no particular place — an audience that is global,
or professional, or just the person themselves — say so out loud and move those
slots to outside-the-category, the same way the competitor bucket moves when
there is nothing at stake. An invented local flavour is worse than none.

#### When there is nothing at stake

Plenty of pages have no competitors: a personal site, a portfolio, a wedding, a
club, a hobby, something someone simply wants to be beautiful. Asking that person
who they lose customers to is how a brief gets abandoned in the first minute.

Take *"there aren't any"* as a real answer, not a gap to fill — and note that it
is the **freer** case, not the poorer one. The competitor bucket exists only to
show what expectations the visitor arrives carrying. Nothing at stake means no
expectations to meet, so drop the bucket and spend its slots where the beauty
was going to come from anyway: outside the category.

Then **ask the beauty question twice more, from different corners of life.** One
answer about a magazine, one about a place, one about an object. Those three are
now most of the reference list, which is the point — a page with nothing to prove
should look like the person whose page it is, and this is the only part of the
brief that carries them.

The other questions still work as written. *"How much strange can this afford?"*
usually answers itself here.

#### The gate: is the direction actually decided?

Most briefs arrive as "build me a landing page" and stop there. Answering that
from what you already know is how every page you make comes out looking like
the last one. Two tests, both things you can check rather than feel:

1. **Can you write the capture list?** Name 8–12 specific sites the brief points
   at. If you are inventing them to fill the list, the brief is not done.
2. **Does the direction exclude something?** Say it in one sentence. *"Modern and
   clean"* forbids nothing and is therefore not a direction. *"A field guide, not
   an app"* forbids a great deal.

Both pass → go to step 2. Either fails → pass two.

#### Pass two: propose directions, do not ask more questions

Someone who could describe the design would have described it. Asking that same
person more abstract questions returns more fog. **What they cannot author, they
can judge** — so stop interviewing and put up options.

Propose **three directions**, and make them *positions*, not visual styles. A
vague client cannot choose between "brutalist" and "editorial", but can answer
whether this should feel like a tool or a companion. The look is decided in step
3 from real captures; what you need here is what the page must claim.

```
A · <short name>
    Claims      <what the page asserts about itself before a word is read>
    Rules out   <what this direction forbids>
    You'd see   <one concrete consequence, so it can be pictured>
```

Three rules for the three:

- **Far apart.** Three flavours of one idea is not a choice, it is a formality.
- **Each must forbid something.** A direction that rules nothing out decides
  nothing, and you will be back here after the first draft.
- **Rejection counts as an answer.** "Not B, definitely not B" settles more than
  a lukewarm yes, and arrives faster.
- **Build them out of their answers**, above all what they said it must not look
  like and the unrelated thing they called beautiful. Three archetypes you could
  have written before meeting this person is the same failure one level up.

**Two rounds, then commit.** If the direction is still open after pass two, pick
the one the brief's own answers point at, say in one line which you picked and
why, and start capturing. An abandoned brief costs more than an imperfect one.
Treat *"you decide"* the same way: it is permission to choose, not permission to
default — so choose out loud, and let them correct a stated choice.

### 2. Capture real sites — this step is the skill

Not a trends article, not remembered examples: the sites themselves, rendered
today. Everything downstream is assembled out of what you collect here, so a
thin capture pass produces a thin design that no amount of care later can
rescue.

**Needs:** [Bun](https://bun.sh) and any Chromium build (Chrome, Chromium, Edge).
It finds one automatically; `CHROME_PATH` overrides. It drives that browser
headlessly — nothing opens on screen and no existing browser session is touched.

```bash
bun capture.ts refs ./refs 1280 \
  "<name>|<url>" "<name>|<url>" "<name>|<url>"
```

**Capture 8–12, spread across four buckets:**

| Bucket | Something at stake | Nothing at stake | Why |
|---|---|---|---|
| Direct competitors | 2–3 | — | what this audience already compares the page to |
| Adjacent category | 2–3 | 2–3 | same job done elsewhere — showing work, telling a story, listing dates |
| **Outside the category entirely** | 2–3 | **5–6** | record labels, museums, type foundries, restaurants, hardware |
| The audience's own culture | 2+ | 2+ | what *that* audience reads as normal, which is not what you read as normal — from the place the brief named, never the language you are being briefed in |

The third bucket is what makes the result new. A page assembled only from
competitors converges on the category average by construction — every input
already agrees with every other input.

**Buckets 1 and 3 are filled from the brief, not by you.** They are exactly the
two the client was asked to name, and they are the two where your own memory
would otherwise decide the outcome: given a category you will recall the same
competitors and the same admired sites every time, so every page built this way
ends up related. If an answer was thin, ask again before filling the gap — and
if you do fill one from memory, say which, because that is the one place the
whole method leaks back into your defaults.

With nothing at stake there is no first bucket at all and the third is most of
the list, so it carries the whole difference between this page and the next one.

**You cannot skip ahead to step 3.** With no Bun or no Chromium, open the sites
yourself and work from what is on screen. If you cannot see any real site at
all, say so and stop. A design built from remembered examples is the exact
failure this skill exists to prevent, and it will come out looking like
whatever you built last.

**What to extract from each capture.** Ask these of the screenshot in front of
you and write down the answer, not your opinion of it:

| Look at | Ask |
|---|---|
| Edges | Where does one section end and the next begin — a rule, a colour change, a cut shape, nothing at all? |
| Repetition | Are repeated items identical, or does each get its own colour, angle, or size? |
| Containment | Does anything overlap, tilt, or break out of its box? |
| Surface | Is any ground textured, or is every fill flat? |
| Colour count | How many hues actually appear, counting the ones used once? |
| Imagery | Photography, illustration, the product's own output, or type alone? |
| Type | How many faces, at what weights — and what does the display face do that the body face does not? |
| Motion | What moves, and does anything respond to being pressed? |
| **The one thing** | What would you still remember about this page tomorrow? |

The last row matters most. A site worth capturing has an answer to it. If you
cannot find one, it is not a reference — it is a competitor.

### 3. Synthesise — take, transform, then check

Collecting one move per reference and stacking them up gives you the average of
the references. The brief asked for something better than any of them.

**Fill the ledger from your own captures.** One row per reference, the move
described in the words of what you saw rather than the name of a technique:

```
<the move you observed>   ← <site you captured>   → <the line in the brief it serves>
<the move you observed>   ← <site you captured>   → <the line in the brief it serves>
```

A row with no site is a memory. A row with no brief line is decoration. Both get
cut. One move per reference, never a whole look: six sites contributing one move
each reads as a point of view, two sites contributing everything reads as a copy.

**One row is not a move — it is the spine.** Palette, texture and type can all
change while the page keeps the same skeleton, and a reader will still say it
looks like everything else, because it does. Layout is the first thing they
register and the thing this method most easily leaves alone: get absorbed in
choosing hues and you will hang them on hero → three features → testimonial →
call to action without ever deciding to.

So one capture supplies the section order and the organising principle, named
and attributed like any other row:

```
spine   ← <site you captured>   organised as <what it is organised as>
```

**Take the spine from the outside-category bucket** wherever you can, because
that is where structures live that are not landing pages at all — an index, a
menu, a timetable, a catalogue, a wall label, a track listing, a scorecard, a
field guide. A page laid out as a printed index and a page laid out as a set
list do not resemble each other whatever colours they arrive at.

If the section order is hero → features → testimonial → CTA and no capture has
that shape, it came from memory.

**Two more rows carry no move either — the type and the palette.** They are the
two everyone forgets to source, and the two that give an AI-built page away
fastest: pages from the same model reach for the same handful of faces and the
same three-hue arrangement, whatever else changed. Neither is settled by taste
here. Both name a capture.

```
spine     ← <site>   organised as <what it is organised as>
type      ← <site>   display is <what kind of face, and what it does that the body face does not>
                    → <a real, available face that answers that description>
palette   ← <site>   ground is <what> · <how many hues> · <what carries the accent> · <how often it appears>
```

**Type cannot be lifted off a screenshot, only described off one.** You are not
identifying the font; you are naming what it *does* — a grotesque with tight
apertures and no contrast, a transitional serif set far larger than the grid
wants, a face whose numerals are the interesting part. Then go and find
something available that answers the description. Jumping straight to a font
name means naming one you already knew, and those are the same few every time.

**The palette row is an arrangement, not swatches.** How many hues actually
appear, which one is the ground, what the accent is spent on and how rarely —
that arrangement is most of why a page feels like a particular place. Take it
from a capture, then let step 5 rule on whether the values you chose are
legible: origin from the capture, validity from the measurement.

**Then transform.** At least one row has to go through one of these, or the page
is a tidy collage of things that already exist:

| Operation | What it does |
|---|---|
| **Transfer** | Apply a reference's move to a different element than it uses it on — its section-edge treatment becomes your card edge |
| **Combine** | Join two moves no reference joins — per-item colour variance *and* a textured ground, where each site does only one |
| **Push** | Take a single move further than any reference dares |

**Exactly one signature move.** Push one; hold everything else steady. Two
pushes read as noise; none reads as tasteful and forgettable.

**Before building, answer this: what does the finished page have that no
captured site has?** If the answer is nothing, you have assembled a mood board.

### 4. Name the operation behind every decision

"Warm and editorial" is a mood, not a decision. If you cannot say which
operation produced a choice, you took it from memory.

| Operation | What it sounds like |
|---|---|
| Transfer | "the edge treatment from X, moved onto the cards" |
| Invert | "the reference uses this for emphasis; here it carries the ground" |
| Constrain | "one accent, appearing exactly four times" |
| Exaggerate | "display type at twice the size the grid wants" |
| Borrow structure | "laid out like a printed index, not like a web page" |

The same discipline applies to naming and copy. An operation can be argued with;
a mood cannot.

### 5. Validate colour computationally, never by eye

Use the `dataviz` skill's validator for any colour carrying data. It catches
what eyes do not: a rose/green pair that looked fine failed CVD separation at
ΔE 4.5 — the classic red/green trap, invisible until measured.

Every mark needs validating **against the surface it actually sits on**. A
colour that passes on a pale ground fails on a dark one; dark blocks need their
own step off the same ramp.

This step rules on legibility, not on origin — the palette row in step 3 already
settled where the arrangement came from. A palette that cannot name its capture
is a palette from memory whatever the hue, and validating it only proves the
memory is readable.

### 6. Verify by rendering and measuring

See "Verification" below. Not optional polish — in one session it caught four
real bugs and stopped three false alarms from being "fixed".

## Imagery

**Where photography is unavailable:** do not substitute stock. Render the
product's own output as the imagery — a real conversation, a month of logged
days, a route, a receipt. It is more convincing than a stock plate, and a
competitor cannot lift it.

This is a source of imagery, not a style. What that output should *look* like
comes from the captures, like everything else.

## Non-Latin typography

Applies when the content is in a script that stacks marks. Worked in Thai;
generalises to Devanagari, Arabic, Vietnamese and the rest. **If the page is in
Latin script, skip this section — it is not a design direction.**

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
| Taking "build me a landing page" as a brief | It is a request, not a direction. Run the gate before capturing anything |
| Asking a vague client more questions | They cannot author a direction. Put up three and let them reject two |
| Capturing only competitors | Half the list should be from outside the category, or the result is the category average |
| Treating a worked example as the answer | Every example in this file is one project's output. The form is the reusable part |
| Removing all rounding to escape "AI look" | Overcorrection. Soft radii on *surfaces*, sharp rules and type |
| Three flat colours, calling it disciplined | Range comes from tonal steps and tinted grounds, not fewer hues |
| Emoji as interface icons | Draw an inline SVG, or use numerals and rules |
| One uniform reveal animation everywhere | Vary by content type; a wipe for printed blocks, a rise for lines |
| Shipping after the first screenshot looks right | Check 380 / 430 / 1280 and re-check after every copy change |

## Red flags

- You started capturing references without asking the user anything
- **You began capturing while the direction was still "modern and clean"**
- **You could not have written the capture list without inventing it**
- **You cannot name the capture the display face came from** — or you named the
  face before describing what it had to do
- **The hue count, the ground and the accent's ratio came from you rather than
  from a capture**
- **A visible decision that cannot name the capture it came from**
- Every reference is a direct competitor
- **Every site on the list was named by you rather than by the client**
- **The audience's culture was inferred from the language of this conversation
  rather than asked for**
- **The section order is hero → features → testimonial → CTA, and no capture has
  that shape**
- A reference contributed more than one move
- Nothing was transferred, combined or pushed — the page is an average
- **This page would work unchanged for an unrelated project**
- **This page resembles the last one you built, or the examples in this file**
- Every block is the same width with the same padding
- You cannot name the operation behind the headline treatment
- You have not rendered it at 380px
- You are about to say "it looks fine" without having measured `scrollWidth`

## Real-world impact

Five directions rejected before one landed, in order: generic AI aesthetic → an
inherited house style → correct but flat → flourishes but a weak navbar →
shipped. Each was a *different* failure mode. Diagnosing which one you have is
most of the work.

The second one is not hypothetical for this document either. An early version
listed the finished moves from that project — a marquee, rotated badges, a
textured ground — in a table with the sites they came from. Readers applied the
table instead of capturing anything, and unrelated products came out looking
like that one project. A menu of answers will always be cheaper than doing the
work, so the answers are gone; what is left is what to look for.
