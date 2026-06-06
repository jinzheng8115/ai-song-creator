# Structured Runtime Examples
# 结构化运行时示例

## Purpose / 目的

This file provides host-side examples for integrating the skill with structured question tools.
本文提供把本 skill 接入结构化提问工具时的宿主侧示例。

These are conceptual examples, not strict platform-specific APIs.
这些是概念示例，不是某个平台的严格 API 规范。

## Example 1: `AskUserQuestion` style / `AskUserQuestion` 风格示例

Use this shape when the runtime provides a direct structured-question tool.
当运行时提供直接的结构化提问工具时，可以采用这种形态。

```json
{
  "question_id": "track_type",
  "title": "音乐类型",
  "description": "先确定这是一首带歌词歌曲，还是纯器乐 BGM。",
  "type": "single_select",
  "options": [
    { "id": "vocal_song", "label": "带歌词歌曲", "recommended": true },
    { "id": "instrumental_bgm", "label": "纯器乐 / BGM" }
  ]
}
```

## Example 2: `request_user_input` style / `request_user_input` 风格示例

Some runtimes use a higher-level question bundle with explicit options.
有些运行时会用更高层的问题包，并要求显式列出选项。

Conceptual mapping:
概念映射：

```json
{
  "questions": [
    {
      "header": "音乐类型",
      "id": "track_type",
      "question": "先选音乐类型",
      "options": [
        {
          "label": "带歌词歌曲",
          "description": "适合需要歌词、主唱、副歌与歌曲结构的创作"
        },
        {
          "label": "纯器乐 / BGM",
          "description": "适合配乐、旁白底乐、情绪氛围与循环型音乐"
        }
      ]
    }
  ]
}
```

## Example 3: Style recommendation cards / 风格推荐卡片示例

For `generated_recommendations`, render 2–3 system-generated directions as cards.
对于 `generated_recommendations`，应把 2–3 个系统推荐方向渲染成卡片。

```json
{
  "question_id": "style_recommendation",
  "type": "generated_recommendations",
  "options": [
    {
      "id": "urban_pop_narrative",
      "label": {
        "zh": "都市叙事流行",
        "en": "Urban narrative pop"
      },
      "reason": {
        "zh": "适合表达现实压力、独立与内在力量",
        "en": "Good for pressure, independence, and inner strength"
      }
    },
    {
      "id": "cinematic_growth_ballad",
      "label": {
        "zh": "电影感成长抒情",
        "en": "Cinematic growth ballad"
      },
      "reason": {
        "zh": "更适合人物故事与情绪推进",
        "en": "Better for character-driven emotional build"
      }
    }
  ]
}
```

## Example 4: `single_select_with_other` / 带 Other 的单选示例

Stable options should appear first. Show free text only when `Other` is selected.
稳定选项应先出现，只有当用户选择 `Other` 时才显示自由输入。

```json
{
  "question_id": "style_choice",
  "type": "single_select_with_other",
  "options": [
    { "id": "chinese_pop", "label": "中文流行" },
    { "id": "folk_pop", "label": "民谣流行" },
    { "id": "urban_folk", "label": "都市民谣" },
    { "id": "other", "label": "其他" }
  ],
  "other_input": {
    "placeholder": "简要描述你想要的风格"
  }
}
```

## Example 5: Minimal host adapter pseudocode / 最小宿主适配伪代码

```text
1. Read the next unresolved node from the shared skill state
2. Look up the node definition in schema/clickable-interaction-schema-v0.1.json
3. Convert the node into the host runtime's question payload shape
4. Render the structured question
5. Wait for the user's selection
6. Write the answer back into music_brief
7. Route to the next node
8. When the brief is sufficient, hand control back to the generation stage
```

对应中文：

```text
1. 从共享 skill 状态里读取下一个未完成节点
2. 去 schema/clickable-interaction-schema-v0.1.json 查对应节点定义
3. 转成宿主运行时要求的问题 payload
4. 渲染结构化问题
5. 等待用户选择
6. 把答案回写到 music_brief
7. 继续路由到下一个节点
8. 当 brief 足够时，交还给生成阶段
```
