# DeepSeek Harness — independently verified goal completion? (OpenSiro internal roadmap)

**PLAN_ONLY · scoped NO_GO · research NO_USEFUL_CHANGE · DRAFT — NOT PUBLISHED**

**Target transition:** NO_QUALIFIED_C_TARGET
**Proposal-stage decision:** NO_GO
**Research disposition:** NO_USEFUL_CHANGE

**Canonical decision receipt:** [roadmap.md](roadmap.md), source of truth for Index pins, six-function dispositions and all status fields.
**Technical review:** [constructor-sufficiency.md](constructor-sufficiency.md).
**Original:** https://github.com/deepseek-ai/deepseek-harness · pinned master commit 2e39e70496aa02986ca6a820c5d497e816b69d7e.
**Working fork:** https://github.com/opensiro-contributions/deepseek-harness, metadata-only opensiro/meta.

## Decision in one paragraph

DeepSeek Harness lets a model declare a durable Goal complete and also has Ralph workers that self-report completion. Its own documentation explicitly defers independent evaluator certification. We independently tested this architecture hypothesis against the first-party code and the cheapest alternatives, **not by running native tasks**. There is no reproduced wrong-completion case or established additional user benefit requiring a new first-party constructed S3* owner over explicit test checks, a human review or an opt-in Cordis plugin. Therefore **NO_GO** to this specific new first-party implementation at present; this says nothing adverse about the harness as a whole.

## Accepted historical VSM starting point

Accepted Index [DeepSeek Harness assessment](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md) at Index commit c2e43bf4750841277b3e58d8ba80314121734764, assessment blob 257a55619d474d8a86a49de6dffa93a4426d7b62, review source ddefc45fbc7f8e46dd73185e68295696d1297887, reviewed 2026-09-18, Profile 0.2.2 / Methodology 0.3.1. **These are historical ownership states, not current code grades or quality scores.** A = autonomous agent owns decisive closure; C = developer-composable autonomous decision constructor; P = supported parent owner; — = no material accepted function at the assessed boundary.

| Function / human meaning | Historical Index state | Source-backed current boundary / owner | Candidate / disposition |
| --- | --- | --- | --- |
| **S1 · Operations** | A | [AgentLoop](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/core/agent-loop/README.md): model selects tools and uses subsequent Session results | NO_TARGET: already agent-operated |
| **S2 · Coordination** | A | [Team service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/team/agent-team/README.md): members share task state, dependencies, CAS and messages | NO_TARGET: functioning optional Team mode |
| **S3 · Current management** | A(P) | Team Lead and parent board govern current assignments and working commitments | NO_TARGET: no evidenced new manager need |
| **S3* · Independent audit** | — | Goal and Ralph completion by same caller/worker; Auto Review only per-tool pre-execution authorization | Candidate evaluated; **NO_GO** for new first-party constructor now |
| **S4 · Future adaptation** | — | Plugins and profile selection are deployment options, no evidenced autonomous future feedback actor | NO_TARGET: no specific prospective task |
| **S5 · Identity / policy** | — | User/deployment permissions and reserved parent authority outside claimed local S5 owner | NO_TARGET: do not invent local ultimate policy |

Product system in focus: first-party Agent/Session with published opt-in Team, Goal, Ralph and Auto Review modes. Maintainer workflows, external evaluators, original CI and model provider are outside this organizational decision boundary.

## What exists and what is actually missing

**Track A (existing):** [Goal service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/README.md) stores a revision-checked objective; [round driver](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal-round-driver/README.md) continues work. [Ralph](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/tool-ralph/README.md) returns self-declared statuses. [Auto Review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md) decides before a tool call, not after a worker's outcome. Existing [Cordis profiles](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/architecture.md) already support user-selected plugins. The [original contributor policy](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) explicitly declines external PRs for now; targeted original issue search found no matching request, and original full PR-list API returned 404 (PR inventory **UNKNOWN**, not empty).

**Track B (considered):** optional independent evaluator consumes goal and artifact/test evidence from outside the worker report; distinct actor selects certify/reject/hold; an authorised result protects completion and influences later Goal rounds; a durable outcome is read back. In [current source](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts), GoalService.complete mutates the goal before emitting a changed event, so a passive event listener is not the required enforcement. A real new first-party pre-commit gate has **not** been justified over a separate plugin or ordinary task tests.

**Distinctness / falsifier:** reproduce an actual false goal completion, then show that deterministic tests, human verification and a non-core plugin cannot achieve the same authorised correction, while the smallest first-party native addition does. Without this, more code adds cost rather than a demonstrated S3* function. The proposed scenario is **HYPOTHETICAL**.

## P0 / P1 / P2 and test boundary

**P0:** NO_QUALIFIED_C_TARGET — no new first-party constructor selected. **P1:** conditionally collect one falsifiable real failure and cheaper-route comparator, identify lawful authority and exact missing native seam. **P2:** NONE. Architectural sufficiency of a new complete C constructor is **NOT ESTABLISHED**, no developer interest or user demand is invented.

Proposed positive witness: false worker success rejected by independent artifact evidence and an authorised later correction; true success certified. Negative witnesses: stale revision, absent reviewer, worker-only evidence, blocked parent action, forbidden policy change and default-mode compatibility. This is a future experiment, not a reported test pass. **Validation: NOT_RUN; benefit/cost: NOT_MEASURED.**

## Publication and historical comparison

The earlier [pre-rerun case](https://github.com/opensiro-contributions/deepseek-harness/blob/37cbf1f044059dfca9e61d0f7c2c8f0ef5222851/.opensiro/issues/independent-goal-verification-20261119/roadmap.md) also selected NO_GO. It was consulted **after** the fresh six-function/Track A/B decision and remains historical provenance, not the basis of this verdict. The owner's subsequent ACTIVE/ALLOW state authorises these internal case documents, not a public fork Issue or external-original interaction.

**DRAFT — NOT PUBLISHED.** This issue.md is a proposed public working-fork Issue body, not a GitHub Issue. No original Issue, Discussion, PR or comment has been sent; no product change, new Index grade or verified return to an actual user task is claimed. AI-assisted source research; no independent human experiment reported.
