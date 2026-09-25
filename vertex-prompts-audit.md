# Vertex AI Prompt Audit — 4 files

Same framework applied to `script-vertex-ai` (6,032 → 3,861 tokens, -36%). Four drafts written with `-DRAFT-v2` suffix in `/Users/beverlybanahene/Claude Code/Creator Scans/N8N/`.

## Summary

| File | Orig chars | New chars | Orig tokens | New tokens | Reduction | maxOut before | maxOut after |
|---|---:|---:|---:|---:|---:|---:|---:|
| `remix-vertex-ai` | 22,995 | 18,372 | ~5,748 | ~4,593 | **-20.1%** | 8,192 | 32,768 |
| `vertex-review-LIVE` | 7,922 | 6,614 | ~1,980 | ~1,653 | **-16.5%** | 8,192 | 32,768 |
| `vertex-review-organic-video` | 8,114 | 7,261 | ~2,028 | ~1,815 | **-10.5%** | 4,096 | 32,768 |
| `vertex-review-shop-video` | 7,575 | 6,801 | ~1,893 | ~1,700 | **-10.2%** | 4,096 | 32,768 |

Total saved across all four: ~7,560 chars (~1,890 tokens) per call. Every taxonomy, scoring category, tone example, and quality directive preserved verbatim — cuts are pure de-duplication and structural reorder.

---

## 1. `remix-vertex-ai`

### Scorecard (before)

| Category | Score | Notes |
|---|---:|---|
| Clarity | 4/10 | Hook frame rules + audio-vs-text + schema field descriptions all describe the same fields in different places. Model has to assemble field meaning from 4 separate sections. |
| Repetition | 3/10 | caption defined 3x (lines 154, 162, 231). voiceover_tag rules in 4 places. "Use exactly as written" stated 5+ times. CRITICAL REQUIREMENTS restates everything. |
| Efficiency | 4/10 | ~20% redundant restatement. Visual action reference duplicates the visual action list. |
| Order/Structure | 6/10 | Logical block sequencing but schema is buried after 5 redundant rule blocks. |
| Schema clarity | 7/10 | Field placeholders OK but hook-vs-other-frame logic split across rules section + schema. |

### Top redundancies cut

1. **Triple-redundant field rules**: `HOOK FRAME RULES` (10 lines) + `For every subsequent frame` (8 lines) + `AUDIO VS TEXT — CRITICAL DISTINCTION` (10 lines) all explained the same 7 fields. Folded into the schema field descriptions inline (e.g. `voiceover_tag: "FRAME 1 (Hook): exactly one VOICEOVER TAG... OTHER FRAMES: ..."`).
2. **Duplicate VISUAL ACTION TYPES**: The bare tag list (line 132) was immediately followed by a "Visual action reference" block (lines 134-149) re-explaining each tag. Merged into one annotated list.
3. **CRITICAL REQUIREMENTS bullet stack** (lines 274-293): 19 bullets restating caption rules, taxonomy enforcement, hook frame structure, square-bracket prohibition, and field-presence rules already stated above. Collapsed to 8 hard constraints covering only what the schema doesn't already say.

Also cut: `TWO-STEP PROCESS` (verbose intro) → 2-bullet `APPROACH`. Cut `CAPTION RULES` standalone block and `AUDIO VS TEXT` block, since their content lives in KEY DEFINITIONS + CAPTION PLACEMENT.

### Structural reorder

Original: role → process → data → angle → format → hooks → sequence → CAPTION RULES → AUDIO MODE → SCRIPT RULES → LANGUAGE → TAXONOMIES → HOOK FRAME RULES → AUDIO VS TEXT → SCHEMA → CRITICAL REQUIREMENTS.

New: role → approach → data → **KEY DEFINITIONS** (script/caption/voiceover up front) → angle → format → hooks → sequence → CAPTION PLACEMENT → AUDIO MODE → SCRIPT RULES → LANGUAGE → TAXONOMIES → SCHEMA → HARD CONSTRAINTS. Matches cognitive task flow: understand the vocabulary, then the strategy, then the taxonomies, then the output shape.

### Preserved verbatim

- All 20 SECTIONS with sub-types
- All 31 SHOT TYPES
- SHOT TYPE SELECTION BY FORMAT (9 format groupings)
- All 27 VOICEOVER TAGS
- All 16 CAPTION HOOK TYPES
- All 16 VISUAL ACTION TYPES with descriptions
- All 25 FORMATS + Proof of Retail definition
- Stage-specific HOOK SELECTION + SECTION SEQUENCE
- All template variables (`{{ $json.* }}`)
- PAIN VS DESIRE decision logic
- Voice matching rules (Bio / Tagline / My Goal / Looking For)
- LANGUAGE REGISTER hook
- Caption complement-not-duplicate rule
- Square-bracket prohibition (in HARD CONSTRAINTS)

---

## 2. `vertex-review-LIVE`

### Scorecard (before)

| Category | Score | Notes |
|---|---:|---|
| Clarity | 7/10 | Coaching expectations split across COACH VOICE + COACHING TONE + per-field schema preamble. |
| Repetition | 5/10 | "Write directly to the creator using you/your" appears 8x in schema field comments after being stated in COACH VOICE. CRITICAL REQUIREMENTS restates "no em dashes", "no 'not observed'", "null/empty rules". |
| Efficiency | 7/10 | ~15% redundant. The prompt is mostly unique content. |
| Order/Structure | 7/10 | Sensible flow; coach voice could come earlier since it conditions every other field. |
| Schema clarity | 7/10 | Per-field "Write directly..." preamble is noise; the category name + focus is what matters. |

### Top redundancies cut

1. **Merged COACH VOICE + COACHING TONE** into one block. Both restated "use you/your", "celebrate they showed up", "be specific not generic", "reference what you saw", "never use em dashes". Now stated once with examples right below.
2. **Per-field preamble cleanup**: removed the repeated "Write directly to the creator using you/your. Tell them..." opener on each `score_N_comment` field — that's the COACH VOICE block's job. Each field now lists only what's specific to that category.
3. **CRITICAL REQUIREMENTS collapse**: dropped restated rules (return JSON, no em dashes, null/empty, no "not observed"). Kept only the schema-mechanical ones: shoppable-only-score_7 omit/include rule and overall_score average rule.

### Structural reorder

Moved COACH VOICE block ABOVE scoring categories (was below). Reader applies the voice while reading the scoring criteria, not after.

### Preserved verbatim

- All 7 scoring categories with their full evaluative questions
- All 5 right-tone examples
- All 4 wrong-tone examples
- All template variables (`{{ $('Get submission')... }}`)
- "Shoppable-only score_7" rule
- "Null score → empty string comment" rule
- overall_score-as-average rule
- "Coach not QA inspector" frame
- Level + lives-per-week personalisation directive

---

## 3. `vertex-review-organic-video`

### Scorecard (before)

| Category | Score | Notes |
|---|---:|---|
| Clarity | 7/10 | Same split as LIVE: voice rules in 2 blocks, restated in field comments. |
| Repetition | 6/10 | Same "Write directly..." per-field repetition. Slightly less critical-requirements redundancy than LIVE. |
| Efficiency | 8/10 | Already tight. Most content is unique (verification, metrics interpretation, 5 scoring categories). |
| Order/Structure | 7/10 | Logical; same coach-voice-too-late issue. |
| Schema clarity | 7/10 | Same per-field noise. |

### Top redundancies cut

1. **Merged COACH VOICE + COACHING TONE** into one block (same pattern as LIVE).
2. **Per-field "Write directly..." preamble** removed from each score comment field.
3. **CRITICAL REQUIREMENTS slimmed**: kept only the average-score + ONE-focus + reference-metrics rules; dropped the duplicate "no em dashes" / JSON-only / saves-and-shares-for-organic restatements (already in the voice block + metrics interpretation).

### Structural reorder

Same as LIVE: COACH VOICE moved above scoring. METRICS INTERPRETATION block stays between voice and scoring — it's a reference table the voice block points to.

### Preserved verbatim

- All 4 VERIFICATION questions
- All 5 scoring categories with evaluative questions
- All 6 metric interpretation lines
- All right-tone / wrong-tone examples
- All TikTok API template variables
- "Saves and shares prioritised for organic" directive
- "ONE focus, not five" directive
- Rejection reason enum
- Submission quality enum

---

## 4. `vertex-review-shop-video`

### Scorecard (before)

| Category | Score | Notes |
|---|---:|---|
| Clarity | 7/10 | Same patterns as organic. |
| Repetition | 6/10 | Same as organic. |
| Efficiency | 8/10 | Already tight. |
| Order/Structure | 7/10 | Same coach-voice-too-late. |
| Schema clarity | 7/10 | Same per-field noise. |

### Top redundancies cut

1. **Merged COACH VOICE + COACHING TONE** (same pattern).
2. **Per-field preamble cleanup** (same pattern).
3. **CRITICAL REQUIREMENTS slimmed**: kept only product-naming + average-score + ONE-focus + reference-metrics. Dropped duplicate JSON-only / em-dash restatements.

### Structural reorder

Same as organic: COACH VOICE moved above scoring; METRICS INTERPRETATION between voice and scoring.

### Preserved verbatim

- All 5 VERIFICATION questions (incl. specific product naming)
- All 5 scoring categories with evaluative questions (Hook & Attention, Product Showcase, Sales Approach, Purchase Pathway, Technical Execution)
- All 5 shop-specific metric interpretation lines
- All right-tone / wrong-tone examples
- All TikTok API template variables
- "Yellow basket / product page / link in bio" specificity examples
- Rejection reason enum
- Submission quality enum

---

## Why the review prompts cut less than remix

The three review prompts (10-16% reductions) are genuinely tighter than the remix prompt (20% reduction). They have:
- A single 5-7 category scoring rubric (vs remix's 6+ taxonomies)
- A single output schema (vs remix's nested script + storyboard)
- No format/section/hook selection trees
- No per-frame conditional logic (hook frame vs other frames)

Most of the reducible bloat across all three reviews was the same pattern: COACH VOICE + COACHING TONE were two blocks saying the same thing, and the "Write directly to the creator using you/your" preamble appeared in COACH VOICE AND on every score_N_comment field AND in the CRITICAL REQUIREMENTS list. One statement is enough.

The reference example (`script-vertex-ai`, -36%) had significantly more cut surface because it had the same trio of redundant blocks (HOOK FRAME RULES + AUDIO VS TEXT + CRITICAL REQUIREMENTS) as remix, plus a top-level full_script-format-stage section that needed restructuring.

---

## How to swap drafts into live

Same pattern as `script-vertex-ai`:

1. **Review the drafts side by side**: open the original and the `-DRAFT-v2` in two tabs. Compare the prompt text in `contents[0].parts[0].text`.
2. **In n8n, find the HTTP Request / Vertex AI node** that posts the JSON body for each workflow:
   - `remix-vertex-ai` → remix script generation workflow
   - `vertex-review-LIVE` → live review workflow
   - `vertex-review-organic-video` → organic post review workflow
   - `vertex-review-shop-video` → shop post review workflow
3. **Replace the JSON body** with the contents of the corresponding `-DRAFT-v2` file. The `fileData.fileUri` template strings are preserved exactly — no other node config needs to change.
4. **Verify `generationConfig`**:
   - `maxOutputTokens` is now 32,768 on all four (was 8,192 / 4,096). Caps, not targets — pure ceiling raise so longer outputs don't get truncated mid-JSON.
   - `temperature` preserved per file (remix 0.7, LIVE 0.3, organic/shop 0.2).
   - `responseMimeType: "application/json"` preserved.
5. **Smoke test each one with a known input** and diff the output JSON shape against a baseline run from the original prompt. The schemas haven't changed — output shape should be identical.
6. **If happy, rename**: `mv vertex-review-LIVE vertex-review-LIVE-OLD && mv vertex-review-LIVE-DRAFT-v2 vertex-review-LIVE` (repeat per file). Keep the `-OLD` files for one or two prod cycles before deleting.
