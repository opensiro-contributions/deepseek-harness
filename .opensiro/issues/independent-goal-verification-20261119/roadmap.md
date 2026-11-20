# DeepSeek Harness — Upstream #58 v0.18 proposal-gate, evidence amendment (2026-11-19)

- Receipt contract: proposal-gate
- Original repository: deepseek-ai/deepseek-harness
- Original HEAD: 2e39e70496aa02986ca6a820c5d497e816b69d7e
- Observed at: 2026-11-19
- Accepted Index assessment: https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md
- Accepted assessment blob SHA: 257a55619d474d8a86a49de6dffa93a4426d7b62
- Accepted review ref: ddefc45fbc7f8e46dd73185e68295696d1297887
- Accepted reviewed at: 2026-09-18
- Profile version: 0.2.2
- Assessment methodology version: 0.3.1
- Accepted Index commit: c2e43bf4750841277b3e58d8ba80314121734764
- System in focus: first-party DeepSeek Harness Agent/Session, optional Goal/Team/Ralph/Auto Review and Cordis composition, without elevating parent policy
- Historical vector: S1=A · S2=A · S3=A(P) · S3*=— · S4=— · S5=—
- Accepted VSM vector: S1=A · S2=A · S3=A(P) · S3*=— · S4=— · S5=—
- Matching fork: https://github.com/opensiro-contributions/deepseek-harness
- Metadata branch: opensiro/meta
- Fork owner control: ACTIVE / ALLOW; owner event 20261119T182226Z--owner-upstream58-active
- Repository-wide source map: AgentLoop Session S1; Team task-board S2; Lead parent S3; Goal/Ralph and Auto Review S3* comparison; Cordis tools profiles; S4 and S5 negative ownership; public Discussions not PRs
- Evaluation object: opt-in independent adjudication of model-declared goal complete, with protected durable outcome and feedback at the harness goal boundary
- Existing-work overlap: native Goal stores self-declared complete before changed event, tests/human acceptances; bpc-oss/dsh-verification implements independent evidence gate but needs vendored GoalService guard
- Our on-top contribution: evaluate only a typed optional native GoalTransitionGuard pre-commit hook and permit attribution enabling composed third-party S3* reviewer; do not build duplicate first-party evaluator
- Incremental benefit: eliminate per-upgrade vendor patch for protected completion and allow bounded plugin-owned independent audit before durable false success; benefit relative to A0/A1 NOT_MEASURED
- Decision scope: GO to evidence-backed bounded native port research, not an implemented C or proposal for default enforcement, policy transfer, maintainer acceptance or new Index grade
- Priority rationale: user Discussion #10471 reports premature model-complete with repeat goals; vendor patch plus first-party commit-after-notify source proves missing precommit boundary; S1/S2/S3 already have owners, S4/S5 unproven
- Target transition: S3*=— -> S3*=C
- P1 dependencies: source-pinned native reproducible false- and true-completion tests; port prototype; A0 deterministic and A1 vendored plugin comparators; guarded owner and backward compatibility; maintainer rights
- P2 optional: NONE
- Proposed C construction: optionally compose distinct independent tool-evidence reviewer and certify/reject/hold actor with GoalTransitionGuard veto BEFORE durable complete, typed permitRef in committed event, later authorised correction and durable feedback; native port alone is not C
- C sufficiency falsifier: original unpatched supported plugin already enforces all completion paths, or A0/A1 matches full outcomes more cheaply, or no lawful independently owned return or parental control preserved
- Scenario basis: OBSERVED
- Proposal-stage decision: GO
- Research disposition: NEEDS_EVIDENCE
- Proposed validation: missing and correct acceptance evidence; direct GoalService calls vs tool calls; stale GoalRef; forged permit; crash/replay; parent override; adviser compatibility; compare A0/A1/B1 cost/outcomes
- Validation state: NOT_RUN
- Proposal falsifier: an unmodified GoalService supported plugin can already veto direct ctx.goals.complete before commit at lower cost, or production verifier cannot be justified over existing plugin plus local tests
- Result: NEEDS_EVIDENCE
- External issue: DRAFT — NOT PUBLISHED
- Public fork Issue: DRAFT — NOT PUBLISHED
- Native tests: NOT_RUN
- Cost status: NOT_MEASURED

## Identity and pins

This is an **evidence-driven amendment of the same independent review**, not a new independent fresh-context run. Original-first 2026-11-19 v0.18 study reached NO_GO before historical comparison, recorded in [previous reconciled decision](https://github.com/opensiro-contributions/deepseek-harness/blob/39bc69e4149528ab89deb60a6ed03f81739b0178/.opensiro/issues/independent-goal-verification-20261119/roadmap.md); later public discovery found both [actual user feedback](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) and [external verifier code](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs), materially changing qualified C target. Original `2e39e70496aa02986ca6a820c5d497e816b69d7e` and canonical Index `c2e43bf4750841277b3e58d8ba80314121734764` remain fixed; historical six-function vector unchanged. The newly proposed `S3*=— -> S3*=C` **is not a new assessment**.

## Rights and authority

Fork `opensiro/meta` state read back ACTIVE/ALLOW under the owner's #58 activation; only internal canonical case records updated. [Original CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) says no external PRs at present; original repo has [`has_issues=false`, `has_pull_requests=false`, `has_discussions=true`](https://api.github.com/repos/deepseek-ai/deepseek-harness). External third-party Discussion, issue, comment, PR or public fork proposal require separate exact conversation consent. No external submission, fork GitHub Issue or original product patch has been published; MIT notices remain in the original repository.

## Existing work / overlap

- Original [Goal service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) has optimistic revision guards, self-reported completion, durable `goal/change` append, then `goal/changed` notification. Original pre-commit independent gate is absent in the pinned source.
- First-party Goal tools, goal-round driver, Ralph and Auto Review provide continuation, worker self-report and pre-tool screening but not final independent certification.
- [Direct user report Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) describes two model-owned premature goal `complete` actions and repeated same-task goal restarts; attribution is user report, not OpenSiro-reproduced native failure.
- [dsh-verification external plugin](https://github.com/bpc-oss/dsh-verification) already supplies an optional evidence-based `enforce` reviewer; its [patch](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs) modifies vendored `dsh-goal` to add a pre-commit guard and `permitRef`, and its [tests](https://github.com/bpc-oss/dsh-verification/blob/main/packages/dsh-verification/test/seam-e2e.test.ts) claim direct service denial and replay. Integration compatibility and tests on current original pinned source remain unverified, and plugin's default advisory mode does not enforce.
- [Original PR listing](https://github.com/deepseek-ai/deepseek-harness/pulls) shows restricted creation and 0 current open/closed; pull REST API 404 follows disabled feature, not proven empty historical PR archive. `/discussions/8736` is a community plugin Discussion, **not a PR #8736**. Relevant current proposal demand belongs in Discussions; exhaustive community overlap remains bounded.

## Function ownership

- S1 disposition: model AgentLoop drives tool execution and feedback; existing A covers target operational function
- S2 disposition: Team shared board, dependencies, CAS and messages manage interference; existing A not target
- S3 disposition: Team Lead and user/parent task management cover current management; A(P) not target
- S3* disposition: accepted historical —, proposed native optional guarded goal-completion port for distinct composed reviewer -> C remains unproved, GO at proposal stage only
- S4 disposition: no evidence of independent future environment adaptation and return loop; no C target
- S5 disposition: deployment policy and parent authority reserved; no justified local final-policy transfer

## Parallel contribution-on-top review

| Operator task | Track A: native / simplest comparator | Track B: smallest source-native optional increment | Objective falsifier |
| --- | --- | --- | --- |
| Identify false completion | Model reports `complete`, human/test acceptance detects after fact | Separately configured reviewer binds original objective and real tool/test evidence, not self-report | A0 tests catch and correct same failures at lower cost |
| Authority before durable state | GoalRef phase/revision and post-change event; external plugin needs vendored patch | Synchronous registered GoalService `complete` guard, no append until independent permit; no guard default unchanged | Unmodified native hook already exists or all service direct callers can be stopped without native patch |
| Actionable loop | Goal rounds and parent can resume or create follow-up; A1 plugin has proof-of-concept | On deny/hold keep active, provide bounded feedback and later legally authorised retry; on allow persist permitRef in strict replay | Denial only logs or cannot trigger authorised correction; parent rights bypassed |
| Distribution | Original declines PRs; plugin fork/patch maintained separately | Portable typed API designed for opt-in plugin use with no default evaluator | Change imposes significant breaking maintenance or no measured benefit vs A1 vendoring |

No native change or external maintainer acceptance was made. The smallest valid C chain needs **distinct independent decision owner + enforceable boundary + feedback**; port alone is enabling infrastructure, not a C-grade claim.

## Capability priority

**P0:** `S3*=— -> S3*=C`, **GO / NEEDS_EVIDENCE** to a source-grounded original-native optional pre-commit Goal guard interface only. **P1:** reproduce the reported premature completion, port/replay/cancellation tests on pinned source, check A0 human/tests and A1 vendor-patched plugin costs and true/false results. **P2:** NONE. Do not expand into broad autonomous system redesign or force default approval.

## Implementation options

**A0:** task-specific deterministic acceptance checks and user approval, no new runtime port. **A1:** existing dsh-verification with a vendored GoalService patch, subject to version-compatible proof. **B1 (candidate):** optional typed registered guarded `complete` pre-commit veto and attributable `permitRef` with correct CAS, replay and parent boundaries; compose reviewer as external plugin. **B2 (reject):** ship built-in mandatory verifier, duplicate task-store, or change S5. The *minimum* native code change is an extension seam, not an entire controller implementation.

## Specification and domain alternatives

Historical Index assessment unchanged, no Profile or Skills spec change. Generic out-of-tree plugin integration alone is not proof of independent S3*; distinct reviewer must have actual evidence and authority to block false certification and return actionable feedback. Because original maintainers explicitly prefer plugins and decline PRs now, native-port adoption is **policy blocked** unless contributor conditions change; GO is an internal proposal research result, not approval to post.

## Cost experiment

Pinned original `2e39e70496aa02986ca6a820c5d497e816b69d7e` and external plugin revision independently; test (i) invalid declared completion, (ii) valid evidence, (iii) direct `ctx.goals.complete` bypass, (iv) stale revisions/parent pause, (v) missing or crashed reviewer, (vi) disable/advisory compatibility, (vii) replay and attribution. Measure false accepts/rejects, later corrective action, integration/upgrade effort, test latency and model requests for A0/A1/B1. **None run by OpenSiro.** Reported third-party tests/benchmarks are not independent proof. Costs **NOT_MEASURED**.

## Delivery and publication

**Current proposal-stage: GO / NEEDS_EVIDENCE; original-native implementation NOT_STARTED; fork metadata PERSISTED only after validation/readback.** Historical first independent run NO_GO/NO_USEFUL_CHANGE remains immutable as [prior commit]([previous reconciled decision](https://github.com/opensiro-contributions/deepseek-harness/blob/39bc69e4149528ab89deb60a6ed03f81739b0178/.opensiro/issues/independent-goal-verification-20261119/roadmap.md)), updated decision is explicitly a **later evidence-driven reconsideration** within the same chat. Original-specific issue/PR inventory caveat resolved: PR feature disabled and Discussion #8736 is not a PR; broad historical coverage not claimed. The [Human draft](issue.md), [AI contract](constructor-sufficiency.md), and this receipt must remain synchronized. No external communication, no Index promotion, no claimed confirmed C.

## v0.18.1 source-native refinement — 2026-11-20 (same case)

This section is an **additive PATCH_REVIEW** on the existing source-first v0.18.0 case, **not** a new independent first pass, Index reassessment, implemented patch, or new outcome. Readback on 2026-11-20: original `master@2e39e70496aa02986ca6a820c5d497e816b69d7e`, accepted Index review `ddefc45fbc7f8e46dd73185e68295696d1297887` (assessment blob `257a55619d474d8a86a49de6dffa93a4426d7b62`). Historical `S1=A · S2=A · S3=A(P) · S3*=— · S4=— · S5=—` is unchanged.

**Specific end-user outcome.** An operator composing a verifier for a DeepSeek Goal can reject a model's premature `update_goal(..., action="complete")` **before the Session records successful completion**, while retaining the goal and returning a reason for an authorised correction attempt. The existing [model-facing tool](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) calls the synchronous `ctx.goals.complete(execution.agent, ref)`; the [native service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) runs `complete → transition → commitCurrent → commitSnapshot → session.append('goal/change')`, then emits `goal/changed`. A post-commit notification is too late for enforcement. This is a narrower actual interface than a generic independent-audit controller.

**Native Track A vs on-top Track B.** A0 = unchanged GoalService with exact `GoalRef` revision/phase CAS and optional manual/test acceptance **after** self-report. A1 = already described external `bpc-oss/dsh-verification` with vendored patch (compatibility not rerun). B1 = a narrowly typed **opt-in, synchronous GoalService `complete` pre-append guard** registered through first-party Cordis composition, with unregistration on plugin disposal; the separate independently configured reviewer supplies external artifact/test evidence *before* invoking `complete`, and the synchronous guard only verifies a bounded verdict/permit bound to live Session + goal ID/revision + evidence and reviewer provenance. Do **not** block synchronous `complete` on a fresh asynchronous model/network call, bypass direct service consumers with only a tool hook, duplicate Session task state, or change the model's ordinary completion semantics when no enforcement is installed. Any audit `permitRef` written to `goal/change` needs an explicitly compatible versioned schema/replay design; do not casually add an unknown field to persisted version-1 snapshots.

**C closure and falsifiers.** `S3*=C` requires an independently configured, decisively acting reviewer and a returned corrective loop, not merely a guard API or the existing Auto Review (which reviews pending tool permissions, not goal acceptance). Under explicit enforce mode: absent/stale/forged evidence, rejected or cancelled reviews, concurrent goal revision change, plugin removal during a guard, and parent pause/authority conflict must fail closed **without append**. An accepted independent permit may commit once against the exact current revision and must remain replay/audit-attributable; a denied attempt leaves the goal state unchanged and gives model/parent usable feedback. An ordinary deployment without the plugin must preserve current `complete` behavior. Compare against A0 and A1 with tests in `packages/goal/goal/tests/goal.spec.ts` and the Goal tool test path; demonstrate actual user benefit and lower integration burden before recommending adoption.

**Decision preserved:** scoped research `GO / NEEDS_EVIDENCE` for `S3*=— -> S3*=C`, priority P0 above; P1 = native direct-service/tool/replay/parent tests plus A0/A1 comparator; P2 = NONE. Original-native implementation **NOT_STARTED**, tests **NOT_RUN**, effects/cost **NOT_MEASURED**, original discussion request **not independently reproduced**. DeepSeek [CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) presently does not accept third-party PRs; there was **no** external or public-fork publication. Reviewer/maintainer product adoption remains their own decision.
