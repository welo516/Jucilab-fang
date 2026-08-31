# Fang Revision Evolution Patterns

Use this reference when deciding how advisor comments were likely repaired across versions. This file is derived only from the skill-internal annotation corpus in `references/fang-advisor-annotation-corpus.md` and `references/fang-advisor-annotation-corpus.json`.

It compares the available version chains:

- `PMIPSGA`: `0928-PMIPSGA-fang .pdf` -> `PMIPSGA_0123_fang.pdf` -> `PMIPSGA_0214_fang.pdf`
- `COFTGA`: `COFTGA_251218-fang.pdf` -> `COFTGA_260115_fang.pdf` -> `COFTGA_260131-fang.pdf`
- `MMGA_BN`: `MMGA_BN-fang.pdf` -> `MMGA_BN (12)-fang.pdf` -> `【0416】MMGA_BN(1) -fang.pdf`

Important: a later version is not automatically correct. Treat a change as stronger evidence only when it moves toward the advisor's repeated principles and is not contradicted by later comments.

## How To Use These Patterns

1. Diagnose the current passage using `fang-advisor-distillation.md`.
2. If the issue resembles a past version problem, use the matching evolution pattern below to choose a repair direction.
3. Rewrite with the base `jucilab-fang` field-common wording rules, not with the raw wording of the version diff.
4. If a later version still contains the same logic break, flag it as unresolved rather than copying it.

## High-Value Evolution Patterns

### 1. Generic field opening -> task-specific opening

Observed in `PMIPSGA_0123_fang.pdf` -> `PMIPSGA_0214_fang.pdf`.

Earlier pattern:

`Bayesian network structure learning (BNSL) from data is a well-known challenge in the field of artificial intelligence. The genetic algorithm (GA) is effective for searching the optimal BN structure.`

Later direction:

`Bayesian network structure learning (BNSL) is a challenging task in representation and reasoning under uncertainty.`

Distilled lesson:

- Remove broad, textbook-like field framing when it does not prepare the method.
- Start closer to the actual task and the reader's technical concern.
- Avoid adding a separate sentence such as "GA is effective" unless the next sentence explains why GA is the selected method for the paper's bottleneck.

Use when:

- The abstract or introduction starts with broad AI/data-mining importance.
- A method family is praised before its necessity is established.

### 2. Overly ornate method naming -> clearer mechanism naming

Observed in `COFTGA_251218-fang.pdf` -> `COFTGA_260115_fang.pdf`.

Earlier pattern:

`collaborative optimization genetic algorithm with feedback-driven adaptive constraint and two-stage mutation`

Later direction:

`Constraint-Search Collaborative Genetic Algorithm (CS-CGA)`

Distilled lesson:

- Replace long stacked names with a shorter name that exposes the main relation.
- The name should identify the central mechanism, not list every component.
- If a term such as `feedback-driven` is used, the manuscript must visibly maintain that concept across abstract, method, figures, and experiments.

Use when:

- The method name contains multiple modifiers.
- The advisor could ask "what is this word?" or "where is the feedback?"

### 3. Vague limitation -> explicit failure mode

Observed in `COFTGA_251218-fang.pdf` -> `COFTGA_260115_fang.pdf`.

Earlier pattern:

`limitations of the constraint-then-search framework and the redundancy of fitness evaluation`

Later direction:

`existing hybrid methods typically treat constraint and structural search as decoupled stages, resulting in the permanent loss of actual dependencies, while redundant fitness evaluations further limit exploration efficiency`

Distilled lesson:

- Name the failure mode, not only the broad limitation.
- Explain what is lost, where it is lost, and why the loss matters.
- A limitation should prepare the proposed mechanism directly.

Use when:

- The text says a method has "limitations" without explaining the mechanism of failure.
- The proposed method appears as a fix before the reader understands the defect.

### 4. Mechanism hidden in one long sentence -> separated collaboration logic

Observed in `COFTGA_260115_fang.pdf` -> `COFTGA_260131-fang.pdf`.

Earlier pattern:

`CS-CGA that couples the constraint-based and score-based search phases into a co-evolutionary framework. Within the framework, ...`

Later direction:

`CS-CGA. The collaboration is realized through two core improvements: ...`

Distilled lesson:

- Do not force the method name, mechanism, and all functions into one sentence.
- State the method, then explain the mechanism through a small numbered or paired structure.
- If the contribution has two core improvements, make the two-part structure visible.

Use when:

- A sentence carries the method name, framework claim, mechanism, and effect all at once.
- The advisor might call the sentence "too advanced" or hard to understand.

### 5. Strong result claims -> bounded result claims

Observed in `COFTGA_251218-fang.pdf` -> `COFTGA_260131-fang.pdf`.

Earlier pattern:

`order-of-magnitude improvements in computational efficiency ... robust transferability`

Later direction:

`outperforms state-of-the-art algorithms in terms of structural accuracy and convergence, while also exhibiting robust transferability`

Distilled lesson:

- Remove result strength that is not clearly supported in the abstract.
- Keep the comparison target and metric category.
- Prefer bounded claims tied to evaluated dimensions.

Use when:

- The abstract claims large improvements without enough context.
- Results are phrased as broad superiority instead of tested-scope superiority.

### 6. Component noun precision

Observed in `MMGA_BN (12)-fang.pdf` -> `【0416】MMGA_BN(1) -fang.pdf`.

Earlier pattern:

`In the mutation, ...`

Later direction:

`In the mutation operator, ...`

Distilled lesson:

- Prefer the precise algorithmic component noun.
- Use `operator`, `strategy`, `mechanism`, `framework`, `constraint`, or `evaluation` only when that noun matches the actual object.

Use when:

- The text uses a broad process word but the paper is describing a concrete algorithmic component.

### 7. Author-centered result wording -> method-centered result wording

Observed in `MMGA_BN (12)-fang.pdf` -> `【0416】MMGA_BN(1) -fang.pdf`.

Earlier pattern:

`our method achieves ...`

Later direction:

`the proposed method achieves ...`

Distilled lesson:

- In final manuscript text, prefer method-centered subjects when they improve technical tone.
- Do not overuse `we` or `our` in algorithm descriptions and results summaries.

Use when:

- Several consecutive sentences start from the authors rather than the method, operator, or results.

### 8. Dataset/condition wording must be exact

Observed through comments on `PMIPSGA_0214_fang.pdf`.

Advisor comments ask which dimensions are `large dataset` and which are `high-dimensional network`, and clarify table markers such as `OOM` and `N/A`.

Distilled lesson:

- Do not use experimental labels as self-evident.
- Define dimensions and markers near the table or results paragraph.
- Distinguish the condition the method targets from the condition under which it remains applicable.

Use when:

- The result paragraph uses labels such as `large-scale`, `high-dimensional`, `OOM`, `N/A`, `one day`, or time units without explanation.

## Unresolved Or Weak Evidence Patterns

### PMIPSGA parallel motivation remains risky

The later `PMIPSGA` abstract still says that GA-based BNSL involves redundant calculations and time consumption, then moves to a full-process parallel method. However, one advisor comment explicitly says that if the problem is only time consumption, parallelism is not necessarily justified.

Do not copy this as a complete repair. A stronger repair should explain why the computation is decomposable or redundant in a way that makes parallelism the right design choice.

Preferred repair direction:

`large-scale/high-dimensional BNSL -> repeated fitness evaluation and decomposable search/evaluation operations -> redundant computation and scalability bottleneck -> parallel MI constraints, fitness evaluation, and GA search in Spark`

### COFTGA "co-evolutionary" term is risky

`COFTGA_260115_fang.pdf` introduced `co-evolutionary framework`, but a later comment questions `co-evolutionary` and asks not to use too many near-synonyms. The next version avoids making `co-evolutionary framework` the central abstract phrase.

Do not use `co-evolutionary` unless the paper explicitly matches recognized co-evolutionary algorithm usage.

Preferred repair direction:

Use `collaboration`, `coupled constraint and score-based search`, or another field-common phrase that describes the actual mechanism.

## Skill Update Implications

Add these checks when revising new manuscripts from the group:

- Does a later draft merely shorten the text, or did it repair the actual evidence-chain break?
- Is a new term introduced as a real mechanism or just as a more impressive label?
- Did the rewrite make the central relation visible, such as constraint-search collaboration or parent-set decomposition?
- Did result wording become more bounded and metric-specific?
- Did method wording become more component-precise?
- Did figure explanations move from idea-level description to visible module/edge/variable description?
