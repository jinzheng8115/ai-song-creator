# Language and Safety Rules
# 语言与安全规则

## Lyrics language / 歌词语言

Lyrics should follow the user’s request.
歌词应跟随用户要求。

If the user asks for:
如果用户要求：

- Chinese lyrics / 中文歌词 → output Chinese lyrics / 输出中文歌词
- English lyrics / 英文歌词 → output English lyrics / 输出英文歌词
- bilingual lyrics / 双语歌词 → output bilingual lyrics / 输出双语歌词

Default to Chinese lyrics only when the user explicitly skips this field or says they do not care.
只有当用户明确跳过这个字段或表示不在意时，才默认输出中文歌词。

If the lyrics require duet roles, multi-gender vocal exchange, or role-tagged delivery, keep the role labels in English.
如果歌词需要对唱角色、多性别人声分配或带标签的演唱指示，应把角色标签保持为英文。

Examples:
例如：

- `Male`
- `Female`
- `Male Lead`
- `Female Lead`
- `Group`
- `All`

Do not switch these role labels into Chinese forms such as `男` or `女` inside the lyrics block.
不要把这些角色标签改成 `男`、`女` 这样的中文形式放进歌词块里。

## Prompt-module language / Prompt 模块语言

Prompt modules should default to English.
Prompt 模块默认应使用英文。

These include blocks such as:
这包括例如：

- `Style Prompt`
- `Structure & Arrangement Notes`
- `Iteration Prompts`
- `Usage Notes`

Do not mix Chinese into the actual prompt payload unless the user explicitly asks for Chinese prompt blocks.
除非用户明确要求中文 prompt 块，否则不要把中文混入实际 prompt 载荷。

The inside of `Style Prompt` should remain English-only by default.
`Style Prompt` 的内部默认必须保持全英文。

## Human-facing explanation language / 面向用户的说明语言

Human-facing explanation should default to Chinese unless the user clearly requests another language.
给用户看的说明文字默认应使用中文，除非用户明确要求其他语言。

Do not mix explanatory prose into the tool-ready prompt block.
不要把解释性文字混入工具可直接使用的 Prompt 模块里。

This creates a two-layer language rule:
这形成一个双层语言规则：

1. prompt payload blocks default to English / prompt 载荷块默认英文
2. outer user-facing wrapper content defaults to Chinese / 外层面向用户包装内容默认中文

## No direct imitation / 不直接模仿

Do not directly imitate a real artist, singer, or existing song.
不要直接模仿真实歌手、歌手风格或现有歌曲。

If the user gives a reference song or singer:
如果用户给出参考歌曲或歌手：

1. extract abstract musical traits / 提取抽象音乐特征
2. describe era feel, vocal texture, arrangement density, melodic warmth, rhythmic feel, or emotional posture / 描述时代感、人声质感、编排密度、旋律温度、节奏感或情绪姿态
3. convert the reference into a non-imitative direction / 转成非模仿式方向

## Commercial-use reminder / 商业用途提醒

When the request is clearly commercial, brand-facing, or public-release oriented, add a brief reminder that the user should review originality, rights, and platform policies before release.
当请求明显涉及商业用途、品牌传播或公开发布时，应补一句简短提醒：上线前请自行复核原创性、权利归属及平台政策。
