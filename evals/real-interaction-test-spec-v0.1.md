# AI Music Prompt Skill Real Interaction Test Spec v0.1
# AI 音乐 Prompt Skill 真实交互测试规范 v0.1

## Purpose / 用途

This document defines how to test the skill in realistic interaction environments.
本文定义如何在真实交互环境中测试这个 skill。

The key distinction is that the same skill may run in two very different environments:
关键点在于：同一个 skill 可能运行在两种非常不同的环境中：

1. a product UI with clickable controls / 带可点击控件的产品 UI
2. a chat-only environment without clickable controls / 没有点击控件的纯聊天环境

The skill should behave differently in these two environments while keeping the same decision logic.
这个 skill 在这两种环境中的交互方式应该不同，但底层决策逻辑应保持一致。

---

## Testing Goals / 测试目标

Real-interaction testing should verify:
真实交互测试应验证：

1. whether fixed-answer questions are presented in the right interaction form / 固定答案问题是否以正确的交互形式出现
2. whether creative questions remain easy to answer / 创意问题是否仍然容易回答
3. whether the skill asks too much or too little / skill 是否问得太多或太少
4. whether fallback behavior is acceptable when clickable UI is unavailable / 在无法点击时，fallback 是否可接受
5. whether the final output remains consistent across environments / 不同环境下最终输出是否保持一致

---

## Environment A: Clickable Product UI / 环境 A：可点击产品 UI

### Expected interaction pattern / 预期交互方式

In a real product UI, fixed-answer questions should use clickable controls first.
在真实产品 UI 中，固定答案问题应优先使用可点击控件。

Preferred UI forms:
优先 UI 形式：

- buttons / 按钮
- radio groups / 单选项
- chips / 标签选项
- segmented controls / 分段选择器
- dropdowns when the choice list is long / 选项过多时用下拉菜单

### What should be clickable / 哪些问题应点击选择

These should usually be clickable:
这些通常应设计成点击选择：

- track type / 音乐类型
- output format / 输出形式
- lyric language / 歌词语言
- vocal preference / 人声偏好
- broad mood presets / 大类情绪预设
- broad use-case presets / 大类使用场景预设
- direct style choice / 直接风格选择

### What can remain open-ended / 哪些仍可开放输入

These should remain open-ended unless the product intentionally constrains them:
除非产品刻意收窄，否则以下内容仍应保留开放输入：

- theme / 主题
- story angle / 故事角度
- personal details / 个人细节
- imagery / 画面感
- why this song matters / 为什么要写这首歌
- favorite reference song or singer / 喜欢的参考歌曲或歌手

### Clickable-first rule / 点击优先规则

If a question can be answered from a small stable answer set, clickable choice should be the first path.
如果一个问题的答案集合小且稳定，点击选择应当是第一路径。

Open text should be used only when:
只有在以下情况下才优先开放输入：

- the answer is inherently creative / 答案本身就是创意内容
- the user explicitly chooses “other” / 用户明确选择“其他”
- the user wants to provide a custom reference / 用户想提供自定义参考输入

---

## Environment B: Chat-Only Fallback / 环境 B：纯聊天 fallback

### Expected interaction pattern / 预期交互方式

If clickable controls are unavailable, the skill should not pretend they exist.
如果没有点击控件，skill 不应假装它们存在。

Instead, it should switch to the lightest possible text fallback.
它应切换到最轻量的文本 fallback。

### Best fallback style / 最佳 fallback 形式

Preferred fallback order:
建议的 fallback 顺序：

1. short labeled options / 简短标签选项
2. A/B/C-style answers / A/B/C 字母回答
3. compact structured reply format / 紧凑结构化回复

Example:
示例：

```text
使用场景
A. 自媒体内容配歌
B. 短视频剧情配歌
C. 个人表达 / 朋友圈分享

情绪方向
A. 温暖治愈
B. 孤独克制
C. 现实苦涩
```

The user should be able to answer with as little typing as possible.
应尽量让用户用最少输入完成回答。

### What should not happen / 不应发生的情况

The fallback should not turn into:
fallback 不应退化成：

- a long questionnaire / 冗长问卷
- repeated restatement of all options / 反复重述所有选项
- asking the user to rewrite obvious structured choices in free text / 让用户把明显可结构化的问题重写成自由文本

---

## Shared Interaction Logic Across Both Environments / 两种环境共用的交互逻辑

Regardless of UI form, the underlying logic should stay the same.
不管 UI 形式如何，底层逻辑应保持一致。

### Rule 1 / 规则 1

Ask only what materially changes the output.
只问会明显改变结果的问题。

### Rule 2 / 规则 2

Fixed routing fields should be selectable.
固定路由字段应可选择。

### Rule 3 / 规则 3

Creative content should stay expressive.
创意内容应保持表达自由度。

### Rule 4 / 规则 4

If the user already gave enough information, skip unnecessary questioning.
如果用户已经给了足够信息，就跳过不必要提问。

### Rule 5 / 规则 5

Style collection should support three paths:
风格采集应支持三条路径：

- direct style choice / 直接选择风格
- guided recommendation / 系统推荐
- reference-based style analysis / 参考作品/歌手分析

---

## Field-by-Field Test Guidance / 分字段测试指导

## 1. Track Type / 音乐类型

### In clickable UI / 可点击 UI
Use buttons or radio choices:
用按钮或单选项：
- 带歌词歌曲
- 纯器乐 / BGM

### In chat fallback / 聊天 fallback
Use:
采用：
- A. 带歌词歌曲
- B. 纯器乐 / BGM

### What to test / 测什么
- is the choice clear / 选项是否足够清楚
- does the user answer quickly / 用户是否能快速作答
- does the skill stop asking vocal-specific questions after instrumental is chosen / 选了器乐后是否停止问歌词/人声问题

---

## 2. Use Case / 使用场景

### In clickable UI / 可点击 UI
Offer a few common presets plus “Other”.
提供几个常见预设，再加“其他”。

### In chat fallback / 聊天 fallback
Offer a short choice list first, then allow short custom text.
先给短选项，再允许简短补充输入。

### What to test / 测什么
- are presets useful / 预设是否有用
- does the user still have room to express nuance / 用户是否还能表达细节
- does use case meaningfully affect output structure / 使用场景是否真的影响结构输出

---

## 3. Style Preference / 风格偏好

### In clickable UI / 可点击 UI
Offer three paths:
提供三条路径：
- 直接选风格
- 帮我推荐
- 用参考歌/歌手分析

### In chat fallback / 聊天 fallback
Use the same three-path logic in text.
在文本中维持同样的三路径逻辑。

### What to test / 测什么
- can uncertain users move forward easily / 不确定风格的用户是否容易继续
- do recommendations feel plausible / 系统推荐是否合理
- are reference songs analyzed safely instead of copied / 参考歌曲是否被安全分析而非直接模仿

---

## 4. Vocal Preference / 人声偏好

### In clickable UI / 可点击 UI
Use direct selectable presets.
直接用可选预设。

### In chat fallback / 聊天 fallback
Use compact options.
使用紧凑选项。

### What to test / 测什么
- is the choice set complete enough / 选项是否足够完整
- does “unsure” lead to useful recommendation / “不确定” 是否导向有效推荐

---

## 5. Output Format / 输出形式

### In clickable UI / 可点击 UI
Always present as selectable options.
始终作为可选择项呈现。

### In chat fallback / 聊天 fallback
Use A/B/C/D-style reply.
使用 A/B/C/D 式回复。

### What to test / 测什么
- can users understand the difference between formats / 用户是否理解不同输出形式的区别
- does format choice actually change output shape / 输出形式是否真的影响输出结构

---

## 6. Title Recommendation / 歌名推荐

### In clickable UI / 可点击 UI
For lyric-based songs, recommended titles should be presented as an explicit list, ideally tappable for follow-up refinement.
对于带歌词歌曲，推荐歌名应作为明确列表展示，理想情况下用户可以直接点击某个歌名继续细化。

### In chat fallback / 聊天 fallback
Still present titles as a visible list, not hidden in a paragraph.
即使在文本 fallback 中，也应把歌名作为清晰列表输出，而不是藏在段落里。

### What to test / 测什么
- are title options visible enough / 歌名是否足够显眼
- can users quickly choose a direction / 用户是否能快速选方向
- does title choice improve downstream refinement / 歌名选择是否真的帮助后续微调

---

## 7. Lyrics vs Structure Split / 歌词与结构分离

### In all environments / 所有环境通用
For lyric-based songs, keep:
对于带歌词歌曲，始终保持：
- `Structure & Arrangement Notes` separate
- `Lyrics` separate

### What to test / 测什么
- is it easier to copy and reuse / 是否更方便复制和复用
- does the user clearly understand what is prompt control and what is lyric text / 用户是否能清楚区分控制信息和歌词正文

---

## Success Criteria / 成功标准

A real-interaction test passes when:
真实交互测试通过的标准是：

1. the user can answer fixed routing questions quickly / 用户能快速回答固定路由问题
2. creative questions still feel open enough / 创意问题仍有足够表达空间
3. the skill does not over-question / skill 不会过度提问
4. clickable UI and chat fallback feel different in form but consistent in logic / 可点击 UI 和聊天 fallback 形式不同，但逻辑一致
5. final outputs remain structurally consistent across environments / 不同环境中的最终输出结构保持一致

---

## Recommended Use of This Spec / 本规范的推荐使用方式

Use this spec before:
在以下场景前使用本规范：

- testing a prototype UI / 测试产品原型 UI
- testing the skill in a text-only assistant / 在纯文本助手里测试 skill
- evaluating whether interaction design matches the skill logic / 评估交互设计是否符合 skill 逻辑
- comparing product UI behavior vs chat fallback behavior / 比较产品 UI 与聊天 fallback 的行为差异
