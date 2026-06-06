# AI Music Prompt Skill Representative Full Response Examples v0.1
# AI 音乐 Prompt Skill 代表性完整回答示例 v0.1

## Purpose / 用途

This document shows five representative full responses that the current skill should be able to produce.
本文展示当前 skill 应该能够产出的 5 个代表性完整回答示例。

These are not final polished product outputs.
它们不是最终精修版产品文案。

They are working reference examples for checking:
它们是工作参考样例，用于检查：

- first-turn behavior / 第一轮响应是否合理
- output structure / 输出结构是否顺手
- language split / 语言分离是否稳定
- consultant tone / 顾问式语气是否成立

---

## Example 1 / 示例 1
### Case: New vocal song with rich input / 场景：信息完整的新建歌曲

**User / 用户**

```text
我想做一首中文流行抒情歌，主题是 30 岁以后还在努力生活，适合发朋友圈，温暖但有点伤感，男声，输出完整 Prompt 包。
```

**Expected skill response / 预期 skill 回答**

我会按这个方向直接生成，不再重复追问：

- 类型：带歌词中文歌曲
- 主题：30 岁以后仍在努力生活
- 使用场景：朋友圈分享
- 曲风：中文流行抒情
- 情绪：温暖、苦甜、克制，但最终有希望感
- 人声：成熟、自然、有生活感的男声
- 节奏：中慢速
- 输出：完整 Prompt 包

# AI Music Prompt Package

## 1. Requirement Summary
- 类型：带歌词歌曲
- 语言：中文歌词
- 场景：朋友圈分享
- 曲风方向：中文流行抒情
- 情绪方向：warm, bittersweet, hopeful
- 人声方向：成熟情绪男声

## 2. Music Direction
这首歌不应该做成单纯“很丧”的苦情歌，而应该是有生活重量感的温暖伤感路线。主歌保持克制和叙事感，副歌再把“还在往前走”的希望感抬起来。整体适合朋友圈传播，所以旋律要顺口、情绪要真诚，不能太戏剧化。

## 3. Title Options
- 还在往前走
- 三十岁以后
- 生活还没停
- 慢一点也算前进
- 还有光

## 4. Style Prompt
```text
Chinese pop ballad, warm and bittersweet mood, medium-slow tempo around 80-90 BPM, mature emotional male vocal, natural and restrained delivery, piano and acoustic guitar driven arrangement, warm bass, light drums, subtle cinematic strings, intimate verse, emotionally uplifting chorus, reflective but hopeful energy curve, suitable for personal social sharing, avoid overly theatrical vocals and heavy electronic effects.
```

## 5. Lyrics Box
```text
[Style: Chinese pop ballad, warm bittersweet, 80-90 BPM]
[Vocal: mature emotional male vocal, natural and restrained]
[Arrangement: piano, acoustic guitar, warm bass, light drums, subtle strings]
[Energy: quiet reflection to hopeful release]
[Use Case: personal sharing]

[Intro - soft piano motif, intimate atmosphere]
三十岁以后
我学会把沉默说得温柔
白天追着生活走
夜里把疲惫慢慢收

[Verse 1 - sparse piano and acoustic guitar]
有些梦没有赢得漂亮
有些路也绕了很久
我不是没有失望过
只是还舍不得回头

[Pre-Chorus - add light drums and warm bass]
人群里我也会迟疑
灯熄了也会想放弃
可天亮以前的那一点呼吸
还提醒我别停在原地

[Chorus - fuller drums, bass, strings, memorable hook]
我还在往前走
慢一点也算没有停留
有些伤口陪着我成熟
有些夜晚教会我温柔
我还在往前走
哪怕风很大路很旧
如果未来来得晚一点
我也想笑着把它等候

[Bridge - drop back to piano and voice]
也许答案不会立刻出现
也许人生本来就没有标准线
但我知道每一步没白走远
我还愿意，再把明天试一遍

[Final Chorus - wider strings, stronger backing support]
我还在往前走
慢一点也算没有停留
那些遗憾没有把我带走
反而让我更懂得拥有
我还在往前走
天再黑也还有出口
如果未来来得晚一点
我就点一盏灯继续等候

[Outro - return to piano motif, warm resolved ending]
三十岁以后
我还是想认真地活
```

## 6. Iteration Prompts
```text
Make the chorus even more catchy with a shorter repeated hook phrase.
```

```text
Make the arrangement more cinematic and expansive in the final chorus.
```

```text
Make the vocal feel more intimate and less polished, like a personal confession.
```

```text
Reduce the sadness slightly and make the hopeful release stronger.
```

## 7. Usage Notes
- 这版更偏“成熟生活感 + 温暖希望感”，适合朋友圈、短视频情绪表达。
- 如果你想更民谣一点，我可以再给你一个更朴素、更像真实口语叙事的版本。
- 如用于商业发布，请先确认目标 AI 音乐平台的商业授权规则。

---

## Example 2 / 示例 2
### Case: Instrumental BGM for product film / 场景：产品片纯器乐 BGM

**User / 用户**

```text
帮我做一段科技产品宣传片背景音乐，不要人声，要高级、未来感、干净一点，适合旁白。
```

**Expected skill response / 预期 skill 回答**

我先按“科技产品宣传片 BGM”直接生成，不再问人声或歌词类问题。

默认方向：
- 类型：纯器乐 BGM
- 场景：科技产品宣传片
- 目标：高级、未来感、干净、适合旁白
- 重点：不给画面和旁白抢空间

# AI Instrumental Prompt Package

## 1. Requirement Summary
- 类型：纯器乐 / BGM
- 人声：无
- 使用场景：科技产品宣传片
- 情绪：premium, futuristic, clean, optimistic
- 约束：voiceover-friendly

## 2. Music Direction
这类音乐不适合做成强 drop、强主唱或强旋律抢镜的电子乐。更适合“高级科技感背景音乐”路线：用干净的电子质感、克制的脉冲节奏和不打扰的主旋律动机，给画面提供推进感，同时为旁白留出中频空间。

## 3. Style Prompt
```text
Premium minimal electronic instrumental, futuristic and clean mood, medium tempo around 100-110 BPM, instrumental only, no vocals, no rap, no spoken words, pulsing synths, minimal electronic drums, soft sub bass, digital pads, subtle arpeggiated motion, non-distracting main motif, clean midrange for voiceover, modern product-film energy, polished and spacious production, avoid aggressive EDM drops and overly dense lead melodies.
```

## 4. Instrumental Structure Box
```text
[Instrumental Only]
[No vocals, no rap, no spoken words]
[Style: premium minimal electronic, futuristic, clean, medium tempo]
[Instrumentation: pulsing synths, minimal drums, soft sub bass, digital pads]
[Use Case: tech product film]
[Energy: controlled build, clear but non-intrusive]
[Voiceover: leave room in the midrange]

[Intro - clean digital texture, soft synth pulse, subtle anticipation]
[Main Groove - minimal beat enters, soft sub bass, stable pulse]
[Build - add light arpeggiated synth movement, slightly wider stereo field]
[Main Theme - memorable but restrained synth motif, still voiceover-friendly]
[Breakdown - reduce rhythm density, keep atmosphere and motion]
[Final Section - polished lift, brighter harmonic layer, no heavy drop]
[Outro - clean resolved ending, suitable for logo reveal or edit cut]
```

## 5. Iteration Prompts
```text
Make it even more minimal and luxurious, with less rhythmic activity.
```

```text
Add a slightly stronger futuristic pulse without making it feel like club EDM.
```

```text
Make the motif more memorable while still leaving room for voiceover.
```

```text
Create a more seamless loop-friendly ending for repeated playback.
```

## 6. Usage Notes
- 这版偏品牌片 / 产品宣传片，不偏功能演示视频的轻快 BGM。
- 如果你要更“苹果式极简高级感”或更“硬科技未来感”，我可以再给你两个变体。
- 如用于商业发布，请先确认目标 AI 音乐平台的商业授权规则。

---

## Example 3 / 示例 3
### Case: Prompt optimization / 场景：已有 Prompt 优化

**User / 用户**

```text
这是我现在的 Suno prompt: sad pop song, male vocal, piano, emotional. 帮我优化得更电影感、更高级一点，适合短视频。
```

**Expected skill response / 预期 skill 回答**

可以，我先不追问，先直接把这个 Prompt 从“太泛”优化成“更可执行的短视频电影感方向”。

# Optimized Music Prompt

## 1. What Needs Improvement
你现在这版 Prompt 的问题主要在这里：

- 信息太泛：`sad pop song` 和 `emotional` 都太宽，不能稳定控制结果。
- 缺少场景信息：没有体现“适合短视频”的结构和开头抓力。
- 缺少编曲推进：只有钢琴，没有说明副歌怎么打开、情绪怎么推进。
- 缺少电影感质感：没有弦乐、空间感、氛围层、能量弧线等线索。
- 人声太模糊：`male vocal` 不够区分音色和演唱方式。

## 2. Optimized Prompt
```text
Cinematic pop ballad for short-form video, bittersweet and emotionally restrained mood, medium-slow tempo around 80-90 BPM, intimate male vocal with warm mature tone, piano-led intro, subtle ambient texture, soft strings entering gradually, light drums and warm bass lifting the chorus, early emotional hook, reflective verse and more expansive chorus, polished and elegant production, suitable for emotional short-video storytelling, avoid overly dramatic vocals and generic radio-pop energy.
```

## 3. Why This Version Is Stronger
这版更强，主要因为：

1. 它把“sad”细化成了 `bittersweet` 和 `emotionally restrained`，情绪更可控。
2. 它明确了 `short-form video` 场景，不再是泛化流行歌。
3. 它给了更清楚的编曲推进：钢琴开场、弦乐渐入、副歌抬升。
4. 它把男声从普通 `male vocal` 升级成了更有辨识度的 `warm mature tone`。
5. 它加入了避免项，减少跑偏成“大喊大叫的苦情流行歌”。

## 4. Optional Variations
```text
More intimate version: make it softer, more piano-forward, and less cinematic.
```

```text
More premium version: add a wider string texture and more elegant ambient depth.
```

```text
More short-video version: move the emotional hook even earlier and shorten the intro.
```

## 5. Next Iteration Prompts
```text
Make the first 5 seconds more emotionally memorable for short-video retention.
```

```text
Add a slightly stronger cinematic lift in the chorus without making it too dramatic.
```

```text
Make the vocal feel more natural and intimate, less polished and less theatrical.
```

---

## Example 4 / 示例 4
### Case: Lyrics optimization requires source text / 场景：歌词优化需要先索要原文

**User / 用户**

```text
我有一段中文歌词，但是副歌不够抓耳，也不太像能唱出来的歌，帮我优化一下，风格偏民谣流行。
```

**Expected skill response / 预期 skill 回答**

可以，但要先给我歌词原文。

因为这次不是单纯给你一个风格方向，而是要做“具体歌词优化”，我需要看到：

- 主歌和副歌现在怎么写
- 哪些句子太像散文
- 哪些位置缺少 Hook
- 哪些句长不够顺口、不够能唱

你直接把歌词贴给我就行。贴完后我会按这个结构帮你处理：

1. 中文诊断：哪里不够抓耳、哪里不够可唱
2. 中文优化歌词：尽量保留原意，不乱改核心表达
3. 英文风格方向：给出适合民谣流行的 Style Prompt
4. 英文迭代 Prompt：方便你下一轮继续调

如果你愿意，我也可以在你贴歌词后额外给你两版：
- 更朴素真诚版
- 更容易传播、Hook 更明显版

**Why this is the right behavior / 为什么这才是正确行为**

这个场景下，skill 不应该假装已经“优化了具体歌词”。
没有歌词原文，只能先索要原文，这是正确的顾问行为。

---

## Example 5 / 示例 5
### Case: Direct artist imitation request / 场景：真实歌手模仿请求

**User / 用户**

```text
帮我做一首像周杰伦那样唱、旋律也像《晴天》那种感觉的歌。
```

**Expected skill response / 预期 skill 回答**

我不能直接帮你做成“像某位真实歌手那样唱”或“旋律像某首具体作品”的版本。

但我可以保留你真正想要的那种感觉，换成不直接模仿具体艺人和作品的写法。

如果我理解你的意图，你大概率是在要这种方向：

- 华语青春感流行
- 温暖、略带怀旧的校园 / 回忆气质
- 顺口、旋律性强的流行抒情写法
- 男声，带一点少年感和自然叙事感
- 不要太重编曲，保留吉他 / 钢琴的清爽感

我先按这个合法替代方向给你一版：

## Alternative Direction / 替代方向

这版不直接模仿具体歌手或具体歌曲，但会保留你想要的“青春怀旧、顺口旋律、清爽华语流行”感觉。

## Style Prompt
```text
Nostalgic Mandopop ballad with youthful warmth, melodic and memorable phrasing, clean male vocal with natural storytelling delivery, light acoustic guitar and piano driven arrangement, soft band feel, reflective and sunny bittersweet mood, medium tempo, campus-memory atmosphere, emotionally sincere but not overly dramatic, polished but not dense production, avoid direct imitation of any real singer or song.
```

## Optional Direction Variants
```text
Make it more acoustic and intimate, like a personal memory song.
```

```text
Make it brighter and more youthful, with a stronger sing-along chorus.
```

```text
Make it slightly more cinematic and nostalgic, while keeping the arrangement clean.
```

## Usage Note
如果你愿意，我下一步可以继续帮你把这个方向细化成：

1. 完整歌曲 Prompt 包
2. 一版中文歌词
3. 两个不同年代感变体（更校园 / 更城市回忆）

这样能保留你想要的气质，但不会直接复制具体歌手和具体作品。

---

## Overall Takeaway / 总结

These five examples represent the most important first-v1 response patterns:
这 5 个示例基本代表了 v1 最关键的几种首轮响应模式：

1. rich-input direct generation / 输入完整时直接生成
2. instrumental constraint handling / 纯器乐约束处理
3. diagnostic prompt optimization / 带诊断的 Prompt 优化
4. source-required lyrics optimization / 需要原文的歌词优化
5. refuse-and-redirect safety handling / 拒绝并改写替代方向的安全处理

If these five feel natural, the skill already has a strong usable core.
如果这 5 类表现都自然，这个 skill 的可用核心就已经很强了。
