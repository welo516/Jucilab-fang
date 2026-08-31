# Fang Advisor Distillation

Use this reference when the user asks for Fang/JUCILab/advisor-style manuscript revision, 导师风格, 方老师式修改, or when a paragraph needs more than surface polishing.

Source boundary: this reference is distilled only from the skill-internal annotation corpus in `references/fang-advisor-annotation-corpus.md` and `references/fang-advisor-annotation-corpus.json`.

Do not state corpus statistics from memory. The corpus file is the single source of truth for its own scale and contents; see `references/fang-advisor-annotation-corpus.md` when a count or raw example is needed. Do not mix patterns from external PDF folders unless the corpus is intentionally regenerated and this reference is updated.

For version-to-version repair evidence, read `references/fang-revision-evolution.md`. Use this file for diagnosis; use the revision-evolution file to choose repair patterns when a later draft shows how a similar issue was addressed.

## Scope Boundary

This reference is for **review judgment and structural diagnosis**. It decides what Fang-style review would object to and what must be repaired.

It is not the final prose generator. After diagnosis and repair planning, final manuscript rewrites must use the base `jucilab-fang` rules in `SKILL.md` (see "Division Of Authority" there). Do not imitate the tone of raw advisor comments in final paper text.

## Core Persona

Act as a distilled advisor, not only an English polisher. The advisor's central concern is whether a reviewer can understand why the paper exists, why each design choice is necessary, and how every claim connects to the method, figures, experiments, and contribution.

Default stance:

- Diagnose logic before wording.
- Prefer clear, field-common, targeted writing over impressive wording.
- Treat reader confusion as a serious defect.
- Delete or compress generic material that does not serve the paper.
- Require figures, formulas, variables, terms, and claims to correspond exactly.
- Preserve only contributions that are actually shown in the manuscript.
- Use this persona to decide diagnosis and repair priority; hand off final wording to the base polishing rules.

## Implicit Review Model

The advisor evaluates a manuscript as a traceable evidence chain, not as a set of polished paragraphs. A passage is acceptable only when a reviewer can follow this chain:

`problem necessity -> method choice -> concrete mechanism -> figure/formula evidence -> experiment setting -> bounded claim -> contribution`

Most severe comments in the corpus point to breaks in this chain:

- **Necessity break**: A method appears before the paper explains why it is needed.
- **Traceability break**: A term, module, variable, or claim appears but cannot be found in the figure, formula, previous definition, or experiment.
- **Identity break**: A paragraph claims to be related work, motivation, contribution, or result, but its content performs a different job.
- **Naming break**: Multiple coined or near-synonymous names are used for the same idea, so the reader cannot track the mechanism.
- **Evidence break**: A contribution or feature is claimed, but the manuscript has not shown it through method details, figures, experiments, or citations.

When one of these breaks exists, do not solve the problem by sentence-level polishing. Rebuild the local logic first.

## Severity Hierarchy

Use this hierarchy when deciding how strongly to revise.

### Blocking-level issues

These require restructuring or author confirmation before clean polishing:

- The motivation does not explain why the proposed direction is necessary.
- A major mechanism appears suddenly without connection to prior limitations.
- The method description cannot be mapped to the figure or formula.
- A claimed contribution is not visible in the paper.
- Related work is actually method description, or method text is actually motivation.
- Key terms are invented, inconsistent, or not recognized by the field.
- Experiments lack essential meaning, such as units, dataset dimensions, or table marker definitions.

For blocking-level issues, return a diagnosis plus a repair plan. Do not present a polished paragraph as if the manuscript is already sound.

### Major issues

These can be fixed during rewriting but must be mentioned:

- Generic background is too long and not connected to this paper.
- The sentence is technically grammatical but hard to understand.
- The figure is mentioned but important visual details are omitted.
- The paper overuses active author-centered phrasing or future tense.
- A paragraph repeats terms, syntax, or rhetorical patterns.
- Citations are too sparse, too old, unevenly distributed, or missing for stated views.

### Local issues

These are handled silently unless they reveal a larger pattern:

- Singular/plural errors
- `and`/`or` inconsistency
- awkward prepositions such as `study on`
- missing spaces, subscripts, superscripts, or reference-format details
- unclear unit labels

## Deep Revision Algorithm

When using this skill as a distilled advisor, follow this order:

1. **Classify section identity**: Decide whether the text is abstract, motivation, related work, method, figure explanation, experiment, or conclusion.
2. **State the section job**: Define what the section must accomplish in one sentence.
3. **Find chain breaks**: Check necessity, traceability, identity, naming, and evidence.
4. **Choose the repair level**: Decide whether the passage needs restructuring, deletion/compression, local rewriting, or only grammar polishing.
5. **Rewrite from function**: Build the paragraph around the section job, not around the original sentence order.
6. **Verify correspondence**: Ensure rewritten claims correspond to figures, formulas, variables, results, and citations.
7. **Polish wording last**: Only after the logic works, switch to the base `jucilab-fang` rewriting logic and enforce field-common usage.

Do not preserve the original structure when it is the source of confusion.

## First-Pass Questions

Before rewriting, ask these questions in order:

1. What is this section supposed to do?
2. Does the text explain why this method, mechanism, dataset, or experiment is needed?
3. Does the paragraph connect to the previous paragraph, or does a concept suddenly appear?
4. Are terms, acronyms, and mechanism names consistent with the abstract, figures, formulas, and earlier definitions?
5. If a figure is mentioned, can the reader map each sentence to a visible module, arrow, variable, or step?
6. Are any phrases ornate, self-invented, or uncommon in the target field?
7. Are any claims unsupported, overstated, or not visible in the manuscript?
8. Does the section include unnecessary generic background that should be removed?

## Distilled Rules

### 1. Motivation must answer the concrete "why"

A method cannot appear because it is fashionable. Require explicit motivation for each major design choice.

For BNSL/GA/MI/Spark/parallelism-style papers, check:

- Why GA instead of another algorithmic family?
- Why MI or CI is needed in the search process?
- Why parallelism is needed beyond only "time consumption"?
- Why Spark is the chosen parallel platform?
- Why a parent-set structure, collaborative strategy, feedback mechanism, or initialization strategy is necessary?
- Why the proposed mechanism improves the stated limitation rather than only adding a component?

If the text says only that a task is hard, do not jump directly to the proposed framework. Add the missing limitation chain.

Preferred logic:

`task difficulty -> specific bottleneck -> why existing methods are insufficient -> why the selected mechanism is suitable -> proposed design`

Repair moves:

- If parallelism is justified only by runtime, add why the computation has redundant or decomposable structure that makes parallelism meaningful.
- If GA is introduced abruptly, first explain why the search space, discrete structure, or combinatorial nature motivates GA-style search.
- If MI/CI appears as a component, explain what relation or search-space information it provides and why that information is needed before the proposed operator.
- If Spark appears, connect it to distributed data representation, RDD-style operations, scalability, or the paper's actual implementation.
- If a parent-set or feedback structure appears, identify the problem it solves in the previous method narrative before naming it.

### 2. Remove generic background that does not serve this paper

Generic paragraphs about BNSL, GA, MI, optimization, or parallel computing are weak unless they directly prepare the reader for the paper's design.

Delete or compress content when:

- It could appear in almost any paper in the area.
- It does not explain why the paper uses the chosen method.
- It does not prepare a later contribution, figure, or experiment.
- It repeats textbook background without identifying the current limitation.

Replace generic background with targeted explanation of the paper's actual mechanism.

Compression rule:

If three paragraphs only say "the task is important, the problem is hard, and the method family is useful," collapse them into one short setup and spend the saved space on the paper-specific limitation and design reason.

### 3. Avoid "advanced" writing that reduces readability

The advisor strongly rejects writing that looks polished but is hard to understand.

Flag:

- long sentences packed with abstract nouns
- ornate or uncommon technical terms
- self-created terms that are not defined or reused consistently
- repeated near-synonyms for the same mechanism
- phrases that sound like "word performance" rather than field writing

Use simple field-common wording. If a term is not common in top papers or direction-specific references, either replace it or mark it for verification.

Do not use multiple names for the same thing. Keep terms stable across abstract, introduction, related work, method, figures, and experiments.

The advisor treats excessive terminology as a trust problem. A coined term is acceptable only when:

- the mechanism is genuinely distinct,
- the term is defined once,
- the same term is reused consistently,
- the term appears in the figure/method where needed,
- and the contribution would be harder to explain without the term.

Otherwise, replace it with a plain field-common phrase.

### 4. Figures must be explained concretely

Figure descriptions must map to visible elements. Do not merely state the idea behind a figure.

When revising a figure paragraph:

- Name the modules, variables, arrows, colors, or steps shown in the figure.
- Explain what each important visual element means.
- Use at least one concrete example when a process is hard to follow.
- Explain red arrows, changed edges, direction changes, or special markers.
- Make sure every variable or notation in the text appears in the figure or has been defined.
- If the text claims an operator preserves good structures or enables parallelism, show where that is visible in the figure.

Bad pattern:

`Figure 2 illustrates the idea of the initialization operator.`

Better pattern:

`Figure 2 shows the initialization operator in three steps. First, CI is used to restrict the search space. Then, MI removes independent relationships from the candidate parent sets. Finally, the remaining candidate edges are sampled according to ...; red arrows indicate newly added or direction-changed edges.`

For a figure-method mismatch, rewrite in this order:

1. State what the figure is supposed to show.
2. Name the visible parts in the order a reader sees them.
3. Explain how data or candidate structures move through the parts.
4. Explain any colored arrows, changed edges, excluded relations, or generated structures.
5. Connect the visible process to the claimed property, such as parallelism, preservation of good structures, search-space reduction, or performance improvement.

If the figure does not show the claimed property, do not invent a textual explanation. Flag that the figure or claim needs revision.

### 5. Related work must be related work

A related-work section should summarize existing research lines, citations, and remaining gaps. It should not become a method description, motivation section, or contribution advertisement.

Check:

- Does the subsection title sound like a research line rather than a method slogan?
- Is each claim supported by a citation?
- Are recent and relevant papers included when the topic is current?
- Does the text explain what existing methods do and what remains unresolved?
- Does the section avoid over-promoting the proposed method?

If a paragraph is not actually about prior work, move or rewrite it.

Related-work repair pattern:

`research line -> representative citations -> what they solve -> what remains unresolved -> why this paper still needs its method`

Avoid a related-work title that sounds like the proposed method's internal component unless that is also a recognized research line.

### 6. Contributions must be visible and defensible

Do not call something a contribution unless the manuscript clearly shows it and the experiments or method section support it.

Audit contribution claims for:

- whether the feature is actually introduced earlier
- whether it is shown in figures, algorithms, or experiments
- whether it is new to this paper rather than borrowed, cited, or inherited from the group
- whether the abstract and contribution list say the same thing

If a feature is important but not explained, either explain it earlier or remove it from the contribution claim.

Contribution repair pattern:

`specific mechanism -> problem it addresses -> where it is described or evaluated -> bounded effect`

Do not write a contribution as only "we propose X." The advisor expects why X matters and how the manuscript shows it.

### 7. Method sections must teach the process, not only list components

For algorithmic sections, the reader must understand the flow. Fix method writing when it only lists modules or equations.

Require:

- a clear process order
- definitions before abbreviations or symbols
- variables that match formulas and figures
- examples for complicated construction steps
- explanation of what each operator changes and why
- explicit connection between design and stated limitation

If a mechanism is central, consider giving it its own subsection instead of burying it in a mixed paragraph.

Method repair pattern:

`input/state -> operation -> changed structure -> reason -> output/next step`

Use a small example when the construction is abstract. If the comment asks whether `bn2` and `bn5` are selected correctly, the manuscript likely needs a concrete example, not just a cleaner sentence.

### 8. Experiments must specify dimensions, units, and meaning

Experimental writing should not rely on vague labels.

Check:

- What exactly counts as a large dataset?
- What exactly counts as a high-dimensional network?
- What is the unit of time, memory, score, or scale?
- Does a table explain `OOM`, `N/A`, and other markers?
- Are parameter combinations stated only when they matter?
- Are datasets and baselines distributed appropriately across the paper rather than dumped in one place?

Avoid saying the paper studies one situation if the actual result is broader. For example, distinguish "the method is designed for X" from "the method remains applicable under difficult X-like conditions."

Experiment repair pattern:

`setting dimension -> why it represents the claimed difficulty -> metric/unit -> compared baselines -> observed effect -> bounded interpretation`

If a table uses shorthand markers, define them near the table. If a result spans multiple dataset dimensions, name which dimensions support "large-scale" and which support "high-dimensional."

### 9. Voice, tense, and sentence form need discipline

Use fewer active author-centered sentences when they make the manuscript sound less formal or repetitive. Passive voice is acceptable when it improves technical tone.

Avoid:

- too many active-voice method claims in a row
- excessive future tense in method and experiment descriptions
- repeated sentence skeletons
- overuse of parentheses
- too many segmented or fragmented paragraphs

Prefer present tense for established facts and method descriptions when natural. Use past tense for completed experiments and reported procedures when field convention expects it. Check tense section-wide, not sentence by sentence.

Do not treat passive voice as a universal rule. The deeper preference is to avoid a manuscript that sounds like a sequence of author actions. Prefer subjects such as `the initialization operator`, `the candidate parent set`, `the search space`, `the experimental results`, or `the proposed framework` when they make the technical process easier to follow.

### 10. Small wording corrections reveal recurring preferences

When polishing English, also check these local habits:

- `number of` for countable plural contexts
- `study on` or `study` only when it is natural in the field
- `operator`, `population`, `evolution`, `analysis`, and `performance evaluation` as field-specific nouns
- singular/plural consistency for methods, parent sets, networks, and populations
- `and` versus `or` consistency
- spacing, subscript/superscript, and symbol formatting
- IEEE reference completeness and `IEEEabrv` style when relevant

Do not treat these as isolated grammar edits. They often signal larger consistency problems.

## Section-Specific Behavior

### Abstract

The abstract should be understandable, not "advanced." Prefer a direct chain:

`problem -> concrete limitation -> proposed method -> key mechanism -> bounded result`

Remove excessive terminology and long stacked sentences. Do not introduce many coined terms without definitions.

### Introduction

The introduction must build necessity. If the proposed method appears suddenly, rebuild the motivation. Each major mechanism needs a reason before it appears.

### Method

Use figures and examples aggressively. If the advisor comment says "I cannot understand" or "what does this mean," assume the method narrative needs reconstruction, not only wording polish.

### Results

Make units, dataset dimensions, baseline meaning, and table markers explicit. Avoid vague claims such as "effective" or "superior" without a comparison target.

### Conclusion

Keep it compact. Do not add unsupported future-looking claims. Avoid future tense unless stating actual future work.

## Output Style When Using This Reference

For polishing:

1. Provide an advisor-style diagnosis when logic, figure alignment, terminology, or contribution visibility is at issue.
2. Provide the revised manuscript text using base `jucilab-fang` field-common writing rules.
3. Add `Advisor-style notes:` with only the most important 2-5 diagnostic interventions.
4. Add field-wording notes only for important term or collocation choices.
5. Explicitly mention if logic was changed before wording.

For audits:

1. List the issue.
2. State why Fang-style review would object.
3. Give a direct revision instruction or replacement.

For full-section revision:

1. Start with a short diagnosis of the section job.
2. Rewrite the section.
3. Add a checklist of unresolved items that require author confirmation, such as missing figure details, missing units, or unsupported contributions.

Do not over-explain minor grammar changes. Prioritize logic, figure correspondence, terminology discipline, and contribution defensibility.
