# Interactive AI Music Prompt Skill
# 交互式 AI 音乐 Prompt Skill

> Turn vague music ideas into structured, reusable AI music prompt packages.  
> 把模糊的音乐想法，转成结构清晰、可直接使用、可继续优化的 AI 音乐 Prompt 包。

---

## What it is / 这是什么

这是一个面向 AI 音乐创作场景的本地 skill，适合用于：

- 创作**带歌词歌曲 Prompt**
- 创作**纯器乐 / BGM Prompt**
- 优化已有**歌词**或**音乐 Prompt**
- 针对同一主题生成多个方向版本
- 把抽象情绪、场景、画面感翻译成更具体的音乐表达

适用对象包括但不限于：

- 用 Suno、Udio 或同类工具创作音乐的人
- 做短视频、Vlog、品牌内容、自媒体配乐的人
- 想把“一个想法”快速收敛成可执行 Prompt 的创作者

---

## Why this skill / 这个 skill 的特点

### 1. Not a long questionnaire / 不是冗长问卷
它不会一上来就抛十几个问题，而是优先根据你已经给出的信息直接收敛。

### 2. Better prompt structure / 输出结构更完整
默认直接输出**完整 Prompt 包**，而不是只给一段零散描述。

### 3. Song and BGM are handled differently / 歌曲与 BGM 分开处理
它会尽早区分：

- 带歌词歌曲
- 纯器乐 / BGM

两者会走不同的生成逻辑。

### 4. Style is easier to edit / 风格 Prompt 更易改
Style Prompt 采用结构化字段，而不是一整段难读的长句，更方便复制和微调。

### 5. Broad themes get clarified properly / 宽泛主题会被继续澄清
像“杭州”“夏天”“毕业”“父亲”这种主题，不会被草率脑补，而是会继续确认真正的表达角度。

---

## Repository contents / 仓库内容

这个仓库只保留**安装和运行 skill 所需的文件**，不包含内部设计稿、测试草稿和评测产物。

主要内容包括：

- `SKILL.md`：skill 主文件
- `agents/openai.yaml`：运行入口配置
- `references/`：交互、输出、语言、安全、运行时适配相关规则
- `ai_music_*.md`：核心音乐规则库与编排知识文件
- `readme.md`：使用说明

---

## Installation / 安装方式

这是一个**本地 Skill 文件夹**，推荐直接按目录安装。

### Minimum requirements / 最小要求

- 根目录存在 `SKILL.md`
- `SKILL.md` 引用到的文件要完整保留
- 你的宿主环境支持加载本地 skill

### Recommended steps / 推荐安装步骤

1. 把整个 skill 文件夹放入你的本地 skills 目录
2. 保持目录结构不变
3. 确保以下内容都在：
   - `SKILL.md`
   - `agents/openai.yaml`
   - `references/`
   - 相关 `ai_music_*.md` 规则文件
4. 重启或刷新你的 skill 运行环境

---

## Quick Start / 快速开始

安装完成后，可以直接像聊天一样调用它。

### Example prompts / 示例输入

#### Song / 歌曲
- 创作一首中文流行歌曲，主题是毕业，温暖怀旧，但最后有一点希望感
- 写一首中文 bossanova 歌曲，在炎炎夏日来一点舒爽的感觉
- 创作一首描写上海夜生活的中文 Rap，男女对唱，对话感更强

#### Instrumental / 纯器乐
- 创作一段疗愈的轻音乐，适合睡前放松，60–90 秒，循环优先
- 做一段适合盛夏咖啡馆的爵士钢琴，清新舒爽
- 做一段科技产品发布会用的高级感 BGM，30–60 秒，旁白友好

#### Optimization / 优化
- 帮我优化这段歌词，让副歌更抓耳
- 帮我把这段音乐 Prompt 改得更适合短视频传播

---

## Recommended input pattern / 推荐输入方式

如果你希望更快得到高质量结果，推荐直接按下面几类句式输入。

### 1. Song creation / 歌曲创作
- 写一首【语言】的【风格】歌曲，主题是【主题】，想表达【内容 / 情绪】，适合【场景】

例如：
- 写一首中文流行歌曲，主题是毕业，想表达温暖怀旧但最后有一点希望感，适合发短视频和朋友圈

### 2. Instrumental / BGM
- 创作一段【风格】的纯音乐，给人【感受】，适合【场景】，时长【长度】，优先【循环 / 剪辑】

例如：
- 创作一段疗愈的轻音乐，给人慢慢放松下来的感觉，适合睡前聆听，时长 60–90 秒，优先循环

### 3. Existing content optimization / 优化已有内容
- 这是我现在的【歌词 / Prompt】，我希望它变得更【目标】

例如：
- 这是我现在的歌词，我希望副歌更抓耳、更适合传播，男女对唱更明显

### 4. Reference-driven style direction / 参考风格方向
- 我想做一首【类型】，我喜欢【某首歌 / 某位歌手】那种【风格特征】，但不要直接模仿

例如：
- 我想做一首世界杯主题歌，我喜欢《意大利之夏》那种大开阔、史诗感、希望感很强的方向，但不要直接模仿

---

## Default output / 默认输出内容

### For songs / 歌曲类
默认通常会输出：

- 需求摘要
- 音乐方向
- 推荐歌名
- Style Prompt
- Lyrics
- 下一步优化方向
- 使用建议

### For instrumental tracks / 纯器乐类
默认通常会输出：

- 需求摘要
- 音乐方向
- Style Prompt
- Instrumental Structure Box
- 下一步优化方向
- 使用建议

默认直接输出**完整 Prompt 包**。
除非你明确要求简洁版、多版本、只要歌词等特殊形式，否则不会额外追问输出格式。

---

## Output style / 输出风格特点

### Structured Style Prompt / 结构化风格 Prompt

```text
Genre: Chinese folk, urban narrative folk
Mood: gentle, nostalgic, relaxed
Vocal: natural sincere male lead
Tempo: mid-slow, steady storytelling pace
Texture: acoustic guitar, light percussion, soft bass
Energy: calm entrance, gradual unfolding, soft return
Hook: natural and memorable chorus
Use Case: personal sharing / city memory expression
```

### Lyrics carry arrangement cues / 歌词区会带结构与编曲控制

```text
[Verse 1 - acoustic guitar, close vocal]
...

[Chorus - fuller harmony, stronger lift]
...
```

### Instrumentals also get structure control / 纯器乐也有结构控制

纯器乐不会只给一个风格词，而会额外输出 `Instrumental Structure Box`，用于控制：

- 时长
- 段落推进
- 循环方式
- 剪辑点
- 结构变化

---

## When the theme is too broad / 当主题过宽时

如果你只给一个大主题，例如：

- 杭州
- 上海
- 夏天
- 父亲
- 校园

skill 通常会继续确认：

- 你真正想表达什么？
- 是城市气质、个人记忆、爱情相遇、漂泊感，还是治愈和停留？

这样生成出来的结果会更贴近你的真实意图，而不是停留在表面。

---

## What it does not do / 它不会做什么

这个 skill 不会：

- 直接模仿真实歌手或现有歌曲
- 输出复制型“像某某一样”的 Prompt
- 把音乐创作变成死板流程化问卷

如果你给了歌手或作品参考，它会提炼：

- 风格特征
- 情绪方向
- 编曲质感
- 演唱气质

而不会直接模仿。

---

## Common bad inputs / 常见错误输入

### Too broad / 主题太宽
- 杭州
- 夏天
- 父亲

更好的写法：
- 写一首关于杭州的民谣，想表达一个人在这座城里慢慢生活下来的感觉

### Only style, no content / 只有风格，没有内容
- 来一首 Rap
- 做一段民谣

更好的写法：
- 写一首描写上海夜色与都市节奏的中文 Rap

### No use case / 只有情绪，没有场景
- 做一段疗愈的轻音乐

更好的写法：
- 做一段疗愈的轻音乐，适合睡前放松，循环播放

### Direct artist imitation request / 直接要求模仿歌手
- 写一首像 Beyond 那样的歌

更好的写法：
- 想要真诚热血、乐队感强、理想主义气质的励志摇滚歌

### No duration for BGM / BGM 没有时长
- 做一段科技感 BGM

更好的写法：
- 做一段科技感 BGM，适合产品发布视频，30–60 秒，旁白友好

---

## Runtime behavior / 运行时交互说明

如果宿主运行时支持结构化提问 / 点击式选择，这个 skill 会优先使用选择式交互。  
如果运行时暂时不支持，也可以退回到简短文本选项交互。

---

## License / 许可

当前仓库未附带单独 LICENSE 文件。  
如需开源发布规范化，可后续补充 MIT / Apache-2.0 / 自定义许可说明。
