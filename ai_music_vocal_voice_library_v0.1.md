# AI Music Vocal & Voice Description Library v0.1

> 用途：作为交互式 AI 音乐 Prompt Skill 的“人声与嗓音描述库”。本库用于把用户口语化表达，例如“温暖男声”“空灵女声”“适合世界杯大合唱”“不要太油腻”，转译成 Suno / Udio / 类 Suno 工具可使用的 vocal prompt 描述。

---

## 1. 设计原则

AI 音乐 Prompt 中的人声描述不应该只写 `male vocal` 或 `female vocal`。更稳定的表达应包含：

```text
Gender / Age Feel + Tone Color + Singing Style + Emotion + Genre Fit + Production Texture
```

例如：

```text
warm mature male vocal, natural and restrained delivery, emotional but not theatrical, suitable for Chinese pop ballad
```

或者：

```text
clear youthful female vocal, bright and airy tone, catchy pop delivery, suitable for short-video hook
```

对于零基础用户，交互时使用中文选项；最终生成 Prompt 时转成英文描述。

---

## 2. 人声字段结构

每一种人声建议按以下字段保存：

```text
Voice ID:
中文名：
英文 Prompt 标签：
适合曲风：
适合主题：
适合场景：
情绪关键词：
音色特点：
演唱方式：
制作质感：
避免项：
示例 Prompt：
```

---

## 3. 用户语言到 Prompt 的基础映射

| 用户说法 | Prompt 转译 |
|---|---|
| 温暖男声 | warm male vocal, soft emotional delivery |
| 成熟男声 | mature emotional male vocal, storytelling delivery |
| 沙哑男声 | slightly raspy male vocal, gritty emotional tone |
| 低沉男声 | deep male vocal, intimate and grounded tone |
| 少年感男声 | youthful male vocal, clear and bright tone |
| 清澈女声 | clear female vocal, bright and pure tone |
| 温柔女声 | soft female vocal, gentle emotional delivery |
| 空灵女声 | ethereal female vocal, airy and cinematic tone |
| 有力量女声 | powerful female vocal, soaring chorus delivery |
| 甜美女声 | sweet female vocal, bright pop tone |
| 烟嗓 | smoky vocal tone, slightly raspy and intimate |
| 故事感 | narrative vocal delivery, emotional storytelling |
| 克制 | restrained vocal performance, natural and subtle |
| 爆发 | powerful chorus vocal, emotional climax |
| 合唱 | group vocals / choir vocals |
| 体育大合唱 | stadium chant vocals, crowd sing-along chorus |
| 儿童合唱 | children’s choir, bright and playful |
| 说唱 | rap vocal, rhythmic flow |
| 旁白式 | spoken-word vocal, narrative tone |
| 男女对唱 | male and female duet |
| 无人声 | instrumental only, no vocals |

---

## 4. 基础声部参考

> 本节用于 Skill 内部理解，不建议在面向零基础用户时直接暴露太多古典声部术语。

| 声部 | 常见范围参考 | Prompt 使用建议 |
|---|---|---|
| Soprano / 女高音 | 高女声 | soprano-like female vocal, bright high register |
| Mezzo-soprano / 女中音 | 中高女声 | warm mezzo female vocal, balanced tone |
| Alto / 女低音 | 较低女声 | alto female vocal, rich lower tone |
| Tenor / 男高音 | 高男声 | tenor male vocal, bright upper register |
| Baritone / 男中音 | 中低男声 | baritone male vocal, warm and grounded |
| Bass / 男低音 | 低男声 | deep bass male vocal, low resonant tone |

在流行音乐 Prompt 里，通常不需要写精确音域。更建议写“tone + emotion + delivery”，例如 `warm baritone-like male vocal`，而不是只写 `baritone`。

---

# 5. Vocal Song Voice Library / 带人声歌曲嗓音库

## 5.1 Male Vocal / 男声类

### 5.1.1 Warm Male Vocal / 温暖男声

- **Voice ID**: `warm_male_vocal`
- **英文标签**: warm male vocal, soft emotional male vocal
- **适合曲风**: Chinese pop ballad, folk-pop, acoustic pop, soft rock
- **适合主题**: 亲情、成长、城市奋斗、中年人生、陪伴
- **适合场景**: 朋友圈、短视频、个人纪念、公众号配乐
- **情绪关键词**: warm, sincere, emotional, hopeful
- **音色特点**: 柔和、亲近、不过度炫技
- **演唱方式**: natural, restrained, intimate
- **示例 Prompt**:

```text
warm male vocal, natural and restrained delivery, sincere emotional tone, suitable for a Chinese pop ballad
```

### 5.1.2 Mature Emotional Male Vocal / 成熟故事感男声

- **Voice ID**: `mature_emotional_male`
- **英文标签**: mature emotional male vocal, storytelling male vocal
- **适合曲风**: Mandopop ballad, soft rock, folk-pop, cinematic pop
- **适合主题**: 中年、人生转折、创业、故乡、普通人的生活
- **情绪关键词**: mature, reflective, bittersweet, grounded
- **音色特点**: 稳重、有生活感、适合叙事
- **示例 Prompt**:

```text
mature emotional male vocal with a storytelling delivery, warm lower register, restrained but deeply expressive
```

### 5.1.3 Slightly Raspy Male Vocal / 沙哑男声

- **Voice ID**: `raspy_male_vocal`
- **英文标签**: slightly raspy male vocal, gritty male vocal
- **适合曲风**: rock, blues rock, soft rock, country rock, folk-rock
- **适合主题**: 沧桑、奋斗、失落、重新出发
- **情绪关键词**: raw, gritty, heartfelt, weathered
- **使用提醒**: 不要写成过度嘶吼，除非用户明确要重摇滚或金属
- **示例 Prompt**:

```text
slightly raspy male vocal, gritty but emotional, raw storytelling tone, suitable for a heartfelt rock ballad
```

### 5.1.4 Deep Male Vocal / 低沉男声

- **Voice ID**: `deep_male_vocal`
- **英文标签**: deep male vocal, low resonant male voice
- **适合曲风**: cinematic pop, dark pop, jazz pop, spoken-word, folk ballad
- **适合主题**: 孤独、夜晚、城市、纪录片感、人生叙事
- **情绪关键词**: intimate, serious, cinematic, lonely
- **示例 Prompt**:

```text
deep male vocal, low resonant tone, intimate and cinematic delivery, suitable for a night-time urban ballad
```

### 5.1.5 Clear Young Male Vocal / 清澈少年感男声

- **Voice ID**: `clear_young_male`
- **英文标签**: clear young male vocal, youthful male vocal
- **适合曲风**: teen pop, campus folk, pop-rock, acoustic pop
- **适合主题**: 校园、青春、毕业、初恋、少年梦想
- **情绪关键词**: bright, youthful, hopeful, sincere
- **示例 Prompt**:

```text
clear youthful male vocal, bright and sincere tone, fresh pop delivery, suitable for a campus youth song
```

### 5.1.6 Powerful Rock Male Vocal / 有力量摇滚男声

- **Voice ID**: `powerful_rock_male`
- **英文标签**: powerful rock male vocal, raspy rock vocal
- **适合曲风**: hard rock, arena rock, pop-rock, stadium anthem
- **适合主题**: 体育、奋斗、团队、反抗、胜利
- **情绪关键词**: powerful, energetic, anthemic, bold
- **示例 Prompt**:

```text
powerful rock male vocal, anthemic chorus delivery, energetic and bold tone, backed by electric guitars and strong drums
```

### 5.1.7 Smooth Male R&B Vocal / 顺滑 R&B 男声

- **Voice ID**: `smooth_male_rnb`
- **英文标签**: smooth male R&B vocal, soulful male vocal
- **适合曲风**: R&B, pop-R&B, neo-soul, quiet storm
- **适合主题**: 爱情、夜晚、都市、暧昧、成熟关系
- **情绪关键词**: smooth, soulful, romantic, intimate
- **示例 Prompt**:

```text
smooth male R&B vocal, soulful and intimate delivery, warm falsetto touches, late-night romantic mood
```

---

## 5.2 Female Vocal / 女声类

### 5.2.1 Soft Female Vocal / 温柔女声

- **Voice ID**: `soft_female_vocal`
- **英文标签**: soft female vocal, gentle female vocal
- **适合曲风**: pop ballad, folk-pop, acoustic pop, healing pop
- **适合主题**: 陪伴、治愈、爱情、亲情、安慰
- **情绪关键词**: soft, gentle, warm, healing
- **示例 Prompt**:

```text
soft female vocal, gentle and healing delivery, warm emotional tone, suitable for an intimate pop ballad
```

### 5.2.2 Clear Female Vocal / 清澈女声

- **Voice ID**: `clear_female_vocal`
- **英文标签**: clear female vocal, pure female voice
- **适合曲风**: pop, campus pop, acoustic pop, bright electronic pop
- **适合主题**: 青春、校园、旅行、治愈、明亮生活
- **情绪关键词**: clear, bright, pure, youthful
- **示例 Prompt**:

```text
clear female vocal with a bright and pure tone, natural pop delivery, uplifting and fresh atmosphere
```

### 5.2.3 Ethereal Female Vocal / 空灵女声

- **Voice ID**: `ethereal_female_vocal`
- **英文标签**: ethereal female vocal, airy female vocal
- **适合曲风**: cinematic pop, ambient pop, Chinese traditional pop, dream pop
- **适合主题**: 梦幻、东方美学、电影感、自然、记忆
- **情绪关键词**: ethereal, airy, dreamy, cinematic
- **示例 Prompt**:

```text
ethereal female vocal, airy and cinematic tone, floating melody, dreamy atmospheric production
```

### 5.2.4 Powerful Female Vocal / 有力量女声

- **Voice ID**: `powerful_female_vocal`
- **英文标签**: powerful female vocal, soaring female vocal
- **适合曲风**: power ballad, pop-rock, gospel pop, stadium anthem
- **适合主题**: 独立、励志、突破、舞台、体育
- **情绪关键词**: powerful, soaring, confident, emotional climax
- **示例 Prompt**:

```text
powerful female vocal with soaring chorus delivery, emotional climax, polished pop-rock arrangement
```

### 5.2.5 Sweet Female Pop Vocal / 甜美女声

- **Voice ID**: `sweet_female_pop`
- **英文标签**: sweet female pop vocal, bright cute female vocal
- **适合曲风**: teen pop, dance-pop, J-pop, K-pop-inspired pop
- **适合主题**: 甜蜜、青春、短视频、轻快、校园
- **情绪关键词**: sweet, playful, bright, catchy
- **示例 Prompt**:

```text
sweet female pop vocal, bright and playful tone, catchy hook, glossy upbeat pop production
```

### 5.2.6 Smoky Female Vocal / 烟嗓女声

- **Voice ID**: `smoky_female_vocal`
- **英文标签**: smoky female vocal, sultry female vocal
- **适合曲风**: jazz pop, R&B, neo-soul, lounge pop, blues pop
- **适合主题**: 夜晚、都市、成熟爱情、高级感、咖啡馆
- **情绪关键词**: smoky, sultry, intimate, elegant
- **示例 Prompt**:

```text
smoky female vocal, intimate and elegant tone, smooth jazz-pop arrangement, late-night lounge atmosphere
```

### 5.2.7 Bright Dance-pop Female Vocal / 明亮舞曲女声

- **Voice ID**: `bright_dancepop_female`
- **英文标签**: bright dance-pop female vocal, energetic female vocal
- **适合曲风**: dance-pop, electro-pop, EDM pop, Y2K pop
- **适合主题**: 派对、短视频、品牌年轻化、夏日、活力
- **情绪关键词**: energetic, bright, confident, catchy
- **示例 Prompt**:

```text
bright energetic female vocal, catchy dance-pop hook, glossy electronic production, upbeat summer vibe
```

---

## 5.3 Rap / Spoken / Hybrid Voice / 说唱、旁白与混合人声

### 5.3.1 Rap Vocal / 说唱人声

- **Voice ID**: `rap_vocal`
- **英文标签**: rap vocal, rhythmic flow
- **适合曲风**: hip-hop, trap, boom bap, rap-rock
- **适合主题**: 态度、城市、青年文化、品牌潮流、社会观察
- **情绪关键词**: confident, rhythmic, sharp, urban
- **示例 Prompt**:

```text
confident rap vocal, rhythmic flow, urban storytelling, tight beat and deep bass
```

### 5.3.2 Melodic Rap Vocal / 旋律说唱人声

- **Voice ID**: `melodic_rap_vocal`
- **英文标签**: melodic rap vocal, sung rap delivery
- **适合曲风**: trap pop, pop rap, alternative R&B, emo rap
- **适合主题**: 年轻、情绪、都市、短视频、失恋
- **情绪关键词**: emotional, catchy, modern, vulnerable
- **示例 Prompt**:

```text
melodic rap vocal, half-sung delivery, emotional trap-pop production, catchy hook
```

### 5.3.3 Spoken-word Vocal / 旁白式人声

- **Voice ID**: `spoken_word_vocal`
- **英文标签**: spoken-word vocal, narrative spoken delivery
- **适合曲风**: cinematic pop, ambient, trip-hop, poetry pop
- **适合主题**: 纪录片、人生独白、城市、诗意表达
- **情绪关键词**: narrative, intimate, reflective, cinematic
- **示例 Prompt**:

```text
spoken-word vocal, intimate narrative tone, cinematic background music, poetic and reflective mood
```

### 5.3.4 Vocal Chop / 人声切片

- **Voice ID**: `vocal_chop`
- **英文标签**: vocal chops, chopped vocal samples
- **适合曲风**: future bass, EDM pop, chillwave, trap pop
- **适合场景**: 短视频、科技产品、潮流品牌、器乐 BGM
- **使用提醒**: 不等于完整演唱；常用于装饰性 hook
- **示例 Prompt**:

```text
instrumental electronic pop with bright vocal chops, no full lyrics, uplifting future bass texture
```

---

## 5.4 Group / Choir / Ensemble / 合唱与多人声

### 5.4.1 Group Vocals / 群体合唱

- **Voice ID**: `group_vocals`
- **英文标签**: group vocals, sing-along chorus
- **适合曲风**: pop anthem, stadium anthem, folk-pop, corporate anthem
- **适合主题**: 团队、毕业、品牌、活动、体育
- **示例 Prompt**:

```text
group vocals in the chorus, sing-along melody, uplifting and communal feeling
```

### 5.4.2 Stadium Chant Vocals / 体育场齐唱

- **Voice ID**: `stadium_chant_vocals`
- **英文标签**: stadium chant vocals, crowd chant chorus
- **适合曲风**: stadium anthem, arena rock, sports cinematic pop, Latin pop
- **适合主题**: 世界杯、赛事、团队、胜利、荣耀
- **示例 Prompt**:

```text
stadium chant vocals, crowd sing-along chorus, powerful drums, anthem energy, suitable for sports highlights
```

### 5.4.3 Gospel Choir / 福音合唱

- **Voice ID**: `gospel_choir`
- **英文标签**: gospel choir, uplifting choir vocals
- **适合曲风**: gospel pop, soul, power ballad, cinematic pop
- **适合主题**: 希望、救赎、庄重、仪式感、鼓舞
- **示例 Prompt**:

```text
uplifting gospel choir in the final chorus, soulful harmonies, emotional and hopeful climax
```

### 5.4.4 Children’s Choir / 儿童合唱

- **Voice ID**: `children_choir`
- **英文标签**: children’s choir, bright children vocals
- **适合曲风**: children’s song, educational song, family pop
- **适合主题**: 儿童教育、亲子、节日、校园
- **示例 Prompt**:

```text
bright children’s choir, simple melody, playful rhythm, family-friendly and easy to sing along
```

### 5.4.5 Male and Female Duet / 男女对唱

- **Voice ID**: `male_female_duet`
- **英文标签**: male and female duet, conversational duet vocals
- **适合曲风**: romantic pop, musical pop, folk duet, R&B duet
- **适合主题**: 爱情故事、对话、重逢、婚礼、剧情歌
- **示例 Prompt**:

```text
male and female duet, conversational vocal exchange, emotional romantic pop ballad arrangement
```

### 5.4.6 A Cappella / 无伴奏人声

- **Voice ID**: `a_cappella`
- **英文标签**: a cappella vocals, vocal harmony arrangement
- **适合曲风**: vocal pop, gospel, barbershop, choir pop
- **适合主题**: 节日、校园、合唱、创意短视频
- **示例 Prompt**:

```text
a cappella vocal harmony arrangement, layered voices, no instruments, warm and intimate performance
```

---

# 6. Vocal Texture Library / 音色质感库

## 6.1 亮度与厚度

| 中文描述 | Prompt 词 |
|---|---|
| 明亮 | bright tone |
| 温暖 | warm tone |
| 厚实 | rich and full tone |
| 轻盈 | light and airy tone |
| 空灵 | ethereal, airy |
| 低沉 | deep, low, resonant |
| 清澈 | clear, pure |
| 沙哑 | raspy, gritty |
| 烟嗓 | smoky, sultry |
| 甜美 | sweet, bright |
| 磁性 | magnetic, intimate, resonant |

## 6.2 演唱强度

| 中文描述 | Prompt 词 |
|---|---|
| 克制 | restrained delivery |
| 自然 | natural vocal delivery |
| 亲密 | intimate vocal performance |
| 情绪化 | emotional delivery |
| 爆发 | powerful chorus delivery |
| 高亢 | soaring vocals |
| 低语 | whispery vocal tone |
| 喊唱 | shout-like rock delivery |
| 戏剧化 | theatrical vocal delivery |
| 叙事感 | storytelling delivery |

## 6.3 制作质感

| 中文描述 | Prompt 词 |
|---|---|
| 干净 | clean vocal production |
| 电台级 | polished radio-ready vocal production |
| 复古 | vintage vocal texture |
| 现场感 | live performance feel |
| 卧室感 | bedroom-pop vocal texture |
| 轻微混响 | subtle reverb |
| 空间感 | spacious reverb |
| 贴耳 | intimate close-mic vocal |
| 自动调音感 | light autotune / autotuned vocal |
| 不要修音太重 | avoid heavy autotune |

---

# 7. Genre-to-Voice Recommendation / 曲风到人声推荐

| 曲风 | 推荐人声 |
|---|---|
| Chinese pop ballad | warm male vocal / soft female vocal / mature emotional vocal |
| Folk-pop | warm male vocal / clear female vocal / intimate duet |
| Pop-rock | powerful male vocal / powerful female vocal / youthful vocal |
| Arena rock | powerful rock male vocal / group vocals / stadium chant vocals |
| R&B | smooth male R&B vocal / smoky female vocal / soft female vocal |
| Neo-soul | soulful male vocal / smoky female vocal / warm mezzo-like vocal |
| Dance-pop | bright female vocal / energetic male vocal / catchy group hook |
| Synth-pop | clear male or female vocal / airy vocal / slightly processed vocal |
| Hip-hop | rap vocal / melodic rap vocal |
| Trap pop | melodic rap vocal / autotuned vocal / youthful vocal |
| Jazz pop | smoky female vocal / warm crooner-style male vocal |
| Country-pop | warm male vocal / clear female vocal / storytelling vocal |
| Latin pop | bright energetic vocal / group chorus / danceable vocal delivery |
| Chinese traditional pop | ethereal female vocal / warm male vocal / poetic vocal delivery |
| Cinematic pop | ethereal female vocal / mature male vocal / choir in final chorus |
| Children’s song | children’s choir / bright playful vocal |
| Corporate anthem | clean warm vocal / group vocals / uplifting chorus |
| Stadium anthem | stadium chant vocals / group vocals / powerful lead vocal |

---

# 8. Scene-to-Voice Recommendation / 场景到人声推荐

| 场景 | 推荐人声策略 |
|---|---|
| 朋友圈个人歌曲 | warm male vocal / soft female vocal / mature emotional vocal |
| 小红书短视频 | clear female vocal / sweet female pop vocal / catchy youthful vocal |
| 品牌宣传 | clean warm vocal / confident female vocal / group vocals |
| 企业年会 | uplifting group vocals / clean pop vocal / choir final chorus |
| 体育赛事 | powerful lead vocal + stadium chant chorus |
| 世界杯主题 | energetic vocal + crowd chant + Latin / stadium chorus |
| 婚礼 | male and female duet / soft female vocal / warm male vocal |
| 毕业季 | youthful male vocal / clear female vocal / group chorus |
| 儿童教育 | children’s choir / bright playful vocal |
| 城市宣传片 | mature male narration-like vocal / ethereal female vocal / cinematic choir |
| 科技产品 | clean processed vocal / airy vocal chops / minimal vocal |
| 夜晚城市 | deep male vocal / smoky female vocal / smooth R&B vocal |
| 国风文旅 | ethereal female vocal / poetic warm male vocal / choir accents |

---

# 9. Vocal Prompt Formulas / 人声 Prompt 公式

## 9.1 基础公式

```text
[voice type], [tone color], [delivery style], suitable for [genre/use case]
```

示例：

```text
warm male vocal, sincere and restrained tone, natural storytelling delivery, suitable for a Chinese pop ballad
```

## 9.2 情绪递进公式

```text
Start with [restrained/intimate] vocal delivery in the verse, then build into [powerful/soaring/group] vocals in the chorus.
```

示例：

```text
Start with restrained intimate male vocals in the verse, then build into a powerful sing-along chorus with subtle group vocals.
```

## 9.3 合唱公式

```text
Lead vocal in the verses, group vocals in the chorus, crowd chant feel in the final chorus.
```

适合体育、品牌、毕业、活动。

## 9.4 纯器乐排除人声公式

```text
instrumental only, no vocals, no rap, no spoken words, focus on melody, groove, and atmosphere
```

适合纯器乐背景音乐。

## 9.5 避免项公式

```text
Avoid overly theatrical vocals, heavy autotune, and direct imitation of any real singer.
```

---

# 10. Interactive Routing Logic / Skill 交互路由逻辑

## 10.1 当用户选择“带歌词歌曲”

优先询问：

```text
1. 你希望男声、女声、合唱，还是不确定？
2. 人声更想要：温暖 / 清澈 / 沙哑 / 空灵 / 有力量 / 甜美 / 低沉？
3. 演唱方式更想要：克制自然 / 情绪爆发 / 故事感 / 适合大合唱？
```

如果用户不确定，则根据曲风与场景自动推荐。

## 10.2 当用户选择“纯器乐”

不要再问人声偏好。自动加入：

```text
instrumental only, no vocals, no rap, no spoken words
```

如果需要人声切片，可以使用：

```text
subtle vocal chops, no full lyrics
```

## 10.3 当用户说“像某某歌手”

不要直接生成模仿真实歌手声音的 Prompt。改写为抽象描述：

```text
用户说：像某位流行男歌手
改写：warm male pop vocal, melodic phrasing, emotional but restrained delivery

用户说：像某位摇滚歌手
改写：raspy rock male vocal, powerful chorus delivery, raw emotional energy
```

---

# 11. Safety & Copyright Notes / 安全与版权提醒

Prompt 应避免：

```text
Clone [artist] voice
Sing exactly like [artist]
Use [artist]’s voice
Copy the vocal style of [artist] exactly
```

建议改写：

```text
warm emotional male vocal
bright dance-pop female vocal
raspy rock vocal
soulful R&B vocal
nostalgic 1990s pop vocal texture
```

如果用户用于商业场景，最终输出应提醒：

```text
If this song is intended for commercial use, check the licensing and commercial-use rules of the AI music platform before publishing.
```

---

# 12. Copy-ready Vocal Prompt Snippets / 可复制人声片段

```text
warm mature male vocal, natural and restrained delivery, emotional storytelling tone
```

```text
soft female vocal, gentle and healing delivery, warm intimate tone
```

```text
clear youthful vocal, bright and sincere tone, suitable for a campus pop song
```

```text
slightly raspy male vocal, gritty but heartfelt rock delivery
```

```text
ethereal female vocal, airy cinematic tone, dreamy atmospheric production
```

```text
powerful female vocal, soaring chorus delivery, emotional climax
```

```text
smooth male R&B vocal, soulful intimate delivery, late-night romantic mood
```

```text
stadium chant vocals, crowd sing-along chorus, powerful anthem energy
```

```text
male and female duet, conversational vocal exchange, emotional romantic pop ballad
```

```text
instrumental only, no vocals, no rap, no spoken words, focus on melody and atmosphere
```

---

# 13. References / 参考来源

- Yale University Library, Vocal Ranges: used for basic soprano / mezzo-soprano / alto / tenor / baritone / bass range reference.
- Berklee Online, vocal range and pop/R&B performance notes: used to support the idea that range, key, and comfortable register matter in vocal performance.
- Travis Nicholson Suno prompting materials and uploaded Suno Decades prompt PDF: used as reference for era-based vocal descriptors such as crooner vocals, harmony vocals, falsetto, raspy vocals, gospel power, polished pop vocals, rap flow, and Y2K dance-pop vocal texture.

