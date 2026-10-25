# Example: refine

## User

```text
We built the argument for my internship essay earlier (thesis: universities should require every student to complete a funded internship before graduation). I already wrote the introduction myself before all that. Here it is:

In today's competitive job market, students face enormous pressure to stand out. Many studies have shown that internships improve graduate employability, and this proves that universities should require every student to complete one before graduation. Internships allow students to test their fit with their chosen field, which is important because students often pick the wrong major. A required internship also helps poorer students because it guarantees them the experience that wealthier students get through family connections. The strongest objection is that mandatory internships burden students who cannot afford unpaid work; funding the placement answers that objection directly.

Can you run your refine pass on it?
```

## Model

```markdown
## Scope

`section:Introduction`, standalone entry. Context: the committed thesis from the user's message. Absent: the capture Output block, the outline, and the source map; citation rows could not be verified at all, and the audit is limited to what the page shows, per refine.md's "an audit limitation, not a blocker." Structural gate: passed; the section does the job the thesis requires (thesis stated, strongest counterargument engaged), so this is a prose-and-logic round.

## Checklist

1. Clarity: warn; "Many studies" and "this" in sentence 2 carry loose referents, and "the wrong major" is vague.
2. Structure: pass; evidence and thesis, mechanism, equity, objection, in order, each with a job.
3. Argument-Strength: pass; the strongest objection is stated fairly and answered with the committed rebuttal (funding the placement).
4. Evidence-Use: fail; three unnamed empirical gestures ("Many studies have shown", "students often pick the wrong major", "wealthier students get through family connections"), zero citations, no source map in hand to attach them to.
5. Academic-Voice: pass; register steady, no slang, no rhetorical questions as a device.
6. Hedging-Calibration: fail; "proves" is a ladder violation, and the leap from an employability effect to a graduation requirement is an inference, not a demonstration.
7. Anti-AI-Tells: warn; a throat-clearing opener and one vague attribution, single sightings with no cluster.

## Defects

1. **[S1, "In today's competitive job market... stand out"]**: throat-clearing opener with inflated stakes (catalogue §6); the frame names a generic climate instead of this essay's territory. **Fix:** cut the sentence; the paragraph opens on the evidence per the replacement sentence in Defect 2. (Major, fixed)
2. **[S2, "Many studies have shown"]**: unnamed empirical gesture carrying the thesis; load-bearing because the mandate rests on it. **Fix:** reported, not patched: the named studies are user material, so the claim stays marked inline until the source map arrives. (Critical, reported)
3. **[S2, "this proves"]**: hedging-ladder violation ("prove" for empirical results) plus an is-ought leap presented as demonstration. **Fix:** recalibrated to "suggests" inside the replacement sentence below, where the mandate is phrased as the essay's position. (Major, fixed)
4. **[S2, thesis drops "funded"]**: the draft's thesis sentence states an unfunded mandate, contradicting the committed thesis; the equity rebuttal the argument owns never appears. **Fix:** the replacement sentence below restores "funded" and re-commits the text to the thesis. (Critical, fixed)
5. **[S3, "which is important because students often pick the wrong major"]**: uncited empirical claim; "the wrong major" is vague. **Fix:** cut the clause; the fit reason stands without it. If the source map holds major-switching data, restore with a citation. (Major, fixed)
6. **[S4, "helps poorer students because it guarantees them the experience that wealthier students get through family connections"]**: uncited load-bearing premise inside the equity claim, one of the argument's pillars; "guarantees" overstates what a requirement can deliver. **Fix:** reported, not patched: softened to a mechanism statement with "often" and "access to" inside the replacement sentence below; the citation is user material and the claim stays marked inline. (Critical, reported)
7. **[S2/S4, loose referents]**: "this" in sentence 2 has two candidate antecedents. **Fix:** removed in the replacement sentences below. (Minor, fixed)

Defects 2-4 and 7 share one replacement for sentence 2, applied once:

- Sentence 2 becomes: "Internships improve graduate employability [citation needed: the employability studies from the confirmed source map], which suggests that universities should require every student to complete a funded internship before graduation."

Defect 6's replacement for sentence 4:

- Sentence 4 becomes: "A required internship would also give poorer students access to the professional experience that wealthier students often obtain through family connections [citation needed: evidence that advantaged students access internships through family connections]."

## Copyediting

Clean. Register-level items ran as defects above, not copyedits.

## Strengths

- The objection handling answers with the funding bound, exactly the rebuttal the argument committed to upstream; protect it while the citations are pending.
- The fit rationale is concrete and arguable from common experience; it earns its place as a sub-claim once the uncited clause is cut.
- The equity pairing (sentence 4 against the objection sentence) is the essay's strongest structural move: the requirement framed as leveller, with the objection pre-answered.

## Revised text

Internships improve graduate employability [citation needed: the employability studies from the confirmed source map], which suggests that universities should require every student to complete a funded internship before graduation. Internships allow students to test their fit with their chosen field. A required internship would also give poorer students access to the professional experience that wealthier students often obtain through family connections [citation needed: evidence that advantaged students access internships through family connections]. The strongest objection is that mandatory internships burden students who cannot afford unpaid work; funding the placement answers that objection directly.

## Continue

Not certified: two Criticals are open and both need material only the user has (Defects 2 and 6, marked inline). Hand over the confirmed source map and the next round can attach the citations, re-check Evidence-Use against the rows, and certify. One round per invocation; whether another round runs is the user's call.
```
