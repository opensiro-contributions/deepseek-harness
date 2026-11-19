# DeepSeek Harness — independent goal-completion audit (S3*) roadmap (OpenSiro, plan-only)

**OpenSiro research · PLAN_ONLY / NO_USEFUL_CHANGE · DRAFT — NOT PUBLISHED**

**Final operator decision: NO_GO.** Do not implement or propose a first-party independent-completion evaluator now. This issue is a research handoff and discussion draft for the OpenSiro working fork, not a request to DeepSeek maintainers.

**Working fork:** https://github.com/opensiro-contributions/deepseek-harness
**AI/developer construction sufficiency and acceptance:** [constructor-sufficiency.md](https://github.com/opensiro-contributions/deepseek-harness/blob/opensiro/meta/.opensiro/issues/independent-goal-verification-20261119/constructor-sufficiency.md)
**Source-pinned technical receipt:** [roadmap.md](https://github.com/opensiro-contributions/deepseek-harness/blob/opensiro/meta/.opensiro/issues/independent-goal-verification-20261119/roadmap.md)

## Why OpenSiro / accepted baseline

OpenSiro examines whether reusable Viable System Model (VSM)-informed organizational specifications can improve agent-harness integration and maintenance versus the simplest product-native solutions. **No savings, adoption or quality benefit has been measured.**

**Accepted historical Index at reviewed source revision:** S1 **A** · S2 **A** · S3 **A(P)** · S3* **—** · S4 **—** · S5 **—**. [Accepted assessment](https://github.com/opensiro/vsm-harness-index/blob/34e11ec4dd52e1ba3ee0111d8bca73f13918f54f/assessments/de/deepseek-harness.md) (assessment blob `257a55619d474d8a86a49de6dffa93a4426d7b62`; Index `34e11ec4dd52e1ba3ee0111d8bca73f13918f54f`; reviewed **2026-09-18**; review ref `ddefc45fbc7f8e46dd73185e68295696d1297887`; Profile **0.2.2**, Methodology **0.3.1**). The vector describes the *historical* first-party boundary, not the latest code and not a feature backlog. Ownership states A/C/P are not maturity ranks.

System in focus: the original's supported and optional first-party agent, goal and experimental Ralph execution modes, one harness organization. External evaluator plugins, maintainers and provider models are not automatically S3* actors. Current original HEAD: [`2e39e70496aa02986ca6a820c5d497e816b69d7e`](https://github.com/deepseek-ai/deepseek-harness/commit/2e39e70496aa02986ca6a820c5d497e816b69d7e), observed **2026-11-19**. The 62-day-old assessment merits Index-owned freshness review before any new grade; this is **advisory**, not a roadmap block.

| Function | Historical Index | Decision |
| --- | --- | --- |
| S1 operations | A | Existing agent ownership; no constructor required |
| S2 coordination | A | Existing team coordination; no constructor required |
| S3 current management | A(P) | Current lead/parent control; no mandatory C conversion |
| S3* independent audit | — | Evaluate a possible independent completion verifier, but **NO_GO** for implementation today |
| S4 future adaptation | — | No supported new user outcome; excluded |
| S5 identity / ultimate policy | — | Do not invent new authority or override parent decisions |

## Native behavior and residual user need

The current [Ralph package](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/tool-ralph/README.md) explicitly labels terminal completion and blocker reports as **worker self-declarations**. The [goal service](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/README.md) and [goal-round driver](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal-round-driver/README.md) explicitly defer independent evaluator-backed certification. By contrast, [Auto review](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/experimental/auto-review/README.md) is a **pre-tool permission gate**, not an independent audit of a completed outcome.

The [plugin architecture](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/docs/architecture.md) already supports composition through Cordis services and lifecycle hooks. A deployment could first test a non-core plugin or deterministic external verification without adding another first-party subsystem. Existing documentation calls evaluator support a **deferred direction, not a committed task backlog**. GitHub issue searches returned no matching evaluator request or competing PR. Direct original pull-list retrieval returned HTTP 404, so the *complete PR inventory is unverified*, not proven empty.

## Priority and why NO_GO

**P0 (rejected for now):** a developer-composable, independently owned goal-completion audit that could reject a false success and feed a lawful correction into a subsequent run. This would require a different evidence channel from the worker's self-report, clear reviewer identity and authority, durable outcome and later-operation application. The first-party construction and extra user benefit are **not yet established**.

**P1 (not scheduled):** only if a falsifiable task demonstrates a meaningful gap in the simplest plugin/deterministic-check alternative, investigate a first-party verification result and authorized correction port. **P2: none justified**. Do not introduce S4, S5 or a new control plane to fill missing grades.

**Positive acceptance for a future hypothesis:** intentionally false worker completion is independently rejected using observable artifact/test evidence, and a legitimately authorized continuation or correction happens and is recorded. **Negative acceptance:** absent reviewer, stale evidence, reviewer collusion, unauthorized goal change and unavailable checks fail closed or remain explicitly uncertified. **Compatibility:** ordinary goal and Ralph runs still work with auditing absent. These are *proposed tests only*, not run tests or shipping guarantees.

The simplest present alternative is to configure explicit task tests/human review or experiment with an out-of-tree Cordis evaluator plugin. No matched task comparing the alternatives, verified operator demand or material cost/correctness delta is available. **Cost status: NOT_MEASURED.**

## Rights and next decision

Original [MIT license](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/LICENSE). The original [contribution policy](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) explicitly says **external PRs are not accepted for now**, and points contributors to Discussions and separate plugins. No original Issue, PR, comment or Discussion has been posted. The correct OpenSiro fork is `opensiro-contributions/deepseek-harness`; case files are restricted to `opensiro/meta` with **PAUSE/DORMANT** owner control and no product edits.

**NO_GO now:** do not implement a speculative first-party S3* constructor, treat worker reports as certified, open an external PR, or change the Index grade. A later **new source-backed operator task** with a reproduced false-success example and a demonstrably insufficient simpler native/plugin solution would justify a *new* decision. Any public fork Issue publication requires exact current-conversation approval of this title/body; this text is **DRAFT — NOT PUBLISHED**.

_AI-assisted analysis; no independent human validation, native test execution or measured engineering savings claimed._
