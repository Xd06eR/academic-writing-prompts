# Example — Output of `2-lit-review`

> This step was run on an LLM with web search. Two of the rows are marked `[VERIFY]` because the assistant could not confirm the exact venue/DOI with high confidence — per the skill's rules, the user is told to verify before pasting any citation. This is the honest output the skill produces, not a polished façade.

## Source map

| # | Claim supported | Source (author, year) | URL/DOI | Finding (1–2 sentences) | Source type |
|---|-----------------|-----------------------|---------|-------------------------|-------------|
| 1 | Sub-claim 1 (mental model required for debugging); foundational frame for the whole essay | Bainbridge, L. (1983). Ironies of automation. *Automatica*, 19(6), 775–779. | https://doi.org/10.1016/0005-1098(83)90046-8 | Argues that automating part of a task degrades the human operator's skill on the un-automated part, because (a) operators no longer practise the manual mode and (b) the operator must intervene precisely when the automation fails, which is the hardest condition under which to act. The argument is theoretical, drawing on process-control engineering. | Theoretical (foundational) |
| 2 | Sub-claim 2 (cognitive effort during construction builds the model) | Sweller, J. (1988). Cognitive load during problem solving: Effects on learning. *Cognitive Science*, 12(2), 257–285. | https://doi.org/10.1207/s15516709cog1202_4 | Establishes that learning is impaired when the cognitive load of problem-solving is consumed by activities extraneous to schema construction; conversely, germane load (effortful processing that builds schemas) is the mechanism by which durable skill is acquired. | Theoretical / experimental |
| 3 | Sub-claim 1 and Sub-claim 3 (skill acquisition requires effortful practice, not exposure) | Ericsson, K. A., Krampe, R. T., & Tesch-Römer, C. (1993). The role of deliberate practice in the acquisition of expert performance. *Psychological Review*, 100(3), 363–406. | https://doi.org/10.1037/0033-295X.100.3.363 | Argues that expert performance is acquired through deliberate practice — effortful, focused work on tasks just beyond current ability with feedback — not through accumulated exposure or general experience. Foundational citation. | Theoretical (foundational) |
| 4 | Productivity counterargument (used in the counter-evidence section) | Peng, S., Kalliamvakou, E., Cihon, P., & Demirer, M. (2023). The impact of AI on developer productivity: Evidence from GitHub Copilot. *arXiv preprint* arXiv:2302.06590. | https://arxiv.org/abs/2302.06590 | Randomised controlled trial (N=95 software developers) where Copilot users completed an HTTP-server task approximately 55% faster than the control group, with effects strongest among less-experienced developers. The study measures task completion time, not later skill retention or debugging ability. | Empirical (RCT) |
| 5 | Sub-claim 2 (developers accept suggestions without sufficient verification) | Vaithilingam, P., Zhang, T., & Glassman, E. L. (2022). Expectation vs. experience: Evaluating the usability of code generation tools powered by large language models. *Extended Abstracts of the 2022 CHI Conference*. | https://doi.org/10.1145/3491101.3519665 | User study (N=24) found participants frequently accepted Copilot suggestions without fully understanding them, and that incorrect suggestions were often discovered only at runtime — not during code review. | Empirical (user study) |
| 6 | Sub-claim 3 (acquisition-stage harm to novices) **[VERIFY]** | Prather, J., Reeves, B. N., Denny, P., Becker, B. A., et al. (2024). The widening gap: The benefits and harms of generative AI for novice programmers. *Proceedings of ICER 2024*. | https://dl.acm.org/doi/10.1145/3632620.3671116 | Reports that high-performing novice programmers gain from generative AI assistance while low-performing novices fall further behind, suggesting AI assistance amplifies rather than evens out skill differences during early acquisition. **Verify exact venue, page numbers, and DOI before citing.** | Empirical (mixed-methods study) **[VERIFY]** |

## Counter-evidence (sources the essay must engage with)

| # | Counter-claim it raises | Source | URL/DOI | Why it matters |
|---|--------------------------|--------|---------|----------------|
| C1 | Productivity gains from AI assistance are real and large; opposing the assistants on skill grounds is romantic about struggle | Peng et al. (2023), as above (Source 4) | https://arxiv.org/abs/2302.06590 | This is the strongest counterargument in the literature. The essay must concede the productivity finding cleanly and argue that productivity ≠ skill acquisition. |
| C2 | AI code generators can help novices when used with appropriate scaffolding | Kazemitabaar, M., Chow, J., Ma, C. K. T., Ericson, B. J., Weintrop, D., & Grossman, T. (2023). Studying the effect of AI code generators on supporting novice learners in introductory programming. *Proceedings of CHI 2023*. **[VERIFY]** | https://doi.org/10.1145/3544548.3580919 | Suggests the AI-coding-assistant harm is not uniform; pedagogical scaffolding can mediate the harm. Concedes part of the thesis, narrows the claim to "unscaffolded use harms juniors". |

## Gaps (claims I could not back with a verifiable source)

- The specific claim that **debugging** skill (as distinct from coding skill broadly) is differentially harmed by AI assistants. No direct empirical study found. The essay should rest on the inference chain: (a) debugging requires a mental model (Sub-claim 1, supported by Bainbridge and cognitive-load literature), and (b) AI assistants reduce the effort required to build that model during construction (Sub-claim 2, supported by Vaithilingam et al.). The bridge from "novice harm in programming" to "debugging skill specifically" is theoretical, not empirical. Flag this honestly in the essay's conclusion.

## ⚠️ Verification step (do this before using any citation)

For every row above, click the URL and confirm:
1. The source exists and is what the assistant said it is.
2. The finding in the table matches what the source actually says.
3. The citation style matches APA 7 (Essay Context requirement).

For the two `[VERIFY]` rows in particular, the assistant flagged that it could not confirm the exact venue, DOI, or finding with high confidence — replace or remove these citations if verification fails. Hallucinated citations are detectable and constitute academic dishonesty.
