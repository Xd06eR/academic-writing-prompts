# Changelog

## 2026-05-11 — Pipeline redesign

Complete rewrite of the prompt system. Previous monolithic prompts (V1–V3 English, V1 Chinese) moved to [`archive/`](archive/).

### What changed

- **Single mega-prompt → five composable skills.** The old V3 mixed persona, drafting, scoring, iteration, and writing guidelines into one request. The new system splits these into discrete steps you can compose, skip, or re-run independently.
- **User owns the argument.** New `1-capture-argument` skill extracts thesis + sub-claims + personal angles from the user *before* drafting, with up to 3 clarifying questions if the input is too thin. Downstream skills never invent a stance.
- **Citation safety becomes a first-class concern.** New `2-lit-review` skill requires a web-search-enabled LLM, returns every source with a working URL, marks unverifiable sources `[VERIFY]`, and tells the user to click every URL before relying on it. Hallucinated citations are an explicit fail mode of LLM-assisted writing the old system did not address.
- **Numeric scoring removed.** The old "score 95+ out of 100" rubric asked the LLM to fake precision it does not have. Replaced with a 7-criterion behavioural checklist (Clarity, Structure, Argument-Strength, Evidence-Use, Academic-Voice, Hedging-Calibration, Anti-AI-Tells) producing `pass / warn / fail` and concrete defect fixes.
- **Anti-AI-tells made explicit.** `5-refine` checks for em-dash overuse, rule-of-three, "delve / leverage / multifaceted / navigate the complexities of / it is important to note", hollow generalities, inflated symbolism, and similar tells documented in the resources linked in the README.
- **Hedging calibration table.** `4-draft` includes a table matching verb register to evidence strength ("proves" for math only; "suggests" for converging studies; "may" for untested mechanisms). Stops the most common undergrad overclaiming pattern.
- **Section-aware scope.** The Essay Context preamble accepts `scope: full` or `scope: section:<name>`, so the same skills produce either a whole essay or a single section with adjacent-section fit notes.
- **Claude Code skill wrappers.** New `skills/` folder with thin SKILL.md wrappers (English + Chinese) for users who want to install the pipeline as Claude Code plugin skills.
- **Worked examples.** New `examples/social-media-procrastination-{en,zh}/` folders show the exact output of every step of the pipeline for one essay (a 250-word introduction).
- **Bilingual parity.** Every skill, example, and SKILL.md exists in both English and Traditional Chinese.

### File renames / moves

- `English/Essay Writer V1.md` → `archive/English/Essay Writer V1.md`
- `English/Essay Writer V2.md` → `archive/English/Essay Writer V2.md`
- `English/Essay Writer V3.md` → `archive/English/Essay Writer V3.md`
- `Chinese/Essay Writer V1.md` → `archive/Chinese/Essay Writer V1.md`

### New top-level structure

```
English/   essay-context.md  1-capture-argument.md  2-lit-review.md  3-outline.md  4-draft.md  5-refine.md
Chinese/   essay-context.md  1-擷取論點.md  2-文獻回顧.md  3-大綱.md  4-起草.md  5-修訂.md
examples/  social-media-procrastination-en/  social-media-procrastination-zh/
skills/    en/<skill>/SKILL.md  zh/<skill>/SKILL.md
archive/   (old V1–V3 prompts)
```

### Why a redesign rather than V4

V4 would imply the new system is the next iteration of V3. It is not: it is a different shape (five composable skills vs. one fat prompt). Calling it V4 would muddle the upgrade path. Versioning has been retired; future changes are tracked in this changelog.
