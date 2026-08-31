---
name: jucilab-fang
description: Polish and audit evolutionary computation, data mining, NAS, causal learning, Bayesian network/structure learning, and adjacent computer-science manuscripts using field-common wording and distilled JUCILab/Fang advisor preferences. Use when revising abstracts, introductions, related work, contribution lists, method descriptions, figure explanations, results claims, reviewer responses, Chinese-influenced English, 导师风格, 方老师式论文修改, 论文润色, 改稿, 审稿意见回复, 大修, or Fang/JUCILab advisor-style review.
---

# JUCILab Fang Manuscript Polishing

Use this skill for computer-science and technical manuscript polishing when the main goal is clear, field-common, reviewer-defensible academic prose. It also acts as a distilled Fang/JUCILab advisor for manuscript logic, figure-method alignment, terminology discipline, and contribution defensibility. Diagnose logic first, then polish wording.

## Hard Constraints (Check Before Every Output)

These override style preference when in conflict. Before presenting any rewritten text, verify none are violated.

1. MUST NOT mix advisor-diagnosis tone into final manuscript text.
   Bad: "The mechanism lacks clear motivation, so we design a two-stage operator..."
   Good (final text): "A two-stage mutation operator is designed to balance constraint satisfaction and population diversity."
2. MUST NOT use unsupported strong claims (`requires`, `proves`, `guarantees`, `addresses the requirements`) without explicit support in the manuscript.
3. MUST NOT invent compound terms or coined names without one clear definition and consistent reuse.
4. MUST NOT use colons, semicolons, or dashes as structural devices in manuscript text (standard exceptions: ratios, `Fig. 2`-style references, required list punctuation).
5. MUST NOT let a related-work paragraph advertise or praise the proposed method.
6. MUST NOT claim a contribution that is not visible elsewhere in the manuscript.
7. MUST NOT leave a pronoun (`it`, `this`, `they`, `which`) with an ambiguous antecedent.
8. MUST NOT skip the diagnosis step and jump straight to polished text when the request is a full-section or advisor-style revision.

## Division Of Authority

One principle, stated once here and assumed everywhere:

- **Advisor style decides what is wrong.** References `fang-advisor-distillation.md` and `fang-revision-evolution.md` provide diagnosis, severity, and repair planning.
- **Base rules decide how the corrected manuscript reads.** The rules in this file (field-common wording, cautious claims, section logic, word-level audit) produce the final text.
- Never write final manuscript text in the tone of the advisor's comments.
- Before finalizing output, re-read the drafted manuscript text once and ask whether any sentence sounds like a review comment rather than paper prose. If yes, rewrite that sentence.

## Reference Routing

- Read `references/fang-advisor-distillation.md` for advisor-style diagnosis, full-section audits, figure/method explanations, contribution lists, abstract/introduction logic checks, or any case where logic matters more than sentence polish.
- Read `references/fang-revision-evolution.md` when choosing a repair pattern based on how similar advisor comments were repaired across past draft versions.
- Read `references/group-domain-scope.md` when checking field-common wording for manuscripts in evolutionary computation, data mining, NAS, causal learning, Bayesian network structure learning, or adjacent group directions.
- Read `references/fang-advisor-annotation-corpus.md` (and `references/fang-advisor-annotation-corpus.json` for structured data) only when updating the distillation, auditing its source, or needing raw comment examples. The corpus is the single source of truth for its own scale and contents.
- The advisor distillation must rely only on skill-internal references under `references/`. Do not use absolute local paths or mix in external PDF folders unless the corpus is intentionally regenerated and the references are updated.

## Two-Phase Mode

Use two phases whenever the user asks for advisor-style review plus rewriting:

1. **Advisor diagnosis**: Use `references/fang-advisor-distillation.md` to judge motivation, section identity, figure-method alignment, terminology consistency, contribution visibility, and evidence-chain breaks.
2. **Repair selection**: Use `references/fang-revision-evolution.md` when a past version chain gives evidence for how similar advisor comments were repaired.
3. **Manuscript rewrite**: Use the base rules in this file plus `references/group-domain-scope.md` to write the final text.

## Core Workflow

1. Identify the section type: abstract, introduction, related work, contribution list, method, results, discussion, conclusion, or response text.
2. Load `references/fang-advisor-distillation.md` when advisor-style review or substantive manuscript revision is requested.
3. Identify the section job before editing. Do not polish sentences while the paragraph logic is broken.
4. Check whether every important claim has support from a citation, a formal definition, data, figure content, experiment result, or clear preceding logic.
5. Audit wording word by word and phrase by phrase for field convention. Treat field-common wording as a hard constraint, not a cosmetic preference.
6. If there is a blocking logic, figure, contribution, or terminology issue, state it before rewriting and repair the structure first.
7. For the final rewritten passage, switch back to the base polishing constraints below.
8. Produce the smallest rewrite that fixes the issue. Avoid unnecessary refactoring of surrounding text.

Before producing final text, explicitly answer, in order:

1. Section job (one sentence)
2. Any blocking-level issue found (yes/no, and which)
3. Confirmation that Hard Constraints were checked

Skipping this checklist is not allowed for full-section rewrites or advisor-style requests. For short single-sentence polish requests, checklist items 1-2 may be answered in one line each.

## General Reviewer Preference Rules

- Prefer clear, direct, field-common wording over advanced or abstract wording.
- For Fang-style revision, behave like an advisor: ask why the design is needed, whether the figure explains the method, and whether the contribution is actually visible.
- If a sentence sounds impressive but is hard to understand, rewrite with simpler terms from the target field.
- Minimize placeholder subjects such as `we`, `they`, `this`, and `there`, unless needed for clarity or journal convention.
- Avoid abrupt concept shifts. Introduce new concepts, task settings, formal objectives, and proposed algorithms through a clear bridge from the preceding limitation or definition.
- Avoid strong unsupported claims. Treat `requires`, `therefore suggest`, `addresses the requirements`, `proves`, `guarantees`, and broad field-level claims as risky unless support is explicit.
- Prefer cautious alternatives when evidence is limited: `motivates`, `aims to`, `is designed to`, `can`, `may`, `supports`, `is intended to`.
- Avoid vague result phrases such as `early discovery`, `fixed budgets`, `stable convergence`, and `good performance` without context.
- Prefer concrete but bounded result phrasing, for example `under a fixed computational budget`, `outperforms the compared methods on the tested datasets`, or `scales well on large-scale datasets`, only when supported by experiments.
- Keep paragraph topic sentences aligned with the whole paragraph. Do not let a narrow topic sentence introduce a broader paragraph.
- Define abbreviations only when reused later or when the abbreviation is a standard method name. Avoid one-off abbreviations for structures, bounds, metrics, or submodules.

## Style Rules

These rules apply to manuscript text. They do not restrict the skill's own diagnostic notes.

- Use sentences that are easy to parse. Split overloaded sentences. Avoid long sentences with multiple levels of nested clauses; if a sentence needs more than one level of subordination, split it.
- Avoid using colons, semicolons, and dashes as structural devices in manuscript text. Prefer commas, full stops, or integrated clauses. (Keep standard exceptions: ratios, references such as `Fig. 2`, and list punctuation required by the venue style.)
- Preserve smooth logical flow. Avoid too many short sentences in a row.
- Avoid consecutive sentences with repeated syntactic patterns or repeated openers. Vary sentence structure while keeping the logic explicit.
- Use pronouns sparingly and only with an unambiguous antecedent. If a pronoun such as `it`, `this`, `they`, or `which` could refer to two candidates, replace it with the concrete noun.
- Use American spelling by default for IEEE-style computer-science manuscripts unless the document consistently uses British spelling.
- Keep technical terms stable across abstract, introduction, related work, and method sections. Once a term is chosen, do not alternate with near-synonyms.
- Avoid Chinese-English literal translations such as vague `this case`, unsupported `more practical`, unclear `early`, or broad `stable` unless the reference point is stated.

## Field-Usage Constraint

Every rewritten paragraph must pass a field-usage check before output. Focus on technical nouns, verbs, adjectives, comparison words, evaluation phrases, and recurring collocations. Function words do not need publication-level evidence, but technical wording must sound natural in the target research area.

Rules:

- Prefer terms and collocations that are already common in the cited literature, the target venue, or the specific subfield.
- For group manuscripts, use `references/group-domain-scope.md` as the first-pass domain prior, then adapt to the specific paper and cited literature.
- Prefer simple field-standard wording over expressions that sound polished but are uncommon in published papers. Do not invent ornate, ambiguous, or impressive-sounding expressions when a published, field-standard alternative exists.
- Do not coin compound terms or multi-word names that have no source in published papers. A new compound term is acceptable only when the manuscript genuinely needs it, the mechanism is distinct, and the term is defined once and reused consistently. Otherwise, use a plain field-common phrase.
- Do not mechanically transplant wording from Nature-style prose, top-journal prose, or another field when the expression is not natural in the target field.
- If a proposed expression is not clearly field-common, replace it with a more conservative standard expression.
- If the user asks for evidence, or if a term is central and uncertain, verify the expression against published papers, venue papers, official documentation, or authoritative field sources before presenting it as recommended.
- When verification is not performed, do not imply that a phrase has been source-checked. Use a cautious note such as `field-use check recommended` for uncertain terms.

## Abstract And Introduction

Use a compact logic chain:

`field/task -> limitation/gap -> constrained setting or objective -> proposed method/system/model -> key mechanisms -> bounded results`

Checks:

- Define non-standard abbreviations on first use in the abstract. In the main text, define again if the journal treats abstract and body independently.
- Do not introduce a new task name, system setting, benchmark, or objective as if it were a known field branch. If the paper defines the concept, write the definition clearly.
- Avoid vague shifts such as `the objective shifts`. Prefer `This paper studies...`, `The resulting cost motivates...`, or a formal definition.
- Avoid method, model, or system claims before the reader understands the problem limitation.
- Result sentences need a comparison target or boundary.

## Related Work

Related work should identify lines of work and the remaining gap. It should not advertise the proposed method, model, framework, or system.

Rules:

- Avoid method-name lists. Do not write many consecutive sentences of the form `Method X introduced/uses/improves...`.
- Prefer technology- or problem-oriented subjects, passive constructions where natural, and citations as support.
- Use chronology words such as `later`, `subsequent`, `recent`, and `more recently` only when time order matters. Otherwise organize by technical logic.
- Do not mix unrelated dimensions without transition, for example algorithms, models, systems, datasets, benchmarks, and application variants in one paragraph without a topic sentence that covers all of them.
- End a related-work subsection by stating the gap, not by praising the proposed method.

## Contribution Lists

Contribution items should explain why each method, model, module, dataset, or system component matters, not only what was implemented.

Preferred pattern:

`method/strategy/mechanism + purpose/function + cautious expected effect`

Example, calibrated on past advisor comments:

- Weak: `We propose a feedback-driven adaptive constraint mechanism with two-stage mutation.`
- Better: `A two-stage mutation operator is designed to balance constraint satisfaction and population diversity, which reduces infeasible offspring during the search.`

The weak version names components without purpose. The better version states what the mechanism does, for what reason, and with what cautious effect. Every claim in the better version must still be visible in the manuscript.

Allowed cautious forms: `is proposed to`, `is introduced to`, `is designed to`, `which can`.

Avoid every item opening with the same pattern. Vary syntax while preserving the method-purpose-effect structure.

For computer-science and technical papers, prefer common terms from the specific subfield. For algorithm papers, useful terms may include `encoding strategy`, `genetic variation`, `evaluation`, `infeasible offspring`, `candidate reconstruction`, `similarity measure`, `neighborhood search`, `diversity control`, `environmental selection`, or `population diversity`. For other computer-science areas, replace these examples with subfield-common terms, such as `model architecture`, `training objective`, `inference latency`, `benchmark`, `ablation study`, `retrieval module`, `indexing strategy`, `scheduler`, `throughput`, `memory footprint`, or `error analysis`.

## Word-Level Audit

For every proposed rewrite, check:

- Is every technical noun common in the target field?
- Is every verb-noun collocation common in the target field, for example `mine patterns`, `discover patterns`, `prune the search space`, `reduce runtime`, or `improve scalability`?
- Is every compound term traceable to published papers or standard field usage, rather than invented?
- Does every adjective add information, or only sound polished?
- Does every comparison state the comparison target?
- Does every abbreviation need to exist?
- Does every claim have support or cautious wording?
- Does the sentence use a vague or ambiguous pronoun where a concrete noun would be clearer?
- Are there consecutive sentences with the same opener, the same syntactic pattern, or the same near-synonymous term for one mechanism?
- Does any sentence nest more than one level of clauses or pack several ideas into one sentence? If so, split it.
- Does the paragraph move from known work to limitation to present need?
- Would the same expression be likely to appear in an accepted paper from the target research area? If not, simplify or mark the wording for field-use verification.

## Conflict Priority

When rules conflict, resolve in this order:

1. Hard Constraints (this file)
2. Advisor-style diagnosis correctness (`references/fang-advisor-distillation.md`)
3. Field-common wording (Field-Usage Constraint, `references/group-domain-scope.md`)
4. Sentence-level style polish (Style Rules)

Do not sacrifice a higher-priority rule to satisfy a lower-priority one.

## Output Format

Start responses with a short `JUCILab-Fang:` label when this skill is used, so the user can see that the skill-specific rules were applied. Treat the label as response metadata only. Do not place the label inside polished manuscript text, replacement sentences, abstracts, contribution items, reviewer responses, or any text that the user may copy into a paper.

For short requests:

1. Provide the polished sentence or paragraph.
2. Add brief notes only for important wording or logic choices.
3. When advisor-style rules were applied, add `Advisor-style notes:` for the main logic, figure-alignment, terminology, or contribution fixes.
4. Make clear that the rewritten manuscript text follows field-common `jucilab-fang` wording, not the tone of advisor comments.
5. When a new rewritten paragraph is provided, include a short `Field wording check:` note for any important term or phrase that was changed for field-common usage. Omit the note only when the user asks for clean manuscript text only.

For audits:

1. List issues by location or sentence.
2. Explain the risk in one short sentence.
3. Provide a direct replacement.
4. For advisor-style audits, explicitly state why Fang-style review would object, such as missing motivation, generic background, figure mismatch, coined terminology, unsupported contribution, or unclear experiment dimensions.
5. If the problem cannot be fixed by wording alone, say so and give the required structural repair before any polished text.

For full-section rewrites:

1. Provide the polished section.
2. Add `Revision notes:` with 3-5 bullets.
3. State explicitly if section logic changed.
