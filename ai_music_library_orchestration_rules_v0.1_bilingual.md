# AI Music Library Orchestration Rules v0.1 Bilingual  
# AI 音乐素材库调用规则 v0.1 双语版

> Purpose / 用途：  
> This document defines how an interactive AI music prompt skill should use the previously designed libraries to generate final AI music prompts.  
> 本文档用于定义交互式 AI 音乐 Prompt Skill 如何调用此前设计的多个素材库，并组装成最终 Prompt。
>
> It describes the order of library calls, input-output relationships, routing logic, fallback rules, and final prompt assembly process.  
> 它描述素材库调用顺序、输入输出关系、路由逻辑、默认补全规则和最终 Prompt 组装流程。

---

## 1. Library Set / 素材库集合

The skill should use the following libraries.  
Skill 应使用以下素材库：

```text
1. ai_music_genre_library_v0.2.md
   曲风库

2. ai_music_rhythm_bpm_scene_mapping_v0.1.md
   节奏 / BPM / 场景映射库

3. ai_music_vocal_voice_library_v0.1.md
   人声与嗓音描述库

4. ai_music_instrumentation_arrangement_library_v0.1.md
   乐器与编曲素材库

5. ai_music_emotion_expression_mapping_v0.1.md
   情绪与音乐表达映射库

6. ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md
   使用场景、结构与编曲映射库

7. ai_music_prompt_templates_v0.1_bilingual.md
   Style Prompt / Lyrics Box / Iteration Prompt 模板库
```

---

## 2. Core Orchestration Principle / 核心调用原则

The skill should not directly convert raw user text into a final prompt.  
Skill 不应直接把用户原话转换成最终 Prompt。

It should first create an internal structured music brief, then assemble final outputs.  
它应先生成一个内部结构化音乐需求对象，再组装最终输出。

Recommended flow / 推荐流程：

```text
User Input
  ↓
Interaction Workflow
  ↓
Internal Music Brief
  ↓
Library Selection
  ↓
Library Outputs
  ↓
Prompt Template Assembly
  ↓
Final Prompt Package
```

中文：

```text
用户输入
  ↓
交互流程
  ↓
内部音乐需求对象
  ↓
素材库选择
  ↓
素材库输出
  ↓
Prompt 模板组装
  ↓
最终 Prompt 包
```

---

## 3. Recommended Library Call Order / 推荐素材库调用顺序

Use this order by default.  
默认按以下顺序调用。

```text
1. Use Case Structure & Arrangement Library
2. Genre Library
3. Emotion Expression Mapping Library
4. Rhythm / BPM / Scene Mapping Library
5. Vocal & Voice Library
6. Instrumentation & Arrangement Library
7. Prompt Template Library
```

中文：

```text
1. 使用场景、结构与编曲映射库
2. 曲风库
3. 情绪与音乐表达映射库
4. 节奏 / BPM / 场景映射库
5. 人声与嗓音描述库
6. 乐器与编曲素材库
7. Style Prompt / Lyrics Box / Iteration Prompt 模板库
```

Why this order / 为什么这个顺序：

```text
Use case decides structure and purpose.
使用场景决定结构和用途。

Genre decides sonic identity.
曲风决定声音身份。

Emotion decides mood, density, and energy curve.
情绪决定氛围、密度和能量曲线。

BPM decides rhythm and tempo.
BPM 决定节奏与速度。

Vocal library applies only to vocal songs.
人声库只用于带人声歌曲。

Instrumentation library converts decisions into sound materials.
乐器库把前面决策转为具体声音材料。

Prompt template library assembles final copy-ready prompts.
模板库负责组装最终可复制 Prompt。
```

---

## 4. Internal Music Brief Schema / 内部音乐需求对象结构

The skill should maintain an internal `music_brief` object.  
Skill 应维护一个内部 `music_brief` 对象。

### 4.1 Vocal Song Brief / 带人声歌曲对象

```json
{
  "track_type": "vocal_song",
  "theme": "",
  "use_case": "",
  "language": "Chinese",
  "genre": "",
  "subgenre": "",
  "mood": [],
  "tempo": {
    "description": "",
    "bpm": ""
  },
  "vocal": {
    "style": "",
    "delivery": "",
    "backing_vocals": ""
  },
  "instrumentation": [],
  "structure": [],
  "arrangement_plan": {},
  "energy_curve": "",
  "lyrics_strategy": "",
  "hook_strategy": "",
  "avoid": [],
  "output_format": "complete_prompt_package"
}
```

### 4.2 Instrumental Brief / 纯器乐对象

```json
{
  "track_type": "instrumental_bgm",
  "theme": "",
  "use_case": "",
  "genre": "",
  "subgenre": "",
  "mood": [],
  "tempo": {
    "description": "",
    "bpm": ""
  },
  "instrumentation": [],
  "structure": [],
  "arrangement_plan": {},
  "energy_curve": "",
  "loopability": "",
  "voiceover_space": "",
  "avoid": [
    "instrumental only",
    "no vocals",
    "no rap",
    "no spoken words"
  ],
  "output_format": "instrumental_prompt_package"
}
```

---

## 5. Library I/O Contracts / 素材库输入输出契约

Each library should receive specific inputs and return specific outputs.  
每个素材库应接收明确输入，并返回明确输出。

---

### 5.1 Use Case Structure & Arrangement Library / 使用场景、结构与编曲库

Input / 输入：

```text
track_type
use_case
output_format
duration_preference
hook_need
loopability
voiceover_need
```

Output / 输出：

```text
recommended_structure
hook_placement
recommended_length
lyrics_density
arrangement_plan
energy_curve
negative_structure_rules
```

Example / 示例：

Input:

```json
{
  "track_type": "vocal_song",
  "use_case": "sports_world_cup_anthem"
}
```

Output:

```text
Structure:
[Intro - Stadium Chant]
[Verse - Percussion Groove]
[Pre-Chorus - Rising Crowd]
[Chorus - Group Vocal]
[Post-Chorus - Chant Hook]
[Bridge - Clap Breakdown]
[Final Chorus - Crowd Chant]
[Outro - Final Chant]

Hook Placement:
chant or rhythm motif within first 10 seconds

Arrangement:
big drums, brass, electric guitar, percussion, choir
```

---

### 5.2 Genre Library / 曲风库

Input / 输入：

```text
user_genre_preference
use_case
track_type
mood
era_preference
instrumental_or_vocal
```

Output / 输出：

```text
genre
subgenre
genre_keywords
genre_default_bpm
genre_default_instruments
genre_default_vocal
genre_avoid
alternative_genre_options
```

Example / 示例：

Input:

```json
{
  "use_case": "World Cup anthem",
  "mood": ["energetic", "triumphant"],
  "user_genre_preference": "not sure"
}
```

Output:

```text
Recommended genres:
1. stadium anthem
2. arena rock
3. Latin pop
4. cinematic pop
5. dance-pop
```

---

### 5.3 Emotion Expression Mapping Library / 情绪与音乐表达映射库

Input / 输入：

```text
mood_words
theme
use_case
track_type
```

Output / 输出：

```text
emotion_keywords
primary_emotion
secondary_emotion
energy_curve
arrangement_density
vocal_delivery
instrument_suggestions
avoid
```

Example / 示例：

Input:

```text
温暖但有点伤感
```

Output:

```text
Primary: warm
Secondary: bittersweet, reflective, hopeful
Energy Curve: quiet reflection to hopeful release
Prompt Keywords: warm, bittersweet, reflective, hopeful chorus
```

Important / 重要：

```text
Do not simply write “warm and sad”.
不要简单写成 “warm and sad”。

Translate it into:
bittersweet, warm sadness, reflective, hopeful chorus
应转译成：苦甜感、温暖伤感、反思、希望感副歌。
```

---

### 5.4 Rhythm / BPM / Scene Mapping Library / 节奏 BPM 场景映射库

Input / 输入：

```text
genre
mood
use_case
energy_level
track_type
```

Output / 输出：

```text
tempo_description
bpm_range
groove_description
rhythm_density
tempo_avoid
```

Example / 示例：

Input:

```json
{
  "genre": "Chinese pop ballad",
  "mood": ["warm", "bittersweet"],
  "use_case": "personal sharing"
}
```

Output:

```text
medium-slow tempo
80–90 BPM
gentle groove
light rhythm density
```

---

### 5.5 Vocal & Voice Library / 人声与嗓音描述库

Only call this if `track_type = vocal_song`.  
仅当 `track_type = vocal_song` 时调用。

Input / 输入：

```text
gender_preference
mood
genre
use_case
age_feeling
energy_level
```

Output / 输出：

```text
vocal_style
vocal_delivery
vocal_texture
backing_vocal_strategy
avoid_vocal
```

Example / 示例：

Input:

```json
{
  "mood": ["warm", "bittersweet"],
  "theme": "middle-aged life",
  "genre": "Chinese pop ballad"
}
```

Output:

```text
mature emotional male vocal
natural and restrained delivery
close intimate vocal tone
optional subtle backing vocals in final chorus
```

For instrumental / 纯器乐：

```text
Skip this library.
跳过本库。

Add:
instrumental only, no vocals, no rap, no spoken words
加入：纯器乐，无人声，无说唱，无旁白。
```

---

### 5.6 Instrumentation & Arrangement Library / 乐器与编曲素材库

Input / 输入：

```text
genre
mood
use_case
track_type
structure
energy_curve
vocal_or_instrumental
```

Output / 输出：

```text
instrumentation
section_arrangement_details
production_texture
transition_strategy
instrument_avoid
```

Example / 示例：

Input:

```json
{
  "genre": "Chinese pop ballad",
  "mood": ["warm", "bittersweet"],
  "structure": "personal_story_song"
}
```

Output:

```text
Instrumentation:
soft piano, acoustic guitar, warm bass, light drums, cinematic strings

Section Arrangement:
Intro: soft piano motif
Verse: sparse piano and acoustic guitar
Pre-Chorus: add light drums and subtle strings
Chorus: full drums, bass, strings
Bridge: piano and vocal only
Final Chorus: wider strings and backing vocals
Outro: return to piano motif
```

---

### 5.7 Prompt Template Library / Prompt 模板库

This is always the final library called.  
该库始终最后调用。

Input / 输入：

```text
music_brief
output_format
track_type
style_prompt_fields
lyrics_box_fields
iteration_prompt_fields
avoid
usage_notes
```

Output / 输出：

```text
Style Prompt
Lyrics Box / Custom Box
Iteration Prompts
Usage Notes
Final Output Package
```

---

## 6. Track-Type-Specific Call Chains / 不同类型的调用链

### 6.1 Vocal Song Call Chain / 带人声歌曲调用链

```text
User Input
  ↓
Use Case Structure Library
  ↓
Genre Library
  ↓
Emotion Library
  ↓
BPM Library
  ↓
Vocal Library
  ↓
Instrumentation Library
  ↓
Prompt Template Library
  ↓
Final Vocal Song Prompt Package
```

中文：

```text
用户输入
  ↓
使用场景结构库
  ↓
曲风库
  ↓
情绪库
  ↓
BPM 库
  ↓
人声库
  ↓
乐器编曲库
  ↓
Prompt 模板库
  ↓
最终带人声歌曲 Prompt 包
```

### 6.2 Instrumental BGM Call Chain / 纯器乐 BGM 调用链

```text
User Input
  ↓
Use Case Structure Library
  ↓
Genre Library
  ↓
Emotion Library
  ↓
BPM Library
  ↓
Skip Vocal Library
  ↓
Instrumentation Library
  ↓
Prompt Template Library
  ↓
Final Instrumental Prompt Package
```

中文：

```text
用户输入
  ↓
使用场景结构库
  ↓
曲风库
  ↓
情绪库
  ↓
BPM 库
  ↓
跳过人声库
  ↓
乐器编曲库
  ↓
Prompt 模板库
  ↓
最终纯器乐 Prompt 包
```

Fixed instrumental phrase / 纯器乐固定短语：

```text
instrumental only, no vocals, no rap, no spoken words
纯器乐，无人声，无说唱，无旁白
```

---

## 7. Missing Information Handling / 缺失信息处理

### 7.1 Missing Genre / 缺失曲风

If genre is missing, infer from use case and mood.  
如果曲风缺失，根据使用场景和情绪推断。

Example / 示例：

```text
Use case: personal story
Mood: warm, bittersweet
→ Genre: Chinese pop ballad / folk-pop
```

If uncertain, provide 3 options.  
如果不确定，提供 3 个选项。

### 7.2 Missing Mood / 缺失情绪

Infer from theme and use case.  
根据主题和场景推断。

Example / 示例：

```text
Theme: graduation
→ Mood: nostalgic, warm, hopeful

Theme: sports
→ Mood: energetic, triumphant, powerful
```

### 7.3 Missing BPM / 缺失 BPM

Infer from genre + mood + use case.  
根据曲风、情绪、场景推断。

Example / 示例：

```text
Chinese pop ballad + warm + personal sharing
→ 80–90 BPM

short video + bright + electro-pop
→ 115–128 BPM
```

### 7.4 Missing Vocal / 缺失人声

Default / 默认：

```text
natural emotional vocal
自然情绪人声
```

But infer better when possible / 但应尽量更精确：

```text
middle-aged personal story → mature emotional male vocal
中年个人故事 → 成熟情绪男声

healing song → soft female vocal or gentle clear vocal
治愈歌曲 → 柔和女声或清澈温柔人声

sports anthem → powerful lead vocal + group vocals
体育主题歌 → 强力主唱 + 群体人声
```

### 7.5 Missing Use Case / 缺失使用场景

Ask one question.  
只追问一个问题。

```text
这首歌准备用在哪里？比如短视频、朋友圈、品牌片、活动开场、学习 BGM、婚礼、体育赛事。
Where will this music be used?
```

---

## 8. Conflict Resolution Rules / 冲突处理规则

### 8.1 Warm + Sad / 温暖 + 伤感

Use / 使用：

```text
bittersweet, warm sadness, reflective, hopeful chorus
苦甜感，温暖伤感，反思，希望感副歌
```

### 8.2 Tech + Warm / 科技感 + 温暖

Use / 使用：

```text
warm futuristic, human-centered tech, soft synths with organic piano
温暖未来感，人本科技，柔和合成器 + 有机钢琴
```

### 8.3 Premium + Playful / 高级感 + 俏皮

Use / 使用：

```text
stylish playful, light luxury, elegant upbeat groove
时尚俏皮，轻奢感，优雅明快律动
```

### 8.4 Calm + Short Video / 平静 + 短视频

Use / 使用：

```text
gentle but catchy hook, soft loop-friendly motif
温柔但抓耳的 Hook，柔和可循环动机
```

Avoid long slow intros.  
避免长慢前奏。

### 8.5 Brand Film + Strong Lead Melody / 品牌片 + 强主旋律

If voiceover is needed, reduce lead melody density.  
如果需要旁白，降低主旋律密度。

Use / 使用：

```text
leave room for voiceover, non-intrusive motif, clean midrange
为旁白留空间，不打扰的动机，干净中频
```

---

## 9. Prompt Assembly Rules / Prompt 组装规则

### 9.1 Style Prompt Assembly / Style Prompt 组装

Style Prompt must include / Style Prompt 必须包含：

```text
genre
mood
tempo / BPM
vocal or instrumental-only
instrumentation
arrangement
energy curve
use case
avoid
```

For vocal song / 带人声歌曲：

```text
Create a [language] [genre] song with a [mood] mood. Use [vocal style] vocals. The tempo should be [BPM]. The arrangement should include [instruments]. Start with [intro arrangement], then build into [chorus arrangement]. The emotional curve should move from [starting emotion] to [ending emotion]. The chorus should be [chorus direction]. The song is intended for [use case]. Avoid [avoid items].
```

For instrumental / 纯器乐：

```text
Create a [genre] instrumental track with a [mood] mood. Instrumental only, no vocals, no rap, no spoken words. The tempo should be [BPM]. Use [instruments] with [production texture]. The arrangement should move from [starting energy] to [ending energy]. Make it [loop-friendly / voiceover-friendly / edit-friendly]. The track is intended for [use case]. Avoid [avoid items].
```

---

### 9.2 Lyrics Box Assembly / Lyrics Box 组装

For vocal songs / 带人声歌曲：

```text
[Style: {genre}, {mood}, {tempo}]
[Vocal: {vocal style}]
[Arrangement: {instrumentation and arrangement plan}]
[Energy: {energy curve}]
[Use Case: {use case}]

[Intro - {intro arrangement}]
{lyrics}

[Verse 1 - {verse arrangement}]
{lyrics}

[Pre-Chorus - {build arrangement}]
{lyrics}

[Chorus - {chorus arrangement and hook instruction}]
{lyrics}

[Bridge - {bridge arrangement}]
{lyrics}

[Final Chorus - {final chorus arrangement}]
{lyrics}

[Outro - {outro arrangement}]
{lyrics}
```

For instrumental / 纯器乐：

```text
[Instrumental Only]
[No vocals, no rap, no spoken words]
[Style: {instrumental genre}, {mood}, {tempo}]
[Instrumentation: {instruments}]
[Use Case: {use case}]
[Energy: {energy curve}]
[Loopability: {loop-friendly / edit-friendly / voiceover-friendly}]

[Intro - {intro texture}]
[Main Theme - {main motif}]
[Variation - {subtle variation}]
[Breakdown - {reduced arrangement}]
[Final Section - {climax or return}]
[Outro / Loop Ending - {ending behavior}]
```

---

### 9.3 Iteration Prompt Assembly / 迭代 Prompt 组装

Always provide 3–5.  
始终提供 3–5 条。

Choose from categories / 从以下类别中选择：

```text
style iteration / 曲风调整
vocal iteration / 人声调整
lyrics iteration / 歌词调整
chorus / hook iteration / 副歌 Hook 调整
arrangement iteration / 编曲调整
tempo iteration / 节奏调整
emotion iteration / 情绪调整
structure iteration / 结构调整
instrumental iteration / 纯器乐调整
use-case iteration / 场景适配调整
```

For vocal songs, prioritize / 带人声歌曲优先：

```text
chorus hook
vocal naturalness
lyrics singability
arrangement build
emotion
```

For instrumental, prioritize / 纯器乐优先：

```text
loopability
no vocals
background usability
instrumentation
edit / voiceover friendliness
```

---

## 10. Output Format Routing / 输出格式路由

| Output Choice / 输出选择 | Template / 使用模板 |
|---|---|
| A. Simple Prompt / 简洁版 | Style Prompt + Lyrics / Custom Box |
| B. Complete Prompt Package / 完整 Prompt 包 | Requirement Summary + Music Direction + Titles + Style Prompt + Lyrics Box + Iteration Prompts + Usage Notes |
| C. Lyrics + Style Prompt / 歌词 + Style Prompt | Lyrics + Style Prompt |
| D. Multi-Style Versions / 多风格版本 | 3 versions: mainstream, short-video, cinematic |
| E. 30-Second Hook / 30 秒 Hook | Hook Concept + Short Style Prompt + Short Lyrics Box + Hook Iteration Prompts |

---

## 11. Example Orchestration: Vocal Song / 示例：带人声歌曲

User input / 用户输入：

```text
我想做一首关于 30 岁以后还在努力生活的歌，适合朋友圈，温暖一点。
```

### 11.1 Internal Brief / 内部对象

```json
{
  "track_type": "vocal_song",
  "theme": "30 岁以后还在努力生活",
  "use_case": "personal_story_song",
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
  "energy_curve": "quiet reflection to hopeful release"
}
```

### 11.2 Library Calls / 调用库

```text
Use Case Library → personal_story_song
Genre Library → Chinese pop ballad
Emotion Library → warm + bittersweet + hopeful
BPM Library → 80–90 BPM
Vocal Library → mature emotional male vocal
Instrumentation Library → piano + acoustic guitar + strings
Prompt Template Library → complete prompt package
```

---

## 12. Example Orchestration: Instrumental BGM / 示例：纯器乐 BGM

User input / 用户输入：

```text
我想做一段科技产品宣传片背景音乐，高级一点，不要人声。
```

### 12.1 Internal Brief / 内部对象

```json
{
  "track_type": "instrumental_bgm",
  "use_case": "tech_product_background_music",
  "genre": "minimal electronic",
  "mood": ["premium", "futuristic", "clean", "optimistic"],
  "tempo": {
    "description": "medium tempo",
    "bpm": "95–115 BPM"
  },
  "instrumentation": [
    "pulsing synths",
    "minimal electronic drums",
    "soft sub bass",
    "digital pads"
  ],
  "structure": [
    "[Intro - clean digital texture and soft synth pulse]",
    "[Pulse Groove - minimal beat and sub bass]",
    "[Build - add arpeggio and brighter synth layers]",
    "[Main Theme - memorable but non-distracting synth motif]",
    "[Outro - clean resolved logo-friendly ending]"
  ],
  "avoid": [
    "vocals",
    "rap",
    "spoken words",
    "club drop",
    "aggressive bass"
  ]
}
```

### 12.2 Library Calls / 调用库

```text
Use Case Library → tech_product_background_music
Genre Library → minimal electronic / corporate electronic
Emotion Library → premium + futuristic + clean
BPM Library → 95–115 BPM
Vocal Library → skipped
Instrumentation Library → pulsing synths + digital pads
Prompt Template Library → instrumental style prompt + custom box
```

---

## 13. Quality Checklist Before Output / 输出前质量检查

Before final output, check:  
最终输出前检查：

```text
1. Is track_type clear?
   类型是否清楚？

2. Is use_case reflected in structure?
   使用场景是否体现在结构里？

3. Is genre specific enough?
   曲风是否足够具体？

4. Is mood translated into musical behavior?
   情绪是否转化成音乐行为？

5. Is BPM appropriate for use case?
   BPM 是否适合场景？

6. Is vocal skipped for instrumental?
   纯器乐是否跳过人声？

7. Does Lyrics Box include section tags and arrangement cues?
   Lyrics Box 是否包含段落标签和编曲提示？

8. Does Style Prompt avoid copying real artists?
   Style Prompt 是否避免直接模仿真实歌手？

9. Are iteration prompts copy-ready?
   迭代 Prompt 是否可直接复制？

10. Are commercial usage notes included when needed?
    商业场景是否加入使用提醒？
```

---

## 14. Progressive Disclosure Guidance / 渐进式加载建议

The main `SKILL.md` should not include all library content.  
主 `SKILL.md` 不应包含所有库内容。

It should include:  
它只应包含：

```text
interaction rules
routing logic
required libraries
when to load each library
final output format
safety rules
```

Detailed materials should live in `libraries/`.  
详细素材应放在 `libraries/` 目录中。

Recommended structure / 推荐结构：

```text
interactive-ai-music-prompt-skill/
├── SKILL.md
├── README.md
├── libraries/
│   ├── ai_music_genre_library_v0.2.md
│   ├── ai_music_rhythm_bpm_scene_mapping_v0.1.md
│   ├── ai_music_vocal_voice_library_v0.1.md
│   ├── ai_music_instrumentation_arrangement_library_v0.1.md
│   ├── ai_music_emotion_expression_mapping_v0.1.md
│   ├── ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md
│   ├── ai_music_prompt_templates_v0.1_bilingual.md
│   ├── ai_music_customer_interaction_workflow_v0.1_bilingual.md
│   └── ai_music_library_orchestration_rules_v0.1_bilingual.md
├── examples/
└── checklists/
```

---

## 15. Version Notes / 版本说明

v0.1 includes / v0.1 包含：

- library set definition / 素材库集合定义
- recommended call order / 推荐调用顺序
- internal music brief schema / 内部需求对象结构
- library I/O contracts / 素材库输入输出契约
- track-type-specific call chains / 不同类型调用链
- missing information rules / 缺失信息处理规则
- conflict resolution rules / 冲突处理规则
- prompt assembly rules / Prompt 组装规则
- output format routing / 输出格式路由
- orchestration examples / 调用示例
- output quality checklist / 输出质量检查清单
- progressive disclosure guidance / 渐进式加载建议
