# DeepSeek Harness — protected goal-completion verification (OpenSiro internal issue draft)

**PLAN_ONLY · scoped GO · research NEEDS_EVIDENCE · DRAFT — NOT PUBLISHED**

**Target transition:** S3*=— -> S3*=C
**Proposal-stage decision:** GO
**Research disposition:** NEEDS_EVIDENCE

**Canonical evidence and status:** [roadmap.md](roadmap.md).
**Technical construction analysis:** [constructor-sufficiency.md](constructor-sufficiency.md).
**Original source:** https://github.com/deepseek-ai/deepseek-harness/commit/2e39e70496aa02986ca6a820c5d497e816b69d7e.
**Current user/problem evidence:** https://github.com/deepseek-ai/deepseek-harness/discussions/10471.
**Independent proof-of-concept alternative:** https://github.com/bpc-oss/dsh-verification.

## Decision

**GO is limited to investigating an optional, original-native GoalService pre-commit completion-guard seam**, allowing a distinct opt-in reviewer plugin to block unsupported `complete`, persist an attributable permit and return a usable rejection to the active goal workflow. The original service's [complete path](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) records `goal/change` before `goal/changed`, so a passive observer cannot veto durable completion. A separate developer plugin already implements the reviewer via a [vendored native patch](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs); this shows the proposed seam is technically meaningful, but is **not evidence of compatibility or advantage on current original HEAD**.

A [user Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) describes two model-declared complete events that ended continuation too early and forced repeated `/goal` setup. This is **third-party user testimony, not an OpenSiro reproduced test**. No user outcome improvement, native test or runtime benchmark has been measured. The original first-party [CONTRIBUTING.md](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) disallows outside PRs and directs users to Discussions/plugins.

## Accepted historical VSM starting point

Included [canonical Index assessment](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md), frozen assessment blob `257a55619d474d8a86a49de6dffa93a4426d7b62`, review ref `ddefc45fbc7f8e46dd73185e68295696d1297887`, reviewed 2026-09-18, Profile 0.2.2 / Methodology 0.3.1. This is a historical ownership vector, **not** a new grade or capability score.

| Function | Historical state | Current observed owner / design | Decision |
| --- | --- | --- | --- |
| **S1 · Operations** | A | AgentLoop and session own tool execution and feedback | Existing; no added C target |
| **S2 · Coordination** | A | Opt-in Teams task board, CAS, dependencies and messages | Existing; no added C target |
| **S3 · Management** | A(P) | Team Lead and parent task-board controls allocate and regulate active work | Existing; no added C target |
| **S3* · Independent audit** | — | Goal / Ralph completion is model/worker asserted; Auto Review is pre-tool approval, not final-goal certification | **Eligible proposal**: `S3*=— -> S3*=C` with explicit composed reviewer and protected completion |
| **S4 · Future adaptation** | — | Extensible profiles/plugins, but no independently evidenced prospective decision actor | No S4 target |
| **S5 · Policy/identity** | — | User/deployer owns authority; no warranted S5 reallocation | No S5 target |

## Track A — shipped behavior and simpler alternatives

- First-party [GoalService.complete](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) enforces current goal revision/phase but has no registered independent pre-commit verifier. It appends `goal/change` before notifying subscribers, so the listener cannot roll back a false completion.
- First-party Goal tool and goal-round driver provide model-owned `complete` and continuation. Ralph terminal state is worker-reported, and Auto Review evaluates pending tools rather than actual final acceptance.
- **A0 cheapest:** task-specific test/CI receipt or human parent acceptance *outside* the goal state. This may be entirely sufficient for some operators.
- **A1 opt-in existing plugin:** [bpc-oss/dsh-verification](https://github.com/bpc-oss/dsh-verification) states advisory/enforce modes, provenance-bound evidence, a separate decision gate, and [real GoalService seam tests](https://github.com/bpc-oss/dsh-verification/blob/main/packages/dsh-verification/test/seam-e2e.test.ts); its enforce path **requires a vendor-patched GoalService** via [patch script](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs). The reported tests and benchmarks are third-party claims not run here.
- **Original PR feature disabled:** [public repo metadata](https://api.github.com/repos/deepseek-ai/deepseek-harness) has `has_pull_requests=false`, [PR tab](https://github.com/deepseek-ai/deepseek-harness/pulls) shows restricted creation and 0/0; REST pull lists return 404. Historical PR visibility cannot be exhaustively inferred. Original Discussion #8736 is a plugin Discussion, **not PR #8736**. Review the live original [Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions) as the actual community route.

## Track B — smallest on-top constructor

Compose **S3* via an optional first-party seam plus external policy actor**, rather than duplicating GoalService:

1. GoalService exposes a typed registration/unregistration of protected `complete` guards, checks before `agent.session.append('goal/change', ...)`, and respects goal id/revision and parent-owned scope.
2. An opt-in independent reviewer receives independently captured artifact/test evidence and existing goal objective/revision, issues `allow / deny / hold` or a narrowly typed permit, and persists an attributable audit. Without a configured reviewer, existing Goal behavior remains unchanged; in an explicitly enforced mode, missing reviewer/evidence must not silently certify success.
3. `deny/hold` keeps the original active state, produces a visible tool/service failure and auditable reason, and permits a later *authorised* correction round; `allow` commits with a verifiable permit reference. No actor can override parent pause/policy.
4. The verified source of decision is not the agent's own completion narrative. A passive event hook or an LLM warning without veto is **not** S3*=C.

This is **GO + NEEDS_EVIDENCE at proposal stage**, not proof of a completed S3* actor. The smallest native delta may be just an API seam; evaluator, policy, evidence storage and correction behavior remain opt-in composed components.

## P0 / P1 / P2 and falsifiers

- **P0:** prototype the bounded native `GoalTransitionGuard`/permit attribution interface against **current original pinned source**, then measure it against the unchanged source plus existing vendored plugin. **Do not publish or implement in the original repository by default.**
- **P1:** positive: bogus worker `complete` with failing independent test is denied **before append**, Goal remains active, later authorised round can fix it; correct completion is certified with independent evidence; cancellation/parent pause/stale revision/reviewer failure fail closed only in enforce mode. Test plugin disabled/advisory for exact backwards compatibility.
- **P2:** NONE. Only consider wider first-party integration after cheaper alternatives are ruled out.

**Positive falsifier / stop:** a standard non-core plugin on unmodified original HEAD can already prevent all relevant direct goal-completion paths, or tests/human acceptance yield equal verified outcomes at lower cost, or additional native ownership violates source policy. Conversely, a user report alone does not prove implementation correctness. **Native tests: NOT_RUN; costs: NOT_MEASURED.**

## Historical attribution and publication

This is an **evidence-driven amendment**, **not another isolated first-attempt rerun**. The original v0.18 source-first [previous reconciled decision](https://github.com/opensiro-contributions/deepseek-harness/blob/39bc69e4149528ab89deb60a6ed03f81739b0178/.opensiro/issues/independent-goal-verification-20261119/roadmap.md) concluded NO_GO/NO_USEFUL_CHANGE before finding the actual user Discussion and independent vendor-patch evidence; its revision is now retained in Git ancestry. The historical Index vector is unchanged. No maintainer acceptance is claimed.

**DRAFT — NOT PUBLISHED.** No original Issue/Discussion/PR/comment, public fork Issue, original product change or index regrade was made. Original contributor policy presently declines external PRs; public contact and external fork proposals require exact current-conversation approval.
