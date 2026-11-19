# DeepSeek Harness — S3* independent goal verification capability roadmap

- Original repository: deepseek-ai/deepseek-harness
- Original HEAD: 2e39e70496aa02986ca6a820c5d497e816b69d7e
- Observed at: 2026-11-19
- Accepted Index assessment: https://github.com/opensiro/vsm-harness-index/blob/34e11ec4dd52e1ba3ee0111d8bca73f13918f54f/assessments/de/deepseek-harness.md
- Accepted assessment blob SHA: 257a55619d474d8a86a49de6dffa93a4426d7b62
- Accepted review ref: ddefc45fbc7f8e46dd73185e68295696d1297887
- Accepted reviewed at: 2026-09-18
- System in focus: DeepSeek Harness first-party Agent/Session with opt-in Goal/Ralph/Team at one harness recursion
- Profile version: 0.2.2
- Assessment methodology version: 0.3.1
- Accepted Index commit: 34e11ec4dd52e1ba3ee0111d8bca73f13918f54f
- Historical vector: S1=A, S2=A, S3=A(P), S3*=—, S4=—, S5=—
- Assessment age: 62 days (advisory re-assessment recommended; historical Index review is not rewritten)
- Matching fork: https://github.com/opensiro-contributions/deepseek-harness
- Fork pinned master HEAD: fcc0ad462172522aaf5c93a7b2e01f6b9f0b0159
- Fork meta branch: opensiro/meta (initial PAUSE/DORMANT bootstrap only)
- Disposition: NO_USEFUL_CHANGE
- Result: NO_USEFUL_CHANGE
- Final operator decision: NO_GO
- External issue: DRAFT — NOT PUBLISHED
- Public fork Issue: DRAFT — NOT PUBLISHED (requires separate exact current-conversation approval)
- Cost status: NOT_MEASURED

## Identity and pins

Pinned [original HEAD](https://github.com/deepseek-ai/deepseek-harness/commit/2e39e70496aa02986ca6a820c5d497e816b69d7e) differs from historical Index review ref [`ddefc45fbc7f8e46dd73185e68295696d1297887`](https://github.com/deepseek-ai/deepseek-harness/commit/ddefc45fbc7f8e46dd73185e68295696d1297887). Verified Index assessment `257a55619d474d8a86a49de6dffa93a4426d7b62` at Index `34e11ec4dd52e1ba3ee0111d8bca73f13918f54f`, accepted status included, catalog identity deepseek-harness and review_ref match; Profile 0.2.2 / Methodology 0.3.1. Current fork master `fcc0ad462172522aaf5c93a7b2e01f6b9f0b0159` is behind current original; the proposed case is **source analysis**, not a fork product implementation. Original HEAD observed 2026-11-19. Reassessment of the 62-day-old accepted review is advisory and separate from the roadmap.

## Rights and authority

Original [MIT](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/LICENSE) grants general licensed uses subject to notice terms; [CONTRIBUTING](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) currently does not accept external PRs, requesting Discussions/plugins instead. Original PR publication therefore disallowed by current contributor preference, even though MIT is permissive. Verified existing working fork `opensiro-contributions/deepseek-harness` with parent `deepseek-ai/deepseek-harness`, master `fcc0ad462172522aaf5c93a7b2e01f6b9f0b0159`, write permission present; `opensiro/meta` absent before initial authorized bootstrap. Owner control initialization PAUSE / DORMANT: no product branch edits, no later engineering without attributable RESUME/ALLOW. No external original interaction or public fork Issue approved.

## Existing work / overlap

Shipped [Ralph](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/tool-ralph/README.md): self-reported complete/blocked, no independent evaluator. Shipped [Goal service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/README.md) and [round driver](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal-round-driver/README.md): caller/model declares completion, evaluator deferred. Shipped [Auto review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md) reviews actions before execution; it is not a post-result complementary audit. [Plugin architecture](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/architecture.md) already provides extension hooks. The repo documents evaluator as a deferred option, explicitly not automatic task backlog.

Open original issue listing was empty and targeted evaluator issue/PR searches found no result. The original direct `pulls?state=open` REST call returned HTTP 404, so exhaustive PR coverage is **UNKNOWN**. No external issue was invented and no implementation requirement is inferred from issue titles or an omitted grade.

## Function ownership

Historical S1=A model Agent-loop; S2=A Team coordination; S3=A(P) Team Lead and parent task control. These already-established A/A(P) functions do not need a C target. Historical S3*=—: neither worker self-report nor per-tool permission review establishes an independent audit-to-correction feedback loop. Historical S4=— and S5=— excluded from current scoped hypothesis; an add-on evaluator cannot silently claim future adaptation or ultimate-policy governance. Present constructor sufficiency **NOT ESTABLISHED**; the current original can differ from the accepted historical grade.

## Capability priority

**P0 candidate rejected now (NO_GO):** independent review of false goal/Ralph completion with actionable feedback. The required cycle is worker claim + independent real-world evidence → separate legitimate reviewer selects certify/reject/hold → governed return to Goal/next iteration → later observable correction. Not established in shipped first-party or demanded by a reproduced user task.

**P1 not scheduled:** investigate only if a reproduced failure shows external test/human review or an out-of-tree plugin cannot produce a sufficiently useful outcome; then determine exact missing first-party authority, durable receipt, reviewer interface and feedback application. **P2 no supported extras.** Positive and negative future tests are specified in [AI contract](https://github.com/opensiro-contributions/deepseek-harness/blob/opensiro/meta/.opensiro/issues/independent-goal-verification-20261119/constructor-sufficiency.md), but none have run.

## Implementation options

First/cheapest: use clear task-specific deterministic tests, human approval or a scoped Cordis plugin around existing Goal/Ralph/Session hooks, without changing original source. Only if a measured material delta appears: consider an opt-in evaluator extension with separate actor, authority-restricted return and durable verification receipt. A mock, mere hook registration or self-reported completion is not an S3* C witness. Current recommendation: **do not implement** or open a PR.

## Specification and domain alternatives

No contradiction requiring Profile/Skills normative modification was observed: the historical Index S3* exclusion remains an honest assessment at its own review_ref. An independent domain-scoped experimental plugin/fork is legally possible under MIT, but a separate task, rights/owner check and direct evidence are required. Not authorized or scheduled here. An external maintainer issue is not justified until there is native benefit evidence; their contributor instructions presently prefer Discussions and out-of-tree plugins.

## Cost experiment

Predeclare the same goal-completion task with intentionally false and true worker claims. Compare native task-specific checks/plugin path versus a proposed evaluator-backed first-party extension; measure verified task correctness, false-accept/reject rate, total setup/implementation/review/test effort, upkeep and runtime/model cost. No experiment has been executed: **NOT_MEASURED**; no claimed VSM savings.

## Delivery and publication

**PLAN_ONLY / NO_USEFUL_CHANGE; final operator decision NO_GO.** Persist a Human [issue.md](https://github.com/opensiro-contributions/deepseek-harness/blob/opensiro/meta/.opensiro/issues/independent-goal-verification-20261119/issue.md), AI [constructor-sufficiency.md](https://github.com/opensiro-contributions/deepseek-harness/blob/opensiro/meta/.opensiro/issues/independent-goal-verification-20261119/constructor-sufficiency.md), this receipt and a case README on independent metadata branch. Public working-fork Issue title: **DeepSeek Harness — independent goal-completion audit (S3*) roadmap (OpenSiro, plan-only)**, with complete body in issue.md, **DRAFT — NOT PUBLISHED** until exact current-conversation approval. Original Issue, PR, comment and fork review PR: **NOT PUBLISHED**. No code/tests, Index reassessment, owner RESUME, new contribution ID or derived savings. Next decision: stop this proposed first-party change; reopen only on reproduced material failure and inadequate cheaper alternative.
