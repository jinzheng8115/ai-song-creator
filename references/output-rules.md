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
