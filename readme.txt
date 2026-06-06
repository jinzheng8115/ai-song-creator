Interactive AI Music Prompt Skill
交互式 AI 音乐 Prompt Skill

1. What this project is
1. 这是什么项目

This project is a reusable skill project for generating structured prompts for AI music tools.
本项目是一个可复用的 skill 工程，用于为 AI 音乐工具生成结构化 Prompt。

It is designed for song creation, instrumental BGM creation, prompt optimization, lyric optimization, multi-version direction generation, and short music hook generation.
它适用于歌曲创作、纯器乐 BGM 创作、Prompt 优化、歌词优化、多版本方向生成，以及短音乐 Hook 生成。

The skill is not intended to behave like a generic songwriting chatbot.
这个 skill 不是为了做成一个泛化写歌聊天机器人。

Its goal is to turn vague user ideas into structured, controllable, copy-ready prompt packages.
它的目标是把用户模糊的创意需求转成结构化、可控、可直接复制使用的 Prompt 包。


2. Core design principles
2. 核心设计原则

- Ask only a few high-value questions.
- 只问少量高价值问题。

- Prefer structured choice interaction for fixed-answer questions.
- 固定答案题优先使用结构化选择。

- Default to a complete prompt package unless the user explicitly requests another output form.
- 除非用户明确要求其他输出形式，否则默认直接输出完整 Prompt 包。

- Use music library files as the real generation source, not only high-level summaries.
- 生成时必须真正使用音乐知识库文件，而不是只看高层摘要。

- Keep prompt payloads in English where needed, while keeping user-facing guidance in Chinese where appropriate.
- 在需要给工具直接使用的部分保持英文，同时在合适的位置为用户提供中文理解层。


3. Main skill capabilities
3. 主要能力

This skill currently supports these core modes:
当前 skill 支持以下核心模式：

- create_vocal_song
- create_instrumental_bgm
- optimize_existing_prompt
- optimize_existing_lyrics
- generate_multi_versions
- generate_short_video_hook


4. Output philosophy
4. 输出哲学

For vocal songs, the final package usually includes:
对于歌曲类输出，最终结果通常包括：

- Requirement Summary
- Music Direction
- Recommended Title Options
- Style Prompt
- Lyrics
- Iteration Directions
- Usage Notes

For instrumental music, the final package usually includes:
对于纯器乐输出，最终结果通常包括：

- Requirement Summary
- Music Direction
- Style Prompt
- Instrumental Structure Box
- Iteration Directions
- Usage Notes

Notes:
说明：

- Style Prompt should be readable and structured.
- Style Prompt 应尽量结构化、可读。

- Style Prompt should not use square-bracket tags.
- Style Prompt 不应使用方括号标签。

- Lyrics should carry structure and arrangement control when needed.
- 歌词模块在需要时应承载结构与编曲控制。

- Instrumental output should still include a structure-control box even without lyrics.
- 纯器乐即使没有歌词，也仍应包含结构控制框。


5. Library-driven generation
5. 基于知识库的生成

This skill depends on the ai_music_* library files in this folder.
这个 skill 依赖当前目录下的 ai_music_* 知识库文件。

Important controller-level files:
重要控制层文件：

- ai_music_customer_interaction_workflow_v0.1_bilingual.md
- ai_music_library_orchestration_rules_v0.1_bilingual.md

Important deep library files:
重要深层知识库文件：

- ai_music_genre_library_v0.2.md
- ai_music_rhythm_bpm_scene_mapping_v0.1.md
- ai_music_vocal_voice_library_v0.1.md
- ai_music_instrumentation_arrangement_library_v0.1.md
- ai_music_emotion_expression_mapping_v0.1.md
- ai_music_use_case_structure_arrangement_mapping_v0.2_bilingual.md
- ai_music_prompt_templates_v0.1_bilingual.md

These files are not decorative references.
这些文件不是装饰性的参考资料。

They are part of the actual generation system.
它们是实际生成系统的一部分。


6. Current interaction rules
6. 当前交互规则

- For broad themes like cities, seasons, family roles, or objects, the skill should ask what the user really wants to express.
- 对于“城市、季节、人物角色、物件”这类宽泛主题，skill 应追问用户真正想表达的角度。

- For music style, the skill should support direct choice, recommendation, and reference-based analysis.
- 在风格选择上，skill 应支持直接选择、系统推荐、参考对象分析三条路径。

- For instrumental music, duration strategy should be collected when it materially affects the result.
- 对于纯器乐，如果时长策略会明显影响结果，就应采集时长信息。

- For duet or multi-gender songs, role labels inside lyrics should use English, such as Male, Female, Group, or All.
- 对于对唱或多性别人声歌曲，歌词内的角色标签应使用英文，如 Male、Female、Group、All。


7. Folder structure
7. 目录结构

SKILL.md
Main skill definition and operating rules.
主 skill 定义与核心运行规则。

agents/openai.yaml
UI-facing skill metadata.
面向 UI 的 skill 元数据。

references/
Supporting rules and structured guidance files.
补充规则和结构化指导文件。

schema/
Schema files for clickable interaction design and related payload shapes.
点击交互设计及相关 payload 结构文件。

evals/
Evaluation prompts and test artifacts.
评测用例与测试产物。

docs/
Specs, plans, and supporting design documents.
规格、计划及相关设计文档。


8. Intended usage style
8. 推荐使用方式

This skill works best when the user gives:
这个 skill 在以下情况下效果最好：

- a theme
- a use case
- a target emotion
- a preferred style or reference direction

Examples:
例如：

- “Write a Chinese bossa nova song for summer.”
- “写一首适合夏天的中文 bossanova 歌曲。”

- “Create a healing instrumental BGM for bedtime relaxation.”
- “做一段适合睡前放松的疗愈纯音乐。”

- “Write a Shanghai urban rap song with male-female duet energy.”
- “写一首描写上海的都市 Rap，男女配合演唱。”


9. Important practical note
9. 重要实用说明

This skill is designed for iterative collaboration.
这个 skill 是为迭代协作设计的。

It should not only generate a result, but also help the user move toward a better next version.
它不应该只产出一个结果，还应帮助用户走向更好的下一版。


10. Status
10. 当前状态

This project has gone through multiple rounds of refinement.
本项目已经过多轮迭代优化。

The current version reflects the accepted interaction rules, output format rules, style-prompt rules, title-quality rules, and library-loading rules discussed during development.
当前版本已吸收开发过程中确认过的交互规则、输出格式规则、Style Prompt 规则、歌名质量规则，以及知识库加载规则。
