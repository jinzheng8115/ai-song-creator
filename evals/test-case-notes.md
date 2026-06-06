# AI Music Prompt Skill Test Cases v0.1
# AI 音乐 Prompt Skill 测试样例 v0.1

## Purpose / 用途

This file explains the first batch of realistic test prompts for the interactive AI music prompt skill.
本文用于说明交互式 AI 音乐 Prompt Skill 的第一批真实测试样例。

The goal is not to test every edge case yet.
当前目标不是一次覆盖所有边界情况。

The goal is to verify whether the first version of `SKILL.md` feels natural, routes correctly, and produces outputs that are actually useful.
当前目标是验证第一版 `SKILL.md` 是否交互自然、路由正确，并且能产出真正有用的结果。

---

## Coverage Strategy / 覆盖策略

This first batch covers five high-value scenarios:
第一批覆盖五个高价值场景：

1. new vocal song creation / 新建带人声歌曲
2. new instrumental BGM creation / 新建纯器乐 BGM
3. prompt optimization / Prompt 优化
4. lyrics optimization / 歌词优化
5. short-video hook generation / 短视频 Hook 生成

This set is intentionally small.
这组样例故意保持较小。

It is meant to test the main controller behavior before expanding into niche scenarios.
它的目的，是先验证主控制逻辑，再扩展到更细分的场景。

---

## Test Case 1 / 测试样例 1

**Prompt:**

```text
我想做一首中文流行抒情歌，主题是 30 岁以后还在努力生活，适合发朋友圈，温暖但有点伤感，男声，输出完整 Prompt 包。
```

**What it tests / 测什么：**
- vocal-song routing / 歌曲路由
- low-question behavior when input is already rich / 输入较完整时的少追问能力
- Chinese lyrics + English prompt-module split / 中文歌词与英文 Prompt 模块分离
- emotional translation from “warm but sad” into actionable music direction / 将“温暖但有点伤感”转成可执行音乐方向

---

## Test Case 2 / 测试样例 2

**Prompt:**

```text
帮我做一段科技产品宣传片背景音乐，不要人声，要高级、未来感、干净一点，适合旁白。
```

**What it tests / 测什么：**
- instrumental routing / 纯器乐路由
- instrumental-only constraint / 无人声约束
- voiceover-friendly arrangement thinking / 为旁白留空间的编曲思路
- tech + premium + clean mood blending / 科技感、高级感、干净感的混合转译

---

## Test Case 3 / 测试样例 3

**Prompt:**

```text
这是我现在的 Suno prompt: sad pop song, male vocal, piano, emotional. 帮我优化得更电影感、更高级一点，适合短视频。
```

**What it tests / 测什么：**
- optimize-existing-prompt routing / Prompt 优化路由
- ability to diagnose weak prompt specificity / 识别原 Prompt 太泛的问题
- conversion from vague adjectives to more concrete arrangement and scene fit / 从模糊形容词转成更具体的编曲与场景适配

---

## Test Case 4 / 测试样例 4

**Prompt:**

```text
我有一段中文歌词，但是副歌不够抓耳，也不太像能唱出来的歌，帮我优化一下，风格偏民谣流行。
```

**What it tests / 测什么：**
- optimize-existing-lyrics routing / 歌词优化路由
- preservation of lyric language defaults / 歌词语言默认规则
- hook strengthening and singability improvement / Hook 强化与可唱性提升
- style-direction suggestion alongside lyric revision / 优化歌词同时给出风格方向建议

---

## Test Case 5 / 测试样例 5

**Prompt:**

```text
我想做一个适合小红书短视频的 30 秒音乐 Hook，最好前几秒就有记忆点，给我 3 个不同方向。
```

**What it tests / 测什么：**
- short-video hook handling / 短视频 Hook 路由能力
- separation between multi-version and hook-oriented output / 多版本输出与 Hook 输出的边界处理
- first-impression impact design / 前几秒抓力设计
- short-form, platform-fit thinking / 短形式与平台适配思路

---

## Review Criteria / 评审标准

When reviewing outputs from these tests, focus on:
在 review 这些测试结果时，重点看：

1. Did the skill choose the right mode? / 路由是否正确？
2. Did it ask too many questions? / 是否问得太多？
3. Did it preserve the Chinese-lyrics / English-prompt split correctly? / 是否正确执行“中文歌词 / 英文 Prompt”分离？
4. Did the output feel like a real music consultant rather than a keyword rewriter? / 输出是否像真正的音乐顾问，而不是关键词改写器？
5. Were the iteration prompts actually reusable? / 迭代 Prompt 是否真的能复用？

---

## Next Expansion Ideas / 下一轮扩展方向

After these five pass basic review, the next batch can cover:
这五个样例通过基础 review 后，下一批可以扩展到：

- brand theme song / 品牌主题歌
- sports anthem / 体育 anthem
- bilingual lyrics / 双语歌词
- wedding song / 婚礼歌曲
- graduation song / 毕业歌曲
- commercial copyright-risk prompts / 商业版权高风险提示词
- artist-imitation rejection cases / 真实歌手模仿拒绝场景
