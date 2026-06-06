# AI Music Use Case, Song Structure & Arrangement Mapping Library v0.2  
# AI 音乐使用场景、歌曲结构与编曲映射库 v0.2

> Purpose / 用途：  
> This library helps an interactive AI music prompt skill translate a user's use case into a concrete song or instrumental structure, with arrangement instructions for each section.  
> 本库用于帮助交互式 AI 音乐 Prompt Skill，把用户的“使用场景”转化为具体的歌曲结构、器乐结构和逐段编曲策略。
>
> This is not only a song-structure library. It is a **scene-driven structure + arrangement decision library**.  
> 它不是单纯的“歌曲段落结构库”，而是一个 **基于使用场景的结构 + 编曲决策库**。
>
> It supports both / 支持两类生成任务：
>
> 1. vocal songs with lyrics / 带歌词、带人声的歌曲  
> 2. modern instrumental music / background music / 现代流行器乐、背景音乐、BGM

---

## 1. Core Design Logic / 核心设计逻辑

Users usually do not know how to describe music structure. They describe the use case instead.  
普通用户通常不会说“我要 Verse-Chorus-Bridge 结构”，他们更常说的是使用场景。

Examples / 用户常见说法：

- “I want a short-video song.” / “我想做一首短视频歌曲。”
- “I want a brand theme song.” / “我想做一首品牌主题歌。”
- “I want World Cup-style music.” / “我想做一首世界杯感觉的歌。”
- “I want background music for a tech product video.” / “我想做一段科技产品宣传片背景音乐。”
- “I want study BGM.” / “我想做学习 BGM。”
- “I want a personal song for social sharing.” / “我想做一首适合朋友圈分享的个人歌曲。”

The skill should translate the use case into the following fields:  
Skill 应该把用户场景转译成以下字段：

```text
Track Type / 音乐类型
Recommended Length / 推荐时长
Hook Placement / Hook 出现位置
Song or Track Structure / 歌曲或器乐结构
Section-by-Section Arrangement Plan / 逐段编曲计划
Energy Curve / 能量曲线
Vocal or Instrumental Strategy / 人声或器乐策略
Best Genres / 推荐曲风
Best BPM Range / 推荐 BPM 范围
Prompt Keywords / Prompt 关键词
Avoid / Negative Prompt / 避免项 / 反向提示词
```

Key rule / 核心规则：

```text
Do not output section tags alone. Always combine structure with arrangement behavior.
不要只输出段落标签。必须把结构标签和每段编曲行为一起输出。
```

Weak output / 较弱输出：

```text
[Intro]
[Verse]
[Chorus]
[Bridge]
[Final Chorus]
[Outro]
```

Better output / 更好的输出：

```text
[Intro - soft piano motif and ambient pad, intimate mood / 柔和钢琴动机与氛围铺底，建立亲密情绪]
[Verse 1 - sparse piano and acoustic guitar, close emotional vocal / 稀疏钢琴与原声吉他，突出贴耳情绪人声]
[Pre-Chorus - add light drums, warm bass, and subtle rising strings / 加入轻鼓、温暖贝斯和逐渐上行的弦乐]
[Chorus - full drums, bass, strings, memorable emotional hook / 鼓、贝斯、弦乐打开，形成有记忆点的情绪 Hook]
[Bridge - breakdown to piano and vocal only / 降低密度，只保留钢琴与人声形成转折]
[Final Chorus - wider strings, stronger drums, backing vocals / 弦乐更宽、鼓组更强，加入和声]
[Outro - return to the piano motif, warm resolved ending / 回到钢琴动机，温暖收束]
```

---

## 2. Vocal Song vs Instrumental Routing / 带人声歌曲与纯器乐路由

Before selecting a structure, the skill should identify the track type.  
在选择结构之前，Skill 必须先判断用户要的是“带人声歌曲”还是“纯器乐 / 背景音乐”。

### 2.1 Vocal Song / 带人声歌曲

Use when the user wants / 适用于：

- a complete song / 完整歌曲
- lyrics / 歌词
- a theme song / 主题歌
- a personal song / 个人歌曲
- a brand song / 品牌歌曲
- a graduation song / 毕业歌曲
- a wedding song / 婚礼歌曲
- a sports anthem with vocals / 带人声的体育主题曲
- a short-video hook song with singing / 带演唱 Hook 的短视频歌曲

Main control fields / 核心控制字段：

```text
lyrics / 歌词
vocal style / 人声风格
hook / Hook
chorus / 副歌
section tags / 段落标签
emotional arc / 情绪弧线
arrangement build / 编曲推进
```

### 2.2 Modern Instrumental Track / 现代流行器乐

Use when the user wants / 适用于：

- background music / 背景音乐
- BGM / BGM
- study music / 学习音乐
- work music / 工作音乐
- product video music / 产品视频音乐
- brand film background / 品牌片背景音乐
- Vlog music / Vlog 音乐
- sports highlight instrumental / 体育高光器乐
- podcast intro / 播客片头
- logo sting / 品牌音效短片
- instrumental only music / 纯器乐音乐

Main control fields / 核心控制字段：

```text
instrumental only / 纯器乐
no vocals / 无人声
main motif / 主动机
groove / 律动
texture / 质感
arrangement variation / 编曲变化
loopability / 可循环性
background usability / 背景可用性
```

Fixed negative prompt when instrumental / 纯器乐固定反向提示：

```text
instrumental only, no vocals, no rap, no spoken words, no lead singing
纯器乐，无人声，无说唱，无旁白，无主唱
```

---

## 3. Section Function Dictionary / 段落功能字典

### 3.1 Vocal Song Sections / 带人声歌曲段落

| Section Tag / 段落标签 | Lyric Function / 歌词功能 | Arrangement Function / 编曲功能 | Common Arrangement Moves / 常见编曲做法 |
|---|---|---|---|
| [Intro] / 前奏 | Set mood before lyrics / 歌词进入前建立氛围 | Establish sound world or motif / 建立音色世界或主动机 | piano motif, guitar riff, synth pad, chant, drum pickup / 钢琴动机、吉他 riff、合成器铺底、chant、鼓进入 |
| [Verse] / 主歌 | Storytelling and setup / 叙事与铺垫 | Keep arrangement restrained, leave room for lyrics / 编曲克制，为歌词和人声留空间 | sparse piano/guitar, minimal drums, close vocal / 稀疏钢琴或吉他、少量鼓、贴耳人声 |
| [Verse 1] / 第一段主歌 | First scene / emotional setup / 第一个场景与情绪设定 | Lowest or low-medium density / 最低或较低密度 | soft chords, light texture / 柔和和弦、轻质感 |
| [Verse 2] / 第二段主歌 | Continue or deepen story / 延续或深化故事 | Slightly more movement than Verse 1 / 比第一段多一点律动 | add bass, light drums, harmonies, fills / 加贝斯、轻鼓、和声或装饰音 |
| [Pre-Chorus] / 副歌前段 | Build tension before chorus / 副歌前制造张力 | Increase energy and expectation / 增加能量与期待 | add drums, bass, rising strings, riser, harmony lift / 加鼓、贝斯、上行弦乐、riser、和声抬升 |
| [Chorus] / 副歌 | Core message and hook / 核心表达与 Hook | Open arrangement, higher energy / 编曲打开，能量提高 | full drums, bass, strings, backing vocals, strong melody / 完整鼓组、贝斯、弦乐、和声、强旋律 |
| [Post-Chorus] / 副歌后段 | Extend hook after chorus / 延续副歌 Hook | Reinforce motif or chant / 强化动机或口号 | synth hook, vocal chop, repeated phrase, instrumental hook / 合成器 Hook、人声切片、重复短句、器乐 Hook |
| [Hook] / 抓耳段 | Catchiest phrase or riff / 最抓耳的短句或 riff | Immediate attention-grabber / 直接抓住注意力 | vocal hook, signature riff, beat already present / 人声 Hook、标志性 riff、节奏直接进入 |
| [Refrain] / 叠句 | Repeated lyrical or melodic idea / 重复歌词或旋律想法 | Light repetition, memory anchor / 轻重复，形成记忆锚点 | short recurring phrase / 反复出现的短句 |
| [Bridge] / 桥段 | Contrast / turning point / 对比与转折 | Change texture, harmony, or density / 改变音色、和声或密度 | breakdown, new chords, stripped section, key lift / breakdown、新和弦、减法编曲、升调 |
| [Breakdown] / 减法段 | Reduce energy for contrast / 降低能量形成对比 | Remove drums or reduce layers / 移除鼓或减少层次 | vocal + piano, pads only, bass drop-out / 人声 + 钢琴、只留 pad、贝斯退出 |
| [Instrumental Break] / 器乐间奏 | Non-lyrical musical section / 无歌词音乐段 | Showcase motif or instrumental color / 展示动机或乐器色彩 | guitar solo, sax solo, synth lead, string interlude / 吉他 solo、萨克斯 solo、合成器 lead、弦乐间奏 |
| [Solo] / 独奏 | Instrumental feature / 乐器展示 | Adds personality and style / 增加个性与风格 | guitar solo, sax solo, piano solo, synth solo / 吉他、萨克斯、钢琴、合成器独奏 |
| [Final Chorus] / 最后副歌 | Final emotional release / 最终情绪释放 | Highest density and widest mix / 最大编曲密度与最宽声场 | full band, choir, ad-libs, bigger drums / 全乐队、合唱、即兴、鼓组加强 |
| [Outro] / 尾奏 | Close the song / 收尾 | Resolve or fade / 解决或淡出 | solo piano ending, final hook repeat, fade out, final hit / 钢琴收尾、Hook 重复、淡出、最终重击 |
| [Chant] / 口号齐唱 | Crowd / group phrase / 群体口号 | Creates collective energy / 制造集体感 | stadium chant, claps, drums / 体育场 chant、拍手、鼓 |
| [Group Vocal] / 群体人声 | Collective singing / 群体演唱 | Adds scale and unity / 增加规模感与团结感 | choir, backing vocals, crowd vocals / 合唱、和声、观众人声 |
| [Spoken Word] / 旁白式段落 | Narration or poetic line / 叙事或诗性表达 | Creates intimacy or documentary feel / 建立亲密感或纪录片感 | soft pad, minimal piano underneath / 柔和 pad、极简钢琴铺底 |

---

### 3.2 Instrumental Sections / 器乐段落

| Section Tag / 段落标签 | Musical Function / 音乐功能 | Common Arrangement Moves / 常见编曲做法 |
|---|---|---|
| [Intro] / 引入 | Establish texture and motif / 建立质感与动机 | filtered synth, soft piano, guitar motif, ambience / 滤波合成器、柔和钢琴、吉他动机、氛围声 |
| [Main Theme] / 主主题 | Present main melodic idea / 呈现主旋律想法 | lead piano/guitar/synth motif, clear rhythm / 钢琴、吉他或合成器主旋律，清晰节奏 |
| [Main Loop] / 主循环 | Stable background groove / 稳定背景律动 | drums, bass, chord loop, subtle motif / 鼓、贝斯、和弦循环、轻动机 |
| [Variation] / 变奏 | Keep repetition interesting / 让重复保持变化 | add percussion, counter-melody, small fills / 加打击乐、对位旋律、小装饰 |
| [Subtle Variation] / 细微变奏 | Non-intrusive development / 不打扰的推进 | texture change, light arpeggio, background pads / 质感变化、轻琶音、背景 pad |
| [Breakdown] / 减法段 | Reduce energy / 降低能量 | remove drums, leave pads/motif / 去掉鼓，只留 pad 或动机 |
| [Build-Up] / 推进段 | Increase tension / 增加张力 | riser, snare roll, added layers, filter opening / riser、军鼓滚奏、加层、滤波打开 |
| [Climax] / 高潮 | Highest energy / emotional payoff / 最高能量或情绪释放 | full drums, bass, strings, lead melody / 完整鼓、贝斯、弦乐、主旋律 |
| [Drop] / Drop 段 | Electronic energy release / 电子音乐能量释放 | full beat, bass drop, synth lead / 完整节拍、低频 drop、合成器 lead |
| [Final Impact] / 最终冲击 | Last strong hit / 最后一击 | final downbeat, cymbal crash, orchestral hit / 最后重拍、镲片、管弦打击 |
| [Loop Ending] / 循环结尾 | Seamless repeat / 无缝循环 | return to main motif, no hard resolution / 回到主动机，不做强终止 |
| [Logo Hit] / Logo 收束 | Brand ending / 品牌结尾 | short resolved final note or impact / 短促、明确、可识别的终止音或音效 |
| [Outro] / 尾奏 | Close or fade / 结束或淡出 | fade, soft ending, final motif / 淡出、柔和结束、最后动机 |

---

### 3.3 Electronic Music Sections / 电子音乐段落

| Section Tag / 段落标签 | Function / 功能 | Arrangement Strategy / 编曲策略 |
|---|---|---|
| [Ambient Intro] / 氛围前奏 | Set atmosphere / 建立氛围 | pads, texture, filtered drums / pad、质感、滤波鼓 |
| [Groove] / 律动段 | Establish rhythm / 建立律动 | kick, bassline, percussion / 底鼓、贝斯线、打击乐 |
| [Build-Up] / 推进段 | Prepare drop / 为 drop 做准备 | riser, snare roll, filter sweep / riser、军鼓滚奏、滤波扫频 |
| [Drop] / Drop 段 | Energy release / 能量释放 | full beat, bass, lead synth / 完整节拍、贝斯、合成器 lead |
| [Breakdown] / 减法段 | Reset energy / 重置能量 | remove drums, pads/chords / 移除鼓，只留 pad 或和弦 |
| [Second Build] / 第二推进 | Rebuild tension / 重新建立张力 | stronger riser, more layers / 更强 riser，更多层次 |
| [Final Drop] / 最后 Drop | Biggest release / 最大释放 | fuller drums, wider synths / 更完整鼓组、更宽合成器 |
| [Outro] / 尾奏 | DJ-friendly or fade ending / 适合 DJ 或淡出结尾 | reduce layers, keep pulse / 减少层次，保留律动 |

---

### 3.4 Sports / Chant Sections / 体育与口号式段落

| Section Tag / 段落标签 | Function / 功能 | Arrangement Strategy / 编曲策略 |
|---|---|---|
| [Intro - Stadium Chant] / 体育场口号前奏 | Immediate identity / 立即建立识别度 | crowd chant, claps, drums / 观众 chant、拍手、鼓 |
| [Verse - Percussion Groove] / 打击乐律动主歌 | Rhythmic vocal setup / 建立节奏型演唱 | drums, bass, guitar/brass support / 鼓、贝斯、吉他或铜管支撑 |
| [Pre-Chorus - Rising Crowd] / 群体抬升段 | Build anticipation / 制造期待 | snare build, brass stabs, group shouts / 军鼓推进、铜管点缀、群体喊声 |
| [Chorus - Group Vocal] / 群体副歌 | Crowd-singing hook / 适合合唱的 Hook | choir, chants, full drums / 合唱、chant、完整鼓组 |
| [Post-Chorus - Chant Hook] / 口号式副歌后段 | Repeatable chant / 可重复口号 | wordless hook, crowd call-response / 无词 Hook、观众 call-response |
| [Bridge - Clap Breakdown] / 拍手减法桥段 | Participation moment / 参与感段落 | claps, drums, vocal call-response / 拍手、鼓、人声呼应 |
| [Final Chorus - Crowd Chant] / 观众最终副歌 | Biggest collective release / 最大群体释放 | choir, brass, percussion, crowd / 合唱、铜管、打击乐、人群声 |
| [Outro - Final Chant] / 最终口号尾奏 | Memorable ending / 记忆点收尾 | final phrase, drum hit / 最后短句、鼓点收束 |

---

## 4. Field Schema for Each Use Case / 每个使用场景的字段模板

Every use case template should use this schema:  
每个场景模板建议统一使用以下字段：

```text
Use Case ID / 场景 ID:
Chinese Name / 中文名称:
Track Type / 音乐类型:
Recommended Length / 推荐时长:
Hook Placement / Hook 出现位置:
Lyrics Density / 歌词密度:
Energy Curve / 能量曲线:
Recommended Structure / 推荐结构:
Arrangement Plan / 编曲计划:
  - Intro / 前奏:
  - Verse / Main Section / 主歌 / 主段落:
  - Pre-Chorus / Build / 副歌前段 / 推进:
  - Chorus / Climax / 副歌 / 高潮:
  - Bridge / Breakdown / 桥段 / 减法段:
  - Final Section / 最终段落:
  - Outro / 尾奏:
Vocal Strategy / 人声策略:
Instrumental Strategy / 器乐策略:
Best Genres / 推荐曲风:
Best BPM Range / 推荐 BPM:
Prompt Keywords / Prompt 关键词:
Negative Prompt / Avoid / 反向提示词 / 避免项:
Example Structure Prompt / 示例结构 Prompt:
```

---

## 5. Vocal Song Use-Case Templates / 带人声歌曲场景模板

### 5.1 Short Video Hook Song / 短视频 Hook 歌曲

- Use Case ID / 场景 ID: `short_video_hook_song`
- Chinese Name / 中文名称: 短视频 Hook 歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 20–45 seconds / 20–45 秒
- Hook Placement / Hook 出现位置: first 3–8 seconds / 前 3–8 秒
- Lyrics Density / 歌词密度: low to medium; short, memorable phrases / 中低密度，短句、易记
- Energy Curve / 能量曲线: immediate hook → catchy chorus → loop-friendly ending / 立即进入 Hook → 抓耳副歌 → 可循环结尾
- Best Genres / 推荐曲风: modern pop, dance-pop, electro-pop, trap pop, folk-pop, pop-rock / 现代流行、舞曲流行、电子流行、Trap Pop、民谣流行、流行摇滚
- Best BPM Range / 推荐 BPM: 105–135 BPM

Recommended Structure / 推荐结构：

```text
[Hook] / 抓耳段
[Verse] / 主歌
[Chorus] / 副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: usually no long intro; start with vocal hook, signature riff, or beat. / 通常不要长前奏；直接用人声 Hook、标志性 riff 或节奏开场。
- Hook / 抓耳段: catchiest vocal phrase appears immediately; rhythm already present. / 最抓耳的人声短句立即出现，节奏已经进入。
- Verse / 主歌: 2–4 short lines; keep beat light but moving. / 2–4 句短歌词，节奏轻但保持推进。
- Chorus / 副歌: full beat, bright chords, layered vocal, repeatable hook. / 完整节拍、明亮和弦、叠加人声、可重复 Hook。
- Outro / 尾奏: quick loop-friendly ending, repeat hook phrase or leave open cadence. / 快速可循环结尾，重复 Hook 短句或留下开放式收束。

Vocal Strategy / 人声策略：

```text
clear vocal, catchy delivery, strong melodic hook, youthful or natural tone
清晰人声，抓耳唱法，强旋律 Hook，年轻或自然的音色
```

Instrumental Strategy / 器乐策略：

```text
short intro, active beat, simple chord loop, bright production
短前奏，节奏直接，简单和弦循环，明亮制作
```

Prompt Keywords / Prompt 关键词：

```text
short intro, hook arrives immediately, catchy chorus, loop-friendly, suitable for short video, memorable phrase
短前奏，Hook 立即出现，抓耳副歌，可循环，适合短视频，记忆点短句
```

Avoid / 避免：

```text
long intro, slow build, complex verse, hook after 30 seconds, too many lyrics
长前奏，慢铺垫，复杂主歌，30 秒后才出现 Hook，歌词过多
```

Example Structure Prompt / 示例结构 Prompt：

```text
[Hook - start immediately with the catchiest vocal phrase and a light beat / 直接以最抓耳的人声短句和轻节奏开场]
[Verse - short 2-line setup, minimal but moving rhythm / 两句短铺垫，节奏简洁但有推进]
[Chorus - full beat, bright chords, layered vocals, repeatable hook / 完整节拍、明亮和弦、叠加人声、可重复 Hook]
[Outro - loop-friendly ending with the hook phrase / 用 Hook 短句形成可循环结尾]
```

---

### 5.2 Personal Story Song / 朋友圈 / 个人故事歌

- Use Case ID / 场景 ID: `personal_story_song`
- Chinese Name / 中文名称: 朋友圈 / 个人故事歌
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 1:30–3:00
- Hook Placement / Hook 出现位置: chorus within 35–50 seconds / 副歌在 35–50 秒内出现
- Lyrics Density / 歌词密度: medium; concrete images and emotional lines / 中等密度，有具体画面和情绪句
- Energy Curve / 能量曲线: quiet reflection → emotional release → warm ending / 安静回忆 → 情绪释放 → 温暖收束
- Best Genres / 推荐曲风: Chinese pop ballad, folk-pop, acoustic folk, soft rock, cinematic pop / 中文流行抒情、民谣流行、原声民谣、软摇滚、电影感流行
- Best BPM Range / 推荐 BPM: 70–100 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse 1] / 第一段主歌
[Pre-Chorus] / 副歌前段
[Chorus] / 副歌
[Verse 2] / 第二段主歌
[Bridge] / 桥段
[Final Chorus] / 最后副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: soft piano or acoustic guitar motif; intimate and warm. / 柔和钢琴或原声吉他动机，亲密、温暖。
- Verse 1 / 第一段主歌: sparse piano/guitar, close emotional vocal, minimal percussion. / 稀疏钢琴或吉他，贴耳情绪人声，极少打击乐。
- Pre-Chorus / 副歌前段: add light drums, bass warmth, subtle string rise. / 加入轻鼓、温暖贝斯和轻微上行弦乐。
- Chorus / 副歌: full but not too loud; drums, bass, strings, memorable emotional hook. / 编曲打开但不过分吵，鼓、贝斯、弦乐和有记忆点的情绪 Hook。
- Verse 2 / 第二段主歌: bring back groove from chorus, add small fills or harmonies. / 保留副歌后的律动，加入小装饰音或和声。
- Bridge / 桥段: breakdown to piano and vocal only; lyrical reflection. / 降低密度，只留钢琴和人声，进行情绪反思。
- Final Chorus / 最后副歌: wider strings, stronger drums, optional backing vocals. / 弦乐更宽、鼓更强，可加入和声。
- Outro / 尾奏: return to piano/guitar motif, warm resolved ending. / 回到钢琴或吉他动机，温暖解决。

Vocal Strategy / 人声策略：

```text
natural emotional vocal, warm male vocal, soft female vocal, mature storytelling delivery
自然情绪人声，温暖男声，柔和女声，成熟叙事唱法
```

Instrumental Strategy / 器乐策略：

```text
piano, acoustic guitar, soft drums, warm bass, gentle strings
钢琴，原声吉他，柔和鼓组，温暖贝斯，轻柔弦乐
```

Prompt Keywords / Prompt 关键词：

```text
intimate verse, emotional chorus, warm ending, personal storytelling, natural vocal
亲密主歌，情绪副歌，温暖结尾，个人叙事，自然人声
```

Avoid / 避免：

```text
overly commercial energy, aggressive drums, abstract slogans, crowded arrangement
过度商业化能量，侵略性鼓组，抽象口号，拥挤编曲
```

---

### 5.3 Brand Theme Song / 品牌主题歌

- Use Case ID / 场景 ID: `brand_theme_song`
- Chinese Name / 中文名称: 品牌主题歌
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 1:00–2:30
- Hook Placement / Hook 出现位置: chorus within 30–45 seconds / 副歌在 30–45 秒内出现
- Lyrics Density / 歌词密度: medium-low; brand idea should sound natural, not slogan-heavy / 中低密度，品牌理念要自然，不要口号堆砌
- Energy Curve / 能量曲线: confident intro → inspiring chorus → memorable ending / 自信开场 → 鼓舞副歌 → 有记忆点收尾
- Best Genres / 推荐曲风: cinematic pop, modern pop, electronic pop, corporate pop, pop-rock / 电影感流行、现代流行、电子流行、企业流行、流行摇滚
- Best BPM Range / 推荐 BPM: 95–125 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse] / 主歌
[Pre-Chorus] / 副歌前段
[Chorus] / 副歌
[Bridge] / 桥段
[Final Chorus] / 最后副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: clean motif that can become brand identity; piano, guitar, or synth. / 干净且可品牌化的动机，可用钢琴、吉他或合成器。
- Verse / 主歌: clear vocal, light rhythm, lyrics introduce brand emotion or user story. / 清晰人声、轻节奏，歌词引入品牌情绪或用户故事。
- Pre-Chorus / 副歌前段: add drums and rising harmony to create optimism. / 加鼓和上行和声，制造积极感。
- Chorus / 副歌: polished full arrangement, memorable brand-friendly hook. / 精致完整编曲，形成适合品牌传播的记忆 Hook。
- Bridge / 桥段: short contrast; can reduce to piano/synth before final lift. / 短暂对比，可降到钢琴或合成器，为最后抬升做准备。
- Final Chorus / 最后副歌: bigger backing vocals, wider mix, stronger rhythm. / 更大的和声、更宽声场、更强节奏。
- Outro / 尾奏: resolved ending with repeatable phrase or logo-friendly final note. / 用可重复短句或适合 Logo 的终止音收束。

Vocal Strategy / 人声策略：

```text
clean modern vocal, confident but natural delivery, uplifting backing vocals
干净现代人声，自信但自然的演唱，积极和声
```

Instrumental Strategy / 器乐策略：

```text
polished drums, piano, subtle synths, guitars, strings depending on brand tone
精致鼓组、钢琴、轻合成器、吉他、弦乐，按品牌调性调整
```

Prompt Keywords / Prompt 关键词：

```text
uplifting, brandable hook, polished production, inspiring chorus, clean modern sound
振奋，品牌化 Hook，精致制作，鼓舞副歌，干净现代声音
```

Avoid / 避免：

```text
too sad, too dark, too many corporate slogans, unresolved ending
过度伤感，过暗，企业口号过多，结尾不解决
```

---

### 5.4 Corporate / Annual Event Song / 企业宣传 / 年会歌曲

- Use Case ID / 场景 ID: `corporate_annual_event_song`
- Chinese Name / 中文名称: 企业宣传 / 年会歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 1:30–3:00
- Hook Placement / Hook 出现位置: chorus within 40 seconds / 副歌 40 秒内出现
- Lyrics Density / 歌词密度: medium-low; simple, positive, collective / 中低密度，简单、积极、有集体感
- Energy Curve / 能量曲线: positive opening → group chorus → celebratory ending / 积极开场 → 群体副歌 → 庆祝式结尾
- Best Genres / 推荐曲风: corporate pop, pop-rock, uplifting pop, stadium-lite anthem / 企业流行、流行摇滚、振奋流行、轻体育场式主题歌
- Best BPM Range / 推荐 BPM: 105–128 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse] / 主歌
[Pre-Chorus] / 副歌前段
[Chorus - Group Vocal] / 群体副歌
[Verse 2] / 第二段主歌
[Bridge] / 桥段
[Final Chorus - Group Vocal] / 最后群体副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: bright piano/guitar/synth motif, energetic but clean. / 明亮钢琴、吉他或合成器动机，有能量但干净。
- Verse / 主歌: simple groove, clear lead vocal. / 简单律动，清晰主唱。
- Pre-Chorus / 副歌前段: add claps, drums, and rising chords. / 加拍手、鼓和上行和弦。
- Chorus / 副歌: group vocals, strong but accessible melody. / 群体人声，旋律强但易唱。
- Verse 2 / 第二段主歌: more percussion and bass than Verse 1. / 比第一段增加打击乐和贝斯。
- Bridge / 桥段: short breakdown with clap rhythm or spoken slogan-like line. / 短暂减法段，可用拍手节奏或口号式旁白。
- Final Chorus / 最后副歌: bigger group vocal, full drums, celebratory ending. / 更大的群体人声，完整鼓组，庆祝式结尾。
- Outro / 尾奏: repeat key phrase, final hit. / 重复关键短句，最后一击收束。

Vocal Strategy / 人声策略：

```text
clear lead vocal, group backing vocals, collective feeling
清晰主唱，群体和声，集体感
```

Instrumental Strategy / 器乐策略：

```text
drums, piano, guitar, claps, synths, optional brass
鼓、钢琴、吉他、拍手、合成器，可加入铜管
```

Prompt Keywords / Prompt 关键词：

```text
uplifting corporate anthem, group vocals, positive energy, celebratory chorus
振奋企业主题歌，群体人声，积极能量，庆祝式副歌
```

Avoid / 避免：

```text
too serious, too dark, overly complex lyrics, weak chorus
过于严肃，过暗，歌词过复杂，副歌无力
```

---

### 5.5 Sports / World Cup Anthem / 体育赛事 / 世界杯主题歌

- Use Case ID / 场景 ID: `sports_world_cup_anthem`
- Chinese Name / 中文名称: 体育赛事 / 世界杯主题歌
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 1:30–3:00
- Hook Placement / Hook 出现位置: chant or rhythm motif within first 10 seconds / 前 10 秒出现 chant 或节奏动机
- Lyrics Density / 歌词密度: medium-low; repeated phrases, easy to sing / 中低密度，重复短句，易合唱
- Energy Curve / 能量曲线: chant intro → rising verse → huge chorus → crowd finale / chant 开场 → 主歌抬升 → 大副歌 → 群体收尾
- Best Genres / 推荐曲风: stadium anthem, arena rock, Latin pop, cinematic pop, pop-rock, dance-pop / 体育场主题歌、竞技场摇滚、拉丁流行、电影感流行、流行摇滚、舞曲流行
- Best BPM Range / 推荐 BPM: 100–130 BPM

Recommended Structure / 推荐结构：

```text
[Intro - Stadium Chant] / 体育场口号前奏
[Verse - Percussion Groove] / 打击乐律动主歌
[Pre-Chorus - Rising Crowd] / 群体抬升段
[Chorus - Group Vocal] / 群体副歌
[Post-Chorus - Chant Hook] / 口号式副歌后段
[Bridge - Clap Breakdown] / 拍手减法桥段
[Final Chorus - Crowd Chant] / 观众最终副歌
[Outro - Final Chant] / 最终口号尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: stadium chant, crowd claps, big drums or brass motif. / 体育场 chant、观众拍手、大鼓或铜管动机。
- Verse / 主歌: rhythmic vocal, percussion-driven groove, bass and guitar support. / 节奏型人声，以打击乐驱动，贝斯和吉他支撑。
- Pre-Chorus / 副歌前段: rising drums, brass stabs, group backing vocals. / 鼓组上升、铜管点缀、群体和声。
- Chorus / 副歌: full stadium anthem, group vocals, powerful drums, simple repeated hook. / 完整体育场主题感，群体人声、强鼓、简单重复 Hook。
- Post-Chorus / 副歌后段: chant phrase or wordless crowd hook. / 口号短句或无词观众 Hook。
- Bridge / 桥段: breakdown with claps, drums, and call-response. / 拍手、鼓和呼应式人声减法段。
- Final Chorus / 最后副歌: bigger choir, brass, percussion, crowd chant, full energy. / 更大合唱、铜管、打击乐、观众 chant，全能量释放。
- Outro / 尾奏: final chant or drum hit. / 最终 chant 或鼓点重击收束。

Vocal Strategy / 人声策略：

```text
powerful lead vocal, group vocals, crowd chant, call-and-response
强力主唱，群体人声，观众 chant，呼应式演唱
```

Instrumental Strategy / 器乐策略：

```text
big drums, brass, electric guitar, bass, percussion, choir, Latin percussion if needed
大鼓、铜管、电吉他、贝斯、打击乐、合唱，可加入拉丁打击乐
```

Prompt Keywords / Prompt 关键词：

```text
stadium anthem, crowd chant, group vocals, powerful drums, repeatable chorus, sports energy
体育场主题歌，观众 chant，群体人声，强鼓，可重复副歌，体育能量
```

Avoid / 避免：

```text
quiet intro, weak drums, complex lyrics, chorus that is hard to sing
安静前奏，鼓太弱，歌词复杂，副歌难以合唱
```

---

### 5.6 Graduation Song / 毕业季歌曲

- Use Case ID / 场景 ID: `graduation_song`
- Chinese Name / 中文名称: 毕业季歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 2:00–3:30
- Hook Placement / Hook 出现位置: chorus within 40–60 seconds / 副歌在 40–60 秒内出现
- Lyrics Density / 歌词密度: medium; school memories and farewell imagery / 中等密度，校园记忆与告别画面
- Energy Curve / 能量曲线: nostalgia → farewell → hopeful future / 怀旧 → 告别 → 未来希望
- Best Genres / 推荐曲风: folk-pop, campus folk, Chinese pop ballad, pop-rock / 民谣流行、校园民谣、中文流行抒情、流行摇滚
- Best BPM Range / 推荐 BPM: 75–110 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse 1] / 第一段主歌
[Pre-Chorus] / 副歌前段
[Chorus] / 副歌
[Verse 2] / 第二段主歌
[Bridge] / 桥段
[Final Chorus - Group Vocal] / 最后群体副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: acoustic guitar or piano motif, nostalgic tone. / 原声吉他或钢琴动机，怀旧氛围。
- Verse 1 / 第一段主歌: light guitar/piano, minimal percussion, concrete campus images. / 轻吉他或钢琴，极少打击乐，呈现校园画面。
- Pre-Chorus / 副歌前段: add bass and light drums, emotional lift. / 加贝斯和轻鼓，情绪抬升。
- Chorus / 副歌: full but warm; strings or backing vocals enter. / 编曲打开但温暖，弦乐或和声进入。
- Verse 2 / 第二段主歌: more rhythmic movement, group harmony hints. / 增加律动，加入群体和声暗示。
- Bridge / 桥段: stripped-down reflection, maybe only piano and vocal. / 减法反思，可只留钢琴与人声。
- Final Chorus / 最后副歌: group vocals, wider strings, hopeful release. / 群体人声、更宽弦乐、希望感释放。
- Outro / 尾奏: soft ending with repeated line or school-bell-like motif. / 柔和结尾，可重复一句歌词或加入类似校铃的动机。

Vocal Strategy / 人声策略：

```text
clear youthful vocal, warm group backing, natural emotional delivery
清澈少年感人声，温暖群体和声，自然情绪表达
```

Instrumental Strategy / 器乐策略：

```text
acoustic guitar, piano, light drums, strings, group vocals
原声吉他、钢琴、轻鼓、弦乐、群体人声
```

Prompt Keywords / Prompt 关键词：

```text
nostalgic graduation song, hopeful final chorus, campus memories, group vocal ending
怀旧毕业歌，希望感最后副歌，校园记忆，群体人声结尾
```

Avoid / 避免：

```text
too dark, too commercial, overly adult sadness, aggressive sound
过暗，过度商业化，过于成人化的悲伤，攻击性声音
```

---

### 5.7 Wedding / Anniversary Song / 婚礼 / 纪念日歌曲

- Use Case ID / 场景 ID: `wedding_anniversary_song`
- Chinese Name / 中文名称: 婚礼 / 纪念日歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 2:00–3:30
- Hook Placement / Hook 出现位置: chorus within 45 seconds / 副歌 45 秒内出现
- Lyrics Density / 歌词密度: medium-low; tender and specific / 中低密度，温柔且具体
- Energy Curve / 能量曲线: intimate → romantic → warm final chorus / 亲密 → 浪漫 → 温暖最后副歌
- Best Genres / 推荐曲风: romantic pop ballad, R&B ballad, acoustic folk-pop, piano ballad / 浪漫流行抒情、R&B 抒情、原声民谣流行、钢琴抒情
- Best BPM Range / 推荐 BPM: 65–100 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse 1] / 第一段主歌
[Chorus] / 副歌
[Verse 2] / 第二段主歌
[Bridge] / 桥段
[Final Chorus] / 最后副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: soft piano or acoustic guitar, romantic motif. / 柔和钢琴或原声吉他，浪漫动机。
- Verse 1 / 第一段主歌: intimate vocal, minimal rhythm. / 亲密人声，极简节奏。
- Chorus / 副歌: warm strings, soft drums, emotional but gentle melody. / 温暖弦乐、柔和鼓组，旋律有情绪但不夸张。
- Verse 2 / 第二段主歌: add bass and subtle harmony. / 加入贝斯和轻和声。
- Bridge / 桥段: tender breakdown, maybe duet or harmony. / 温柔减法段，可做男女对唱或和声。
- Final Chorus / 最后副歌: fuller strings and backing vocals, romantic resolution. / 更丰满弦乐和和声，浪漫解决。
- Outro / 尾奏: soft final line, piano or guitar ending. / 柔和最后一句，以钢琴或吉他收尾。

Vocal Strategy / 人声策略：

```text
tender vocal, smooth male/female vocal, duet if requested
温柔人声，顺滑男声或女声，如需要可做对唱
```

Instrumental Strategy / 器乐策略：

```text
piano, acoustic guitar, soft strings, light R&B drums
钢琴、原声吉他、柔和弦乐、轻 R&B 鼓组
```

Prompt Keywords / Prompt 关键词：

```text
romantic, tender, intimate, warm final chorus, wedding-friendly
浪漫，温柔，亲密，温暖最后副歌，适合婚礼
```

Avoid / 避免：

```text
aggressive drums, dark lyrics, tragic ending, overly dramatic tension
攻击性鼓组，黑暗歌词，悲剧结尾，过度戏剧化张力
```

---

### 5.8 Birthday / Blessing Song / 生日 / 祝福歌曲

- Use Case ID / 场景 ID: `birthday_blessing_song`
- Chinese Name / 中文名称: 生日 / 祝福歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 30–120 seconds / 30–120 秒
- Hook Placement / Hook 出现位置: within 10–20 seconds / 10–20 秒内
- Lyrics Density / 歌词密度: low; clear blessing phrases / 低密度，清晰祝福短句
- Energy Curve / 能量曲线: warm opening → cheerful chorus → friendly ending / 温暖开场 → 愉快副歌 → 友好收束
- Best Genres / 推荐曲风: bright pop, acoustic pop, children’s pop, folk-pop / 明亮流行、原声流行、儿童流行、民谣流行
- Best BPM Range / 推荐 BPM: 90–125 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse] / 主歌
[Chorus] / 副歌
[Repeat Chorus] / 重复副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: friendly motif, light piano/guitar/ukulele. / 友好动机，轻钢琴、吉他或尤克里里。
- Verse / 主歌: short blessing setup, simple rhythm. / 简短祝福铺垫，简单节奏。
- Chorus / 副歌: memorable blessing line, claps or light percussion. / 有记忆点的祝福句，加入拍手或轻打击乐。
- Repeat Chorus / 重复副歌: reinforce the blessing phrase. / 强化祝福短句。
- Outro / 尾奏: warm final line. / 温暖最后一句。

Vocal Strategy / 人声策略：

```text
cheerful vocal, warm natural delivery, group vocal if family/friends
愉快人声，温暖自然演唱，如家庭或朋友场景可用群体人声
```

Instrumental Strategy / 器乐策略：

```text
ukulele, piano, acoustic guitar, hand claps, soft drums
尤克里里、钢琴、原声吉他、拍手、柔和鼓组
```

Prompt Keywords / Prompt 关键词：

```text
warm birthday song, cheerful blessing, simple catchy chorus, family-friendly
温暖生日歌，愉快祝福，简单抓耳副歌，适合家庭
```

Avoid / 避免：

```text
too long, sad tone, complex metaphors, intense drums
过长，伤感语气，复杂隐喻，强烈鼓组
```

---

### 5.9 Children’s Educational Song / 儿童教育歌曲

- Use Case ID / 场景 ID: `children_educational_song`
- Chinese Name / 中文名称: 儿童教育歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 30–90 seconds / 30–90 秒
- Hook Placement / Hook 出现位置: first 5–10 seconds / 前 5–10 秒
- Lyrics Density / 歌词密度: low; simple, repetitive, easy to remember / 低密度，简单、重复、易记
- Energy Curve / 能量曲线: cheerful from start to end / 从头到尾明亮愉快
- Best Genres / 推荐曲风: children’s song, playful pop, cartoon theme / 儿童歌、俏皮流行、动画主题曲
- Best BPM Range / 推荐 BPM: 90–130 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse] / 主歌
[Chorus] / 副歌
[Repeat Chorus] / 重复副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: bright motif, bells/ukulele/claps. / 明亮动机，可用铃声、尤克里里、拍手。
- Verse / 主歌: simple teaching point, short lines. / 简单知识点，短句。
- Chorus / 副歌: repeated key learning phrase. / 重复核心学习短句。
- Repeat Chorus / 重复副歌: reinforce memory. / 强化记忆。
- Outro / 尾奏: friendly ending or call-and-response. / 友好结尾或呼应式互动。

Vocal Strategy / 人声策略：

```text
cheerful vocal, children’s choir, simple call-and-response
愉快人声，儿童合唱，简单呼应式演唱
```

Instrumental Strategy / 器乐策略：

```text
ukulele, hand claps, toy piano, bells, light drums
尤克里里，拍手，玩具钢琴，铃声，轻鼓
```

Prompt Keywords / Prompt 关键词：

```text
children’s educational song, simple lyrics, playful, bright melody, easy to remember
儿童教育歌曲，简单歌词，俏皮，明亮旋律，易记
```

Avoid / 避免：

```text
complex metaphors, dark mood, long bridge, intense bass
复杂隐喻，黑暗情绪，长桥段，强低频
```

---

### 5.10 Article-to-Song Adaptation / 公众号文章 / 观点内容改编歌曲

- Use Case ID / 场景 ID: `article_to_song_adaptation`
- Chinese Name / 中文名称: 公众号文章 / 观点内容改编歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 1:30–3:00
- Hook Placement / Hook 出现位置: chorus within 45 seconds / 副歌 45 秒内出现
- Lyrics Density / 歌词密度: medium-high, but lines must remain singable / 中高密度，但每句必须可唱
- Energy Curve / 能量曲线: idea setup → emotional summary → memorable conclusion / 观点铺垫 → 情绪总结 → 记忆化结论
- Best Genres / 推荐曲风: Chinese pop ballad, folk-pop, cinematic pop, spoken-word pop / 中文流行抒情、民谣流行、电影感流行、旁白流行
- Best BPM Range / 推荐 BPM: 70–110 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse 1] / 第一段主歌
[Pre-Chorus] / 副歌前段
[Chorus] / 副歌
[Verse 2] / 第二段主歌
[Bridge] / 桥段
[Final Chorus] / 最后副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: mood-setting motif that matches article tone. / 用符合文章调性的动机建立情绪。
- Verse 1 / 第一段主歌: turn article situation into concrete scene. / 把文章议题转成具体生活场景。
- Pre-Chorus / 副歌前段: condense tension or question from the article. / 压缩文章中的矛盾或问题。
- Chorus / 副歌: summarize the core insight emotionally. / 用情绪化方式总结核心观点。
- Verse 2 / 第二段主歌: second example or deeper angle. / 第二个例子或更深层角度。
- Bridge / 桥段: reflection or turning point. / 反思或转折。
- Final Chorus / 最后副歌: repeat the article’s emotional conclusion in a memorable way. / 用有记忆点的方式重复文章情绪结论。
- Outro / 尾奏: leave one quotable final line. / 留下一句金句式收尾。

Vocal Strategy / 人声策略：

```text
natural storytelling vocal, mature emotional delivery, optional spoken-word intro
自然叙事人声，成熟情绪表达，可加入旁白式前奏
```

Instrumental Strategy / 器乐策略：

```text
depends on article tone; often piano, guitar, strings, soft drums
根据文章调性调整，常用钢琴、吉他、弦乐、柔和鼓组
```

Prompt Keywords / Prompt 关键词：

```text
story-driven, reflective, article-inspired, emotional summary, singable lines
叙事驱动，反思感，文章改编，情绪总结，歌词可唱
```

Avoid / 避免：

```text
essay-like long lines, slogan stacking, too many concepts, no concrete imagery
作文式长句，口号堆砌，概念过多，缺乏具体画面
```

---

### 5.11 City / Cultural Tourism Song / 城市 / 文旅宣传歌曲

- Use Case ID / 场景 ID: `city_cultural_tourism_song`
- Chinese Name / 中文名称: 城市 / 文旅宣传歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 1:30–3:00
- Hook Placement / Hook 出现位置: chorus within 40–50 seconds / 副歌 40–50 秒内出现
- Lyrics Density / 歌词密度: medium; place names and images should be poetic, not list-like / 中等密度，地名与画面要诗意，不要清单式罗列
- Energy Curve / 能量曲线: scenic opening → emotional identity → expansive final chorus / 景象开场 → 情感身份 → 开阔最后副歌
- Best Genres / 推荐曲风: Chinese traditional pop, cinematic pop, folk-pop, world fusion / 国风流行、电影感流行、民谣流行、世界融合
- Best BPM Range / 推荐 BPM: 75–115 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse 1] / 第一段主歌
[Pre-Chorus] / 副歌前段
[Chorus] / 副歌
[Verse 2] / 第二段主歌
[Bridge] / 桥段
[Final Chorus] / 最后副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: local color motif, traditional instrument or cinematic piano. / 地域色彩动机，可用传统乐器或电影感钢琴。
- Verse 1 / 第一段主歌: scenic images, restrained arrangement. / 呈现景物画面，编曲克制。
- Pre-Chorus / 副歌前段: add percussion or strings, emotional lift. / 加入打击乐或弦乐，情绪抬升。
- Chorus / 副歌: open, memorable city identity phrase. / 开阔、有记忆点的城市身份短句。
- Verse 2 / 第二段主歌: add more rhythmic movement and local texture. / 增加律动和地方音色。
- Bridge / 桥段: instrumental break with regional instrument. / 用地方乐器做器乐间奏。
- Final Chorus / 最后副歌: full arrangement, choir or backing vocal. / 完整编曲，加入合唱或和声。
- Outro / 尾奏: return to local motif. / 回到地方动机收束。

Vocal Strategy / 人声策略：

```text
clear emotional vocal, poetic delivery, optional group backing
清晰情绪人声，诗性表达，可加入群体和声
```

Instrumental Strategy / 器乐策略：

```text
piano, strings, Chinese instruments, regional percussion, cinematic drums
钢琴、弦乐、中国乐器、地域打击乐、电影感鼓组
```

Prompt Keywords / Prompt 关键词：

```text
city anthem, cultural tourism, poetic imagery, cinematic Chinese pop, local musical color
城市主题歌，文旅宣传，诗意画面，电影感国风流行，地方音乐色彩
```

Avoid / 避免：

```text
tourism slogan list, too many place names, generic stock music feel
旅游口号清单，地名堆砌，通用素材音乐感
```

---

### 5.12 Healing Emotional Song / 情绪疗愈歌曲

- Use Case ID / 场景 ID: `healing_emotional_song`
- Chinese Name / 中文名称: 情绪疗愈歌曲
- Track Type / 音乐类型: vocal song / 带人声歌曲
- Recommended Length / 推荐时长: 1:30–3:30
- Hook Placement / Hook 出现位置: chorus within 45–60 seconds / 副歌 45–60 秒内出现
- Lyrics Density / 歌词密度: medium-low; simple comforting language / 中低密度，简单安慰性语言
- Energy Curve / 能量曲线: soft comfort → gentle hope → peaceful ending / 柔和安慰 → 温柔希望 → 平静收尾
- Best Genres / 推荐曲风: healing pop, acoustic folk-pop, piano ballad, ambient pop / 治愈流行、原声民谣流行、钢琴抒情、氛围流行
- Best BPM Range / 推荐 BPM: 60–90 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 前奏
[Verse 1] / 第一段主歌
[Chorus] / 副歌
[Verse 2] / 第二段主歌
[Bridge] / 桥段
[Final Chorus] / 最后副歌
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 前奏: soft piano, ambient pad, gentle texture. / 柔和钢琴、氛围 pad、轻柔质感。
- Verse 1 / 第一段主歌: intimate vocal, minimal accompaniment. / 亲密人声，极简伴奏。
- Chorus / 副歌: gentle lift, light strings or warm harmonies. / 温柔抬升，轻弦乐或温暖和声。
- Verse 2 / 第二段主歌: add subtle percussion or bass warmth. / 加入轻打击乐或温暖贝斯。
- Bridge / 桥段: very soft breakdown, comforting line. / 非常柔和的减法段，加入安慰性句子。
- Final Chorus / 最后副歌: slightly fuller but still gentle. / 稍微丰满但仍保持轻柔。
- Outro / 尾奏: peaceful fade or soft final chord. / 平静淡出或柔和终止和弦。

Vocal Strategy / 人声策略：

```text
soft vocal, breathy delivery, clear gentle tone
柔和人声，气声感，清澈温柔音色
```

Instrumental Strategy / 器乐策略：

```text
soft piano, pads, acoustic guitar, light strings, minimal percussion
柔和钢琴、pad、原声吉他、轻弦乐、极简打击乐
```

Prompt Keywords / Prompt 关键词：

```text
healing, soothing, gentle, comforting, peaceful, soft final chorus
治愈，舒缓，轻柔，安慰，平静，柔和最后副歌
```

Avoid / 避免：

```text
loud drums, dramatic climax, aggressive vocal, harsh synths
响亮鼓组，戏剧化高潮，攻击性人声，刺耳合成器
```

---

## 6. Instrumental Use-Case Templates / 纯器乐使用场景模板

### 6.1 Short Video BGM / 短视频 BGM

- Use Case ID / 场景 ID: `short_video_bgm`
- Chinese Name / 中文名称: 短视频 BGM
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 15–60 seconds / 15–60 秒
- Hook Placement / Hook 出现位置: first 3–8 seconds / 前 3–8 秒
- Energy Curve / 能量曲线: immediate identity → small variation → seamless loop / 立即建立识别 → 小变化 → 无缝循环
- Best Genres / 推荐曲风: lo-fi, electro-pop instrumental, chillhop, future bass, funk groove / Lo-fi、电子流行器乐、Chillhop、Future Bass、Funk 律动
- Best BPM Range / 推荐 BPM: 85–130 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Main Hook] / 主 Hook
[Variation] / 变奏
[Loop Ending] / 循环结尾
```

Arrangement Plan / 编曲计划：

- Intro / 引入: very short; start with beat, motif, or recognizable sound. / 非常短；用节拍、动机或可识别音色开场。
- Main Hook / 主 Hook: simple instrumental melody or rhythmic motif. / 简单器乐旋律或节奏动机。
- Variation / 变奏: add small percussion, counter-melody, or texture shift. / 加小打击乐、对位旋律或质感变化。
- Loop Ending / 循环结尾: return to main motif without hard finality. / 回到主动机，不做强终止，方便循环。

Instrumental Strategy / 器乐策略：

```text
instrumental only, no vocals, no rap, no spoken words, short intro, loop-friendly
纯器乐，无人声，无说唱，无旁白，短前奏，可循环
```

Prompt Keywords / Prompt 关键词：

```text
short video BGM, hook arrives early, instrumental hook, loop-friendly, clear beat
短视频 BGM，Hook 早出现，器乐 Hook，可循环，节奏清晰
```

Avoid / 避免：

```text
vocals, long build, complex changes, sudden dramatic ending
人声，长铺垫，复杂变化，突然戏剧化结尾
```

---

### 6.2 Study / Work BGM / 学习 / 工作 BGM

- Use Case ID / 场景 ID: `study_work_bgm`
- Chinese Name / 中文名称: 学习 / 工作 BGM
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 2:00–5:00 or loopable / 2–5 分钟或可循环
- Hook Placement / Hook 出现位置: subtle motif, not distracting / 轻微动机，不打扰
- Energy Curve / 能量曲线: stable and calm / 稳定、平静
- Best Genres / 推荐曲风: lo-fi hip-hop, chillhop, ambient pop, piano instrumental, downtempo / Lo-fi Hip-hop、Chillhop、氛围流行、钢琴器乐、Downtempo
- Best BPM Range / 推荐 BPM: 60–90 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Main Loop] / 主循环
[Subtle Variation] / 细微变奏
[Breakdown] / 减法段
[Main Loop Return] / 主循环回归
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 引入: soft piano chords, vinyl texture, or ambient pad. / 柔和钢琴和弦、黑胶质感或氛围 pad。
- Main Loop / 主循环: mellow drums, warm bass, simple piano/guitar motif. / 柔和鼓组、温暖贝斯、简单钢琴或吉他动机。
- Subtle Variation / 细微变奏: add light keys, small percussion, or background texture. / 加轻键盘、小打击乐或背景质感。
- Breakdown / 减法段: remove drums briefly, keep pad and main motif. / 短暂去掉鼓，保留 pad 和主动机。
- Main Loop Return / 主循环回归: bring drums and bass back gently. / 温和带回鼓和贝斯。
- Outro / 尾奏: fade or loop-friendly ending. / 淡出或循环友好结尾。

Instrumental Strategy / 器乐策略：

```text
instrumental only, no vocals, non-intrusive, steady groove, subtle variations, loop-friendly
纯器乐，无人声，不打扰，稳定律动，细微变化，可循环
```

Prompt Keywords / Prompt 关键词：

```text
study background music, calm, non-intrusive, subtle variation, warm lo-fi texture
学习背景音乐，平静，不打扰，细微变化，温暖 Lo-fi 质感
```

Avoid / 避免：

```text
vocals, sudden drops, dramatic transitions, big chorus, aggressive drums
人声，突然 drop，戏剧化转场，大副歌，攻击性鼓组
```

---

### 6.3 Brand Film Background Music / 品牌宣传片背景音乐

- Use Case ID / 场景 ID: `brand_film_background_music`
- Chinese Name / 中文名称: 品牌宣传片背景音乐
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 60–120 seconds / 60–120 秒
- Hook Placement / Hook 出现位置: recognizable motif within 10–15 seconds / 10–15 秒内出现可识别动机
- Energy Curve / 能量曲线: clean opening → confident build → uplifting climax / 干净开场 → 自信推进 → 振奋高潮
- Best Genres / 推荐曲风: corporate pop instrumental, cinematic pop instrumental, uplifting electronic / 企业流行器乐、电影感流行器乐、振奋电子
- Best BPM Range / 推荐 BPM: 90–125 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Build] / 推进
[Main Theme] / 主主题
[Climax] / 高潮
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 引入: clean piano or minimal synth motif, premium brand identity. / 干净钢琴或极简合成器动机，建立高级品牌识别。
- Build / 推进: add soft pulse, bass, light percussion, sense of progress. / 加入柔和脉冲、贝斯、轻打击乐，形成前进感。
- Main Theme / 主主题: introduce memorable melody, polished drums and warm harmony. / 引入有记忆点旋律、精致鼓组和温暖和声。
- Climax / 高潮: cinematic strings, bigger drums, wider mix, uplifting feeling. / 电影感弦乐、更大鼓组、更宽声场，形成振奋感。
- Outro / 尾奏: resolved ending, logo-friendly final note or hit. / 明确解决，适合 Logo 的终止音或收束音效。

Instrumental Strategy / 器乐策略：

```text
instrumental only, polished, optimistic, leave room for voiceover, premium mix
纯器乐，精致，积极，为旁白留空间，高级混音
```

Prompt Keywords / Prompt 关键词：

```text
brand film background music, uplifting corporate, premium, clean build, inspiring climax
品牌片背景音乐，振奋企业感，高级，干净推进，鼓舞高潮
```

Avoid / 避免：

```text
too sad, too busy, cheap stock music feel, too many lead melodies fighting voiceover
过度伤感，过于拥挤，廉价素材音乐感，主旋律太多抢旁白
```

---

### 6.4 Tech Product Background Music / 科技产品背景音乐

- Use Case ID / 场景 ID: `tech_product_background_music`
- Chinese Name / 中文名称: 科技产品背景音乐
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 45–120 seconds / 45–120 秒
- Hook Placement / Hook 出现位置: subtle motif within 10–15 seconds / 10–15 秒内出现轻微动机
- Energy Curve / 能量曲线: precise → optimistic → premium / 精准 → 积极 → 高级
- Best Genres / 推荐曲风: minimal electronic, tech product background, synth-pop instrumental, corporate electronic / 极简电子、科技产品背景、合成器流行器乐、企业电子
- Best BPM Range / 推荐 BPM: 90–125 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Pulse Groove] / 脉冲律动
[Build] / 推进
[Main Theme] / 主主题
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 引入: clean digital texture, soft synth pulse. / 干净数字质感，柔和合成器脉冲。
- Pulse Groove / 脉冲律动: minimal beat, sub bass, precise rhythmic movement. / 极简节拍、低频贝斯、精准节奏运动。
- Build / 推进: add arpeggio, brighter synth layers, slight lift. / 加琶音、更明亮合成器层，轻微抬升。
- Main Theme / 主主题: memorable but not distracting synth/piano motif. / 有记忆点但不打扰的合成器或钢琴动机。
- Outro / 尾奏: clean resolved ending, logo-friendly. / 干净解决，适合 Logo 收尾。

Instrumental Strategy / 器乐策略：

```text
instrumental only, clean futuristic, minimal electronic, premium, non-intrusive
纯器乐，干净未来感，极简电子，高级，不打扰
```

Prompt Keywords / Prompt 关键词：

```text
tech product background, futuristic, clean, pulsing synths, digital texture, premium
科技产品背景，未来感，干净，脉冲合成器，数字质感，高级
```

Avoid / 避免：

```text
rustic acoustic-only, overly emotional strings, club drop, aggressive bass
纯乡村原声感，过度情绪化弦乐，夜店 drop，攻击性低频
```

---

### 6.5 Vlog / Travel BGM / Vlog / 旅行生活方式 BGM

- Use Case ID / 场景 ID: `vlog_travel_bgm`
- Chinese Name / 中文名称: Vlog / 旅行生活方式 BGM
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 30–120 seconds / 30–120 秒
- Hook Placement / Hook 出现位置: light motif within first 10 seconds / 前 10 秒内轻动机
- Energy Curve / 能量曲线: relaxed and breezy / 轻松、清爽
- Best Genres / 推荐曲风: acoustic instrumental, bossa nova instrumental, chillhop, lifestyle pop / 原声器乐、Bossa Nova 器乐、Chillhop、生活方式流行
- Best BPM Range / 推荐 BPM: 85–120 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Main Groove] / 主律动
[Variation] / 变奏
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 引入: light guitar, ukulele, or piano motif. / 轻吉他、尤克里里或钢琴动机。
- Main Groove / 主律动: soft beat, warm bass, breezy melody. / 柔和节拍、温暖贝斯、清爽旋律。
- Variation / 变奏: small percussion, hand claps, or second guitar line. / 小打击乐、拍手或第二条吉他线。
- Outro / 尾奏: gentle close or loop-friendly ending. / 温柔收束或可循环结尾。

Instrumental Strategy / 器乐策略：

```text
instrumental only, sunny, relaxed, friendly, lifestyle background
纯器乐，阳光，轻松，友好，生活方式背景
```

Prompt Keywords / Prompt 关键词：

```text
travel vlog BGM, breezy, sunny, relaxed groove, acoustic texture, lifestyle
旅行 Vlog BGM，清爽，阳光，轻松律动，原声质感，生活方式
```

Avoid / 避免：

```text
dramatic climax, heavy drums, dark mood, too cinematic
戏剧化高潮，重鼓，黑暗情绪，过度电影感
```

---

### 6.6 Documentary / Character Story Score / 纪录片 / 人物故事配乐

- Use Case ID / 场景 ID: `documentary_character_story_score`
- Chinese Name / 中文名称: 纪录片 / 人物故事配乐
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 1:00–3:00
- Hook Placement / Hook 出现位置: emotional motif within 20–30 seconds / 20–30 秒内出现情绪动机
- Energy Curve / 能量曲线: reflective opening → emotional build → restrained resolution / 反思开场 → 情绪推进 → 克制解决
- Best Genres / 推荐曲风: cinematic emotional instrumental, piano score, ambient pop, orchestral pop instrumental / 电影感情绪器乐、钢琴配乐、氛围流行、管弦流行器乐
- Best BPM Range / 推荐 BPM: 60–100 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Main Theme] / 主主题
[Development] / 发展段
[Emotional Build] / 情绪推进
[Resolution] / 解决段
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 引入: soft piano, ambient texture, documentary tone. / 柔和钢琴、氛围质感、纪录片语气。
- Main Theme / 主主题: simple motif, emotionally clear. / 简单动机，情绪清晰。
- Development / 发展段: add strings, low percussion, or subtle guitar. / 加弦乐、低打击乐或轻吉他。
- Emotional Build / 情绪推进: widen strings, add deeper bass or percussion. / 加宽弦乐，加入更深贝斯或打击乐。
- Resolution / 解决段: reduce density, leave emotional space. / 降低密度，留下情绪空间。
- Outro / 尾奏: soft final chord or unresolved reflective ending if needed. / 柔和终止和弦，或根据需要做未完全解决的反思结尾。

Instrumental Strategy / 器乐策略：

```text
instrumental only, emotional, cinematic, restrained, leave room for narration
纯器乐，情绪化，电影感，克制，为旁白留空间
```

Prompt Keywords / Prompt 关键词：

```text
documentary score, emotional build, reflective piano, warm strings, restrained climax
纪录片配乐，情绪推进，反思钢琴，温暖弦乐，克制高潮
```

Avoid / 避免：

```text
overly pop chorus, too loud, too busy, distracting lead melody
过度流行副歌，太响，过于拥挤，主旋律抢注意力
```

---

### 6.7 Sports Highlight Instrumental / 体育剪辑 / 高光集锦配乐

- Use Case ID / 场景 ID: `sports_highlight_instrumental`
- Chinese Name / 中文名称: 体育剪辑 / 高光集锦配乐
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 30–120 seconds / 30–120 秒
- Hook Placement / Hook 出现位置: strong rhythm or impact within first 5–10 seconds / 前 5–10 秒出现强节奏或冲击点
- Energy Curve / 能量曲线: tension → impact → bigger final hit / 张力 → 冲击 → 更大最终冲击
- Best Genres / 推荐曲风: sports highlight instrumental, cinematic action, trap instrumental, arena rock instrumental / 体育高光器乐、电影动作配乐、Trap 器乐、竞技场摇滚器乐
- Best BPM Range / 推荐 BPM: 100–150 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Build-Up] / 推进
[Drop / Main Impact] / Drop / 主冲击段
[Breakdown] / 减法段
[Final Impact] / 最终冲击
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 引入: punchy hit, drum motif, or tense pulse. / 有力音效、鼓动机或紧张脉冲。
- Build-Up / 推进: rising percussion, bass, guitar/synth/brass layers. / 上升打击乐、贝斯、吉他、合成器或铜管层。
- Drop / Main Impact / 主冲击段: full drums, bass, impacts, lead motif. / 完整鼓组、贝斯、冲击音效、主旋律动机。
- Breakdown / 减法段: reduce energy briefly for edit contrast. / 短暂减法，为剪辑制造对比。
- Final Impact / 最终冲击: bigger drums, brass/guitar/synth, wide mix. / 更大鼓组、铜管/吉他/合成器，更宽声场。
- Outro / 尾奏: strong final hit or cut-friendly ending. / 强最终击或适合剪辑切点的结尾。

Instrumental Strategy / 器乐策略：

```text
instrumental only, powerful rhythm, high-impact, edit-friendly, strong hits
纯器乐，强节奏，高冲击，适合剪辑，强击点
```

Prompt Keywords / Prompt 关键词：

```text
sports highlight music, powerful drums, cinematic action, impact hits, high-energy build
体育高光音乐，强鼓，电影动作感，冲击点，高能推进
```

Avoid / 避免：

```text
slow mellow intro, weak rhythm, no impact points, overly soft instrumentation
缓慢柔和前奏，弱节奏，没有冲击点，乐器过软
```

---

### 6.8 Podcast Intro / Logo Sting / 播客片头 / Logo Sting

- Use Case ID / 场景 ID: `podcast_intro_logo_sting`
- Chinese Name / 中文名称: 播客片头 / Logo Sting
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 5–15 seconds for logo sting; 10–30 seconds for podcast intro / Logo Sting 5–15 秒；播客片头 10–30 秒
- Hook Placement / Hook 出现位置: immediate motif / 动机立即出现
- Energy Curve / 能量曲线: quick identity → resolved ending / 快速建立识别 → 明确收束
- Best Genres / 推荐曲风: minimal electronic, corporate pop, jazz pop, acoustic logo, synth logo / 极简电子、企业流行、爵士流行、原声 Logo、合成器 Logo
- Best BPM Range / 推荐 BPM: flexible; usually 90–125 BPM feel / 灵活，通常 90–125 BPM 体感

Recommended Structure / 推荐结构：

```text
[Signature Motif] / 标志性动机
[Short Build] / 短推进
[Logo Hit] / Logo 收束
```

Arrangement Plan / 编曲计划：

- Signature Motif / 标志性动机: 2–4 note identity, immediately recognizable. / 2–4 个音形成识别动机，立即可识别。
- Short Build / 短推进: one quick swell or rhythmic movement. / 一次短促上升或节奏运动。
- Logo Hit / Logo 收束: clean final resolved note, hit, or chord. / 干净解决的最后音、音效或和弦。

Instrumental Strategy / 器乐策略：

```text
instrumental only, concise, memorable, brandable, clean ending
纯器乐，简洁，有记忆点，可品牌化，干净结尾
```

Prompt Keywords / Prompt 关键词：

```text
podcast intro, logo sting, short signature motif, brandable, resolved final hit
播客片头，Logo Sting，短标志性动机，可品牌化，明确最终收束
```

Avoid / 避免：

```text
long development, unresolved ending, too many instruments, vocals
长发展段，不解决结尾，乐器过多，人声
```

---

### 6.9 Fashion / Lifestyle Background / 时尚 / 生活方式背景音乐

- Use Case ID / 场景 ID: `fashion_lifestyle_background`
- Chinese Name / 中文名称: 时尚 / 生活方式背景音乐
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 30–120 seconds / 30–120 秒
- Hook Placement / Hook 出现位置: groove within first 5–10 seconds / 前 5–10 秒出现律动
- Energy Curve / 能量曲线: stylish steady groove → subtle variations → clean ending / 时尚稳定律动 → 细微变化 → 干净结尾
- Best Genres / 推荐曲风: nu jazz instrumental, fashion groove, minimal house, disco-funk instrumental, chill electronic / Nu Jazz 器乐、时尚律动、极简 House、Disco-Funk 器乐、Chill Electronic
- Best BPM Range / 推荐 BPM: 95–125 BPM

Recommended Structure / 推荐结构：

```text
[Intro] / 引入
[Groove] / 律动段
[Variation] / 变奏
[Breakdown] / 减法段
[Groove Return] / 律动回归
[Outro] / 尾奏
```

Arrangement Plan / 编曲计划：

- Intro / 引入: clean bassline, muted guitar, or stylish synth. / 干净贝斯线、闷音吉他或时尚合成器。
- Groove / 律动段: drums, bass, minimal chord pattern. / 鼓、贝斯、极简和弦模式。
- Variation / 变奏: add percussion, synth stab, or guitar lick. / 加打击乐、合成器短音或吉他 lick。
- Breakdown / 减法段: reduce drums briefly for edit contrast. / 短暂减少鼓，为剪辑制造对比。
- Groove Return / 律动回归: bring back rhythm with more polish. / 以更精致的方式带回节奏。
- Outro / 尾奏: clean fade or final groove hit. / 干净淡出或最终律动击点。

Instrumental Strategy / 器乐策略：

```text
instrumental only, stylish, minimal, polished, groove-based
纯器乐，时尚，极简，精致，律动驱动
```

Prompt Keywords / Prompt 关键词：

```text
fashion background music, stylish groove, minimal, polished, elegant, modern lifestyle
时尚背景音乐，时尚律动，极简，精致，优雅，现代生活方式
```

Avoid / 避免：

```text
overly emotional melody, childish sounds, cluttered arrangement
过度情绪化旋律，幼稚音色，拥挤编曲
```

---

### 6.10 Meditation / Sleep Ambient / 冥想 / 睡眠氛围音乐

- Use Case ID / 场景 ID: `meditation_sleep_ambient`
- Chinese Name / 中文名称: 冥想 / 睡眠氛围音乐
- Track Type / 音乐类型: instrumental / 纯器乐
- Recommended Length / 推荐时长: 3:00–10:00 or loopable / 3–10 分钟或可循环
- Hook Placement / Hook 出现位置: no strong hook / 不需要强 Hook
- Energy Curve / 能量曲线: extremely stable, slow evolution / 极度稳定，缓慢变化
- Best Genres / 推荐曲风: ambient, ambient electronic, soft piano ambient, healing soundscape / Ambient、氛围电子、柔和钢琴氛围、治愈声景
- Best BPM Range / 推荐 BPM: no strict BPM or 50–70 BPM feel / 无严格 BPM，或 50–70 BPM 体感

Recommended Structure / 推荐结构：

```text
[Ambient Intro] / 氛围前奏
[Soft Main Texture] / 柔和主质感
[Subtle Evolution] / 细微变化
[Calm Return] / 平静回归
[Fade Out] / 淡出
```

Arrangement Plan / 编曲计划：

- Ambient Intro / 氛围前奏: pads, nature texture, soft drone. / pad、自然环境声、柔和 drone。
- Soft Main Texture / 柔和主质感: long sustained tones, soft piano or bells. / 长持续音，柔和钢琴或铃声。
- Subtle Evolution / 细微变化: barely noticeable harmonic or texture changes. / 几乎不打扰的和声或质感变化。
- Calm Return / 平静回归: simplify back to main texture. / 简化并回到主质感。
- Fade Out / 淡出: very soft ending or loop-friendly fade. / 非常柔和收尾或循环友好淡出。

Instrumental Strategy / 器乐策略：

```text
instrumental only, no vocals, no drums or minimal pulse, calm, spacious, sleep-friendly
纯器乐，无人声，无鼓或极少脉冲，平静，空间感，适合睡眠
```

Prompt Keywords / Prompt 关键词：

```text
meditation ambient, sleep music, spacious pads, soft texture, slow evolution, peaceful
冥想氛围，睡眠音乐，宽阔 pad，柔和质感，缓慢变化，平静
```

Avoid / 避免：

```text
strong beat, sudden change, vocals, bright hook, dramatic climax
强节拍，突然变化，人声，明亮 Hook，戏剧化高潮
```

---

## 7. Length & Hook Placement Reference / 时长与 Hook 出现位置参考

| Use Case / 使用场景 | Recommended Length / 推荐时长 | Hook / Main Motif Placement / Hook 或主动机位置 |
|---|---:|---|
| Short video hook song / 短视频 Hook 歌曲 | 20–45 sec / 20–45 秒 | 3–8 sec / 3–8 秒 |
| Short video BGM / 短视频 BGM | 15–60 sec / 15–60 秒 | 3–8 sec / 3–8 秒 |
| Personal story song / 个人故事歌 | 1:30–3:00 | chorus 35–50 sec / 副歌 35–50 秒 |
| Brand theme song / 品牌主题歌 | 1:00–2:30 | chorus 30–45 sec / 副歌 30–45 秒 |
| Corporate / annual event song / 企业年会歌 | 1:30–3:00 | chorus within 40 sec / 副歌 40 秒内 |
| Sports / World Cup anthem / 体育 / 世界杯主题歌 | 1:30–3:00 | chant within 10 sec / chant 10 秒内 |
| Graduation song / 毕业歌 | 2:00–3:30 | chorus 40–60 sec / 副歌 40–60 秒 |
| Wedding song / 婚礼歌 | 2:00–3:30 | chorus within 45 sec / 副歌 45 秒内 |
| Birthday song / 生日歌 | 30–120 sec / 30–120 秒 | 10–20 sec / 10–20 秒 |
| Children’s educational song / 儿童教育歌 | 30–90 sec / 30–90 秒 | 5–10 sec / 5–10 秒 |
| Study / work BGM / 学习工作 BGM | 2:00–5:00 or loop / 2–5 分钟或循环 | no strong hook / 无强 Hook |
| Brand film BGM / 品牌片 BGM | 60–120 sec / 60–120 秒 | motif 10–15 sec / 动机 10–15 秒 |
| Tech product BGM / 科技产品 BGM | 45–120 sec / 45–120 秒 | motif 10–15 sec / 动机 10–15 秒 |
| Documentary score / 纪录片配乐 | 1:00–3:00 | motif 20–30 sec / 动机 20–30 秒 |
| Sports highlight instrumental / 体育高光器乐 | 30–120 sec / 30–120 秒 | impact 5–10 sec / 冲击点 5–10 秒 |
| Podcast intro / logo sting / 播客片头 / Logo Sting | 5–30 sec / 5–30 秒 | immediate / 立即 |

---

## 8. Scene-to-Structure Quick Map / 场景到结构快速映射

| User Scene / 用户场景 | Track Type / 类型 | Structure / 推荐结构 |
|---|---|---|
| 短视频歌曲 / Short video song | vocal / 人声歌曲 | [Hook] [Verse] [Chorus] [Outro] |
| 朋友圈个人歌 / Personal story song | vocal / 人声歌曲 | [Intro] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Bridge] [Final Chorus] [Outro] |
| 品牌主题歌 / Brand theme song | vocal / 人声歌曲 | [Intro] [Verse] [Pre-Chorus] [Chorus] [Bridge] [Final Chorus] [Outro] |
| 体育 / 世界杯 / Sports / World Cup | vocal / 人声歌曲 | [Intro - Stadium Chant] [Verse] [Pre-Chorus] [Chorus - Group Vocal] [Post-Chorus] [Bridge] [Final Chorus] [Outro] |
| 毕业歌 / Graduation song | vocal / 人声歌曲 | [Intro] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Bridge] [Final Chorus - Group Vocal] [Outro] |
| 婚礼歌 / Wedding song | vocal / 人声歌曲 | [Intro] [Verse 1] [Chorus] [Verse 2] [Bridge] [Final Chorus] [Outro] |
| 儿童教育 / Children’s education | vocal / 人声歌曲 | [Intro] [Verse] [Chorus] [Repeat Chorus] [Outro] |
| 短视频 BGM / Short video BGM | instrumental / 纯器乐 | [Intro] [Main Hook] [Variation] [Loop Ending] |
| 学习 BGM / Study BGM | instrumental / 纯器乐 | [Intro] [Main Loop] [Subtle Variation] [Breakdown] [Main Loop Return] [Outro] |
| 品牌片 BGM / Brand film BGM | instrumental / 纯器乐 | [Intro] [Build] [Main Theme] [Climax] [Outro] |
| 科技产品 BGM / Tech product BGM | instrumental / 纯器乐 | [Intro] [Pulse Groove] [Build] [Main Theme] [Outro] |
| 运动剪辑 / Sports highlight | instrumental / 纯器乐 | [Intro] [Build-Up] [Drop / Main Impact] [Breakdown] [Final Impact] [Outro] |

---

## 9. Scene-to-Arrangement Quick Map / 场景到编曲快速映射

| Scene / 场景 | Arrangement Priority / 编曲优先级 |
|---|---|
| Short video / 短视频 | hook early, short intro, loop-friendly / Hook 早出现、短前奏、可循环 |
| Personal story / 个人故事 | intimate verse, emotional chorus, warm ending / 亲密主歌、情绪副歌、温暖结尾 |
| Brand theme / 品牌主题 | polished build, brandable hook, positive ending / 精致推进、可品牌化 Hook、积极结尾 |
| Corporate event / 企业活动 | group vocal, claps, celebratory final chorus / 群体人声、拍手、庆祝式最后副歌 |
| Sports anthem / 体育主题 | chant, big drums, group vocal, repeatable hook / chant、大鼓、群体人声、可重复 Hook |
| Graduation / 毕业 | nostalgic intro, hopeful group final chorus / 怀旧前奏、希望感群体最终副歌 |
| Wedding / 婚礼 | tender intro, romantic strings, warm final chorus / 温柔前奏、浪漫弦乐、温暖最后副歌 |
| Children’s song / 儿童歌 | simple melody, playful instruments, repetition / 简单旋律、俏皮乐器、重复 |
| Article adaptation / 文章改歌 | turn concept into emotional chorus / 把观点转化为情绪副歌 |
| City tourism / 城市文旅 | local motif, cinematic expansion / 地域动机、电影感展开 |
| Study BGM / 学习 BGM | stable loop, subtle variation, no vocals / 稳定循环、细微变化、无人声 |
| Tech product / 科技产品 | minimal synth pulse, clean build, leave space / 极简合成器脉冲、干净推进、留空间 |
| Brand film BGM / 品牌片 BGM | premium motif, steady uplift, resolved logo ending / 高级动机、稳定抬升、Logo 式解决 |
| Documentary / 纪录片 | restrained emotional build, narration-friendly / 克制情绪推进，适合旁白 |
| Sports highlight / 体育高光 | edit-friendly impacts, tension and release / 适合剪辑的冲击点，张力与释放 |
| Podcast / logo / 播客 / Logo | immediate motif, short build, final hit / 动机立即出现、短推进、最终击点 |

---

## 10. Negative Structure Rules / 结构与编曲反向规则

| Scene / 场景 | Avoid / 避免 |
|---|---|
| Short video / 短视频 | long intro, hook too late, slow cinematic build / 长前奏、Hook 太晚、慢电影式铺垫 |
| Brand promo / 品牌宣传 | too sad, too dark, unresolved ending / 太伤感、太暗、结尾不解决 |
| Sports anthem / 体育主题 | weak drums, complex lyrics, no chant / 鼓太弱、歌词复杂、没有 chant |
| Study BGM / 学习 BGM | vocals, drops, big chorus, sudden changes / 人声、drop、大副歌、突然变化 |
| Wedding / 婚礼 | aggressive drums, dark lyrics, tragic ending / 攻击性鼓、黑暗歌词、悲剧结尾 |
| Children’s song / 儿童歌 | complex metaphors, long bridge, dark mood / 复杂隐喻、长桥段、黑暗情绪 |
| Tech product / 科技产品 | rustic acoustic-only, club drop, cluttered mix / 纯乡村原声感、夜店 drop、混音拥挤 |
| Documentary / 纪录片 | loud pop hook, distracting lead melody / 响亮流行 Hook、抢注意力主旋律 |
| Logo sting / Logo 音效 | long development, unresolved ending / 长发展、不解决结尾 |
| Instrumental BGM / 器乐 BGM | vocals, rap, spoken words unless requested / 人声、说唱、旁白，除非用户要求 |
| Background music with voiceover / 带旁白背景音乐 | busy lead melody, dense vocals, harsh transients / 主旋律过忙、人声密集、瞬态过强 |

---

## 11. Prompt Formula / Prompt 公式

### 11.1 Vocal Song Structure + Arrangement Formula / 带人声歌曲结构 + 编曲公式

```text
Use the following song structure and arrangement plan:
请使用以下歌曲结构与编曲计划：

[Intro - {intro arrangement / 前奏编曲}]
[Verse 1 - {verse arrangement, vocal focus / 主歌编曲，突出人声}]
[Pre-Chorus - {build strategy / 推进策略}]
[Chorus - {full arrangement, hook strategy / 完整编曲与 Hook 策略}]
[Verse 2 - {slightly expanded verse arrangement / 略微扩展的第二段主歌编曲}]
[Bridge - {contrast or breakdown / 对比或减法段}]
[Final Chorus - {largest arrangement, emotional payoff / 最大编曲密度与情绪释放}]
[Outro - {ending strategy / 结尾策略}]

The arrangement should move from {starting energy} to {ending energy}. 
编曲应从 {起始能量} 逐渐推进到 {最终能量}。

The hook should appear {hook placement}. 
Hook 应该在 {Hook 出现位置} 出现。

The song is intended for {use case}. 
这首歌用于 {使用场景}。
```

### 11.2 Instrumental Structure + Arrangement Formula / 纯器乐结构 + 编曲公式

```text
Create a {genre} instrumental track for {use case}.
为 {使用场景} 创作一段 {曲风} 纯器乐音乐。

Instrumental only, no vocals, no rap, no spoken words.
纯器乐，无人声，无说唱，无旁白。

Use the following structure:
请使用以下结构：

[Intro - {texture / motif / 质感或动机}]
[Main Theme - {main melody / groove / 主旋律或律动}]
[Variation - {subtle change / 细微变化}]
[Breakdown - {reduced energy / 降低能量}]
[Final Section - {climax or return / 高潮或回归}]
[Outro / Loop Ending - {ending behavior / 结尾行为}]

The arrangement should be {energy curve}, with {instrumentation}. 
编曲应呈现 {能量曲线}，使用 {乐器配置}。

Make it {loop-friendly / narration-friendly / edit-friendly / brandable}.
请让它 {适合循环 / 适合旁白 / 适合剪辑 / 可品牌化}。
```

### 11.3 Short-Video Hook Formula / 短视频 Hook 公式

```text
Create a short, catchy {genre} track for short videos. 
为短视频创作一段短小抓耳的 {曲风} 音乐。

The hook should arrive within the first 3–8 seconds. 
Hook 应在前 3–8 秒内出现。

Use a short intro, clear rhythm, memorable melodic phrase, and loop-friendly ending.
使用短前奏、清晰节奏、有记忆点的旋律短句和可循环结尾。
```

### 11.4 Brand Film Formula / 品牌片公式

```text
Create a polished {genre} background track for a brand film.
为品牌片创作一段精致的 {曲风} 背景音乐。

Start with a clean motif, build gradually with subtle rhythm and harmonic layers, reach an uplifting climax, and end with a resolved logo-friendly final note.
以干净动机开场，通过细腻节奏和和声层逐步推进，到达振奋高潮，并以适合 Logo 的明确终止音收束。

Leave room for voiceover.
为旁白留出空间。
```

### 11.5 Sports Anthem Formula / 体育主题歌公式

```text
Create a powerful stadium anthem.
创作一首有力量的体育场主题歌。

Start with a chant or percussion motif, build with drums and brass, use group vocals in the chorus, add a chant-like post-chorus, and finish with a full crowd-style final chorus.
以 chant 或打击乐动机开场，用鼓和铜管推进，副歌使用群体人声，副歌后加入口号式 chant，并以完整观众合唱式最后副歌收束。
```

---

## 12. Skill Routing Logic / Skill 路由逻辑

### 12.1 If User Gives Only a Scene / 如果用户只给场景

Example / 示例：

> I want music for a tech product video.  
> 我想做一段科技产品视频音乐。

Infer / 推断：

```text
Track Type: instrumental / 纯器乐
Use Case: tech product background music / 科技产品背景音乐
Structure: [Intro] [Pulse Groove] [Build] [Main Theme] [Outro]
Arrangement: minimal synth pulse, clean beat, digital texture, premium mix
编曲：极简合成器脉冲、干净节拍、数字质感、高级混音
Negative: instrumental only, no vocals / 反向提示：纯器乐，无人声
```

### 12.2 If User Gives Scene + Wants Lyrics / 如果用户给场景且需要歌词

Example / 示例：

> I want a tech product theme song with lyrics.  
> 我想做一首有歌词的科技产品主题歌。

Infer / 推断：

```text
Track Type: vocal song / 带人声歌曲
Use Case: brand theme song / tech brand song / 品牌主题歌 / 科技品牌歌
Structure: [Intro] [Verse] [Pre-Chorus] [Chorus] [Bridge] [Final Chorus] [Outro]
Arrangement: clean electronic pop, synth pulse, polished drums, inspiring chorus
编曲：干净电子流行，合成器脉冲，精致鼓组，鼓舞型副歌
```

### 12.3 If User Says “BGM” / 如果用户说 “BGM”

Default to instrumental / 默认判定为纯器乐：

```text
instrumental only, no vocals, no rap, no spoken words
纯器乐，无人声，无说唱，无旁白
```

Then select use-case structure / 然后根据使用场景选择结构。

### 12.4 If User Says “Theme Song” / 如果用户说“主题曲”

Default to vocal song unless they specify instrumental.  
默认判定为带人声歌曲，除非用户明确说纯器乐。

### 12.5 If User Says “Short Video” / 如果用户说“短视频”

Ask or infer / 需要追问或推断：

```text
Do they want a vocal hook or instrumental BGM?
用户想要带人声 Hook，还是纯器乐 BGM？
```

If unclear, generate two options / 如果不清楚，可以输出两个选项：

1. vocal hook version / 带人声 Hook 版本  
2. instrumental BGM version / 纯器乐 BGM 版本

### 12.6 If User Says “Study / Work / Sleep” / 如果用户说“学习 / 工作 / 睡眠”

Always default to instrumental.  
始终默认纯器乐。

Use / 使用：

```text
non-intrusive, stable, loop-friendly, no vocals
不打扰，稳定，可循环，无人声
```

### 12.7 If User Says “Brand Promo” / 如果用户说“品牌宣传”

Ask or infer whether it is / 需要判断或追问是：

1. brand theme song with lyrics / 带歌词品牌主题歌  
2. background music for brand film / 品牌片背景音乐

If unclear, default to background music for brand film and offer theme-song alternative.  
如果不明确，默认品牌片背景音乐，同时提供品牌主题歌作为备选方向。

---

## 13. Integration with Other Libraries / 与其他素材库的关系

This library should call / 本库应调用：

```text
Genre Library → choose genre / 曲风库 → 选择曲风
Rhythm / BPM Library → choose tempo / 节奏 BPM 库 → 选择速度
Vocal Library → choose vocal style / 人声库 → 选择人声
Instrumentation Library → choose instruments / 乐器编曲库 → 选择乐器
Emotion Mapping Library → choose emotional curve / 情绪映射库 → 选择情绪曲线
Use Case Structure Library → choose section structure and arrangement plan / 场景结构库 → 选择结构与逐段编曲计划
```

Recommended order / 推荐调用顺序：

```text
Use Case → Track Type → Structure → Arrangement Plan → Genre → BPM → Vocal / No Vocal → Instrumentation → Emotion Curve → Final Prompt

使用场景 → 音乐类型 → 结构 → 编曲计划 → 曲风 → BPM → 人声 / 无人声 → 乐器 → 情绪曲线 → 最终 Prompt
```

---

## 14. Version Notes / 版本说明

v0.2 includes / v0.2 包含：

- full bilingual Chinese-English structure / 完整中英文双语结构
- vocal song vs instrumental routing / 带人声歌曲与纯器乐路由
- section function dictionary / 段落功能字典
- scene-based structure templates / 基于场景的结构模板
- section-by-section arrangement planning / 逐段编曲计划
- hook placement reference / Hook 出现位置参考
- length reference / 时长参考
- negative structure rules / 结构反向规则
- prompt formulas / Prompt 公式
- skill routing logic / Skill 路由逻辑

Future versions can add / 后续版本可增加：

- platform-specific structure tags for Suno / Udio / Suno / Udio 平台专用结构标签
- 15-second / 30-second / 60-second variations / 15 秒、30 秒、60 秒版本
- detailed Chinese lyric section templates / 中文歌词分段模板
- arrangement density levels / 编曲密度等级
- transition FX library / 转场音效库
- voiceover-friendly background music presets / 适合旁白的背景音乐预设
- multi-version output templates / 多版本输出模板
