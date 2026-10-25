# Example: capture-argument

## User

```text
I need to write an argumentative essay for my university writing course, around 1500 words. I want to argue that universities should require every student to complete an internship before graduation. Honestly my main reason is that I did one last summer and it changed how I think about my major, but I know that's just me. Can you help me build the argument properly?
```

## Model

```text
Intake: the input carries more than a topic; a stance and one non-generic personal angle are already in hand.

Settled: thesis candidate (universities should require every student to complete an internship before graduation; arguable, specific, wording to be sharpened) and the personal angle (last summer's internship changed how the user thinks about their major).

Still open: sub-claims (only the n=1 personal reason so far), counterargument, evidence types. The weakest branch is the missing general sub-claim: without one, the essay rests on a single-context generalization.

> **Q[1]:** Beyond your own experience, what makes this requirement true for all students?
>
> **My recommended answer:** The strongest general reason is fit assessment under uncertainty: students cannot accurately judge their fit with their major until they have practiced the work, and a required internship forces that reality check before graduation. Your own change is one instance of this mechanism, not the reason itself. Take fit as the lead sub-claim, and employability data as the second.
>
> **Why this matters:** Readiness item 2 (at least two sub-claims); without a general reason the essay rests on a single-context generalization, which a sceptic kills in one sentence.
```

## User

```text
Hmm, the fit thing makes sense, I literally thought I wanted to go into marketing until I did it for eight weeks and realized I hated the day-to-day. But honestly, isn't the employability argument stronger? My career centre keeps telling us graduates with internship experience get hired faster, and that feels like the more convincing point for a sceptical reader? And yeah I admit I have no idea what the strongest counterargument would be. Something about how it delays graduation for people who can't afford to work unpaid, maybe?
```

## Model

```text
Answering the pushback first: employability should be kept, but it cannot lead, because it supports "encourage" just as well as "require"; only fit justifies compulsion. The career-centre hearsay is an appeal to authority and cannot enter the essay; that pattern becomes the next question's target. The equity worry is logged as the counterargument candidate.

Settled this round: sub-claim 1 (fit assessment under uncertainty), with the personal angle upgraded to concrete form (expected marketing, eight weeks, disliked the day-to-day); sub-claim 2 (employability) admitted, framing still open; counterargument candidate logged (unpaid internships burden students who cannot afford them; may delay graduation), rebuttal strategy unassigned.

> **Q[2]:** What type of source would make "graduates with internship experience get hired faster" convincing to a sceptic?
>
> **My recommended answer:** Two routes, and I recommend the first: your university career services' annual first-destination employment report (concrete numbers: employment rates for graduates with and without internship experience), or a named quantitative study on internship-to-offer conversion. Write the claim as correlation, explicitly not causation: the selection effect (students who seek internships differ to begin with) is the sceptic's first bullet, and you want to fire it yourself.
>
> **Why this matters:** Readiness item 5 (an evidence type per sub-claim); written as causation, or resting on the career centre's say-so, sub-claim 2 dies to correlation-as-causation in one line.
```

## User

```text
The first-destination report sounds findable, our career services office publishes one every year. I can get the actual numbers. And okay, correlation not causation, got it. For the counterargument, yeah the unpaid thing genuinely worries me, some of my classmates already work weekends to support themselves. Could the answer just be that the requirement only counts paid internships? Or is that dodging the objection?
```

## Model

```text
Not dodging: that is the concede-and-limit direction, but paid-only alone is not enough. Two gaps remain. Supply: paid placements cannot cover every student, especially outside popular fields. Opportunity cost: a paid internship's wage can still undercut the work a student lives on.

Settled this round: sub-claim 2's evidence type (first-destination report, numbers obtainable); correlation framing locked. Counterargument confirmed as strongest: the equity objection, which the user genuinely worries about and which sceptics raise first.

> **Q[3]:** Will you accept the concede-and-limit package for this objection: internships must be paid or stipend-supported, schedulable around students' jobs, with the essay conceding in text that the objection defeats an unfunded mandate, not a requirement itself?
>
> **My recommended answer:** Accept, and narrow the thesis to match: from "universities should require an internship" to "universities should require a funded internship." This does not weaken the position; it occupies the sceptic's ground first.
>
> **Why this matters:** Readiness item 4 (counterargument with strategy assigned); if the strategy stays open, this dispute re-opens downstream, and paid-only on its own collapses to the supply question.
```

## User

```text
Yes, take the whole package. And 'funded internship' is genuinely better, you're right it doesn't weaken the position, it just answers the objection before it's raised. For the fit sub-claim's evidence... hmm. Maybe surveys where graduates say the internship changed their plans? Or something about students choosing the wrong major? I don't actually know what that kind of source is called.
```

## Model

```text
One branch remains: sub-claim 1's evidence type.

> **Q[4]:** What study design would survive a sceptic for the claim that students revise their fit judgments after an internship?
>
> **My recommended answer:** Primary evidence: a pre-post survey of interns, the same students measured before and after, on career certainty. The construct's name is career decision self-efficacy; search that term. It beats "graduates looking back say it changed them" because retrospective self-report is discounted by memory rationalization. Backup: a large national alumni survey reporting the share of graduates who would choose a different major, carrying the front half (students do choose wrong).
>
> **Why this matters:** Readiness item 5, last entry; fit is the essay's lead claim, and resting it on your n=1 plus retrospective testimony returns it to single-context generalization. If the lead falls, the essay falls with it.
```

## User

```text
Pre-post survey sounds exactly right, and career decision self-efficacy is a great keyword, I'd never have found that on my own. Yes, take that as the main evidence with the alumni survey as backup.
```

## Model

````text
All five readiness items clear. The Output block:

```markdown
## Thesis
Universities should require every student to complete a funded internship before graduation.

## Sub-claims
1. Students cannot accurately assess their fit with their major until they have practiced the work; a required internship is the mechanism that forces this reality check before graduation.
2. Graduates with internship experience report better early-career employment outcomes, and a requirement closes that gap for students who would not pursue one voluntarily. (Framed as correlation, not causation.)

## Personal angles
- The author's own internship last summer: expected to go into marketing, spent eight weeks in it, and found the day-to-day work unlikeable. A live instance of sub-claim 1, used as illustration, not as the argument's ground.

## Counterarguments to address
- A universal requirement burdens students who cannot afford unpaid work and may delay their graduation. Strategy: concede-and-limit: the objection defeats an unfunded mandate, not a funded one; the essay concedes this in text and bounds the claim accordingly (internships must be paid or stipend-supported, and schedulable around students' jobs).

## Evidence needed
- For sub-claim 1 (primary): a pre-post survey of undergraduate interns measuring career decision self-efficacy before and after the internship. (Backup: a large national alumni survey reporting the share of graduates who would choose a different major.)
- For sub-claim 2: the university career services first-destination employment report, with specific numbers, cited as correlation.

## Open questions
- None. All five readiness items cleared within four questions.
```

Does this argument feel like yours? Edit any field, or approve and we move on.
````

Four questions is the fast path, not the norm: eight is the soft cap, and the escapes (soft cap with flagged gaps, non-convergence bailout) exist for runs that do not converge this cleanly.
