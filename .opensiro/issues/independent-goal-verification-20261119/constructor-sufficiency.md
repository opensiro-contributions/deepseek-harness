# DeepSeek Harness — technical constructor-sufficiency analysis

**Target transition:** S3*=— -> S3*=C
**Proposal-stage decision:** GO
**Research disposition:** NEEDS_EVIDENCE

**Human draft:** [issue.md](issue.md). **Canonical receipt:** [roadmap.md](roadmap.md).
**Scope:** narrow research GO for an **opt-in pre-commit GoalService guard port**; real S3*=C remains unproven until an independent configured actor plus feedback works under native runtime tests.

## Source and six-function coverage

Original master pinned: https://github.com/deepseek-ai/deepseek-harness/commit/2e39e70496aa02986ca6a820c5d497e816b69d7e. Historical Index ownership S1=A / S2=A / S3=A(P) / S3*=— / S4=— / S5=— is recorded in the Human's six-function table and [canonical Index record](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md). The source-first evaluation covered AgentLoop/Session, Team/board, Goal service/tool/driver, Ralph, Auto Review, Cordis composition and parent constraints. Do not treat absent historical cells as defects.

- S1 already drives work through agent tool events and feedback.
- S2 Team task dependencies/CAS coordinate competing work.
- S3 Lead/parent control manages live goals and assignments.
- **S3*** currently lacks a first-party protected, independent goal-completion certification port; [GoalService](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) persists `goal/change` and only then emits `goal/changed`.
- S4 no evidenced future-environment prediction/adaptation owner; no target.
- S5 user/deployment policy remains with lawful parent; no invented agent authority.

## Track A and concrete counterfactual

**Actual operator demand:** in [Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) a user reports repeated model-authorised `update_goal complete`, requiring creation of several goals for the same work, and specifically proposes `propose_complete` plus independent evidence verification. This is a first-party-hosted **user report**, not a reproduced production defect or maintainer acceptance.

**Current native:** `GoalService.complete()` delegates to `transition(... 'complete' ...)`. `commitSnapshot()` builds the change and `commit()` calls `agent.session.append('goal/change', change)` before emitting `goal/changed`. Goal id/revision, tool authority, goal-round feedback and ordinary acceptance checks exist, but are not an independent goal certification boundary.

**A0:** manual acceptance and task-specific CI/tests can reject bad deliverables, at least after worker self-report; low-cost alternative.

**A1 concrete external construction:** [bpc-oss/dsh-verification](https://github.com/bpc-oss/dsh-verification) implements an optional evidence/permit verifier with source-visible [vendor patch](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs) injecting `registerTransitionGuard` and pre-commit synchronous dispatch and `permitRef` into `@deepseek-ai/dsh-goal`. Its [seam-e2e tests](https://github.com/bpc-oss/dsh-verification/blob/main/packages/dsh-verification/test/seam-e2e.test.ts) claim direct `ctx.goals.complete` without permit is rejected without mutation, and verify enable/disable/stale/permit attribution paths. These tests were **read, not run**; package last pushed August 2026, and compatibility with frozen original November HEAD is **UNKNOWN**. The plugin's default advisory path is not an enforce path; npm publication is not established. This implementation is a counterfactual **proof of practical seam pressure**, not proof a new baked-in verifier is needed.

**PRs and original issue tracking:** [repo metadata](https://api.github.com/repos/deepseek-ai/deepseek-harness) explicitly reports `has_pull_requests=false` and `has_issues=false`, while Discussions are enabled. [GitHub PR page](https://github.com/deepseek-ai/deepseek-harness/pulls) restricts creation and currently reports 0 open and 0 closed; REST pull endpoints return 404. Thus native PR bodies/diffs are not available for exhaustive overlap, not evidence of a hidden accepted verifier. Discussion #8736 is a task-notify plugin discussion (not a PR). Original [contributor policy](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) prioritises independent plugins and explicitly declines PRs.

## Minimum Track B on-top component

**P0 = GoalTransitionGuard extension seam**, not a new mandatory reviewer package. Add a registered plugin-visible synchronous veto on `complete` **before** the session's durable `goal/change` append; check current goal id/revision, never accept stale receipts, and permit scoped observer identity. Optional goal-change `permitRef` attribution must be schema-aware with compatible replay/projection and no unexplained authority escalation. The separate plugin can already supply evidence capture and reviewer decision; goal service only supplies the protected boundary.

**S3* proof obligations for the composed system:** (i) evidence independent of worker self-report, (ii) distinct lawful reviewer decision `certify/reject/hold`, (iii) enforcement before state change, (iv) verifiable audit/ref, (v) authorised corrective work following a rejected claim. A hook alone cannot be graded C. Parent pause/stop and release gate must win. Non-enforce/advisory mode must remain backwards-compatible.

**Falsifier:** show an unpatched original Cordis plugin alone can veto *all* direct completion paths at matching revision, or that the vendored plugin plus ordinary tests has equal effect at lower maintenance cost, or no user value in controlled reproduction. In any of those cases revert to NO_GO for the native seam. Conversely, denial on `tools/pre-execute` only might miss an internal direct `ctx.goals.complete` caller; do not confuse tool gate with complete authority.

## Source-backed test / cost plan

1. Pin original `2e39e70496aa02986ca6a820c5d497e816b69d7e` and plugin version separately. Reproduce direct GoalService completion without verifier, with (a) insufficient evidence and (b) independently accepted objective.
2. Run the external vendor-patched A1 on matching original source, then implement a disposable optional native port B1 without vendor patch. Exercise `goal/change` log sequence under no-guard/advisory/enforce modes.
3. Inject stale `revision`, absent reviewer, forged/stale permitRef, plugin rejection/throw, parent pause, restart/replay, concurrent guard install/remove. Confirm no false permitted completion and that permitted cases are exactly attributed.
4. Verify denials become actionable feedback and the active goal continues only through authorised owner action; explicit true positive succeeds. Compare to A0 acceptance and A1 vendoring.
5. Record source test logs, timestamps, runtime/failure/maintenance cost; if a simple route matches B1, reject B1.

**Current state:** no original native tests were run, external prototype's assertions were not independently reproduced, no actual cost measured, maintainer approval absent. Current result is source-grounded **GO / NEEDS_EVIDENCE**, not accepted or shipped C.

## Historical comparison

[Previous independent v0.18 case]([previous reconciled decision](https://github.com/opensiro-contributions/deepseek-harness/blob/39bc69e4149528ab89deb60a6ed03f81739b0178/.opensiro/issues/independent-goal-verification-20261119/roadmap.md)) concluded NO_GO/NO_USEFUL_CHANGE under the evidence then known. This follow-up found a direct actual user report and a working-repository *claim* with source-level patch/tests. Revision to GO is attributed to **newly retrieved external evidence after the original independent pass**, not a second fresh-chat assessment or evidence of downstream Index promotion. No outward publication.

## v0.18.1 AI constructor refinement — 2026-11-20

**Proposal-stage:** `S3*=— -> S3*=C`, `GO / NEEDS_EVIDENCE` unchanged; same-case refinement, not an independently rerun decision. The source-native interception point is [`GoalService.complete(agent, ref): GoalView`](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) before [`commitSnapshot`](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) calls `session.append('goal/change')`; [`tool-goal`](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) is **one consumer**, not the authority boundary.

**Minimal independently installable constructor:** keep GoalService's synchronous mutation shape and existing CAS; introduce a scoped register/unregister pre-commit `complete` guard port, called after exact live-goal + revision/phase validation but before durable mutation. An optional separately configured reviewer first gathers test/artifact evidence, computes a signed/bound decision against goal/session/revision, then passes a permit to the guard; guard rejects absent/stale/forged verdict in explicit enforce mode. The abstract reviewer and its data retention stay outside GoalService; no new generic orchestration loop, default-on verifier, parent-policy promotion, or bypass via direct service caller. Define one deterministic typed rejection and feed it back to the current model/parent, retaining active state for correction; handle cancellation, teardown and concurrent revisions without a false successful append. If `permitRef` is persisted, explicitly version/update `GoalSnapshotChangeMeta`, strict fold and replay/compatibility tests — do not mutate event-v1 ad hoc.

**Matched tests/falsification:** reproduce the source user report against baseline, exercise direct `ctx.goals.complete`, model `update_goal complete`, no-plugin/advisory/enforce, faulty reviewer, stale goal ID/revision, parent pause, denial→correction→acceptance, Session restart/replay, disposal and malformed permit. Show independent evidence rather than a worker narrative; run comparator A0 (human/CI acceptance) and existing A1 (`bpc-oss/dsh-verification` vendored patch) at pinned original SHA. If baseline/plugin-only already enforces all routes at lower total cost, native B1 is `NO_USEFUL_CHANGE` **for adoption**, not a historical reassessment rewrite. Tests **NOT_RUN**; costs **NOT_MEASURED**. Linked [issue.md](issue.md), canonical [roadmap.md](roadmap.md).
