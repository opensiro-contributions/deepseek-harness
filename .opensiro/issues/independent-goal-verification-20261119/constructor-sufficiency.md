# DeepSeek Harness — technical S3* C-constructor sufficiency review

**Target transition:** NO_QUALIFIED_C_TARGET
**Proposal-stage decision:** NO_GO
**Research disposition:** NO_USEFUL_CHANGE

**Human decision:** [issue.md](issue.md). **Canonical technical/status receipt:** [roadmap.md](roadmap.md). This AI contract is a proposal-stage source-evidence analysis, not a new Index assessment or native implementation.

## 1. Boundary and actual function-specific source

Original source: https://github.com/deepseek-ai/deepseek-harness/commit/2e39e70496aa02986ca6a820c5d497e816b69d7e. Historical included Index assessment, review ref, accepted vector and six-function outcomes are exclusively pinned in [roadmap.md](roadmap.md). One supported harness organization includes its Agent/Session and opt-in Team, Goal, experimental Ralph/Auto Review; not external maintainers, user policy or a reviewer outside its composed runtime.

- S1 existing closure: [AgentLoop](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/core/agent-loop/README.md) binds model tool action and subsequent Session feedback.
- S2 existing closure: [Teams](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/team/agent-team/README.md) regulate mutual work via board, dependencies, CAS and messages.
- S3 existing closure: Team Lead and authorised parent Task Board manage assignments and current commitments.
- S3* candidate: independent review after a claimed Goal/Ralph completion; current Goal and Ralph own self-declared terminal status only.
- S4 negative: no evidenced specific future-environment adaptation need; plugin availability is not an autonomous future-return actor.
- S5 negative: user and deployment control remain legitimate parent/governance boundaries, not automatically installable local policy.

**Function witness only if later substantiated:** independent actor reads evidence from a different channel than worker summary, uses legitimate certify/reject/hold alternatives, enforces any certified label and returns information that changes later authorised work. A mere audit message or code review UI does not establish it.

## 2. Track A — source-native mechanisms and cheapest alternative

| Native surface | What it actually enforces | What it does not prove |
| --- | --- | --- |
| [Goal service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) | GoalRef CAS, persisted goal/change, complete/block state transitions, goal/changed notice | Independent reviewer consent before completion |
| [Goal tools](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) | Model update_goal routes complete/blocked to Goal service under existing tool authority | Evidence-independent verifier judgment |
| [Goal-round driver](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal-round-driver/src/index.ts) | Bounded continuation, cancellation, stale reservation checks and source feedback | Review/certification of goal completion |
| [Ralph](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/tool-ralph/README.md) | Fresh child rounds, structured self-report and cap | Outcome evidence not chosen by the worker |
| [Auto Review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md) | Separate model review of pending tool effects before execution | Post-result independent validation |
| [Cordis composition](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/architecture.md) | User-selected services/events/plugins and profile overlays | Permission to mutate goal as a separate bounded S3* owner |

The source-visible GoalService.complete() appends goal/change and then emits goal/changed (same [source](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts)). The model-facing [tool code](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) calls complete directly after completionAuthority permits goal-round completion. Therefore a passive subscriber to goal/changed cannot reliably reject the worker's false success **before it becomes durable**. Revision guards alone do not certify factual task success; an authorised plugin or parent can already use task-specific tests without another core component.

Original PR inventory: targeted search returned no matching first-party evaluator, but the direct original open PR list returned HTTP 404, so comprehensive overlap status remains **UNKNOWN**. Original [CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) currently rejects external PR submissions. No maintainer feature mandate is inferred.

## 3. Independent Track B alternatives and C sufficiency

| Option | Mechanism and actual owner | Return-to-operation question | Evaluation |
| --- | --- | --- | --- |
| A0 task tests / parent accept | Explicit deterministic test command or human checks the artifact after worker reports | Parent/user can decide whether to continue; not an in-runtime C actor | Lowest integration cost; no demonstrated failure |
| A1 opt-in out-of-tree plugin | Separate Cordis reviewer reads independent evidence, publishes its own verdict; parent owns any task correction | Can it legally prevent inaccurate certification or merely add a warning? | Preferred experiment if a real case appears; source hooks exist, enforcement remains unproven |
| B1 smallest new first-party S3* port | Define completion/certification interface only if non-core path cannot achieve a required protected decision; evaluator composed from developer policy, evidence and owner | Guard completion before durable success, reject stale/parent-forbidden decisions, append return evidence, influence next authorised goal round | Coherent hypothesis, but **not qualified or implemented** |
| B2 standalone controller | Duplicate Goal store and policy authority to control worker completion | Changes parent policy and competition with native state | Overbuilt, no independent justification |

For B1 a **complete hypothetical constructor** requires: (a) independent provenance of objective/worker claim and external artifact/test evidence, (b) separately selected reviewer with explicit lawful authority to certify/hold/reject, (c) a protected point that prevents falsely claiming certified completion or provides distinct status without rewriting the worker's result, (d) durable audit record tied to exact Goal id/revision and review evidence, and (e) authorised later goal work or escalation with observable return. An exposed hook with no independent decision owner or one-way warning is **insufficient**. These are logical obligations; the number of physical native APIs is not prescribed. Existing native code could cover all but one edge, if a real counterexample proved it.

**Counterfactual owner test:** remove the reviewer but keep Goal service, checks, CAS and events. Worker completion and task tests still work; no independent model audit actor makes a decision *inside the harness*. But absence of that C function alone is not evidence the user needs a first-party implementation. External test/human/sidecar alternatives must first be shown insufficient for the exact task.

**Reason for current NO_GO:** actual task failure and distinct positive user result have not been demonstrated; the original documents deliberate evaluator deferral; full original-native PR-list coverage was unavailable; a protected completion port's lawful owner and effect have not been proven necessary. This is not a blanket judgment that independent verification is useless, and a source-backed intentional omission of all future auditing is **not** claimed.

## 4. Falsifiable future validation, and decision boundaries

Native commands advertised in original [AGENTS.md](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/AGENTS.md): pnpm run test, pnpm run typecheck, pnpm run build; actual supported developer workflow requires installed dependencies and model credentials for real-API tests. **None run** in this plan-only review. Proposed disposable fixtures/test cases:

1. Worker reports complete on a task with an externally failing acceptance artifact; reviewer cannot certify and a properly authorised next round receives a corrective input.
2. Worker reports complete when independent artifact/test passes; distinct reviewer is permitted to certify, and the decision is recorded separately.
3. Reviewer is missing, unavailable, shares only worker-provided evidence, or has stale Goal id/revision; no invented independent certification or unauthorised goal mutation occurs.
4. Parent/user pauses or revokes right: reviewer cannot override control; attempt fails closed with an attributable result.
5. Reviewer disabled: ordinary Goal and Ralph modes continue with accurately labelled self-reported completion.
6. Matched cost/outcome comparison vs deterministic tests, human review and A1 plugin; if either matches correction with less implementation/maintenance burden, stop first-party B1.

**Positive result needed for reconsideration:** real false-success reproducer, unmatched verified outcome through B1, actual independent actor/authority/feedback closure, and tests showing A0/A1 insufficient. **Negative falsifier:** simple tests or supported external plugin produce the same effect, or required first-party hook cannot be made lawful. No real false-success run, benchmark, cost estimate or test result was produced.

## 5. Decision and post-verdict historical comparison

Canonical P0 remains NO_QUALIFIED_C_TARGET; conditional P1 evidence and simpler option comparator; P2 NONE. Source-first independent decision: scoped **NO_GO / NO_USEFUL_CHANGE**. The old [pre-rerun case](https://github.com/opensiro-contributions/deepseek-harness/blob/37cbf1f044059dfca9e61d0f7c2c8f0ef5222851/.opensiro/issues/independent-goal-verification-20261119/roadmap.md) was read only after this result and agreed on NO_GO; the new technical observation adds the current direct-complete/post-notice authority limitation. No Index regrade, external Issue or PR, fork public Issue or product implementation. Upstream [#58](https://github.com/opensiro/upstream/issues/58) owner state ACTIVE/ALLOW permits only this internal case update. AI-assisted, no independent human test.
