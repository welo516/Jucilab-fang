# Examples

Load this file for full reviews, pre-submission checks, and reviewer responses. Each case shows the expected diagnosis format: where the problem is, why it matters, and the repair direction. Cases 1-10 are distilled from the advisor annotation corpus (quotes are advisor voice, kept as evidence); case 11 is a worked abstract rewrite. Adapt locations and wording to the manuscript at hand — do not copy text into a paper.

## 1. Coined terms pile up and drift (naming break)

Advisor: `造了好多词 前后也不统一`, `这都是些什么词！`, `太混乱了，感觉就是在炫技、炫词`, `你一直在强调的feedback呢？`

Meaning: many self-created terms, inconsistent across sections, and a promised concept (`feedback`) that the text never sustains. Repair: keep one name per mechanism, defined once and reused everywhere; if the text cannot keep a promised concept visible, remove the term rather than adding another. A long stacked method name is replaced by a shorter name exposing the central relation.

## 2. Related work performs a different job (identity break)

Advisor: `从内容来看 不是related work`, `不像是related work的标题`.

Meaning: the section advertises or describes the proposed method instead of prior research lines. Repair: rewrite as `research line -> representative citations -> what they solve -> remaining gap`; the subsection title should sound like a research line.

## 3. Text does not map to the figure (traceability break)

Advisor: `跟图没有任何对应关系`, `整个介绍跟图没有联系！你要至少用一组边进行介绍。 又怎么能看出你的算子保留了优秀的结构？`, `图中红色箭头表示什么意思？`, `对图2没有具体介绍，你只是说了理念。`

Meaning: idea-level figure description with no visible elements. Repair: name modules, edges, colors, and steps in reader order; explain changed edges explicitly; if the claimed property is not visible in the figure, flag the figure, not the wording.

## 4. Contribution claimed but never shown (evidence break)

Advisor: `这个不能作为贡献？`, `全文都没有看出、也没有指出这个特征`, `跟你的摘要就对不上`.

Meaning: a contribution item has no matching method description, figure, or experiment. Repair: either add the missing support or remove the item; check abstract-contribution consistency.

## 5. Parallelism motivated only by runtime (necessity break)

Advisor: `并行方法是为了解决收敛问题？`, `而且为什么你要用并行GA，不是并行其他的算法`, `但是我觉得不应该仅仅是time consumption，否则不一定需要并行。`

Meaning: "it takes time" does not justify parallelism. Repair: explain the decomposable or redundant structure (repeated fitness evaluations, independent candidate scoring) that makes parallelism the right design, then connect to the chosen platform.

## 6. Generic opening paragraphs (necessity break)

Advisor: `以下三段都是通用内容，没有针对性，对本文的作用并不大。 本文为什么用GA，为什么用MI，为什么设计并行GA，为什么是spark并行，为什么提出父集结构，都没有给出足够的铺垫。`

Meaning: textbook background without a paper-specific limitation. Repair: compress to one setup paragraph and rebuild the chain `task difficulty -> specific bottleneck -> why existing methods fail -> why this mechanism fits`.

## 7. Tense and voice discipline

Advisor: `少用将来时，其他地方不再一一指出`, `主动语态太多`, `少用这种主动语态`.

Meaning: future tense in method/experiment text and strings of author-centered sentences. Repair: present tense for established facts and method descriptions, past tense for completed experiments, method-centered subjects; check section-wide.

## 8. Experimental labels used as self-evident

Advisor: `你这里要说清楚，哪些维度是large dataset，哪些维度是high-dimentional network`, `OOM INDICATES OUT-OF-MEMORY. N/A MEANS NO MEMORY IS REQUIRED.`, `什么单位？`, `一天？两天？`

Meaning: vague condition labels and undefined table markers. Repair: define dimensions and markers near the table; state units; distinguish the target condition from the condition under which the method remains applicable.

## 9. Terminology and small-consistency signals

Advisor: `时而and 时而or`, `这个是什么词`, `你特别喜欢用这个词`, `2025的文献基本没有`, `标出的文献均缺少信息； 文献格式 IEEEabrv`.

Meaning: near-synonym drift, pet words, citation recency and formatting gaps. Repair: one term per mechanism across the whole paper; verify citations are recent enough for the claimed state of the art and complete per the venue style. These small signals often indicate larger consistency problems.

## 10. Contradictory statements inside one manuscript

Advisor: `会不会有点矛盾？前面说MI用的少、后面说MI过于依赖`.

Meaning: the motivation says existing methods underuse MI while the limitation section says over-reliance on MI is a risk. Repair: make the two claims compatible explicitly (e.g., existing methods underuse dependency information in stage A but over-rely on it in stage B), or fix the inconsistency before polishing.

## 11. Worked abstract rewrite (baseline shape)

Original (typical weak abstract): `Bayesian network structure learning is an important problem and the learning task is NP-hard. Genetic algorithms are effective for this problem. However, the advantages of mutual information have not yet been fully explored. We propose an improved genetic algorithm, which uses mutual information to guide the search. Experimental results on standard Bayesian networks show that our method achieves better performance than other algorithms.`

Issues: generic opening; unexplained GA and MI; empty gap sentence; method sentence without mechanism; unbounded result claim.

Rewritten shape (replace bracketed parts with manuscript facts):

> Bayesian network structure learning is NP-hard, and the number of candidate structures grows exponentially with the number of variables. Genetic algorithms are well suited to searching such a large discrete space, but existing GA-based methods evaluate candidates mainly with scores and exploit little dependency information among variables. [Mechanism sentence: what MI provides and where it acts.] This paper proposes [method], in which [key mechanism]. Experiments on [networks, scales] show that the proposed method [bounded result with metric and comparison scope].

The rewrite is a template, not an output to submit: every bracket, and the claim about existing methods, must be checked against the manuscript's own related work and experiments.
