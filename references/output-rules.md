# Output Rules
# 输出规则

## Core rule / 核心规则

Do not stop at paraphrasing the user request.
不要停留在复述用户需求。

Convert the request into an executable prompt package.
要把需求转成可执行的 Prompt 包。

Default to the complete prompt package unless the user explicitly asks for another output form.
除非用户明确要求其他输出形式，否则默认直接输出完整 Prompt 包。

## User-facing wrapper language / 面向用户的包装层语言

All non-prompt user-facing wrapper content should default to Chinese.
所有非 prompt 的面向用户包装层内容默认都应使用中文。

This includes:
这包括：

- section headings shown to the user / 给用户看的章节标题
- summaries shown outside prompt payload blocks / prompt 载荷块之外的摘要
- explanation notes shown outside prompt payload blocks / prompt 载荷块之外的说明
- recommendation notes shown outside prompt payload blocks / prompt 载荷块之外的推荐说明

Only the actual prompt payload blocks should default to English.
只有真正作为 prompt 载荷的内容块，才默认使用英文。

Typical prompt payload blocks include:
典型 prompt 载荷块包括：

- `Style Prompt`
- `Structure & Arrangement Notes`
- `Iteration Prompts`
- `Usage Notes`

## Title recommendations / 歌名推荐

For lyric-based songs, title recommendations are mandatory.
对于带歌词歌曲，推荐歌名是必需项。

Use title suggestions as a creative steering tool, not as decoration.
要把歌名建议当成创作 steering tool，而不是装饰品。

Default recommendation count:
默认推荐数量：

- usually 3–5 title options / 通常给 3–5 个歌名选项

Title options should sound like actual song titles.
歌名候选应当像真正的歌曲名。

Prefer:
优先：

- short or medium-length titles / 短到中等长度
- titles with clear emotional or image anchor / 有明确情绪或画面锚点
- titles that feel natural in playlists and player UI / 放进歌单或播放器界面里很自然

Avoid:
避免：

- slogan-like full sentences / 口号式完整句子
- social caption style phrasing / 社交媒体标题腔
- lines that feel like raw lyric excerpts rather than titles / 更像歌词摘句而不像歌名的表达
- brand-copy or ad-copy feeling / 广告文案感

If a candidate sounds more like a line of lyrics than a title, shorten, compress, or re-anchor it before presenting it.
如果某个候选更像一句歌词而不是歌名，应先压缩、重写或重新锚定后再给用户。

## Lyrics separation rule / 歌词分离规则

For lyric-based songs, keep these as separate blocks:
对于带歌词歌曲，以下模块必须分开：

- `Style Prompt`
- `Structure & Arrangement Notes`
- `Lyrics`

Do not merge lyrics into structure notes.
不要把歌词和结构说明混成一个框。

## Lyrics language boundary / 歌词模块语言边界

Inside the `Lyrics` block, allow the lyric body itself to follow the user-requested language.
在 `Lyrics` 模块内部，歌词正文可以跟随用户要求的语言。

However, all non-lyric control content inside the same block must remain English-only.
但是，同一模块中的所有非歌词控制内容都必须保持全英文。

This includes:
这包括：

- section labels / 段落标签
- role labels / 角色标签
- arrangement cues / 编曲提示
- vocal delivery notes / 演唱说明
- transition notes / 过渡说明

Good example:
推荐示例：

```text
[Verse 1]
[acoustic guitar, close vocal]
风吹过操场的傍晚
我们还站在光里面
```

Bad example:
不推荐示例：

```text
[主歌 1]
[木吉他, 贴近人声]
风吹过操场的傍晚
我们还站在光里面
```

If the lyrics are bilingual, multilingual, or non-English, this rule still holds.
即使歌词本身是双语、多语或非英文，这条规则仍然成立。

## Arrangement line format inside `Lyrics` / `Lyrics` 内的编曲行格式

For vocal songs, prefer splitting the section tag and the arrangement cue into two separate bracketed lines.
对于带歌词歌曲，默认优先把段落标签与编曲提示拆成两行独立方括号内容。

Preferred format:
推荐格式：

```text
[Verse 1]
[Soft piano carries the harmony while muted guitar adds a gentle pulse, with very light percussion under a close vocal]
```

This is usually better than compressing everything into one tag.
这通常比把所有内容压进一个标签里更清楚。

Avoid this as the default style:
默认不要优先使用这种写法：

```text
[Verse 1 - soft piano, muted guitar pulse, close vocal, very light percussion]
```

Use the combined one-line format only when the output must stay extremely compact.
只有在必须极度压缩输出时，才使用合并成一行的格式。

Both lines must remain English-only unless the user explicitly asks for Chinese prompt payload.
除非用户明确要求中文 prompt 载荷，否则这两行都必须保持全英文。

## Richer arrangement cues inside `Lyrics` / `Lyrics` 内的更丰富编曲提示

For vocal songs, the arrangement cues inside section tags should usually be more informative than a single instrument label.
对于带歌词歌曲，段落后的编曲提示通常应比“单一乐器标签”更丰富。

The arrangement cue should usually read like a natural short English sentence or sentence fragment, not like a pile of disconnected keywords.
编曲提示通常应写成自然的、短的英文句子或句式片段，而不是一堆割裂关键词的堆砌。

Weak example:
较弱示例：

```text
[Verse 1]
[piano]
```

Better example:
更好示例：

```text
[Verse 1]
[Soft piano carries the harmony while muted guitar adds a gentle pulse, with very light percussion under a close vocal]
```

Preferred sentence feel:
推荐句感：

- sounds like an actual arrangement instruction / 听起来像真实编曲指令
- has internal flow and coherence / 内部有连贯性
- can mention movement or change, not just static ingredients / 可以描述推进和变化，而不只是静态元素

Good examples:
推荐示例：

```text
[Acoustic guitar gets groovier, and soft syncopated drums start to enter]
[The bassline kicks in and builds a smoother groove, with light vocal ad-libs around the phrasing]
[The music drops down to a light, bouncy acoustic rhythm with a casual head-nodding beat]
```

Less preferred examples:
不推荐示例：

```text
[acoustic guitar, syncopated drums, groove]
[bassline, vocal ad-libs, smoother groove]
[light acoustic rhythm, bouncy beat]
```

Preferred arrangement-cue density:
推荐的编曲提示密度：

- 2-4 concrete arrangement cues per major section / 主要段落尽量给 2-4 个具体编曲信息
- enough information to guide texture and movement / 信息量足以指导质感和推进
- not so much that the tag becomes bloated or unreadable / 但不要膨胀到难读

Good cue dimensions include:
推荐包含的维度：

- instrumentation layers / 乐器层次
- rhythm behavior / 节奏状态
- vocal placement / 人声位置或唱法
- energy movement / 能量变化
- harmony or pad support / 和声或铺底支持
- width or density change / 声场或密度变化

Examples:
示例：

```text
[Verse 1]
[Soft piano carries the harmony while muted guitar adds a gentle pulse, with very light percussion under a close vocal]
[Pre-Chorus]
[The bassline enters softly as the drums lift a little, and the harmony begins to rise around tighter phrasing]
[Chorus]
[Full drums open up with warm bass and broader guitar support, while backing vocals widen the hook]
[Bridge]
[The drums pull back, piano moves to the front, and suspended chords create a more intimate space]
[Final Chorus]
[Bigger drums and brighter strings push the section higher, with wider choir support for the strongest lift]
```

Do not turn every section tag into a full paragraph.
不要把每个段落标签写成整段说明。

Aim for compact richness rather than verbosity.
目标是“紧凑但更丰富”，而不是冗长。

## Lyrics structure consistency / 歌词结构一致性

The lyric structure should follow the chosen song structure rather than being mechanically fixed in advance.
歌词结构应跟随所选歌曲结构生成，而不是机械预设死一套。

However, once a structure is chosen, the `Lyrics` block must stay consistent with the structure declared in `Structure & Arrangement Notes`.
但是一旦结构被选定，`Lyrics` 模块必须与 `Structure & Arrangement Notes` 中声明的结构保持一致。

Do not casually drift into a different structure midway through output.
不要在输出过程中随意漂移到另一套结构。

If section labels are used inside the lyrics block, keep them aligned with the declared structure.
如果在歌词模块内部使用段落标签，就必须与已声明结构对齐。

## `create_vocal_song` output blocks / 带歌词歌曲输出模块

Typical complete-package output:
典型完整包输出：

1. Requirement Summary / 需求摘要
2. Music Direction / 音乐方向
3. Recommended Title Options / 推荐歌名
4. Style Prompt / 风格 Prompt
5. Lyrics / 歌词
6. Iteration Prompts / 迭代 Prompt
7. Usage Notes / 使用说明

## User-facing delivery style / 面向用户的交付样式

Use the libraries and templates to generate the result, but present the normal final package in a cleaner delivery format.
应使用知识库与模板来生成结果，但默认最终交付版应采用更干净的展示格式。

Recommended delivery style:
推荐交付样式：

- `Style Prompt`: optional short Chinese note, then a Chinese counterpart version of the prompt content, then one structured English copy-ready prompt block / 可选简短中文提示 + prompt 内容中文对照版 + 结构化、纯英文、可直接复制的 prompt 块
- `Style Prompt` should usually use readable field-style lines such as `Genre: ...`, `Mood: ...`, `Texture: ...` instead of one long sentence; this applies to both songs and instrumental music / `Style Prompt` 通常应使用 `Genre: ...`、`Mood: ...`、`Texture: ...` 这类可读字段行，而不是一整段长句；歌曲和纯器乐都一样
- `Style Prompt` should not use square-bracket tags / `Style Prompt` 不要使用方括号标签
- `Lyrics`: a separate readable lyrics block / 单独、可读的歌词块
- `Instrumental Structure Box`: optional short Chinese note, then Chinese counterpart, then English prompt block / `Instrumental Structure Box`：可选简短中文提示 + 中文对照版 + 英文 prompt 块
- `Iteration Prompts` and `Usage Notes`: default to Chinese user-facing output; English is optional only when explicitly requested / `Iteration Prompts` 和 `Usage Notes`：默认中文面向用户输出；只有在明确要求时才额外给英文

Do not dump the full raw library template into the final user-facing lyrics block unless the user explicitly asks for template mode.
除非用户明确要求模板模式，否则不要把底层完整库模板原样塞进最终用户歌词块。

Keep Chinese explanation outside the English prompt block.
中文解释放在英文 prompt 块外部。

The Chinese counterpart should mirror the English prompt content itself.
中文对照版应当对应英文 prompt 内容本身。

Do not treat "Chinese explanation" as a substitute for the Chinese counterpart.
不要把“中文说明”当成“中文对照版”的替代品。

For `Iteration Prompts` and `Usage Notes`, prioritize direct Chinese guidance over English mirroring in the normal workflow.
对于 `Iteration Prompts` 和 `Usage Notes`，在默认工作流中，应优先提供直接中文指导，而不是英文镜像。

For `Genre`, do not output `Sub-style` as a separate field by default.
对于 `Genre`，默认不要把 `Sub-style` 单独拆成一行。

Prefer one `Genre` line that contains the broad style and the relevant sub-style(s), separated clearly by commas.
优先使用一行 `Genre`，把泛风格和相关子风格一起写进去，并用逗号清晰分隔。

Example:
例如：

```text
Genre: Chinese folk, urban narrative folk
Genre: rock, anthemic pop rock
```

This is better than either:
这比以下两种都更好：

1. splitting `Sub-style` into a separate field when it is unnecessary / 在不必要时拆出单独 `Sub-style`
2. fusing everything into one blurred label / 把所有东西揉成一个模糊标签

For the normal default delivery format, `Structure & Arrangement Notes` may be omitted as a separate block because its information can already be covered by `Style Prompt` plus `Lyrics` or `Instrumental Structure Box`.
对于默认交付格式，`Structure & Arrangement Notes` 可以省略独立输出，因为它的信息已经可由 `Style Prompt` 加 `Lyrics` 或 `Instrumental Structure Box` 覆盖。

## `create_instrumental_bgm` output blocks / 器乐输出模块

Typical output:
典型输出：

1. Requirement Summary / 需求摘要
2. Music Direction / 音乐方向
3. Style Prompt / 风格 Prompt
4. Instrumental Lyrics Box / Instrumental Structure Box / 器乐 Lyrics Box / 器乐结构框
5. Iteration Prompts / 迭代 Prompt
6. Usage Notes / 使用说明

For instrumental music, `Style Prompt` alone is not enough.
对于纯器乐，只有 `Style Prompt` 是不够的。

The final package should also include a separate instrumental structure-control block.
最终交付包还应包含单独的器乐结构控制块。

This block plays the role of a `Lyrics Box` for instrumental output:
这个模块在纯器乐输出中承担 `Lyrics Box` 的作用：

- it has section tags / 它有段落标签
- it has arrangement cues / 它有编曲提示
- it has pacing and evolution control / 它有推进和演变控制
- it does not contain actual sung lyrics / 它不包含实际演唱歌词

Recommended example shape:
推荐形态：

```text
[Intro - ...]
[Main Theme - ...]
[Variation - ...]
[Breakdown - ...]
[Outro - ...]
```

Use this block to help control duration, loopability, and edit-friendliness.
用这个模块来帮助控制时长、循环友好度和剪辑友好度。

## `optimize_existing_prompt` output blocks / Prompt 优化输出模块

Typical output:
典型输出：

1. Problem Diagnosis / 问题诊断
2. Optimized Prompt / 优化后 Prompt
3. Why This Version Works Better / 为什么更好
4. Optional Variants / 可选变体

## `optimize_existing_lyrics` output blocks / 歌词优化输出模块

Typical output:
典型输出：

1. Lyric Diagnosis / 歌词诊断
2. Revised Lyrics / 优化后歌词
3. Hook and Structure Notes / Hook 与结构说明
4. Optional Next-step Variants / 下一步可选变体

## `generate_multi_versions` output blocks / 多版本输出模块

Typical output:
典型输出：

1. Shared Requirement Summary / 共用需求摘要
2. Version A / 版本 A
3. Version B / 版本 B
4. Version C if needed / 如有必要，版本 C
5. Comparison Advice / 对比建议

## `generate_short_video_hook` output blocks / 短 Hook 输出模块

Typical output:
典型输出：

1. Hook Direction / Hook 方向
2. Short Style Prompt / 短风格 Prompt
3. Hook Lyric or Vocal Idea if relevant / 如适用，Hook 歌词或人声想法
4. Edit Cue Notes / 剪辑提示
5. Variant Options / 变体选项

## Gold examples / 标准样例

These are compact reference shapes for stable output formatting.
以下是用于稳定输出格式的紧凑参考形态。

Do not copy them mechanically. Use them to keep block structure consistent.
不要机械照抄它们；应把它们用作保持输出块结构一致的参考。

### `create_vocal_song` example

```text
Requirement Summary
- A Chinese graduation song for short-video and social sharing

Music Direction
- Warm nostalgic pop with a hopeful late lift

Recommended Title Options
- After the Bell
- The Last Summer Uniform
- See You in Brighter Days

Style Prompt
Genre: Chinese pop, youth nostalgia pop
Mood: warm, reflective, hopeful
Vocal: mixed group vocal, emotionally sincere
Tempo: mid tempo
Texture: piano, light guitar, gradual band lift
Energy: gentle opening, widening chorus, bright finish
Hook: memorable sing-along chorus
Use Case: graduation sharing, class memory montage

Lyrics
[Verse 1]
[Soft piano leads the harmony while light guitar support keeps the rhythm restrained under a close vocal]
...

[Chorus]
[Fuller drums and warm bass open the section up, while wider harmony gives the chorus an uplifting lift]
...

Iteration Prompts
- Make the chorus more anthemic and easier to sing together

Usage Notes
- Suitable for class memory videos and graduation recap edits
```

### `create_instrumental_bgm` example

```text
Requirement Summary
- A healing instrumental track for pre-sleep relaxation

Music Direction
- Soft ambient piano with slow emotional release

Style Prompt
Genre: ambient piano, healing new-age instrumental
Mood: calm, weightless, restorative
Texture: soft piano, warm pad, light air noise
Rhythm: free-flowing, low-percussion or no-percussion
Energy: low and stable, slow bloom, gentle fade
Development: subtle motif repetition with small variations
Use Case: sleep, breathing reset, quiet night routine
Duration: 60-90 seconds, loop-friendly

Instrumental Structure Box
[Intro - sparse piano, wide air]
[Main Theme - soft repeating motif, warm pad support]
[Variation - slightly fuller harmony, still restrained]
[Release - thinner texture, slower decay]
[Loop Out - clean tail for seamless repeat]

Iteration Prompts
- Make it even softer and more bedtime-friendly

Usage Notes
- Works well under low-volume narration or sleep content intros
```

### `optimize_existing_prompt` example

```text
Problem Diagnosis
- The original prompt is too generic in genre and emotional movement

Optimized Prompt
Genre: rock, anthemic pop rock
Mood: determined, expansive, idealistic
Vocal: strong male lead with open-throat chorus delivery
Tempo: mid-up
Texture: electric guitar, live drums, bass drive, crowd-lift chorus
Energy: steady build, large chorus release, confident finish
Hook: direct, chant-ready chorus
Use Case: motivational song, collective uplift, sports montage

Why This Version Works Better
- The genre, hook behavior, and chorus scale are now much clearer

Optional Variants
- A more melodic version
- A rougher live-band version
```

### `optimize_existing_lyrics` example

```text
Lyric Diagnosis
- The chorus idea is clear, but the key line is not memorable enough

Revised Lyrics
[Verse 1]
[A close vocal stays in front while sparse chords and minimal rhythm keep the space intimate]
...

[Chorus]
[The section lifts more strongly with fuller backing, wider vowel shapes, and clearer downbeat support]
...

Hook and Structure Notes
- The chorus line now lands earlier and repeats more cleanly

Optional Next-step Variants
- A more poetic chorus version
- A more direct and shareable chorus version
```

### `generate_multi_versions` example

```text
Shared Requirement Summary
- A city-themed song about Shanghai with stronger street-life detail

Version A
- Urban narrative rap with dialogue energy

Version B
- Night-drive pop with cinematic loneliness

Version C
- City-folk storytelling with drifting warmth

Comparison Advice
- Choose A for sharper imagery and spreadability
- Choose B for atmosphere and visual montage
- Choose C for emotional intimacy
```

### `generate_short_video_hook` example

```text
Hook Direction
- A fast emotional hook for first-impression impact

Short Style Prompt
Genre: pop, short-form emotional hook pop
Mood: immediate, bright, slightly aching
Vocal: youthful lead with clean top-line emphasis
Tempo: mid-up
Hook: first-line catch, short repeat payoff

Hook Lyric or Vocal Idea
[Hook]
[The hook should enter instantly with no long intro, landing on the beat from the first phrase]
...

Edit Cue Notes
- Best if the first vocal phrase lands in the opening second

Variant Options
- More anthemic
- More intimate
```
