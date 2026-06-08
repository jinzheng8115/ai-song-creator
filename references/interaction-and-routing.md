# Interaction and Routing Rules
# 交互与路由规则

## Purpose / 目的

This file defines how to route user requests, how to ask questions, and how to handle missing information without over-interviewing the user.
本文定义如何路由用户请求、如何提问，以及如何在不过度盘问用户的前提下处理缺失信息。

## User interaction language / 用户交互语言

User-facing interaction should be Chinese-first.
面向用户的交互应以中文为主。

Use English as support only when it improves precision, especially for:
只有在提升准确性时才用英文辅助，尤其是：

- genre names / 曲风名称
- production terms / 制作术语
- vocal or groove labels / 人声或律动标签
- option shorthand / 选项短标签

Do not present fixed-choice questions as English-only lists when the user is Chinese-speaking.
面对中文用户时，不要把固定选项写成纯英文列表。

Recommended choice style:
推荐选项格式：

```text
A. 烟雾感 Trip-hop Lounge：更暧昧、更夜色，适合贴耳女声和慢速低频律动
B. 复古霓虹 City Pop：更时髦、更都市，适合丝滑贝斯和清晰副歌
C. 暗色 R&B Cabaret：更戏剧、更危险，适合克制鼓点和近距离人声
```

Avoid:
避免：

```text
A. Smoky trip-hop lounge
B. Retro neon city pop
C. Dark R&B cabaret
```

## Primary modes / 主模式

### `create_vocal_song`

Use when the core task is creating a lyric-based song.
当核心任务是创作带歌词歌曲时使用。

Pay special attention to:
重点关注：

- lyric language / 歌词语言
- vocal identity and delivery / 人声身份与唱法
- section-based structure / 分段结构
- chorus strategy / 副歌策略
- singability / 可唱性

### `create_instrumental_bgm`

Use when the user needs instrumental-only music, background music, underscore, ambience, or loop-first music.
当用户需要纯器乐、BGM、配乐、氛围音乐或循环优先音乐时使用。

Pay special attention to:
重点关注：

- instrumental-only constraint / 纯器乐约束
- loopability / 可循环性
- voiceover friendliness / 旁白友好度
- motif strategy / 主动机策略
- production texture / 制作质感

### `optimize_existing_prompt`

Use when the user already has a music prompt and wants it to become clearer, more musical, more tool-ready, or better aligned with intent.
当用户已经有一个音乐 Prompt，想把它优化得更清晰、更音乐化、更适配工具、或更贴合意图时使用。

### `optimize_existing_lyrics`

Use when the user already has lyrics and wants better structure, hook strength, singability, coherence, imagery, or emotional consistency.
当用户已有歌词，想提升结构、Hook、可唱性、连贯性、画面感或情绪一致性时使用。

### `generate_multi_versions`

Use when the user wants several distinct directions for the same theme.
当用户希望同一主题得到多个不同方向时使用。

### `generate_short_video_hook`

Use when the user wants a short-form concept, 30-second hook, or first-impression music idea.
当用户想要短形式概念、30 秒 Hook 或第一印象音乐点子时使用。

If multiple short directions are requested inside a short-hook task, keep this mode primary and treat the alternatives as internal variants.
如果在短 Hook 任务里顺带要求多个方向，仍以该 mode 为主，把多个方向当作内部变体。

## First-round questions / 第一轮问题

If the user has not already provided enough information, focus the first round on:
如果用户尚未提供足够信息，第一轮优先锁定：

1. track type / 类型
2. theme plus use case / 主题 + 使用场景
3. style plus mood / 风格 + 情绪

Do not begin with a giant questionnaire.
不要一开始就抛巨大问卷。

## Follow-up questions / 追问规则

Ask follow-up questions only when the missing detail materially changes the result.
只有在某个缺失字段会明显改变结果时才追问。

Typical follow-ups for vocal songs:
带歌词歌曲常见追问：

- lyric language / 歌词语言
- vocal preference / 人声偏好
- tempo preference / 节奏快慢
- hook importance / 是否强调 Hook
- existing lyric draft / 是否已有歌词草稿
- theme expression angle / 主题真正想表达的角度

Typical follow-ups for instrumental BGM:
纯器乐 BGM 常见追问：

- loopability / 是否可循环
- voiceover space / 是否给旁白留空间
- texture / 主要质感
- main instrument preference / 主体乐器偏好
- duration target / 目标时长
- duration strategy / 时长策略（循环优先 / 剪辑优先 / 精确短时长）

## Fixed-answer questions should be structured / 固定答案题应结构化

For stable-answer questions, do not force free-form typing.
对于稳定答案题，不要强迫用户自由输入。

Prefer:
优先顺序：

1. clickable structured choices / 可点击结构化选项
2. concise numbered or lettered choices / 简洁编号或字母选项
3. free text only when needed / 仅在必要时开放文本输入

Typical structured fields:
典型结构化字段：

- track type / 音乐类型
- lyric language / 歌词语言
- vocal preference / 人声偏好
- style path / 风格确定方式

When the theme is broad or under-specified, add one short disambiguation question about the intended expression angle.
当主题很宽泛或信息不足时，应增加一个简短澄清问题，确认真正想表达的角度。

Examples:
例如：

- “杭州” → 是想写城市氛围、个人记忆、爱情相遇、还是漂泊感？
- “夏天” → 是想写清爽、炽热、怀旧、青春，还是某段具体经历？
- “父亲” → 是想写感恩、距离感、沉默关系、成长回望，还是现实压力？

Prefer clickable or compact choices instead of a fully open question when a few stable angles cover most use cases.
如果少量稳定角度就能覆盖大多数需求，应优先用可点击或紧凑选项，而不是完全开放提问。

`output_format` is no longer a default interview question in the normal flow.
`output_format` 不再是默认流程中的常规提问项。

Default to the complete prompt package unless the user explicitly asks for another output form.
除非用户明确要求其他输出形式，否则默认直接输出完整 Prompt 包。

## Style selection paths / 风格选择路径

Support three style-selection paths:
支持三条风格选择路径：

1. direct style choice / 直接选择风格
2. guided recommendation when the user is unsure / 用户不确定时系统推荐
3. reference-based style analysis from a favorite song or singer / 基于喜欢的歌曲或歌手做风格分析

If the user chooses direct style choice, prefer selectable options when possible.
如果用户直接选风格，能选择就优先选择，不要逼用户手打。

If the user is unsure, recommend 2–3 plausible directions based on theme and use case.
如果用户不确定，就根据主题和场景推荐 2–3 个合理方向。

If the user gives a reference song or singer, extract abstract traits instead of instructing direct imitation.
如果用户给了参考歌曲或歌手，应提取抽象特征，而不是直接输出模仿指令。

## Creative style exploration / 创意风格探索

When the user's theme has a strong mood, character, scene, or aesthetic identity, do not jump too quickly into a generic style.
当用户主题本身具有强烈情绪、人物、场景或审美身份时，不要过快落入泛风格。

First infer what the user may be attracted to, then offer 2-3 creative style directions for selection when the runtime can ask cleanly.
应先推断用户可能在意的审美点，再在运行时允许清晰提问时，给出 2-3 个创意风格方向供用户选择。

This is especially useful for themes such as:
这尤其适用于：

- nightlife characters / 夜色人物
- urban romance / 都市暧昧
- retro nostalgia / 复古怀旧
- sports anthems / 体育主题歌
- city portraits / 城市人物或城市气质
- healing or private emotional states / 治愈或私人情绪

Each proposed direction should show the skill's creative judgment, not just repeat the user's words.
每个候选方向都应展示 skill 的创意判断，而不是简单复述用户原话。

Good direction options should include:
好的方向选项应包括：

- a concise style label / 简洁风格标签
- the mood or scene it emphasizes / 它强调的情绪或场景
- the likely vocal or groove character / 可能的人声或律动特征

Example:
示例：

```text
A. Smoky trip-hop lounge / emphasizes late-night intimacy, breathy female vocal, slow downtempo groove
B. Retro neon city pop / emphasizes stylish urban glamour, smooth bass, polished melodic hook
C. Dark R&B cabaret / emphasizes seductive tension, sparse drums, dramatic close-mic vocal
```

If the user already gives a precise style phrase, use it directly and do not over-interview.
如果用户已经给出精确风格短语，就直接使用，不要过度追问。

If the user gives a reference generated by another model or tool, treat it as useful style evidence.
如果用户给出其他模型或工具生成的参考，应把它视为有价值的风格证据。

Extract the useful musical traits and map them into structured fields such as `Genre`, `Mood`, `Vocal`, `Groove`, `Texture`, `Energy`, and `Atmosphere`.
应提取其中有用的音乐特征，并映射到 `Genre`、`Mood`、`Vocal`、`Groove`、`Texture`、`Energy`、`Atmosphere` 等结构化字段。

## Missing-information policy / 缺失信息策略

Use reasonable defaults only when they do not erase meaningful user choice.
只有在不会抹掉用户有意义选择的前提下，才使用合理默认值。

If a missing field materially changes the result, ask the user instead of silently deciding.
如果某个缺失字段会明显改变结果，就应提问，而不是静默替用户决定。

Fast path:
快速通道：

If the user already gave track type, theme or use case, style or mood, and output intent, skip the generic interview and generate directly.
如果用户已经给出类型、主题或场景、风格或情绪、以及输出意图，就跳过通用访谈直接生成。
