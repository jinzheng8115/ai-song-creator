# AI Music Prompt Skill Design
# AI 音乐 Prompt Skill 设计说明

- Date / 日期: 2026-06-06
- Status / 状态: Draft for review
- Scope / 范围: v1 design only, no implementation

---

## 1. Overview / 概述

This project will define a single interactive skill that behaves like an AI music creation consultant.
本项目将定义一个统一的交互式 skill，让它像一位 AI 音乐创作顾问一样工作。

Its job is to turn vague user ideas into structured, copy-ready prompts for Suno, Udio, and similar AI music tools.
它的核心任务，是把用户模糊的创作想法转成适用于 Suno、Udio 及类似 AI 音乐工具的结构化、可直接复制的 Prompt。

The skill should not act like a long questionnaire or a music theory encyclopedia.
这个 skill 不应表现得像一张冗长问卷，也不应像音乐理论百科。

Instead, it should:
它应该做到：

1. ask a small number of useful questions / 只问少量关键问题
2. infer missing details when safe / 在可安全推断时主动补全
3. build an internal music brief / 构建内部音乐需求对象
4. orchestrate multiple music knowledge libraries / 编排多个音乐知识库
5. output a prompt package plus creative guidance / 输出 Prompt 包与创作辅助说明
6. support easy iteration / 支持下一轮快速迭代

---

## 2. Product Positioning / 产品定位

### 2.1 Primary Role / 核心角色

The skill is a **conversational AI music creation consultant**.
这个 skill 的定位是一个 **对话式 AI 音乐创作顾问**。

It helps users move from:
它帮助用户从以下状态：

- vague idea / 模糊创意
- incomplete creative brief / 不完整需求
- weak existing prompt / 较弱的已有 Prompt
- rough lyrics draft / 粗糙歌词草稿

into:
转化为：

- tool-ready music prompts / 可直接给工具使用的音乐 Prompt
- clearer song or BGM direction / 更清晰的歌曲或 BGM 方向
- structured iteration options / 结构化迭代入口

### 2.2 Non-Goals / 非目标

v1 does not try to be:
第一版不试图成为：

- a full music production tutor / 完整音乐制作教学工具
- a legal advisor on music licensing / 音乐授权法律顾问
- a voice-cloning assistant / 声音克隆助手
- a complete DAW arrangement generator / 完整 DAW 编曲生成器
- a generic songwriting chatbot with no prompt focus / 没有 Prompt 聚焦的泛歌词聊天机器人

---

## 3. Supported Modes in v1 / 第一版支持的模式

The skill will be a single top-level skill with six internal modes.
这个 skill 采用一个统一入口，内部包含六个 mode。

1. `create_vocal_song`
2. `create_instrumental_bgm`
3. `optimize_existing_prompt`
4. `optimize_existing_lyrics`
5. `generate_multi_versions`
6. `generate_short_video_hook`

### 3.1 Why one skill instead of many / 为什么做成一个 skill 而不是多个

A single entry point keeps the user experience simple and preserves the “creative consultant” feeling.
统一入口能保持简单体验，也更符合“创作顾问”的角色设定。

The internal mode system keeps the design modular without splitting the user-facing workflow.
内部 mode 则保证结构清晰，同时不把用户流程拆散。

---

## 4. Target Users / 目标用户

The default user model is mixed:
默认用户模型是混合型：

- beginners who do not know music terms / 不懂音乐术语的小白用户
- semi-experienced users who know some genres or BPM / 略懂曲风或 BPM 的用户
- experienced Suno/Udio users who want faster refinement / 想快速打磨结果的熟练用户

### Design implication / 设计含义

The skill should be beginner-friendly by default, but it should automatically become concise when the input is already complete.
默认要对小白友好，但当用户输入已经很完整时，应自动变得简洁，不继续盘问。

---

## 5. Interaction Style / 交互风格

### 5.1 Personality / 人格感

The tone should be:
语气应当是：

- professional like a music producer / 有音乐制作人的专业判断
- warm like a creative collaborator / 也有创作搭子的温度
- confident but not rigid / 有判断但不僵硬
- helpful without overexplaining / 有帮助但不过度教学

### 5.2 Core Principle / 核心原则

**Ask less, infer more.**
**少问，多推断。**

The skill should not start with a long form.
不应一开始就像填表。

Instead, it should use:
它应使用：

- first round: 3 core questions / 第一轮 3 个核心问题
- second round: up to 2–3 refinement questions if needed / 第二轮按需补 2–3 个追问
- direct generation when information is sufficient / 信息足够就直接生成

---

## 6. Top-Level Workflow / 顶层工作流

```text
INTENT DETECTION
→ MODE ROUTING
→ CORE QUESTIONING (up to 3)
→ OPTIONAL REFINEMENT (up to 2–3)
→ BRIEF SUMMARY
→ LIBRARY ORCHESTRATION
→ OUTPUT PACKAGE
→ ITERATION SUPPORT
```

中文：

```text
意图识别
→ 模式路由
→ 第一轮 3 个核心问题
→ 必要时补充追问
→ 需求摘要
→ 素材库编排
→ 最终输出
→ 迭代支持
```

### 6.1 Core question set / 第一轮核心问题

For creation tasks, the first round should mainly determine:
对创作类任务，第一轮主要锁定：

1. track type / 类型：vocal song or instrumental BGM
2. theme + use case / 主题 + 使用场景
3. style + mood / 风格 + 情绪

### 6.2 Refinement questions / 第二轮追问

Only ask refinement questions when they materially affect output quality.
只有在会明显影响结果质量时才追问。

For vocal songs, likely refinement fields are:
对歌曲常见追问字段：

- lyric language / 歌词语言
- vocal preference / 人声偏好
- tempo preference / 节奏快慢
- hook importance / 是否特别强调副歌 Hook
- existing lyric draft / 是否已有歌词草稿

For instrumental BGM, likely refinement fields are:
对器乐常见追问字段：

- loopability / 是否可循环
- voiceover space / 是否给旁白留空间
- texture / 主要质感
- main instrument preference / 主体乐器偏好

---

## 7. Mode Routing Rules / 模式路由规则

### 7.1 `create_vocal_song`
Use when the user wants a song with singing, lyrics, chorus, theme song structure, or vocal direction.
当用户想要带演唱、带歌词、副歌、主题歌结构或明确人声方向时进入。

### 7.2 `create_instrumental_bgm`
Use when the user wants BGM, background music, instrumental, product music, study music, or no vocals.
当用户想要 BGM、背景音乐、纯器乐、产品片配乐、学习音乐或明确不要人声时进入。

### 7.3 `optimize_existing_prompt`
Use when the user already has a prompt and wants it stronger, clearer, more stable, more cinematic, more catchy, or more suitable for a scene.
当用户已经有 Prompt，并希望它更强、更清晰、更稳定、更电影感、更抓耳或更适合某个场景时进入。

### 7.4 `optimize_existing_lyrics`
Use when the user already has lyrics and wants better singability, structure, rhyme, emotional focus, or hook quality.
当用户已有歌词，想提升可唱性、结构、押韵、情绪集中度或 Hook 质量时进入。

### 7.5 `generate_multi_versions`
Use when the user asks for several directions or is unsure which style to choose.
当用户想看多个方向，或不确定该选哪种风格时进入。

### 7.6 `generate_short_video_hook`
Use when the user needs a short-form music idea, 30-second hook, first-impression impact, or short-video-friendly concept.
当用户需要短音乐片段、30 秒 Hook、开场抓力或短视频友好方向时进入。

---

## 8. Internal Music Brief / 内部 music_brief 结构

The skill should always build an internal `music_brief` before final output.
最终输出前，skill 必须先构建内部 `music_brief`。

### 8.1 Shared fields / 共享字段

```text
intent
mode
track_type
theme
use_case
language
genre
subgenre
mood
tempo
vocal
instrumentation
structure
arrangement_plan
energy_curve
hook_strategy
lyrics_strategy
loopability
voiceover_space
avoid
output_format
```

### 8.2 Vocal song brief emphasis / 歌曲 brief 重点

For vocal songs, the brief must pay special attention to:
对带人声歌曲，重点放在：

- lyric language / 歌词语言
- vocal identity and delivery / 人声身份与唱法
- chorus strategy / 副歌策略
- singability / 可唱性
- section-by-section arrangement / 逐段编曲推进

### 8.3 Instrumental brief emphasis / 器乐 brief 重点

For instrumental BGM, the brief must pay special attention to:
对纯器乐 BGM，重点放在：

- loopability / 可循环性
- non-vocal constraint / 无人声约束
- voiceover friendliness / 旁白友好度
- motif strategy / 主动机策略
- texture and editing friendliness / 质感与剪辑适配性

---

## 9. Library Orchestration Model / 素材库编排模型

The project already has a multi-library architecture. The skill should use it as a modular pipeline.
项目已具备多库架构，skill 应将其作为模块化流水线使用。

### 9.1 Library roles / 库的角色划分

#### Routing libraries / 路由层
- `ai_music_customer_interaction_workflow_v0.1_bilingual.md`
- `ai_music_library_orchestration_rules_v0.1_bilingual.md`

Use for interaction policy, mode routing, and orchestration rules.
用于交互策略、模式路由和总体编排规则。

#### Decision libraries / 决策层
- `ai_music_genre_library_v0.2.md`
- `ai_music_emotion_expression_mapping_v0.1.md`
- `ai_music_rhythm_bpm_scene_mapping_v0.1.md`
- `ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md`

Use for deciding direction, emotion translation, BPM, and structure.
用于决定音乐方向、情绪转译、BPM 与结构。

#### Realization libraries / 落地层
- `ai_music_vocal_voice_library_v0.1.md`
- `ai_music_instrumentation_arrangement_library_v0.1.md`

Use for vocal realization and arrangement realization.
用于人声落地与编曲落地。

#### Output library / 输出层
- `ai_music_prompt_templates_v0.1_bilingual.md`

Use for assembling final copy-ready output.
用于组装最终可复制输出。

### 9.2 Default call chain for vocal songs / 歌曲默认调用链

```text
Use Case Structure
→ Genre
→ Emotion
→ BPM / Rhythm
→ Vocal
→ Instrumentation / Arrangement
→ Prompt Templates
```

### 9.3 Default call chain for instrumental BGM / 器乐默认调用链

```text
Use Case Structure
→ Genre
→ Emotion
→ BPM / Rhythm
→ Skip Vocal
→ Instrumentation / Arrangement
→ Prompt Templates
```

---

## 10. Missing Information Policy / 缺失信息处理策略

The default rule is:
默认规则是：

> infer when risk is low, ask when risk is high.
> 推断风险低就补全，推断风险高才追问。

### 10.1 Inference priorities / 常见推断规则

- missing genre → infer from use case + mood / 缺曲风则从场景与情绪推断
- missing mood → infer from theme + use case / 缺情绪则从主题与场景推断
- missing BPM → infer from genre + mood + use case / 缺 BPM 则从曲风、情绪、场景推断
- missing vocal → default to natural emotional vocal, then specialize if possible / 缺人声则先给自然情绪人声，再尽量细化
- missing use case → ask one direct question / 缺使用场景时只追问一次

### 10.2 Conflict translation / 冲突信息转译

The skill should translate tension into better creative direction instead of rejecting it.
遇到信息张力时，skill 应转译成更高级的创作方向，而不是报错或机械冲突处理。

Examples:
示例：

- warm + sad → bittersweet / 温暖 + 伤感 → 苦甜感
- tech + warm → human-centered futuristic / 科技感 + 温暖 → 人本未来感
- premium + playful → stylish playful / 高级感 + 俏皮 → 时尚俏皮
- calm + short video → gentle but catchy / 平静 + 短视频 → 温柔但抓耳

---

## 11. Output Design / 输出设计

The default output principle is:
默认输出原则：

> explain briefly, provide copy-ready prompt content, then provide iteration entry points.
> 先做简短说明，再给可复制 Prompt，最后给迭代入口。

### 11.1 `create_vocal_song` default output / 歌曲默认输出

```markdown
## Requirement Summary
## Music Direction
## Title Options
## Style Prompt
## Lyrics Box
## Iteration Prompts
## Usage Notes
```

### 11.2 `create_instrumental_bgm` default output / 器乐默认输出

```markdown
## Requirement Summary
## Music Direction
## Style Prompt
## Instrumental Structure Box
## Iteration Prompts
## Usage Notes
```

### 11.3 `optimize_existing_prompt` default output / Prompt 优化默认输出

```markdown
## What Needs Improvement
## Optimized Prompt
## Why This Version Is Stronger
## Optional Variations
## Next Iteration Prompts
```

### 11.4 `optimize_existing_lyrics` default output / 歌词优化默认输出

```markdown
## Diagnosis
## Optimized Lyrics
## Suggested Style Direction
## Singability / Hook Notes
## Iteration Prompts
```

### 11.5 `generate_multi_versions` default output / 多版本默认输出

Provide three clearly separated versions.
默认提供三个区分明确的版本：

1. mainstream / 主流稳妥版
2. short-video / 短视频传播版
3. cinematic / 电影感增强版

### 11.6 `generate_short_video_hook` default output / 短视频 Hook 默认输出

```markdown
## Hook Direction
## Hook Concept Options
## Short Style Prompt
## Hook Lyrics Box / Hook Structure Box
## Iteration Prompts
```

---

## 12. Language Rules / 语言规则

This section is critical and should be enforced consistently.
这一节非常关键，必须一致执行。

### 12.1 Lyric language / 歌词语言

Lyrics must follow the user’s request.
歌词必须跟随用户要求。

- Chinese requested → output Chinese lyrics / 用户要求中文 → 输出中文歌词
- English requested → output English lyrics / 用户要求英文 → 输出英文歌词
- bilingual requested → output bilingual lyrics / 用户要求双语 → 输出双语歌词
- unspecified → default to Chinese lyrics / 未说明 → 默认中文歌词

### 12.2 Prompt language / Prompt 模块语言

All tool-ready prompt modules should default to English.
所有给工具复制使用的 Prompt 模块默认使用英文。

This includes:
包括：

- Style Prompt
- Instrumental Prompt
- control tags in Lyrics Box or Structure Box / Lyrics Box 或 Structure Box 中的控制标签
- Iteration Prompts
- Avoid / Negative instructions

### 12.3 Human-facing explanation / 给人看的说明

Human-facing explanation may follow the user’s language.
给人看的说明可以跟随用户语言。

Chinese explanation is allowed for:
中文说明允许用于：

- requirement summary / 需求摘要
- music direction notes / 音乐方向说明
- diagnosis / 问题诊断
- usage notes / 使用提醒

But explanatory text should not be mixed into tool-ready prompt blocks.
但说明文字不应混入给工具使用的 Prompt 本体。

---

## 13. Safety Rules / 安全规则

### 13.1 No direct imitation of real artists / 不直接模仿真实歌手或作品

The skill must not output prompts that request copying a real singer’s voice, a real song’s melody, or a specific artist’s exact style.
skill 不得输出复制真实歌手声音、复制具体歌曲旋律、或要求某位艺人“完全一样”的 Prompt。

Allowed replacement strategy:
允许的替代策略：

- abstract era-based style / 抽象年代风格
- genre-driven sound description / 曲风驱动的声音描述
- vocal texture description / 嗓音质感描述
- mood-based arrangement language / 基于情绪的编曲语言

### 13.2 Commercial-use reminder only / 商业使用仅做提醒

If the use case is obviously commercial, the skill should add a reminder to check platform licensing.
如果场景明显属于商业用途，skill 应提醒用户检查平台授权规则。

The skill should not pretend to provide legal certainty.
但不应假装提供法律结论。

---

## 14. Quality Checklist / 质量检查清单

Before final output, the skill should verify:
最终输出前，skill 应检查：

1. track type is clear / 类型是否清楚
2. use case is reflected in structure / 使用场景是否体现到结构中
3. mood is translated into musical behavior / 情绪是否被转成音乐行为
4. prompt is specific enough / Prompt 是否足够具体
5. vocal and instrumental logic are not mixed / 歌曲与器乐逻辑是否混淆
6. lyrics or structure look executable / 歌词或结构是否可执行
7. iteration prompts are copy-ready / 迭代 Prompt 是否可直接复制
8. no direct real-artist imitation / 是否避免真实歌手直接模仿
9. prompt modules remain in English by default / Prompt 模块是否默认英文
10. lyric language follows user request / 歌词语言是否跟随用户要求

---

## 15. SKILL.md Responsibilities / 主 SKILL.md 的职责

The main `SKILL.md` should remain lightweight.
主 `SKILL.md` 应保持轻量。

It should define:
它应定义：

1. what the skill does / skill 是做什么的
2. when it should trigger / 什么时候触发
3. how the six modes route / 六个 mode 如何路由
4. how questioning works / 提问策略如何工作
5. how `music_brief` is constructed / `music_brief` 如何构建
6. which libraries to load and when / 何时读取哪些库
7. output structure / 输出结构
8. language rules / 语言规则
9. safety rules / 安全规则
10. quality checklist / 质量检查清单

It should **not** inline the full content of all libraries.
不应把所有知识库全文塞进主 `SKILL.md`。

### 15.1 Progressive disclosure / 渐进式加载

Always read first:
优先读取：

- `ai_music_customer_interaction_workflow_v0.1_bilingual.md`
- `ai_music_library_orchestration_rules_v0.1_bilingual.md`

Then load deeper libraries only as needed.
再按需读取更深层知识库。

---

## 16. Success Criteria for v1 / 第一版成功标准

v1 is successful if the skill can reliably do the following:
如果 skill 能稳定做到以下几点，第一版就算成功：

1. turn vague ideas into usable prompt packages / 把模糊想法转成可用 Prompt 包
2. ask only a few useful questions / 只问少量真正有用的问题
3. distinguish vocal songs from instrumental BGM correctly / 正确区分歌曲与纯器乐
4. produce English prompt modules and correctly localized lyrics / 输出英文 Prompt 模块与正确语言的歌词
5. give users clear next-step iteration prompts / 给出清晰的下一轮优化入口
6. feel like a music consultant instead of a rigid form / 像创作顾问，而不是僵硬表单

---

## 17. Open Implementation Follow-up / 后续实现工作

After this spec is approved, the next work should be:
本 spec 批准后，下一步应当是：

1. draft `SKILL.md` / 起草主 `SKILL.md`
2. draft `README.md` / 起草 `README.md`
3. reorganize files into skill-style directories if desired / 按 skill 结构重组目录（如果需要）
4. add examples / 增加 examples
5. add prompt quality and copyright checklists / 增加 Prompt 质量与版权检查清单
6. create a small eval set for real prompts / 准备一小组真实测试用例

