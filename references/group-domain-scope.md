# Group Domain Scope

Use this reference when applying `jucilab-fang` to the group's manuscripts. It defines the default domain prior for field-common wording, method framing, and claim boundaries.

This is a flexible scope, not a hard exclusion rule. The group may occasionally write in adjacent small directions. When a manuscript is outside the core areas, keep the same review logic but verify field wording against that manuscript's own target literature.

## Core Direction

The group's center of gravity is algorithmic computer-science research, especially:

- evolutionary computation
- genetic algorithms and evolutionary search
- data mining
- neural architecture search (NAS)
- causal learning
- Bayesian network structure learning (BNSL)
- Bayesian-network-related structure, scoring, and inference problems

Treat evolutionary computation as the methodological backbone when GA, population, mutation, crossover, selection, diversity, or search-space exploration appears. Treat data mining, NAS, causal learning, and BNSL as application/problem contexts that require their own field-common terms.

## Default Review Priorities For This Group

When reviewing or rewriting group manuscripts, prioritize:

1. **Why this search or optimization strategy is needed**  
   Explain why the problem structure motivates an evolutionary, mining, NAS, causal, or Bayesian-network approach.

2. **What bottleneck the method addresses**  
   Name the specific bottleneck, such as search-space size, redundant evaluation, constraint loss, expensive scoring, infeasible candidates, poor diversity, premature convergence, or scalability.

3. **How the mechanism changes the search process**  
   Make the actual operation visible: initialization, encoding, variation, constraint relaxation, parent-set construction, scoring, caching, parallel evaluation, architecture mutation, or causal relation filtering.

4. **Where the evidence appears**  
   Tie claims to figures, formulas, algorithms, ablation studies, benchmarks, runtime, memory, accuracy, structural quality, or scalability results.

5. **Whether terminology is field-common**  
   Prefer terms likely to appear in evolutionary computation, data mining, NAS, causal learning, and BNSL papers. Avoid ornate labels or coined names unless the mechanism is genuinely distinct and consistently defined.

## Field-Common Term Families

Use these as safe default families, adapting to the exact paper.

### Evolutionary computation

- `population`
- `individual`
- `candidate solution`
- `encoding strategy`
- `fitness evaluation`
- `selection`
- `crossover operator`
- `mutation operator`
- `genetic variation`
- `environmental selection`
- `population diversity`
- `premature convergence`
- `exploration and exploitation`
- `search space`
- `constraint handling`
- `infeasible candidate`
- `repair strategy`
- `neighborhood search`

### Data mining

- `pattern mining`
- `candidate generation`
- `search-space pruning`
- `utility evaluation`
- `upper bound`
- `support`
- `sequence database`
- `transaction database`
- `scalability`
- `runtime`
- `memory consumption`
- `large-scale datasets`

### NAS

- `architecture search`
- `search space`
- `cell-based search space`
- `architecture encoding`
- `candidate architecture`
- `performance estimation`
- `weight sharing`
- `surrogate evaluation`
- `search cost`
- `evolutionary NAS`
- `mutation operator`
- `selection strategy`

### Causal learning and Bayesian networks

- `Bayesian network`
- `directed acyclic graph`
- `conditional independence`
- `constraint-based search`
- `score-based search`
- `hybrid structure learning`
- `parent set`
- `candidate parent set`
- `superstructure`
- `structure score`
- `score decomposability`
- `mutual information`
- `conditional mutual information`
- `structure learning`
- `causal relationship`
- `dependency`
- `redundant fitness evaluation`
- `score memoization`
- `search-space restriction`

## Wording Preferences

Prefer precise mechanism phrases:

- `restrict the search space`
- `reduce redundant evaluations`
- `relax superstructure constraints`
- `construct candidate parent sets`
- `preserve promising structures`
- `improve population diversity`
- `accelerate fitness evaluation`
- `parallelize fitness evaluation`
- `balance exploration and exploitation`
- `improve the search for potential dependencies`
- `maintain structural accuracy while reducing runtime`

Avoid or verify:

- ornate names that combine many modifiers
- repeated near-synonyms for one mechanism
- broad claims such as `robust transferability` without evidence
- vague result terms such as `good performance`
- unsupported claims that a mechanism `guarantees`, `proves`, or `solves` a broad problem
- generic phrases such as `effective method`, `important significance`, or `advanced framework`

## Claim Boundaries

Use cautious claims unless the manuscript provides direct evidence.

Prefer:

- `is designed to`
- `aims to`
- `can reduce`
- `supports`
- `improves on the tested datasets`
- `shows better scalability under the tested settings`
- `reduces redundant evaluations in the evaluated cases`

Avoid:

- `guarantees`
- `proves`
- `completely solves`
- `universally applicable`
- `achieves robust transferability` without transfer experiments

## Transfer To Minor Directions

For occasional adjacent directions:

1. Keep the advisor diagnostic model: motivation, traceability, identity, naming, evidence.
2. Keep the base manuscript rewriting rules: field-common wording, cautious claims, stable terminology.
3. Replace only the domain lexicon with terms from the target literature.
4. Do not force GA/BNSL terminology into a paper where it does not belong.
