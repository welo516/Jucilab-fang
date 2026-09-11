# Domain Pack: Causal Learning, DAG Learning, and Bayesian Network Structure Learning

Load this file only when the manuscript concerns causal discovery, DAG learning, BNSL, or Bayesian-network-adjacent structure/scoring problems (including GA-based, parallel, or cache-accelerated BNSL methods). It adds field facts and claim boundaries on top of the base rules; it never overrides `SKILL.md`. Evolutionary-computation wording (population, mutation operator, crossover, fitness evaluation, premature convergence, exploration and exploitation) is common in the group's papers and may be used when the method is genuinely evolutionary.

## 1. Field-Common Terms

`Bayesian network`, `directed acyclic graph`, `conditional independence`, `constraint-based search`, `score-based search`, `hybrid structure learning`, `parent set`, `candidate parent set`, `superstructure`, `structure score`, `score decomposability`, `mutual information`, `conditional mutual information`, `structure learning`, `dependency`, `redundant fitness evaluation`, `score memoization`, `search-space restriction`, `candidate edge`, `relax superstructure constraints`, `reconsider excluded candidate edges`, `structural recovery`, `structural accuracy`, `SHD`.

Wording cautions: `correlation` only for correlation or a specific statistic (use `statistical dependence` / `conditional dependence` for dependency claims); `score memoization`, not `memorization`, for caching; `structural accuracy` must not be confused with classification accuracy; `recover` must distinguish candidate recovery from true-edge recovery; a missing edge in the candidate graph must not be written as `independent`.

## 2. Scientific Claim Boundaries

- A standard BN represents a factorization of a joint distribution; a causal reading needs causal modeling semantics and assumptions. Do not upgrade a statistical BNSL paper into a causal-discovery paper during polishing.
- Learnable objects differ: statistical dependency structure, skeleton, DAG, CPDAG/Markov equivalence class, or a uniquely identified causal DAG. Arrows in a figure do not by themselves mean discovered causality.
- Observational data do not imply directions are never identifiable; identifiability depends on the model class, independence or distribution assumptions, observability, and additional information (priors, interventions). Any unique-DAG conclusion must name its actual conditions. `under appropriate assumptions` still requires the method section to state the assumptions.
- Five properties that never imply each other: function expressiveness, statistical identifiability, estimation consistency, optimization behavior, finite-sample recovery. A theorem about one covers only that one.
- MI/CMI quantify statistical dependence and can guide search heuristics; they do not establish causal direction. BIC or likelihood fit does not verify causal correctness. MI is non-negative, can be zero, and for finite discrete variables is bounded by `min(H(X), H(Y))` — do not write an open interval `(0, +inf)`; handle zero-denominator normalization explicitly.
- A super-exponential count of DAGs motivates avoiding enumeration but is not an NP-hardness proof; complexity claims need the matching problem-and-scoring-setting result (e.g., Chickering, Heckerman & Meek, 2004, for large-sample score-based learning).
- Differentiable acyclicity (continuous relaxation, log-det/M-matrix domains, analytic constraints) characterizes DAGs in its stated domain; it does not make the optimization convex, guarantee the global optimum, or validate the learned graph causally. Zero-temperature limits and finite-temperature computation are different regimes.
- Relaxing a superstructure lets excluded candidate edges re-enter the searchable set; whether a true edge is finally recovered is decided by the later search and scoring. Precise score caching changes computation, not the statistical objective.

## 3. Method And Experiment Writing Checks

**Algorithm reproducibility.** Fix the adjacency-matrix direction (`A_ij` = i→j or j→i) before citing formulas; distinguish candidate parent sets from final parent sets; state the search operator's trigger, probability, and repair steps; distinguish fixed per-generation schedules from state-feedback adaptation; state the stopping criterion (generations, evaluations, time, convergence) and what is returned.

**Score caching.** Caching is valid for the same data, the same local distribution setting, and the same scoring hyperparameters. Separate statistic reuse, parent-set-level reuse, and whole-graph reuse (encoding, hashing, collision handling). An average `O(1)` lookup excludes key-construction time; worst case, amortized cost, and measured time are different numbers. Cost formulas such as `T ≈ (1-h_global)(1-h_local) T_base` are conditional approximations, not identities. With a fixed candidate sequence and exact scoring, caching preserves scores; within a fixed time budget it may change which candidates are evaluated.

**Parallelism.** Name what is parallel (data scan, local scoring, individual evaluation, operators, independent runs); distinguish multi-threading from distributed runs and `speedup = T_1/T_p` from a runtime ratio against another algorithm; state whether preprocessing, cache init, serialization, and synchronization are included; strong and weak scaling are not interchangeable; load imbalance depends on more than node count, so do not extrapolate linear speedup.

**Metrics.** F1: skeleton or directed edges, how reversals count, zero-denominator handling. SHD: reversal counted once or twice, graph type, implementation. CPDAG/PAG comparisons must match the identifiability target. BIC may be maximized (log-likelihood minus penalty) or minimized — check the formula before writing higher/lower. Percentages: 60%→66% is +6 points or +10% relative; do not report relative improvement for negative-oriented scores without care. Ties, per-network wins, and averages need explicit denominators.

**Fairness.** Baselines using true skeletons or orders use extra information and are not the same protocol. Sample, seed, and graph-generation repeats are different statistical units. Equal generations ≠ equal evaluations ≠ equal time; pick the budget matching the claim. Timeout, OOM, and unsupported are different outcomes — not F1 = 0 or infinite SHD. Synthetic data from known BNs is not real-world application data.

## 4. Domain Examples

**BN is not causal (introduction).** `The DAG structure describes the causal relationships between variables, while the CPT quantifies the strength of these relationships.` → `The DAG encodes the dependency structure, and the CPTs specify the local conditional distributions.` In language-only mode, keep the original sentence and flag the issue out-of-band.

**Local Markov property.** Not `independent of all variables that are not directly connected` (that includes indirect descendants), but `each variable is conditionally independent of its non-descendants given its parents`.

**Counting is not NP-hardness.** Do not derive NP-hardness from DAG-count growth; separate the enumeration-infeasibility statement from the complexity claim, and match the cited hardness result to the paper's scoring setting.

**Candidate recovery vs true-edge recovery.** A constraint-relaxation mechanism is described as `relaxes the superstructure constraints when the search stagnates, allowing previously excluded candidate edges to be reconsidered`; true-edge recall needs its own experiments. With host-algorithm transfer experiments, write `is also evaluated within [host methods] to examine its applicability beyond [this method]`, not `robust transferability`.

**Algorithm classification is checkable.** Do not call a known hybrid method exact because it appears next to exact solvers in one experiment table; recheck the claims that depended on the old classification.
