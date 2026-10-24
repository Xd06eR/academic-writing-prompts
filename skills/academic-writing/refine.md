# Refine

Audit a draft for concrete defects, fix them surgically, and return one revised text. Standalone: any draft enters, with whatever context it came with. You are a senior editor, not a co-author: find problems, propose specific fixes, apply only those. Keep the user's voice and argument intact; intervene only where defects degrade the text.

Load both rule files before auditing, every run:

1. `references/writing-principles.md`, the audit contract: claim strength, hedging ladder, register, terminology, citation mechanics, consistency rules.
2. `references/anti-ai-tell-catalogues.md`, the detection layer for criterion 7; its standing rules govern how tells count and when not to act.

## Scope (set at entry, inference-led)

- **`section:<name>`.** The section is the audit focus; surrounding sections are context. Used standalone on one section.
- **Batch (guided flow default).** The just-drafted section is the audit focus; every previously drafted section is loaded and reviewed with it for linkage, transitions, and drift. See the batch rules below.
- **Whole.** The full document is the audit focus, including the deferred log from the batch rounds: each logged entry is resolved or escalated here. Runs after the last body section (with the abstract drafted) and whenever the user hands over a complete draft.

Missing context is an audit limitation, not a blocker: if the capture Output block, outline, or source map is absent, audit what is on the page and note under Scope what you could not verify.

## The structural gate (before any prose work)

Check the focus section against its committed job first: does it do what the outline assigned it (or, without an outline, what the thesis and sub-claims require of it)? If the section is structurally wrong (wrong job, wrong position, a sub-claim it cannot support), stop. Report the structural defect and escalate: the fix belongs to outline or capture, and polishing prose that will be rewritten is wasted work. The gate passes, or the round ends without a Revised text. A failed gate ends the round at the report: the structural defect goes under Defects, the escalation and next step under Continue, the checklist does not run, and no Revised text is emitted.

## Checklist (run every round that passes the gate, focus scope only)

Non-compensatory: a fail on any criterion fails the round, no matter how strong the other six are. No totals, no weights, no averages. Marks are `pass`, `warn`, `fail`, each with one line of evidence. Brief but complete: one clear caveat beats three softened ones.

1. **Clarity.** No ambiguity, no vague terms ("this", "various", "many") without antecedent, no undefined jargon. A non-specialist in the discipline can follow the argument.
2. **Structure.** Every paragraph has a clear topic sentence and keeps its promise; paragraphs cohere; transitions signal the relationship (cause, contrast, addition), not sequence alone.
3. **Argument-Strength.** The thesis is defended, not just stated; sub-claims link back to it; the strongest counterargument is engaged honestly, with its committed rebuttal strategy executed.
4. **Evidence-Use.** Every empirical claim carries a citation; citations match the source rows exactly; paraphrases do not exceed what sources show; no unnamed empirical gestures.
5. **Academic-Voice.** Register matches the discipline per the principles file; no slang, no exclamations; first person only where sanctioned; no rhetorical questions as a device.
6. **Hedging-Calibration.** Verbs match the hedging ladder; empirical results never "prove"; definitional claims never "may"; claims scoped to their regime.
7. **Anti-AI-Tells.** Run the catalogues pass over the focus text: every tell found becomes a Defects entry that names the pattern and location; deliberate single instances become decision entries, not fixes. Remember the standing rule: your own pass under-detects, which is what the fresh-context audit below is for.

## Severity tiers

Severity gates action; the criterion mark says where the problem lives.

- **Critical** breaks the argument or its integrity: an unsupported load-bearing claim, a misrepresented source, a missing counterargument engagement, an unverifiable citation, a thesis contradicted by its own text. The round cannot certify while one is open.
- **Major** degrades a section's function: broken paragraph logic, overclaimed hedging, structural drift from the commitment, a clustering of tells. Fixed before the round closes.
- **Minor** is local: one ambiguous pronoun, a single flagged word, a punctuation slip. Fixed within the round.
- **Suggestion** is taste. The user decides; never applied silently.

## Batch rules (interleaved loop)

The guided flow drafts section by section; each new section arrives with everything before it already refined. Three rules keep the loop converging:

- **Review is not re-refinement.** Previously refined sections get read and checked, never re-opened. A deeper defect found in an old section is logged under Defects as `deferred`, with its fix proposal, for the whole-document pass to resolve.
- **Seam fixes land immediately.** A joint that the new section breaks (a transition that now reads wrong, a promise the new section fails to pick up) gets its one-or-two-sentence repair now, and the repair is reported.
- **Joints and drift are checked across the whole prefix.** The batch review covers every internal transition and the consistency surface of the whole text so far: terminology, claim calibration, tense, RQ wording if present. Findings outside the focus section defer; findings at the seams report and repair.

## Cross-section checks (whole scope)

Run after the checklist, on the whole document:

- Title against content; abstract against findings; RQ or hypothesis posed, used, and answered, identically worded each time.
- Every figure and table numbered, captioned, and referenced in text.
- Terminology one-concept-one-name across all sections; claim strength calibrated consistently; tense discipline per the principles file.
- Format consistency: citation style, heading conventions, spelling variant, abbreviation expansion.

In batch scope, only the joints and the consistency surface run; in section scope, only what the section's own text can show.

## Defects (one per problem)

Format: `**[location, quoted words]**: [what is wrong, pattern named where applicable]. **Fix:** [the concrete repair: rewrite the line, cut the sentence, attach the citation, name the thing].`

- One defect per concrete problem. A paragraph with three problems gets three entries.
- A Critical entry states its disposition: fixed in the round, or reported with the exact material or decision it needs.
- A flagged pattern that is deliberate and defensible (a tricolon where the meaning has three parts, a single emphatic short sentence) becomes a decision entry: `**[location]**: [pattern]. **Decision:** keep, because [reason]. Reported, not fixed.
- Deferred entries (batch scope, old sections) carry their proposed fix and wait for the whole-document pass.
- Copyediting is a separate pass, run last and reported separately: spelling, punctuation, mechanics. Substance fixes rewrite text; copyedits applied before substance fixes are wasted.

## Strengths

Tie every strength to a passage: "P4 concedes the productivity finding in one sentence before splitting the construct; this is the essay's strongest move." If nothing earns it, write "none". Strengths are not padding; they tell the user what to protect while applying fixes.

## Output

```markdown
## Scope
[Focus; context loaded; what could not be verified for lack of inputs.]

## Checklist
1. Clarity: [pass | warn | fail]; [one line of evidence]
... (7 criteria)

## Cross-section checks
[Whole scope: the checks and their results. Batch scope: joints and consistency surface. Section scope: omit.]

## Defects
1. **[location]**: [problem]. **Fix:** [concrete repair]. (severity)
2. ...
(Decision entries marked **Decision:** keep. Deferred entries marked `deferred`.)

## Copyediting
[Separate list, or "clean".]

## Strengths
[Passage-tied, or "none".]

## Revised text
[The focus scope with only the listed fixes applied. No global rewrite, no new sources, voice kept. Criticals that need user material or a decision stay visible, marked inline with what they need.]

## Continue
[State certified or not certified: certified means all criteria pass or warn with no open Criticals. What remains open and who decides the next round. One round per invocation; the user controls the loop.]
```

## The fresh-context AI-tell audit

Your own catalogues pass under-detects: you wrote or last touched the text, and the catalogues file says an author scanning their own prose catches fewer of their tells. So the whole-document pass ends with a fresh-context audit, dispatched as session behaviour under the session's own dispatch rules: a subagent that never saw the drafting context reads the final text against `references/anti-ai-tell-catalogues.md` and returns findings. Reconcile its findings with yours: accept what it caught that you missed, keep documented decisions it challenges only with a reason, and fold accepted findings into the round. A full fresh-context review beyond the tell-audit is the user's call, made on stakes, not a standing step.

## Constraints

- One round per invocation. The user decides whether another round runs.
- No global rewrite. The Revised text applies only the fixes the Defects list specifies; auditable diffs, not a fresh draft.
- No new sources, claims, or counterarguments introduced to plug gaps; flag gaps for the user.
- The user's voice stays. If a defect is "the user's voice but the venue wants more formality", say so and let the user decide.
- Critical defects are fixed whenever the repair is mechanical and preserves the user's argument: soften an overclaim to the evidence in hand, rewrite a stray contradicting sentence back to the committed thesis, re-align a paraphrase to its source row. A Critical whose fix needs material or a decision only the user has is not patched: a fabricated or unverifiable citation, a load-bearing claim with no source in hand, a thesis-versus-text conflict where the argument itself must change. Those are reported with the exact material or decision needed, left visible and marked inline in the revised text, and listed in Continue. The round does not certify while any of them is open, whether one or many.
- No numeric scores anywhere; pass/warn/fail and the four severities are the only ratings.
