# AI Music Prompt Skill 文件索引 v0.1  
# AI Music Prompt Skill File Index v0.1

> 本索引用于管理目前已经生成的 AI 音乐 Prompt Skill 相关 Markdown 文件。  
> This index organizes all Markdown files currently generated for the AI Music Prompt Skill project.

---

## 1. 项目目标 / Project Goal

本项目目标是构建一个 **交互式 AI 音乐 Prompt Skill**。

它通过客户访谈方式采集需求，并调用多个素材库，最终生成适合 Suno、Udio 或类似 AI 音乐工具使用的：

- Style Prompt / 风格提示词
- Lyrics Box / 歌词框
- Instrumental Custom Box / 纯器乐结构框
- Iteration Prompt / 迭代优化 Prompt
- 完整 AI 音乐 Prompt 包

项目采用 **progressive disclosure / 渐进式加载** 思路：主 `SKILL.md` 只保留核心工作流、触发条件和路由规则，详细知识放在 `libraries/` 目录中按需调用。

---

## 2. 推荐 Skill 项目目录 / Recommended Skill Folder Structure

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
│   ├── vocal_song_example.md
│   ├── instrumental_bgm_example.md
│   ├── short_video_hook_example.md
│   ├── brand_theme_song_example.md
│   └── sports_anthem_example.md
└── checklists/
    ├── requirement_collection_checklist.md
    ├── prompt_quality_checklist.md
    └── copyright_safety_checklist.md
```

---

## 3. 当前核心文件 / Current Core Files

| 序号 | 文件名 | 中文名称 | 作用 | 建议目录 | 状态 |
|---:|---|---|---|---|---|
| 1 | `ai_music_genre_library_v0.2.md` | 曲风库 v0.2 | 管理带人声歌曲与现代流行器乐的曲风分类、子风格、场景映射、年代增强器 | `libraries/` | 核心库 |
| 2 | `ai_music_rhythm_bpm_scene_mapping_v0.1.md` | 节奏 / BPM / 场景映射库 | 把用户节奏描述、曲风、情绪、场景转成 BPM、律动和节奏密度 | `libraries/` | 核心库 |
| 3 | `ai_music_vocal_voice_library_v0.1.md` | 人声与嗓音描述库 | 管理男声、女声、合唱、说唱、旁白、儿童声、人声质感和演唱方式 | `libraries/` | 核心库 |
| 4 | `ai_music_instrumentation_arrangement_library_v0.1.md` | 乐器与编曲素材库 | 管理乐器层、编曲素材、曲风到乐器、场景到乐器、纯器乐编曲 | `libraries/` | 核心库 |
| 5 | `ai_music_emotion_expression_mapping_v0.1.md` | 情绪与音乐表达映射库 | 把温暖、伤感、治愈、热血、电影感、高级感等转成音乐表达 | `libraries/` | 核心库 |
| 6 | `ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md` | 使用场景、结构与编曲映射库 v0.2 双语版 | 根据短视频、品牌片、体育、学习 BGM 等场景选择结构、Hook 位置和逐段编曲 | `libraries/` | 核心库 |
| 7 | `ai_music_prompt_templates_v0.1_bilingual.md` | Style Prompt / Lyrics Box / Iteration Prompt 模板库 | 将前面所有库的决策组装成可复制的最终 Prompt | `libraries/` | 核心库 |
| 8 | `ai_music_customer_interaction_workflow_v0.1_bilingual.md` | 客户创作交互流程库 | 定义客户访谈流程、核心问题、可选追问、默认值和交互示例 | `libraries/` 或 `workflows/` | 核心流程 |
| 9 | `ai_music_library_orchestration_rules_v0.1_bilingual.md` | 素材库调用规则库 | 定义各素材库调用顺序、输入输出契约、内部 music_brief 对象和质量检查 | `libraries/` 或 `workflows/` | 核心流程 |

---

## 4. 历史版本 / Earlier Drafts

以下文件是早期版本或过渡版本，可以保留为参考，但正式 Skill 建议优先使用上面的核心版本。

| 文件名 | 说明 | 建议 |
|---|---|---|
| `ai_music_genre_library.md` | 曲风库早期版本 | 可归档 |
| `ai_music_use_case_structure_arrangement_mapping_v0.1.md` | 使用场景与结构 / 编曲映射库英文版早期版本 | 可归档，正式使用 v0.2 双语版 |

---

## 5. 各文件之间的关系 / File Dependency Map

```text
客户输入 / User Input
  ↓
ai_music_customer_interaction_workflow_v0.1_bilingual.md
客户访谈、需求采集、歌曲 / 器乐路由
  ↓
ai_music_library_orchestration_rules_v0.1_bilingual.md
决定素材库调用顺序，生成内部 music_brief
  ↓
素材库 / Libraries
  ├── ai_music_genre_library_v0.2.md
  ├── ai_music_rhythm_bpm_scene_mapping_v0.1.md
  ├── ai_music_vocal_voice_library_v0.1.md
  ├── ai_music_instrumentation_arrangement_library_v0.1.md
  ├── ai_music_emotion_expression_mapping_v0.1.md
  └── ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md
  ↓
ai_music_prompt_templates_v0.1_bilingual.md
组装 Style Prompt / Lyrics Box / Iteration Prompt
  ↓
最终输出 / Final Prompt Package
```

---

## 6. 推荐调用顺序 / Recommended Call Order

生成 Prompt 时，建议按以下顺序调用素材库：

```text
1. 客户创作交互流程库
   ai_music_customer_interaction_workflow_v0.1_bilingual.md

2. 素材库调用规则库
   ai_music_library_orchestration_rules_v0.1_bilingual.md

3. 使用场景、结构与编曲映射库
   ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md

4. 曲风库
   ai_music_genre_library_v0.2.md

5. 情绪与音乐表达映射库
   ai_music_emotion_expression_mapping_v0.1.md

6. 节奏 / BPM / 场景映射库
   ai_music_rhythm_bpm_scene_mapping_v0.1.md

7. 人声与嗓音描述库
   ai_music_vocal_voice_library_v0.1.md
   仅带人声歌曲调用；纯器乐跳过。

8. 乐器与编曲素材库
   ai_music_instrumentation_arrangement_library_v0.1.md

9. Style Prompt / Lyrics Box / Iteration Prompt 模板库
   ai_music_prompt_templates_v0.1_bilingual.md
```

---

## 7. 文件用途详解 / Detailed File Roles

### 7.1 `ai_music_customer_interaction_workflow_v0.1_bilingual.md`

**定位：客户交互层。**

它规定 Skill 如何和用户沟通，包括：

- 什么时候进入访谈模式
- 什么时候直接生成
- 第一轮 6 个核心问题
- 带歌词歌曲 / 纯器乐的路由
- 可选追问
- 需求摘要
- 默认值
- 特殊场景处理
- 对话示例

这个文件是未来 `SKILL.md` 的交互蓝图。

---

### 7.2 `ai_music_library_orchestration_rules_v0.1_bilingual.md`

**定位：素材库调度层。**

它规定 Skill 如何调用各类素材库，包括：

- 推荐调用顺序
- 每个库的输入输出契约
- `music_brief` 内部数据结构
- 带人声歌曲调用链
- 纯器乐调用链
- 缺失信息处理
- 冲突处理
- 输出前质量检查

这个文件是未来 `SKILL.md` 的执行蓝图。

---

### 7.3 `ai_music_genre_library_v0.2.md`

**定位：曲风知识库。**

它负责回答：

- 用户要什么曲风？
- 如果用户不知道曲风，应推荐哪些？
- 某个使用场景适合哪些曲风？
- 带人声歌曲和现代流行器乐分别有哪些风格？
- 如何用英文 Prompt 词表达细分曲风？

主要包含：

- Pop / Folk / Rock & Metal / R&B / Hip-hop / Electronic 等细分
- 现代流行器乐分类
- 场景到曲风推荐
- 年代风格增强器
- 曲风到 Prompt 关键词

---

### 7.4 `ai_music_rhythm_bpm_scene_mapping_v0.1.md`

**定位：节奏与速度库。**

它负责回答：

- 用户说“慢一点 / 燃一点 / 适合短视频”，应该是多少 BPM？
- 不同曲风常见 BPM 是多少？
- 不同场景需要什么律动？
- 纯器乐 BGM 是否需要稳定循环？

主要输出：

- BPM 范围
- Tempo 描述
- Groove 描述
- Rhythm Density
- 场景节奏建议

---

### 7.5 `ai_music_vocal_voice_library_v0.1.md`

**定位：人声与嗓音库。**

它只在带人声歌曲中调用。

它负责回答：

- 男声 / 女声 / 合唱 / 对唱如何表达？
- “温暖”“沙哑”“空灵”“成熟”“少年感”如何转成 Prompt？
- 不同曲风适合什么人声？
- 不同场景适合什么人声？

纯器乐场景下应跳过该库，并加入：

```text
instrumental only, no vocals, no rap, no spoken words
```

---

### 7.6 `ai_music_instrumentation_arrangement_library_v0.1.md`

**定位：乐器与编曲素材库。**

它负责回答：

- 某个曲风应使用哪些乐器？
- 某种情绪适合哪些乐器？
- 每种乐器在 Prompt 中如何表达？
- 带人声歌曲与纯器乐的编曲逻辑有什么不同？
- 如何从 Intro 到 Chorus / Climax 推进？

---

### 7.7 `ai_music_emotion_expression_mapping_v0.1.md`

**定位：情绪到音乐表达的转译库。**

它负责把用户说的情绪转成音乐行为。

例如：

```text
温暖但有点伤感
→ bittersweet, warm sadness, reflective, hopeful chorus
```

它不是简单翻译情绪词，而是进一步映射到：

- BPM
- 乐器
- 编曲密度
- 人声表达
- 制作质感
- 能量曲线
- 避免项

---

### 7.8 `ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md`

**定位：场景、结构与编曲决策库。**

它负责回答：

- 短视频应该什么结构？
- 品牌片应该怎么推进？
- 体育主题歌需要什么 chant 和群体副歌？
- 学习 BGM 如何保持不打扰？
- 每一段应该如何编曲？

它的关键特点是：**不只给段落标签，还给逐段编曲行为。**

---

### 7.9 `ai_music_prompt_templates_v0.1_bilingual.md`

**定位：最终 Prompt 组装层。**

它负责把前面所有库的决策组装成：

- Style Prompt
- Lyrics Box
- Custom Box
- Iteration Prompts
- Negative Prompt / Avoid
- 完整输出包

这是离最终用户最近的一层。

---

## 8. 未来需要补充的文件 / Future Files To Create

下一步建议生成以下文件：

| 文件名 | 用途 | 优先级 |
|---|---|---|
| `SKILL.md` | Skill 主文件，定义触发条件、工作流、库调用方式 | 最高 |
| `README.md` | 给人看的项目说明，包括安装、目录、使用方式 | 高 |
| `requirement_collection_checklist.md` | 需求采集检查清单 | 中 |
| `prompt_quality_checklist.md` | Prompt 输出质量检查清单 | 中 |
| `copyright_safety_checklist.md` | 版权与声音安全检查清单 | 中 |
| `vocal_song_example.md` | 带人声歌曲完整示例 | 中 |
| `instrumental_bgm_example.md` | 纯器乐 BGM 完整示例 | 中 |
| `short_video_hook_example.md` | 短视频 Hook 示例 | 中 |
| `brand_theme_song_example.md` | 品牌主题歌示例 | 中 |
| `sports_anthem_example.md` | 体育主题歌示例 | 中 |

---

## 9. 推荐下一步 / Recommended Next Step

建议下一步生成：

```text
SKILL.md
README.md
```

其中：

- `SKILL.md` 应尽量简洁，只写触发条件、核心流程、路由逻辑、库调用顺序和输出格式。
- 详细素材继续放在 `libraries/` 目录。
- `README.md` 面向人类使用者，解释这个 Skill 的目标、目录结构、用法和维护方式。

---

## 10. 版本说明 / Version Notes

当前索引版本：`v0.1`

当前已生成核心文件数量：9 个  
当前历史 / 过渡文件数量：2 个  
当前项目状态：素材库与交互流程基本完成，下一步可生成正式 `SKILL.md`。

