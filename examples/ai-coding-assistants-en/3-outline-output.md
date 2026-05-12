# Example — Output of `3-outline`

> Built from the Output block of `1-capture-argument` and the Source map / Counter-evidence tables of `2-lit-review`. Full essay outline, 2000-word target, APA 7.

## Outline — [Scope: full]

### Introduction (~250 words)

**Function:** Open with the personal anecdote that motivates the argument; define the scope (debugging skill in juniors, not all coding skill); state the thesis; preview the three sub-claims and the counterargument the essay will engage.

#### Paragraph 1 (~120 words)
- **Topic sentence:** "Last semester I built a side project of roughly 8,000 lines almost entirely by accepting suggestions from Copilot and Claude Code, and when it broke in production three weeks later I could not read my own code."
- **Function:** Hook with the personal anecdote; signal that the essay is written from inside the AI-assisted experience rather than as moral panic.
- **Evidence/content:** Personal angle (no source needed).
- **Transition out:** "The experience pointed to something the productivity literature is not measuring."

#### Paragraph 2 (~130 words)
- **Topic sentence:** "Generative AI coding assistants harm junior developers' acquisition of debugging skill by displacing the productive struggle through which the underlying mental models are built — a harm that is acquisition-stage-specific and is consistent with, but extends, Bainbridge's ironies of automation."
- **Function:** State the thesis verbatim; preview three sub-claims (mental-model dependency, construction-phase short-circuit, junior-specific mechanism) and flag the productivity counterargument.
- **Evidence/content:** No source needed — thesis and roadmap.
- **Transition out:** "The first piece of the argument is about what debugging actually requires."

### Body section 1 — Mechanism: what gets short-circuited (~450 words)

**Function:** Establish Sub-claims 1 and 2. Show that debugging is mental-model-dependent (Sub-claim 1) and that AI-assisted construction reduces the cognitive effort that builds the model (Sub-claim 2).

#### Paragraph 3 (~250 words)
- **Topic sentence:** "Debugging is the activity in which a developer's mental model of a system is most heavily taxed, because the bug exists precisely where the model and the reality diverge."
- **Function:** Establish Sub-claim 1 — debugging requires a mental model, and that model is built through effortful engagement during construction.
- **Evidence/content:** Source row 3 (Ericsson, Krampe, & Tesch-Römer, 1993) for the deliberate-practice frame; Source row 2 (Sweller, 1988) for germane cognitive load as the schema-construction mechanism.
- **Transition out:** "If the mental model is built by effortful construction, then anything that reduces that effort during construction has a price."

#### Paragraph 4 (~200 words)
- **Topic sentence:** "AI coding assistants replace the construction-phase effort with an acceptance decision, and the acceptance decision is far less cognitively loaded than authorship."
- **Function:** Establish Sub-claim 2 — AI assistants short-circuit the effort that builds the model. Connect to germane vs extraneous load.
- **Evidence/content:** Source row 5 (Vaithilingam et al., 2022) for empirical evidence that developers accept suggestions without fully understanding them; Source row 1 (Bainbridge, 1983) for the theoretical frame that automation degrades the un-automated skill.
- **Transition out:** "The cost of this short-circuit is not evenly distributed across developers."

### Body section 2 — Acquisition-stage asymmetry: why juniors are hit harder (~450 words)

**Function:** Establish Sub-claim 3 (junior-specific mechanism) by extending Bainbridge's argument and grounding it in empirical evidence on novice harm.

#### Paragraph 5 (~250 words)
- **Topic sentence:** "Bainbridge's ironies of automation gain sharper edges when the human in the loop is still acquiring the skill the automation is replacing, because a senior verifies AI output against an existing mental model while a junior accepts AI output in lieu of building one."
- **Function:** Propose the mechanism for the junior-vs-senior asymmetry; flag explicitly that this is a theoretical extension of Bainbridge, not a directly tested claim.
- **Evidence/content:** Source row 1 (Bainbridge, 1983) for the foundational frame; Source row 6 (Prather et al., 2024, **[VERIFY]**) for empirical evidence that AI assistance widens skill gaps among novices.
- **Transition out:** "What this looks like from the inside is worth describing directly."

#### Paragraph 6 (~200 words)
- **Topic sentence:** "From the inside, the experience is not that the AI made me worse at programming — it is that I never built the model in the first place."
- **Function:** Personal angle — render the lived experience in first person where the HCI register allows it; argue that the deficit is invisible during construction and only surfaces during debugging.
- **Evidence/content:** Personal angle (no source). Optionally re-cite Source row 5 (Vaithilingam et al., 2022) for the gap between acceptance and understanding.
- **Transition out:** "An honest essay has to engage the strongest reading of the opposite case."

### Body section 3 — Counterargument engagement (~400 words)

**Function:** Engage the two strongest counterarguments (productivity gains and the calculator analogy). Concede what is conceded and defend what is defended.

#### Paragraph 7 (~200 words)
- **Topic sentence:** "The strongest counterargument is empirical: Peng et al. (2023) found that Copilot users completed an HTTP-server task approximately 55% faster than controls, with the largest gains among less-experienced developers — and this finding is to be conceded, not disputed."
- **Function:** Concede the productivity finding cleanly; split the construct.
- **Evidence/content:** Source row 4 (Peng et al., 2023). Distinguish task-completion productivity (what the study measures) from skill acquisition (what the thesis is about).
- **Transition out:** "A weaker form of the same objection comes through the calculator analogy."

#### Paragraph 8 (~200 words)
- **Topic sentence:** "The calculator analogy fails because computational off-loading and model-construction off-loading are not the same operation."
- **Function:** Engage the calculator analogy via cognitive load theory. Concede that AI assistance with scaffolding may help novices (Source row C2).
- **Evidence/content:** Source row 2 (Sweller, 1988) as warrant; Source row C2 (Kazemitabaar et al., 2023, **[VERIFY]**) as conceded counter-empirical.
- **Transition out:** "What follows from this is narrower, and more useful, than 'AI assistants are bad'."

### Conclusion (~250 words)

**Function:** Restate the narrowed thesis; flag the theoretical (not empirical) status of Sub-claim 3; identify what juniors should actually do.

#### Paragraph 9 (~250 words)
- **Topic sentence:** "The defensible version of this essay's thesis is not 'AI assistants harm developers' but 'unscaffolded use of AI assistants during the early-acquisition window costs juniors the productive struggle that debugging skill is built from.'"
- **Function:** Restate the narrowed thesis; acknowledge the limit (the junior-specific mechanism is theoretical, not directly tested); offer one practical implication.
- **Evidence/content:** No new sources. Optionally re-cite Source row 1 (Bainbridge, 1983) to close the loop.
- **Transition out:** N/A (final paragraph).

## Coverage check
- [✓] Every sub-claim from `1-capture-argument` is addressed in at least one paragraph (Sub-claim 1 in P3; Sub-claim 2 in P4 and P6; Sub-claim 3 in P5–P6).
- [✓] Every source in the Source map is used at least once (Bainbridge in P4 and P5; Sweller in P3 and P8; Ericsson et al. in P3; Peng et al. in P7; Vaithilingam et al. in P4 and P6; Prather et al. in P5; Kazemitabaar et al. in P8).
- [✓] Counter-evidence is engaged with explicitly in a dedicated section (P7 and P8).
- [✓] Word counts sum to 2000 ±10% (250 + 450 + 450 + 400 + 250 = 1800; budget for 2000 leaves +200 slack distributed across body paragraphs).

## Flags
- Sub-claim 3 (junior-specific mechanism) is theoretical, supported by inference from Bainbridge and one **[VERIFY]** empirical source (Prather et al., 2024). The essay must explicitly flag this in P5 and the conclusion.
- The bridge from "novice harm in programming" to "debugging skill specifically" is also theoretical (lit-review Gap). Conclusion should acknowledge.
- Two `[VERIFY]` sources are load-bearing for one paragraph each (P5, P8). If verification fails, those paragraphs need to fall back on theoretical-only support.
