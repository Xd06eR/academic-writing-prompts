# Academic Writing Prompts

A 5-phase pipeline for writing academic essays with an LLM, where **the user owns the argument** and the LLM handles structure, sourcing, hedging, and editorial discipline. Designed so the resulting essay does not sound like generic AI output.

> **What's new in this revision (2026-05-12)**
> - Phase 1 (`capture-argument`) now runs an **iterative grill loop** until the argument is solid (soft cap 8 questions), not a flat "ask 3 questions and stop". Each question carries a recommended answer and a "why this matters" line, so the user can react to a concrete proposal rather than generate one cold.
> - Chinese prompts rewritten in native Traditional Chinese rather than literal translation, with English technical terms inline where they help the LLM (e.g. `thesis`, `sub-claim`, `Essay Context`).
> - Worked example replaced with a real end-to-end run on **AI coding assistants and junior-developer debugging skill** — every phase's output is the actual output, not a stub.
> - Claude Code installation collapses 5 standalone skills into **one orchestrator skill** per language. The user no longer copy-pastes between phases; the orchestrator handles handoffs internally with light checkpoints after Capture and Lit-review.

## What the pipeline does

```
[Essay Context preamble]              ← define topic, audience, citation style, scope once
        │
        ▼
  1. capture-argument                  ← grill loop: 1 Q/turn with recommended answer,
        │                                stops when argument passes the Readiness checklist
        │                                (soft cap 8 questions)
        ▼
  2. lit-review        (optional)      ← finds real, verifiable sources (requires web-search LLM)
        │
        ▼
  3. outline                            ← granular paragraph-level structure with literal topic sentences
        │
        ▼
  4. draft                              ← renders the outline as academic prose with calibrated hedging
        │
        ▼
  5. refine                             ← 7-criterion behavioural checklist + concrete defect fixes
                                          (re-invoke for additional rounds)
```

Each phase's output is the input to the next. In Claude Code, the orchestrator skill manages the handoff for you. For manual use with any LLM, paste-and-go between the step files.

## Why the redesign (V4 history)

The old V1–V3 prompts produced essays that read like the LLM had written them, even when the underlying argument was the student's. They are preserved in [`archive/`](archive/) for reference. The current system isolates each concern:

- **Argument ownership** lives in `1-capture-argument`. The LLM grills the user one question at a time until the argument can survive a sceptical reader, then commits it in writing. Nothing downstream invents arguments for you.
- **Citation safety** lives in `2-lit-review`. The skill refuses to return any source without a working URL, and tells you to verify before pasting. Hallucinated citations are how students get caught.
- **Scoring is gone.** The old numeric rubric ("score 95+") asked the LLM to fake precision it does not have. `5-refine` uses a behavioural checklist with `pass / warn / fail` plus concrete defect fixes — auditable diffs instead of made-up numbers.
- **Anti-AI-tells are explicit** in `5-refine`. The checklist scans for em-dash overuse, rule-of-three, "delve / leverage / multifaceted", hollow generalities, and similar tells documented in the resources linked below.

## Quick start

### Option A — Claude Code (recommended)

Install the orchestrator skill and just describe what you want.

```bash
git clone https://github.com/Xd06eR/academic-writing-prompts.git
cd academic-writing-prompts

# English orchestrator (covers all 5 phases)
ln -s "$(pwd)/skills/en/academic-writing" ~/.claude/skills/academic-writing

# Chinese orchestrator (optional, if you write in Traditional Chinese)
ln -s "$(pwd)/skills/zh/academic-writing" ~/.claude/skills/academic-writing-zh
```

Restart Claude Code (or `/skills reload` if your version supports it). Then in any project:

```
$ cd ~/essays/my-paper
$ claude

> help me write a 2000-word APA-7 essay arguing that AI coding assistants
  hurt junior developers' debugging skill

  [Claude Code triggers academic-writing]
  [Phase 0: asks for any missing Essay Context fields]
  [Phase 1: runs the grill loop, one question at a time, until the
   Readiness checklist clears; emits Thesis/Sub-claims/Personal angles/
   Counterarguments/Evidence-needed/Open questions]
  [CHECKPOINT: confirms the argument with you before continuing]

> looks good

  [Phase 2: offers lit-review (optional). If yes, runs web search and
   returns source-map + counter-evidence + gaps + verification reminder.
   Marks uncertain sources [VERIFY].]
  [CHECKPOINT: reminds you to verify URLs]

> looks good

  [Phase 3: granular outline]
  [Phase 4: 2000-word prose draft + author's notes]
  [Phase 5: 7-criterion checklist + defects + revised draft]

> another refine round

  [Re-runs Phase 5 on the revised draft]
```

For Chinese essays, just ask in Chinese — the `academic-writing-zh` skill takes over.

### Option B — Manual use (any LLM)

Open the step files in [`skills/en/academic-writing/steps/`](skills/en/academic-writing/steps/) or [`skills/zh/academic-writing/steps/`](skills/zh/academic-writing/steps/) and paste them into your LLM chat one phase at a time:

1. Pick a language: [`skills/en/academic-writing/`](skills/en/academic-writing/) or [`skills/zh/academic-writing/`](skills/zh/academic-writing/).
2. Fill in `steps/00-essay-context.md` for your essay.
3. Open `steps/01-capture-argument.md`. Paste the Essay Context at the top, paste your raw thinking under `## Raw input:`, and run it.
4. Take the output, paste it into the next phase (`02-lit-review.md` if you need sources, otherwise `03-outline.md`), and continue down the pipeline.
5. Each step has clear input/output contracts. The output of step N is what you paste at the top of step N+1.

A fully worked example for both languages lives in each skill's `references/` folder.

## Files

### Pipeline prompts (the source of truth for both Claude Code and manual users)

| # | English | Chinese |
|---|---------|---------|
| — | [`skills/en/academic-writing/steps/00-essay-context.md`](skills/en/academic-writing/steps/00-essay-context.md) | [`skills/zh/academic-writing/steps/00-essay-context.md`](skills/zh/academic-writing/steps/00-essay-context.md) |
| 1 | [`skills/en/academic-writing/steps/01-capture-argument.md`](skills/en/academic-writing/steps/01-capture-argument.md) | [`skills/zh/academic-writing/steps/01-擷取論點.md`](skills/zh/academic-writing/steps/01-擷取論點.md) |
| 2 | [`skills/en/academic-writing/steps/02-lit-review.md`](skills/en/academic-writing/steps/02-lit-review.md) | [`skills/zh/academic-writing/steps/02-文獻回顧.md`](skills/zh/academic-writing/steps/02-文獻回顧.md) |
| 3 | [`skills/en/academic-writing/steps/03-outline.md`](skills/en/academic-writing/steps/03-outline.md) | [`skills/zh/academic-writing/steps/03-大綱.md`](skills/zh/academic-writing/steps/03-大綱.md) |
| 4 | [`skills/en/academic-writing/steps/04-draft.md`](skills/en/academic-writing/steps/04-draft.md) | [`skills/zh/academic-writing/steps/04-起草.md`](skills/zh/academic-writing/steps/04-起草.md) |
| 5 | [`skills/en/academic-writing/steps/05-refine.md`](skills/en/academic-writing/steps/05-refine.md) | [`skills/zh/academic-writing/steps/05-修訂.md`](skills/zh/academic-writing/steps/05-修訂.md) |

### Worked example (synthetic, for reference)

A complete pipeline output for the topic **"AI coding assistants harm junior developers' debugging skill acquisition"** (HCI / cognitive-psych frame, APA 7, 2000 words, full essay):

- English — [`skills/en/academic-writing/references/`](skills/en/academic-writing/references/)
- Chinese — [`skills/zh/academic-writing/references/`](skills/zh/academic-writing/references/)

Each folder contains the output of every phase: Essay Context, the grill-loop transcript and capture-argument output, the lit-review source map (with two `[VERIFY]` rows demonstrating the skill's honesty about uncertainty), the outline, the 2000-word draft, and the refine checklist + revised draft.

> **⚠️ Synthetic, not a real student run.** The bundled example was generated by an LLM playing both Socratic editor and student to demonstrate the workflow end-to-end. No human student wrote this essay, ran the grill loop, or verified the citations. Treat it as a **shape reference** — what good output for each phase looks like — not as evidence that the pipeline always produces publishable work. Full disclaimer in each folder's `README.md`. Will be replaced when a real student's output becomes available.

### Claude Code skill wrappers

| Language | Skill folder | What it does |
|----------|--------------|--------------|
| English | [`skills/en/academic-writing/`](skills/en/academic-writing/) | Orchestrator: runs all 5 phases with checkpoints |
| Traditional Chinese | [`skills/zh/academic-writing/`](skills/zh/academic-writing/) | Same, in Chinese |

Each orchestrator's `steps/` subfolder contains the canonical prompt files for that language; `references/` holds the worked example output.

### Archive

The previous monolithic prompts (V1–V3 English, V1 Chinese) live in [`archive/`](archive/) for reference. They are not the recommended path — the orchestrator skill or the manual-use step files are.

## LLM requirements

- **Phase 2 (lit-review) requires web search.** Use ChatGPT with Search, Claude with web access, Perplexity, or Gemini with Google grounding. The Claude Code orchestrator uses Claude's built-in web tools automatically. LLMs without web access will hallucinate citations — that is academic dishonesty and is increasingly detectable.
- Phases 1, 3, 4, 5 work with any current LLM.

## Citation safety (read this once)

The single biggest failure mode of LLM-assisted academic writing is fabricated citations. To prevent it:

1. Phase 2 returns every source with a URL. **Click every URL before pasting any citation into your essay.**
2. Phase 5's `Evidence-Use` checklist item audits each citation in the draft against the source map and flags any citation not present in the map.
3. If any source row in lit-review is marked `[VERIFY]`, the assistant could not guarantee it — do not use that source without confirming or replacing it yourself.

## Companion resources for human-sounding writing

The `5-refine` skill's anti-AI-tells checklist is informed by these resources. Read them once to internalise the patterns and write better even before the refine step:

- Wikipedia, [*Signs of AI writing*](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — comprehensive catalogue of AI-writing patterns
- [`humanizer` by blader](https://github.com/blader/humanizer)
- [`stop-slop` by hardikpandya](https://github.com/hardikpandya/stop-slop)
- [`tropes.fyi`](https://gist.github.com/ossa-ma/f3baa9d25154c33095e22272c631f5a1) (also at https://tropes.fyi/tropes-md)

## Repo layout

```
academic-writing-prompts/
├── README.md
├── LICENSE                                ← MIT
├── skills/                                ← Claude Code orchestrator skills (canonical content)
│   ├── en/academic-writing/
│   │   ├── SKILL.md                       ← runs all 5 phases with checkpoints
│   │   ├── steps/                         ← canonical English prompt files
│   │   │   ├── 00-essay-context.md
│   │   │   ├── 01-capture-argument.md
│   │   │   ├── 02-lit-review.md
│   │   │   ├── 03-outline.md
│   │   │   ├── 04-draft.md
│   │   │   └── 05-refine.md
│   │   └── references/                    ← worked example output (LLM-generated demo)
│   │       ├── README.md
│   │       └── 0..5-*.md
│   └── zh/academic-writing/
│       ├── SKILL.md                       ← runs all 5 phases with checkpoints, in Chinese
│       ├── steps/                         ← canonical Traditional Chinese prompt files
│       │   ├── 00-essay-context.md
│       │   ├── 01-擷取論點.md
│       │   ├── 02-文獻回顧.md
│       │   ├── 03-大綱.md
│       │   ├── 04-起草.md
│       │   └── 05-修訂.md
│       └── references/                    ← worked example output
│           ├── README.md
│           └── 0..5-*.md
└── archive/                               ← old V1–V3 single-prompt versions
    ├── English/
    └── Chinese/
```

## License

MIT — see [`LICENSE`](LICENSE). Reuse, fork, and adapt freely. Attribution appreciated but not required.
