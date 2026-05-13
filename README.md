# Academic Writing Prompts

A 5-phase pipeline for writing academic essays with an LLM, where **the user owns the argument** and the LLM handles structure, sourcing, hedging, and editorial discipline. Designed so the resulting essay does not sound like generic AI output.

## Features

- **Iterative grill loop** captures the user's argument before any drafting starts. One question per turn, each with a recommended answer and a "why this matters" line, until the argument can survive a sceptical reader (soft cap 8 questions).
- **Single orchestrator per language** — one skill runs all 5 phases with checkpoints after Capture and Lit-review. No copy-pasting between phases.
- **Bilingual parity.** English and Traditional Chinese pipelines, with Chinese written natively (not literal translation) and English technical terms inline where they help the LLM.
- **Citation-safe lit-review.** Every source returned with a working URL; uncertain sources flagged `[VERIFY]`; refusal to fabricate.
- **Behavioural refinement, not fake scores.** `pass / warn / fail` checklist with concrete defect fixes — auditable diffs instead of made-up numeric rubrics.
- **Anti-AI-tells built into the refine step.** Scans for em-dash overuse, rule-of-three, "delve / leverage / multifaceted", hollow generalities, and similar patterns documented in the linked resources.
- **Full worked example** for both languages in each skill's `references/` folder.

## What the pipeline does

```
[Essay Context preamble]              ← define topic, audience, citation style, scope once
        │
        ▼
  1. capture-argument                  ← grill loop: 1 Q/turn with recommended answer,
        │                                stops when argument passes the Readiness checklist
        ▼
  2. lit-review        (optional)      ← finds real, verifiable sources (requires web-search LLM)
        │
        ▼
  3. outline                            ← granular paragraph-level structure
        │
        ▼
  4. draft                              ← renders the outline as academic prose with calibrated hedging
        │
        ▼
  5. refine                             ← 7-criterion behavioural checklist + concrete defect fixes
```

## Installation

### Claude Code

```bash
git clone https://github.com/Xd06eR/academic-writing-prompts.git
cd academic-writing-prompts
mkdir -p ~/.claude/skills

# English (covers all 5 phases)
cp -r skills/en/academic-writing ~/.claude/skills/academic-writing

# Traditional Chinese (optional)
cp -r skills/zh/academic-writing ~/.claude/skills/academic-writing-zh
```

OpenCode users: swap `~/.claude/skills` for `~/.config/opencode/skills`. Restart the client after install.

### Manual use (any LLM)

Open the step files in [`skills/en/academic-writing/steps/`](skills/en/academic-writing/steps/) or [`skills/zh/academic-writing/steps/`](skills/zh/academic-writing/steps/) and paste them into your chat one phase at a time. The output of each step is the input to the next. Phase 2 (lit-review) requires an LLM with web search.

## Companion resources

The refine step's anti-AI-tells checklist is informed by these resources:

- Wikipedia, [*Signs of AI writing*](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
- [`humanizer` by blader](https://github.com/blader/humanizer)
- [`stop-slop` by hardikpandya](https://github.com/hardikpandya/stop-slop)
- [`tropes.fyi`](https://gist.github.com/ossa-ma/f3baa9d25154c33095e22272c631f5a1)

## Archive

[`archive/`](archive/) holds the original monolithic V1–V3 prompts (English and Chinese) that this pipeline replaced. Kept for reference only — not maintained. Use the `skills/` folder instead.

## License

MIT — see [`LICENSE`](LICENSE).
