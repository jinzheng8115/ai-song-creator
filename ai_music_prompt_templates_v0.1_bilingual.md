# AI Music Prompt Template Library v0.1 Bilingual  
# AI 音乐 Style Prompt / Lyrics Box / Iteration Prompt 模板库 v0.1 双语版

> Purpose / 用途：  
> This library is the final assembly layer for an interactive AI music prompt skill.  
> 本库是交互式 AI 音乐 Prompt Skill 的“最终组装层”。
>
> It converts decisions from the genre, BPM, vocal, instrumentation, emotion, and structure libraries into copy-ready prompts for AI music tools such as Suno, Udio, and similar platforms.  
> 它负责把曲风库、BPM 库、人声库、乐器编曲库、情绪库、场景结构库中的决策，组装成可以直接复制到 Suno、Udio 或类似 AI 音乐软件中的最终 Prompt。
>
> This library covers / 本库覆盖：
>
> 1. Style Prompt Templates / Style Prompt 模板  
> 2. Lyrics Box / Custom Lyrics Templates / 歌词框 / Custom Lyrics 模板  
> 3. Instrumental Custom Box Templates / 纯器乐 Custom Box 模板  
> 4. Iteration Prompt Templates / 迭代优化 Prompt 模板  
> 5. Negative Prompt / Avoid Templates / 避免项模板  
> 6. Final Output Package Templates / 最终输出包模板  

---

## 1. Core Prompt Architecture / 核心 Prompt 架构

AI music generation prompts should normally be separated into two layers:  
AI 音乐生成 Prompt 通常应拆成两个层次：

```text
1. Style Prompt / 风格提示词
2. Lyrics Box or Custom Lyrics / 歌词框或自定义歌词框
```

### 1.1 Style Prompt / 风格提示词

Style Prompt describes how the music should sound.  
Style Prompt 描述“音乐听起来应该是什么样”。

It should include / 应包含：

```text
Genre / 曲风
Mood / 情绪
Tempo or BPM / 速度或 BPM
Vocal Style / 人声风格
Instrumentation / 乐器配置
Arrangement / 编曲方式
Energy Curve / 能量曲线
Use Case / 使用场景
Production Texture / 制作质感
Avoid / 避免项
```

Style Prompt should **not** contain the full lyrics.  
Style Prompt 不应放完整歌词。

---

### 1.2 Lyrics Box / Custom Lyrics / 歌词框 / 自定义歌词

Lyrics Box controls the song content and section behavior.  
Lyrics Box 负责控制歌词内容、段落结构和每段的演唱 / 编曲行为。

It should include / 应包含：

```text
Top control tags / 顶部控制标签
Section tags / 段落标签
Lyrics / 歌词
Arrangement cues / 编曲提示
Vocal cues / 人声提示
Hook instructions / Hook 指令
```

For instrumental music, the Lyrics Box can be used as a structure and arrangement control box.  
对于纯器乐音乐，Lyrics Box 可以作为“结构 + 编曲指令框”，不写歌词。

---

## 2. Style Prompt Templates / Style Prompt 模板

### 2.1 Vocal Song Style Prompt Formula / 带人声歌曲 Style Prompt 公式

```text
Create a [language] [genre] song with a [mood] mood. 
Use [vocal style] vocals. 
The tempo should be [tempo / BPM]. 
The arrangement should include [instruments]. 
Start with [intro arrangement], then build into [chorus arrangement]. 
The emotional curve should move from [starting emotion] to [ending emotion]. 
The chorus should be [chorus direction]. 
The song is intended for [use case]. 
Avoid [negative elements].
```

中文说明：

```text
创作一首【语言】【曲风】歌曲，整体情绪是【情绪】。
使用【人声类型】。
速度为【节奏 / BPM】。
编曲包含【乐器】。
开头使用【前奏编曲】，随后推进到【副歌编曲】。
情绪曲线从【起始情绪】走向【最终情绪】。
副歌需要【副歌方向】。
歌曲用于【使用场景】。
避免【不希望出现的元素】。
```

---

### 2.2 Instrumental Style Prompt Formula / 纯器乐 Style Prompt 公式

```text
Create a [genre] instrumental track with a [mood] mood. 
Instrumental only, no vocals, no rap, no spoken words. 
The tempo should be [tempo / BPM]. 
Use [main instruments] with [production texture]. 
The arrangement should move from [starting energy] to [ending energy]. 
Make it [loop-friendly / voiceover-friendly / edit-friendly / brandable]. 
The track is intended for [use case]. 
Avoid [negative elements].
```

中文说明：

```text
创作一段【曲风】纯器乐音乐，整体情绪是【情绪】。
纯器乐，无人声，无说唱，无旁白。
速度为【节奏 / BPM】。
使用【主要乐器】和【制作质感】。
编曲应从【起始能量】推进到【最终能量】。
让它适合【循环 / 旁白 / 剪辑 / 品牌识别】。
这段音乐用于【使用场景】。
避免【不希望出现的元素】。
```

---

### 2.3 Short Video Style Prompt / 短视频 Style Prompt

```text
Create a short and catchy [genre] track for short videos. 
The hook should arrive within the first 3–8 seconds. 
Use [vocal style / instrumental motif], a clear rhythm, [instruments], and a loop-friendly ending. 
The mood should be [mood]. 
Keep the structure simple and memorable. 
Avoid long intros, slow builds, and complex lyrics.
```

中文说明：

```text
创作一段适合短视频的短小抓耳【曲风】音乐。
Hook 应在前 3–8 秒出现。
使用【人声风格 / 器乐动机】、清晰节奏、【乐器】和可循环结尾。
整体情绪为【情绪】。
结构要简单、有记忆点。
避免长前奏、慢铺垫和复杂歌词。
```

---

### 2.4 Brand Film Style Prompt / 品牌片 Style Prompt

```text
Create a polished [genre] background track for a brand film. 
Use [instruments] with a clean, premium production texture. 
Start with a recognizable motif, build gradually with subtle rhythm and harmonic layers, reach an uplifting climax, and end with a resolved logo-friendly final note. 
Leave room for voiceover. 
Avoid cluttered arrangement, cheap stock music feel, and unresolved endings.
```

中文说明：

```text
为品牌片创作一段精致的【曲风】背景音乐。
使用【乐器】，制作质感干净、高级。
以可识别动机开场，通过细腻节奏和和声层逐步推进，到达振奋高潮，并以适合 Logo 的明确终止音收束。
为旁白留出空间。
避免编曲拥挤、廉价素材音乐感和不解决结尾。
```

---

### 2.5 Sports Anthem Style Prompt / 体育主题歌 Style Prompt

```text
Create a powerful stadium anthem with an energetic and triumphant mood. 
Use a strong lead vocal, group vocals, and crowd chant. 
Medium-fast tempo around [BPM]. 
Start with stadium claps, big drums, and a short chant motif, then build with brass, electric guitar, percussion, and choir. 
The chorus should be simple, repeatable, and suitable for crowd singing. 
Avoid weak drums, complex lyrics, and slow cinematic intros.
```

中文说明：

```text
创作一首有力量的体育场主题歌，情绪高能、胜利、振奋。
使用强力主唱、群体人声和观众 chant。
速度为中快速，约【BPM】。
以体育场拍手、大鼓和短 chant 动机开场，然后用铜管、电吉他、打击乐和合唱推进。
副歌要简单、可重复、适合观众合唱。
避免鼓太弱、歌词太复杂和慢电影式前奏。
```

---

### 2.6 Study BGM Style Prompt / 学习 BGM Style Prompt

```text
Create a calm [genre] instrumental track for study and work background music. 
Instrumental only, no vocals, no rap, no spoken words. 
Use [instruments] with a warm and non-intrusive texture. 
The tempo should be [BPM] with a steady groove and subtle variations. 
Make it loop-friendly and suitable for long listening. 
Avoid sudden drops, dramatic transitions, strong hooks, and aggressive drums.
```

中文说明：

```text
创作一段适合学习和工作的平静【曲风】纯器乐背景音乐。
纯器乐，无人声，无说唱，无旁白。
使用【乐器】，质感温暖、不打扰。
速度为【BPM】，律动稳定，并有细微变化。
适合循环和长时间聆听。
避免突然 Drop、戏剧化转场、强 Hook 和攻击性鼓组。
```

---

## 3. Lyrics Box Templates / Lyrics Box 模板

### 3.1 Vocal Song Lyrics Box Template / 带人声歌曲 Lyrics Box 模板

```text
[Style: {genre}, {mood}, {tempo}]
[Vocal: {vocal style}]
[Arrangement: {instrumentation and arrangement plan}]
[Energy: {energy curve}]
[Use Case: {use case}]

[Intro - {intro arrangement}]
{intro lyric or short vocal phrase}

[Verse 1 - {verse arrangement}]
{lyrics}

[Pre-Chorus - {build arrangement}]
{lyrics}

[Chorus - {chorus arrangement and hook instruction}]
{lyrics}

[Verse 2 - {verse 2 arrangement}]
{lyrics}

[Bridge - {bridge arrangement}]
{lyrics}

[Final Chorus - {final chorus arrangement}]
{lyrics}

[Outro - {outro arrangement}]
{lyrics}
```

中文说明：

```text
[Style: 曲风、情绪、速度]
[Vocal: 人声类型]
[Arrangement: 乐器与编曲计划]
[Energy: 情绪与能量曲线]
[Use Case: 使用场景]

[Intro - 前奏编曲提示]
前奏歌词或短人声

[Verse 1 - 第一段主歌编曲提示]
歌词

[Pre-Chorus - 副歌前段推进提示]
歌词

[Chorus - 副歌编曲与 Hook 指令]
歌词

[Verse 2 - 第二段主歌编曲提示]
歌词

[Bridge - 桥段编曲提示]
歌词

[Final Chorus - 最后副歌编曲提示]
歌词

[Outro - 尾奏编曲提示]
歌词
```

---

### 3.2 Short Video Hook Lyrics Box / 短视频 Hook Lyrics Box

```text
[Style: {genre}, short video hook, {mood}, {tempo}]
[Vocal: {vocal style}]
[Arrangement: short intro, clear rhythm, hook arrives immediately]
[Use Case: short video / social media]
[Length: 20–45 seconds]

[Hook - start immediately with the catchiest phrase]
{hook lyric}

[Verse - short setup, 2–4 lines]
{short verse lyric}

[Chorus - repeatable hook, full beat]
{chorus lyric}

[Outro - loop-friendly ending]
{ending hook phrase}
```

中文说明：

```text
[Style: 曲风，短视频 Hook，情绪，速度]
[Vocal: 人声类型]
[Arrangement: 短前奏，节奏清晰，Hook 立即出现]
[Use Case: 短视频 / 社交媒体]
[Length: 20–45 秒]

[Hook - 直接以最抓耳短句开场]
Hook 歌词

[Verse - 2–4 句短铺垫]
短主歌歌词

[Chorus - 可重复 Hook，完整节奏]
副歌歌词

[Outro - 可循环结尾]
结尾 Hook 短句
```

---

### 3.3 Sports Anthem Lyrics Box / 体育主题歌 Lyrics Box

```text
[Style: stadium anthem, energetic, triumphant, medium-fast tempo]
[Vocal: powerful lead vocal, group vocals, crowd chant]
[Arrangement: big drums, brass, electric guitar, percussion, choir]
[Energy: chant intro, rising verse, huge chorus, crowd finale]
[Use Case: sports event / World Cup / highlight video]

[Intro - Stadium Chant]
{short chant phrase}

[Verse - Percussion Groove]
{verse lyrics}

[Pre-Chorus - Rising Crowd]
{pre-chorus lyrics}

[Chorus - Group Vocal, simple repeatable hook]
{chorus lyrics}

[Post-Chorus - Chant Hook]
{chant phrase}

[Bridge - Clap Breakdown, call-and-response]
{bridge lyrics}

[Final Chorus - Crowd Chant, full energy]
{final chorus lyrics}

[Outro - Final Chant]
{final chant phrase}
```

中文说明：

```text
[Style: 体育场主题歌，高能，胜利感，中快速]
[Vocal: 强力主唱，群体人声，观众 chant]
[Arrangement: 大鼓，铜管，电吉他，打击乐，合唱]
[Energy: chant 前奏，主歌抬升，大副歌，观众式收尾]
[Use Case: 体育赛事 / 世界杯 / 高光视频]

[Intro - 体育场 chant]
短 chant 口号

[Verse - 打击乐律动主歌]
主歌歌词

[Pre-Chorus - 群体抬升段]
副歌前段歌词

[Chorus - 群体人声，简单可重复 Hook]
副歌歌词

[Post-Chorus - 口号 Hook]
chant 短句

[Bridge - 拍手减法，呼应式]
桥段歌词

[Final Chorus - 观众 chant，全能量]
最后副歌歌词

[Outro - 最终 chant]
最终口号短句
```

---

### 3.4 Children’s Song Lyrics Box / 儿童歌曲 Lyrics Box

```text
[Style: children’s song, bright, playful, simple melody]
[Vocal: cheerful vocal, children’s choir if needed]
[Arrangement: ukulele, hand claps, toy piano, bells, light drums]
[Energy: cheerful from start to end]
[Use Case: children’s education / family-friendly]

[Intro - bright motif]
{short intro phrase}

[Verse - simple teaching point]
{simple lyrics}

[Chorus - repeated learning phrase]
{chorus lyrics}

[Repeat Chorus - reinforce memory]
{repeat chorus lyrics}

[Outro - friendly ending]
{ending lyric}
```

中文说明：

```text
[Style: 儿童歌，明亮，俏皮，简单旋律]
[Vocal: 愉快人声，如需要可用儿童合唱]
[Arrangement: 尤克里里，拍手，玩具钢琴，铃声，轻鼓]
[Energy: 从头到尾愉快]
[Use Case: 儿童教育 / 亲子友好]

[Intro - 明亮动机]
短前奏句

[Verse - 简单知识点]
简单歌词

[Chorus - 重复学习短句]
副歌歌词

[Repeat Chorus - 强化记忆]
重复副歌歌词

[Outro - 友好结尾]
结尾歌词
```

---

## 4. Instrumental Custom Box Templates / 纯器乐 Custom Box 模板

### 4.1 General Instrumental Custom Box / 通用纯器乐 Custom Box

```text
[Instrumental Only]
[No vocals, no rap, no spoken words]
[Style: {instrumental genre}, {mood}, {tempo}]
[Instrumentation: {instruments}]
[Use Case: {use case}]
[Energy: {energy curve}]
[Loopability: {loop-friendly / edit-friendly / voiceover-friendly / brandable}]

[Intro - {intro texture}]
[Main Theme - {main motif}]
[Variation - {subtle variation}]
[Breakdown - {reduced arrangement}]
[Final Section - {climax or return}]
[Outro / Loop Ending - {ending behavior}]
```

中文说明：

```text
[Instrumental Only / 纯器乐]
[No vocals, no rap, no spoken words / 无人声，无说唱，无旁白]
[Style: 器乐曲风，情绪，速度]
[Instrumentation: 乐器配置]
[Use Case: 使用场景]
[Energy: 能量曲线]
[Loopability: 可循环 / 适合剪辑 / 适合旁白 / 可品牌化]

[Intro - 引入质感]
[Main Theme - 主动机]
[Variation - 细微变化]
[Breakdown - 降低密度]
[Final Section - 高潮或回归]
[Outro / Loop Ending - 结尾行为]
```

---

### 4.2 Lo-fi Study BGM Custom Box / Lo-fi 学习 BGM Custom Box

```text
[Instrumental Only]
[No vocals, no rap, no spoken words]
[Style: lo-fi hip-hop instrumental, healing, calm, 75 BPM]
[Instrumentation: soft piano, mellow bass, dusty drums, vinyl crackle, warm tape texture]
[Use Case: study and work background music]
[Energy: steady, calm, non-intrusive]
[Loopability: seamless loop-friendly ending]

[Intro - soft piano chords with vinyl crackle]
[Main Loop - mellow drums, warm bass, simple piano motif]
[Subtle Variation - add light keys and small percussion]
[Breakdown - remove drums briefly, keep pad and piano motif]
[Main Loop Return - bring drums and bass back gently]
[Loop Ending - return to the main piano motif without hard resolution]
```

中文说明：

```text
[Instrumental Only / 纯器乐]
[No vocals, no rap, no spoken words / 无人声，无说唱，无旁白]
[Style: Lo-fi Hip-hop 器乐，治愈，平静，75 BPM]
[Instrumentation: 柔和钢琴，温暖贝斯，颗粒感鼓组，黑胶噪声，磁带质感]
[Use Case: 学习和工作背景音乐]
[Energy: 稳定，平静，不打扰]
[Loopability: 无缝循环友好]

[Intro - 带黑胶噪声的柔和钢琴和弦]
[Main Loop - 柔和鼓组，温暖贝斯，简单钢琴动机]
[Subtle Variation - 加入轻键盘和小打击乐]
[Breakdown - 短暂去掉鼓，保留 pad 和钢琴动机]
[Main Loop Return - 温和带回鼓和贝斯]
[Loop Ending - 回到主钢琴动机，不做强终止]
```

---

### 4.3 Tech Product BGM Custom Box / 科技产品 BGM Custom Box

```text
[Instrumental Only]
[No vocals, no rap, no spoken words]
[Style: minimal electronic, futuristic, premium, 105 BPM]
[Instrumentation: pulsing synths, minimal electronic drums, soft sub bass, digital pads]
[Use Case: tech product video]
[Energy: precise, clean, optimistic, premium]
[Voiceover: leave room for voiceover]

[Intro - clean digital texture and soft synth pulse]
[Pulse Groove - minimal beat and sub bass]
[Build - add arpeggio and brighter synth layers]
[Main Theme - memorable but non-distracting synth motif]
[Outro - clean resolved logo-friendly ending]
```

中文说明：

```text
[Instrumental Only / 纯器乐]
[No vocals, no rap, no spoken words / 无人声，无说唱，无旁白]
[Style: 极简电子，未来感，高级，105 BPM]
[Instrumentation: 脉冲合成器，极简电子鼓，柔和低频贝斯，数字 pad]
[Use Case: 科技产品视频]
[Energy: 精准，干净，积极，高级]
[Voiceover: 为旁白留空间]

[Intro - 干净数字质感与柔和合成器脉冲]
[Pulse Groove - 极简节拍和低频贝斯]
[Build - 加入琶音和更明亮合成器层]
[Main Theme - 有记忆点但不打扰的合成器动机]
[Outro - 干净解决，适合 Logo 收尾]
```

---

### 4.4 Brand Film BGM Custom Box / 品牌片 BGM Custom Box

```text
[Instrumental Only]
[No vocals, no rap, no spoken words]
[Style: cinematic corporate pop instrumental, uplifting, premium, 100 BPM]
[Instrumentation: clean piano, subtle synths, soft drums, warm strings, polished bass]
[Use Case: brand film background music]
[Energy: clean opening, steady build, uplifting climax]
[Voiceover: leave room for voiceover]

[Intro - clean piano motif and subtle ambient texture]
[Build - add soft pulse, bass, and light percussion]
[Main Theme - polished melody with warm harmony]
[Climax - cinematic strings, bigger drums, wider mix]
[Outro - resolved logo-friendly final note]
```

中文说明：

```text
[Instrumental Only / 纯器乐]
[No vocals, no rap, no spoken words / 无人声，无说唱，无旁白]
[Style: 电影感企业流行器乐，振奋，高级，100 BPM]
[Instrumentation: 干净钢琴，轻合成器，柔和鼓组，温暖弦乐，精致贝斯]
[Use Case: 品牌片背景音乐]
[Energy: 干净开场，稳定推进，振奋高潮]
[Voiceover: 为旁白留空间]

[Intro - 干净钢琴动机和轻氛围质感]
[Build - 加入柔和脉冲、贝斯和轻打击乐]
[Main Theme - 精致旋律与温暖和声]
[Climax - 电影感弦乐、更大鼓组、更宽声场]
[Outro - 适合 Logo 的明确终止音]
```

---

## 5. Iteration Prompt Templates / 迭代优化 Prompt 模板

AI music generation is usually a multi-round process.  
AI 音乐生成通常不是一次成功，而是多轮调整。

Iteration prompts should be copy-ready.  
迭代 Prompt 必须是用户可以直接复制的句子。

---

### 5.1 Style Iteration / 曲风调整

```text
Make the song sound more like [genre / style direction], while keeping the same theme and lyrics.
```

中文：

```text
在保持主题和歌词不变的基础上，让歌曲更接近【曲风方向】。
```

Example / 示例：

```text
Make the song sound more like a warm Chinese pop ballad, with less electronic production and more piano, acoustic guitar, and strings.
让歌曲更接近温暖的中文流行抒情，减少电子制作感，增加钢琴、原声吉他和弦乐。
```

---

### 5.2 Vocal Iteration / 人声调整

```text
Make the vocal more [target vocal quality], less [unwanted vocal quality].
```

中文：

```text
让人声更【目标人声质感】，减少【不想要的人声质感】。
```

Examples / 示例：

```text
Make the vocal more natural and emotionally restrained, less theatrical and less exaggerated.
让人声更自然、更克制有情绪，减少戏剧化和夸张唱法。
```

```text
Make the vocal warmer and more intimate, with a close-mic feeling and less reverb.
让人声更温暖、更亲密，有贴耳录音感，减少混响。
```

```text
Make the vocal more powerful and anthem-like, suitable for a stadium chorus.
让人声更有力量、更像主题歌，适合体育场合唱副歌。
```

---

### 5.3 Lyrics Iteration / 歌词调整

```text
Make the lyrics more singable, with shorter lines, clearer imagery, and less abstract language.
```

中文：

```text
让歌词更适合演唱，句子更短，画面更清楚，减少抽象表达。
```

More examples / 更多示例：

```text
Make the lyrics less slogan-like and more emotional, with concrete scenes and natural language.
让歌词少一点口号感，多一点情绪和具体画面，语言更自然。
```

```text
Make the lyrics more suitable for Chinese pop singing, with smoother phrasing and a stronger chorus hook.
让歌词更适合中文流行歌演唱，断句更顺，副歌 Hook 更强。
```

---

### 5.4 Chorus / Hook Iteration / 副歌与 Hook 调整

```text
Make the chorus more catchy, memorable, and easier to sing along to.
Bring the hook earlier and make the main phrase repeat more naturally.
```

中文：

```text
让副歌更抓耳、更有记忆点、更适合跟唱。
让 Hook 更早出现，并让核心短句更自然地重复。
```

More examples / 更多示例：

```text
Make the chorus bigger and more emotionally uplifting, with fuller drums, strings, and backing vocals.
让副歌更大、更振奋，加入更丰满的鼓组、弦乐和和声。
```

```text
Make the hook appear within the first 5 seconds and keep it simple enough for short-video use.
让 Hook 在前 5 秒内出现，并保持足够简单，适合短视频使用。
```

---

### 5.5 Arrangement Iteration / 编曲调整

```text
Make the arrangement build more clearly from sparse verses to a fuller chorus.
Add [instrument] in the chorus and reduce [unwanted element].
```

中文：

```text
让编曲从克制主歌到丰满副歌的推进更清楚。
在副歌加入【乐器】，减少【不需要的元素】。
```

Examples / 示例：

```text
Make the verses more intimate with only piano and acoustic guitar, then add drums, bass, and strings in the chorus.
让主歌更亲密，只保留钢琴和原声吉他；副歌再加入鼓、贝斯和弦乐。
```

```text
Make the final chorus bigger, with wider strings, stronger drums, and subtle backing vocals.
让最后副歌更大，加入更宽的弦乐、更强的鼓组和轻和声。
```

---

### 5.6 Tempo / BPM Iteration / 节奏与 BPM 调整

```text
Make the tempo slightly slower and more emotional, around [BPM] BPM.
```

中文：

```text
让速度稍微慢一点，更有情绪，约【BPM】BPM。
```

Examples / 示例：

```text
Make it more upbeat and suitable for short videos, around 120 BPM, with a clearer rhythm.
让它更明快，更适合短视频，约 120 BPM，节奏更清晰。
```

```text
Make the groove more laid-back and relaxed, around 80 BPM.
让律动更松弛、更放松，约 80 BPM。
```

---

### 5.7 Emotion Iteration / 情绪调整

```text
Make the mood more [target emotion], while keeping the song structure and main melody direction.
```

中文：

```text
在保持歌曲结构和主旋律方向的基础上，让整体情绪更【目标情绪】。
```

Examples / 示例：

```text
Make the song warmer and more hopeful, less sad and less dark.
让歌曲更温暖、更有希望感，减少伤感和暗色。
```

```text
Make it more cinematic and emotional, with a stronger build toward the final chorus.
让它更有电影感和情绪推进，最后副歌的抬升更强。
```

---

### 5.8 Structure Iteration / 结构调整

```text
Bring the chorus earlier and shorten the intro.
```

中文：

```text
让副歌更早出现，并缩短前奏。
```

More examples / 更多示例：

```text
Add a short pre-chorus to build tension before the chorus.
在副歌前增加一个短 Pre-Chorus，用来制造张力。
```

```text
Add a breakdown bridge before the final chorus, reducing the arrangement to piano and vocal only.
在最后副歌前增加一个减法桥段，只保留钢琴和人声。
```

---

### 5.9 Instrumental Iteration / 纯器乐调整

```text
Make it more suitable as background music: less distracting, more loop-friendly, no vocals, no rap, no spoken words.
```

中文：

```text
让它更适合作为背景音乐：减少打扰，更适合循环，无人声、无说唱、无旁白。
```

More examples / 更多示例：

```text
Make the instrumental more loop-friendly, with a seamless ending that returns to the main motif.
让这段器乐更适合循环，结尾无缝回到主动机。
```

```text
Make it more voiceover-friendly by reducing busy lead melodies and leaving more space in the midrange.
让它更适合旁白，减少繁忙主旋律，在中频留出更多空间。
```

```text
Make the track more edit-friendly, with clearer impact points every 8 bars.
让音乐更适合剪辑，每 8 小节有更清晰的冲击点。
```

---

### 5.10 Commercial / Use-Case Iteration / 商业与场景适配调整

```text
Make it more suitable for [use case], with [scene-specific requirement].
```

中文：

```text
让它更适合【使用场景】，并具备【场景特定要求】。
```

Examples / 示例：

```text
Make it more suitable for a brand film: premium, polished, uplifting, and not too distracting under voiceover.
让它更适合品牌片：高级、精致、振奋，并且在旁白下不抢戏。
```

```text
Make it more suitable for sports highlights: stronger drums, bigger impacts, and more tension before the drop.
让它更适合体育高光：鼓更强，冲击点更大，Drop 前张力更明显。
```

```text
Make it more suitable for a wedding video: warmer, more romantic, and less dramatic.
让它更适合婚礼视频：更温暖、更浪漫，减少戏剧化冲突。
```

---

## 6. Negative Prompt / Avoid Templates / 避免项模板

### 6.1 General Avoid Formula / 通用避免项公式

```text
Avoid [unwanted instruments], [unwanted vocal quality], [unwanted arrangement behavior], and [unwanted mood].
```

中文：

```text
避免【不需要的乐器】、【不想要的人声质感】、【不想要的编曲行为】和【不想要的情绪】。
```

---

### 6.2 Common Avoid Phrases / 常见避免项

```text
Avoid aggressive drums, harsh synths, overly theatrical vocals, and long instrumental intros.
避免攻击性鼓组、刺耳合成器、过度戏剧化人声和过长器乐前奏。
```

```text
Avoid generic stock music feel, cluttered arrangement, and unresolved ending.
避免通用素材音乐感、拥挤编曲和不解决结尾。
```

```text
Avoid vocals, rap, spoken words, sudden drops, and dramatic transitions.
避免人声、说唱、旁白、突然 Drop 和戏剧化转场。
```

```text
Avoid copying any real artist’s voice, melody, or lyrics.
避免模仿任何真实歌手的声音、旋律或歌词。
```

---

### 6.3 Scene-Based Avoid Map / 按场景的避免项

| Scene / 场景 | Avoid / 避免 |
|---|---|
| Short video / 短视频 | long intro, hook too late, slow build / 长前奏、Hook 太晚、慢铺垫 |
| Study BGM / 学习 BGM | vocals, rap, spoken words, sudden drops / 人声、说唱、旁白、突然 Drop |
| Brand film / 品牌片 | cheap stock music feel, cluttered arrangement, unresolved ending / 廉价素材音乐感、编曲拥挤、结尾不解决 |
| Sports anthem / 体育主题歌 | weak drums, complex lyrics, no chant / 鼓太弱、歌词复杂、没有 chant |
| Wedding / 婚礼 | aggressive drums, dark lyrics, tragic ending / 攻击性鼓组、黑暗歌词、悲剧结尾 |
| Children’s song / 儿童歌曲 | complex metaphors, dark mood, intense bass / 复杂隐喻、黑暗情绪、强低频 |
| Tech product / 科技产品 | rustic acoustic-only, club drop, overly emotional strings / 纯乡村原声、夜店 Drop、过度情绪弦乐 |
| Instrumental BGM / 纯器乐 BGM | vocals, rap, spoken words, lead singing / 人声、说唱、旁白、主唱 |

---

## 7. Final Output Package Templates / 最终输出包模板

### 7.1 A. Simple Prompt / A. 简洁版 Prompt

```markdown
## Style Prompt / 风格提示词

{style_prompt}

## Lyrics Box / Custom Box / 歌词框 / 自定义框

{lyrics_box}
```

Use when / 适用于：

```text
User wants quick copy-ready output.
用户只想快速复制使用。
```

---

### 7.2 B. Complete AI Music Prompt Package / B. 完整 AI 音乐 Prompt 包

```markdown
# AI Music Prompt Package / AI 音乐 Prompt 包

## 1. Requirement Summary / 需求摘要

- Theme / 主题:
- Use Case / 使用场景:
- Track Type / 音乐类型:
- Language / 语言:
- Genre / 曲风:
- Mood / 情绪:
- Tempo / BPM / 速度:
- Vocal / 人声:
- Instrumentation / 乐器:
- Output Format / 输出格式:

## 2. Music Direction / 音乐方向

{direction_summary}

## 3. Title Options / 歌名建议

{title_options}

## 4. Style Prompt / 风格提示词

{style_prompt}

## 5. Lyrics Box / Custom Lyrics / 歌词框 / 自定义歌词

{lyrics_box}

## 6. Iteration Prompts / 迭代优化 Prompt

{iteration_prompts}

## 7. Usage Notes / 使用提醒

{usage_notes}
```

Use as default / 默认使用这个格式。

---

### 7.3 C. Lyrics + Style Prompt / C. 歌词 + Style Prompt

```markdown
## Lyrics / 歌词

{lyrics}

## Style Prompt / 风格提示词

{style_prompt}
```

Use when / 适用于：

```text
User already understands AI music tools and only needs lyrics plus style.
用户已经熟悉 AI 音乐工具，只需要歌词和风格提示。
```

---

### 7.4 D. Multi-Style Versions / D. 多风格版本

```markdown
# Multi-Style AI Music Prompt Package / 多风格 AI 音乐 Prompt 包

## Version 1: Mainstream Pop / 版本 1：大众流行版

### Style Prompt / 风格提示词
{style_prompt_1}

### Lyrics Box / 歌词框
{lyrics_box_1}

## Version 2: Short-Video Viral / 版本 2：短视频传播版

### Style Prompt / 风格提示词
{style_prompt_2}

### Lyrics Box / 歌词框
{lyrics_box_2}

## Version 3: Cinematic Premium / 版本 3：电影感高级版

### Style Prompt / 风格提示词
{style_prompt_3}

### Lyrics Box / 歌词框
{lyrics_box_3}
```

Use when / 适用于：

```text
User is unsure about style or wants several creative directions.
用户不确定曲风，或希望比较多个创作方向。
```

---

### 7.5 E. 30-Second Hook Package / E. 30 秒 Hook 包

```markdown
# 30-Second Hook Prompt Package / 30 秒 Hook Prompt 包

## 1. Hook Concept / Hook 概念

{hook_concept}

## 2. Style Prompt / 风格提示词

{style_prompt}

## 3. Lyrics Box / 歌词框

{short_lyrics_box}

## 4. Iteration Prompts / 迭代优化 Prompt

{hook_iteration_prompts}
```

Use when / 适用于：

```text
User wants short-video music, viral hook, teaser, ad hook, or social media snippet.
用户想要短视频音乐、爆款 Hook、预告片段、广告短句或社交媒体片段。
```

---

## 8. Template Selection Logic / 模板选择逻辑

### 8.1 If User Wants a Song with Lyrics / 如果用户要带歌词歌曲

Use / 使用：

```text
Vocal Song Style Prompt
Vocal Song Lyrics Box
Vocal Iteration Prompts
Lyrics Iteration Prompts
Chorus / Hook Iteration Prompts
```

### 8.2 If User Wants Instrumental / 如果用户要纯器乐

Use / 使用：

```text
Instrumental Style Prompt
Instrumental Custom Box
Instrumental Iteration Prompts
Background Music Avoid Templates
```

Add fixed phrase / 加入固定表达：

```text
instrumental only, no vocals, no rap, no spoken words
纯器乐，无人声，无说唱，无旁白
```

### 8.3 If User Wants Short Video / 如果用户要短视频

Ask or infer / 询问或推断：

```text
Vocal hook or instrumental BGM?
带人声 Hook，还是纯器乐 BGM？
```

If unclear, provide two versions / 如果不明确，提供两个版本：

```text
1. Vocal Hook Version / 带人声 Hook 版本
2. Instrumental BGM Version / 纯器乐 BGM 版本
```

### 8.4 If User Wants Brand Music / 如果用户要品牌音乐

Ask or infer / 询问或推断：

```text
Brand theme song with lyrics or brand film background music?
带歌词品牌主题歌，还是品牌片背景音乐？
```

If unclear, default to brand film BGM and offer theme-song alternative.  
如果不明确，默认品牌片背景音乐，同时提供主题歌备选。

### 8.5 If User Wants Study / Work / Sleep Music / 如果用户要学习 / 工作 / 睡眠音乐

Default to instrumental.  
默认纯器乐。

Use / 使用：

```text
Study BGM Style Prompt
General Instrumental Custom Box
No vocals fixed negative prompt
Loop-friendly instruction
```

### 8.6 If User Wants Sports / World Cup / Event Anthem / 如果用户要体育 / 世界杯 / 活动主题

Default to vocal anthem unless user says BGM.  
默认带人声主题歌，除非用户说 BGM。

Use / 使用：

```text
Sports Anthem Style Prompt
Sports Anthem Lyrics Box
Chant / Group Vocal Iteration Prompts
```

---

## 9. Usage Notes Template / 使用提醒模板

### 9.1 Copyright / Voice Safety / 版权与声音安全

```text
Do not directly copy a real artist’s voice, melody, or lyrics. Use abstract style descriptions instead, such as “nostalgic 1990s pop ballad feeling” or “cinematic stadium anthem”.
```

中文：

```text
不要直接模仿真实歌手的声音、旋律或歌词。可以改用抽象风格描述，例如“90 年代怀旧流行抒情感”或“电影感体育场主题歌”。
```

### 9.2 Commercial Use / 商业使用

```text
If this music will be used commercially, check the commercial-use rules of the AI music platform before publishing.
```

中文：

```text
如果音乐用于商业发布，请在发布前确认所使用 AI 音乐平台的商业授权规则。
```

### 9.3 Iteration Advice / 迭代建议

```text
AI music generation often requires multiple attempts. Generate 3–5 versions first, then use the iteration prompts to refine vocal, chorus, arrangement, tempo, and mood.
```

中文：

```text
AI 音乐生成通常需要多次尝试。建议先生成 3–5 个版本，再用迭代 Prompt 调整人声、副歌、编曲、速度和情绪。
```

---

## 10. Examples / 示例

### 10.1 Example: Personal Chinese Pop Ballad / 示例：个人故事中文流行抒情

Style Prompt / 风格提示词：

```text
Create a Chinese pop ballad with a warm and bittersweet mood. Use a mature emotional male vocal with natural, restrained delivery. Medium-slow tempo around 80–90 BPM. Start with soft piano and acoustic guitar, then gradually add warm bass, light drums, and cinematic strings in the chorus. The emotional curve should move from quiet reflection to hopeful release. The chorus should be memorable, sincere, and suitable for personal sharing. Avoid aggressive drums, overly theatrical singing, and excessive electronic effects.
```

Lyrics Box / 歌词框：

```text
[Style: Chinese pop ballad, warm, bittersweet, 85 BPM]
[Vocal: mature emotional male vocal, natural and restrained]
[Arrangement: soft piano and acoustic guitar in verse, warm bass, light drums, cinematic strings in chorus]
[Energy: quiet reflection to hopeful release]
[Use Case: personal sharing]

[Intro - soft piano motif]
夜还没亮
风吹过这座城

[Verse 1 - sparse piano and acoustic guitar]
最后一班地铁开走了
我站在灯影里沉默
手机里还有没回的问候
像远方轻轻闪烁

[Pre-Chorus - add light drums and subtle strings]
有些梦被生活磨旧
有些话没说出口
可我还想往前走
哪怕慢一点也足够

[Chorus - full drums, bass, strings, memorable hook]
我走在没亮的城里
把梦藏进风衣
就算世界太拥挤
也要给自己一束光明

[Outro - return to piano motif]
夜会过去
天总会亮起
```

---

### 10.2 Example: Instrumental Tech Product BGM / 示例：科技产品纯器乐 BGM

Style Prompt / 风格提示词：

```text
Create a clean futuristic minimal electronic instrumental for a tech product video. Instrumental only, no vocals, no rap, no spoken words. Medium tempo around 105 BPM. Use pulsing synths, minimal electronic drums, soft sub bass, digital pads, and a polished premium mix. The arrangement should feel precise, optimistic, and non-intrusive, leaving room for voiceover. Avoid club drops, aggressive bass, and overly emotional strings.
```

Custom Box / 自定义框：

```text
[Instrumental Only]
[No vocals, no rap, no spoken words]
[Style: minimal electronic, futuristic, premium, 105 BPM]
[Instrumentation: pulsing synths, minimal electronic drums, soft sub bass, digital pads]
[Use Case: tech product video]
[Energy: precise, clean, optimistic, premium]
[Voiceover: leave room for voiceover]

[Intro - clean digital texture and soft synth pulse]
[Pulse Groove - minimal beat and sub bass]
[Build - add arpeggio and brighter synth layers]
[Main Theme - memorable but non-distracting synth motif]
[Outro - clean resolved logo-friendly ending]
```

---

## 11. Version Notes / 版本说明

v0.1 includes / v0.1 包含：

- bilingual Style Prompt templates / 中英文 Style Prompt 模板
- bilingual Lyrics Box templates / 中英文 Lyrics Box 模板
- instrumental custom box templates / 纯器乐 Custom Box 模板
- iteration prompt templates / 迭代优化 Prompt 模板
- negative prompt / avoid templates / 避免项模板
- final output package templates / 最终输出包模板
- template selection logic / 模板选择逻辑
- usage notes / 使用提醒

Future versions can add / 后续版本可增加：

- platform-specific Suno / Udio variants / Suno / Udio 平台专用版本
- shorter 15-second, 30-second, 60-second template variants / 15 秒、30 秒、60 秒模板
- lyric language style templates / 歌词语言风格模板
- title-generation templates / 歌名生成模板
- multi-version prompt templates / 多版本 Prompt 模板
- prompt scoring checklist / Prompt 质量评分清单
