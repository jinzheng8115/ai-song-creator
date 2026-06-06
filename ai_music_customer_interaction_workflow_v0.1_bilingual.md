# AI Music Customer Interaction Workflow v0.1 Bilingual  
# AI 音乐客户创作交互流程 v0.1 双语版

> Purpose / 用途：  
> This document defines the customer-facing interaction workflow for an interactive AI music prompt skill.  
> 本文档用于定义交互式 AI 音乐 Prompt Skill 的客户创作交互流程。
>
> The skill should behave like an AI music producer: it asks a small number of useful questions, understands the user’s creative intent, summarizes the brief, and then generates copy-ready prompts for AI music tools such as Suno, Udio, or similar platforms.  
> 这个 Skill 应该像一位 AI 音乐制作人：通过少量关键问题理解用户创作意图，整理需求摘要，然后生成可以直接复制到 Suno、Udio 或类似 AI 音乐软件中的 Prompt。

---

## 1. Design Principles / 设计原则

### 1.1 Ask Less, Infer More / 少问问题，多做推断

Most users are not music professionals.  
大多数用户不是音乐专业人士。

The skill should not ask a long questionnaire at the beginning.  
Skill 不应一开始就抛出长问卷。

Default rule / 默认规则：

```text
Ask at most 5–6 core questions in the first round.
第一轮最多问 5–6 个核心问题。
```

If the user has already provided enough information, proceed directly.  
如果用户已经提供足够信息，应直接生成，不要继续追问。

---

### 1.2 Separate Vocal Song and Instrumental BGM Early / 尽早区分带歌词歌曲与纯器乐 BGM

This is the most important routing question.  
这是最重要的路由问题。

Vocal songs need / 带歌词歌曲需要：

```text
lyrics, vocal style, chorus, hook, song structure
歌词、人声、主歌副歌、Hook、歌曲结构
```

Instrumental tracks need / 纯器乐需要：

```text
instrumental only, no vocals, motif, groove, texture, loopability
纯器乐、无人声、主动机、律动、质感、可循环性
```

If the user says “BGM”, “background music”, “study music”, “product video music”, or “instrumental”, default to instrumental.  
如果用户说“BGM”“背景音乐”“学习音乐”“产品视频音乐”“纯器乐”，默认进入纯器乐路线。

If the user says “theme song”, “song”, “lyrics”, “sing”, or “chorus”, default to vocal song.  
如果用户说“主题歌”“歌曲”“歌词”“演唱”“副歌”，默认进入带歌词歌曲路线。

---

### 1.3 Use Progressive Interaction / 使用渐进式交互

The skill should collect only the information needed for the current task.  
Skill 只采集完成当前任务所需的信息。

Interaction depth should depend on input completeness.  
交互深度取决于用户输入完整度。

When a question has a fixed answer set, present choices instead of asking the user to type a free-form answer. When the interface supports clickable options, clickable selection is preferred.  
当一个问题的答案集合是固定的，应该直接给用户选项，而不是让用户自由输入。如果界面支持可点击选项，优先使用点击选择。

Use free-form questions only for creative content such as theme, use case, style, mood, story angle, or imagery.  
只有主题、场景、风格、情绪、故事角度、画面感这类创意内容，才使用开放输入。

Three levels / 三种情况：

```text
1. vague input → interview mode
   输入模糊 → 访谈模式

2. partially complete input → ask only missing critical fields
   输入部分完整 → 只追问关键缺失项

3. complete input → summarize and generate directly
   输入完整 → 摘要后直接生成
```

---

## 2. Trigger Conditions / Skill 触发条件

Use this workflow when the user asks to:  
当用户提出以下需求时，应使用本流程：

```text
create a song / 创作歌曲
generate a Suno prompt / 生成 Suno Prompt
generate a Udio prompt / 生成 Udio Prompt
write lyrics for AI music / 为 AI 音乐写歌词
create BGM / 创作 BGM
create instrumental music / 创作纯器乐
create a theme song / 创作主题歌
create a brand song / 创作品牌歌
create a sports anthem / 创作体育主题歌
create short-video music / 创作短视频音乐
optimize an AI music prompt / 优化 AI 音乐 Prompt
turn an article or idea into a song / 把文章或想法改成歌曲
```

---

## 3. Interaction State Machine / 交互状态机

```text
START
  ↓
INTENT_DETECTION
  ↓
TRACK_TYPE_ROUTING
  ↓
REQUIREMENT_COLLECTION
  ↓
OPTIONAL_REFINEMENT
  ↓
REQUIREMENT_SUMMARY
  ↓
LIBRARY_SELECTION
  ↓
PROMPT_ASSEMBLY
  ↓
OUTPUT_PACKAGE
  ↓
ITERATION_SUPPORT
```

中文说明：

```text
开始
  ↓
意图识别
  ↓
歌曲 / 器乐路线判断
  ↓
核心需求采集
  ↓
可选细化
  ↓
需求摘要
  ↓
素材库选择
  ↓
Prompt 组装
  ↓
最终输出
  ↓
后续迭代支持
```

---

## 4. Step 1: Intent Detection / 第一步：意图识别

The skill should first identify what the user wants.  
Skill 首先判断用户要做什么。

### 4.1 Possible Intents / 可能意图

| Intent ID | English | 中文 |
|---|---|---|
| `new_vocal_song` | create a new song with lyrics | 创作带歌词歌曲 |
| `new_instrumental` | create instrumental music / BGM | 创作纯器乐 / BGM |
| `suno_prompt` | generate a Suno-style prompt | 生成 Suno 风格 Prompt |
| `udio_prompt` | generate a Udio-style prompt | 生成 Udio 风格 Prompt |
| `lyrics_only` | write lyrics only | 只写歌词 |
| `style_prompt_only` | write style prompt only | 只写 Style Prompt |
| `optimize_prompt` | improve an existing prompt | 优化已有 Prompt |
| `optimize_lyrics` | improve existing lyrics | 优化已有歌词 |
| `multi_version` | generate multiple style versions | 生成多风格版本 |
| `short_video_hook` | generate 30-second hook | 生成 30 秒短视频 Hook |

---

## 5. Step 2: Track Type Routing / 第二步：音乐类型路由

### 5.1 Track Type Options / 类型选项

```text
vocal_song / 带人声歌曲
instrumental_bgm / 纯器乐 / BGM
unclear / 不明确
```

### 5.2 Routing Rules / 路由规则

| User Says / 用户说 | Route / 路由 |
|---|---|
| 歌、歌曲、主题歌、歌词、演唱、副歌 | `vocal_song` |
| song, theme song, lyrics, sing, chorus | `vocal_song` |
| BGM、背景音乐、纯器乐、配乐、学习音乐 | `instrumental_bgm` |
| BGM, background music, instrumental, score, study music | `instrumental_bgm` |
| 短视频音乐 / short video music | ask or provide both / 追问或提供两版 |
| 品牌音乐 / brand music | ask theme song or background / 追问主题歌或背景音乐 |

### 5.3 Clarifying Question / 澄清问题

If unclear, ask as a direct choice:  
如果不明确，用直接选择题询问：

```text
先选音乐类型：
A. 带歌词、有人声演唱的歌曲
B. 纯器乐 / BGM

Choose the track type:
A. Vocal song with lyrics
B. Instrumental / BGM
```

---

## 6. Step 3: Core Requirement Collection / 第三步：核心需求采集

First-round questions should be limited to 6.  
第一轮问题控制在 6 个以内。

### 6.1 First-Round Question Block / 第一轮提问话术

For fixed routing fields, use direct choices. Clickable choices are preferred whenever the interface supports them.  
对于固定路由字段，直接给用户选项。如果界面支持，优先使用可点击选项。

Example / 示例：

```text
好的，我会帮你生成一套可以直接复制到 Suno / Udio / 类 Suno AI 音乐软件里的 Prompt。

我们先快速确认 3 件事：

1. 先选音乐类型：
   A. 带歌词歌曲
   B. 纯器乐 / BGM

2. 主题和使用场景是什么？
   比如毕业、爱情、品牌、世界杯；短视频、朋友圈、婚礼、活动开场、学习 BGM。

3. 风格怎么定？你可以三选一：
   A. 直接选风格（中文流行 / 民谣 / R&B / 电影感 / 电子 / 国风 ...）
   B. 不确定，让我推荐 2–3 个方向
   C. 给我一首你喜欢的歌或一个歌手，我来帮你分析成风格方向
```

If output format is still unclear, ask it as a choice question too. Prefer clickable options in product UI, and use typed A/B/C only as fallback:  
如果输出形式仍不明确，也用选项题继续问。产品界面中优先用可点击选项，A/B/C 文本输入仅作为 fallback：

```text
你希望输出哪一种？
A. 简洁版 Prompt
B. 完整 Prompt 包
C. 歌词 + Style Prompt
D. 多风格版本
E. 30 秒短视频 Hook
```

English version / 英文版：

```text
Great. I will help you create a copy-ready prompt package for Suno / Udio / similar AI music tools.

Please answer these 6 questions:

1. Do you want a vocal song with lyrics, or an instrumental / BGM track?
2. What is the theme?
3. Where will it be used? Short video, social sharing, brand film, event opening, study BGM, wedding, sports event, etc.
4. What style do you like? Pop, folk, rock, electronic, R&B, Chinese traditional pop, cinematic, lo-fi, sports anthem, etc.
5. What emotion should it express? Warm, sad, healing, energetic, nostalgic, cinematic, premium, futuristic, etc.
6. What output format do you want?
   A. Simple Prompt
   B. Complete Prompt Package
   C. Lyrics + Style Prompt
   D. Multi-Style Versions
   E. 30-Second Short-Video Hook
```

---

## 7. Step 4: Optional Refinement / 第四步：可选细化

Only ask optional questions if the answer is necessary.  
只有在确实需要时才追问可选问题。

### 6.2 Style Selection Paths / 曲风选择路径

Style should not rely on only one interaction path.  
曲风选择不应只有单一路径。

Support these three paths / 支持以下三条路径：

```text
A. Direct style choice / 直接选风格
B. Guided recommendation / 系统推荐风格
C. Reference-based style analysis / 参考歌曲或歌手分析风格
```

If the user chooses guided recommendation, the system should recommend 2–3 likely directions based on the theme and use case.  
如果用户选择系统推荐，系统应根据主题和场景推荐 2–3 个可能方向。

If the user gives a favorite song or singer, the system should extract abstract style traits instead of directly imitating the reference.  
如果用户给了喜欢的歌曲或歌手，系统应提取抽象风格特征，而不是直接模仿。

### 7.1 Optional Questions for Vocal Songs / 带人声歌曲可选问题

```text
1. 歌曲语言：中文 / 英文 / 中英混合？
2. 人声偏好：男声 / 女声 / 合唱 / 男女对唱 / 不确定？
3. 节奏偏好：慢歌 / 中速 / 快歌？
4. 是否需要副歌特别抓耳？
5. 有没有已有歌词需要优化？
```

English:

```text
1. Language: Chinese / English / bilingual?
2. Vocal preference: male / female / group vocals / duet / unsure?
3. Tempo preference: slow / medium / fast?
4. Should the chorus be especially catchy?
5. Do you already have lyrics to improve?
```

### 7.2 Optional Questions for Instrumental BGM / 纯器乐可选问题

```text
1. 是否需要适合循环播放？
2. 是否需要给旁白留空间？
3. 主要想要什么质感：Lo-fi、科技感、电影感、轻松 Vlog、运动高光？
4. 主体乐器偏好：钢琴、吉他、合成器、鼓点、弦乐，还是不确定？
```

English:

```text
1. Should it be loop-friendly?
2. Should it leave room for voiceover?
3. What texture do you want: lo-fi, tech, cinematic, relaxed vlog, sports highlight?
4. Preferred main instruments: piano, guitar, synth, drums, strings, or unsure?
```

---

## 8. Step 5: Requirement Summary / 第五步：需求摘要

Before generating, the skill should summarize the inferred direction.  
生成前，Skill 应先整理需求摘要。

Do not force confirmation unless the user requested it.  
除非用户明确要求确认，否则不强制等待确认。

### 8.1 Vocal Song Summary Example / 带人声歌曲摘要示例

```text
我会按下面这个方向生成：

- 类型：带歌词中文歌曲
- 主题：中年人仍在努力生活
- 使用场景：朋友圈 / 短视频
- 曲风：中文流行抒情
- 情绪：温暖、苦甜、最终有希望
- 人声：成熟男声
- 速度：中慢速，约 80–90 BPM
- 结构：Intro → Verse → Pre-Chorus → Chorus → Bridge → Final Chorus
- 输出：完整 Prompt 包（包含推荐歌名）

下面直接生成。
```

### 8.2 Instrumental Summary Example / 纯器乐摘要示例

```text
我会按下面这个方向生成：

- 类型：纯器乐 / BGM
- 使用场景：科技产品宣传片
- 曲风：极简电子 / 科技感背景音乐
- 情绪：高级、未来感、干净、积极
- 人声：无。使用 instrumental only, no vocals
- 速度：中速，约 95–115 BPM
- 编曲：合成器脉冲、极简电子鼓、低频贝斯、数字质感
- 输出：纯器乐 Prompt 包

下面直接生成。
```

---

## 9. Step 6: Library Selection / 第六步：素材库选择

After collecting requirements, select libraries based on track type and use case.  
采集需求后，根据类型和场景选择需要调用的素材库。

### 9.1 Required Libraries / 必须调用的库

For every generation / 每次生成都需要：

```text
Use Case Structure & Arrangement Library
使用场景结构与编曲库

Genre Library
曲风库

Emotion Expression Mapping Library
情绪与音乐表达映射库

Rhythm / BPM / Scene Mapping Library
节奏 / BPM / 场景映射库

Instrumentation & Arrangement Library
乐器与编曲素材库

Prompt Template Library
Style Prompt / Lyrics Box / Iteration Prompt 模板库
```

For vocal songs only / 仅带人声歌曲需要：

```text
Vocal & Voice Library
人声与嗓音描述库
```

For instrumental tracks / 纯器乐：

```text
Skip vocal library and add:
instrumental only, no vocals, no rap, no spoken words
跳过人声库，并加入上述固定排除语
```

---

## 10. Step 7: Prompt Assembly / 第七步：Prompt 组装

The skill should not generate the final prompt directly from user text.  
Skill 不应直接从用户原话跳到最终 Prompt。

It should first create an internal structured brief.  
应先生成内部结构化需求对象。

### 10.1 Internal Music Brief / 内部音乐需求对象

```json
{
  "track_type": "vocal_song",
  "theme": "中年人还在努力生活",
  "use_case": "朋友圈 / 短视频",
  "language": "Chinese",
  "genre": "Chinese pop ballad",
  "mood": ["warm", "bittersweet", "hopeful"],
  "tempo": {
    "description": "medium-slow",
    "bpm": "80–90 BPM"
  },
  "vocal": {
    "style": "mature emotional male vocal",
    "delivery": "natural, restrained, intimate"
  },
  "instrumentation": [
    "soft piano",
    "acoustic guitar",
    "warm bass",
    "light drums",
    "cinematic strings"
  ],
  "structure": [
    "[Intro - soft piano motif]",
    "[Verse 1 - sparse piano and acoustic guitar]",
    "[Pre-Chorus - add light drums and subtle strings]",
    "[Chorus - full drums, bass, strings, memorable emotional hook]",
    "[Bridge - breakdown to piano and vocal only]",
    "[Final Chorus - wider strings and backing vocals]",
    "[Outro - return to piano motif]"
  ],
  "energy_curve": "quiet reflection to hopeful release",
  "avoid": [
    "aggressive drums",
    "overly theatrical vocals",
    "excessive electronic effects"
  ],
  "output_format": "complete_prompt_package"
}
```

---

## 11. Step 8: Output Package / 第八步：最终输出

Default output format / 默认输出格式：

```markdown
# AI Music Prompt Package / AI 音乐 Prompt 包

## 1. Requirement Summary / 需求摘要

## 2. Music Direction / 音乐方向

## 3. Recommended Title Options / 推荐歌名

## 4. Style Prompt / 风格提示词

## 5. Structure & Arrangement Notes / 结构与编曲说明

## 6. Lyrics / 歌词正文

## 7. Iteration Prompts / 迭代优化 Prompt

## 8. Usage Notes / 使用提醒
```

For lyric-based songs, `Recommended Title Options` should normally contain 3–5 recommended names instead of a single default title.  
对于带歌词歌曲，`Recommended Title Options` 通常应提供 3–5 个推荐歌名，而不是只给一个默认歌名。

Song-title recommendations should be visually explicit and easy to choose from.  
歌名建议应显式呈现，并方便用户直接选择。

When the user is still exploring direction, the title list can be phrased so the user can pick one and continue refining the song around that title.  
当用户还在收方向时，歌名列表可以设计成便于用户直接选一个，再围绕该歌名继续细化歌曲。

For lyric-based songs, do not merge lyrics into the same block as control tags or arrangement notes. Keep `Lyrics` separate from `Structure & Arrangement Notes`.  
对于带歌词歌曲，不要把歌词正文和控制标签、编曲说明混在同一个模块里。应把 `Lyrics` 与 `Structure & Arrangement Notes` 分开。

For instrumental / 纯器乐输出格式：

```markdown
# AI Instrumental Prompt Package / AI 纯器乐 Prompt 包

## 1. Requirement Summary / 需求摘要

## 2. Music Direction / 音乐方向

## 3. Style Prompt / 风格提示词

## 4. Custom Box / 结构编曲框

## 5. Iteration Prompts / 迭代优化 Prompt

## 6. Usage Notes / 使用提醒
```

---

## 12. Step 9: Iteration Support / 第九步：迭代支持

Always provide 3–5 copy-ready iteration prompts.  
始终提供 3–5 条可直接复制的迭代优化 Prompt。

Example / 示例：

```text
Make the chorus more catchy and emotionally uplifting, with a stronger repeated hook phrase and fuller arrangement.
让副歌更抓耳、更振奋，加入更强的重复 Hook 短句和更丰满的编曲。
```

```text
Make the vocal more natural and emotionally restrained, less theatrical and less exaggerated.
让人声更自然、更克制有情绪，减少戏剧化和夸张唱法。
```

```text
Make the arrangement build more clearly from sparse verses to a fuller chorus.
让编曲从克制主歌到丰满副歌的推进更清楚。
```

For instrumental / 纯器乐：

```text
Make it more suitable as background music: less distracting, more loop-friendly, no vocals, no rap, no spoken words.
让它更适合作为背景音乐：减少打扰，更适合循环，无人声、无说唱、无旁白。
```

---

## 12.1 Real-user interaction preference / 真实用户交互优先

When the workflow is being tested or used in a real user-facing interaction, prefer asking the user directly for meaningful missing choices instead of silently filling them with defaults.  
当工作流处于真实用户测试或真实用户交互场景时，优先直接向用户询问有意义的缺失选择，而不是静默用默认值补齐。

Defaults are still useful when the user explicitly wants speed or does not care about the missing field.  
如果用户明确希望更快，或明确表示不在意该字段，默认值仍然有用。

## 13. Default Values / 默认值

If the user does not specify, use these defaults.  
用户未说明时，使用以下默认值。

| Field / 字段 | Default / 默认值 |
|---|---|
| track_type / 类型 | vocal_song unless BGM/instrumental is mentioned / 默认带人声，除非用户说 BGM 或纯器乐 |
| language / 语言 | Chinese / 中文 |
| output_format / 输出格式 | complete_prompt_package / 完整 Prompt 包 |
| tempo / 速度 | medium tempo / 中速 |
| lyrics / 歌词 | required for vocal song / 带人声歌曲默认需要歌词 |
| instrumental exclusion / 纯器乐排除项 | instrumental only, no vocals, no rap, no spoken words |
| structure / 结构 | selected by use case / 根据使用场景选择 |
| vocal / 人声 | natural emotional vocal / 自然情绪人声 |
| iteration prompts / 迭代 Prompt | always include 3–5 / 始终包含 3–5 条 |

---

## 14. Special Handling Rules / 特殊处理规则

### 14.1 User Does Not Know the Genre / 用户不知道曲风

If the user says “I don’t know the style”, recommend 3 options.  
如果用户说“不知道什么风格”，推荐 3 个方向。

Example / 示例：

```text
你可以从这 3 个方向选：

1. 中文流行抒情：最稳妥，适合大众传播和情感表达。
2. 民谣流行：更真诚，适合个人故事和生活感。
3. 电影感流行：更高级，适合视频、公众号或品牌感。
```

### 14.2 User Wants Short Video Music / 用户要短视频音乐

If unclear, offer two routes.  
不明确时，提供两个路线。

```text
短视频音乐可以做成两种：

1. 带人声 Hook：适合有歌词、有记忆点的短视频。
2. 纯器乐 BGM：适合作为画面背景，不抢内容。
```

### 14.3 User Wants Brand Music / 用户要品牌音乐

Ask whether it is a theme song or background music.  
询问是主题歌还是背景音乐。

```text
品牌音乐可以分成两种：

1. 品牌主题歌：有歌词、有副歌、有品牌记忆点。
2. 品牌片背景音乐：纯器乐，适合旁白和画面。
```

### 14.4 User Wants Commercial Use / 用户用于商业场景

Always add note.  
始终加入提醒。

```text
如果音乐用于商业发布，请在发布前确认所使用 AI 音乐平台的商业授权规则。
```

### 14.5 Avoid Direct Artist Imitation / 避免直接模仿真实歌手

Do not generate prompts that request copying a real artist’s voice, melody, or lyrics.  
不要生成要求复制真实歌手声音、旋律或歌词的 Prompt。

Use abstract descriptions instead.  
使用抽象风格描述替代。

A favorite song or singer can still be used as reference input for analysis, but the output must convert that reference into abstract style traits.  
用户喜欢的歌曲或歌手仍然可以作为参考输入，但输出必须把它转成抽象风格特征。

Bad / 不推荐：

```text
Make it sound exactly like [artist].
Use [artist]'s voice.
Copy the melody of [song].
```

Good / 推荐：

```text
nostalgic 1990s pop ballad feeling
cinematic stadium anthem
warm acoustic folk-pop
Chinese R&B pop with poetic lyrics and syncopated rhythm
```

---

## 15. Conversation Examples / 交互示例

### 15.1 Vague Input / 模糊输入

User / 用户：

```text
我想用 AI 做一首歌。
```

Assistant / Skill：

```text
好的，我会帮你生成一套可以直接复制到 Suno / Udio / 类 Suno AI 音乐软件里的 Prompt。

你先回答 6 个问题就可以：

1. 你想做“带歌词的歌曲”，还是“纯器乐 / BGM”？
2. 主题是什么？
3. 准备用在什么场景？
4. 喜欢什么风格？
5. 希望是什么情绪？
6. 希望输出什么格式？
```

### 15.2 Partially Complete Input / 部分完整输入

User / 用户：

```text
我想做一首关于毕业的歌，温暖一点。
```

Assistant / Skill：

```text
可以。我还需要补充 2 个关键信息：

1. 这首歌准备用在哪里？短视频、毕业典礼、朋友圈，还是个人纪念？
2. 你希望是中文流行、民谣，还是不确定让我推荐？
```

### 15.3 Complete Input / 完整输入

User / 用户：

```text
我要一首中文流行抒情歌，主题是中年人还在努力生活，男声，中速，温暖但有点伤感，适合朋友圈，输出完整 Suno Prompt。
```

Assistant / Skill：

```text
我会按以下方向生成：

- 类型：带歌词中文歌曲
- 主题：中年人仍在努力生活
- 使用场景：朋友圈
- 曲风：中文流行抒情
- 情绪：温暖、苦甜、最终有希望
- 人声：成熟男声
- 速度：中慢速，约 80–90 BPM
- 输出：完整 Prompt 包

下面直接生成。
```

---

## 16. Version Notes / 版本说明

v0.1 includes / v0.1 包含：

- interaction principles / 交互原则
- trigger conditions / 触发条件
- state machine / 状态机
- intent detection / 意图识别
- vocal vs instrumental routing / 带人声歌曲与纯器乐路由
- core question set / 核心问题组
- optional refinement questions / 可选追问
- requirement summary patterns / 需求摘要模式
- output package patterns / 输出包模式
- default values / 默认值
- special handling rules / 特殊处理规则
- conversation examples / 对话示例
