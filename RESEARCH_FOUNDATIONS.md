# Research Foundations for ADA-7 v5

ADA-7 v5 is a research-grounded **SOTA candidate**, not a universal performance guarantee. This document maps research findings to the mechanisms used in the canonical prompt and records where transfer is uncertain.

## Design conclusion

No single wording consistently maximizes every model and task. Prompt performance is sensitive to phrasing, formatting, examples, order, model family, decoding, and evaluator. The strongest general design is therefore an **adaptive controller** that chooses among decomposition, prompt ensembles, tool use, deliberate search, verification, feedback, and benchmark-driven prompt evolution.

## Technique map

| Mechanism in ADA-7 | Research basis | What is retained | Important limitation |
|---|---|---|---|
| Adaptive technique router | *The Prompt Report* (Schulhoff et al., 2024/2025), arXiv:2406.06608 | Techniques are selected by task instead of stacked blindly | The survey shows techniques can degrade performance and prompt sensitivity is high |
| Meta-prompting conductor | Suzgun & Kalai, 2024, *Meta-Prompting*, arXiv:2401.12954 | Decompose work and assign genuinely distinct expert objectives | Simulated experts are not independent models unless separate calls are actually made |
| Prompt-space exploration | Bsharat & Shen, 2025, *Prompting Test-Time Scaling*, arXiv:2510.09599 | Generate semantically aligned but strategically varied prompt contexts | Main evidence comes from teacher-generated math traces and SFT; direct transfer to open-ended ideation is unproven |
| Diverse sampling and aggregation | Wang et al., 2022, *Self-Consistency Improves Chain of Thought Reasoning*, arXiv:2203.11171 | Use independent solution paths and objective voting where appropriate | Majority vote is unsuitable for many free-form outputs |
| Deliberate search and backtracking | Yao et al., 2023, *Tree of Thoughts*, arXiv:2305.10601 | Branch, evaluate, prune, and backtrack when early choices matter | Search increases cost and can amplify a weak evaluator |
| Reasoning-action interleaving | Yao et al., 2022, *ReAct*, arXiv:2210.03629 | Use tools and observations to update plans | Requires useful external actions and reliable tool results |
| Agentic tree search | Zhou et al., 2023, *Language Agent Tree Search*, arXiv:2310.04406 | Combine planning, action, reflection, and external feedback | Complex and expensive for ordinary tasks |
| Draft-feedback-refine | Madaan et al., 2023, *Self-Refine*, arXiv:2303.17651 | Diagnose concrete defects and revise iteratively | Intrinsic self-feedback alone is not a dependable correctness signal |
| External-feedback reflection | Shinn et al., 2023, *Reflexion*, arXiv:2303.11366 | Convert test or environment feedback into reusable lessons | Persistent memory requires actual environment support |
| Verification questions | Dhuliawala et al., 2023, *Chain-of-Verification*, arXiv:2309.11495 | Verify claims independently from the draft | Verification can still fail without retrieval or reliable evidence |
| Prompt optimization loop | Yang et al., 2023, *OPRO*, arXiv:2309.03409 | Generate, score, retain, and improve prompt candidates | Gains are task/model/evaluator dependent and can overfit development examples |
| Automatic prompt search | Zhou et al., 2022, *Automatic Prompt Engineer*, arXiv:2211.01910 | Treat instructions as programs selected by measured performance | Requires a representative dataset and objective scoring |
| Self-referential evolution | Fernando et al., 2023, *Promptbreeder*, arXiv:2309.16797 | Mutate both task prompts and improvement strategies | Evolution can be compute-heavy and exploit evaluator weaknesses |
| Declarative pipeline optimization | Khattab et al., 2023, *DSPy*, arXiv:2310.03714 | Optimize compound prompt pipelines against metrics | Requires examples, metrics, and execution infrastructure |
| Textual gradients | Yuksekgonul et al., 2024, *TextGrad*, arXiv:2406.07496 | Backpropagate textual feedback to specific system components | LLM feedback quality remains a bottleneck |
| Reflective prompt evolution | Agrawal et al., 2025, *GEPA*, arXiv:2507.19457 | Learn high-level rules from trajectories and preserve Pareto-optimal variants | Reported gains do not establish universal cross-model superiority |
| Autonomous research lifecycle | Lu et al., 2024, *The AI Scientist*, arXiv:2408.06292 | Link ideation, implementation, experiments, writing, and review | Automated reviewers can reward superficial or contaminated work |
| Progressive scientific tree search | Yamada et al., 2025, *The AI Scientist-v2*, arXiv:2504.08066 | Explore and manage experiment branches rather than follow one plan | One accepted workshop paper does not imply reliable autonomous science |
| Human-guided research agents | Schmidgall et al., 2025, *Agent Laboratory*, arXiv:2501.04227 | Add human checkpoints after literature, design, and experiments | Quality varies strongly by model and human feedback |
| Research replication benchmark | Starace et al., 2025, *PaperBench*, arXiv:2504.01848 | Evaluate research agents with decomposed, author-grounded rubrics | Frontier agents remained far below expert human replication performance in the reported evaluation |
| Research ideation chains | Li et al., 2024, *Chain of Ideas*, arXiv:2410.13185 | Organize prior work as progressive mechanisms before generating ideas | Ideation quality still depends on retrieval coverage and evaluation |
| Facet recombination and novelty search | Radensky et al., 2024, *Scideator*, arXiv:2409.14634 | Recombine purposes, mechanisms, and evaluations; search for overlap | Automated novelty judgment is not proof of novelty |
| Concept-network ideation | Zhao et al., 2025, *Deep Ideation*, arXiv:2511.02238 | Explore, expand, evolve, and critique ideas over a structured concept network | Recent result; broad independent replication is not yet established |

## Critical negative evidence

### Blind self-correction is unreliable

Huang et al., 2023 (*Large Language Models Cannot Self-Correct Reasoning Yet*, arXiv:2310.01798) found that intrinsic self-correction can fail or degrade correct reasoning. Kamoi et al., 2024 (arXiv:2406.01297) conclude that reliable external feedback is the strongest condition for successful correction. ADA-7 therefore prioritizes tests, retrieval, compilers, calculators, environment feedback, and explicit rubrics over generic “check your answer again” loops.

### Prompt wording is a hyperparameter

The Prompt Report documents large sensitivity to small wording, formatting, and ordering changes. ADA-7 does not enshrine a single emotional, reward, penalty, correctness, or chain-of-thought wrapper as universally optimal. These are optional candidates in a measured prompt-space search.

### P-TTS must not be misrepresented

P-TTS used 90 curated AIME seeds, multiple instructional wrappers, DeepSeek-R1-generated reasoning traces, and supervised fine-tuning of Qwen2.5 models. Its strongest results therefore support **prompt-space diversity as a data and search mechanism**, not the claim that adding “I will tip you” to one user prompt universally improves frontier-model outputs. The paper itself lists limited external validity, teacher bias, calibration risks, hyperparameter sensitivity, possible contamination, and inference-generation compute as limitations.

### Autonomous paper generation is not autonomous truth

AI Scientist, AI Scientist-v2, and Agent Laboratory demonstrate increasingly complete research workflows, but PaperBench shows research replication remains difficult. ADA-7 must not label an output novel, reproducible, accepted, or state of the art without real literature checks, executed experiments, comparisons, and review.

## Why the prompt uses an adaptive controller

The final design combines four layers:

1. **Task compiler** — converts vague requests into goals, constraints, evaluators, and stopping conditions.
2. **Strategy router** — selects only techniques with expected value for that task.
3. **Search-and-verify loop** — explores alternatives, uses tools, tests claims, and revises defects.
4. **Measured optimizer** — when examples and metrics exist, evolves prompts and selects on held-out performance.

This structure is intended to close the gap between casual chat prompting and the richer inference scaffolds used in research systems.

## Reference repositories

- VILA-Lab/PTTS
- stanfordnlp/dspy
- gepa-ai/gepa
- google-deepmind/opro
- princeton-nlp/tree-of-thought-llm
- lapisrocks/LanguageAgentTreeSearch
- noahshinn/reflexion
- SakanaAI/AI-Scientist
- SakanaAI/AI-Scientist-v2

Repository activity and performance claims must be rechecked at the time they are used; they are not frozen facts embedded in the prompt.
