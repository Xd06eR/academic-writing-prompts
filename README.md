# Academic Writing Prompts

A skill for writing academic prose in English that survives a meticulous reader. The user owns the argument; the skill handles structure, sourcing discipline, register, hedging, and the editorial passes that keep prose honest.

## How it works

Entry is any-phase: bring nothing, a topic, scattered materials, or a finished draft. The skill reads what arrived and starts at the matching capability. Each capability is standalone and runs on whatever it is given.

Five capabilities:

- **capture-argument**: grills a vague intent into a structured argument (thesis, sub-claims, counterarguments, evidence needed) before any drafting.
- **lit-review**: builds the source map, counter-evidence list, and gap register an argument stands on; refuses to fabricate and flags what verification owes.
- **outline**: commits structure to paper: literal topic sentences, per-section word allocations, and evidence placements the draft renders without re-deciding.
- **draft**: renders committed structure into prose with calibrated hedging, discipline-correct register, and citations attached at claim creation.
- **refine**: audits a draft against a seven-criterion checklist, fixes defects surgically, and runs the fresh-context anti-AI-tells audit.

A guided flow chains the five for users who bring nothing: capture, then an optional lit-review, then outline, then an interleaved draft/refine loop that closes with a whole-document pass and the tell-audit. Checkpoints after capture and after the source map keep the user in charge of the argument.

## The rules library

Two files govern all writing work:

- `references/writing-principles.md` is the contract: sourcing, claim strength, hedging ladder, register, citation mechanics, consistency. Every rule carries a `HARD` (violation is a defect) or `JUDGMENT` (prompt, not quota) label.
- `references/anti-ai-tell-catalogues.md`: the detection layer for machine-pattern prose, loaded before prose is generated or revised.

Venue and document-owner rules outrank the principles file; venue typesetting conventions outrank the catalogues.

## Research pairing

This repo is the writing base of a two-repo setup: the research base is [academic-research-skills](https://github.com/Imbad0202/academic-research-skills). Rigorous research (multi-agent search, verification infrastructure, systematic pipelines) lives there; the lit-review capability here stays lightweight and cedes large systematic work to it.

## Examples

`skills/examples/` holds synthetic worked examples (generated prose, unchecked citation rows) as shape references only.

## Companion resources

The anti-AI-tell catalogues are informed by these resources:

- [`humanizer` by blader](https://github.com/blader/humanizer)
- [`stop-slop` by hardikpandya](https://github.com/hardikpandya/stop-slop)
- [`tropes.fyi`](https://gist.github.com/ossa-ma/f3baa9d25154c33095e22272c631f5a1)

## Installation

```bash
git clone https://github.com/Xd06eR/academic-writing-prompts.git
mkdir -p ~/.claude/skills/academic-writing
cp -r academic-writing-prompts/skills/. ~/.claude/skills/academic-writing/
```

Restart the client after install; the skill loads on `/academic-writing` or when the model routes to it. Each capability file also runs alone as a portable prompt: paste it into any chat together with `references/writing-principles.md` (add `references/anti-ai-tell-catalogues.md` for draft and refine) to run that capability by hand.

## Archive

`archive/` is frozen; nothing live reads from it.

## License

MIT: see [`LICENSE`](LICENSE).
