---
name: jucilab-writing
description: Polish, review, and audit computer-science manuscripts (evolutionary computation, data mining, NAS, causal learning, Bayesian network structure learning, and adjacent areas) with field-common wording, advisor-style diagnosis, and reviewer-defensible claims. Use when revising abstracts, introductions, related work, contribution lists, method descriptions, figure explanations, results claims, reviewer responses, Chinese-influenced English, 导师风格, 方老师式论文修改, 论文润色, 改稿, 去AI味, 审稿意见回复, 大修, or Fang/JUCILab advisor-style review.
---

# JUCILab Writing — Manuscript Polishing and Advisor-Style Review

Advisor-style judgment decides what is wrong; the base rules in this file decide how the corrected manuscript reads. Diagnose logic first, then polish wording. Final manuscript text must never imitate the tone of advisor comments.

## Task Routing

Classify the request before reading any reference file, and load only what the table requires. Never load the corpus for ordinary revision tasks.

| Task | Read | Notes |
|---|---|---|
| Short polish or translation of a sentence/paragraph | this file; plus the domain pack on domain match | smallest sufficient rewrite; science issues flagged out-of-band (Hard Constraint 9) |
| Language-only cleanup / de-AI-tone | this file; plus the domain pack on domain match | Language-Only Mode boundaries below; preserve numbers, citations, and claim strength |
| Substantive revision (abstract/intro/contributions/method/figure text) | `references/review.md`; plus the domain pack when the domain matches | diagnosis before rewriting |
| Full review, pre-submission check, reviewer response | `references/review.md` + `references/examples.md`; plus the domain pack | build the cross-section fact table; report P0/P1/P2 |
| Corpus or rule maintenance | `references/corpus.md` + Governance section | follow the rule-tier process |

Domain detection applies to every row above — `this file` never excludes the matching domain pack: causal discovery, DAG learning, or Bayesian network structure learning manuscripts → also read `references/domain-causal-bnsl.md` (its claim boundaries are what make out-of-band science checks possible, including in language-only mode). Other fields (NLP, systems, ML infrastructure, and so on) → base rules only; never transplant BNSL vocabulary into them. The domain pack adds field facts only; the claim-hygiene rules below are field-independent and always apply.

## Hard Constraints

These override style preference when in conflict. Verify none are violated before presenting any rewritten text.

1. MUST NOT mix advisor-diagnosis tone into final manuscript text.
   Bad: "The mechanism lacks clear motivation, so we design a two-stage operator..."
   Good (final text): "A two-stage mutation operator is designed to balance constraint satisfaction and population diversity."
2. MUST NOT use unsupported strong claims (`requires`, `proves`, `guarantees`, `ensures`, `addresses the requirements`) without explicit support in the manuscript. See Claim Hygiene for downgrades.
3. MUST NOT invent compound terms or coined names without one clear definition and consistent reuse.
4. MUST NOT use colons, semicolons, or dashes as structural devices in manuscript text (standard exceptions: ratios, `Fig. 2`-style references, required list punctuation).
5. MUST NOT let a related-work paragraph advertise or praise the proposed method.
6. MUST NOT claim a contribution that is not visible elsewhere in the manuscript.
7. MUST NOT leave a pronoun (`it`, `this`, `they`, `which`) with an ambiguous antecedent.
8. MUST NOT skip the diagnosis step and jump straight to polished text when the request is a full-section or advisor-style revision.
9. Science boundary: if a sentence is fluent but scientifically wrong, language-only mode keeps the sentence unchanged and flags the issue outside the manuscript text; substantive revision may correct it explicitly. Never silently keep a wrong scientific claim unflagged, and never silently change the research positioning.

## Claim Hygiene

Strong claims need explicit support in the manuscript. Common downgrades:

- `guarantees recovery` → `allows excluded candidate edges to be reconsidered` (mechanism claim) or `improves structural recovery on the evaluated benchmarks` (results claim)
- `proves` / `ensures` → `shows` / `is consistent with`, unless a theorem or formal result is cited
- `significantly improves` → report the statistical test, or `achieves a higher mean ...` with the numbers
- `best performance on all datasets` → `the best performance among the compared methods on all tested datasets`
- `ensures practical applicability` → `supports the practical applicability`

Vague result phrases (`good performance`, `stable convergence`, `early discovery`, `fixed budgets`) need a metric category, a comparison target, and a tested scope. `can guarantee` still contains `guarantee`; hedging must match the missing evidence instead of blanket-softening every sentence.

## Language-Only Mode

When the user asks only for language cleanup or de-AI-tone:

1. Preserve sentence meaning, information, numbers, citations, conditions, negation, and claim strength.
2. Fix only located language problems: empty importance, hollow gaps (`not fully explored` without a failure mode), decorative modifiers (`novel`, `effectively`, `dramatically`), abstract subjects, repeated openers, Chinese-English collocations (`this case`, `more practical`, `time consumption`).
3. Keep `we`, passive voice, necessary lists, math colons, and genuine `not A but B` distinctions; they are not errors. Do not judge text as AI-generated from word choice.
4. Do not adjust section structure or borrow cleanup to add motivation or experiments.
5. Reverse-check before output: every added technical noun and number must trace to the source; every removed condition must not change the claim. If it cannot be traced, revert it or mark it as pending confirmation.

## Style And Field-Usage Essentials

- Split overloaded sentences; avoid more than one level of nested clauses. Keep logical flow; avoid machine-gun short sentences.
- Keep terms stable across abstract, introduction, related work, method, and figures; never alternate near-synonyms for one mechanism.
- Define abbreviations only when reused later or when standard.
- Use American spelling by default for IEEE-style manuscripts unless the document is consistently British.
- Technical wording must sound natural in the target subfield: prefer collocations already common in the cited literature or venue; do not coin ornate names; do not transplant Nature-style prose across fields. When verification is not performed, say `field-use check recommended` instead of implying a source check.
- Avoid abrupt concept shifts; bridge new concepts from the preceding limitation or definition.

## Reviewer Preference Essentials

- Motivation chain: `task difficulty -> specific bottleneck -> why existing methods fail -> why this mechanism fits -> proposed design`. A method must not appear before its necessity.
- Prefer cautious verbs when evidence is limited: `motivates`, `aims to`, `is designed to`, `supports`. Prefer method-centered subjects (`the proposed method achieves...`) over strings of author-centered sentences; passive voice is acceptable.
- Avoid excessive future tense in method and experiment text; check tense section-wide.
- Compress generic background that could appear in any paper of the area; spend the space on the paper-specific limitation.
- Result sentences need a comparison target or boundary. Prefer precise component nouns (`mutation operator`, not `mutation`).

## Output Conventions

Start responses with the `JUCILab-Writing:` label as metadata only; never place it inside manuscript text the user may copy.

- **Short polish:** copyable text first; notes only for meaning-affecting choices; keep the reply compact for one-paragraph requests. Add `Field wording check:` only when an important term changed.
- **Substantive review:** format issues as `位置—问题—为何影响结论—具体修复`; then the revised text; then items requiring author confirmation.
- **Full review:** report P0 scientific/factual errors, P1 argument/experiment gaps, P2 expression issues. Build the cross-section fact table (network/dataset counts, budgets, metric direction, figure-abstract consistency); on conflict, report both sources instead of choosing by majority. `references/examples.md` shows the expected format.
- **LaTeX:** preserve commands, formulas, label/ref/cite mapping, revision macros, and highlighting; do not delete revision marks or claim compilation without the source project.

## Pre-Output Checklist

Before producing final text, explicitly answer:

1. Section job (one sentence)
2. Blocking-level issue found (yes/no, and which)
3. Hard Constraints checked (yes)

Items 1-2 may be one line each for short single-sentence polish; the checklist is mandatory for full-section rewrites and advisor-style requests.

## Governance

- The corpus (`references/corpus.md`, `references/corpus.json`) is the single source of truth for advisor annotations. Do not state corpus statistics from memory.
- Rule tiers: `observed` / `adopted` / `author-preferred` / `field fact`. A single revision never upgrades to a global rule; rules may be downgraded or removed when a new manuscript or reliable source challenges them.
- Distilling new corpus material requires updating the corpus and `references/review.md` together; do not mix in external PDF folders unless the corpus is intentionally regenerated.
