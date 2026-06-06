# AI Music Instrumentation & Arrangement Library v0.1

> 用途：作为交互式 AI 音乐 Prompt Skill 的“乐器与编曲素材库”。
> 目标：帮助 Claude Code / Codex / AI Agent 根据用户的主题、曲风、场景、情绪与歌曲类型，自动生成更专业、更稳定、更可复制到 Suno / Udio / 类 Suno 工具中的音乐 Prompt。

---

## 0. 使用原则

AI 音乐 Prompt 中，“乐器与编曲”决定的是歌曲的声音质感、空间感、情绪推进和完成度。

不要只写：

```text
pop song, emotional, male vocal
```

应该写成：

```text
Chinese pop ballad, warm male vocal, piano and acoustic guitar intro, soft drums and bass entering in the pre-chorus, cinematic strings lifting the chorus, restrained verse, emotional final chorus, clean polished production
```

对于纯器乐，不要写：

```text
lo-fi music
```

应该写成：

```text
lo-fi hip-hop instrumental, no vocals, warm electric piano loop, dusty boom bap drums, mellow bass, vinyl crackle, soft tape saturation, subtle arrangement variations, loop-friendly ending
```

---

## 1. 编曲素材库的数据结构

每一类乐器或编曲素材建议按以下字段保存：

```text
中文名：
英文 Prompt 标签：
功能角色：rhythm / harmony / melody / texture / hook / transition / climax
适合曲风：
适合情绪：
适合场景：
常见搭配：
Prompt 关键词：
使用提醒：
```

---

## 2. Prompt 中的四层编曲逻辑

AI 音乐 Prompt 最好不要只列乐器，而要说明它们在编曲里的位置。

### 2.1 Rhythm Layer / 节奏层

决定律动、速度感和身体反应。

常见元素：

```text
drums
kick
snare
hi-hats
claps
percussion
808 drums
toms
shaker
tambourine
latin percussion
tribal drums
orchestral percussion
```

### 2.2 Harmony Layer / 和声层

决定歌曲的情绪底色。

常见元素：

```text
piano
electric piano
acoustic guitar
rhythm guitar
synth pads
strings
organ
jazz chords
choir pads
```

### 2.3 Melody / Hook Layer / 旋律与记忆点层

决定歌曲是否容易被记住。

常见元素：

```text
lead vocal
lead synth
piano motif
guitar riff
whistling melody
string melody
saxophone line
flute melody
guzheng motif
choir hook
```

### 2.4 Texture / Atmosphere Layer / 质感与氛围层

决定“高级感”“年代感”“空间感”。

常见元素：

```text
vinyl crackle
tape saturation
reverb
ambient pads
field recordings
rain sounds
city ambience
analog synth texture
lo-fi noise
wide stereo soundstage
```

---

## 3. 乐器功能分类

## 3.1 Keyboard / 键盘类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 钢琴 | piano | pop ballad, cinematic, folk-pop | 情绪、叙事、开场 |
| 立式钢琴 | upright piano | lo-fi, indie, intimate ballad | 温暖、不完美、生活感 |
| 电钢琴 | electric piano / Rhodes | R&B, neo-soul, lo-fi, jazz-hop | 柔和、律动、高级感 |
| 合成器键盘 | synth keys | synth-pop, electronic, future bass | 现代感、科技感 |
| 风琴 | organ | soul, gospel, blues rock | 复古、灵魂、宗教感 |
| 管风琴 | church organ | gothic, cinematic, epic | 庄重、黑暗、戏剧性 |
| 钢片琴 | celesta | dream pop, children’s, cinematic | 梦幻、童话感 |

Prompt 关键词：

```text
warm piano intro
soft upright piano
Rhodes electric piano chords
bright synth keys
vintage organ texture
minimal piano motif
emotional piano progression
```

使用建议：

- 情绪歌：优先 `piano intro`
- Lo-fi / Jazz-hop：优先 `Rhodes electric piano`
- 科技 / 电子：优先 `synth keys`
- Gospel / Soul：可加入 `organ`

---

## 3.2 Guitar / 吉他类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 原声吉他 | acoustic guitar | folk, pop ballad, travel, wedding | 真诚、温暖、叙事 |
| 指弹吉他 | fingerpicked acoustic guitar | folk, country, intimate song | 细腻、个人感 |
| 节奏吉他 | rhythm guitar | pop-rock, indie rock | 推进、律动 |
| 电吉他 | electric guitar | rock, pop-rock, blues, metal | 力量、Hook、情绪爆发 |
| 失真吉他 | distorted electric guitar | hard rock, metal, punk | 重、燃、攻击性 |
| 清音吉他 | clean electric guitar | indie, city pop, math rock, post-rock | 清爽、空间感 |
| 延迟吉他 | delay guitar | post-rock, ambient rock, cinematic | 空间、递进、史诗感 |
| 滑棒吉他 | slide guitar | blues, country, Americana | 乡村、蓝调、怀旧 |
| 放克吉他 | funk guitar | funk, disco, R&B | 律动、时尚、身体感 |
| 冲浪吉他 | surf guitar | surf rock, retro, beach | 阳光、复古、海边 |

Prompt 关键词：

```text
acoustic guitar driven
fingerpicked acoustic guitar
clean electric guitar arpeggios
crunchy rhythm guitar
distorted guitar riffs
delay-soaked guitar lines
funky guitar chops
anthemic electric guitar solo
```

使用建议：

- 民谣：`fingerpicked acoustic guitar`
- 青春流行：`acoustic guitar + light drums`
- 摇滚：`electric guitar riffs + powerful drums`
- Post-rock：`clean delay guitars + gradual build-up`
- Funk / Disco：`funky guitar chops`

---

## 3.3 Bass / 贝斯与低频类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 电贝斯 | electric bass | pop, rock, funk, R&B | 支撑律动 |
| 原声贝斯 | upright bass | jazz, bossa nova, lounge | 高级、自然 |
| 合成器贝斯 | synth bass | electronic, synth-pop, future bass | 现代、厚重 |
| 808 贝斯 | 808 bass | trap, hip-hop, drill | 低频冲击、潮流 |
| 放克贝斯 | funky bassline / slap bass | funk, disco, city pop | 律动核心 |
| Sub Bass | sub bass | EDM, D&B, dubstep | 强低频、空间震动 |
| Walking Bass | walking bass | jazz, swing | 摇摆、爵士感 |

Prompt 关键词：

```text
warm bass groove
deep 808 bass
funky slap bassline
smooth electric bass
sub bass pulse
walking upright bass
round mellow bass
```

使用建议：

- R&B：`smooth bass groove`
- Funk：`funky slap bassline`
- Trap：`deep 808 bass`
- Jazz：`walking upright bass`
- 科技背景：`subtle synth bass pulse`

---

## 3.4 Drums / 鼓组类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 原声鼓 | acoustic drums | rock, pop-rock, folk-rock | 自然、真实、现场感 |
| 电子鼓 | electronic drums | pop, EDM, synth-pop | 现代、干净 |
| 软鼓点 | soft drums | ballad, folk, chill | 克制、温柔 |
| 强鼓点 | powerful drums | rock, sports, anthem | 热血、推进 |
| Boom bap 鼓 | boom bap drums | hip-hop, lo-fi, jazz-hop | 复古、律动 |
| Trap 鼓 | trap drums | trap, hip-hop, pop | hi-hat 滚动、现代感 |
| 四拍鼓 | four-on-the-floor | house, disco, dance-pop | 舞曲、稳定推进 |
| Breakbeat | breakbeat drums | D&B, jungle, big beat | 高速、破碎、能量 |
| 大鼓 / 战鼓 | epic drums / taiko-like drums | cinematic, sports, trailer | 史诗、仪式感 |
| 手拍 | hand claps | pop, children’s, corporate | 明亮、亲和 |
| 踩镲 | hi-hats | hip-hop, trap, pop | 速度感与细节 |

Prompt 关键词：

```text
soft brushed drums
powerful live drums
tight electronic drums
dusty boom bap drums
trap hi-hat rolls
four-on-the-floor kick
cinematic epic drums
hand claps and light percussion
```

使用建议：

- 朋友圈情绪歌：`soft drums`
- 体育主题：`powerful drums + crowd claps`
- Lo-fi：`dusty boom bap drums`
- 舞曲：`four-on-the-floor drums`
- 史诗：`cinematic epic drums`

---

## 3.5 Percussion / 打击乐类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 沙锤 | shaker | folk, pop, bossa, acoustic | 轻快、细节 |
| 铃鼓 | tambourine | folk, gospel, pop-rock | 明亮、复古 |
| 康加鼓 | congas | Latin, Afrobeat, world | 拉丁、律动 |
| 邦戈鼓 | bongos | bossa nova, Latin, chill | 轻松、生活感 |
| 卡宏鼓 | cajon | acoustic, folk, unplugged | 原声、亲近 |
| 木箱 / 木鱼 | wood percussion | children’s, world, organic | 自然、童趣 |
| 铜钹 | cymbals | rock, cinematic | 爆发、转场 |
| 军鼓滚奏 | snare roll | cinematic, sports | 推进、紧张 |
| 太鼓感大鼓 | taiko-like drums | epic, Chinese cinematic, sports | 庄重、史诗 |

Prompt 关键词：

```text
light shaker groove
tambourine accents
latin percussion groove
bongos and soft guitar
cajon-driven acoustic rhythm
snare roll build-up
taiko-like epic drums
```

---

## 3.6 Strings / 弦乐类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 弦乐组 | strings / string section | pop ballad, cinematic, orchestral pop | 情绪抬升 |
| 小提琴 | violin | cinematic, folk, romantic | 旋律、抒情 |
| 大提琴 | cello | emotional, sad, cinematic | 深沉、孤独 |
| 弦乐铺底 | string pads | pop, cinematic | 氛围、厚度 |
| 弦乐渐强 | string build-up | anthem, cinematic | 推进、高潮 |
| 拨弦 | pizzicato strings | children’s, playful, quirky | 轻快、俏皮 |
| 管弦乐 | orchestral strings | epic, trailer, brand film | 大片感 |

Prompt 关键词：

```text
cinematic strings
warm string section
emotional cello line
swelling strings in the chorus
orchestral string build-up
pizzicato strings
```

使用建议：

- 情绪副歌：`swelling strings in the chorus`
- 孤独、成熟：`emotional cello line`
- 品牌大片：`orchestral string build-up`
- 儿童 / 俏皮：`pizzicato strings`

---

## 3.7 Brass / 铜管类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 铜管组 | brass section | funk, soul, big band, sports | 力量、明亮 |
| 小号 | trumpet | jazz, Latin, cinematic | 明亮、号召 |
| 长号 | trombone | funk, jazz, big band | 厚度、幽默感 |
| 圆号 | French horn | cinematic, epic, orchestral | 英雄感、宽广 |
| 铜管重音 | brass stabs | funk, disco, sports | 节奏强调 |
| 史诗铜管 | epic brass | trailer, sports, anthem | 大片、胜利感 |

Prompt 关键词：

```text
brass stabs
bright trumpet lines
funky brass section
epic brass hits
heroic French horns
big band brass arrangement
```

使用建议：

- Funk / Disco：`brass stabs`
- 体育：`epic brass hits`
- 复古爵士：`big band brass arrangement`
- 电影英雄感：`heroic French horns`

---

## 3.8 Woodwinds / 木管与吹奏类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 长笛 | flute | folk, cinematic, Chinese, dream pop | 空灵、自然 |
| 单簧管 | clarinet | jazz, vintage, playful | 复古、俏皮 |
| 萨克斯 | saxophone | jazz, city pop, R&B, synthwave | 都市、性感、复古 |
| 口琴 | harmonica | folk, blues, Americana | 公路、乡村、叙事 |
| 哨声 | whistling | pop, vlog, children’s | 轻快、Hook |

Prompt 关键词：

```text
soft flute melody
smooth saxophone solo
nostalgic harmonica line
playful clarinet phrase
catchy whistling hook
```

使用建议：

- City pop / 夜晚城市：`smooth saxophone solo`
- 民谣 / 公路：`nostalgic harmonica line`
- 儿童 / Vlog：`catchy whistling hook`

---

## 3.9 Synths / 合成器类

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 合成器铺底 | synth pads | electronic, cinematic, ambient | 空间、氛围 |
| 主奏合成器 | lead synth | synth-pop, EDM, future bass | Hook、旋律 |
| 模拟合成器 | analog synths | synthwave, retro, 80s | 复古、霓虹 |
| 琶音器 | arpeggiator / arpeggiated synth | electronic, techno, synthwave | 流动、科技 |
| 脉冲贝斯 | pulsing synth bass | tech, product, electronic | 推进、冷静 |
| 合成器弦乐 | synth strings | 80s pop, retro, cinematic | 年代感 |
| 颗粒质感 | granular texture | experimental, ambient | 细碎、未来 |
| Glitch | glitch effects | IDM, tech, experimental | 数字感、破碎 |

Prompt 关键词：

```text
warm synth pads
bright lead synth hook
analog synth texture
arpeggiated synth pattern
pulsing synth bass
glitchy electronic textures
retro-futuristic synthwave sound
```

使用建议：

- 科技产品：`minimal synth pulse + clean electronic texture`
- 80s 复古：`analog synths + gated drums`
- Future bass：`bright lead synth + sidechain pads`
- Ambient：`warm synth pads + spacious reverb`

---

## 3.10 Chinese / Oriental Instruments / 中国与东方乐器

| 中文名 | 英文 Prompt 标签 | 适合曲风 | 典型作用 |
|---|---|---|---|
| 古筝 | guzheng | 国风、文旅、江南、东方流行 | 东方感、流水感 |
| 琵琶 | pipa | 国风、武侠、戏剧化 | 颗粒感、节奏感 |
| 二胡 | erhu | 情绪、故乡、沧桑 | 深情、哀而不伤 |
| 笛子 | dizi / Chinese bamboo flute | 江南、山水、自然 | 清亮、空间 |
| 箫 | xiao | 古风、空灵、静谧 | 深远、禅意 |
| 扬琴 | yangqin | 民乐融合、轻快 | 清脆、流动 |
| 中国鼓 | Chinese drums | 史诗、体育、国潮 | 力量、仪式感 |
| 戏曲打击 | Chinese opera percussion | 戏腔、国潮、戏剧化 | 转场、张力 |
| 唢呐 | suona | 民俗、喜庆、强烈戏剧 | 高能、标志性 |

Prompt 关键词：

```text
guzheng motif
pipa plucked accents
erhu emotional melody
dizi flute line
Chinese bamboo flute
Chinese percussion
cinematic Chinese orchestral pop
modern pop with traditional Chinese instruments
```

使用建议：

- 江南 / 文旅：`guzheng + dizi + cinematic strings`
- 故乡 / 情绪：`erhu emotional melody`
- 国潮 / 运动：`Chinese drums + electronic beat`
- 古风：`guzheng, pipa, xiao, poetic atmosphere`

---

## 3.11 World / Regional Instruments / 世界音乐色彩

| 中文名 | 英文 Prompt 标签 | 适合场景 | 典型作用 |
|---|---|---|---|
| 尤克里里 | ukulele | vlog, children’s, travel | 轻松、阳光 |
| 曼陀林 | mandolin | folk, travel, country | 清脆、旅行感 |
| 手风琴 | accordion | French, tango, vintage | 欧陆、复古 |
| 西塔琴 | sitar | psychedelic, Indian fusion | 迷幻、异域 |
| 非洲鼓 | African drums / djembe | Afrobeat, world, sports | 律动、生命力 |
| 钢鼓 | steel drums | tropical, Caribbean, summer | 海岛、夏天 |
| 卡林巴 | kalimba | children’s, healing, ambient | 轻柔、治愈 |
| 尼龙弦吉他 | nylon guitar | bossa nova, Latin, romantic | 温柔、拉丁 |

Prompt 关键词：

```text
ukulele and hand claps
nylon guitar and soft percussion
accordion melody
sitar-inspired psychedelic texture
Afrobeat percussion groove
tropical steel drums
kalimba motif
```

---

## 4. 编曲结构素材库

## 4.1 常见歌曲段落

| 段落 | 英文标签 | 编曲作用 |
|---|---|---|
| 前奏 | [Intro] | 建立氛围、引出主旋律 |
| 主歌 | [Verse] | 叙事、低密度、铺垫 |
| 预副歌 | [Pre-Chorus] | 增加张力、准备副歌 |
| 副歌 | [Chorus] | 情绪爆发、记忆点 |
| 桥段 | [Bridge] | 情绪转折、制造变化 |
| 间奏 | [Instrumental Break] | 乐器展示、喘息 |
| 落段 | [Breakdown] | 降低密度、制造反差 |
| Drop | [Drop] | 电子音乐高潮 |
| 最终副歌 | [Final Chorus] | 强化情绪、全编制 |
| 尾奏 | [Outro] | 收束、淡出或循环 |

Prompt 关键词：

```text
restrained verse
build-up pre-chorus
big emotional chorus
instrumental break with guitar solo
breakdown before final chorus
final chorus with full arrangement
fade-out outro
loop-friendly outro
```

---

## 4.2 编曲密度变化

| 中文描述 | 英文 Prompt 表达 | 适合场景 |
|---|---|---|
| 从少到多 | gradually builds | 大多数歌曲 |
| 克制主歌 | restrained verse | 情绪歌、品牌歌 |
| 副歌爆发 | explosive chorus / full chorus | 热血、抒情爆发 |
| 层层推进 | layered build-up | 电影感、体育 |
| 先安静后明亮 | starts intimate, becomes uplifting | 人生、成长、亲情 |
| 中段降密度 | stripped-down bridge | 情绪转折 |
| 最后全编制 | full arrangement in final chorus | 大合唱、高潮 |
| 保持低密度 | minimal arrangement | BGM、Lo-fi、科技 |
| 循环友好 | loop-friendly arrangement | 短视频、背景音乐 |

Prompt 关键词：

```text
starts minimal and gradually builds
restrained verses with sparse instrumentation
chorus opens up with full drums and strings
stripped-down bridge before the final chorus
full arrangement in the final chorus
minimal non-intrusive background arrangement
loop-friendly structure with subtle variations
```

---

## 4.3 常见转场与效果

| 中文名 | 英文 Prompt 标签 | 用途 |
|---|---|---|
| 上升音效 | riser | 进入副歌 / Drop |
| 反向音效 | reverse swell | 转场、梦幻 |
| 鼓花 | drum fill | 段落切换 |
| 停顿 | stop-time break | 制造记忆点 |
| 扫频 | filter sweep | 电子转场 |
| 白噪上升 | white noise rise | EDM / pop build-up |
| 低频下潜 | bass drop | 电子高潮 |
| 余音混响 | reverb tail | 空间感、收尾 |
| 淡出 | fade out | 复古、循环 |
| 现场欢呼 | crowd chant / crowd ambience | 体育、演唱会感 |

Prompt 关键词：

```text
short drum fill before the chorus
riser into the drop
reverse swell transition
brief stop-time before the hook
filter sweep build-up
crowd chant atmosphere
wide reverb tail
```

---

## 5. 曲风到乐器 / 编曲映射

## 5.1 Pop / 流行

推荐乐器：

```text
piano, acoustic guitar, electric guitar, bass, drums, synth pads, strings, hand claps
```

推荐编曲：

```text
clean pop production, verse-pre-chorus-chorus structure, memorable chorus, polished drums, layered backing vocals
```

Prompt 示例：

```text
modern pop arrangement with clean drums, warm piano, subtle synth pads, bass groove, hand claps, and a big memorable chorus
```

---

## 5.2 Chinese Pop Ballad / 中文流行抒情

推荐乐器：

```text
piano, acoustic guitar, strings, soft drums, bass, subtle pads
```

推荐编曲：

```text
piano intro, restrained verse, strings entering in pre-chorus, emotional chorus, final chorus with fuller arrangement
```

Prompt 示例：

```text
warm Chinese pop ballad arrangement, emotional piano intro, acoustic guitar layers, soft drums, cinematic strings lifting the chorus, restrained verse and powerful final chorus
```

---

## 5.3 Folk / 民谣

推荐乐器：

```text
acoustic guitar, fingerpicked guitar, harmonica, cajon, light percussion, upright bass, soft strings
```

推荐编曲：

```text
organic acoustic arrangement, intimate vocal, simple rhythm, storytelling structure
```

Prompt 示例：

```text
acoustic folk-pop arrangement with fingerpicked guitar, warm bass, light cajon, soft harmonica, intimate organic texture
```

---

## 5.4 Rock / Metal / 摇滚与金属

推荐乐器：

```text
electric guitar, distorted guitar, bass, live drums, toms, cymbals, guitar solo, choir or gang vocals for anthem styles
```

推荐编曲：

```text
powerful drums, driving guitar riffs, anthemic chorus, breakdown or guitar solo, high-energy final chorus
```

不同子风格：

| 子风格 | 乐器 / 编曲重点 |
|---|---|
| pop-rock | clean guitars, punchy drums, catchy chorus |
| arena rock | huge drums, soaring guitar, group vocals, stadium chorus |
| hard rock | distorted riffs, powerful drums, gritty vocal |
| heavy metal | heavy palm-muted guitar riffs, double kick drums, aggressive energy |
| power metal | fast drums, epic guitars, heroic chorus, orchestral accents |
| post-rock | clean delay guitars, gradual build-up, cinematic drums, instrumental climax |
| math rock | clean tapping guitars, complex rhythms, bright tone |
| shoegaze | wall of guitars, reverb, dreamy texture |

Prompt 示例：

```text
arena rock arrangement with huge live drums, electric guitar riffs, bass drive, soaring chorus, crowd chant energy, and a powerful final chorus
```

```text
post-rock instrumental arrangement with clean delay guitars, deep bass, cinematic drums, slow emotional build-up, and a massive instrumental climax
```

---

## 5.5 R&B / Soul

推荐乐器：

```text
Rhodes electric piano, smooth bass, soft drums, snap percussion, organ, strings, backing harmonies
```

推荐编曲：

```text
laid-back groove, warm chords, expressive vocal space, subtle rhythmic details
```

Prompt 示例：

```text
smooth R&B arrangement with Rhodes electric piano, mellow bass groove, soft drums, snap percussion, warm backing harmonies, and late-night atmosphere
```

---

## 5.6 Hip-hop / Rap

推荐乐器：

```text
808 bass, boom bap drums, trap hi-hats, chopped samples, synth plucks, piano loop, brass hits
```

推荐编曲：

```text
beat-driven arrangement, strong groove, hook section, sparse verse, bass-heavy mix
```

Prompt 示例：

```text
modern trap-pop beat with deep 808 bass, crisp trap hi-hats, dark synth plucks, sparse verse arrangement, and a catchy hook section
```

```text
lo-fi boom bap arrangement with dusty drums, mellow piano loop, warm bass, vinyl crackle, and relaxed head-nod groove
```

---

## 5.7 Electronic / 电子

推荐乐器：

```text
synth pads, lead synth, electronic drums, pulsing bass, arpeggiator, risers, drops, sidechain pads
```

推荐编曲：

```text
intro groove, build-up, drop, breakdown, second build, final drop
```

Prompt 示例：

```text
uplifting electronic pop arrangement with bright synth leads, sidechain pads, punchy electronic drums, pulsing bass, energetic build-up, and melodic drop
```

---

## 5.8 Disco / Funk

推荐乐器：

```text
funky bassline, clean guitar chops, brass stabs, hand claps, four-on-the-floor drums, strings
```

推荐编曲：

```text
danceable groove, syncopated rhythm, bright brass accents, party energy
```

Prompt 示例：

```text
retro disco-funk arrangement with funky bassline, clean guitar chops, brass stabs, hand claps, four-on-the-floor drums, and glossy 1970s dancefloor energy
```

---

## 5.9 Jazz / Lounge / Vocal

推荐乐器：

```text
upright bass, piano, brushed drums, saxophone, trumpet, jazz guitar, strings
```

推荐编曲：

```text
smooth jazz chords, elegant rhythm section, warm lounge atmosphere
```

Prompt 示例：

```text
elegant jazz-pop arrangement with warm piano chords, upright bass, brushed drums, smooth saxophone lines, and classy lounge atmosphere
```

---

## 5.10 Latin / Reggae / World

推荐乐器：

```text
nylon guitar, latin percussion, congas, bongos, brass, accordion, tropical drums, reggae guitar skank
```

推荐编曲：

```text
syncopated groove, danceable rhythm, warm guitar, tropical atmosphere
```

Prompt 示例：

```text
Latin pop arrangement with nylon guitar, congas, bongos, bright brass accents, danceable percussion groove, and warm summer energy
```

```text
reggae-pop arrangement with offbeat guitar skank, warm bassline, relaxed drums, tropical percussion, and laid-back sunny atmosphere
```

---

## 5.11 Chinese / 国风

推荐乐器：

```text
guzheng, pipa, erhu, dizi, xiao, Chinese drums, cinematic strings, modern pop drums
```

推荐编曲：

```text
traditional Chinese instrument motif, modern pop rhythm, cinematic strings, poetic atmosphere
```

Prompt 示例：

```text
modern Chinese traditional pop arrangement with guzheng motif, dizi flute lines, cinematic strings, soft pop drums, and poetic oriental atmosphere
```

---

## 5.12 Cinematic / Stage & Screen

推荐乐器：

```text
piano, orchestral strings, brass, epic drums, choir, ambient pads, sound design risers
```

推荐编曲：

```text
slow build-up, wide soundstage, emotional climax, orchestral layers
```

Prompt 示例：

```text
cinematic orchestral pop arrangement with emotional piano, swelling strings, epic drums, heroic brass, wide soundstage, and a dramatic final climax
```

---

## 6. 现代流行器乐编曲库

纯器乐 Prompt 必须明确：

```text
instrumental only, no vocals, no lyrics, no rap, no spoken words
```

如果用于短视频 / 背景音乐，建议加入：

```text
loop-friendly, background music, non-intrusive, subtle variations
```

---

## 6.1 Lo-fi / Chill / Study Instrumental

推荐乐器：

```text
Rhodes electric piano, soft piano, mellow bass, dusty boom bap drums, vinyl crackle, tape saturation, soft pads
```

推荐编曲：

```text
short loop, subtle variations, steady groove, warm texture, no strong climax
```

Prompt 示例：

```text
lo-fi hip-hop instrumental, no vocals, warm Rhodes electric piano loop, dusty boom bap drums, mellow bass, vinyl crackle, soft tape saturation, cozy and relaxed mood, subtle variations, loop-friendly ending
```

---

## 6.2 Instrumental Hip-hop / Urban Beats

推荐乐器：

```text
808 bass, boom bap drums, trap hi-hats, chopped vocal samples, piano loop, synth plucks, brass hits
```

推荐编曲：

```text
beat-driven, strong groove, sparse melody, clear hook motif, bass-heavy mix
```

Prompt 示例：

```text
instrumental hip-hop beat, no vocals, deep bass, tight drums, chopped piano sample, subtle brass hits, urban night mood, catchy instrumental hook, clean modern mix
```

---

## 6.3 Electronic Instrumental

推荐乐器：

```text
analog synths, synth pads, lead synth, arpeggiator, electronic drums, pulsing bass, risers, drops
```

推荐编曲：

```text
intro, build-up, drop, breakdown, final drop
```

Prompt 示例：

```text
synthwave instrumental, no vocals, analog synth arpeggios, gated drums, pulsing bass, neon retro-futuristic mood, wide reverb, cinematic night drive atmosphere
```

```text
minimal electronic instrumental, no vocals, clean synth pulses, subtle bass, light electronic percussion, premium tech product background music, non-intrusive and loop-friendly
```

---

## 6.4 Guitar / Band Instrumental

推荐乐器：

```text
clean electric guitar, delay guitar, bass, live drums, acoustic guitar, reverb, ambient pads
```

推荐编曲：

```text
motif-based, gradual build-up, instrumental climax, emotional arc
```

Prompt 示例：

```text
post-rock instrumental, no vocals, clean delay guitars, warm bass, cinematic live drums, ambient pads, gradual emotional build-up, massive instrumental climax, hopeful and expansive mood
```

---

## 6.5 Lifestyle / Commercial Instrumental

推荐乐器：

```text
piano, acoustic guitar, ukulele, soft synths, light drums, hand claps, bass, strings
```

推荐编曲：

```text
clean, positive, friendly, polished, loop-friendly, no distracting melody
```

Prompt 示例：

```text
uplifting corporate pop instrumental, no vocals, bright piano, acoustic guitar, soft synth pads, light drums, hand claps, clean bass, optimistic and polished brand video background music, loop-friendly
```

---

## 6.6 Sports / Action Instrumental

推荐乐器：

```text
epic drums, electric guitar, brass, strings, synth bass, risers, crowd ambience
```

推荐编曲：

```text
strong pulse, build-up, impact hits, heroic climax, high energy
```

Prompt 示例：

```text
sports highlight instrumental, no vocals, powerful drums, electric guitar riffs, epic brass hits, cinematic strings, risers, crowd ambience, energetic build-up and heroic climax
```

---

## 6.7 Chinese / Oriental Instrumental

推荐乐器：

```text
guzheng, pipa, erhu, dizi, xiao, Chinese drums, cinematic strings, ambient pads
```

推荐编曲：

```text
traditional motif, modern rhythm, cinematic atmosphere, elegant emotional movement
```

Prompt 示例：

```text
modern Chinese instrumental, no vocals, guzheng motif, dizi flute melody, soft cinematic strings, subtle electronic pads, gentle percussion, elegant oriental atmosphere, suitable for travel and cultural video background
```

---

## 7. 场景到乐器 / 编曲推荐映射

| 使用场景 | 推荐乐器 | 推荐编曲 |
|---|---|---|
| 朋友圈个人歌曲 | piano, acoustic guitar, strings | restrained verse, emotional chorus |
| 短视频 Hook | punchy drums, synth hook, claps | chorus early, catchy motif |
| 品牌宣传 | piano, synth pads, guitar, light drums | clean, uplifting, polished |
| 科技产品 | minimal synths, pulse bass, electronic percussion | clean, futuristic, non-intrusive |
| 体育赛事 | drums, electric guitar, brass, choir | powerful build-up, stadium chorus |
| 世界杯主题 | latin percussion, drums, brass, group vocals | danceable rhythm, chant chorus |
| 城市宣传 | piano, strings, synth pads, drums | cinematic build, wide soundstage |
| 文旅宣传 | guzheng, dizi, strings, soft drums | poetic, oriental, cinematic |
| 婚礼 | piano, acoustic guitar, strings | warm, romantic, emotional lift |
| 毕业季 | acoustic guitar, piano, light drums | nostalgic, youthful, uplifting |
| 学习 / 工作 BGM | Rhodes, soft piano, dusty drums | low-density, loop-friendly |
| Vlog | ukulele, guitar, light percussion | bright, casual, friendly |
| 儿童教育 | ukulele, hand claps, bells, children’s choir | playful, simple, repetitive |
| 播客片头 | short synth motif, clean drums, bass | concise, branded, memorable |

---

## 8. 情绪到乐器 / 编曲推荐映射

| 情绪 | 推荐乐器 | 编曲策略 |
|---|---|---|
| 温暖 | piano, acoustic guitar, soft strings | soft intro, gentle build |
| 伤感 | piano, cello, soft pads | sparse verse, emotional chorus |
| 治愈 | acoustic guitar, kalimba, soft piano | light rhythm, warm texture |
| 热血 | drums, electric guitar, brass | powerful build, big chorus |
| 孤独 | piano, ambient pads, cello | minimal, spacious, restrained |
| 怀旧 | analog synths, saxophone, vinyl texture | retro production, warm reverb |
| 明亮 | claps, ukulele, guitar, light drums | upbeat, simple, sunny |
| 高级感 | Rhodes, upright bass, brushed drums, sax | elegant, restrained, smooth |
| 电影感 | piano, strings, epic drums, brass | gradual build, wide soundstage |
| 科技感 | minimal synth, pulse bass, electronic percussion | clean, precise, futuristic |
| 梦幻 | pads, celesta, reverb guitar | airy, soft, spacious |
| 史诗 | orchestral strings, brass, choir, epic drums | layered, dramatic, climactic |

---

## 9. 编曲 Prompt 固定短语库

## 9.1 开头 / Intro

```text
piano intro
acoustic guitar intro
ambient synth intro
cinematic string intro
short instrumental intro
atmospheric intro
minimal intro with soft pads
intro with distant crowd ambience
```

## 9.2 主歌 / Verse

```text
restrained verse arrangement
sparse verse with piano and vocal
low-density verse
intimate verse with acoustic guitar
verse driven by soft bass groove
minimal drums in the verse
```

## 9.3 预副歌 / Pre-Chorus

```text
pre-chorus gradually builds tension
drums and bass enter in the pre-chorus
rising strings before the chorus
subtle synth build-up before the hook
```

## 9.4 副歌 / Chorus

```text
big emotional chorus
catchy chorus with full arrangement
anthemic chorus
chorus opens up with drums and strings
stadium-style chorus
choir-backed final chorus
```

## 9.5 桥段 / Bridge

```text
stripped-down bridge
bridge with only piano and vocal
instrumental bridge with guitar solo
cinematic bridge with strings and drums
quiet bridge before the final chorus
```

## 9.6 尾奏 / Outro

```text
soft fade-out outro
loop-friendly outro
piano outro
reverb-heavy outro
short clean ending
final chord with long reverb tail
```

## 9.7 纯器乐排除词

```text
instrumental only
no vocals
no lyrics
no rap
no spoken words
background music
non-intrusive
loop-friendly
subtle variations
```

---

## 10. Skill 生成 Prompt 时的使用规则

### 10.1 带人声歌曲

必须至少指定：

```text
Genre
Mood
Vocal
Main Instruments
Arrangement Development
Chorus Treatment
Production Texture
```

推荐公式：

```text
Create a [genre] song with a [mood] atmosphere. Use [vocal style]. Start with [intro instruments], keep the verses [arrangement density], then build into [chorus arrangement]. Include [main instruments]. The emotional curve should move from [starting emotion] to [ending emotion]. The chorus should be [catchy / anthemic / emotional / cinematic].
```

### 10.2 纯器乐背景音乐

必须至少指定：

```text
Instrumental only
No vocals
Use Case
Genre
Mood
BPM / Groove
Main Instruments
Texture
Loopability
```

推荐公式：

```text
Create a [genre] instrumental track, no vocals, no lyrics. It should be used for [use case]. Mood: [mood]. Tempo: [BPM or tempo]. Main instruments: [instruments]. Arrangement: [arrangement]. Texture: [production texture]. Make it [loop-friendly / non-intrusive / cinematic / energetic] with subtle variations.
```

---

## 11. 常见错误与修正

### 错误 1：只列曲风，不列乐器

不推荐：

```text
Chinese pop, emotional
```

推荐：

```text
Chinese pop ballad with warm piano intro, acoustic guitar layers, soft drums, cinematic strings in the chorus, emotional male vocal, polished production
```

### 错误 2：纯器乐没有写 no vocals

不推荐：

```text
lo-fi background music
```

推荐：

```text
lo-fi hip-hop instrumental, no vocals, no lyrics, warm Rhodes piano loop, dusty drums, mellow bass, vinyl crackle, loop-friendly background music
```

### 错误 3：编曲没有动态变化

不推荐：

```text
piano, guitar, drums, strings
```

推荐：

```text
piano and acoustic guitar in the intro, restrained verse, drums and bass enter in the pre-chorus, strings lift the chorus, full arrangement in the final chorus
```

### 错误 4：乐器和场景不匹配

例如“学习 BGM”不宜写：

```text
explosive drums, aggressive guitar, huge chorus
```

应改为：

```text
soft piano, mellow bass, light drums, warm pads, low-density arrangement, loop-friendly and non-intrusive
```

---

## 12. 与其他素材库的关系

本文件应与以下素材库配合使用：

```text
ai_music_genre_library_v0.2.md
ai_music_rhythm_bpm_scene_mapping_v0.1.md
ai_music_vocal_voice_library_v0.1.md
```

组合逻辑：

```text
Genre Library 决定曲风
Rhythm / BPM Library 决定速度和律动
Vocal Library 决定人声
Instrumentation / Arrangement Library 决定乐器、编曲和声音质感
```

最终 Prompt 应该由这四类信息共同生成，而不是只依赖单一曲风标签。

---

## 13. 参考来源说明

本文件参考了此前整理的曲风库、BPM 映射库、人声库，以及 Suno 年代风格 Prompt 样例中关于 crooner vocals、harmony vocals、electric guitar riffs、funky keys、horn stabs、disco-funk、synthpop、arena rock、grunge、G-Funk、Y2K dance-pop 等乐器与编曲提示词的表达方式。

同时也参考了现代音乐制作中常见的 drums / bass / chords / melody / song structure 分层逻辑，以及 AI 音乐 Prompt 中对 structure tags、scene-based language、instrumentation 和 arrangement development 的常见写法。
