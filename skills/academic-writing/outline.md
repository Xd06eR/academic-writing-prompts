# Outline

Commit structure to paper before prose exists. Turn the argument and the sources in hand into a section-by-section plan with literal topic sentences, evidence assignments, and word allocations that the draft can render without re-deciding anything. Standalone: builds from a capture Output block, a rough thesis, a template, or a partial outline.

Load `references/writing-principles.md` before running. Its one-concept-one-name rule governs the committed sentences, and its structure section governs what each section owes the argument. This capability commits structure, not prose, so the detection catalogues are not needed here.

## Inputs (run on whatever arrives)

- **Capture Output block** (with or without a lit-review source map). Full build: sections, paragraphs, allocations, coverage check.
- **A thesis and sub-claims in any form.** Build the outline around them; evidence slots name what is in hand and flag what is missing.
- **A template, brief, or venue spec alone.** Adopt it as the structure authority (below); then ask one question for the thesis, since nothing can be outlined without it.
- **A partial outline.** Extend it under the same contract; paragraphs already committed are left alone unless they fail the checks below.
- **`section:<name>`.** Outline that one section against the thesis and the surrounding sections' committed sentences, in whatever state they are in.
- **Nothing.** Ask one question: what is the document's thesis? There is no structure to infer from without it.

## Structure authority

An external template (venue spec, assignment brief, journal structure, document-owner template) is a parameter that overrides every internal default in this file: section set, section order, headings, word splits, paragraph shape where specified. Where the template speaks it wins; where it is silent, the defaults below apply. It arrives with any input, attached, named, or pasted. It binds structure only, never content: it cannot supply or force a claim, source, or counterargument.

State the authority at the top of the outline: named template, or "internal default". An assumed target or style is flagged, not silent.

## Section design

Default order for empirical papers: Introduction → Literature review → Methods → Results → Discussion → Conclusion. Genres without Methods/Results collapse the order accordingly (see `draft.md`); the invariant ends are Introduction first and Conclusion last, with the abstract slot reserved in the allocation and written after the body. Counterarguments are placed where the genre puts them: a dedicated engagement section in essays, the Discussion in empirical papers.

Each section gets one **Function** line: the job the section must do for the argument ("establishes Sub-claim 2", "concedes the productivity finding and splits the construct"). Write it in argument terms, not topic terms, per the section so-what list in the principles file. The Function line is what refine's structural gate checks the drafted section against.

## Paragraph planning

Each paragraph gets four commitments:

1. **Topic sentence.** A literal sentence in quotation marks, committed verbatim. It carries the paragraph's claim: no meta-commentary, no placeholders, load-bearing terms pinned per one-concept-one-name. The draft renders this sentence as written (see `draft.md`).
2. **Function.** The sub-claim, personal angle, or counterargument the paragraph carries, named so the coverage check can trace it.
3. **Evidence placement.** The source rows assigned to this paragraph's claims, placed now, not retrofitted. Allowed states: named rows in hand; "none", for paragraphs carrying the thesis, a personal angle, or the roadmap; or the flag `[no source in hand: needs <type>]`, naming the source type that would fill it (from capture's Evidence needed when that block is in hand, otherwise named from the claim). Paragraph-level placement is enough; the draft attaches citations at claim creation.
4. **Transition out.** The committed hand-off sentence to the next paragraph, or "none" where the section ending carries it.

TEEL (topic sentence, evidence, explanation, link) is the default shape, not a quota. A paragraph whose function breaks the shape (a definition paragraph, a pure concession, the thesis paragraph) follows its function; state the deviation in one line at planning time.

Every paragraph must trace to a sub-claim, a personal angle, or a counterargument. A paragraph that traces to nothing is cut from the plan; a sub-claim that traces to no paragraph is an unfilled claim, not yet a paragraph.

## Word allocation

- Target: from the user, venue, or template. None given: assume one, state it in the header, and flag it.
- Allocate per section, split to paragraphs. Allocations sum exactly to the body target; reserves outside the body (abstract, front matter) are stated separately.
- Draft tolerances (±15% per section, ±10% overall, see `draft.md`) absorb the drafting wobble; the outline's arithmetic does not rely on them.

## Citation style

From the user, venue, or template; none given: ask once at this step, and the header carries it downstream.

## Coverage check

Run before presenting; every line must close:

- [ ] Every sub-claim maps to at least one paragraph.
- [ ] Every personal angle is placed.
- [ ] Every committed counterargument is placed where the genre puts it.
- [ ] Every source in hand is assigned to a paragraph or waived with a one-line reason.
- [ ] Word allocations sum to the body target.
- [ ] RQ or hypothesis, if the document has one, is stated once and verbatim; the same wording rides the Introduction, Methods, and Conclusion slots.
- [ ] Every Function line names an argument job, not a topic.

A failed check closes before drafting starts. Mapping or arithmetic failures are fixed in the plan now; evidence failures cannot be fixed here and become Flags, since filling them needs material only the user or lit-review can supply.

## Output

```markdown
## Outline: [Scope: full | section:<name>]
Target: [N words body; reserves: abstract ~N; citation style: X]
Structure authority: [named template | internal default]
RQ (if any): "[verbatim sentence]"

### [Section name] (~N words)
**Function:** [the job in argument terms]

#### Paragraph N (~N words)
- **Topic sentence:** "[literal committed sentence]"
- **Function:** [sub-claim / angle / counterargument carried]
- **Evidence:** [source rows | none | [no source in hand: needs <type>]]
- **Transition out:** "[committed hand-off sentence]" | none

## Coverage check
[all boxes checked, or the failure fixed pre-presentation]

## Flags
- [Sub-claims lacking evidence: what would fill them.]
- [Sources in hand that are load-bearing but unverified.]
- [Theoretical inferences the draft must label as such.]
- [Assumed target, style, or structure authority.]
```

Present the outline and stop. In the guided flow this is the plan the draft/refine loop renders section by section (see `draft.md`); standalone, it is the deliverable. Changes after presentation are outline changes: re-commit here, not in the draft.

## Constraints

- Topic sentences are committed once, here; the draft does not re-decide them.
- No claims, sources, or counterarguments beyond what the inputs carry: the outline places, it does not invent.
- A sub-claim lacking evidence is flagged with the source type that would fill it, never silently sourced and never left bare.
- Word allocations sum to the target; slack is not hidden inside paragraphs.
- No prose beyond the committed sentences; no numeric scores.
