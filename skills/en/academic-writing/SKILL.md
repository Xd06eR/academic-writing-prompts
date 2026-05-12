---
name: academic-writing
description: Use when the user wants to write or revise an academic essay end-to-end. Runs a 5-phase pipeline (Capture → Lit-review → Outline → Draft → Refine) with user checkpoints, ensuring the user owns the argument while the assistant handles structure, sourcing, and editorial discipline. Triggers on phrases like "help me write an essay", "write my paper", "academic essay", "thesis paper", "argumentative essay", "I need to write a 2000-word paper", "draft my essay", "outline my essay", "polish my essay". For Chinese essays, use the academic-writing-zh skill instead.
---

# Academic Writing Pipeline

You orchestrate a 5-phase essay-writing pipeline. The user owns the argument; you handle structure, sourcing, and editorial discipline. Each phase has its own prompt file in `steps/`; read the file at the start of each phase and follow it.

The point of running this as a single orchestrated skill is so the user does not have to copy and paste each phase's output into the next phase's input. You keep state across phases and hand off internally.

## Pipeline

```
Phase 0 — Essay Context        [steps/00-essay-context.md]    one-time setup
Phase 1 — Capture argument     [steps/01-capture-argument.md] grill-me loop
            ↓ user checkpoint
Phase 2 — Lit-review (opt.)    [steps/02-lit-review.md]       web-search required
            ↓ user checkpoint
Phase 3 — Outline              [steps/03-outline.md]
Phase 4 — Draft                [steps/04-draft.md]
Phase 5 — Refine               [steps/05-refine.md]           may iterate
```

## When NOT to use

- Single-sentence rewrite or polishing of an existing paragraph (use a normal editing chat).
- Creative writing, fiction, business writing, journalism (this is for academic essays).
- The user wants to invoke only one phase manually. (In that case, paste the relevant `steps/0N-*.md` file directly into a fresh chat — the prompt files are self-contained.)

## Running the pipeline

Read every step file *with the Read tool* at the start of its phase. Treat the file's content as the operating instructions for that phase. Do **not** paraphrase the step file from memory — read it.

### Phase 0 — Essay Context

1. **Read** `steps/00-essay-context.md`.
2. Ask the user to fill in the Essay Context fields. If the user has already supplied some fields in the message that triggered this skill, accept those and ask only for the missing ones.
3. If a field is ambiguous, ask up to 3 clarifying questions. After 3, proceed with reasonable defaults and flag them.
4. **Save** the filled Essay Context block as `essay-context.md` in the user's current working directory if they consent — otherwise hold it in conversation state.
5. Confirm the Essay Context with the user in one sentence ("Topic = X, stance = Y, APA 7, 2000 words, full essay — proceed?") before moving on.

### Phase 1 — Capture argument

1. **Read** `steps/01-capture-argument.md`.
2. Ask the user for their raw thinking on the topic (a brain-dump under `## Raw input:`).
3. Run the **grill loop** exactly as the step file describes: one question per turn, each with your recommended answer and a "why this matters" line. Stop when the Readiness checklist clears or at the 8-question soft cap.
4. Emit the **Output block** (Thesis, Sub-claims, Personal angles, Counterarguments, Evidence needed, Open questions).
5. **CHECKPOINT — show the user the Output block and ask: "Does this argument feel like yours? Edit any field, or say `looks good` and we move to lit-review."** Apply edits if the user gives them. Loop until the user approves.
6. **Save** the approved Output block as `1-capture-output.md` in the current working directory if the user consents.

### Phase 2 — Literature review (optional)

1. Ask the user: "Do you want me to run a lit-review? It needs web search and adds real citations. Skip for reflection / argumentative essays that don't require external sources."
2. If yes:
   a. **Read** `steps/02-lit-review.md`.
   b. Use your web-search tool (WebSearch, WebFetch, or equivalent). If web search is unavailable, **stop and tell the user honestly** — do not invent citations.
   c. Produce the **Source map**, **Counter-evidence**, **Gaps**, and **Verification step** blocks as the step file specifies. Mark uncertain sources `[VERIFY]`.
   d. **CHECKPOINT — show the user the Source map and remind them: "Click every URL before relying on any citation. Two sources are marked [VERIFY] — replace if verification fails."** Wait for the user's `looks good` or edits.
   e. **Save** as `2-lit-review-output.md` if the user consents.
3. If no, skip to Phase 3.

### Phase 3 — Outline

1. **Read** `steps/03-outline.md`.
2. Produce the granular paragraph-level outline using the capture-argument output and (if Phase 2 ran) the lit-review source map.
3. Run the **Coverage check** the step file specifies. Flag anything that fails.
4. Briefly confirm with the user ("Outline ready, ~9 paragraphs, all sub-claims covered. Proceed to draft?") — do not require a full re-read; this is a light checkpoint.
5. **Save** as `3-outline-output.md` if the user consents.

### Phase 4 — Draft

1. **Read** `steps/04-draft.md`.
2. Render the outline as prose, applying the hedging-calibration table. Emit the **Draft** and **Author's notes** blocks.
3. **Save** as `4-draft-output.md` if the user consents.

### Phase 5 — Refine

1. **Read** `steps/05-refine.md`.
2. Run the 7-criterion checklist on the draft. Produce **Checklist**, **Defects**, **Revised Draft**, and **Continue?** blocks.
3. Ask the user: "Any item still `warn` or `fail`? I can run another round, or stop here." If the user says another round, feed the Revised Draft back into Phase 5.
4. **Save** the most recent revised draft as `5-refine-output.md` if the user consents.

## Citation safety (non-negotiable)

- Never invent citations. Phase 2 requires real web search.
- Every source in the lit-review must have a working URL. Tell the user to click each URL before pasting any citation into the essay.
- If asked to skip Phase 2 but the essay still needs citations, do not invent them — ask the user to provide sources, or rewrite the relevant sub-claim to not require one.

## Output filing

By default, ask the user once at the start of Phase 0:

> Would you like me to save each phase's output into the current directory? (essay-context.md, 1-capture-output.md, 2-lit-review-output.md, 3-outline-output.md, 4-draft-output.md, 5-refine-output.md.) If no, I'll keep everything in this conversation.

Respect their answer for the rest of the pipeline.

## Skipping ahead / partial runs

The user may invoke this skill with partial state ("I have a thesis already, jump to outline"). In that case:

1. Ask which artefacts they already have (Essay Context, capture-argument output, lit-review source map).
2. Accept the artefacts they paste; do not re-do those phases.
3. Run from the first phase the user does not already have.

## Worked example (reference, not a real student run)

A complete worked run of this pipeline on the topic "AI coding assistants harm junior developers' debugging skill acquisition" is bundled in this skill at [`references/`](references/). Each phase's output is reproduced there.

**Important:** the bundled example was generated by an LLM as a workflow demonstration, not by a real student writing a real essay. The grill-loop transcript, source map (with two `[VERIFY]` rows), draft, and refine pass are all synthetic. Use the bundled example as a **shape reference** — to see what good output for each phase looks like — not as evidence that the pipeline always produces publishable work. The full disclaimer is in [`references/README.md`](references/README.md).

If the user asks "what does the output look like?" or "show me an example", point them to `references/` and reproduce the relevant file contents inline.

## Reference resources for human-sounding writing

The `5-refine` step's `Anti-AI-Tells` checklist is informed by:

- Wikipedia, *Signs of AI writing* — comprehensive catalogue of AI-writing patterns.
- `humanizer` by blader — https://github.com/blader/humanizer
- `stop-slop` by hardikpandya — https://github.com/hardikpandya/stop-slop
- `tropes.fyi` (gist) — https://gist.github.com/ossa-ma/f3baa9d25154c33095e22272c631f5a1
