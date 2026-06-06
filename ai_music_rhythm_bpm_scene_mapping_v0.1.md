# AI Music Rhythm / BPM / Scene Mapping Library v0.1

> 用途：作为交互式 AI 音乐 Prompt Skill 的“节奏、BPM、使用场景映射库”。  
> 目标：帮助 Skill 根据用户的场景、情绪、曲风和用途，自动选择合适的速度、律动、段落结构和 Prompt 表达。  
> 适用对象：Suno / Udio / 类 Suno AI 音乐生成软件。  
> 注意：BPM 范围不是绝对规则，而是用于 Prompt 生成的经验参考。AI 音乐工具未必严格服从 BPM，但写入合理的速度区间有助于稳定风格结果。

---

## 1. 这个库解决什么问题

在 AI 音乐生成中，用户通常会说：

- “我想要温暖一点”
- “我想要燃一点”
- “适合短视频”
- “适合品牌宣传”
- “适合学习工作背景音乐”
- “我想要世界杯主题曲感觉”

但这些描述还不能直接变成稳定的音乐 Prompt。Skill 需要把它们转译为：

```text
Tempo / BPM
Rhythm Feel
Groove
Energy Level
Arrangement Density
Chorus Entry
Loopability
Scene Fit
```

所以这个库的核心任务是：

```text
用户场景 + 用户情绪 + 曲风偏好 → 推荐 BPM / 节奏感觉 / 编曲推进 / Prompt 关键词
```

---

## 2. Prompt 里与节奏相关的核心字段

生成最终音乐 Prompt 时，节奏相关信息建议拆成 7 个字段：

```text
Tempo: 90–105 BPM / medium tempo / slow ballad / fast energetic
Rhythm Feel: laid-back / driving / danceable / half-time / four-on-the-floor
Groove: steady groove / syncopated groove / boom bap groove / Latin groove
Energy Level: low / medium / high / explosive
Arrangement Density: sparse / moderate / full / cinematic build
Chorus Entry: early chorus / gradual build / big chorus / chant chorus
Loopability: loop-friendly / seamless loop / clear ending / short hook
```

对于带人声歌曲，节奏字段要服务于：

```text
歌词表达 + 副歌记忆点 + 情绪推进
```

对于纯器乐音乐，节奏字段要服务于：

```text
背景用途 + 律动稳定性 + 可循环性 + 不干扰内容
```

---

## 3. 用户语言到 BPM 的基础映射

这是交互式 Skill 最常用的转换表。

| 用户说法 | 推荐 BPM | 英文 Prompt 表达 | 适合用途 |
|---|---:|---|---|
| 很慢 / 极慢 | 50–65 | very slow, spacious, minimal | 情绪铺垫、冥想、电影感开场 |
| 深情慢歌 | 60–75 | slow emotional ballad | 爱情、亲情、伤感、人生故事 |
| 慢速 | 70–85 | slow tempo, relaxed | 民谣、R&B、治愈、Lo-fi |
| 舒缓中速 | 85–100 | relaxed medium tempo | 朋友圈、Vlog、城市生活 |
| 中速 | 100–115 | medium tempo | 中文流行、品牌歌、校园歌 |
| 明快 | 115–128 | upbeat, bright tempo | 短视频、活动、轻快品牌 |
| 快节奏 | 128–145 | fast, energetic | 电子、运动、舞曲、潮流视频 |
| 很燃 / 高能 | 145–170 | high-energy, intense | 摇滚、朋克、体育、动作剪辑 |
| 极速 / 疾驰感 | 170–180+ | very fast, drum and bass energy | 高速电子、极限运动、游戏感 |

---

## 4. 传统速度术语参考

虽然现代 AI 音乐 Prompt 不一定需要写 Largo / Andante / Allegro 这类术语，但它们可以帮助 Skill 理解“慢、中、快”的大致边界。

| 速度术语 | 大致 BPM | 中文理解 | Prompt 用法建议 |
|---|---:|---|---|
| Largo / Lento | 40–66 | 缓慢、宽广 | 少量使用，适合氛围或庄重开场 |
| Adagio | 44–76 | 慢速、有表情 | 适合抒情慢歌、钢琴、弦乐 |
| Andante | 76–108 | 行走速度 | 适合民谣、叙事、轻柔流行 |
| Moderato | 108–120 | 中速 | 适合大多数流行歌和品牌歌 |
| Allegro | 120–156 | 快速、明亮 | 适合欢快、运动、电子、摇滚 |
| Vivace | 156–176 | 活泼、快速 | 适合高能摇滚、朋克、动作感 |
| Presto | 168–200 | 非常快 | 适合极速感，不建议普通歌曲默认使用 |

Skill 输出时，不建议给普通用户解释这些术语；内部使用即可。

---

## 5. 按大类曲风的 BPM 参考

### 5.1 Pop / 流行类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Chinese pop ballad / 中文流行抒情 | 70–95 | slow to medium, emotional | 朋友圈、亲情、爱情、人生 |
| Mandopop / 华语流行 | 85–115 | medium, melodic | 大众歌曲、短视频、个人歌 |
| Modern pop | 100–125 | polished, radio-friendly | 品牌、短视频、活动 |
| Dance-pop | 115–130 | upbeat, danceable | 短视频、活动、年轻化品牌 |
| Synth-pop | 90–125 | steady synth groove | 科技、复古、城市夜晚 |
| Electro-pop | 105–130 | bright electronic beat | 潮流、产品、短视频 |
| Teen pop | 105–125 | bright, simple, catchy | 校园、青春、儿童/青少年 |
| Power ballad | 65–90 | slow build, big chorus | 情绪爆发、励志、爱情 |
| City pop | 90–115 | smooth, urban, nostalgic | 城市、夏天、复古高级感 |
| Dream pop | 70–105 | floating, soft pulse | 梦幻、治愈、影像配乐 |

Prompt 关键词：

```text
medium tempo, catchy chorus, polished production, melodic hook, radio-friendly, emotional build
```

---

### 5.2 Folk / 民谣类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Acoustic folk | 70–95 | gentle strumming | 旅行、故乡、个人故事 |
| Folk-pop | 80–105 | warm, singable | 毕业、朋友圈、生活感 |
| Indie folk | 75–100 | intimate, organic | 独立、真实、叙事 |
| Country folk | 80–110 | steady, storytelling | 公路、家庭、人生故事 |
| Campus folk | 85–105 | clean, youthful | 校园、青春、毕业 |

Prompt 关键词：

```text
acoustic guitar rhythm, warm organic groove, intimate tempo, storytelling feel
```

---

### 5.3 Rock & Metal / 摇滚与金属类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Soft rock | 75–105 | steady, mellow | 成长、回忆、人生 |
| Pop-rock | 95–130 | driving but accessible | 励志、青春、品牌 |
| Classic rock | 100–140 | guitar-driven | 复古、热血、公路感 |
| Hard rock | 110–150 | heavy riffs, strong drums | 燃、团队、比赛 |
| Arena rock | 100–130 | big chorus, stadium feel | 体育、活动开场 |
| Punk rock | 150–190 | fast, raw, aggressive | 反叛、青春、短促爆发 |
| Pop-punk | 140–180 | fast, bright, punchy | 校园、热血、少年感 |
| Grunge | 80–120 | heavy, loose, angst | 压抑、反抗、90s 质感 |
| Alternative rock | 90–140 | varied, guitar-driven | 青年、城市、独立表达 |
| Post-rock instrumental | 70–120 | slow build, explosive climax | 纯器乐、视频、人生叙事 |
| Heavy metal | 110–160 | powerful, dense | 史诗、力量、游戏感 |
| Thrash metal | 160–220 | very fast, aggressive | 极限、高压、战斗感 |
| Power metal | 140–180 | fast, heroic, melodic | 英雄、奇幻、游戏、体育 |
| Doom metal | 50–80 | slow, heavy, dark | 黑暗、压迫、低频氛围 |
| Metalcore | 130–180 | breakdowns, intense | 高能、动作、冲突 |

Prompt 关键词：

```text
driving rhythm, powerful drums, electric guitar riffs, anthemic chorus, high-energy build
```

---

### 5.4 R&B / Soul 类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Smooth R&B | 65–90 | slow groove, intimate | 夜晚、爱情、成熟感 |
| Contemporary R&B | 70–105 | polished groove | 都市、情感、短视频 |
| Pop-R&B | 85–110 | catchy, smooth | 年轻、爱情、商业流行 |
| Neo-soul | 70–95 | laid-back, organic | 高级感、咖啡馆、成熟情绪 |
| Soul ballad | 60–85 | expressive, emotional | 深情、亲情、爱情 |
| Motown soul | 95–125 | upbeat, classic groove | 复古、快乐、活动 |
| New jack swing | 100–115 | syncopated, rhythmic | 80s/90s 复古、律动感 |
| Quiet storm | 60–80 | slow, sensual | 夜晚、私密、浪漫 |

Prompt 关键词：

```text
smooth groove, soulful vocal, warm bass, syncopated drums, intimate rhythm
```

---

### 5.5 Hip-hop / Rap / Beat 类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Hip-hop | 75–105 | rhythmic, beat-driven | 城市、态度、故事 |
| Boom bap | 85–95 | head-nod groove | 复古说唱、街头叙事 |
| West Coast / G-Funk | 85–100 | laid-back, smooth | 阳光、城市、复古 |
| Trap | 130–150 或 65–75 half-time | 808, hi-hat rolls | 潮流、运动、短视频 |
| Drill | 135–150 | dark, sparse, sliding 808 | 冷峻、街头、动作感 |
| Lo-fi hip-hop | 65–90 | relaxed loop | 学习、陪伴、夜晚 |
| Jazz rap | 80–100 | jazzy, smooth | 高级、城市、叙事 |
| Rap-rock | 95–140 | hybrid groove | 运动、热血、冲突 |
| Instrumental hip-hop | 75–105 | beat-led, loopable | BGM、短视频、城市感 |

Prompt 关键词：

```text
deep bass, tight drums, rhythmic flow, 808 drums, head-nod groove, loopable beat
```

---

### 5.6 Electronic / Dance 类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| House | 115–130 | four-on-the-floor, danceable | 活动、时尚、品牌 |
| Deep house | 110–125 | smooth, warm, club-lite | 高级、生活方式、夜晚 |
| Tech house | 120–130 | clean, driving | 潮流、活动、产品视频 |
| Techno | 120–140 | hypnotic, driving | 科技、冷峻、高级 |
| Trance | 125–140 | uplifting, arpeggiated | 史诗、能量、电子感 |
| EDM | 128–150 | build and drop | 活动、派对、运动 |
| Future bass | 130–160 | bright, emotional drop | 短视频、年轻、潮流 |
| Dubstep | 135–145 或 70 half-time | heavy half-time | 游戏、动作、冲击 |
| Drum and bass | 160–180 | fast breakbeats | 高速、极限、运动 |
| Synthwave | 80–110 | retro-futuristic pulse | 科技、复古、霓虹 |
| Chillwave | 75–100 | hazy, nostalgic | 夏天、Vlog、梦幻 |
| Ambient electronic | free / 50–90 | no strong beat | 空间、冥想、背景 |
| Minimal electronic | 90–125 | sparse pulse | 科技、产品、高级 |

Prompt 关键词：

```text
pulsing synth bass, electronic drums, four-on-the-floor groove, atmospheric pads, energetic drop
```

---

### 5.7 Disco / Funk / Groove 类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Funk | 90–115 | syncopated groove | 活力、时尚、律动 |
| Disco | 105–125 | dance floor groove | 派对、复古、快乐 |
| Disco-funk | 105–125 | bassline + brass | 品牌、活动、短视频 |
| Nu-disco | 110–125 | modern retro groove | 时尚、潮流、Vlog |
| Funk-pop | 100–120 | catchy, groovy | 年轻、品牌、明亮 |

Prompt 关键词：

```text
funky bassline, syncopated guitar, brass hits, hand claps, danceable groove
```

---

### 5.8 Jazz / Lounge / Bossa 类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Jazz pop | 75–110 | elegant swing or soft groove | 高级、城市、咖啡馆 |
| Vocal jazz | 60–100 | intimate, expressive | 复古、浪漫、夜晚 |
| Lounge pop | 70–105 | relaxed, smooth | 酒店、咖啡馆、品牌 |
| Swing | 120–180 | swinging, lively | 复古、快乐、舞会 |
| Smooth jazz | 70–100 | soft groove | 商务、酒店、背景音乐 |
| Nu jazz | 90–125 | electronic jazz groove | 高级、城市、广告 |
| Jazz-hop | 75–95 | boom bap + jazz chords | 学习、城市、咖啡馆 |
| Bossa nova | 90–130 | gentle syncopation | 夏天、旅行、轻松 |

Prompt 关键词：

```text
smooth jazz chords, gentle swing, elegant groove, brushed drums, warm bass
```

---

### 5.9 Latin / Reggae / World Groove 类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Latin pop | 95–125 | bright, danceable | 世界杯、夏天、派对 |
| Reggaeton | 85–105 | dembow rhythm | 潮流、运动、拉丁感 |
| Salsa pop | 90–120 | energetic Latin percussion | 活动、派对、庆典 |
| Samba | 95–130 | lively percussion | 巴西、节庆、运动 |
| Afrobeat | 95–120 | polyrhythmic groove | 国际化、阳光、活力 |
| Reggae | 70–95 | offbeat skank | 海边、轻松、夏天 |
| Dancehall | 90–110 | rhythmic, bass-heavy | 潮流、派对、短视频 |
| World fusion | 80–120 | hybrid groove | 文旅、城市、国际感 |

Prompt 关键词：

```text
latin percussion, syncopated groove, tropical rhythm, danceable bassline, sunny energy
```

---

### 5.10 Chinese / 国风 / 东方融合类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Chinese traditional pop | 70–105 | melodic, flowing | 文旅、节日、国潮 |
| 古风抒情 | 60–90 | slow, poetic | 古风、东方美学、剧情 |
| 国风电子 | 95–130 | electronic + Chinese instruments | 国潮、品牌、科技文旅 |
| 戏腔融合 | 65–100 | dramatic, expressive | 戏曲、文化、短视频 |
| 江南民谣 | 70–100 | soft, flowing | 城市文旅、水乡、诗意 |
| 东方电影感器乐 | 60–110 | cinematic build | 宣传片、纪录片、城市 |

Prompt 关键词：

```text
guzheng, pipa, erhu, dizi, Chinese percussion, flowing rhythm, poetic atmosphere
```

---

### 5.11 Cinematic / Commercial / Background 类

| 曲风 | 推荐 BPM | 节奏感觉 | 适合场景 |
|---|---:|---|---|
| Cinematic pop | 70–110 | emotional build | 视频、品牌、人生叙事 |
| Epic orchestral | 80–130 | big drums, heroic | 体育、史诗、城市大片 |
| Trailer music | 90–140 | rising tension | 预告片、发布会、冲击感 |
| Emotional score | 60–95 | piano + strings | 纪录片、故事、情绪 |
| Corporate pop instrumental | 100–125 | clean, optimistic | 企业宣传、产品介绍 |
| Tech product background | 90–125 | minimal pulse | 科技、发布会、高级 |
| Sports highlight instrumental | 120–150 | driving, powerful | 体育剪辑、动作、燃 |
| Podcast intro | 90–120 | short, branded motif | 播客、片头、栏目 |

Prompt 关键词：

```text
cinematic build, uplifting corporate rhythm, emotional piano, inspiring drums, clean background music
```

---

## 6. 纯器乐专用 BPM 与律动参考

纯器乐音乐与带人声歌曲不同，重点不是副歌，而是“用途、可循环、不过度抢注意力”。

| 器乐类型 | 推荐 BPM | 是否适合循环 | 典型用途 | Prompt 关键词 |
|---|---:|---|---|---|
| Lo-fi instrumental | 65–90 | 很适合 | 学习、陪伴、夜晚 | loop-friendly, dusty drums, mellow keys |
| Chillhop | 75–95 | 很适合 | 咖啡馆、Vlog、学习 | chill groove, jazzy piano, soft drums |
| Jazz-hop | 75–95 | 很适合 | 城市、学习、咖啡馆 | jazz chords, boom bap drums, warm bass |
| Ambient pop instrumental | 60–90 | 适合 | 情绪视频、空间感 | airy pads, soft piano, spacious texture |
| Synthwave instrumental | 80–110 | 适合 | 科技、复古、霓虹 | analog synths, retro drums, neon atmosphere |
| Future bass instrumental | 130–160 | 一般 | 短视频、年轻感 | bright synth chords, emotional drop |
| Post-rock instrumental | 70–120 | 不一定 | 人生叙事、长视频 | clean guitar, delay, slow build, big climax |
| Corporate instrumental | 100–125 | 适合 | 企业宣传、产品 | uplifting, clean, optimistic, soft claps |
| Tech background | 90–125 | 适合 | 科技产品、发布会 | minimal synth pulse, premium, clean |
| Sports instrumental | 120–150 | 不一定 | 体育剪辑、开场 | powerful drums, driving rhythm, action energy |
| Bossa instrumental | 90–125 | 适合 | 旅行、生活方式 | nylon guitar, soft percussion, breezy groove |
| Acoustic instrumental | 70–105 | 适合 | 旅行、温暖、自然 | acoustic guitar, light percussion, organic |

纯器乐 Prompt 固定短语：

```text
instrumental only, no vocals, no lyrics, background music, loop-friendly, seamless loop, subtle arrangement variations, clean mix
```

如果是短视频 BGM，可以加入：

```text
catchy instrumental hook, 30-second loop, quick intro, memorable motif
```

如果是品牌背景音乐，可以加入：

```text
non-intrusive, polished, optimistic, clean corporate production, suitable for voiceover
```

---

## 7. 使用场景到节奏的映射

### 7.1 短视频 / 小红书 / Reels / TikTok

| 目标 | 推荐 BPM | 推荐律动 | 结构建议 | 曲风建议 |
|---|---:|---|---|---|
| 情绪共鸣 | 80–105 | medium, melodic | 5 秒内进入主情绪 | Chinese pop ballad, folk-pop |
| 爆款 Hook | 105–130 | upbeat, catchy | 15–30 秒强 Hook | dance-pop, electro-pop, pop-R&B |
| 潮流感 | 120–150 | beat-driven | 快速进入节奏 | trap pop, future bass, house |
| 治愈生活 | 70–95 | relaxed | 可循环 | lo-fi, chillhop, acoustic |
| 运动剪辑 | 125–150 | driving | 直接高能 | sports instrumental, rock, EDM |

Prompt 关键词：

```text
short-video friendly, catchy hook, quick intro, memorable chorus, 30-second highlight section
```

---

### 7.2 朋友圈 / 个人纪念

| 目标 | 推荐 BPM | 推荐律动 | 结构建议 | 曲风建议 |
|---|---:|---|---|---|
| 真诚表达 | 70–95 | warm, restrained | 主歌有画面，副歌有共鸣 | Chinese pop ballad, folk-pop |
| 人生故事 | 75–100 | storytelling | 慢慢推进 | acoustic folk, soft rock |
| 温暖治愈 | 80–105 | gentle groove | 不要太炸 | pop ballad, piano pop |
| 纪念日 | 65–90 | emotional | 副歌温暖 | romantic ballad, R&B |

Prompt 关键词：

```text
warm and personal, emotional but restrained, memorable chorus, suitable for sharing with friends
```

---

### 7.3 品牌宣传 / 企业宣传

| 品牌气质 | 推荐 BPM | 推荐律动 | 曲风建议 | Prompt 方向 |
|---|---:|---|---|---|
| 科技感 | 90–125 | minimal pulse | electronic pop, minimal electronic | clean, futuristic, premium |
| 年轻潮流 | 115–130 | upbeat | dance-pop, future bass | bright, energetic, modern |
| 稳重可信 | 85–110 | steady | cinematic pop, corporate instrumental | warm, trustworthy, polished |
| 高端品牌 | 70–105 | restrained | jazz pop, cinematic, ambient pop | elegant, minimal, premium |
| 企业年会 | 105–125 | uplifting | corporate pop, pop-rock | inspiring, optimistic, group-friendly |

Prompt 关键词：

```text
uplifting corporate, polished production, clean mix, optimistic, suitable for brand video and voiceover
```

---

### 7.4 活动开场 / 发布会

| 场景 | 推荐 BPM | 推荐律动 | 曲风建议 | 结构建议 |
|---|---:|---|---|---|
| 科技发布会 | 100–128 | pulse, build-up | minimal electronic, cinematic electronic | 从低频脉冲到开场爆发 |
| 企业年会 | 105–125 | uplifting | corporate pop, pop-rock | 明亮开场，副歌合唱感 |
| 大型活动 | 120–140 | driving | EDM, cinematic anthem | buildup + drop |
| 颁奖典礼 | 80–115 | cinematic | orchestral pop, cinematic pop | 庄重但不沉重 |

Prompt 关键词：

```text
opening theme, energetic build-up, powerful intro, polished event music, inspiring climax
```

---

### 7.5 体育赛事 / 世界杯 / 球队主题

| 目标 | 推荐 BPM | 推荐律动 | 曲风建议 | 结构建议 |
|---|---:|---|---|---|
| 体育热血 | 115–140 | driving drums | stadium anthem, arena rock | 大副歌、合唱 |
| 世界杯夏日感 | 95–125 | Latin groove | Latin pop, reggaeton, Afrobeat | 副歌可齐唱 |
| 史诗感 | 90–130 | cinematic drums | epic orchestral, cinematic pop | 渐进爆发 |
| 短视频剪辑 | 125–150 | high energy | EDM, rock instrumental | 直接进入高能段落 |
| 球迷合唱 | 95–125 | chant rhythm | stadium chant, rock anthem | 简单重复短句 |

Prompt 关键词：

```text
stadium anthem, chant chorus, powerful drums, group vocals, crowd energy, heroic and uplifting
```

---

### 7.6 学习 / 工作 / 陪伴 BGM

| 目标 | 推荐 BPM | 推荐律动 | 曲风建议 | 注意事项 |
|---|---:|---|---|---|
| 学习专注 | 65–85 | relaxed loop | lo-fi, ambient pop | 不要人声，不要强副歌 |
| 咖啡馆 | 75–95 | mellow groove | chillhop, jazz-hop | 柔和鼓点 |
| 深夜陪伴 | 60–80 | sparse | lo-fi, downtempo | 温暖、少变化 |
| 工作效率 | 80–105 | steady pulse | minimal electronic, chillhop | 节奏稳定，不抢注意力 |
| 冥想放松 | free / 50–70 | no strong beat | ambient electronic | 极简、空间感 |

Prompt 关键词：

```text
instrumental only, no vocals, loop-friendly, non-intrusive, suitable for focus and background listening
```

---

### 7.7 Vlog / 旅行 / 生活方式

| 目标 | 推荐 BPM | 推荐律动 | 曲风建议 | Prompt 方向 |
|---|---:|---|---|---|
| 城市 Vlog | 85–110 | relaxed groove | city pop, chillhop, jazz-hop | urban, stylish, warm |
| 夏日旅行 | 95–125 | breezy | bossa nova, Latin pop, acoustic pop | sunny, light, travel |
| 海边度假 | 85–110 | tropical | reggae, bossa, Latin groove | relaxing, beachside |
| 日常生活 | 80–105 | gentle | acoustic instrumental, folk-pop | simple, warm, organic |
| 美食探店 | 90–115 | playful | jazz pop, funk groove, bossa | light, elegant, friendly |

Prompt 关键词：

```text
lifestyle vlog music, warm groove, light percussion, sunny mood, loop-friendly background
```

---

### 7.8 公众号视频 / 纪录片 / 人生叙事

| 目标 | 推荐 BPM | 推荐律动 | 曲风建议 | 结构建议 |
|---|---:|---|---|---|
| 人物故事 | 65–95 | slow emotional | piano pop, cinematic pop | 由安静到情绪抬升 |
| 城市纪录片 | 70–110 | cinematic pulse | cinematic instrumental, ambient pop | 有空间感 |
| 历史回顾 | 60–90 | stately | orchestral pop, emotional score | 稳重、叙事 |
| 热点评论 | 85–115 | steady | minimal electronic, documentary score | 不抢旁白 |
| 结尾升华 | 80–110 | uplifting build | cinematic pop, post-rock | 最后 20 秒抬升 |

Prompt 关键词：

```text
cinematic narrative, emotional build-up, suitable for documentary voiceover, not too busy
```

---

### 7.9 儿童 / 教育 / 课程

| 目标 | 推荐 BPM | 推荐律动 | 曲风建议 | 注意事项 |
|---|---:|---|---|---|
| 儿童歌 | 90–125 | simple, playful | children’s song | 旋律简单，重复性强 |
| 课堂记忆歌 | 95–120 | clear beat | educational pop | 词要清晰，节奏稳定 |
| 亲子活动 | 95–130 | bright | family pop, ukulele pop | 明亮、轻快 |
| 动画主题 | 110–140 | lively | cartoon theme song | 强 Hook，活泼 |

Prompt 关键词：

```text
bright playful rhythm, simple melody, easy to sing along, child-friendly, repetitive chorus
```

---

## 8. 情绪到 BPM / 节奏 / 编曲密度的映射

| 情绪 | 推荐 BPM | 节奏感觉 | 编曲密度 | 推荐曲风 |
|---|---:|---|---|---|
| 温暖 | 75–105 | gentle, steady | sparse to moderate | pop ballad, folk-pop, acoustic |
| 伤感 | 60–85 | slow, spacious | sparse | piano ballad, R&B ballad |
| 治愈 | 70–100 | relaxed | sparse to moderate | lo-fi, acoustic, ambient pop |
| 孤独 | 55–85 | minimal | sparse | ambient pop, piano, slow R&B |
| 怀旧 | 80–115 | steady | moderate | city pop, synth-pop, soft rock |
| 明亮 | 105–128 | upbeat | moderate | dance-pop, teen pop, acoustic pop |
| 热血 | 115–150 | driving | full | arena rock, EDM, stadium anthem |
| 史诗 | 80–130 | big build | full | cinematic, orchestral, power metal |
| 高级 | 70–110 | restrained | sparse to moderate | jazz pop, nu jazz, minimal electronic |
| 科技 | 90–130 | pulse | moderate | synth-pop, minimal electronic, techno-lite |
| 浪漫 | 65–95 | slow groove | sparse to moderate | pop ballad, R&B, bossa |
| 快乐 | 105–130 | danceable | moderate | disco-funk, dance-pop, Latin pop |
| 压迫 | 50–90 | slow heavy / dark pulse | dense or minimal | doom, trip-hop, dark electronic |
| 梦幻 | 65–100 | floating | sparse | dream pop, ambient, chillwave |

---

## 9. 输出格式到节奏策略的映射

| 输出格式 | 节奏策略 | 结构建议 |
|---|---|---|
| 简洁版 Prompt | 只写 tempo 感觉，不必写精确 BPM | 1 段 Style Prompt |
| 完整 Suno Prompt | 写 BPM 范围 + rhythm feel + energy curve | 完整歌词结构 |
| 歌词 + Style Prompt | 歌词结构和节奏匹配 | Verse / Chorus 明确 |
| 多风格版本 | 每个版本给不同 BPM 和律动 | 3 个版本对比 |
| 30 秒短视频 Hook | 节奏更直接，前奏短 | Hook / Chorus 优先 |
| 纯器乐 BGM | 强调 loop-friendly 和 non-intrusive | 8/16 小节循环感 |
| 品牌宣传 | 中速或明快，稳重不乱 | build-up + clean ending |
| 体育 / 活动 | 高能，副歌或 drop 明确 | chant / climax / drop |

---

## 10. Skill 路由逻辑

### 10.1 用户选择“带歌词歌曲”

优先判断：

```text
主题 → 情绪 → 场景 → 曲风 → 人声 → BPM → 歌曲结构
```

默认策略：

```text
如果用户没有指定 BPM，则根据曲风和情绪自动选择。
如果用户说“温暖 / 伤感 / 治愈”，优先选择 70–100 BPM。
如果用户说“热血 / 体育 / 活动开场”，优先选择 110–140 BPM。
如果用户说“短视频爆款”，优先选择 105–130 BPM，并要求 quick intro / catchy hook。
```

### 10.2 用户选择“纯器乐背景音乐”

优先判断：

```text
使用场景 → 是否需要循环 → 情绪 → 主体乐器 → BPM → 编曲密度
```

默认策略：

```text
如果是学习 / 工作：65–95 BPM，instrumental only, loop-friendly, no vocals。
如果是品牌 / 产品：90–125 BPM，clean, polished, non-intrusive。
如果是体育 / 动作：120–150 BPM，driving rhythm, powerful drums。
如果是 Vlog / 生活方式：80–115 BPM，warm, light percussion, loop-friendly。
```

---

## 11. 典型场景 Prompt 模板

### 11.1 短视频 Hook 歌曲

```text
Create a [language] [genre] song at [BPM range], with an upbeat and catchy rhythm. The intro should be very short, and the hook should appear within the first 10 seconds. Use a memorable chorus, clean production, and a strong emotional payoff. Suitable for short videos and social media sharing.
```

### 11.2 朋友圈情绪歌

```text
Create a warm [language] pop ballad at [BPM range], with a restrained rhythm and emotional vocal delivery. Start with piano or acoustic guitar, then gradually add soft drums and strings in the chorus. The mood should feel personal, sincere, and suitable for sharing with friends.
```

### 11.3 品牌宣传器乐

```text
Create an instrumental corporate pop track at [BPM range]. No vocals, no lyrics. Use clean piano, soft synths, light drums, and an uplifting but non-intrusive groove. The music should feel polished, optimistic, and suitable for brand video, product introduction, and voiceover.
```

### 11.4 学习工作 Lo-fi BGM

```text
Create a lo-fi hip-hop instrumental at [BPM range]. No vocals, no lyrics. Use dusty drums, mellow piano, warm bass, vinyl crackle, and a relaxed loop-friendly groove. Keep the arrangement subtle and non-intrusive, suitable for focus, study, and background listening.
```

### 11.5 体育主题曲

```text
Create a powerful stadium anthem at [BPM range], with driving drums, electric guitars, group vocals, and a chant-like chorus. The rhythm should feel energetic and suitable for sports events, team spirit, and crowd sing-along moments.
```

### 11.6 科技产品背景音乐

```text
Create a modern instrumental electronic track at [BPM range]. No vocals, no lyrics. Use minimal synth pulses, clean bass, subtle percussion, and a premium futuristic texture. The track should be polished, non-intrusive, and suitable for tech product videos or launch events.
```

---

## 12. Prompt 中常用节奏词库

### 12.1 速度词

```text
very slow
slow tempo
medium-slow
medium tempo
upbeat
fast-paced
high-energy
very fast
```

### 12.2 律动词

```text
laid-back groove
steady groove
driving rhythm
danceable beat
syncopated groove
four-on-the-floor
half-time feel
head-nod groove
Latin groove
swing feel
shuffle rhythm
pulsing rhythm
```

### 12.3 编曲推进词

```text
short intro
gradual build-up
restrained verse
big chorus
anthemic chorus
explosive climax
subtle variations
loop-friendly arrangement
clear ending
seamless loop
```

### 12.4 背景音乐控制词

```text
instrumental only
no vocals
no lyrics
non-intrusive
background music
suitable for voiceover
clean mix
not too busy
subtle melody
soft dynamics
```

---

## 13. 默认推荐规则

当信息不足时，Skill 可以使用以下默认值。

| 条件 | 默认推荐 |
|---|---|
| 用户只说“写一首歌” | 中文流行，中速 90–105 BPM，完整 Suno Prompt |
| 用户只说“温暖一点” | 75–100 BPM，piano / acoustic guitar，soft drums |
| 用户只说“燃一点” | 115–140 BPM，driving drums，anthemic chorus |
| 用户只说“高级感” | 70–110 BPM，jazz pop / minimal electronic / cinematic |
| 用户只说“短视频” | 105–130 BPM，quick intro，catchy hook |
| 用户只说“背景音乐” | 80–110 BPM，instrumental only，loop-friendly |
| 用户只说“学习 BGM” | 65–90 BPM，lo-fi / chillhop，no vocals |
| 用户只说“品牌宣传” | 100–125 BPM，corporate pop instrumental 或 cinematic pop |
| 用户只说“世界杯” | 95–125 BPM Latin pop 或 115–140 BPM stadium anthem |
| 用户只说“科技感” | 90–125 BPM，minimal electronic / synth-pop |

---

## 14. 质量检查清单

生成最终 Prompt 前，检查：

```text
[ ] 是否明确了带人声歌曲还是纯器乐？
[ ] 是否给出了合理 BPM 或速度描述？
[ ] 是否包含 rhythm feel / groove？
[ ] 是否匹配用户场景？
[ ] 是否匹配情绪？
[ ] 如果是短视频，是否要求 quick intro / catchy hook？
[ ] 如果是背景音乐，是否要求 no vocals / non-intrusive / loop-friendly？
[ ] 如果是品牌或商业场景，是否避免过度抢戏？
[ ] 如果是体育或活动，是否加强 chorus / chant / climax？
[ ] 是否避免直接模仿真实歌手、旋律或已有歌曲？
```

---

## 15. 参考来源与使用说明

本库的 BPM 范围主要参考了常见音乐制作、音乐教育与电子音乐资料，并结合 AI 音乐 Prompt 的实际生成需求进行了整理。不同来源对 BPM 边界会有差异，因此本库采用“可用于 Prompt 的推荐范围”，而不是绝对音乐学定义。

参考方向包括：

- Ableton Learning Music 对 Dub、Hip-hop、House、Techno/Trance、Dubstep、Drum and Bass 的典型 BPM 范围。
- MasterClass 与常见 tempo marking 资料对 Andante、Moderato、Allegro 等速度术语的 BPM 解释。
- iZotope 对 EDM / Hip-hop / Dubstep / Drum and Bass 等制作速度的说明。
- Berklee 对电子音乐类型在现代音乐制作中重要性的说明。
- 用户上传的《Decades - Suno AI Prompts.pdf》中按年代整理的 Suno 风格提示词，用于保持本库和曲风库的年代风格体系一致。

