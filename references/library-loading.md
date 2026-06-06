# Library Loading Rules
# 知识库加载规则

## Purpose / 目的

This file explains which music knowledge files to load for which kind of task.
本文说明不同任务应加载哪些音乐知识文件。

## Controller-level starting point / 控制层起点

Always start with:
始终先从以下文件开始：

- `ai_music_customer_interaction_workflow_v0.1_bilingual.md`
- `ai_music_library_orchestration_rules_v0.1_bilingual.md`

These two files define the top-level workflow and library orchestration logic.
这两个文件定义了顶层工作流和知识库编排逻辑。

## Deep library files / 深层知识库文件

Load only what is needed:
按需加载：

- `ai_music_genre_library_v0.2.md`
- `ai_music_rhythm_bpm_scene_mapping_v0.1.md`
- `ai_music_vocal_voice_library_v0.1.md`
- `ai_music_instrumentation_arrangement_library_v0.1.md`
- `ai_music_emotion_expression_mapping_v0.1.md`
- `ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md`
- `ai_music_prompt_templates_v0.1_bilingual.md`

## Default call chain for vocal songs / 歌曲默认调用链

For most lyric-based song requests:
对于大多数带歌词歌曲请求：

1. controller workflow / 控制层工作流
2. orchestration rules / 编排规则
3. genre library / 曲风库
4. emotion mapping / 情绪映射
5. vocal voice library / 人声库
6. use-case structure mapping / 场景结构映射
7. prompt templates / Prompt 模板

Add rhythm/BPM or instrumentation references only when they materially improve the result.
只有在确实能提升结果时，才额外加载节奏/BPM 或配器参考。

## Default call chain for instrumental BGM / 器乐默认调用链

For most instrumental or BGM requests:
对于大多数纯器乐或 BGM 请求：

1. controller workflow / 控制层工作流
2. orchestration rules / 编排规则
3. genre library / 曲风库
4. rhythm/BPM scene mapping / 节奏 BPM 场景映射
5. instrumentation library / 配器库
6. emotion mapping / 情绪映射
7. prompt templates / Prompt 模板

## Selection hints / 选择提示

Load the vocal voice library when:
以下情况加载人声库：

- lead vocal identity matters / 主唱身份重要
- delivery style matters / 唱法重要
- chorus or duet decisions matter / 合唱或对唱决策重要

Load the instrumentation library when:
以下情况加载配器库：

- main texture matters / 主要质感重要
- instrument-led imagery matters / 乐器主导的画面感重要
- arrangement density matters / 编排密度重要

Load rhythm/BPM mapping when:
以下情况加载节奏/BPM 映射：

- scene pacing matters / 场景节奏重要
- edit-friendliness matters / 剪辑友好度重要
- short-video timing matters / 短视频时长节奏重要
- duration control matters / 时长控制重要
