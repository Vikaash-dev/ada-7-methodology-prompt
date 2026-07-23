# ADA-7 Review and Consolidation

## Scope reviewed

- `main`
- merged PR #2
- open PRs #1 and #3
- the v3 branch and its `Prompt.original`, `Prompt`, `Prompt.lite`, `Prompt.full`, configuration, comparison, implementation, and self-evaluation documents
- the P-TTS paper and implementation (`arXiv:2510.09599`, VILA-Lab/PTTS)
- research on meta-prompting, decomposition, ensembling, deliberate search, tool use, verification, refinement, prompt optimization, ideation, and autonomous science

## Strengths retained

- Seven-stage software lifecycle
- Constraint-aware engineering decisions
- Alternatives, risks, acceptance criteria, ADRs, and implementation plans
- Adaptive-depth direction from the Lite edition
- Evidence-based development
- Professional documentation
- Critical self-evaluation rather than unqualified self-praise

## Defects corrected

1. Unsupported alignment, quality, consensus, and improvement percentages
2. Claims of autonomous browsing, testing, deployment, monitoring, persistence, and scheduled updates without guaranteed tools
3. Requirements to expose chain-of-thought
4. Fixed paper/repository quotas for every decision
5. Enterprise, Kubernetes, Terraform, and microservices defaults for small projects
6. Multiple competing active prompt editions
7. Uncalibrated self-confidence scores
8. Stale hard-coded model recommendations
9. Mandatory approval after every stage
10. Pseudo-functions that imply executable control flow
11. Blind self-correction without reliable feedback
12. Decorative multi-agent personas without independent objectives
13. Universal use of “think step by step” despite task-dependent results
14. Confusing benchmark-specific prompting effects with universal capability gains
15. No held-out evaluation or regression protocol
16. Generic ideation with no prior-art collision filter or candidate tournament
17. Autonomous paper claims without experimental and reproducibility gates

## v5 architecture

The canonical prompt is [`ADA7.md`](ADA7.md). It contains five integrated layers:

1. **Task compiler** — identifies the real goal, constraints, evaluator, unknowns, tools, and stopping condition.
2. **Adaptive effort router** — selects fast, standard, deep, or maximum effort.
3. **Strategy router** — chooses decomposition, meta-prompting, prompt ensembles, deliberate search, tools, verification, or measured optimization only when useful.
4. **Domain engines** — specialized workflows for winning ideation, autonomous science, and software/repository work.
5. **Quality gates** — outcome, correctness, evidence, novelty, feasibility, adversarial, regression, and communication checks.

## Interpretation of P-TTS

The paper's useful transferable principle is **controlled prompt-space exploration**. P-TTS generated diverse reasoning traces from 90 AIME seeds using multiple wrappers and a teacher model, then fine-tuned Qwen2.5 students. The result does not prove that one dramatic reward or penalty sentence universally improves a frontier model's direct answer.

ADA-7 therefore:

- varies mechanisms and prompt contexts rather than relying on a single wording;
- evaluates variants before retaining them;
- does not use reward/penalty framing by default;
- records that math/SFT results may not transfer to open-ended ideation;
- combines diversity with verifiers, retrieval, tests, and held-out selection.

## Ideation correction

The previous prompt could produce polished but generic ideas. v5 now requires:

- opportunity and judge mapping;
- recent prior-art research when available;
- cross-domain mechanism transfer;
- a broad internal candidate population;
- a genericity and collision filter;
- explicit novelty, feasibility, demo, impact, and defensibility scoring;
- skeptical review and repair;
- selection of one winning idea only after comparison.

## Autonomous research correction

v5 integrates literature review, novelty checks, hypotheses, experiment design, implementation, execution, analysis, paper writing, and reviewer loops. It also requires:

- falsifiable claims;
- baselines and ablations;
- data and experiment provenance;
- negative-result retention;
- executed evidence before performance claims;
- human checkpoints for important research decisions;
- no acceptance, novelty, reproducibility, or SOTA claims without proof.

## Prompt optimization correction

Prompt optimization is treated as empirical optimization:

- development/validation/holdout separation;
- baseline measurement;
- diverse prompt and pipeline variants;
- trajectory-level feedback;
- mutation and recombination;
- Pareto selection across quality, cost, latency, and robustness;
- held-out selection and rollback.

## Repository state on the consolidation branch

- `ADA7.md` — one active prompt
- `RESEARCH_FOUNDATIONS.md` — evidence and limitations
- `evals/BENCHMARK_PLAN.md` — evaluation and ablations
- `legacy/Prompt.v1.md` — archived historical prompt
- obsolete root `Prompt` removed
- README rewritten for v5

## Acceptance criteria

- One canonical prompt
- No fabricated quantitative claims
- No chain-of-thought disclosure requirement
- No unperformed tool-action claims
- External validators preferred over blind self-correction
- Research depth proportional to risk and uncertainty
- Scale-appropriate architecture
- Non-generic ideation process
- Evidence-gated autonomous paper workflow
- Held-out evaluation before performance claims
- Natural-language usability without commands
- Clear rollback and migration history

## Remaining work before a measured SOTA claim

1. Build representative evaluation cases.
2. Run cost-matched baselines across several current model families.
3. Perform the required component ablations.
4. Use blinded human evaluation for ideation and paper planning.
5. Publish exact prompts, settings, traces, evaluators, and negative results.
6. Revise the prompt based on measured failures.
7. Tag a stable release only after regression gates pass.
