# Writing principles

The discipline contract behind every writing action this skill performs. Load this file before touching prose in any capability.

**Layers.** `HARD` = violation is a defect; fix before shipping. `JUDGMENT` = a prompt for taste, not a quota; revise only when a real clarity, precision, or support problem exists. Venue rules and document-owner requirements outrank everything here.

---

## 1. Sourcing (HARD)

- Every external claim (fact, number, trend, named system) traces to a listed reference or is explicitly project-own content (your design, your data, your scope). Neither → do not write the sentence.
- A work mentioned in the prose must appear in the reference list. You either reference it or do not mention it; name-dropping an unlisted work reads as a fabricated reference.
- A factual sentence without a citation is a defect: add the source, mark it as project-own characterization, or cut it. Hedging is not evidence.
- Never gesture at unnamed empirical support. "Studies have shown", "research indicates", "it is widely accepted" without a named study = Evidence-Use failure.
- Direct quotes are verbatim from the source text at a stated version, with a locator (section or page), and are attributed in prose per the citation style. Quotes may not import the source's own citation markers in a way that collides with the host document's apparatus. Quote density stays sparing: short phrase quotes may be frequent where they carry precision, full-sentence quotes default to at most one per section unless venue or corpus practice says otherwise.
- A source's own limitations are reported as its own: "the paper's own limitations acknowledge...", not as your measured finding.
- Verbatim quotation is rationed across the document: a quotation's third use defaults to paraphrase or a shortened re-quote with a pointer back; a second use in a different chapter paraphrases. Key statistics are exempt and repeat as consistency anchors.
- A paraphrase never exceeds what the source actually shows. Overstatement is a misrepresentation-level defect, not a style issue.
- Numbers carry provenance. Distinguish measured (your data), reported (a source's data, attributed: "X reports"), derived (your arithmetic from source numbers, labelled as derived), and hypothetical (never cite as evidence).
- Cite only what was actually read, at the depth read. Abstract-only access supports abstract-level claims only; a citation resting on abstract-only access says so at first use.
- Venue, year, authors, and DOI come from authoritative records (DOI registry, proceedings, OpenReview, the published record), never from search snippets or arXiv sidecar fields. Unconfirmed = mark UNVERIFIED; never guess.
- Describe verification at the level actually performed; an unchecked lookup is stated as unchecked, never implied as run.
- Absence and novelty claims ("no published work...") require a documented search basis. Write the scoped negative ("our search of [databases], covering [period and scope], found no..."), name the nearest prior work, and state your delta. Never claim a vacuum.
- A source's self-promotional claims ("the first comprehensive survey") are framed as self-claims: "X describes itself as...".

## 2. Claim strength and hedging (HARD)

Match the verb to the evidence. The ladder:

| Evidence | Calibrated verbs |
|---|---|
| Proof, definition, established fact | demonstrates, establishes, is |
| Systematic review, meta-analysis | indicates, shows |
| Several converging empirical studies | suggests |
| Single empirical study | one study found |
| Theoretical or position argument | argues, proposes |
| Speculation, open question | may, remains open |

- Empirical results never "prove". Definitional and established facts never "may".
- Your own methods and data are reported unhedged: "latency was measured", not "appeared to be".
- Polishing improves syntax and voice; it never strengthens a claim. Under reviewer pressure, narrow the claim rather than delete qualifiers.
- Universal claims (every, all, none, only) are checked against every cited source before they ship; if the evidence does not cover the universal, narrow the claim.
- Temporal claims (A enabled B, "current", "recent", "latest") are anchored to dates or versions, or not written.
- Version discipline: the same work's preprint and version of record are different sources for citation purposes. Year, venue, DOI, and quotes never mix across versions. Quote locators name the version they were verified against.
- Mechanism and effect are named separately. If a source reports an effect and hypothesizes a mechanism, attribute each precisely; never merge them into a hybrid the source did not state.
- Internal consistency: if a source is internally inconsistent (two counts, two numbers), pick the authoritative one, state its level (abstract vs table vs section), and stay with it.
- Hedge findings, not actions. "This study examines X" (committed); "the results suggest Y" (hedged).
- A claim is scoped to the regime it was evaluated in (model, hardware, population, period); extending a result beyond its evaluated regime is a claim-strength defect, not a wording problem.

## 3. Terminology and conciseness (HARD with stated exemptions)

- One concept, one name. Synonym cycling (students → learners → participants within one text) is a defect in academic writing; repetition of the correct term is a virtue.
- Paired variants that genuinely differ (outcome judgment vs adjudication) are defined together at first use and used consistently thereafter.
- Abbreviations expand at first use: full term (SHORT), short form thereafter. Exemptions: units, product names, bibliographic venue abbreviations, and text inside quotes.
- Technical terms are defined or citation-supported at first use. Informal words ("a lot of", "very good", "things", "stuff", "we can see that") have no place in academic prose.
- Wordy phrases go direct:

| Wordy | Direct |
|---|---|
| in order to | to |
| due to the fact that | because |
| a large number of | many |
| at the present time | now |
| it is important to note that | cut, or state the point |
| in the event that | if |
| has the ability to | can |
| with regard to | regarding |
| in spite of the fact that | despite |
| conduct an investigation of | investigate |

- Vague terms go specific:

| Vague | Precise |
|---|---|
| many studies | several studies (named, cited) |
| a significant impact | the actual number |
| in recent years | since 2020 / over the past five years |
| it is well known that | cite the source or cut |

- Pronouns have one unambiguous antecedent; "this", "it", "various", "many" without a referent are defects.
- No ambiguous readings, no dangling modifiers. If a sentence parses two ways, rewrite it.

## 4. Register, tense, and formality (HARD tables and mechanical rules; JUDGMENT application)

- Register by discipline:

| Discipline | Register | Voice | Credible because of |
|---|---|---|---|
| Natural / applied sciences | Formal, impersonal | Passive common for methods, active for findings | Precision of measurement |
| Engineering / CS | Formal, problem-solution | Passive for methods, active for contributions | Reproducibility |
| Social sciences | Formal, theory-informed | Active; first person for researcher decisions | Limitation transparency |
| Humanities | Formal, argument-driven | First person acceptable; active | Depth of source engagement |
| Medicine / health | Formal, evidence-hierarchy conscious | Passive for methods, active for findings | Reporting-guideline adherence |
| Education | Formal, practice-oriented | Active; first person for reflexive practice | Stakeholder-aware evidence |

- Third person unless the discipline allows first person. No slang, no exclamations, no contractions, no rhetorical questions as a stylistic device (research questions are governed by §5).
- One spelling variant per document (e.g., US: -ize, -or), enforced in a final sweep.
- Tense:

| Context | Tense |
|---|---|
| Reporting a study's findings | Past ("Smith found") |
| Ongoing states, definitions | Present ("the theory posits") |
| Methodology | Past |
| Results | Past |
| Discussion (interpreting) | Present |
| Conclusion (implications) | Present / future |

- Formality keeps what helps the reader: signposting and qualification that carry meaning stay; decoration goes (see the catalogues file for the detection lists).

## 5. Structure and narrative (JUDGMENT; the meta-commentary ban, the RQ-wording identity rule, and the figure-reference rule are HARD)

- Paragraph shape: topic sentence (a promise the paragraph keeps) → cited evidence → interpretation (analysis, not restatement) → link forward.
- Transitions signal the relation (cause, contrast, addition), not sequence alone. Topic sentences carry most of the inter-paragraph flow; transition words only where the relation is not already obvious; a second transition for the same relation on one page is a cut candidate. Transitions between sections are complete sentences, not single words.
- Relation vocabulary, used only where the relation needs spelling out: addition (moreover, furthermore, similarly), contrast (however, nevertheless, whereas, conversely), cause (therefore, consequently, thus), example (for instance, specifically, such as), sequence (subsequently, meanwhile), concession (although, despite, granted that).
- Cross-references to other sections name the target first, with the number in parentheses, at low density; navigation never substitutes for argument.
- The reader's four questions stay answerable at every point: Where am I? Why am I here? What do I take away? Where next? Any one unclear → revise.
- Clarity Test per paragraph: if deleting it breaks the argument, it is load-bearing and earns multiple drafts; if it only adds context, keep it short; if nothing is lost, cut it. Vary investment across paragraphs; equal-weight prose is the AI signature.
- Section so-what: Introduction earns care (stakes, gap); Literature review earns "what is missing"; Methodology earns trust; Results lead with the finding; Discussion answers the gap with the delta; Conclusion leaves one sentence that carries the contribution.
- Introduction rhetoric (CARS): Move 1 territory (centrality claims cited, synthesized not listed) → Move 2 niche (licensed by the review; scoped negative, never a universal) → Move 3 occupy (purpose sentence concrete, active, answering exactly that niche; RQ stated verbatim). Failure modes: funnel too wide, literature dump, unlicensed gap, buried purpose, niche-purpose mismatch, findings leaked into the preview.
- RQ or hypothesis wording is identical everywhere it appears: posed in the Introduction, used in Methods, answered in Conclusion; wording that drifts between appearances is a defect. Intro may preview the contribution type; numbers stay in Results.
- Counter-evidence is engaged, never avoided. The strongest objection gets a fair statement and a response in its committed rebuttal strategy; limitations and alternative interpretations are acknowledged in the text, not silently skipped.
- Meta-commentary ("this section will discuss") is banned; roadmap sentences appear only where the venue or document convention expects them. Section numbering and figure references are output-facing only; internal working labels never enter academic prose.
- Structure patterns are audited at document scale: mirror structure (the same section template repeated where the content asks otherwise), binary-contrast habits and false dichotomies, and colon-list sequences that fragment the argument. Fix only a real clarity or support problem; parallel structure that aids comparison stays.
- Every figure and table is numbered per the venue convention, captioned, and referenced in the text; a figure inserted without an in-text reference and a statement of what it shows is a defect.
- When the word budget tightens, cut adjective stacks and meta-commentary first, never content.

## 6. Citation mechanics (HARD; apply the chosen style)

- In-text numbers or keys appear in strictly increasing order of first appearance for numeric styles; appending a new reference mid-document requires renumbering or a style-compliant fix, never out-of-order reuse.
- Zero orphans in both directions: every in-text citation resolves to a list entry; every list entry is cited in text.
- Consecutive sentences drawing on one source cluster under one anchor citation; a sentence combining distinct claims from one source may cite each. Citing every sentence is noise.
- A claim taken secondhand names both layers, "(Original, Year, as cited in Citing, Year)", and secondhand sources are used sparingly; never present a work as read firsthand when it was encountered through another source.
- The citation entry line makes the venue self-evident per the style's own convention (e.g., "in Proc." for IEEE conference entries). Preprints are labelled preprints, never dressed as venue publications. No extra editorial labels ("clearly-marked") on top.
- Placeholders state exactly what is pending (authors, pages, venue); they never impersonate complete entries.
- Mechanical checks (orphans, DOI resolution, format lint) may be scripted; whether a citation supports the sentence it sits in is a judgment check no script can do.

## 7. Abstract and keywords (HARD except keyword selection, which is JUDGMENT)

- Structure follows the venue or document template; absent one, use: background → problem → objectives → methodology → key findings → conclusion.
- Findings carry specific numbers. "Results will be discussed" and vague findings ("significant results were found") are banned.
- Zero citations and zero undefined abbreviations inside the abstract.
- Keywords are terms a searcher would type (method + domain coverage); they complement the title rather than copying it, and use established vocabulary.

## 8. Consistency under editing (HARD)

- Deleting an item (a deliverable, a sub-claim, a source) triggers a sweep of every count, cross-reference, and repeated mention in the same pass. A count that no longer matches its list is a defect.
- A revision that touches one claim re-checks the surrounding claims that cite the same sources. Local fixes that create remote contradictions are defects.
- Write what IS: no date stamps, no campaign narrative ("in this revision we"), no session vocabulary. Version facts (which version was read, verification state) are current state and stay.
- Before shipping, sweep for leftover scaffolding: unresolved placeholder markers, draft annotations, unexpanded acronym first-uses, and pronouns whose antecedent drifted during revision.

## 9. Revision decisions (JUDGMENT)

- Reviewer "unclear" → rewrite for clarity; zero cost.
- "Missing reference" → add only if it genuinely fills a gap, not as citation promotion.
- "Wrong method" → if defensible, justify with evidence; if not, change.
- "Not novel" → reframe the contribution within the documented search; never inflate the novelty claim.
- "Too long" → apply the Clarity Test paragraph by paragraph.
- Under pressure for more confidence: strengthen the writing, never the claim (see Claim strength).

## 10. What you do not fix here

AI-pattern detection (vocabulary lists, structure patterns, punctuation tells, sentence-shape tells) lives in `anti-ai-tell-catalogues.md`. Load it when generating or revising prose; it is descriptive, not prescriptive: patterns are tells in combination or repetition, discipline-standard terms are exempt, and over-correction that damages sound prose is itself a defect.
