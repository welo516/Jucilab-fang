# Substantive Review Toolbox

Load this file for substantive revision, advisor-style review, full review, or reviewer responses. It decides what Fang-style review would object to and what must be repaired; final manuscript text still follows the base rules in `SKILL.md` and never imitates advisor tone.

Provenance: distilled only from the skill-internal corpus (`references/corpus.md`, `references/corpus.json`; 228 text annotations over the PMIPSGA, COFTGA, and MMGA_BN version chains). Repair patterns in Section 7 come from those version chains. A later version is not automatically correct; treat a change as evidence only when it moves toward the repeated advisor principles.

## 1. Evidence-Chain Model

The advisor evaluates a manuscript as a traceable evidence chain, not as polished paragraphs. A passage is acceptable only when a reviewer can follow:

`problem necessity -> method choice -> concrete mechanism -> figure/formula evidence -> experiment setting -> bounded claim -> contribution`

Five break types; when one exists, sentence-level polishing cannot fix it — rebuild the local logic first:

- **Necessity break**: a method appears before the paper explains why it is needed.
- **Traceability break**: a term, module, variable, or claim cannot be found in the figure, formula, prior definition, or experiment.
- **Identity break**: a paragraph claims to be related work, motivation, contribution, or result, but performs a different job.
- **Naming break**: multiple coined or near-synonymous names for the same idea.
- **Evidence break**: a contribution or feature is claimed but never shown through method details, figures, experiments, or citations.

## 2. Severity Hierarchy

**Blocking-level** (return diagnosis plus repair plan; do not present polished text as if the manuscript were sound):
motivation does not explain necessity; a major mechanism appears suddenly; method text cannot be mapped to the figure or formula; a claimed contribution is invisible; related work is actually method description (or vice versa); key terms invented, inconsistent, or unrecognized; experiments lack essential meaning (units, dataset dimensions, table markers).

**Major** (fix during rewriting, must be mentioned): generic background not connected to this paper; grammatical but hard to understand; figure mentioned but key visual details omitted; overuse of author-centered phrasing or future tense; repeated terms, syntax, or rhetorical patterns; citations too sparse, old, or uneven.

**Local** (handle silently unless part of a pattern): singular/plural, `and`/`or` consistency, awkward prepositions (`study on`), spacing, subscripts/superscripts, reference-format details, unclear unit labels.

## 3. Deep Revision Algorithm

1. Classify section identity: abstract, motivation, related work, method, figure explanation, experiment, or conclusion.
2. State the section job in one sentence.
3. Find chain breaks (the five types above).
4. Choose the repair level: restructure, delete/compress, rewrite locally, or grammar only.
5. Rewrite from function: build the paragraph around the section job, not the original sentence order.
6. Verify correspondence: claims ↔ figures, formulas, variables, results, citations.
7. Polish wording last, switching to the base rules in `SKILL.md`.

First-pass questions, in order: What is this section supposed to do? Why is this method/mechanism/dataset needed? Does the paragraph connect to the previous one? Are terms consistent with abstract, figures, formulas, definitions? If a figure is mentioned, can each sentence map to a visible element? Are any phrases ornate or uncommon in the field? Are any claims unsupported or invisible? Is there generic background to remove?

## 4. Distilled Rules

### 4.1 Motivation must answer the concrete "why"

A method cannot appear because it is fashionable. For BNSL/GA/MI/parallelism-style papers, check: why GA instead of another algorithmic family? Why MI or CI in the search? Why parallelism beyond "time consumption"? Why Spark? Why a parent-set, feedback, or initialization structure? Preferred logic: `task difficulty -> specific bottleneck -> why existing methods are insufficient -> why the selected mechanism is suitable -> proposed design`.

Repair moves: if parallelism is justified only by runtime, add why the computation is decomposable or redundant; if GA appears abruptly, first explain why the discrete combinatorial space motivates GA-style search; if MI appears, say what relation information it provides and why that is needed; if Spark appears, connect it to the data representation and actual implementation; name the problem a parent-set or feedback structure solves before introducing it.

### 4.2 Remove generic background that does not serve this paper

Delete or compress content that could appear in almost any paper of the area, does not explain the method choice, or repeats textbook background without a current limitation. If three paragraphs only say "important, hard, useful family," collapse them into one short setup and spend the space on the paper-specific limitation.

### 4.3 Avoid "advanced" writing that reduces readability

Flag long noun-stacked sentences, ornate or uncommon terms, self-created terms, and repeated near-synonyms. A coined term is acceptable only when the mechanism is genuinely distinct, defined once, reused consistently, visible in figure/method, and the contribution would be harder to explain without it. Quick test: if a sentence reads like mechanical translation from Chinese academic phrasing (`this case`, `more practical`, `effectively solves`), replace it with a field-common equivalent.

### 4.4 Figures must be explained concretely

Map text to visible elements: modules, variables, arrows, colors, steps. Bad: `Figure 2 illustrates the idea of the initialization operator.` Better: name the steps in reader order, explain how data or candidate structures move through them, and explain colored arrows or changed edges. For a figure-method mismatch: state what the figure should show, name visible parts in order, trace the process, connect it to the claimed property. If the figure does not show the claimed property, do not invent a textual explanation — flag that the figure or claim needs revision.

### 4.5 Related work must be related work

Repair pattern: `research line -> representative citations -> what they solve -> what remains unresolved -> why this paper still needs its method`. No method-name lists (`Method X introduced...`, `Method Y improved...`) — use technology- or problem-oriented subjects with citations as support. Chronology words (`later`, `recent`) only when time order matters. Do not mix unrelated dimensions without a covering topic sentence. Do not end by praising the proposed method — end by stating the gap. A subsection title should sound like a research line, not the method's internal component.

### 4.6 Contributions must be visible and defensible

Audit: is the feature introduced earlier, shown in figures/algorithms/experiments, new to this paper rather than inherited, and stated identically in abstract and contribution list? If important but unexplained, explain it or remove the claim.

Worksheet (for your own analysis, not the paper): `new content | bottleneck solved | method location | supporting validation | how far the claim can go`. Pattern: `specific mechanism -> problem it addresses -> where described/evaluated -> bounded effect`. Prefer `is designed to` for design purpose; use direct verbs (`reuses`, `restricts`, `updates`) when the mechanism simply does it. Vary syntax across items; do not credit standard components (BIC decomposability, hash tables, classic GA steps) as inventions.

### 4.7 Method sections must teach the process

Require: clear process order; definitions before symbols; variables matching formulas and figures; small examples for abstract construction steps; what each operator changes and why; explicit link between design and stated limitation. Pattern: `input/state -> operation -> changed structure -> reason -> output/next step`. If a mechanism is central, give it its own subsection.

### 4.8 Experiments must specify dimensions, units, and meaning

Check: what exactly counts as `large` or `high-dimensional`; units of time/memory/score; whether `OOM` / `N/A` markers are defined near the table; whether datasets and baselines are distributed sensibly. Pattern: `setting dimension -> why it represents the claimed difficulty -> metric/unit -> baselines -> observed effect -> bounded interpretation`. Distinguish "designed for X" from "remains applicable under X-like conditions."

### 4.9 Voice, tense, and sentence form

Fewer author-centered action sequences; passive voice acceptable when it improves technical tone. Present tense for established facts and method descriptions; past tense for completed experiments, by field convention. Avoid repeated sentence skeletons, future tense in method/experiment text, and overuse of parentheses. Prefer technical subjects (`the initialization operator`, `the candidate parent set`, `the experimental results`).

### 4.10 Small wording corrections reveal patterns

`number of` for countable plurals; `study on` only when natural; singular/plural consistency for methods, parent sets, networks, populations; `and` vs `or` consistency; spacing, subscripts, symbol formatting; IEEE reference completeness (`IEEEabrv` when relevant). These often signal larger consistency problems.

## 5. Section Tasks

**Abstract.** Compact chain `problem -> concrete limitation -> proposed method -> key mechanism -> bounded result`. Define non-standard abbreviations on first use. No new task name, benchmark, or objective presented as if known. Result sentences need a comparison target or boundary. Network/dataset counts, metric advantages, and method names must match the main text.

**Introduction.** Builds necessity. Each major mechanism needs a reason before it appears. Method/model claims must not precede the reader's understanding of the limitation.

**Method.** Teach the process; use figures and examples aggressively. If an advisor comment says "I cannot understand," assume the narrative needs reconstruction, not polish.

**Results.** Make units, dataset dimensions, baseline meaning, and table markers explicit. Avoid `effective` or `superior` without a comparison target. Same paragraph: separate observation (which metric, which condition) from attribution (which ablation supports it) from explanation (possible cause, not causal fact without measurement).

**Conclusion.** Compact; no unsupported future-looking claims; future tense only for actual future work. Do not write untested experiments (robustness, interventions, cross-domain) as existing capability.

**Reviewer response.** Order: accurate understanding of the comment -> answer the technical question -> state the actual revision -> give section/formula/table locations. When disagreeing, state the conditions first, then evidence. Unperformed experiments are plans or alternative explanations, never "we have added." If the comment implies a false premise (e.g., demanding a unique causal DAG from observational BNSL without extra assumptions), state the premise issue explicitly; tighten the paper's claim instead of inventing a proof.

## 6. Claim Tightening

First ask what evidence is missing: comparison object, metric, conditions, theoretical premises, or mechanism. Add only the necessary dimension — do not stack hedges on every sentence.

| Overstated | Downgrade to |
|---|---|
| `guarantees recovery of true structures` | `allows excluded candidate edges to be reconsidered` (mechanism) + `improves structural recovery on the evaluated benchmarks` (results) |
| `proves` / `ensures` | `shows` / `is consistent with` / `supports`, unless citing a theorem |
| `significantly improves` | statistical test + effect size, or `a higher mean X on the tested datasets` |
| `robust transferability` | `is also evaluated within [host methods] to examine its applicability beyond [this method]` |
| `reaches a near-optimal solution` | `reaches a comparable [metric] in fewer iterations`, if the curve supports only that |
| `avoids local optima` | `is designed to escape ...` (design intent) or a trajectory observation |
| `solely determined by X` / guaranteed linear scaling | report measured ratios and limit the claim to tested scales |

## 7. Evidence–Contribution Audit

| Claim | Needs direct evidence | Not sufficient alone |
|---|---|---|
| Component X improves exploration | controlled comparison; diversity measurement if diversity is claimed | higher final score only |
| Cache reduces computation | no-cache vs standard-cache vs proposed; hit rates, evaluation counts, memory | full algorithm beats others |
| Parallelism scales | fixed hardware config, scale sweep, quality constraint | single-point total runtime |
| Robust to noise/prior errors | noise/error type and strength, plus controls | clean benchmark results |
| Component transfers to other methods | integration into named hosts with results and cost | `plug-and-play` wording |
| Causal/structural validity | identifiability target, reference structures, direction-aware metrics | downstream task accuracy |

Ablation supports local contributions, not necessity in all combinations. If one control changed several components at once, do not attribute the whole gain to one module.

## 8. Cross-Section Fact Table

For full reviews, record: method/abbreviation — research goal — data type — network count — sample-size combinations — repeats — baseline count and class — budget — score symbol and direction — metric definitions (F1 over skeleton or directed edges, SHD reversal counting, BIC direction) — main results — figure/table/code location. Every fact points to a location; on conflict, report both places (e.g., abstract says eight networks, datasets section lists thirty-four) instead of choosing by majority.

## 9. Repair Patterns From Version Chains

1. **Generic field opening -> task-specific opening** (PMIPSGA). Drop textbook framing; start near the task; no praise of a method family before its necessity.
2. **Ornate method naming -> mechanism naming** (COFTGA). Replace stacked-modifier names (`collaborative optimization genetic algorithm with feedback-driven adaptive constraint and two-stage mutation`) with a name exposing the central relation; every word in the name must stay visible across abstract, method, figures, experiments.
3. **Vague limitation -> explicit failure mode** (COFTGA). Say what is lost, where, and why it matters: e.g., `existing hybrid methods treat constraint and search as decoupled stages, resulting in permanent loss of actual dependencies...`.
4. **One overloaded sentence -> visible collaboration structure** (COFTGA). State the method, then explain mechanisms in a paired or numbered structure.
5. **Strong results -> bounded results** (COFTGA). Keep comparison target and metric category; see Section 6.
6. **Component noun precision** (MMGA_BN). `mutation operator`, not `the mutation`; use `operator/strategy/mechanism/framework` only when the noun matches the object.
7. **Author-centered -> method-centered results** (MMGA_BN). `the proposed method achieves...`.
8. **Dataset/condition wording must be exact** (PMIPSGA). Define which dimensions are `large-scale` and which are `high-dimensional`; define `OOM`/`N/A` near the table; distinguish the target condition from the condition under which the method remains applicable.

Weak-evidence warnings: PMIPSGA's parallel motivation (time consumption alone does not justify parallelism — explain decomposable/redundant computation); `co-evolutionary framework` (questioned by the advisor; do not use unless the paper matches recognized co-evolutionary usage — prefer `collaboration` or `coupled constraint and score-based search`).

## 10. Word-Level Audit Checklist

- Is every technical noun common in the target field?
- Is every verb-noun collocation common (`mine patterns`, `prune the search space`, `reduce runtime`)?
- Is every compound term traceable to published usage rather than invented?
- Does every adjective add information, or only sound polished?
- Does every comparison state its target?
- Does every abbreviation need to exist?
- Does every claim have support or cautious wording?
- Is any vague pronoun replaceable by a concrete noun?
- Are there consecutive sentences with the same opener, pattern, or near-synonym for one mechanism?
- Does any sentence nest more than one clause level? Split it.
- Does the paragraph move from known work to limitation to present need?
- Would the expression likely appear in an accepted paper from the target area? If not, simplify or mark `field-use check recommended`.
