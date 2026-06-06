# AI Music Prompt Skill Clickable Interaction Schema v0.1
# AI 音乐 Prompt Skill 点击交互规范 v0.1

## Purpose / 用途

This document defines how the skill should behave in an interaction environment that supports clickable UI controls.
本文定义本 skill 在支持可点击 UI 控件的交互环境中应如何工作。

The goal is to turn the existing interaction logic into a UI-ready schema.
目标是把现有的交互逻辑转成一份可供 UI 实现的规范。

This schema does not replace the skill logic.
这份规范不替代 skill 逻辑本身。

It describes how that logic should be presented and collected through clickable interaction.
它描述的是：这些逻辑在可点击交互里应如何被呈现和采集。

---

## Design Principles / 设计原则

### 1. Clickable first / 点击优先

If a field has a small stable answer set, use clickable selection first.
如果一个字段的答案集合小且稳定，优先使用点击选择。

### 2. Open text only when needed / 仅在必要时开放输入

Use open text only when:
只有在以下情况下才使用开放输入：

- the field is inherently creative / 该字段本身属于创意表达
- the user chooses “Other” / 用户选择“其他”
- the user wants to supply a reference / 用户要提供参考歌/歌手

### 3. Short path by default / 默认走最短路径

The UI should minimize typing and reduce unnecessary branching.
UI 应尽量减少输入量，避免不必要分支。

### 4. Same logic, different surface / 逻辑一致，界面不同

The clickable UI and chat fallback should use the same underlying skill logic.
点击 UI 和聊天 fallback 底层逻辑应保持一致。

---

## Interaction Model / 交互模型

Each node in the flow should define:
流程中的每个节点应定义：

- `field_id` / 字段 ID
- `label` / 显示名称
- `type` / 交互类型
- `options` / 选项
- `required` / 是否必填
- `when_to_show` / 何时显示
- `fallback` / 文本 fallback 方式
- `next` / 下一步流转

Suggested UI types:
建议的 UI 类型：

- `single_select` / 单选
- `multi_select` / 多选
- `single_select_with_other` / 单选 + 其他输入
- `text_input` / 文本输入
- `text_area` / 长文本输入
- `generated_recommendations` / 系统生成推荐选项

---

## Core Flow / 核心流程

```text
Intent Entry
→ Track Type
→ Use Case
→ Style Path Choice
→ Style Selection / Recommendation / Reference Analysis
→ Mood Selection
→ Vocal Preference (if vocal song)
→ Lyric Language (if vocal song)
→ Output Format
→ Optional Refinement
→ Requirement Summary
→ Final Output
→ Title Selection (optional follow-up)
→ Iteration Follow-up
```

---

## Node Specifications / 节点规范

## Node 1: Track Type / 节点 1：音乐类型

- `field_id`: `track_type`
- `type`: `single_select`
- `required`: `true`

### Options / 选项
- 带歌词歌曲
- 纯器乐 / BGM

### When to show / 显示时机
Always show when track type is not already clear from the user’s first message.
当用户首句还未明确音乐类型时显示。

### Fallback / fallback
```text
A. 带歌词歌曲
B. 纯器乐 / BGM
```

### Next / 下一步
- if 带歌词歌曲 → go to Use Case
- if 纯器乐 / BGM → go to Use Case

---

## Node 2: Use Case / 节点 2：使用场景

- `field_id`: `use_case`
- `type`: `single_select_with_other`
- `required`: `true`

### Options / 选项
- 自媒体内容配歌
- 短视频剧情配歌
- 个人表达 / 朋友圈分享
- 品牌广告 / 活动主题歌
- 纪录片 / 采访配歌
- Livehouse / 演出感歌曲
- 婚礼 / 毕业 / 校园纪念
- 体育主题 / 助威歌曲
- 其他

### Other behavior / 其他行为
If the user chooses “其他”, open a short text field.
如果用户选择“其他”，展开一个简短文本输入。

### Fallback / fallback
Short choice list first, then allow one-line custom use case.
先短选项，再允许一行补充说明。

---

## Node 3: Style Path Choice / 节点 3：风格路径选择

- `field_id`: `style_path`
- `type`: `single_select`
- `required`: `true`

### Options / 选项
- 直接选风格
- 不确定，帮我推荐
- 用参考歌 / 歌手分析风格

### Next / 下一步
- 直接选风格 → Node 4A
- 帮我推荐 → Node 4B
- 参考歌/歌手分析 → Node 4C

### Fallback / fallback
```text
A. 直接选风格
B. 不确定，帮我推荐
C. 用参考歌/歌手分析风格
```

---

## Node 4A: Direct Style Choice / 节点 4A：直接选风格

- `field_id`: `style_choice`
- `type`: `single_select_with_other`
- `required`: `true`

### Options / 选项
- 中文流行
- 民谣流行
- 都市民谣
- R&B / 都市流行
- 摇滚 / 流行摇滚
- 电子流行
- 电影感流行
- 国风流行
- 体育 anthem
- 治愈抒情
- 其他

### Fallback / fallback
A short pick list or A/B/C choice.
短选项列表或 A/B/C 选择。

---

## Node 4B: Guided Recommendation / 节点 4B：系统推荐风格

- `field_id`: `style_recommendation`
- `type`: `generated_recommendations`
- `required`: `true`

### Behavior / 行为
The system generates 2–3 likely style directions based on:
系统根据以下内容生成 2–3 个推荐方向：

- use case / 使用场景
- theme / 主题
- mood / 情绪
- track type / 音乐类型

### UI form / UI 形式
Present the recommendations as clickable cards or chips.
把推荐方向渲染成可点击卡片或标签。

### Fallback / fallback
List 2–3 recommended directions in text and let the user reply with 1/2/3.
用文本列出 2–3 个推荐方向，让用户回复 1/2/3。

---

## Node 4C: Reference-Based Style Analysis / 节点 4C：参考歌/歌手分析风格

- `field_id`: `style_reference`
- `type`: `text_input`
- `required`: `true`

### Prompt / 提示语
“给我一首你喜欢的歌，或一个你喜欢的歌手，我来帮你分析成风格方向。”
“Give me a favorite song or singer, and I’ll analyze it into style traits.”

### System behavior / 系统行为
The system should extract abstract traits such as:
系统应提取抽象特征，例如：

- era feel / 年代感
- vocal texture / 嗓音质感
- arrangement density / 编曲密度
- melodic warmth / 旋律温度
- rhythmic feel / 节奏气质
- emotional posture / 情绪姿态

### Safety rule / 安全规则
Do not output direct imitation instructions.
不要输出直接模仿指令。

### UI follow-up / UI 后续
After analysis, show 2–3 abstracted style directions as clickable options.
分析后，把 2–3 个抽象化风格方向以可点击选项展示。

---

## Node 5: Mood Selection / 节点 5：情绪选择

- `field_id`: `mood`
- `type`: `single_select_with_other`
- `required`: `true`

### Options / 选项
- 温暖治愈
- 孤独克制
- 现实苦涩
- 怀旧伤感
- 坚定向前
- 热血高燃
- 高级感 / 电影感
- 不确定，帮我推荐
- 其他

### Behavior / 行为
If the user picks “不确定，帮我推荐”, recommend 2–3 likely moods based on theme and use case.
如果用户选择“不确定，帮我推荐”，系统根据主题和场景推荐 2–3 个可能情绪方向。

---

## Node 6: Vocal Preference / 节点 6：人声偏好

- `field_id`: `vocal_preference`
- `type`: `single_select`
- `required`: `true` for vocal songs
- `when_to_show`: only if `track_type = vocal_song`

### Options / 选项
- 男声主唱
- 女声主唱
- 男女对唱
- 合唱感更强
- 不确定，帮我推荐

---

## Node 7: Lyric Language / 节点 7：歌词语言

- `field_id`: `lyric_language`
- `type`: `single_select`
- `required`: `true` for vocal songs
- `when_to_show`: only if `track_type = vocal_song`

### Options / 选项
- 中文
- 英文
- 中英混合

### Default / 默认值
Default to Chinese only if the user chooses to skip this field or explicitly does not care.
只有当用户主动跳过或明确表示不在意时，才默认中文。

---

## Node 8: Output Format / 节点 8：输出形式

- `field_id`: `output_format`
- `type`: `single_select`
- `required`: `true`

### Options / 选项
- 简洁版 Prompt
- 完整 Prompt 包
- 歌词 + Style Prompt
- 多个版本方向
- 30 秒 Hook

---

## Node 9: Optional Refinement / 节点 9：可选细化

- `field_id`: `refinement`
- `type`: conditional
- `required`: `false`

### Show only when / 仅在以下情况显示
- the selected mode still lacks a critical field / 当前 mode 仍缺关键字段
- the user chooses “refine more” / 用户主动想进一步细化
- the use case requires one more structural decision / 场景确实需要再补一项结构性决策

Examples:
示例：
- hook strength / Hook 强度
- loopability / 可循环性
- voiceover space / 旁白空间
- tempo preference / 节奏偏好

---

## Node 10: Requirement Summary / 节点 10：需求摘要

Before final generation, show a short summary card.
正式生成前，展示一个简短需求摘要卡片。

### Purpose / 用途
- confirm direction quickly / 快速确认方向
- avoid silent misinterpretation / 避免静默误解
- allow one last correction / 给用户最后一次改正机会

This should be skippable if the user asked for maximum speed.
如果用户明确要求快一点，这一步可以弱化或跳过。

---

## Node 11: Final Output / 节点 11：最终输出

### For lyric-based songs / 带歌词歌曲
Output structure should include:
输出结构应包含：

- Requirement Summary
- Music Direction
- Recommended Title Options
- Style Prompt
- Structure & Arrangement Notes
- Lyrics
- Iteration Prompts
- Usage Notes

### For instrumental tracks / 纯器乐
Output structure should include:
输出结构应包含：

- Requirement Summary
- Music Direction
- Style Prompt
- Instrumental Structure Box
- Iteration Prompts
- Usage Notes

---

## Node 12: Title Selection Follow-up / 节点 12：歌名选择后续

- `field_id`: `title_selection`
- `type`: `single_select`
- `required`: `false`
- `when_to_show`: after lyric-based final output

### Behavior / 行为
If the UI supports it, recommended titles should be clickable so the user can pick one and ask for refinement around that title.
如果 UI 支持，推荐歌名应可点击，让用户选中一个歌名后继续围绕它做微调。

### Fallback / fallback
If clickable title selection is unavailable, list titles clearly and let the user respond with the title or a number.
如果无法点击，就清晰列出歌名，让用户回复歌名或序号。

---

## Node 13: Iteration Follow-up / 节点 13：迭代后续

After the first output, the UI should offer a few structured next actions.
第一轮输出后，UI 应提供几个结构化下一步动作。

Suggested options:
建议选项：
- 调整副歌更抓耳
- 改得更电影感
- 改得更真实克制
- 换一个风格版本
- 围绕某个歌名继续细化
- 重新生成歌词

These can be clickable chips or buttons.
这些都可以设计成可点击标签或按钮。

---

## Fallback Mapping / fallback 映射

When clickable UI is unavailable:
当没有点击 UI 时：

- `single_select` → A/B/C text choice
- `single_select_with_other` → A/B/C + “其他”文本输入
- `generated_recommendations` → numbered recommendations
- `title_selection` → numbered title list

The fallback should preserve the same branching logic.
fallback 应保持与点击版同样的分支逻辑。

---

## Success Criteria / 成功标准

A clickable implementation passes if:
可点击交互实现通过的标准是：

1. users can answer fixed questions with little or no typing / 用户几乎不需要打字就能回答固定问题
2. open text is reserved for truly creative fields / 开放输入只保留给真正的创意字段
3. style collection supports all three paths cleanly / 曲风采集三路径都清晰可用
4. reference-song or singer input is analyzed safely / 参考歌/歌手输入被安全分析
5. lyric-based outputs show recommended titles explicitly / 歌词歌输出显式展示推荐歌名
6. lyrics remain separate from structure and arrangement notes / 歌词与结构/编曲说明保持分离
7. chat fallback remains usable when clickable UI is absent / 无点击 UI 时，聊天 fallback 仍可用

---

## Recommended Use / 推荐用途

Use this schema when:
在以下场景使用本规范：

- designing a real product UI for the skill / 为 skill 设计真实产品 UI
- prototyping the clickable flow / 制作点击交互原型
- comparing clickable flow with chat fallback / 比较点击交互与聊天 fallback
- implementing structured interaction on top of the skill logic / 在 skill 逻辑之上实现结构化交互
