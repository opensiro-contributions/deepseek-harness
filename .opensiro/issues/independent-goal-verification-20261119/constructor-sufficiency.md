# DeepSeek Harness — source-native protected Goal completion technical contract

**Canonical storage:** `opensiro-contributions/deepseek-harness@opensiro/meta:.opensiro/issues/independent-goal-verification-20261119/constructor-sufficiency.md`.
**Level 1 / Human decision Issue:** [issue.md](issue.md).
**Canonical decision receipt:** [roadmap.md](roadmap.md) — source of truth for accepted Index states, P0/P1/P2, proposal GO and research NEEDS_EVIDENCE. The historical vector is not duplicated as a second six-row table.
**Stage:** PLAN_ONLY / source-grounded proposal, independently unverified. **DRAFT — NOT PUBLISHED**; code and tests NOT_RUN, not shipped, and not a new Index assessment.

## 1. Function-specific construction boundary and methodology checks

**Source and mode boundary:** First-party `deepseek-ai/deepseek-harness` `master@2e39e70496aa02986ca6a820c5d497e816b69d7e` ([source](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/README.md)), observed 2026-11-20, with `GoalService` backed by the owning Agent's durable Session and optional Goal tool, goal-round driver, Team, Ralph and Auto Review compositions. The [historical included Index assessment](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md) at review `ddefc45fbc7f8e46dd73185e68295696d1297887` is a separate September source pin. User/deployment and maintainer governance are outside the target runtime S5 boundary.

**Target transition:** S3*=— -> S3*=C

**Six-function dependencies (S1/S2/S3/S3*/S4/S5):** S1 AgentLoop executes tasks and returns tool results; S2 Team manages shared board dependencies/CAS; S3 Lead/user manages current assignments and goals; **S3*** must receive evidence independent of the completion-claiming worker and return a decisive correction; S4 future adaptation is not involved; S5 user/deployer limits must not be overruled. Existing current closure and the historic grades remain the canonical receipt's facts; no parallel assessment table is maintained here.

**Function witness:** The disturbance is a model-reported successful Goal whose real task evidence may be insufficient. In the opt-in composition, a developer-appointed independent reviewer compares actual tests/artifacts against the objective and may `allow`, `deny` or `hold` on exact live Goal ID/revision. A permitted decision changes the durable state; a rejection leaves the Goal non-complete and gives the model/parent an actionable reason for later authorized correction. The reviewer does not invent parent authority.

**Counterfactual owner test:** Without a separately installed reviewer, GoalService and its model tool can still transition to complete after ordinary phase/CAS checks, but no **distinct independent choice based on external task evidence** is made. A transport-only hook, generic warning or a post-completion notification is not S3*=C.

**Possible methodological negative control:** A human or deterministic test-based acceptance step may be sufficient for many deployments; a historical missing S3* is not a product defect. No original evidence proves intentional exclusion. Changing the bounded system/recursion level or proving a supported shipped C should prompt an Index-owned review rather than silently regrading the case.

**Contributor / maintainer priorities:** [Original CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) encourages plugins and states external PRs are not accepted presently. [Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) reports premature model completion as one user experience; it does **not** establish maintainer approval. Additional expressed maintainer product priority: `NOT_STATED`.

## 2. Source-pinned baseline and parallel native Track A / on-top Track B

**Original native workflow:** [`tool-goal/src/index.ts`](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) dispatches `update_goal(... action="complete")` to synchronous `ctx.goals.complete(execution.agent, ref)`. [`GoalService.complete`](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) validates the live agent, exact GoalRef and allowed phase using `transition`, then `commitCurrent` and `commitSnapshot`; `commit` appends `goal/change` to Session and emits `goal/changed` **after** append. The accepted notification cannot veto a previously persisted completion. [Goal replay contract](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/subsystems/goal.md) is strict and versioned.

**Closest existing solution:** A0 = ordinary native Goal state plus human review and/or task-specific deterministic tests. A1 = external [bpc-oss/dsh-verification](https://github.com/bpc-oss/dsh-verification) with its [vendored pre-commit guard patch](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs), proposed as a comparator; compatibility and third-party tests are **NOT_RUN** by OpenSiro. The built-in [Auto Review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md) is a pre-tool authorization gate, not independent final acceptance of all Goal state writers.

**Relevant original Issues/PRs:** [Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) is an **OBSERVED USER REPORT** asking for evidence verification, not a shipped fix or maintainer-backed plan. Current original GitHub metadata reports `has_issues=false`, `has_pull_requests=false`, `has_discussions=true`; original PR REST listings 404, so no exhaustive PR history is claimed. An earlier supposed `#8736 PR` was actually a Discussion reference; do not use it as implementation evidence. Existing external verification code is **EXPERIMENT**, not a first-party shipped port.

| Required C link or operator outcome | Track A current source and status | Track B smallest native integration | Falsifier |
| --- | --- | --- | --- |
| Exact owner and goal-state eligibility | [GoalService](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) already enforces live agent, GoalRef revision, phase and durable Session state (**SHIPPED**) | Reuse; no new task board or identity system | Existing validation missing only if the source readback changes |
| Independent decision before commit | Existing `goal/changed` arrives after `session.append` (**SHIPPED**); external verifier needs [vendored patch](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs) | Optional scoped synchronous `complete` pre-append veto/register-dispose port at service level, driven by an independently installed verifier | An unpatched plugin already blocks all direct and model-tool completions |
| Returned result and replay-safe attribution | [Tool goal](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) conveys service result; [Session](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/subsystems/goal.md) requires versioned events | Typed reject/hold reason, bound permit/audit reference, explicit schema compatibility if persisted | Failure only logs a warning or a permit can be forged/replayed after Goal changes |

**On-top distinctness:** The proposed original-native delta is *not another verifier*. It is a protected, plugin-composable `GoalService.complete` decision boundary that might remove the need to edit a vendored copy for enforcement. An ordinary `tools/pre-execute` listener alone is insufficient if a direct first-party `ctx.goals.complete` caller still commits. The full S3* function requires independently sourced evidence, a distinct reviewer decision, first-party effect and corrected future work; merely exposing the guard is insufficient.

**Source ambiguity / rights blockers:** The reported user failure is not reproduced; the vendor patch's compatibility with the current original SHA and maintenance burden are unmeasured; the exact plugin reviewer and permit format are future design. `NEEDS_EVIDENCE`, not source/identity BLOCKED. External PR publication is prohibited by current contributor instructions and requires separate explicit owner consent if an allowed route later exists.

## 3. Minimal complete S3* first-party C construction

**Required property:** A function-specific first-party construction path through which a developer can install an independent goal-completion reviewer with lawful evidence-based choice, an effect on the real Goal outcome, and returned feedback for another operational step. A generic observer or tool-level guard alone does not establish C.

**Physical interface count is NOT prescribed.** The logical obligation may be fulfilled by reusing the entire GoalService with one optional guard API and a separately composed reviewer. Do not copy Paperclip's five-port pattern or create unrelated infrastructure.

| Necessary native component or port | Current file/API | Smallest proposed edit / integration | Legitimate owner, effect and return |
| --- | --- | --- | --- |
| Goal completion boundary | [`GoalService.complete → transition → commitSnapshot`](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts), synchronous; validates phase/revision | Register/dispose optional typed pre-append `complete` guard; execute after validation and before `session.append('goal/change')` | Separate reviewer decides; GoalService enforces; denial returns an error without durable complete |
| Evidence binding and effect record | [`GoalSnapshotChangeMeta`](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/subsystems/goal.md) version 1; no reviewer permit | Reviewer plugin binds signed/scoped verdict to Session/Goal/revision and actual external artifact/test provenance; if permitRef enters the log, design an explicit compatible event version and strict replay | On allow one attributable completion commits; on deny/hold the Goal stays active and feedback enables authorized correction |

**Native-specific design advice (not a new gate):** This is specifically DeepSeek Harness's `update_goal` → `GoalService.complete` → `goal/change` edge, not a portable "independent audit controller". A callback from `goal/changed` is too late; a pre-tool checker alone does not protect direct service calls. Preserve the synchronous public method shape unless a source-supported migration is explicitly designed.

**Architectural C-sufficiency argument:** Two alternatives are available: (A0) no runtime change with after-the-fact acceptance and correction, or (A1) existing external reviewer with a vendor patch. The proposed B1 adds an **optional original-native pre-append API** that a separately packaged independent reviewer can call via a bounded permit/decision, while GoalService remains the sole state authority. With reviewer absent, legacy complete behavior is identical. In enforce mode, rejection occurs before any `goal/change`; the tool/service conveys a reason, and a later lawful agent/parent step can correct work and retry. This is *proposed* closure, not a shipped actor, measured utility or accepted grade.

**Explicit non-goals:** No default-on independent reviewer, mandatory model/network call from synchronous `complete`, duplicated Goal state, broad S4 controller, new S5 policy owner, revised Project acceptance of external PRs, or promotion of parent decisions to agent autonomy.

**Implementation dependency graph:** P1 pin/reproduce user symptom and verify unchanged A0 + vendor-patch A1 → propose/test B1 pre-commit API and independently configured reviewer with direct-call/return coverage → validate versioned Session replay and owner boundaries → compare operational outcomes and total maintenance. P0/P1 are derived from [roadmap.md](roadmap.md), not reassigned here.

## 4. Priorities, optional alternative and stopping rules

**P0 and P1:** P0 is the **minimal optional protected GoalService completion seam enabling composed S3***, not a new built-in evaluator. P1 is source-pinned reproduction, permitted actor/parent rights, positive/negative direct service and tool tests, strict replay and matched A0/A1 cost/output comparison. No original implementation is authorized by this research.

**P2:** `NONE`. No mandatory second function or separate five-port S4/S5 path.

**Alternative path:** Use manual/CI completion acceptance if that solves the operator's same task; or retain the external vendor-patched plugin if it is portable, safe and cheaper to maintain. Product adoption is a maintainer decision, not a VSM score.

**Stop:** Do not advance B1 if a supported unmodified extension already guards all completion writers, if the composed reviewer cannot exercise a separate lawful decision with real independent evidence and feedback, or if its effect or replay breaks valid parent authority. Absence of measured demand/cost is a research limitation, not an automatic NO_GO; an external PR prohibition is an independent hard publication gate.

## 5. Future source-native acceptance — derive tests, do not copy a matrix

**Native test commands and entry points:** Original [AGENTS.md](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/AGENTS.md) prescribes `pnpm run test` and `pnpm run typecheck`, with [goal-specific tests](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/tests/goal.spec.ts) and [model-facing goal tool](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts). Exact future focused runner selection must be verified locally. All tests for this proposal **NOT_RUN**; original native tests are not claimed passing.

**Positive functional closure:** Separate reviewer verifies an exact human task/test artifact rather than model prose; a valid permit on current Goal ID/revision leads to exactly one durable `complete` and a replayable attribution. After a previous denial, the model/parent sees evidence needed, performs authorized correction and can complete on valid evidence.

**Independent alternative (where applicable):** Under the same proposed enforce mode, one independently evidenced `reject/hold` and one `allow` on valid but different live states produce different lawful outcomes. The goal service alone cannot synthesize the independent choice from worker self-report.

**Negative authority and compatibility (where applicable):** Missing/forged/stale permit, changed goal revision, revoked reviewer, failed verifier, parent pause, teardown and cancellation must not append a false `complete` in enforce mode. No-guard/advisory behavior must remain compatible with existing synchronous callers, Session replay, projection schema and current approval policy.

**Matched native alternative:** Reproduce the same premature-complete scenario under A0 unchanged service with human/CI check, A1 vendor-patched verifier and B1 optional native extension. Compare false accepts/rejections, subsequent correction, delivery, review and maintenance work; no winner or savings can be claimed in advance.

| Proposed native case | Source-backed setup / future command | Expected effect and return | Falsifier or stop |
| --- | --- | --- | --- |
| Premature completion, NOT_RUN | Extend [Goal tests](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/tests/goal.spec.ts) to invoke `ctx.goals.complete` with rejected permit | No `goal/change` complete; goal revision unchanged; reason visible | Mutation appended despite guard |
| Authorized completion, NOT_RUN | Same Goal test with independently verified positive permit | One durable complete; attribution survives restart | Forged permit passes or replay fails |
| Direct-call/tool parity, NOT_RUN | Test `ctx.goals.complete` and `update_goal` via [tool](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) | Both reach guard; no bypass | Only tool route is protected |
| Compatibility and parent rights, NOT_RUN | Test no guard, reviewer error, stale revision, teardown and parent pause | Legacy no-guard behavior; enforce-mode fail-closed where applicable | Parent loses control or valid old Sessions break |

**Example IDs such as AC-01…AC-09, fixed ports and universal test counts are deliberately not supplied.** Only source-applicable cases matter. Execution evidence is **NONE / NOT_RUN**.

## 6. Proposal verdict, falsification, evidence ownership and handoff

**Proposal-stage decision:** GO

**Research disposition:** NEEDS_EVIDENCE

**GO + NEEDS_EVIDENCE is valid** for the proposed lawful, complete and falsifiable C hypothesis without native tests or cost data. Do not automatically turn NEEDS_EVIDENCE into NO_GO or BLOCKED. Actual product use, implementation permission and accepted Index C remain separate future actions.

**Primary falsifier:** A supported unmodified service/plugin already enforces all direct and tool completion routes, or the reviewer cannot own an independent decisive choice based on separate evidence, or no actionable return path exists. **Validation state:** `NOT_RUN`, matching the receipt, with no claimed product tests.

**Ownership of truth:** Profile defines VSM semantics; Skills defines classification; Index owns accepted historical grades and any later reassessment; the original maintainers own runtime implementation and adoption; [roadmap.md](roadmap.md) owns these case-level research decisions. This technical contract only details proposed construction.

**Cost status:** `NOT_MEASURED`. Cost saving and operator value must be established by a future matched experiment.
**Next permitted action:** If authorized, prototype and test on the recorded original HEAD as a separate task; do not publish an original PR/Discussion while contributor rules forbid PRs or without exact current-conversation permission. **Human backlink:** [issue.md](issue.md); **case receipt:** [roadmap.md](roadmap.md).

**No original external Issue/comment/PR**, public fork Issue/PR, product code, new authority grant or accepted Index revision follows from this draft. Fork `PAUSE/STOP` blocks unauthorized writes, and exact public consent remains independent. **AI disclosure:** Prepared with AI assistance, without presumed native test execution, endorsement or independent human review.
