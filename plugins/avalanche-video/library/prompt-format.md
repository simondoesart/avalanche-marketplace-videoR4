# Canonical Prompt Format

One standard format for every generation prompt, from the **first draft**. It reads well for a human and submits cleanly to the model — no reformatting rounds.

Two views of the same prompt:

1. **Review view** — what you show the editor. Uses `@names`. Labeled sections, numbered shots, paragraph breaks.
2. **Submit view** — identical text with each `@name` swapped for `<<<element_id>>>`. (The Higgsfield backend rewrites `<<<id>>>` back to `@element_name` internally, so the two views stay symmetric.)

Never show a prompt in any other layout. Never submit anything that wasn't shown in review view first.

---

## The template

```
GENERATION {n} of {total} — "{working title}" · covers script beats {x–y}

ELEMENTS
@name — one-line identity, then the LOCKED wardrobe/state phrasing from the
        continuity bible, verbatim. One line per element used in THIS generation.
@name — …
(Only elements allowed in these shots per the element-usage map.)

SHOT 1 — {slug} ({~s})
Action paragraph: who does what, where. Include prop state explicitly
(e.g. "dragging her rolling hard-shell suitcase"). Background characters
each described distinctly.

Camera: framing + move, one line.

SHOT 2 — {slug} ({~s})
…

LOOK
{Style descriptor — house default from brand/brand-visual-style.md §2,
or the video type's override. Verbatim, never paraphrased.}

AUDIO
{Audio rule — house default: diegetic only, no music, no score — plus any
scene-specific sound notes.}

AVOID
{Global negatives + de-creep set + style negatives + this project's extra
negatives, from library/global-negatives.md and the continuity bible.}

FORMAT
{aspect} · {duration}s · {model} ({mode/resolution}) · {n} shots · audio {on/off}
```

## Rules

- **One generation = one prompt block.** Multi-generation videos get one block per generation, numbered, each mapped to script beats.
- **Blank line between every section and every shot.** The paragraph breaks are the point — they're what makes human review possible.
- **Shots are numbered and self-contained.** A reviewer must be able to check any shot against the shotlist and continuity bible without reading the others.
- **ELEMENTS lines are copied, not paraphrased**, from the continuity bible's locked phrasing. If the phrasing needs to change, change the bible first, then regenerate the prompt.
- **LOOK / AUDIO / AVOID are pasted verbatim** from their sources. No ad-hoc trimming — that's how drift starts.
- **Duration sanity:** shots × ~2.5–3s should ≈ generation duration. Flag over-packing before review, not after.

## Review etiquette

Present the review view, then ask for line-level edits ("tighten shot 2", "wardrobe wrong in shot 3"). Apply edits to the **source artifact** (script, shotlist, or bible), regenerate the prompt from source, and show a short diff of what changed since the last version. Prompts are derived artifacts — never hand-edited in place.
