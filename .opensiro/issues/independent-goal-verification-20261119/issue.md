# DeepSeek Harness — optional evidence gate before goal completion (Opensiro roadmap)

**PLAN_ONLY · proposal-stage GO · research NEEDS_EVIDENCE · DRAFT — NOT PUBLISHED**

**One-sentence proposal:** Expose an optional guard at DeepSeek Harness's existing goal-completion boundary so an independently configured verification plugin can reject premature completion before the goal is durably marked complete.

**Canonical decision receipt:** [roadmap.md](roadmap.md) — source of truth for the accepted Index vector, chosen target, P0/P1/P2, verdict, and evidence status.
**Technical companion:** [constructor-sufficiency.md](constructor-sufficiency.md) — source-native design and future test contract; the two documents share this case's receipt.
**Working fork:** `opensiro-contributions/deepseek-harness` · **Case:** `.opensiro/issues/independent-goal-verification-20261119/` on `opensiro/meta`.

## 1. Why Opensiro and central accepted VSM assessment

Opensiro uses the Viable System Model to identify who makes, enforces, and learns from organizational decisions. Applying this method to DeepSeek Harness is **research**, not a claim that DeepSeek must adopt VSM or that this proposal improves quality or reduces costs. This case starts with a real reported goal-completion problem and tests whether a developer-composable independent check is feasible using the harness's own interfaces.

### Central starting point — accepted Index, not the target

> **ACCEPTED HISTORICAL INDEX — not current-HEAD grades or proposed after-states**
>
> **`S1=A · S2=A · S3=A(P) · S3*=— · S4=— · S5=—`**
>
> [Accepted assessment](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md) at Index `c2e43bf4750841277b3e58d8ba80314121734764`, blob `257a55619d474d8a86a49de6dffa93a4426d7b62`; `review_ref=ddefc45fbc7f8e46dd73185e68295696d1297887`, reviewed **2026-09-18**, Profile **0.2.2**, Skills Methodology **0.3.1**.

**Repository-wide audit:** Original `deepseek-ai/deepseek-harness` default `master@2e39e70496aa02986ca6a820c5d497e816b69d7e` ([immutable source](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/README.md)), observed **2026-11-20**. System in focus: first-party model-driven Agent and durable Session, opt-in Team, Goal, Ralph and Auto Review compositions; one team is the relevant recursion boundary. Reviewed [architecture](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/architecture.md), [AgentLoop](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/core/agent-loop/README.md), [Team](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/team/agent-team/README.md), [Goal](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/README.md), [Goal tool](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/README.md), [Ralph](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/tool-ralph/README.md), [Auto Review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md), goal tests, [CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md), GitHub Discussions and repository issue/PR availability. Developer governance outside the runtime is not credited as S5.

| Function / plain-language role | Historical Index state | Current source-backed owner/closure | Candidate / uncertainty and priority |
| --- | --- | --- | --- |
| **S1 · Operations** — agent doing the work | A | [AgentLoop](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/core/agent-loop/src/agent.ts) executes model/tool steps and returns results to the Session | NO_TARGET: current agent-driven operations already exist |
| **S2 · Coordination** — avoiding conflicting work | A | [Agent Teams board](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/team/agent-team/src/task-board.ts) provides task dependencies, CAS and overlap warnings in opt-in Team mode | NO_TARGET: no independent new coordination chain selected |
| **S3 · Current management** — regulating ongoing commitments | A(P) | Team Lead assignments plus supported parent task controls; [Team service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/team/agent-team/README.md) | NO_TARGET: preserve agent/parent decision boundaries |
| **S3* · Independent review** — checking outcomes with separate evidence | — | [Goal](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) accepts a completion request at the service boundary; [Auto Review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md) screens tool permissions, not completed-goal evidence | **P0 proposed C**: opt-in independent evidence-backed completion guard, unimplemented |
| **S4 · Future adaptation** — external and future changes | — | Plugins, web access and workflows exist, but no distinct future-adaptation closure established here | DEFER: no source-backed selected S4 hypothesis |
| **S5 · Identity/policy** — ultimate legitimate authority | — | User/deployment controls are external constraints, not a claimed runtime S5 owner | NO_TARGET: no new policy owner or transferred parent authority |

**Interpretation:** `A` means supported autonomous agent ownership; `C` means a function-specific first-party path enabling developer composition of such an owner; `P` is an evidenced parent-governed mode; `A(P)` / `C(P)` add that parent mode; `—` is a bounded absence in the assessed system; `?` is unresolved evidence. These are **ownership categories, not quality ranks**. A historical `—` is not a bug report or a mandate to build a feature.

**Priority rationale:** The concrete [user Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) reports early model-declared completion; original GoalService has a directly identifiable state transition. The external [dsh-verification](https://github.com/bpc-oss/dsh-verification) already explores an independent checker through a vendor patch, giving an alternative to compare. This makes a small, testable S3* hypothesis more specific than new S4/S5 subsystems.

**Deliberate exclusions / methodology challenge:** No source proves the project intentionally excludes an independent completion check; intent is **UNVERIFIED**. The user/deployer retains authority to configure enforcement, and ordinary parent control cannot be reclassified as autonomous S5. No Profile/Skills amendment is proposed.

**Contributor / maintainer interests (OPTIONAL):** DeepSeek [CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) encourages independent plugins and says external PRs are not currently accepted; the user's Discussion is a user request, **not** maintainer adoption. Other maintainer product preferences: **NOT_STATED**.

## 2. Selected construction hypothesis and operator outcome

**Target transition:** S3*=— -> S3*=C

**Function-specific disturbance:** A Goal agent can call `update_goal` with action `complete` before an independently observed task outcome is satisfied. [Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) reports repeated restarts after premature completion; this is **OBSERVED user testimony**, not an OpenSiro-reproduced failure.

**Proposed C capability (P0):** A developer can install a separate verifier that inspects actual task/test evidence, permits or rejects an exact goal completion, and returns a reason that the active agent/parent can act on. The harness exposes only the minimal protected completion seam; it does not ship a mandatory reviewer.

**Best native operator alternative:** Without new native code, the user can inspect deliverables and run task-specific acceptance tests or use an existing [Goal service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/README.md) without enforcement. The external [dsh-verification](https://github.com/bpc-oss/dsh-verification) uses a vendored patch for its enforce path; compatibility with this original revision is **NOT_RUN**.

**Expected user benefit:** If the hypothesis works, false completion is not durably recorded and the same Goal can be corrected without recreating it. Reliability, adoption, effort and savings remain **NOT_MEASURED**.

**Architectural sufficiency argument:** The first-party `GoalService.complete(agent, ref)` transition checks the live goal, then `commitSnapshot` writes `goal/change` and notifies `goal/changed` afterward ([source](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts)). A read-only post-event listener cannot veto that commit. An optional pre-append, revision-bound guard plus a *separately installed evidence reviewer* could supply independent decision, enforcement and corrective feedback; the guard API **alone** does not constitute S3*=C.

## 3. Existing native work versus missing construction

**Track A — native coverage:** Shipped: Goal lifecycle, revision checks, `update_goal` tool and round driver; **SHIPPED/opt-in:** Team and experimental Auto Review; **EXTERNAL experiment:** [dsh-verification vendor patch](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs), not a first-party shipped interface. [Discussion #10471](https://github.com/deepseek-ai/deepseek-harness/discussions/10471) is a user report, not an accepted upstream feature issue. GitHub metadata currently has Issues/PRs disabled; there is no supported open PR diff to rely on, and no exhaustive claim about historical PRs.

**Track B — independent on-top C construction:** Source-native optional synchronous guard in `packages/goal/goal/src/index.ts`, reached by both the model tool and direct `ctx.goals.complete` callers. A separately composed plugin owns evidence, verdict and audit; registration/disposal and replay compatibility belong to the contract, not to a generic new controller.

| C-sufficiency requirement | Already present / proposed in original (A) | What still must be constructed (B) |
| --- | --- | --- |
| Validated goal identity and state | [GoalService](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) checks exact ID/revision/phase and persists changes | Optional pre-commit decision boundary for `complete`, with no default behavior change |
| Independent verdict and operational return | [Goal tool](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) returns service outcomes, but model self-report alone is not independent acceptance | Separate reviewer produces permit/reject/hold from non-self-reported evidence; rejection leaves Goal unchanged and reaches agent/parent |
| Durable proof and compatibility | [Session goal contract](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/subsystems/goal.md) uses strict `goal/change` versioned replay | Verify attributable approved completion without a silent v1 event-schema change |

**Distinctness and falsifier:** An ordinary pre-tool approval check might miss direct service completion. Conversely, if a supported unmodified plugin can already veto **all** relevant completion callers, or unchanged native tests/manual approval provide the same result more cheaply, there may be no useful native delta. Existing community work is a comparator, not evidence that maintainers have rejected or approved this approach.

## 4. Priorities and minimum sufficient result

- **P0:** An optional, first-party GoalService completion guard enabling independently composed `S3*=C` acceptance with returned feedback; do not implement a bundled mandatory verifier.
- **P1:** Reproduce the reported failure on pinned source; compare unchanged human/CI acceptance with the vendor-patched plugin; test direct callers, valid/invalid evidence, stale revision, authority, disposal and Session replay.
- **P2:** NONE; no second function or unrelated policy mechanism.

**Proposed C-sufficiency verdict:** `PROPOSED_C_SUFFICIENT` as an **untested architectural hypothesis only**, conditional on an independently installed decisive reviewer and actual correction loop. A port or API alone is not C, and no Index reclassification follows.

## 5. Proposed acceptance and stop gates

**Future positive test:** In enforce mode, a separately configured verifier receives independently obtained passing evidence for an exact Goal, approves `complete`, and a durable completion with an attributable review is visible on restart. A prior rejected completion should have returned an actionable error, allowing an authorized correction.

**Future negative test:** Missing/rejected/forged evidence, stale Goal revision, reviewer error, plugin teardown or a parent authority prohibition does **not** append `goal/change` as `complete`. A no-guard deployment must behave like unmodified GoalService.

**Proposed falsifier:** An unpatched first-party extension already prevents all direct `complete` calls, or matched human/tests/vendor-patch alternatives achieve the same outcome at lower total maintenance and integration cost.

**Validation state:** `NOT_RUN`. The cited third-party tests were read, not independently executed by OpenSiro.

## 6. Independent paths

**Original-native contribution:** Prefer an optional extension seam over duplicating an existing verifier. No automatic external PR or discussion is justified; DeepSeek currently does not accept external PRs.

**Profile / Skills:** NONE at present; a real classification counterexample would be handled in the owning methodology repositories, without changing this historical Index result.

**Domain fork:** A lawful MIT-based experimental fork/plugin may test the integration without imposing it on the original maintainers. Do not claim a public fork issue or original submission exists.

## 7. Cost hypothesis

Compare the same false-completion and correct-completion tasks under unchanged manual/CI checks, existing vendored plugin, and a minimal native guard plus independent reviewer. Count implementation, integration, testing, compatibility and maintenance work. **Cost status: `NOT_MEASURED`**; no savings or measured quality claim.

## 8. Decision / handoff

**Proposal-stage decision:** GO

**Research disposition:** NEEDS_EVIDENCE

**Decision reason / next permitted step:** A reported user failure and the exact GoalService state boundary support an optional verification proposal. Next, if independently authorized, test the three alternatives on the pinned original; do not publish or change product code merely because this draft exists. The maintainers choose product fit.

**Agent/developer handoff:** [constructor-sufficiency.md](constructor-sufficiency.md) for exact source interfaces and tests; [roadmap.md](roadmap.md) for canonical evidence and statuses. The P0/P1/P2 and result are derived from the same case.

**Rights and publication:** Original MIT [LICENSE](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/LICENSE), [CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) currently declines outside PRs; no CLA/DCO exemption or AI acceptance inferred. Verified matching fork `owner_control=ALLOW`, `attention=ACTIVE` on `opensiro/meta`; this permits only authorized internal metadata work. **No public fork Issue**, original Issue/Discussion/comment/PR, code change, grade change or authority grant is authorized by this draft. Publication requires exact current-conversation approval of destination, action and complete text. `PAUSE/STOP` overrides ALLOW.

**AI disclosure:** Draft prepared with AI assistance. No original runtime test, maintainer endorsement, independently measured benefit or external publication is claimed.
