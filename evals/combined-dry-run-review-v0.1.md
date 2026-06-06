# AI Music Prompt Skill Combined Dry-Run Review v0.1
# AI 音乐 Prompt Skill 合并 Dry-Run 评审 v0.1

## Purpose / 用途

This document combines the first ten evaluation prompts into one design-level dry-run review.
本文把前 10 个测试样例合并成一份设计层面的 dry-run 评审。

The goal is not to simulate every line of every answer.
目标不是逐字模拟每个完整回答。

The goal is to evaluate whether the current skill design behaves consistently across common cases, edge cases, branding cases, bilingual cases, and safety-sensitive cases.
目标是评估当前 skill 设计，在常见场景、边界场景、品牌场景、双语场景和安全敏感场景下，是否能稳定工作。

---

## Review Scope / 评审范围

This combined review covers all ten current eval cases:
这份合并评审覆盖当前全部 10 个测试样例：

1. new vocal song / 新建带人声歌曲
2. new instrumental BGM / 新建纯器乐 BGM
3. prompt optimization / Prompt 优化
4. lyrics optimization / 歌词优化
5. short-video hook / 短视频 Hook
6. brand theme song / 品牌主题歌
7. sports anthem / 体育 anthem
8. bilingual graduation song / 双语毕业歌曲
9. wedding song / 婚礼歌曲
10. artist-imitation refusal / 真实歌手模仿拒绝

---

## Executive Summary / 执行摘要

At the design level, the current skill looks strong enough to support a meaningful v1.
从设计层面看，当前 skill 已经足够支撑一个有实际价值的 v1。

Its strongest areas are:
它目前最强的几个方面是：

1. the split between vocal songs and instrumental BGM / 歌曲与纯器乐的清晰分流
2. the Chinese-lyrics / English-prompt language discipline / 中文歌词与英文 Prompt 模块的语言纪律
3. the ability to treat the skill as a consultant instead of a keyword expander / 把 skill 做成顾问而不是关键词扩写器
4. the mode system being broad enough for real usage / mode 体系已足够覆盖真实使用场景

Its biggest risks are not missing capability, but loss of discipline.
它最大的风险不是“缺能力”，而是“失去纪律”。

The most likely failure modes are:
最可能的失败方式是：

1. asking too many questions when the user already gave enough detail / 用户信息已足够时仍追问过多
2. optimizing prompts by rewording instead of diagnosing / 做 Prompt 优化时只改写，不做诊断
3. flattening specialized use cases into generic pop output / 把特殊场景扁平化成泛流行输出
4. failing to enforce refusal-and-redirect behavior on artist imitation requests / 没有稳定执行“拒绝 + 改写替代方向”

---

## Case Cluster Review / 分组评审

## A. Core Creation Cases / 核心创作类

Covered cases:
覆盖样例：
- Case 1 / 样例 1
- Case 2 / 样例 2
- Case 8 / 样例 8
- Case 9 / 样例 9

### What looks strong / 看起来较强的地方

The skill should perform well whenever the user clearly states:
当用户清楚给出以下信息时，skill 表现应该会比较强：

- song vs BGM / 歌曲还是 BGM
- emotional direction / 情绪方向
- major use case / 主要使用场景
- vocal preference or no-vocal constraint / 人声偏好或无人声约束

This is because the current controller rules already:
因为当前控制层已经做对了几件事：

- short-circuit unnecessary interviews / 能跳过不必要访谈
- build a concise brief / 能构建精简 brief
- enforce output structure / 能约束输出结构
- maintain language separation / 能保持语言分离

### What can still go wrong / 仍可能出错的地方

1. The skill may still default to generic genre labels when the user’s scene implies a more specialized format.
   用户场景已经很特殊时，skill 仍可能退回泛化曲风标签。
2. The skill may treat “wedding”, “graduation”, or “brand” as mood-only cases rather than structure-shaping cases.
   可能把“婚礼 / 毕业 / 品牌”只当情绪标签，而不是结构与 Hook 设计的决定因素。
3. In bilingual requests, the skill may keep prompt modules in English correctly, but still produce weak bilingual lyric transitions.
   在双语请求里，虽然 Prompt 模块可能保持英文，但双语歌词切换未必自然。

### Design implication / 设计启示

The next refinement priority is not adding more fields.
下一步重点不是继续加字段。

It is making sure use case meaningfully changes output structure.
而是确保“使用场景”真的会改变输出结构。

---

## B. Optimization Cases / 优化类

Covered cases:
覆盖样例：
- Case 3 / 样例 3
- Case 4 / 样例 4

### What looks strong / 看起来较强的地方

The skill now has explicit rules that improve these cases a lot:
当前这两类之所以看起来更稳，是因为规则里已经明确补了：

- prompt optimization must diagnose weakness first / Prompt 优化要先诊断
- lyric optimization must request the lyric draft if missing / 歌词优化缺原文时必须索要原文

These two changes greatly reduce “fake helpfulness.”
这两条极大减少了“看起来有帮助、实际上没做事”的风险。

### What can still go wrong / 仍可能出错的地方

1. Prompt optimization may still overproduce and become too ornate.
   Prompt 优化可能仍会补偿过度，写得过于花哨。
2. Lyrics optimization may focus too much on wording polish and not enough on singability.
   歌词优化可能过于关注措辞润色，而忽略可唱性。
3. The skill may not clearly distinguish between “improve the prompt for generation” and “improve the underlying musical direction.”
   skill 可能没有清楚区分“优化提示词本身”和“优化背后音乐方向”。

### Design implication / 设计启示

Optimization quality is where the “consultant” identity is truly tested.
优化类正是最能测试“顾问感”的地方。

If these outputs feel smart, the skill will feel valuable.
如果这两类输出显得聪明，这个 skill 就会显得有价值。

---

## C. Short-Form and Spreadability Cases / 短形式与传播场景类

Covered cases:
覆盖样例：
- Case 5 / 样例 5
- Case 6 / 样例 6
- Case 7 / 样例 7
- Case 9 / 样例 9

### What looks strong / 看起来较强的地方

The skill already captures several useful distinctions:
当前 skill 已经抓住了几个关键区分：

- short-video hook vs full song / 短视频 Hook 与完整歌曲的区别
- brand theme song vs generic ad music / 品牌主题歌与普通广告音乐的区别
- sports anthem vs ordinary energetic pop / 体育 anthem 与普通热血流行的区别
- wedding intimacy vs broad social shareability / 婚礼亲密感与社交传播感之间的平衡

### What can still go wrong / 仍可能出错的地方

1. The skill may overuse “catchy” without specifying where the memorability comes from.
   可能会反复说 catchy，但没有具体说明记忆点来自哪里。
2. Brand-song requests may accidentally become generic youthful pop with a logo mention.
   品牌歌请求可能会退化成“年轻流行歌 + 品牌名提及”。
3. Sports anthem outputs may become loud but not communal.
   体育 anthem 可能会变得很吵，但没有群体共唱感。
4. Wedding-song outputs may become too cliché if “don’t be cheesy” is not interpreted strongly enough.
   如果对“不要太俗”理解不够强，婚礼歌可能还是会很俗套。

### Design implication / 设计启示

These cases need the skill to think in terms of audience behavior, not just music adjectives.
这类场景要求 skill 站在“听众/使用者行为”角度思考，而不是只堆音乐形容词。

---

## D. Safety-Sensitive Cases / 安全敏感类

Covered case:
覆盖样例：
- Case 10 / 样例 10

### What looks strong / 看起来较强的地方

The skill now has a clear rule:
当前 skill 已经有比较明确的规则：

- refuse direct artist imitation
- redirect into abstract style language

This is the correct high-level behavior.
这是高层策略上正确的方向。

### What can still go wrong / 仍可能出错的地方

1. The refusal may be too cold and lose the user’s underlying intent.
   拒绝可能太硬，导致用户真实意图被丢掉。
2. The redirect may become too generic and no longer feel helpful.
   替代方案可能太泛，导致虽然合规，但不够有帮助。
3. The skill may fail to preserve the specific emotional and era cues hidden inside the imitation request.
   skill 可能没有保留模仿请求背后真正想要的年代感、情绪感和旋律气质。

### Design implication / 设计启示

The best refusal is not only compliant.
最好的拒绝不只是合规。

It also preserves as much of the user’s legitimate intent as possible.
它还应尽可能保留用户合法、合理的真实创作意图。

---

## Cross-Case Rule Stability / 跨样例规则稳定性

### 1. Mode routing stability / mode 路由稳定性

Overall, the mode system looks stable enough.
整体看，mode 系统已经比较稳定。

The biggest remaining ambiguity is between:
当前最大边界仍然在：

- `generate_short_video_hook`
- `generate_multi_versions`

But the current rule — keep `generate_short_video_hook` primary when short-hook intent is explicit — is a good solution.
但目前“短 Hook 意图明确时，以 `generate_short_video_hook` 为主 mode”的规则是一个比较好的解决方案。

### 2. Questioning discipline / 提问纪律

This remains one of the most important quality signals.
这仍然是最重要的质量信号之一。

If the skill asks too much, users will feel slowed down.
问太多，用户会觉得被拖慢。

If it asks too little in the wrong place, outputs will become fake-precise.
问太少又会导致输出“看似具体，其实假精确”。

Current design is good, but real runs should keep watching this closely.
当前设计已经不错，但真实运行时要持续盯这个点。

### 3. Language split stability / 语言分离稳定性

The language split rule is one of the strongest parts of the current design.
语言分离规则是当前设计最强的部分之一。

It is clear, testable, and meaningful.
它清晰、可测，而且有实际价值。

The main future risk is not confusion about the rule.
未来主要风险不是规则本身混乱。

The risk is weak execution inside bilingual lyric writing.
而是在双语歌词写作里执行不够自然。

### 4. Output-structure stability / 输出结构稳定性

The output blocks are well-defined.
当前输出模块划分已经比较清楚。

The remaining challenge is making sure specialized cases really feel specialized.
剩下的挑战，是确保特殊场景输出出来时真的“有区别”。

---

## What the Skill Is Already Good Enough to Do / 当前已经足够做好的事

The current skill design appears ready for:
从现在的设计看，这个 skill 已经足以较稳地支持：

- mainstream song prompt generation / 主流歌曲 Prompt 生成
- mainstream BGM prompt generation / 主流 BGM Prompt 生成
- first-pass prompt optimization / 第一轮 Prompt 优化
- first-pass lyric optimization / 第一轮歌词优化
- platform-friendly short-hook ideation / 平台友好型短 Hook 设计
- basic branded music consultation / 基础品牌音乐顾问式生成
- safe redirect on artist imitation requests / 对真实歌手模仿请求的安全改写

---

## What Still Needs the Most Real-World Validation / 最需要真实验证的地方

1. bilingual lyric naturalness / 双语歌词是否自然
2. wedding-song taste control / 婚礼歌的审美控制
3. sports-anthem crowd scale / 体育 anthem 的群体规模感
4. brand-song memorability without sounding cheesy / 品牌歌的记忆点是否不俗套
5. refusal quality on imitation prompts / 模仿类请求的拒绝质量

---

## Recommended Priority Order / 建议优先级顺序

If only one next step is chosen, do this first:
如果下一步只做一件事，优先推荐：

### Priority 1 / 优先级 1
Run one manual dry response for each of the ten cases.
对这 10 个样例各手工跑一轮完整响应。

That will reveal whether the output actually feels as structured and useful as the design suggests.
这将直接暴露：当前设计在实际回答里，是否真的如预期一样清晰和有用。

### Priority 2 / 优先级 2
Write the README after the manual dry responses.
手工 dry response 之后，再写 README。

The README will be better if it reflects observed behavior instead of only intended behavior.
因为那样 README 反映的是“已验证行为”，而不只是“设计意图”。

### Priority 3 / 优先级 3
Expand safety-focused tests only after the first ten feel stable.
只有在前 10 个样例整体稳定后，再继续扩展更细的安全测试。

---

## Final Verdict / 最终判断

The current skill design is coherent, focused, and promising.
当前 skill 设计整体是连贯的、聚焦的，也很有潜力。

It is not yet proven by runtime behavior, but it is already much more than a loose document set.
它还没有被真实运行完全证明，但已经远不只是一些松散文档的堆积。

It now behaves like a real system design for an AI music creation consultant skill.
它现在已经像一个真正的“AI 音乐创作顾问 skill 系统设计”。

The next meaningful leap is not more abstract design.
下一步最有价值的跃迁，不再是继续抽象设计。

It is seeing full answers on the ten cases.
而是看它在这 10 个样例上的完整回答表现。
