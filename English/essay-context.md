# Essay Context (Shared Preamble)

> Fill this block **once per essay**. Paste it at the top of every skill invocation (`1-capture-argument`, `2-lit-review`, `3-outline`, `4-draft`, `5-refine`). The skills assume these fields are defined.

## Essay Context

- **Topic and stance:** [State the topic + your stance in one sentence. Example: "Social media use harms university students' academic performance, primarily through procrastination."]
- **Discipline:** [e.g. Psychology, Computer Science, Literature, Sociology]
- **Target audience:** [e.g. undergraduate peers, course professor, academic journal reader]
- **Citation style:** [e.g. APA 7, MLA 9, Chicago 17, IEEE]
- **Scope:**
  - `full` — produce the whole essay in one run, OR
  - `section:<name>` — produce one section only (e.g. `section:literature_review`, `section:introduction`, `section:body_paragraph_2`)
- **Word count (full essay):** [e.g. 2000]
- **Word count (responsible section):** [Required if scope is `section:*`. Otherwise leave blank.]
- **Specific requirements:** [Any constraints the prof set: theoretical framework to use, sources to include, sources to avoid, formatting quirks, rubric items. Leave blank if none.]
- **Background context (your angle):** [Your personal experience, prior reading, course themes, or perspective that should colour the writing. This is what stops the essay from sounding like generic AI output.]

## Notes for the assistant

- Treat the user (the student) as the **owner of the argument**. Your role is to structure, polish, and stress-test their thinking — never to invent a stance for them.
- If any field above is blank or vague, ask up to **3 clarifying questions** before producing output. After 3 questions, proceed with reasonable assumptions and flag them.
- If `scope` is `section:*`, reference the rest of the essay only by allusion (e.g. "as established in the literature review"). Do not write other sections.
- Citation hygiene: never invent citations. If you cannot back a claim with a verifiable source (URL/DOI), either drop the claim, mark it `[needs citation]`, or rewrite without it.
