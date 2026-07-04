# Continuity Bible — {{TITLE}}

_Companion to `briefs/{{slug}}.md` · Created in Phase 4, BEFORE any shotlist or prompt._

> This file is the continuity contract. Every shot prompt is linted against it before generation. If something here changes mid-project, re-lint every unsubmitted prompt.

---

## 1. @Element registry

Naming convention: lowercase, hyphenated, unique, human-readable (`@woman`, `@kiosk-scanner`, `@london-taxi`). The @name **must equal the Higgsfield element name** — the backend rewrites `<<<element_id>>>` to `@element_name`, so matching names keep review and submit views identical. One @name = one element_id, forever. Re-uploading creates a NEW id — never silently swap; update this table deliberately.

| @name | Type | element_id | Source image | Status |
|-------|------|-----------|--------------|--------|
| @{{name}} | character / prop / environment | `{{uuid}}` | {{uploaded / generated / existing}} | confirmed |

## 2. Characters — locked descriptions

One block per character. The **Locked phrasing** line is copied verbatim into every prompt's ELEMENTS section — never paraphrased.

### @{{name}}
- **Identity:** {{age range, build, hair, distinguishing features}}
- **Locked wardrobe phrasing:** "{{exact wardrobe sentence — e.g. 'camel tailored coat over a simple black top, dark trousers'}}"
- **Wardrobe changes:** {{none / "changes to X at beat N" — list every change explicitly}}
- **Carries:** {{props attached to this character and HOW — 'drags a rolling hard-shell suitcase', not 'has a bag'}}

## 3. Props — state over time

Track every prop that persists across shots. The classic failure is luggage: carried → checked → gone → back. Make state transitions explicit.

| @prop | Beats 1–{{n}} | State / who has it | Transition |
|-------|---------------|--------------------|------------|
| @{{name}} | {{1–3}} | {{"dragged by @woman"}} | {{"checked at counter, beat 4 — ABSENT after"}} |

## 4. Locations & geography

| @location | What it is | Appears in beats | Staging notes |
|-----------|-----------|------------------|---------------|
| @{{name}} | {{one line}} | {{n–n}} | {{light, time of day, crowd level}} |

## 5. Element-usage map (hard constraint)

Each element may appear ONLY in its allowed shots. The lint pass rejects any prompt that places an element outside its map.

| @element | Allowed in shots | Never in |
|----------|------------------|----------|
| @{{name}} | {{e.g. "kiosk shots only (S9–S10)"}} | {{e.g. "security, boarding"}} |

## 6. Background & crowd direction

Vague crowds render as clones. For every shot with background people, list 2–4 distinct one-line descriptions here and reuse them.

- Shot {{n}}: {{"an older man in a grey raincoat reading a folded paper; a student with a green backpack; …"}}

## 7. Extra negatives (project slot — feeds Tier 4 of `library/global-negatives.md`)

- {{e.g. "no wedding dresses in street scenes"}}

## 8. Continuity lint checklist (run on EVERY prompt before review)

- [ ] Every @name in the prompt exists in §1 with a confirmed element_id
- [ ] Wardrobe phrasing matches §2 verbatim (no paraphrase, no drift)
- [ ] Prop states match the §3 timeline for these beats (nothing vanishes or teleports)
- [ ] Every element is inside its §5 usage map
- [ ] Background characters use §6 distinct descriptions (no vague crowds)
- [ ] §7 extras are present in the AVOID section
- [ ] Geography/staging consistent with §4 (time of day, weather, direction of travel)
- [ ] Heavy shots flagged: 4+ element refs in one shot = higher drift risk — call it out in review
