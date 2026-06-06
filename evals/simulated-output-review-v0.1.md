# AI Music Prompt Skill Simulated Output Review v0.1
# AI 音乐 Prompt Skill 模拟输出评审 v0.1

## Purpose / 用途

This document simulates how the current `SKILL.md` should behave on the first five evaluation prompts.
本文用于模拟当前 `SKILL.md` 在前五个测试样例上的预期行为。

This is not a real runtime execution log.
这不是实际运行日志。

It is a design-level review that checks whether the skill routing, questioning behavior, output structure, and language split feel correct.
它是一份设计层面的 review，用来检查 skill 的路由、提问策略、输出结构和语言分离是否合理。

---

## Review Method / 评审方法

For each test case, review four things:
每个测试样例重点看四件事：

1. Expected mode / 预期 mode
2. Expected questioning behavior / 预期提问行为
3. Expected output shape / 预期输出结构
4. Likely risks or refinement needs / 可能风险与可优化点

---

## Test Case 1 / 测试样例 1

**Input / 输入**

```text
我想做一首中文流行抒情歌，主题是 30 岁以后还在努力生活，适合发朋友圈，温暖但有点伤感，男声，输出完整 Prompt 包。
```

### Expected mode / 预期 mode

`create_vocal_song`

Reason / 原因：
- 明确是歌曲
- 明确有男声
- 明确要完整 Prompt 包
- 主题、场景、情绪、风格都已经给得比较全

### Expected questioning behavior / 预期提问行为

The skill should probably ask **zero** follow-up questions, or at most **one** clarifying question about whether the user already has lyric ideas.
这个样例理论上应该 **不追问**，最多只补问 **一句** 是否已有歌词想法。

Why / 原因：
- `track_type` 已明确
- `theme` 已明确
- `use_case` 已明确
- `genre direction` 已明确
- `mood` 已明确
- `vocal preference` 已明确
- `output_format` 已明确

If the skill asks a full 3-question interview here, that is a failure.
如果这里还走完整 3 问访谈，说明 skill 过度提问。

### Expected output shape / 预期输出结构

Should produce:
应输出：

- 中文 Requirement Summary
- 中文 Music Direction
- 中文 Title Options
- English Style Prompt
- Lyrics Box with English control tags + Chinese lyrics
- English Iteration Prompts
- 中文 Usage Notes

### Expected musical direction / 预期音乐方向

Likely brief:
可能的 brief：

- genre: Chinese pop ballad
- mood: warm, bittersweet, hopeful
- vocal: mature emotional male vocal
- tempo: medium-slow, around 80–90 BPM
- arrangement: piano, acoustic guitar, warm bass, light drums, soft strings
- energy curve: quiet reflection → hopeful release

### Risks / 风险点

1. The skill may default to generic “emotional male vocal” and miss the stronger “mature life-story” angle.
   可能会只写成泛化的 emotional male vocal，没抓住“30 岁以后仍在努力生活”的成熟叙事感。
2. The chorus may become too sad and lose the “still trying / still hopeful” arc.
   副歌可能过度伤感，丢掉“仍在努力、仍有希望”的弧线。

### Verdict / 判断

This should be an **easy pass** case for the current design.
这个案例对当前设计来说应该属于 **容易通过** 的样例。

---

## Test Case 2 / 测试样例 2

**Input / 输入**

```text
帮我做一段科技产品宣传片背景音乐，不要人声，要高级、未来感、干净一点，适合旁白。
```

### Expected mode / 预期 mode

`create_instrumental_bgm`

Reason / 原因：
- 明确是背景音乐
- 明确不要人声
- 明确是科技产品宣传片
- 明确旁白友好

### Expected questioning behavior / 预期提问行为

The skill should ask **zero** or **one** follow-up question.
理论上应该 **不追问**，或最多 **追问一句**：是否需要循环结尾。

It should not ask about vocal preference, lyric language, or chorus.
不应再问人声偏好、歌词语言或副歌问题。

### Expected output shape / 预期输出结构

Should produce:
应输出：

- 中文 Requirement Summary
- 中文 Music Direction
- English Style Prompt
- English Instrumental Structure Box
- English Iteration Prompts
- 中文 Usage Notes

### Expected musical direction / 预期音乐方向

Likely brief:
可能的 brief：

- genre: minimal electronic / premium corporate electronic
- mood: premium, futuristic, clean, optimistic
- instrumentation: pulsing synths, minimal drums, soft sub bass, digital pads
- arrangement: leave room for voiceover, non-distracting motif, clean midrange
- tempo: medium, around 95–115 BPM

### Risks / 风险点

1. The skill may make it too “EDM” instead of “brand-film premium”.
   有可能误跑成偏 EDM，而不是品牌片高级电子。
2. It may forget to keep the melody sparse enough for voiceover.
   可能忘记给旁白留出足够空间。

### Verdict / 判断

This should also be a **strong pass** case if the instrumental-only constraint is respected consistently.
如果“纯器乐约束”执行稳定，这个也应该是 **强通过** 案例。

---

## Test Case 3 / 测试样例 3

**Input / 输入**

```text
这是我现在的 Suno prompt: sad pop song, male vocal, piano, emotional. 帮我优化得更电影感、更高级一点，适合短视频。
```

### Expected mode / 预期 mode

`optimize_existing_prompt`

### Expected questioning behavior / 预期提问行为

The skill should probably ask **zero** follow-up questions first and attempt a direct optimization.
这个案例更适合 **先直接优化**，而不是先追问。

A possible optional follow-up could be:
可选追问只有一种比较合理：

- “Do you want it closer to emotional short-video storytelling, or closer to premium cinematic montage?”
- “你想更偏情绪短视频叙事，还是更偏高级电影感 montage？”

But the skill should be able to proceed without this.
但即使不问，这个案例也应该能直接推进。

### Expected output shape / 预期输出结构

Should produce:
应输出：

- 中文 What Needs Improvement
- English Optimized Prompt
- 中文 Why This Version Is Stronger
- English Optional Variations
- English Next Iteration Prompts

### Expected diagnosis / 预期诊断

The skill should identify that the original prompt is too weak because it is:
skill 应识别原 Prompt 偏弱的原因：

- too generic
- no scene logic
- no BPM or energy curve
- no arrangement evolution
- no cinematic texture
- no short-video fit

### Expected optimized direction / 预期优化方向

Likely upgraded language:
可能的升级方向：

- cinematic pop ballad
- emotional but restrained male vocal
- piano-led intro
- subtle strings and ambient texture
- medium-slow tempo
- early emotional hook
- short-video-friendly emotional arc

### Risks / 风险点

1. The skill may overcompensate and produce a prompt that is too long or too ornate.
   有可能补偿过度，写得太长、太花。
2. It may optimize for “cinematic” but forget “short-video fit”.
   可能只顾电影感，忘了短视频适配。

### Verdict / 判断

This is a **high-value discriminating case**.
这是一个 **很有区分度** 的样例。

If the skill handles this well, it proves the “consultant” value beyond basic routing.
如果这个案例处理得好，说明它不只是会路由，还真的有顾问价值。

---

## Test Case 4 / 测试样例 4

**Input / 输入**

```text
我有一段中文歌词，但是副歌不够抓耳，也不太像能唱出来的歌，帮我优化一下，风格偏民谣流行。
```

### Expected mode / 预期 mode

`optimize_existing_lyrics`

### Expected questioning behavior / 预期提问行为

The skill should ask **one necessary question** first:
这个案例最合理的是先问 **一个必要问题**：

- “Please send the lyric draft.”
- “请把歌词草稿发给我。”

Without the lyric draft, it should not pretend to optimize actual lyrics.
如果没有歌词原文，不能假装已经优化了具体歌词。

### Expected output shape / 预期输出结构

After the user provides the lyrics, it should produce:
在用户补充歌词后，应输出：

- 中文 Diagnosis
- 中文 Optimized Lyrics
- 中文 Singability / Hook Notes
- English Suggested Style Direction
- English Iteration Prompts

### Expected improvement focus / 预期优化重点

The skill should focus on:
应重点关注：

- making the chorus more memorable
- tightening line length for singability
- reducing prose-like lines
- preserving folk-pop sincerity
- improving repeatable hook phrasing

### Risks / 风险点

1. The skill may become too pop and lose the folk-pop plain-spoken quality.
   可能优化得太流行，失去民谣流行那种朴素表达。
2. It may rewrite too aggressively and lose the user’s core meaning.
   可能改写过猛，丢掉用户原意。

### Verdict / 判断

This is the best case for testing whether the skill knows when it **must ask for missing source material**.
这是最适合测试 skill 是否知道 **必须追要原始素材** 的案例。

---

## Test Case 5 / 测试样例 5

**Input / 输入**

```text
我想做一个适合小红书短视频的 30 秒音乐 Hook，最好前几秒就有记忆点，给我 3 个不同方向。
```

### Expected mode / 预期 mode

This is slightly ambiguous.
这个案例有一点边界模糊。

It could route to:
它可能进入：

- `generate_short_video_hook`
- or `generate_multi_versions`

### Preferred routing / 更推荐的路由

Prefer `generate_short_video_hook` as the main mode, with `3 directions` handled inside that mode.
更推荐主路由进入 `generate_short_video_hook`，然后在该 mode 内处理“3 个不同方向”。

Why / 原因：
- “30 秒”是强信号
- “前几秒就有记忆点”是 Hook-first 信号
- “3 个方向”只是输出形式，不应抢走主 mode

### Expected questioning behavior / 预期提问行为

The skill should ask **zero** or **one** question.
理论上应该 **不追问**，最多 **追问一句**：更偏带人声 Hook 还是纯器乐 Hook。

If it asks a full generic song interview, that is a miss.
如果它又退回完整歌曲访谈，就说明路由不够精确。

### Expected output shape / 预期输出结构

Should produce three clearly different options, each with:
应输出三个明显不同的方向，每个方向至少有：

- 中文 Hook Direction
- English Short Style Prompt
- English Hook Structure / Hook Lyrics Box
- English Hook Iteration Prompts

### Expected direction split / 预期方向拆分

Good version split might be:
一个比较好的方向拆分可以是：

1. catchy vocal hook / 抓耳人声 Hook
2. stylish electronic transition hook / 时尚电子转场 Hook
3. soft lifestyle / vlog-friendly hook / 柔和生活流 Hook

### Risks / 风险点

1. The skill may confuse “3 directions” with full multi-version package output.
   可能把“3 个方向”误做成完整多版本包，而不是短 Hook 方向。
2. It may forget the first-3-seconds impact requirement.
   可能忘掉“前几秒抓力”这个核心要求。

### Verdict / 判断

This is the best test for **short-form creativity + routing discipline**.
这是测试 **短形式创意能力 + 路由纪律性** 的最佳样例。

---

## Overall Findings / 总体观察

### What already looks strong / 当前看起来比较强的地方

1. The mode system is broad enough for the first batch.
   mode 体系已经足够覆盖第一批测试。
2. The Chinese-lyrics / English-prompt split is testable and meaningful.
   “中文歌词 / 英文 Prompt”分离是可测且有价值的。
3. The instrumental-vs-vocal split is one of the strongest parts of the design.
   歌曲 / 纯器乐分流是当前设计最强的一部分。

### What needs the most attention / 最值得重点盯的地方

1. Do not over-question when the user already gave enough information.
   用户信息足够时，不能过度提问。
2. Prompt optimization must feel smarter than simple rewording.
   Prompt 优化必须表现出比“改写措辞”更强的顾问能力。
3. Hook mode should not collapse into generic song generation.
   Hook 模式不能退化成普通歌曲生成。
4. Lyrics optimization must require the actual lyric draft when needed.
   歌词优化在需要原文时，必须明确索要原始歌词。

---

## Recommended Next Step / 建议下一步

Before expanding the eval set, do one lightweight manual dry run for each of the five cases.
在扩展测试集之前，建议先对这 5 个样例各做一次轻量人工 dry run。

The goal is to verify:
目标是验证：

- whether the first reply feels right
- whether follow-up questions are too many or too few
- whether the final output blocks feel appropriately scoped
- whether the prompt-language split remains consistent
