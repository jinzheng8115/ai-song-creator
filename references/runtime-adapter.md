# Structured Question Runtime Adapter
# 结构化提问运行时适配器

## Purpose / 目的

This file defines how the skill should integrate with a host runtime that supports structured question tools, so the user can interact through clickable buttons, chips, cards, or radio options.
本文定义当宿主运行时支持结构化提问工具时，本 skill 应如何接入，从而让用户通过按钮、chips、卡片或单选项进行点击交互。

## Core principle / 核心原则

Clickable interaction is a runtime capability, not a markdown effect.
可点击交互是运行时能力，不是 markdown 文案效果。

The skill should support two compatible paths:
本 skill 应支持两条兼容路径：

1. structured-choice runtime path / 结构化提问运行时路径
2. plain-chat fallback path / 普通聊天降级路径

Both paths must share:
两条路径必须共享：

- the same node order / 相同节点顺序
- the same option semantics / 相同选项语义
- the same routing logic / 相同路由逻辑

## Supported tool concepts / 支持的工具概念

Examples:
示例：

- `AskUserQuestion`
- `request_user_input`
- any equivalent structured choice API / 任何等价的结构化选项 API

The exact tool name may vary. The contract matters more than the name.
具体工具名可以不同，真正重要的是适配契约，而不是名称本身。

## Node mapping / 节点映射

- `single_select` → one structured single-choice question / 一个结构化单选题
- `multi_select` → one structured multi-choice question / 一个结构化多选题
- `single_select_with_other` → stable options plus an `Other` text branch / 稳定选项加一个 `其他` 文本分支
- `generated_recommendations` → 2–3 recommendation cards or numbered choices / 2–3 个推荐卡片或编号选项
- `text_input` and `text_area` → open text only where creative specificity is needed / 只有在确实需要创意细节时才开放文本输入

## Batching / 合并提问

If the runtime supports multiple questions in one step, batch only closely related fixed-answer questions.
如果运行时支持一步多问，只合并紧密相关的固定答案题。

Recommended batching:
推荐合并：

- `track_type` + `output_format`
- `vocal_preference` + `lyric_language` in vocal-song mode

Do not over-batch into a giant form.
不要一次性堆成一个巨大的表单。

## Fallback order / 降级顺序

1. clickable structured question / 可点击结构化问题
2. numbered or lettered concise choices / 编号或字母简洁选项
3. open text only when necessary / 仅在必要时开放文本输入

## Source of truth / 事实来源

Use these as the main source of truth:
以下文件是主要事实来源：

- `SKILL.md`
- `schema/clickable-interaction-schema-v0.1.json`

Useful examples:
有用示例：

- `schema/demo-interaction-payloads-v0.1.json`
- `evals/real-interaction-test-spec-v0.1.md`
