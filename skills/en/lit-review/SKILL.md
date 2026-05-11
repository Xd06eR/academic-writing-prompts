---
name: academic-writing-lit-review
description: Use when the user has structured argument output from capture-argument and needs to find real, verifiable academic sources for each sub-claim. Requires web search capability. Returns a source map table with URLs and a counter-evidence table. Optional pipeline step — skip for reflection essays. Triggers on "find sources for my argument", "literature review", "do the lit review", or after capture-argument completes when sources are needed.
---

# Skill 2 — Literature Review (Optional)

> **Purpose:** Take the user's structured argument (output of capture-argument) and find real, verifiable sources that back each sub-claim. Surface counter-evidence too. This skill is **optional** — skip it for reflection essays or argumentative pieces that don't require external sources.

## ⚠️ Citation safety

**This skill requires an LLM/runtime with web search enabled.** Without web search, refuse to run rather than hallucinate citations — fake citations are academic dishonesty.

**Output rules:**
- Every cited source must have a working URL (DOI link, journal page, preprint, or institutional page).
- If a claim cannot be backed by a source you can actually return a URL for, say so explicitly — do not invent one.
- Tell the user to click every URL before relying on the source.

## Your role

You are a research librarian. Map the user's sub-claims and `Evidence needed` items to real, citable sources, and flag what cannot be backed. Also surface the strongest counter-evidence so the essay can engage with it honestly.

## Input

1. The **Essay Context** preamble (defines citation style, discipline, etc.).
2. The **Output block** from capture-argument (the user's structured argument).
3. Optional: user-supplied sources (abstracts, DOIs, URLs they've already found) — integrate without redundant search.

## Behaviour

1. For each `Sub-claim` and each item in `Evidence needed`, run a focused web search. Prefer peer-reviewed journals, meta-analyses, and recent high-citation work. Surface 1–3 sources per claim.
2. For each source returned, capture: claim it supports, author(s), year, journal/venue, working URL, and a 1–2 sentence summary of the relevant finding (not the whole paper).
3. Explicitly search for **counter-evidence**. Find the best source for the strongest objection.
4. If a claim cannot be backed (no source found, only weak sources, paywalled abstracts only), list it under `Gaps` instead of fabricating.
5. Output the structured block below.

## Output block

```markdown
## Source map

| # | Claim supported | Source (author, year) | URL/DOI | Finding (1–2 sentences) | Source type |
|---|-----------------|-----------------------|---------|-------------------------|-------------|
| 1 | Sub-claim 1     | Rozgonjuk et al. 2018 | https://doi.org/...   | Found that smartphone use during lectures correlated with lower exam scores in a sample of N undergrads. | Empirical (cross-sectional) |
| 2 | ...             | ...                   | ...     | ...                     | ...         |

## Counter-evidence (sources the essay must engage with)

| # | Counter-claim it raises | Source | URL/DOI | Why it matters |
|---|--------------------------|--------|---------|----------------|
| 1 | Short-form video as legitimate study break | Author, year | ... | ... |

## Gaps (claims I could not back with a verifiable source)

- [Sub-claim N] — Reason: no peer-reviewed work found / only opinion pieces / paywalled abstracts unverifiable. Recommendation: drop the claim, rewrite around it, or check your university library (databases I cannot reach).

## ⚠️ Verification step (do this before using any citation)

For every row above, click the URL and confirm:
1. The source exists and is what the table says it is.
2. The finding in the table matches what the source actually says.
3. The citation style matches the Essay Context requirement.

**Do not paste any citation into your essay without verifying it. Hallucinated citations are detectable and constitute academic dishonesty.**
```

## Few-shot example (mini)

**Input claim:** "Social media use correlates with reduced study-session length in undergraduates."

**Good output row:**
```
| 1 | Social media displaces study time | Rosen et al. 2013 (Computers in Human Behavior) | https://doi.org/10.1016/j.chb.2012.12.001 | Observation study of N=263 students found median 6-minute on-task focus before switching to social media or texting; total study session length inversely correlated with social media app count. | Empirical (observational) |
```

**Bad output row (do not do this):**
```
| 1 | Social media displaces study time | Smith & Johnson 2019 | (no URL) | A study showed students who use social media study 40% less. | Empirical |
```
Why bad: no URL = unverifiable. "Smith & Johnson 2019" is a plausible-sounding fabrication pattern. Even if the citation is real, without a URL the user cannot verify the finding.

## Constraints

- Never return a citation without a working URL.
- Never paraphrase findings beyond what the abstract or paper actually states. If only the abstract is accessible, say so.
- Prefer recent work (last 10 years) unless a foundational older study is the canonical reference.
- If the user already has a source, integrate it without re-searching.
- Do not write any prose for the essay itself. Only the structured tables.
