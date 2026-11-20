# DeepSeek Harness — S3* completion verification case (Upstream #58)

- Case ID: independent-goal-verification-20261119
- Original: https://github.com/deepseek-ai/deepseek-harness
- Original source fixed: 2e39e70496aa02986ca6a820c5d497e816b69d7e (master, checked 2026-11-19)
- Accepted Index: https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/de/deepseek-harness.md; historical vector S1=A · S2=A · S3=A(P) · S3*=— · S4=— · S5=—
- Matching fork: https://github.com/opensiro-contributions/deepseek-harness
- Metadata ref only: opensiro/meta; verified owner state ACTIVE/ALLOW, event 20261119T182226Z--owner-upstream58-active
- **Current bounded proposal: GO / NEEDS_EVIDENCE** for `S3*=— -> S3*=C` via an **optional, original-native, pre-commit completion-guard extension seam** plus separately composed evidence-review plugin. No newly shipped C or updated Index vector is claimed.
- Original independent v0.18 source-first assessment: [previous reconciled decision](https://github.com/opensiro-contributions/deepseek-harness/blob/39bc69e4149528ab89deb60a6ed03f81739b0178/.opensiro/issues/independent-goal-verification-20261119/roadmap.md) was NO_GO / NO_USEFUL_CHANGE; a dated **follow-up evidence correction** changed this scoped proposal after new original Discussion and external prototype evidence. This is **not a second independent fresh-context audit**.
- Native original tests: NOT_RUN; compatibility at current original pinned HEAD: NOT_RUN; user outcomes/cost: NOT_MEASURED
- Original-facing or public fork issue/comment/PR: NOT PUBLISHED. Draft only.

## Canonical case artifacts

- [Human issue draft](issue.md)
- [AI constructor sufficiency](constructor-sufficiency.md)
- [Canonical roadmap receipt](roadmap.md)

## Why the decision changed

A user [reports premature model-owned goal completion and repeated restart of the same work](https://github.com/deepseek-ai/deepseek-harness/discussions/10471); the exact third-party https://github.com/bpc-oss/dsh-verification provides a non-core verification engine whose [vendored GoalService patch](https://github.com/bpc-oss/dsh-verification/blob/main/scripts/patch-vendored-goal.cjs) demonstrates that an **unmodified upstream GoalService lacks the required guarded transition seam**. The community plugin's stated [seam tests](https://github.com/bpc-oss/dsh-verification/blob/main/packages/dsh-verification/test/seam-e2e.test.ts) are source evidence, **not tests run by OpenSiro**.

The minimal delta is **not a new baked-in verifier or a new S5 policy authority**. A supported optional pre-commit veto/permit attribution port can allow authorised, separately configured reviewers to form an S3* feedback loop. A plugin version with local vendoring is the concrete Track A comparator; native portability, safety and incremental value are still untested. Hence GO is a **research proposal**, not implementation permission or upstream maintainer acceptance.

The [original contributor policy](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/CONTRIBUTING.md) currently does not accept external PRs and routes feedback to Discussions and plugins; all third-party public contact needs a separate exact approval.

### 2026-11-20 · v0.18.1 same-case source-native PATCH_REVIEW

Preserves the 2026-11-19 independent case and `GO / NEEDS_EVIDENCE` proposal outcome while narrowing the optional S3* hypothesis to the actual synchronous [GoalService.complete](https://github.com/deepseek-ai/deepseek-harness/blob/2e39e70496aa02986ca6a820c5d497e816b69d7e/packages/goal/goal/src/index.ts) → durable `goal/change` seam, with direct-service/tool bypass and replay/parent tests. [Human](issue.md) · [AI](constructor-sufficiency.md) · [canonical receipt](roadmap.md). Original remains `master@2e39e70496aa02986ca6a820c5d497e816b69d7e`. Implementation/test/cost NOT_RUN/NOT_MEASURED; no third-party or public fork publication; no new Upstream status-only PR.

**Canonical case links:** [issue.md](issue.md) · [constructor-sufficiency.md](constructor-sufficiency.md) · [roadmap.md](roadmap.md).
