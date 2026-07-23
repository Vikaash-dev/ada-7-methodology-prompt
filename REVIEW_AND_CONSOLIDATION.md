# ADA-7 Repository Review and Consolidation

## Scope reviewed

- Default branch: `main`
- Merged redesign: PR #2 (`copilot/create-clean-github-design`)
- Open template branch: PR #1
- Open v3 rebuild: PR #3 (`copilot/rethink-and-reinvent-prompt`)
- Key artifacts: `Prompt`, `Prompt.original`, `Prompt.lite`, `Prompt.full`, `README.md`, `prompt-config.json`, research comparison, implementation guide, and critical self-evaluation

## What should be retained

1. The seven-stage lifecycle provides a useful project-development map.
2. Explicit constraints, alternatives, risk analysis, acceptance criteria, and ADRs improve decision quality.
3. The Lite branch correctly moves toward adaptive depth and a smaller command surface.
4. The critical self-evaluation identifies real weaknesses: verbosity, rigidity, unsupported scores, lack of empirical evaluation, and confusing autonomy claims.
5. The professional repository documentation and example structure from PR #2 are worth preserving.

## Defects found

### 1. Unsupported claims

Several files assign exact alignment, quality, consensus, and improvement percentages without a reproducible evaluation. These values should not be treated as evidence.

### 2. Capability overclaiming

`Prompt.full` directs an assistant to continuously research, maintain a knowledge graph, execute tests, deploy staging infrastructure, monitor production, and update knowledge weekly. A prompt cannot guarantee these capabilities. They depend on tools, permissions, runtime, persistence, and user approval.

### 3. Forced reasoning disclosure

The prompt repeatedly requests explicit chain-of-thought. A production prompt should request concise rationale, assumptions, evidence, and verification rather than hidden internal reasoning.

### 4. Arbitrary research volume

Fixed requirements such as 10–15 sources for every technical decision waste time and can lower evidence quality. Research depth should be proportional to uncertainty, risk, and consequence.

### 5. Architecture bias

The old prompt defaults to enterprise architecture, Kubernetes, Terraform, microservices comparisons, 80% coverage, and full observability regardless of project scale. This risks over-engineering.

### 6. Version fragmentation

Four competing prompt files make it unclear which behavior is canonical. README guidance partly addresses this but preserves contradictory rules across editions.

### 7. Self-scoring without calibration

A model-generated 0–100 confidence or quality score is not a validated measurement. Confidence should be explained through evidence quality, uncertainty, test results, and assumptions.

### 8. Stale model and version metadata

The configuration references model names and context assumptions that age quickly. Current capabilities should be verified at use time rather than hard-coded as optimal.

### 9. Stage-gate friction

Mandatory approval after every stage can block autonomous progress even when requirements are clear. Checkpoints should be tied to irreversible, costly, risky, or ambiguous decisions.

### 10. Prompt-as-program ambiguity

The pseudo-functions imply executable state and control flow, but most chat environments do not execute them. Natural-language behavior contracts are more portable.

## Consolidated v4 decisions

| Area | Previous behavior | v4 decision |
|---|---|---|
| Canonical prompt | Multiple active editions | One `ADA7.md` core prompt |
| Research | Fixed source quotas | Evidence proportional to risk |
| Reasoning | Request chain-of-thought | Provide concise rationale only |
| Capabilities | Assume autonomous tools | Check and report actual capabilities |
| Validation | Self-assigned scores | Executed tests and evidence labels |
| Architecture | Enterprise defaults | Simplest sufficient design |
| Stage flow | Mandatory linear gates | Adaptive, iterative lifecycle |
| Commands | 15-command pseudo-runtime | 8 optional natural-language aliases |
| Confidence | Numeric without calibration | Qualitative uncertainty with basis |
| Tool results | Implied execution | Passed/failed/skipped/unavailable |

## Migration plan

1. Make `ADA7.md` the canonical prompt.
2. Keep older prompt files under `legacy/` for historical comparison in a future cleanup PR.
3. Replace unsupported benchmark and alignment claims with reproducible evaluations.
4. Add scenario-based prompt evaluations before publishing a stable v4 tag.
5. Update README to point new users to `ADA7.md` and label older editions as legacy.
6. Close or supersede PR #1 after preserving any unique template content.
7. Do not merge PR #3 unchanged; use this consolidation branch as its successor.

## Acceptance criteria for v4

- No fabricated or unsupported quantitative claims.
- No requirement to reveal private chain-of-thought.
- No claim of tool execution without an execution result.
- Research depth adapts to the decision.
- Simple projects can skip irrelevant stages.
- Architecture and infrastructure recommendations are scale-appropriate.
- The prompt remains usable without slash commands.
- The core prompt has one canonical source of truth.
