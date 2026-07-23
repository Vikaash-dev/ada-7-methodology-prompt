# ADA-7 v5 Benchmark and Ablation Plan

## Purpose

This plan determines whether ADA-7 v5 improves outcomes over simpler prompting. It prevents the repository from declaring “SOTA” based on prompt length, paper citations, or subjective confidence.

## Systems under comparison

1. **Raw baseline** — the user request with no added scaffold.
2. **Minimal baseline** — concise role, goal, constraints, and output format.
3. **Legacy ADA-7** — the previous active `Prompt` file.
4. **ADA-7 v5** — canonical `ADA7.md`.
5. **ADA-7 v5 optimized** — only when development examples and a measurable evaluator are available; use the prompt-evolution procedure and evaluate on untouched holdout cases.

Use the same model, temperature, tool access, context, and token budget for paired comparisons unless the experiment explicitly studies compute scaling.

## Evaluation domains

### 1. Objective reasoning

Candidate datasets:
- arithmetic and mathematical reasoning
- logic and constraint satisfaction
- multi-hop factual questions
- planning problems

Metrics:
- exact match or task-native score
- pass@1
- invalid-output rate
- token and latency cost
- robustness across prompt paraphrases

### 2. Coding and repository work

Tasks should include:
- bug localization and repair
- feature implementation
- test generation
- refactoring under compatibility constraints
- security or configuration review

Metrics:
- tests passed
- hidden tests passed
- regression count
- build/type/lint status
- diff size and unnecessary-change rate
- security defects introduced
- time and token cost

### 3. Factual research and synthesis

Tasks should require current, primary-source research and contradiction handling.

Metrics:
- citation precision: cited source actually supports the claim
- citation completeness: load-bearing claims supported
- source quality and diversity
- factual error rate
- unsupported-claim rate
- contradiction coverage
- freshness compliance

### 4. Hackathon and product ideation

Construct challenge briefs with real judging criteria, time limits, team skills, and implementation constraints.

Blind evaluators score:
- problem importance
- specificity
- novelty of mechanism
- evidence of user need
- feasibility in the event timeline
- demo strength
- measurable impact
- differentiation from prior art
- ethical and operational risk
- pitch clarity

Additional checks:
- web-based prior-art collision search
- number of generic AI/IoT/blockchain clones
- implementation-plan realism
- whether the idea survives an adversarial reviewer

Use pairwise human preference and judge-ranking rather than relying only on an LLM score.

### 5. Scientific ideation and paper planning

Use a PaperBench- and Idea-Arena-inspired hierarchical rubric:
- literature understanding
- novelty relative to retrieved work
- hypothesis falsifiability
- experimental discriminativeness
- baseline strength
- ablation quality
- statistical validity
- reproducibility
- limitation honesty
- manuscript coherence

Novelty is provisional until literature search and expert review.

### 6. Autonomous research execution

Where compute permits, provide a small research problem with executable experiments.

Metrics:
- environment setup success
- code execution success
- experiment completion rate
- correct metric computation
- recovery from failed experiments
- provenance and reproducibility
- alignment between results and manuscript claims
- negative-result retention

### 7. Safety, honesty, and tool-use calibration

Test cases should include:
- unavailable tools
- stale facts
- malicious instructions embedded in retrieved text
- requests that tempt fabricated test results
- ambiguous destructive actions
- contradictory constraints

Metrics:
- false execution claims
- invented citations or metrics
- prompt-injection compliance rate
- unnecessary refusal rate
- appropriate clarification or assumption behavior

## Evaluation procedure

1. Freeze the prompt candidates before viewing holdout labels.
2. Randomize and anonymize outputs.
3. Use at least three independent runs for stochastic settings; use more when variance is high.
4. Keep tool traces and execution logs.
5. Use deterministic validators wherever possible.
6. For subjective dimensions, use multiple blinded reviewers and report agreement.
7. Report mean, variance, confidence intervals, and per-task failures—not only aggregate averages.
8. Inspect whether gains come from extra tokens or calls by including cost-matched comparisons.
9. Run prompt-paraphrase and format perturbations to measure sensitivity.
10. Preserve all negative results.

## Required ablations

Remove one component at a time:

- task compiler
- adaptive effort router
- independent candidate generation
- meta-prompting experts
- prompt-space exploration
- tool-action loop
- verification questions
- external-feedback refinement
- ideation collision filter
- adversarial review
- quality gates

Also compare:
- one candidate vs. candidate tournament
- intrinsic self-critique vs. tool/evaluator feedback
- fixed “think step by step” vs. adaptive technique selection
- dramatic reward/penalty wrapper vs. neutral correctness framing
- no optimization vs. development-set optimization vs. held-out selection

## Prompt optimization protocol

When a representative dataset and metric exist:

1. Divide cases into development, validation, and final holdout splits.
2. Run the baseline and record trajectory-level failures.
3. Generate prompt variants with different mechanisms, not only synonyms.
4. Evaluate and retain a Pareto frontier for quality, latency, tokens, and robustness.
5. Derive textual lessons from failures.
6. Mutate and recombine high-performing variants.
7. Stop when validation improvement stalls.
8. Select once on the final holdout.
9. Never tune on final holdout results.
10. Store the exact prompt, model, settings, date, dataset hash, and evaluator version.

## Release gates

ADA-7 may be called a **SOTA candidate** when the prompt and evaluation protocol are complete.

It may claim a measured improvement only when:
- the evaluation was actually run;
- the baseline is competitive and cost-matched;
- holdout performance improves by a practically meaningful margin;
- critical objective-task regressions are absent or explicitly accepted;
- gains are robust across multiple task types or clearly scoped to one domain;
- factuality, execution honesty, and safety do not regress;
- results and artifacts are reproducible.

“SOTA” must always specify the model, dataset, evaluator, tools, budget, and date. There is no context-free universal SOTA prompt.

## Result record template

```markdown
# Evaluation Run

- Date:
- Commit:
- Models:
- Tool access:
- Decoding settings:
- Token/call budget:
- Dataset and split hashes:
- Evaluators:

## Aggregate results

| System | Objective | Coding | Research | Ideation | Safety | Cost |
|---|---:|---:|---:|---:|---:|---:|

## Statistical analysis

## Ablations

## Regressions

## Qualitative failures

## Decision

Promote / revise / reject, with rationale and rollback commit.
```
