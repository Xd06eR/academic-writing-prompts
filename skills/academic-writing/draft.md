# Draft

Render committed structure into prose. This is the capability that produces academic prose; every load-bearing decision was made upstream, and the draft executes. Do not invent new arguments, sources, or counterarguments here.

Load both rule files before generating any prose, every run:

1. `references/writing-principles.md`, the contract: claim strength, hedging ladder, register, tense, terminology, citation mechanics, paragraph shape.
2. `references/anti-ai-tell-catalogues.md`, the detection layer: prose comes out clean the first time. Do not rely on refine to catch what the catalogues forbid at the point of writing.

## Inputs (run on whatever arrives)

- **Full outline** (committed topic sentences, word allocation, evidence assignments). Render it paragraph by paragraph. This is the default input.
- **Capture Output block only** (no outline yet). Derive the minimum structure and state it in one line before drafting: thesis to the Introduction, one body section per sub-claim, counterarguments to a dedicated engagement section, Conclusion last. Then do not re-decide it.
- **Partial outline.** Draft the committed sections; list the uncommitted ones under Author's notes as gaps.
- **`section:<name>`.** Draft that section only, against its committed topic sentence. If no topic sentence is committed for it, ask one question; do not improvise the section's spine.
- **Sources in hand:** a source map from lit-review, user-supplied sources, or a fixed project corpus. Citations render only from what is in hand.

## The rendering contract

- Topic sentences render verbatim or with minor cleanup only. The outline committed them as literal sentences; the draft is not a second outline pass.
- Do not re-decide structure: no reordering sections, no merging or splitting paragraphs, no changing the thesis or the sub-claim set, no promoting a personal angle into a claim or vice versa.
- A discrepancy (an assigned source missing from the map, a topic sentence that cannot be written as committed) gets flagged under Author's notes, not silently fixed.
- The outline's transition-out lines render as the committed links between paragraphs; where none is committed, end on the paragraph's own finding.

## Paragraph loop

Work paragraph by paragraph, in the outline's order:

1. **Topic sentence.** As committed.
2. **Evidence, attached at claim creation.** Every claim sentence is born with its support attached: the citation rendered in the chosen style from the source row's data, used exactly, never with invented fields. Evidence is never retrofitted after the paragraph is written. If the support for a committed claim is not in hand, the claim still ships with an explicit placeholder stating exactly what is pending ("[needs citation: longitudinal study on X]"), and the gap lands in Author's notes.
3. **Development.** Analysis, not restatement: interpret the evidence, connect it to the sub-claim, honour the paragraph's committed function. Apply per sentence: the hedging ladder (one study found / suggests / indicates, per the principles file), register and tense per discipline, active voice by default.
4. **Voice.** Active voice names the actor and is the default. Passive is correct where the action matters more than the actor, or where the discipline's convention dictates it (methods sections in empirical sciences are the common case). The choice is per-sentence, made once, not a global habit.
5. **Close.** The committed transition out, or a sentence that states the paragraph's finding and hands off.
6. **Word check.** Actual against the paragraph's allocation (see Word tracking).

First person appears only where the outline commits a personal angle and the discipline's register allows it (see the principles file, Register). The personal angles from capture are the essay's anti-generic load; do not sand them down into detached prose, and do not leak first person elsewhere.

## Document order and the abstract

Draft whole documents in this order: Introduction, Literature review, Methods, Results, Discussion, Conclusion. The Introduction fixes the promise every later section answers; each section is written with the ones before it already on the page. The abstract is written last, from the finished body: it summarizes what exists, it does not announce what is planned (see the principles file, Abstract). Genres without Methods/Results collapse the order accordingly; the invariant ends are Introduction first, abstract last. A `section:<name>` run skips the order and drafts its section against the surrounding context.

In the guided flow the document is built section by section: one section per invocation, in the canonical order, each run emitting that section plus its notes, the whole assembling in order; the abstract and front matter run last, after the final body section. Each drafted body section goes to refine immediately, while the prior sections are fresh context; the abstract skips its own refine round and lands in the whole-document pass (see `refine.md`).

## Word tracking

- Tolerances: ±15% per section against its allocation, ±10% overall against the target. Paragraphs stay inside their committed allocations.
- The target and the per-section allocation come from the outline. With no outline, take the user's or venue's target; if none is given, state your assumed target in Author's notes.
- Over budget: cut redundancy first (adjective stacks, meta-commentary, restated claims), never content (see the principles file, Structure). Under budget: add supported analysis, cite deeper from sources already in hand, or develop the strongest example. Never pad: no throat-clearing, no repeated framing, no filler transitions.
- A section that cannot reach its allocation without padding is under-supported; say so in Author's notes rather than inflating it.

## Pre-handoff sweep

One mechanical pass over everything emitted this run before it ships to refine:

- One spelling variant throughout (-ize/-ise, -or/-our), per the principles file.
- Pronouns: every "this", "it", "they" has one unambiguous antecedent.
- Scaffolding: no leftover placeholder markers beyond the declared citation gaps, no draft annotations, every abbreviation expanded at first use.
- Catalogues quick checks (§10 of the catalogues file): run the full list there; it is the operative pre-delivery scan.
- Citation hygiene: zero orphans in both directions (every in-text citation resolves to an entry; every entry is cited), per the principles file.

This sweep is mechanical. The full AI-tell audit runs later, in refine, as a fresh-context pass; the draft does not self-certify.

## Output

```markdown
## Draft

[Prose only. Headings only where the structure committed them. No commentary inside the draft.]

## Author's notes

- [Outline paragraph rendered differently than committed, and why.]
- [Claims carrying citation placeholders: what is pending for each.]
- [Claims the hedging ladder forced softer than the structure implied.]
- [Word count: actual vs allocation per section, and vs target overall.]
- [Citation style used; any assumed targets or styles, flagged.]
- [Uncommitted sections, if the input was a partial outline.]
```

The draft plus these notes is the handoff. Downstream, refine takes the draft: behavioural review, the fresh-context AI-tell audit, and revision.

## Constraints

- Prose only inside the draft; no bullet points in paragraphs unless the discipline's form requires them.
- No claims, sources, or counterarguments beyond what the committed structure and the sources in hand support.
- One citation style per document. If the venue or document-owner does not specify it, ask once; do not silently pick.
- Placeholders are the only allowed unfinished state, and each states exactly what is pending.
- No numeric scores, no quality ratings, no self-congratulation in the notes: facts, gaps, and deviations only.
