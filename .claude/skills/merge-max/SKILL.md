---
name: merge-max
description: Merge a large, variable-sized folder of marketing tutorial transcripts (20-50+ files, combined word count up to ~150,000) into a single deduplicated, up-to-date, full-depth reference document for one topic. Use when the user points at one topic folder (e.g. a "TikTok", "Marketing", or "Ecommerce" folder full of transcripts) and wants it merged in this session, with the output saved as AI-MERGE-<TOPIC>.md (plus numbered part files if it grows too long) in the project's "output" folder. Each topic folder is handled in its own session, one at a time. Use "merge-tutorial" instead for small, informal, single-shot merges where none of this matters.
---

# Merge Max

Merge every transcript in one topic folder into a single, deduplicated,
up-to-date reference document at full explanatory depth. Built for
folders with many files (20-50+) of wildly varying length, where a naive
single-pass read would blow past useful extraction quality. Work in three
passes (extract, consolidate, audit) so no detail and no depth gets lost.

The output is a reference someone can learn and execute from without the
sources, not a digest. Every technique must carry its what, why, how and
example at the depth the best source gave it.

## Scope: one folder, one topic, one session

- Each session handles exactly one topic folder. Do not try to merge
  multiple topics in the same run.
- The topic name is the folder name (e.g. `TIKTOK`, `MARKETING`,
  `ECOMMERCE`). If the folder name doesn't clearly read as a topic, ask
  the user to confirm the topic name before proceeding.
- If the folder mixes unrelated topics, flag it and ask whether to split
  before merging, rather than silently merging everything into one file.

## PASS 1: EXTRACT (batched by size, not file count)

File count per folder varies a lot (20 files one time, 50 the next) and
individual file word counts vary just as much. Don't batch by a fixed
number of files; batch by combined word count instead:

- Group files into batches targeting roughly 20,000-30,000 words per
  batch. A batch might be 2-3 long files or 15 short ones.
- Process one batch at a time. For each file, extract passages, not
  one-liners. For each distinct technique, concept or rule, capture its
  full explanation:
  - **What** it is.
  - **Why** it works (the source's reasoning, psychology or mechanism).
  - **How** to do it (every step, in order).
  - **Example(s)** exactly as given: scripts, email copy, dialogue,
    case stories, before/after, numbers.
  - **Caveats**: when not to use it, failure cases, warnings.
- An entry is as long as the source's explanation of that technique. Keep
  the source's own phrasing wherever it carries nuance.
- Tag each entry with the topic it belongs to (e.g. "Keyword Research,"
  "Ad Targeting," "Short-Form Hooks") and the file it came from, so
  Pass 2 can go back to the source passage.
- Preserve exact numbers, frameworks, formulas, and named examples
  verbatim. Do not paraphrase them.
- Do not deduplicate or compare across files yet. Just build a complete
  running list across all batches.
- After each batch, note which files were covered so none get skipped or
  processed twice across a long session.
- Once all files in the folder are covered, confirm extraction is done
  and give a count of entries per topic before moving to Pass 2.

## PASS 2: CONSOLIDATE

Group entries by topic and merge overlapping points. When writing each
section, re-open the source passages tagged for that topic, not only the
Pass 1 entries, so nothing lost in extraction stays lost.

- For each topic, keep the clearest and most complete version of each
  point and drop true repeats. When two sources explain the same thing,
  merge them into one explanation that keeps every non-overlapping
  detail, reason and example from both.
- If two entries conflict, keep both and flag the conflict in one short
  parenthetical, e.g. "(one source recommends X, another Y, untested which
  holds in 2026)." Never silently pick a winner.

### Format per technique

Write each technique as explanatory prose, not a bullet list, under its
own heading, using this structure wherever the sources support it:

- **What it is**: 1-2 sentences.
- **Why it works**: the psychology or mechanism, in full.
- **How to do it**: numbered steps.
- **Example**: the full example, including any scripts, email or ad copy,
  or dialogue.
- **Pitfalls / when not to use it**.

Omit a sub-part only when no source covers it; never invent content to
fill it. Use bullet lists only for true lists: checklists, subject-line
or hook collections, tool lists, statistics.

### Length and depth

"Merge" and "deduplicate" pull toward summarizing. Resist that: the goal
is a complete reference, not a digest.

- No target length. Completeness beats brevity; the output is as long as
  the unique content requires. Do not aim for or stop at any word count.
- Depth floor: merge duplicates, but never shorten a unique explanation.
  After removing true repeats and non-content, each topic's section
  should be at least as long and as detailed as the fullest single
  source's treatment of that topic. If a source spends a paragraph or
  more explaining something, the output spends at least that.
- Only two things may be dropped: true repeats (keep the fullest version)
  and non-content (intros, thank-yous, banter, giveaways, sponsor
  pitches, speaker credentials).
- Keep every named example, sample ad line or script excerpt, and the
  reasoning behind a rule (the "why"), not just the rule itself.
- Write the output section by section: one write for the skeleton and
  first major section, then append each further major section in its own
  write or edit. Never try to produce the whole document in a single
  write, so each section keeps its full detail and no single response
  hits the output limit.

## PASS 3: AUDIT (source against output)

Anything Pass 1 missed or Pass 2 dropped or compressed is invisible
without going back to the sources. After the output is written, verify
it against the original transcripts:

- Number check first: collect every number from the Pass 1 list and
  confirm each one appears in the output. Restore any that were dropped
  or paraphrased (e.g. "about 232" must not become "hundreds").
- Then re-read the transcripts in the same size-based batches as Pass 1.
  For each file, compare it against the output and list:
  - every substantive point, number, framework, named example, or step
    that is missing, and
  - every point that is present but compressed: the source explains it
    in a paragraph or more (reasoning, steps, example) while the output
    gives it a line or two. Rewrite these at full depth.
- Ignore true non-content: intros, thank-yous, host banter, audience
  hand-raises, giveaways/QR codes, sponsor pitches, and speaker
  credentials (the output carries no attribution).
- Add or expand each item in the right section of the output, following
  the same rules (verbatim numbers, conflicts flagged, format per
  technique, no em-dashes).
- Report per file: the items added, the items expanded, or "nothing
  missing". Also give the final word count of each output file.

## OUTPUT

- Save as a new file named `AI-MERGE-<TOPIC>.md` (e.g.
  `AI-MERGE-MARKETING.md`), with `<TOPIC>` uppercased and spaces
  replaced by hyphens, in the `output` folder at the project root
  (e.g. `AI WHISPER/output/`). Never save it inside the source
  transcript folder. Create `output` if it does not exist.
- Splitting long output: if the document would exceed about 40,000
  words, or a single file gets too large to write or edit reliably,
  continue in additional files named `AI-MERGE-<TOPIC>-PART2.md`,
  `AI-MERGE-<TOPIC>-PART3.md`, and so on. Split only at a major section
  boundary, never mid-section. The first file keeps the plain
  `AI-MERGE-<TOPIC>.md` name and opens with a short table of contents
  listing every section and which file holds it. Never cut depth to
  stay inside one file; add a part instead.
- If a file with any of these names already exists in `output`, ask
  before overwriting it.
- Clean markdown, organized by topic and theme.
- No source attribution.
- No summary.
- No changelog.

