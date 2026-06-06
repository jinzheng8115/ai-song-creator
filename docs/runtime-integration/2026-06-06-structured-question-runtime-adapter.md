# Structured Question Runtime Adapter for AI Music Skill
# AI 音乐 Skill 的结构化提问运行时适配规范

## Purpose / 目的

This document defines how the skill should integrate with a host runtime that supports structured question tools, so the user can see clickable buttons, chips, radio options, or cards instead of typing everything manually.
本文定义本 skill 如何接入支持结构化提问工具的宿主运行时，从而让用户看到可点击按钮、chips、单选项或卡片，而不是所有内容都靠手动输入。

This document does not replace the skill logic. It is an adapter contract between:
本文不替代 skill 本身的逻辑。它是以下两层之间的适配契约：

1. the skill decision flow / skill 的决策流程
2. the host UI or runtime question renderer / 宿主 UI 或运行时的问题渲染器

## Core idea / 核心思想

Clickable interaction does not come from markdown wording alone.
可点击交互并不是仅靠 markdown 文案自然产生的。

It requires a runtime that can render structured questions.
它需要一个能够渲染结构化问题的运行时。

Therefore, the integration target is:
因此，集成目标是：

- keep one canonical decision flow / 保留一套唯一的标准决策流
- let the runtime render stable-choice nodes as clickable UI / 让运行时把稳定选项节点渲染成可点击 UI
- keep creative-detail nodes as text input when needed / 需要创意细节时保留文本输入
- preserve a plain-chat fallback / 保留普通聊天降级路径

## Supported runtime tool shapes / 支持的运行时工具形态

The skill should be compatible with any structured interaction tool that can express:
本 skill 应兼容任何能表达以下能力的结构化交互工具：

1. a short question prompt / 简短问题提示
2. 2–8 explicit options / 2–8 个明确选项
3. optional recommended option / 可选的推荐项
4. optional `Other` text entry / 可选的 `其他` 文本输入
5. a stable choice identifier / 稳定的选项 ID

Examples of host-side tool concepts:
宿主侧工具概念示例：

- `AskUserQuestion`
- `request_user_input`
- custom structured choice APIs
- in-product form or chat widget renderers

The exact tool name can vary. The adapter contract matters more than the name.
具体工具名可以不同，真正重要的是适配契约，而不是名字本身。

## Source of truth / 单一事实来源

Use the following files as the main source of truth:
以下文件应作为主要事实来源：

- `SKILL.md`
- `schema/clickable-interaction-schema-v0.1.json`

Recommended demo and testing references:
建议的 demo 与测试参考：

- `schema/demo-interaction-payloads-v0.1.json`
- `evals/real-interaction-test-spec-v0.1.md`

## Node-to-UI mapping / 节点到 UI 的映射

### 1. `single_select`

Render as one clickable single-choice control.
渲染为一个可点击的单选控件。

Good UI candidates:
合适的 UI 形式：

- radio list
- segmented control
- choice chips
- cards

### 2. `multi_select`

Render as one clickable multi-choice control.
渲染为一个可点击的多选控件。

Good UI candidates:
合适的 UI 形式：

- checkbox list
- multi-select chips

### 3. `single_select_with_other`

Render the stable options first, and expose `Other` only when selected.
优先渲染稳定选项，只有当用户点了 `Other` 时，才展开额外文本输入。

Do not show the custom text field too early.
不要过早显示自定义文本输入框。

### 4. `generated_recommendations`

Render 2–3 system-generated directions as clickable cards or numbered options.
把系统生成的 2–3 个方向渲染为可点击卡片或编号选项。

Each recommendation should include:
每个推荐方向应包含：

- stable id / 稳定 ID
- short label / 短标签
- one-sentence reason / 一句话推荐理由

### 5. `text_input` and `text_area`

Use only where the user’s own words materially shape the creative result.
只有在用户原始表达会明显影响创作结果时才使用。

Typical valid cases:
典型适用场景：

- theme description / 主题描述
- scenario details / 场景细节
- story intent / 故事意图
- reference song or singer / 参考歌曲或歌手
- custom style description / 自定义风格描述

## Batching rules / 合并提问规则

The host runtime may support asking multiple questions in one structured interaction.
宿主运行时可能支持在一次结构化交互里同时问多个问题。

Use batching only when it improves speed without reducing clarity.
只有在提升效率且不降低清晰度时，才进行合并提问。

Recommended batching:
推荐的合并方式：

- `track_type` + `output_format`
- `vocal_preference` + `lyric_language` for vocal-song mode

Avoid batching these together too early:
避免过早把以下内容混在一起：

- style path
- style recommendation cards
- custom creative text input

Reason:
原因：

These often depend on the user’s earlier answers.
这些内容通常依赖用户前面的选择结果。

## Fallback rules / 降级规则

If structured rendering is unavailable, fall back to plain chat without changing the underlying logic.
如果结构化渲染不可用，应退回普通聊天，但不能改变底层逻辑。

Recommended fallback order:
建议的降级顺序：

1. clickable structured question / 可点击结构化问题
2. numbered or lettered concise choices / 编号或字母的简洁选项
3. open text only if necessary / 仅在必要时开放输入

The fallback must preserve:
降级时必须保留：

- same node IDs / 相同节点 ID
- same option semantics / 相同选项语义
- same routing behavior / 相同路由行为

## Example runtime payload shape / 运行时 payload 示例

This is a conceptual example, not a strict platform-specific API:
以下是概念示例，不是某个平台的严格 API：

```json
{
  "question_id": "track_type",
  "label": {
    "zh": "音乐类型",
    "en": "Track Type"
  },
  "type": "single_select",
  "options": [
    { "id": "vocal_song", "label": { "zh": "带歌词歌曲", "en": "Vocal song with lyrics" } },
    { "id": "instrumental_bgm", "label": { "zh": "纯器乐 / BGM", "en": "Instrumental / BGM" } }
  ],
  "recommended_option_id": "vocal_song"
}
```

For a recommendation node:
对于推荐节点：

```json
{
  "question_id": "style_recommendation",
  "type": "generated_recommendations",
  "options": [
    {
      "id": "urban_pop_narrative",
      "label": { "zh": "都市叙事流行", "en": "Urban narrative pop" },
      "reason": {
        "zh": "适合表达现实压力与内在力量",
        "en": "Fits real-world pressure and inner strength"
      }
    }
  ]
}
```

## Skill execution contract / Skill 执行契约

When structured question runtime is available, the skill should:
当结构化提问运行时可用时，本 skill 应：

1. detect the next unresolved node / 识别下一个未完成节点
2. convert it into a structured question payload / 转成结构化问题 payload
3. wait for the user selection / 等待用户选择
4. write the result back into the internal `music_brief` / 回写到内部 `music_brief`
5. continue routing / 继续路由

The skill should not:
本 skill 不应：

- duplicate the same question in prose and structured form at the same time / 同时用 prose 和结构化格式重复问同一个问题
- silently skip meaningful user choice when the runtime can cleanly ask it / 当运行时能清楚提问时，静默跳过重要选择
- ask for free text when a stable choice set is already known / 在已知稳定选项集时还要求自由输入

## Recommended implementation strategy / 建议实现策略

If you want real clickable UX, add a host-side adapter layer that:
如果你想获得真实可点击体验，应增加一个宿主侧适配层，它负责：

1. read the node definitions from `schema/clickable-interaction-schema-v0.1.json`
2. map them into the host’s structured question API
3. store answers into a shared state object
4. feed the final state back into the skill generation stage

This keeps the skill logic stable while allowing different frontends or runtimes to reuse it.
这样既能保持 skill 逻辑稳定，也能让不同前端或运行时复用同一套能力。

## Karpathy-style quality checklist / Karpathy 风格自检清单

Before claiming runtime integration is ready, check:
在声称运行时接入完成之前，请检查：

1. Is there one clear source of truth for the question flow? / 是否有一套清晰唯一的问题流事实来源？
2. Can fixed-answer questions really render as clickable UI? / 固定答案题是否真的能渲染成可点击 UI？
3. Does fallback preserve the same semantics? / 降级路径是否保留相同语义？
4. Are creative text fields kept only where they are necessary? / 创意文本输入是否只保留在必要位置？
5. Can the same skill run both in clickable UI and plain chat? / 同一个 skill 是否同时支持 clickable UI 和普通聊天？
