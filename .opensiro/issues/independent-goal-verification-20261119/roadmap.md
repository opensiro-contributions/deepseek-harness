# DeepSeek Harness — Upstream #58 independent v0.18 roadmap receipt

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
- System in focus: first-party DeepSeek Harness Agent/Session runtime and supported opt-in Teams, Goal, Ralph and Auto Review modes at one harness organization
- Historical vector: S1=A · S2=A · S3=A(P) · S3*=— · S4=— · S5=—
- Accepted VSM vector: S1=A · S2=A · S3=A(P) · S3*=— · S4=— · S5=—
- Matching fork: https://github.com/opensiro-contributions/deepseek-harness
- Metadata branch: opensiro/meta
- Fork owner control: ACTIVE / ALLOW (verified state.json; owner event 20261119T182226Z--owner-upstream58-active)
- Repository-wide source map: Agent loop and session; Teams and task board; Goal service/tool/driver; experimental Ralph and Auto Review; Cordis profiles and events; code/CI, contributor restrictions and current Issue/PR discovery
- Evaluation object: opt-in S3* independent audit of claimed goal or Ralph completion and lawful correction of later action, at the supported runtime boundary
- Existing-work overlap: first-party worker self-report, Goal CAS/continuation and pluggable tests; experimental Auto Review is pre-tool permission only; community plugins and human verification are cheaper comparators
- Our on-top contribution: considered but not qualified first-party independent evaluator and completion-enforcement extension; no evidence of required product-native integration beyond existing plugin/check routes
- Incremental benefit: hypothetical rejection of false completion with lawful correction; not independently observed or measured against tests, human review, or an out-of-tree Cordis plugin
- Decision scope: only whether to add a first-party S3* completion certification constructor, not a project-wide, security, or canonical Index verdict
- Priority rationale: S1/S2/S3 already own operational closures; S3* has the clearest source-explicit deferral, but no demonstrated unmet outcome against simpler verification; S4/S5 need separate justified problems and legitimate ownership
- Target transition: NO_QUALIFIED_C_TARGET
- P1 dependencies: only on new reproduced false-completion evidence, compare cheapest deterministic check/parent review/out-of-tree plugin, and identify a lawful native pre-commit gate or authorised correction port
- P2 optional: NONE
- Proposed C construction: considered independent evidence reader and separate audit actor choosing certify/reject/hold, guarded goal completion application and durable next-round feedback; no source-backed material first-party requirement established
- C sufficiency falsifier: same verified completion/correction outcome attainable by task-specific tests, human verification or a separate plugin, or absence of a reachable independent pre-completion authority
- Scenario basis: HYPOTHETICAL
- Proposal-stage decision: NO_GO
- Research disposition: NO_USEFUL_CHANGE
- Proposed validation: false and true worker claims against independent artifact/test, compare existing checker/plugin route with opt-in evaluator; verify stale CAS, parent veto, missing reviewer and durable correction feedback
- Validation state: NOT_RUN
- Proposal falsifier: reproducible counterexample where native tests and an out-of-tree plugin cannot correct a false success but a smallest lawful first-party addition does so with observable benefit
- Result: NO_USEFUL_CHANGE
- External issue: DRAFT — NOT PUBLISHED
- Public fork Issue: DRAFT — NOT PUBLISHED
- Native tests: NOT_RUN
- Cost status: NOT_MEASURED

## Identity and pins

The accepted Index assessment [deepseek-harness](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md) is status included and matches current Index [catalog](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/data/catalog.psv) row 109 for the exact original and reviewed source ref. The [historical source commit](https://github.com/deepseek-ai/deepseek-harness/commit/ddefc45fbc7f8e46dd73185e68295696d1297887) resolves. The [current original master HEAD](https://github.com/deepseek-ai/deepseek-harness/commit/2e39e70496aa02986ca6a820c5d497e816b69d7e) is independently pinned and must not change the historical grade. The source is a rapidly changing developer preview; a new Index review is advisory and belongs to Index.

The first-party runtime boundary includes supported opt-in modes and genuine product behavior. Plugin authors, the model provider, user/parent policy, repository maintainers, test CI and developer-only code-review processes are not automatically local S3*/S5 owners. Review scope was all six functions, rather than treating an empty historical cell as a defect.

## Rights and authority

The original [MIT license](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/LICENSE) permits lawful fork-side research, preserving notices. The [current contributor policy](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) explicitly says external PRs are not being accepted and prefers Discussions and independent plugins. No original PR, issue, comment, or community discussion was published by this review; no public fork Issue or product patch was created. Fork was independently checked as a true child of deepseek-ai/deepseek-harness; ACTIVE/ALLOW on opensiro/meta permits only internal metadata work under Upstream #58, not any third-party public communication.

## Existing work / overlap

- **SHIPPED:** [agent loop](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/core/agent-loop/README.md) owns tool execution and Session results fed back into later model decisions.
- **SHIPPED / optional:** [Team operations](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/team/agent-team/README.md) and [model-facing Team tools](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/team/tool-agent-team/README.md) supply existing coordination and lead regulation; they do not prove post-outcome independent audit.
- **SHIPPED:** [Goal service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/README.md), [Goal tools](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/README.md), and [round driver](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal-round-driver/README.md) support durable objectives, bounded same-session continuation, and revision-checked updates. Their current first-party docs explicitly defer independent verification and place completion judgment with caller/model.
- **SHIPPED / experimental:** [Ralph](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/tool-ralph/README.md) uses worker self-declared terminal status; [Auto Review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md) checks a pending tool action before execution, not the truth of a claimed final goal.
- **NATIVE EXTENSION BASELINE:** [Cordis architecture](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/architecture.md) supports separately composed plugins, services and events; [Goal source implementation](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) exposes GoalService.complete() with revision checking but emits goal/changed only after appending the goal/change state mutation. [Model-facing update tool](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/tool-goal/src/index.ts) directly invokes complete() or block(). A passive post-event observer is therefore not an independently enforced pre-completion veto or a complete S3* constructor.
- **DEDUPE COVERAGE:** GitHub open-Issue list returned empty and focused evaluator search had no matching issue/PR result. Direct original open-PR list returned HTTP 404: exhaustive PR inventory is **UNKNOWN**, not zero. First-party sources expressly mark evaluator as deferred, not a committed backlog.

## Function ownership

- S1 disposition: existing autonomous model AgentLoop chooses tool-using work, and results return via Session history; no need to construct S1=C solely to change an established A
- S2 disposition: optional Team members share CAS task board, dependencies, message feedback and write-scope coordination; autonomous S2=A already owns interference regulation
- S3 disposition: Team Lead regulates live work, and supported parent task-board controls provide an additional A(P) mode; no independently demonstrated deficiency requiring S3=C
- S3* disposition: goal and Ralph completion remain self-declaration; Auto Review only gates pending tool effects, not independent post-outcome audit. Potential C is coherent but material on-top demand and enforceable native correction path are not yet demonstrated
- S4 disposition: configuration/plugins/tools can adapt a task, but no source-supported need for an independent future-environment decision and later viability feedback was established; non-target, intent UNKNOWN
- S5 disposition: deployment/user permission and ultimate-policy choices remain outside the claimed local runtime owner, with no justification to transfer reserved parent authority to an added agent; non-target

## Parallel contribution-on-top review

| Requirement / operator task | Track A — original shipped and simplest alternative | Track B — smallest on-top construction considered | Falsifier |
| --- | --- | --- | --- |
| Detect false completion | Worker reports complete; task tests, human review or opt-in separate Cordis verifier can inspect artifact evidence | Explicit independent evidence input and reviewer identity, no reliance on worker summary alone | A deterministic acceptance command already catches false claim reliably |
| Legitimately choose certify/reject/hold | Goal persists CAS revision and update path; caller decides complete/blocked today | Independent reviewer returns bounded judgment, but no proven need for a new first-party authority | Existing legal plugin/parent mechanism makes the same choice |
| Change later operation and observe result | Goal-round driver resumes authorized goals; goal/changed emitted after change, not an automatic veto | Introduce genuinely required pre-completion enforcement or protected return port *if shown necessary*, durable verdict and feedback to later round | Only monitoring or an unguarded post-event correction; parent pause, stale revision or absent reviewer |
| Distribution and cost | Existing profile patches and plugins plus external tests; repo declines external PRs currently | Optional first-party interface change would need maintainer acceptance and a measured advantage | Added component yields no new verified task outcome or raises maintenance without benefit |

The Track B C-constructor is deliberately **not** selected as P0: even a technically plausible reviewer is not yet demonstrated to require a first-party new source extension, and its full bounded rights/feedback loop has not been exercised. Original failure-case demand and relative cost are NOT_MEASURED, not claimed. Distinguish this narrow judgment from a blanket rejection of future evaluator experiments.

## Capability priority

**P0: NO_QUALIFIED_C_TARGET** for this observed task: no supported increment requires a new first-party C-construction at S1, S2, S3, S3*, S4 or S5. **P1: conditional evidence only** — reproduce wrong completion and prove insufficient cheaper tests/parent/plugin path, map the missing native protected enforcement point, then revisit a bounded S3* design. **P2: NONE**. The participant's actual application problem is unverified, and neither absent reviewer nor missing historical grade proves the need.

## Implementation options

Cheapest supported counterfactual: task-specific deterministic tests/human acceptance or a separately installed Cordis evaluator. A later justified first-party adapter could read original objective, structured claim and independent artifact/test evidence, select certify/reject/hold with bounded permissions, prevent or visibly qualify an uncertified success, and route a guarded correction into subsequent authorized work with a durable receipt. This is conceptual only. The current Goal service's direct complete() and post-commit event make generic event listening alone insufficient: stronger enforcement would require evidence for one smallest native API/ownership change rather than an invented independent S5 or a duplicate goal store.

## Specification and domain alternatives

No new Profile/Skills normative issue was established. The historical Index vector remains immutable. The repository's first-party plugin framework is the plausible lower-cost extension path; original contribution restrictions make an external PR specifically unavailable. Independent fork/plugin experiments need separate scope and validation, not an automatic Upstream implementation mandate.

## Cost experiment

Use one false-success and one true-success task with predeclared independent artifact checks. Compare native checks/human review/opt-in plugin against a proposed first-party verifier for false accept/reject, lawful completion vs hold, correction success after next round, setup effort, ongoing maintenance, model requests and wall clock cost. Include adversarial worker-supplied evidence, stale goal revisions, reviewer absence and parent pause. **Not executed. Cost NOT_MEASURED.**

## Delivery and publication

**Independent v0.18 source-first verdict: NO_GO; research NO_USEFUL_CHANGE; selected target NO_QUALIFIED_C_TARGET.** Confidence **moderate** for current narrow no-material-delta decision, lower for any untested future benefit. Reviewed source/docs/selected implementation and existing public search; native tests NOT_RUN, no corrected task demonstrated.

**Historical comparison happened only AFTER the independent decision:** existing fork-local [pre-rerun case at metadata parent commit](https://github.com/opensiro-contributions/deepseek-harness/blob/37cbf1f044059dfca9e61d0f7c2c8f0ef5222851/.opensiro/issues/independent-goal-verification-20261119/roadmap.md) also concluded NO_GO/NO_USEFUL_CHANGE about first-party S3*. The independent result **agrees**, now explicitly checking GoalService.complete() and post-commit notifications. Same pinned original HEAD; this is a fresh review procedure and evidence refinement, not a separate shipped feature or an Index reassessment. Historical git provenance remains accessible. Earlier PAUSE/DORMANT language was superseded by the [2026-11-19 owner ACTIVE/ALLOW action](https://github.com/opensiro/upstream/issues/58).

[Human internal issue draft](issue.md) and [technical AI contract](constructor-sufficiency.md) intentionally share this one receipt. Public fork GitHub Issue and external original interactions are **DRAFT / NOT PUBLISHED**, pending exact current-conversation approval where applicable. No original product files, fork default branch, feature branches or contributions were changed.
