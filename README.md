<div align="center">

# ADA-7 v5

### Adaptive Capability Amplifier

*A single research-grounded controller prompt for stronger reasoning, ideation, research, software development, verification, and autonomous scientific workflows.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-SOTA_candidate-orange.svg)](evals/BENCHMARK_PLAN.md)
[![Prompt](https://img.shields.io/badge/canonical-ADA7.md-blue.svg)](ADA7.md)

</div>

## What changed

Earlier ADA-7 versions were comprehensive but rigid, excessively long, and contained unsupported claims about research alignment, confidence, autonomy, and performance. The v5 consolidation keeps the useful seven-stage lifecycle while replacing fixed ceremony with an adaptive search-and-verify controller.

There is now **one active prompt**:

- [`ADA7.md`](ADA7.md) — canonical ADA-7 v5 prompt

Previous prompt material is historical and should not be treated as an active alternative.

## Core idea

A model often performs far below the capabilities reported in research because an ordinary user prompt requests one immediate answer. Strong research systems instead add decomposition, prompt-space exploration, tool use, independent candidates, deliberate search, verifiers, feedback loops, and measured optimization.

ADA-7 v5 acts as a controller that selects those mechanisms only when they are useful.

```text
User goal
   ↓
Task compiler → constraints + evaluator + stopping condition
   ↓
Adaptive effort router
   ↓
Strategy selection
   ├─ decomposition
   ├─ meta-prompting experts
   ├─ prompt/candidate ensemble
   ├─ deliberate search and backtracking
   ├─ tools and retrieval
   ├─ verification
   └─ external-feedback refinement
   ↓
Quality gates
   ↓
Best verified deliverable
```

## Major capabilities

### Winning ideation

The ideation engine is designed to prevent generic “AI-powered app” answers. It performs opportunity mapping, cross-domain transfer, divergent generation, prior-art collision checks, candidate tournaments, adversarial review, feasibility analysis, and pitch construction.

Typical request:

```text
/ideate Create the strongest implementable idea for this hackathon.
Analyze prior implementations, judging criteria, novelty, feasibility,
demo strength, and measurable impact before choosing a winner.
```

### Autonomous research and paper creation

The paper mode links:

```text
literature → novelty check → hypotheses → experiment design →
implementation → execution → analysis → manuscript → review → revision
```

It requires real evidence and executed experiments before claiming novelty, reproducibility, acceptance, or state-of-the-art performance.

### Prompt and pipeline optimization

When examples and a measurable evaluator are available, ADA-7 can guide an OPRO/GEPA/DSPy-style optimization loop:

- establish a baseline;
- generate diverse prompt or pipeline variants;
- evaluate trajectories;
- derive textual lessons;
- mutate and recombine candidates;
- preserve a quality/cost/latency Pareto frontier;
- select on untouched holdout cases;
- retain rollback history.

### Software and repository work

The controller inspects the current system, reproduces defects, implements the smallest coherent fix, adds regression tests, runs available checks, reviews the diff, and reports exact outcomes.

## Quick start

1. Copy the full contents of [`ADA7.md`](ADA7.md) into the model's system or custom-instruction context.
2. Describe the outcome, constraints, and available tools.
3. Use natural language or an optional mode command.

```text
/max Research and design a hackathon-winning edge-AI accessibility system.
Do not give me a common smart-stick clone. Search prior work, identify an
underserved failure point, generate and compare diverse mechanisms, then
provide the winning concept, MVP, demo, architecture, validation, and pitch.
```

Optional commands:

- `/fast` — minimum sufficient effort
- `/deep` — multi-path analysis and verification
- `/max` — maximum justified effort
- `/ideate` — non-generic innovation engine
- `/research` — primary-source synthesis
- `/paper` — autonomous scientific workflow
- `/build` — implementation mode
- `/verify` — strongest available checks
- `/optimize-prompt` — measured prompt evolution
- `/review` — adversarial audit and repair

Natural language always takes precedence.

## Why it does not promise universal benchmark gains

Prompt effectiveness depends on the model, task, examples, evaluator, decoding, tools, and wording. Some techniques improve one benchmark while degrading another. A universal “best prompt” cannot be established without a defined evaluation context.

ADA-7 is therefore labeled a **SOTA candidate** until it earns scoped claims through the held-out process in [`evals/BENCHMARK_PLAN.md`](evals/BENCHMARK_PLAN.md).

## Research basis

[`RESEARCH_FOUNDATIONS.md`](RESEARCH_FOUNDATIONS.md) maps prompt components to research including:

- The Prompt Report
- Meta-Prompting
- Prompting Test-Time Scaling
- Self-Consistency
- Tree of Thoughts and Language Agent Tree Search
- ReAct
- Self-Refine, Reflexion, and Chain-of-Verification
- Automatic Prompt Engineer, OPRO, Promptbreeder, DSPy, TextGrad, and GEPA
- The AI Scientist, AI Scientist-v2, Agent Laboratory, and PaperBench
- Chain of Ideas, Scideator, and Deep Ideation

The document also records negative evidence and transfer limitations so the prompt does not cargo-cult benchmark-specific techniques.

## Repository documents

| File | Purpose |
|---|---|
| [`ADA7.md`](ADA7.md) | Single canonical prompt |
| [`RESEARCH_FOUNDATIONS.md`](RESEARCH_FOUNDATIONS.md) | Evidence map and limitations |
| [`evals/BENCHMARK_PLAN.md`](evals/BENCHMARK_PLAN.md) | Held-out evaluation, ablation, and release gates |
| [`REVIEW_AND_CONSOLIDATION.md`](REVIEW_AND_CONSOLIDATION.md) | Review of previous branches and migration decisions |
| [`examples/`](examples/) | Usage examples |

## Design principles

- Best verified result, not first plausible output
- External validators over blind self-correction
- Search diversity without unnecessary agent theatre
- Primary sources and executed tests
- Capability honesty
- Adaptive effort and proportional complexity
- One source of truth
- No fabricated scores, citations, or execution claims

## Contributing

Useful contributions include:

- reproducible evaluation results;
- difficult ideation, coding, research, and safety cases;
- prompt ablations;
- model-specific compatibility findings;
- failure analyses;
- optimizer integrations;
- independent replications.

Performance claims must include the exact prompt commit, model, settings, tool access, dataset split, evaluator, cost, and date.

## License

MIT License. See [`LICENSE`](LICENSE).
