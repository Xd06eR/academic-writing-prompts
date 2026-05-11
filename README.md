# Academic Writing Prompts

A pipeline of five focused prompts for writing academic essays with an LLM, where **the user owns the argument** and the LLM handles structure, language, hedging, and editorial discipline. Designed so the resulting essay does not sound like generic AI output.

> Heads-up: the previous repo (V1–V3) was a single mega-prompt that mixed brainstorming, drafting, scoring, and editing into one request. It is preserved in [`archive/`](archive/) for reference. The new system splits those concerns into five small skills you compose.

## What the pipeline does

```
[Essay Context preamble]              ← define topic, audience, citation style, scope once
        │
        ▼
  1. capture-argument                  ← externalise your thesis & sub-claims; asks ≤3 clarifying Qs
        │
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

Each step's output is the input to the next. Strict handoff formats (markdown sections / tables) keep the chain reliable.

## Why the redesign

The old V3 prompt produced essays that read like the LLM had written them — even when the underlying argument was the student's. The new system isolates each concern:

- **Argument ownership** lives in `1-capture-argument`. The LLM asks for your stance and personal angles, then commits them in writing. Nothing downstream invents arguments for you.
- **Citation safety** lives in `2-lit-review`. The skill refuses to return any source without a working URL, and tells you to verify before pasting. Hallucinated citations are how students get caught.
- **Scoring is gone.** The old numeric rubric ("score 95+") asked the LLM to fake precision it does not have. `5-refine` uses a behavioural checklist with `pass / warn / fail` plus concrete defect fixes — auditable diffs instead of made-up numbers.
- **Anti-AI-tells** are explicit in `5-refine`. The checklist scans for em-dash overuse, rule-of-three, "delve / leverage / multifaceted", hollow generalities, and similar tells documented in the resources linked below.

## Quick start

1. Pick a language: [`English/`](English/) or [`Chinese/`](Chinese/).
2. Open `essay-context.md` and fill in the preamble fields for your essay (topic, stance, discipline, audience, citation style, scope, word count, requirements, background).
3. Open `1-capture-argument.md`. Paste the Essay Context at the top, paste your raw thinking under `## Raw input:`, and run it in your LLM chat.
4. Take the output, paste it into the next skill (`2-lit-review` if you need sources, otherwise `3-outline`), and continue down the pipeline.
5. Each skill has clear input/output contracts. The output of step N is what you paste at the top of step N+1.

A fully worked example for both languages is in [`examples/`](examples/).

## Files

### Pipeline prompts

| # | English | Chinese |
|---|---------|---------|
| — | [`English/essay-context.md`](English/essay-context.md) | [`Chinese/essay-context.md`](Chinese/essay-context.md) |
| 1 | [`English/1-capture-argument.md`](English/1-capture-argument.md) | [`Chinese/1-擷取論點.md`](Chinese/1-擷取論點.md) |
| 2 | [`English/2-lit-review.md`](English/2-lit-review.md) | [`Chinese/2-文獻回顧.md`](Chinese/2-文獻回顧.md) |
| 3 | [`English/3-outline.md`](English/3-outline.md) | [`Chinese/3-大綱.md`](Chinese/3-大綱.md) |
| 4 | [`English/4-draft.md`](English/4-draft.md) | [`Chinese/4-起草.md`](Chinese/4-起草.md) |
| 5 | [`English/5-refine.md`](English/5-refine.md) | [`Chinese/5-修訂.md`](Chinese/5-修訂.md) |

### Worked examples

- English — [`examples/social-media-procrastination-en/`](examples/social-media-procrastination-en/)
- Chinese — [`examples/social-media-procrastination-zh/`](examples/social-media-procrastination-zh/)

Each example folder shows the exact output of every step of the pipeline for one essay (a 250-word introduction section on short-form video and academic performance).

### Claude Code skill wrappers

If you use [Claude Code](https://claude.com/claude-code), the [`skills/`](skills/) folder contains self-contained SKILL.md wrappers (English + Chinese) that Claude Code auto-triggers based on what you ask. Each wrapper embeds the full prompt body, so installation is just dropping them into your Claude Code skills directory.

```
skills/en/<skill>/SKILL.md
skills/zh/<skill>/SKILL.md
```

#### Install (global — recommended)

Clone the repo, then symlink each skill folder into `~/.claude/skills/`:

```bash
git clone https://github.com/Xd06eR/academic-writing-prompts.git
cd academic-writing-prompts

# English skills
for s in capture-argument lit-review outline draft refine; do
  ln -s "$(pwd)/skills/en/$s" ~/.claude/skills/academic-writing-$s
done

# Chinese skills (optional — skip if you only want English)
for s in capture-argument lit-review outline draft refine; do
  ln -s "$(pwd)/skills/zh/$s" ~/.claude/skills/academic-writing-$s-zh
done
```

Restart your Claude Code session (or run `/skills reload` if your version supports it). Claude Code will now auto-trigger the right skill based on your message.

#### Install (per-project — keeps skills scoped to one essay folder)

```bash
mkdir -p .claude/skills
ln -s /path/to/academic-writing-prompts/skills/en/capture-argument .claude/skills/academic-writing-capture-argument
# repeat for the other four skills
```

#### Using the skills in Claude Code

Once installed, just describe what you want — the skills auto-trigger by description match. Example session:

```
$ cd ~/essays/social-media-paper
$ claude

> help me write a 2000-word APA-7 essay for my cognitive psych class arguing
  that TikTok harms studying. course frame is Skinner's operant conditioning.

  [Claude Code triggers academic-writing-capture-argument]
  [It asks up to 3 clarifying questions, then outputs structured Thesis,
   Sub-claims, Personal angles, Counterarguments, Evidence-needed, Open questions]

> find sources

  [Triggers academic-writing-lit-review, uses Claude Code's built-in web search]
  [Returns source-map table with URLs + counter-evidence + gaps + verify warning]

> outline it

  [Triggers academic-writing-outline → granular outline with literal topic sentences]

> draft

  [Triggers academic-writing-draft → 2000-word prose draft + author's notes]

> refine

  [Triggers academic-writing-refine → checklist + defect list + revised draft]
  [Say "refine again" to iterate]
```

For Chinese essays, ask in Chinese and the `-zh` variants take over automatically.

> **One caveat:** the user-supplied Essay Context preamble (topic, stance, citation style, scope, word counts, your background angle) is what makes each skill produce good output. When Claude Code first triggers a skill, it will ask for any Essay Context fields you haven't provided yet — answer those before the real work starts. The fields are documented in [`English/essay-context.md`](English/essay-context.md) and [`Chinese/essay-context.md`](Chinese/essay-context.md).

### Archive

The previous monolithic prompts (V1–V3 English, V1 Chinese) are preserved in [`archive/`](archive/) for reference.

## LLM requirements

- **Skill 2 (lit-review) requires web search.** Use ChatGPT with Search, Claude with web access, Perplexity, or Gemini with Google grounding. LLMs without web access will hallucinate citations — that is academic dishonesty and is increasingly detectable.
- Skills 1, 3, 4, 5 work with any current LLM.

## Citation safety (read this once)

The single biggest failure mode of LLM-assisted academic writing is fabricated citations. To prevent it:

1. Skill 2 returns every source with a URL. **Click every URL before pasting any citation into your essay.**
2. Skill 5's `Evidence-Use` checklist item audits each citation in the draft against the source map and flags any citation not present in the map.
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
├── CHANGELOG.md
├── LICENSE                                ← MIT
├── AI-Writer-Improvement-Areas.docx       ← original notes that motivated this redesign
├── English/
│   ├── essay-context.md                   ← shared preamble template
│   ├── 1-capture-argument.md
│   ├── 2-lit-review.md
│   ├── 3-outline.md
│   ├── 4-draft.md
│   └── 5-refine.md
├── Chinese/
│   ├── essay-context.md
│   ├── 1-擷取論點.md
│   ├── 2-文獻回顧.md
│   ├── 3-大綱.md
│   ├── 4-起草.md
│   └── 5-修訂.md
├── examples/
│   ├── social-media-procrastination-en/   ← 0..5 outputs for one worked essay
│   └── social-media-procrastination-zh/
├── skills/                                ← Claude Code SKILL.md wrappers
│   ├── en/{capture-argument,lit-review,outline,draft,refine}/SKILL.md
│   └── zh/{capture-argument,lit-review,outline,draft,refine}/SKILL.md
└── archive/                               ← old V1–V3 single-prompt versions
    ├── English/
    └── Chinese/
```

## License

MIT — see [`LICENSE`](LICENSE). Reuse, fork, and adapt freely. Attribution appreciated but not required.
