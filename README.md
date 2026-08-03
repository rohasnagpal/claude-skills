# Claude Skills for Legal Work

Eighteen Agent Skills that give Claude a defined role, a structured workflow, and a consistent output format for legal tasks — case analysis, contract review, due diligence, litigation drafting, compliance, evidence work, negotiation, and dispute resolution.

Each skill is a self-contained folder containing a `SKILL.md` and any supporting files. Install skills individually, install the full collection in Claude Code, or fork and adapt them to your practice.

---

## Install

### claude.ai / Claude Desktop / Cowork

First, enable **Code execution and file creation** under **Settings → Capabilities**. Then download the `.zip` file for the skill you want from [`dist/`](dist) and upload it under **Customize → Skills → + → Create skill → Upload a skill**. Claude will use it automatically when a request matches.

### Claude Code

Skills are just folders. Clone the repo and copy what you want:

```bash
git clone https://github.com/rohasnagpal/claude-skills.git
cp -r claude-skills/skills/case-law-analyst ~/.claude/skills/
```

Or install all eighteen:

```bash
cp -r claude-skills/skills/* ~/.claude/skills/
```

For a team, commit the folders into your project's `.claude/skills/` so everyone working in that repo gets them.

### Claude API

Upload the `.zip` archive through the Skills API, or upload the files individually while preserving their common top-level skill directory. Skills run in a sandboxed container, so everything they need must be bundled.

---

## The skills

Click a skill name to download its upload-ready ZIP. Editable source folders are available under [`skills/`](skills).

| Skill file | Skill details |
|---|---|
| [`adversarial-reviewer`](dist/adversarial-reviewer.zip) | A red-team pass on a position or draft — assumption audit, contrary evidence, the opponent's best case, a stress-test table, and a repair plan |
| [`arbitrator`](dist/arbitrator.zip) | Runs a structured hearing of both sides and delivers a reasoned ruling |
| [`case-law-analyst`](dist/case-law-analyst.zip) | A litigation-ready case note in ten parts — snapshot, material facts, procedural history, issues, holding, ratio, obiter, reasoning, how to use it, how to distinguish it |
| [`chronology-builder`](dist/chronology-builder.zip) | A source-linked timeline with confidence ratings, date conflicts, key periods, and deadlines to verify |
| [`client-intake-interviewer`](dist/client-intake-interviewer.zip) | A structured intake record — facts, dates, documents held and needed, preliminary issues, and conflict flags |
| [`contract-reviewer`](dist/contract-reviewer.zip) | A 41-parameter CUAD-style clause table with evidence citations, plus risk analysis, missing protections, and negotiation priorities |
| [`courtroom-coach`](dist/courtroom-coach.zip) | Prepares someone to present their own case: structure, evidence, the hardest questions, and conduct on the day |
| [`cross-examination-strategist`](dist/cross-examination-strategist.zip) | A document-linked cross plan — themes, contradiction map, leading question sequence, risk controls, admissions to lock in |
| [`devils-advocate-legal`](dist/devils-advocate-legal.zip) | Attacks their position the way opposing counsel would, then gives a candid fight-or-settle read |
| [`due-diligence-reviewer`](dist/due-diligence-reviewer.zip) | Executive red flags, document checklist, consents and approvals, closing actions, and a severity-rated risk register |
| [`evidence-organizer`](dist/evidence-organizer.zip) | An issue-linked evidence index with privilege risk, admissibility questions, exhibit candidates, and gaps |
| [`legal-explainer`](dist/legal-explainer.zip) | Explains a legal term, clause, or process in plain language, with jurisdiction caveats and honest complexity |
| [`legal-researcher`](dist/legal-researcher.zip) | A research plan and issue map — what to verify, where to search, and which authorities to check. Deliberately does not invent citations |
| [`legal-strategist`](dist/legal-strategist.zip) | Maps realistic options — negotiate, demand letter, mediate, sue, complain, walk away — with time, cost, and leverage for each |
| [`litigation-drafting-assistant`](dist/litigation-drafting-assistant.zip) | A controlled first draft of notices, pleadings, affidavits, applications, or submissions, with unverified facts left as visible placeholders |
| [`mediator`](dist/mediator.zip) | Facilitates a conflict conversation in four modes — both sides, interview, live session, or preparing one party |
| [`regulatory-compliance-analyst`](dist/regulatory-compliance-analyst.zip) | An obligation matrix with triggers, owners, deadlines and evidence, plus filings, controls, and a phased action plan |
| [`settlement-evaluator`](dist/settlement-evaluator.zip) | BATNA/WATNA, a risk-adjusted range with the arithmetic shown, a leverage map for both sides, and settlement options |

---

## Design principles

These skills are built around the ways AI legal work actually goes wrong.

**No invented authorities.** `legal-researcher` names the *category* of authority to look for rather than producing case names, citations, and paragraph numbers from memory. Where a case is supplied by the user, it is cited precisely; where it is not, it is flagged for verification.

**Placeholders over plausible detail.** `litigation-drafting-assistant` marks every unverified fact, date, citation, and annexure as `[DATE — verify from Annexure __]` rather than filling the gap with something realistic. A draft with twenty visible placeholders is safe; one with two invented specifics is not.

**Established, alleged, assumed, unverified — kept apart.** Most weak legal positions fail because an assumption was carried forward as a fact. Several of these skills separate the categories explicitly.

**Sources on every finding.** Clause, paragraph, exhibit, or filename. A finding without a source cannot be verified, disclosed against, or argued.

**Limits stated, not buried.** Where a data room is incomplete, a judgment is only an excerpt, or a jurisdiction has not been established, the skill says what cannot be assessed instead of producing confident output anyway.

---

## Jurisdiction

The skills are jurisdiction-neutral by default and will ask where the matter sits before making jurisdiction-specific statements.

`case-law-analyst` ships with a reference file on Indian precedent doctrine — binding force by court and bench, per incuriam and sub silentio, dismissal of an SLP in limine, Article 142 orders, tribunal hierarchy — which it consults when analysing Indian judgments. The same pattern extends to any jurisdiction: add a file under `references/` and point to it from `SKILL.md`.

---

## Use responsibly

AI-generated legal work must be checked by a qualified lawyer before it is relied on, filed, or sent.

Confirm the applicable jurisdiction. Verify every authority and citation independently. Do not upload confidential or privileged material to any service your organisation has not approved. Nothing produced by these skills is legal advice, and using them does not create a lawyer-client relationship.

---

## Adapting them

Every skill is a single markdown file. Open it, change the output structure, add your firm's house style, bundle your own precedents under `references/`, and reinstall. That is the whole workflow.

If you add a jurisdiction reference file or a materially improved skill, pull requests are welcome.

---

## Credits

Based on the [AI prompts for lawyers](https://www.rohasnagpal.com/ai-prompts-for-lawyers.php) collection by Rohas Nagpal.
