# Agent notes: academic-writing-prompts

AGENTS.md is a symlink to this file; edit here, never there.

What the skill files cannot say: the load-bearing decisions, and the traps that keep re-appearing.

**Capability** = one of the five standalone work files: `capture-argument`, `lit-review`, `outline`, `draft`, `refine`. Each runs alone, from any amount of prior material.

## Decisions

- This repo is the **writing base** of a two-repo setup: the product is academic prose that survives a meticulous reader. Rigorous research (multi-agent search, verification infrastructure, systematic pipelines) lives in dedicated research suites; the `lit-review` capability here stays lightweight, sized for small and medium work.
- Entry is inference-led: `SKILL.md` reads what the user brought (nothing, a topic, materials, a draft) and starts at the matching capability. Each capability runs alone on whatever the user brought; a capability that demands another capability's output breaks mid-project entry, the use case this design exists for.
- The rules live in two layers. `writing-principles.md` is the contract, loaded before any writing action; `anti-ai-tell-catalogues.md` is the detection layer, loaded before prose is generated, so writing comes out clean the first time. The exhaustive post-write audit still runs, every time.
- The post-draft AI-tell audit is a fresh-context pass: the drafting session dispatches a subagent that never saw the drafting context, because an author scanning their own prose under-detects. The dispatch is session behaviour, not shipped machinery.
- Every rule in the principles file carries a `HARD` (violation-is-defect) or `JUDGMENT` (prompt, not quota) label. The label is the contract; unlabelled rules get enforced inconsistently.

## Traps

- The catalogues file is a one-time extraction baked into the repo, not a maintained distill. Do not reintroduce provenance headers, refresh triggers, or source URLs into it; the source credits live in the README.
- Everything in `examples/` is synthetic: generated prose, unchecked citation rows. Present it only as a shape reference.
- Extend the principles library from the actual sources; rules patched in from summaries of summaries drift.
- Project-specific bindings (one citation style, official templates, frozen corpora) exist only as parameters and optional inputs; as defaults they break every user who is not that project.
- `archive/` is frozen; no live file reads from it. This repo is MIT and borrows judgment content from a CC-BY-NC suite: synthesize fresh text, keep the URL credits where they live.
