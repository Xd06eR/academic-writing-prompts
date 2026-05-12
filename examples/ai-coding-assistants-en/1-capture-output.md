# Example — Output of `1-capture-argument`

> What the user fed in: the Essay Context above, plus a raw brain-dump (reproduced under "Raw input" below). The skill ran a grill loop of four questions until the Readiness checklist cleared. The questions, the user's answers, and the resulting Output block are all reproduced here verbatim so a reader can see what the loop actually looks like.

## Raw input (what the user pasted under `## Raw input:`)

> I use Copilot and Claude Code daily. I've noticed I just accept suggestions without really reading them. Last semester I built a side project almost entirely with AI help and now I can't read my own code or debug it when it breaks. I think the issue is specific to juniors — seniors have the mental model and AI is a force multiplier; juniors don't, and AI substitutes for building one. There's Bainbridge's "ironies of automation" from like the 80s saying humans get worse at the task the automation takes over. My prof has been covering cognitive load and skill acquisition. I want to argue this from inside my own experience, not as a moral panic.

## Grill loop (verbatim)

> **Q1:** Your raw input talks about "skill" broadly. Is the thesis about *all* coding skill (writing code, design, testing, debugging), or specifically about *debugging* skill — the part where you need a mental model of what the code does and why?
>
> **My recommended answer based on what you've said:** Specifically debugging. Your evidence — "I can't read my own code or debug it when it breaks" — is sharpest there. A thesis that tries to cover all coding skill becomes vague; debugging is concrete, has a clear cognitive-psych signature (it depends on the mental model the developer holds), and matches the Bainbridge framing tightly.
>
> **Why this matters:** Scope decides which literature you cite. "All coding skill" makes the essay defensible only with a meta-review that doesn't exist; "debugging skill" lets you anchor on cognitive load and Bainbridge directly.

**User answer:** Yes, debugging specifically. I can write new features with AI fine — I get stuck when it breaks.

---

> **Q2:** Is the harm you're claiming *permanent* (juniors who lean on AI now will never develop debugging skill), or *delayed-but-recoverable* (juniors can recover the skill later if they choose to struggle, but the early-acquisition window is where it matters)? Pick the weaker, more honest version unless you have evidence for the stronger one.
>
> **My recommended answer based on what you've said:** Delayed-but-recoverable, with the early-acquisition window as the crux. This matches the deliberate-practice literature (skill is acquired through effortful struggle, not exposure) and matches your own report — you noticed the deficit and could now choose to work on it. The stronger "permanent" claim isn't defensible from your evidence and would overreach.
>
> **Why this matters:** Overclaiming is the #1 way undergraduate essays lose marks. Picking the weaker, honest version is also more interesting — it suggests a remediable problem, not a moral panic.

**User answer:** Delayed-but-recoverable. The early window is what I'm arguing for.

---

> **Q3:** Strongest counterargument: GitHub-funded research (Peng et al. 2023) finds Copilot users complete tasks ~55% faster. A sceptic will say productivity gains *are* skill — you're letting nostalgia for struggle override empirical evidence. How do you want the essay to engage that?
>
> **My recommended answer based on what you've said:** Concede the productivity finding fully — don't dispute the 55%. Then split the concept: *task completion productivity* and *skill acquisition* are different constructs. The Copilot study measures the former on tasks the developer is already equipped to do; it does not measure what happens when the developer has to debug code they did not internally model. Your thesis is about the second construct, not the first.
>
> **Why this matters:** This is the strongest counterargument in the literature, and conceding it cleanly is far more credible than disputing it. The split-the-construct move is also the essay's intellectual core — it turns a one-sided argument into a real disagreement.

**User answer:** Yes, exactly. Concede productivity, argue skill acquisition is different.

---

> **Q4:** The "junior vs. senior" split is the most original move in your argument. Do you have a *mechanism* for why it should hold, or is it just intuition? If it's just intuition, the essay needs to either (a) propose a mechanism and flag it as theoretical, or (b) drop the junior-specific claim and argue the weaker "AI assistants harm debugging skill" version.
>
> **My recommended answer based on what you've said:** Propose a mechanism and flag it as theoretical. The mechanism: seniors already hold the mental models that AI suggestions slot into, so the AI's output is verified against an existing internal representation. Juniors don't have those models yet; AI output gets accepted without verification because there is nothing to verify it against. This is consistent with Bainbridge's framing (humans deteriorate on tasks the automation handles) but adds an acquisition-stage twist — automation is most harmful where the human is still building the model the automation is replacing.
>
> **Why this matters:** Without a mechanism, "juniors are different" is hand-waving. With a mechanism, it becomes a testable extension of Bainbridge and earns the essay its theoretical contribution.

**User answer:** That mechanism is exactly what I meant but couldn't articulate. Use it.

---

Readiness checklist clears after Q4. (Five items: thesis defensible ✓, ≥2 sub-claims ✓, personal angle ✓, strongest counterargument identified ✓, evidence types named ✓.) Output block follows.

## Output block

```markdown
## Thesis
Generative AI coding assistants harm junior developers' acquisition of debugging skill by displacing the productive struggle through which the underlying mental models are built — a harm that is acquisition-stage-specific and is consistent with, but extends, Bainbridge's ironies of automation.

## Sub-claims
1. Debugging skill depends on a mental model of the system the debugger is working on, and that mental model is built through effortful engagement with the code during construction, not from passive exposure to it.
2. AI coding assistants short-circuit the construction-phase effort by producing working code without requiring the developer to hold the design rationale in working memory — a productive struggle is replaced by an acceptance decision.
3. The harm is sharper for juniors than seniors because seniors verify AI output against existing mental models, while juniors accept AI output in lieu of building one — automation is most harmful at the acquisition stage of the skill it replaces.

## Personal angles
- User built a side project almost entirely with AI assistance last semester and subsequently could not debug their own code when it broke. The essay should argue from inside that experience, in first person where the discipline allows, not as a detached observer or moralist.
- Frame the mechanism around cognitive load and deliberate practice (course material from weeks 3–5), not generic "AI bad" talk.

## Counterarguments to address
- Productivity counterargument: Peng et al. (2023) find Copilot users complete tasks ~55% faster. Concede fully; argue task-completion productivity and skill acquisition are different constructs and the productivity finding does not measure the latter.
- "Calculator analogy" counterargument: calculators did not destroy mathematical skill; AI assistants will not destroy programming skill. Engage by distinguishing computational off-loading (the calculator case) from model-construction off-loading (the AI case), with cognitive load theory as the warrant.

## Evidence needed
- Foundational: Bainbridge (1983) ironies of automation, directly cited.
- Foundational: cognitive load theory and deliberate practice — Sweller (1988) or successor, Ericsson, Krampe, & Tesch-Römer (1993) or successor.
- Empirical (recent): at least one 2022+ study on AI coding assistants. Peng et al. (2023) for the productivity counterargument; an empirical study on novice harm (e.g. Prather et al. 2024 or a comparable CHI/ICER paper) for Sub-claim 3.
- Counter-empirical: a study showing AI coding assistants help novices when scaffolded appropriately (e.g. Kazemitabaar et al. 2023, if it holds up — engage so the essay isn't one-sided).

## Open questions
- Most published evidence on AI coding assistants is concentrated on Copilot and short-task settings; the side-project, multi-week setting of the user's personal experience is undersampled in the literature. Acknowledge this gap rather than overgeneralising.
- The mechanism for the junior-specific harm (Sub-claim 3) is theoretical, not directly tested. Flag in the essay as a theoretical contribution requiring empirical follow-up.
```
