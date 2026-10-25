---
name: academic-writing
description: Use when the user wants to write, outline, revise, or polish an essay, report chapter, or paper section in English. Entry at any phase, from blank page to finished prose. Not for systematic research reviews or other large literature projects, and not for writing in languages other than English.
---

# Academic writing

The writing base: academic prose that survives a meticulous reader. This skill reads what the user brought and routes it to one of five standalone capabilities: `capture-argument`, `lit-review`, `outline`, `draft`, `refine`. Each capability runs alone on whatever arrives; the guided flow below chains them for users who bring nothing.

## Protocol (hard lines)

- Load `references/writing-principles.md` before any writing action. Every capability states its own load line; this line is the contract they inherit from.
- Load `references/anti-ai-tell-catalogues.md` before generating or revising prose.

## Intake (inference-led)

Read what the user's message carries and route:

- **Nothing but a want to write.** The guided flow below.
- **A topic, vibe, or gut position.** `capture-argument.md`.
- **A thesis, brain-dump, or settled argument.** `capture-argument.md` verifies and completes it.
- **A research question, a pile of sources, or a named corpus.** `lit-review.md`.
- **An argument plus structure to commit.** `outline.md`.
- **A committed outline.** `draft.md`.
- **Draft prose, any stage.** `refine.md`.

Ask one question only when the route is genuinely ambiguous (materials that fit two capabilities with different next actions). Otherwise start at the capability; each one re-checks its own inputs and says what is missing.

## Guided flow

For the user who brings nothing. Checkpoints mark where the user confirms before further work.

1. **Capture.** Run `capture-argument.md` to the Output block.
   **Checkpoint:** ask "Does this argument feel like yours? Edit any field, or approve and we move on." Nothing downstream starts before approval.
2. **Lit-review (optional).** Skip when the essay needs no external sources. Otherwise run `lit-review.md` on the Evidence needed list.
   **Checkpoint:** ask the user to confirm the source map, `[VERIFY]` rows named. Drafting cites only the confirmed map.
3. **Outline.** Run `outline.md` on the approved Output block and confirmed source map. The presented outline is the plan the loop renders.
4. **Interleaved draft/refine loop.** For each section in the canonical order (Introduction → Literature review → Methods → Results → Discussion → Conclusion, collapsing per genre): draft the section (`draft.md`, `section:<name>`), then refine it (`refine.md`, batch scope: the new section is the audit focus, all previous sections loaded for linkage, transitions, and drift). Deferred entries accumulate across rounds; this flow carries the log and hands it to step 5, where `refine.md`'s Whole scope resolves or escalates each one.
5. **Close the document.** Draft the abstract (`draft.md`; it skips its own refine round). Run the mandatory whole-document refine: the deferred log and the cross-section checks resolve in this pass.
6. **Fresh-context audit.** Dispatch the AI-tell audit per `refine.md`: a subagent that never saw the drafting context reads the final text against `references/anti-ai-tell-catalogues.md`. A full fresh-context review beyond the tell-audit is the user's call, made on stakes.

## Capabilities

| Capability | File | Runs on |
|---|---|---|
| Capture argument | `capture-argument.md` | nothing, a topic, a brain-dump, a settled argument |
| Lit review | `lit-review.md` | a search seed, supplied sources, a fixed corpus |
| Outline | `outline.md` | an Output block, a rough thesis, a template, a partial outline |
| Draft | `draft.md` | a committed outline, an Output block, sources in hand |
| Refine | `refine.md` | any draft, any stage (`section:<name>`, batch, whole) |

## Rule layers

`references/writing-principles.md` is the contract, loaded before any writing action. `references/anti-ai-tell-catalogues.md` is the detection layer, loaded before prose is generated or revised. Every rule in the principles file carries a `HARD` or `JUDGMENT` label; venue and document-owner rules outrank the principles file, and venue typesetting conventions outrank the catalogues.

## Out of scope

Venue submission machinery (desk-reject screening, cover letters, submission-stage retraction correspondence), bilingual writing, and numeric scoring of any kind. Large systematic research is out of scope, as `lit-review.md` states at its head.

## Examples

`examples/` holds synthetic worked examples for `capture-argument` and `refine`: generated prose and unchecked citation rows, presented as a shape reference only. Point users there when they ask what the output looks like.
