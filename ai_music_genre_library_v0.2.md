# AI Music Genre Library v0.2

> 用途：作为交互式 AI 音乐 Prompt Skill 的曲风素材库。  
> 目标：把用户的模糊需求，转译成 Suno / Udio / 类 Suno AI 音乐软件可理解的专业 Prompt。  
> 更新重点：从“泛曲风列表”升级为“带人声歌曲曲风库 + 现代流行器乐曲风库 + 年代风格增强器”。

---

## 0. 设计原则

这个曲风库不是音乐百科，而是 **Prompt 可用的风格知识库**。

因此，每个曲风都要服务最终生成：

```text
Genre + Era + Mood + BPM + Vocal/Instrumental + Instrumentation + Arrangement + Production Texture + Use Case
```

对于带歌词歌曲，重点是：

```text
曲风 + 人声 + 歌词结构 + 副歌设计 + 编曲推进
```

对于纯器乐，重点是：

```text
曲风 + 用途 + BPM + 主乐器 + 律动 + 质感 + 是否可循环 + 情绪曲线
```

---

## 1. 曲风数据结构

建议每个曲风按如下字段维护：

```text
Genre ID:
中文名：
英文 Prompt 标签：
一级分类：
二级分类：
是否适合人声：
是否适合纯器乐：
适合主题：
适合场景：
情绪关键词：
BPM 范围：
人声建议：
主乐器 / 声音元素：
编曲特点：
制作质感：
Prompt 关键词：
不适合情况：
示例 Style Prompt：
```

---

## 2. Skill 交互路由逻辑

在问用户曲风之前，Skill 应先判断：

```text
你想生成的是：
A. 带歌词的歌曲
B. 纯器乐背景音乐
C. 两个都要，先给我多个方向
```

### 2.1 带歌词歌曲需要采集

```text
主题 / 使用场景 / 曲风 / 情绪 / 语言 / 人声 / 节奏 / 输出格式
```

### 2.2 纯器乐需要采集

```text
用途 / 情绪 / 曲风 / BPM / 主乐器 / 质感 / 是否可循环 / 输出长度
```

### 2.3 信息不足时默认值

```text
语言：中文
节奏：中速
输出格式：完整 Suno Prompt 包
歌曲结构：[Intro] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Bridge] [Final Chorus] [Outro]
纯器乐默认：instrumental only, no vocals, loop-friendly, polished production
```

---

# 3. Vocal Song Genre Library / 带人声歌曲曲风库

---

## 3.1 Pop / 流行类

### 3.1.1 Chinese Pop / 中文流行

- 英文标签：Chinese pop, Mandopop, C-pop
- 适合主题：爱情、成长、亲情、城市生活、人生故事
- 适合场景：朋友圈、短视频、个人纪念、公众号配乐
- BPM：80–115
- 人声：warm male vocal, soft female vocal, clear youthful vocal
- 乐器：piano, acoustic guitar, soft drums, strings
- Prompt 关键词：melodic, emotional, radio-friendly, memorable chorus, polished production

示例：

```text
Chinese pop song with warm emotional vocals, medium tempo, melodic piano and guitar arrangement, polished production, memorable chorus, suitable for personal sharing and short videos.
```

### 3.1.2 Chinese Pop Ballad / 中文流行抒情

- BPM：65–95
- 情绪：warm, melancholic, bittersweet, hopeful
- 人声：mature emotional male vocal / soft female vocal
- 编曲：钢琴开头，副歌加入弦乐与鼓组，情绪逐步抬升
- 适合：中年人生、爱情遗憾、亲情、个人故事

Prompt 关键词：

```text
emotional Chinese pop ballad, warm piano, cinematic strings, restrained verse, uplifting chorus
```

### 3.1.3 Modern Pop / 现代流行

- BPM：95–125
- 适合：品牌、短视频、年轻用户、活动传播
- 人声：clean pop vocal, youthful vocal
- 编曲：电子鼓、合成器、清晰副歌
- 关键词：modern, catchy, polished, bright, hook-driven

### 3.1.4 Dance-pop / 舞曲流行

- BPM：110–130
- 适合：活动、短视频、派对、年轻品牌
- 乐器：synth bass, electronic drums, hand claps, bright synths
- 关键词：danceable, upbeat, glossy production, catchy hook

### 3.1.5 Synth-pop / 合成器流行

- BPM：90–125
- 情绪：复古、未来、霓虹、科技感
- 乐器：analog synths, drum machines, pads
- 适合：科技产品、复古短视频、城市夜景
- 关键词：retro-futuristic, neon, synth-driven, atmospheric

### 3.1.6 Electro-pop / 电子流行

- BPM：100–130
- 适合：时尚、品牌、潮流、短视频
- 关键词：electronic pop, crisp beats, bright synths, polished vocal, modern texture

### 3.1.7 Teen Pop / 青少年流行

- BPM：100–130
- 适合：校园、青春、亲子、年轻活动
- 关键词：bright, playful, catchy, youthful, clean vocal

### 3.1.8 City Pop / 城市流行

- BPM：90–115
- 适合：都市夜晚、复古、生活方式、Vlog
- 乐器：funky bass, electric piano, clean guitar, smooth drums
- 关键词：Japanese city pop feeling, urban night, smooth groove, nostalgic, polished

### 3.1.9 Dream Pop / 梦幻流行

- BPM：70–105
- 适合：治愈、梦幻、青春、影像配乐
- 乐器：reverb guitar, soft synth pads, airy vocals
- 关键词：dreamy, hazy, ethereal, soft vocal, shimmering texture

### 3.1.10 Hyperpop / 超流行

- BPM：130–170
- 适合：年轻、二次元、潮流、实验短视频
- 声音：glitchy synths, pitched vocals, hard electronic drums
- 关键词：glitchy, exaggerated, high-energy, futuristic, maximalist

### 3.1.11 K-pop / J-pop / C-pop Idol Style

- BPM：100–140
- 适合：偶像感、舞台、活力短视频
- 人声：group vocals, polished harmonies
- 关键词：idol pop, polished group vocals, dance break, bright hook, energetic choreography feel

---

## 3.2 Folk / 民谣类

### 3.2.1 Folk / 民谣

- BPM：70–105
- 适合：人生故事、故乡、远方、青春
- 乐器：acoustic guitar, harmonica, light percussion
- 关键词：storytelling, acoustic, sincere, warm vocal, organic

### 3.2.2 Folk-pop / 民谣流行

- BPM：80–110
- 适合：个人故事、毕业、旅行、朋友圈
- 编曲：民谣底色 + 流行副歌
- 关键词：acoustic folk-pop, warm vocal, melodic chorus, intimate

### 3.2.3 Indie Folk / 独立民谣

- BPM：70–105
- 适合：文艺、独立影像、情绪表达
- 关键词：indie folk, intimate, raw, organic texture, minimal arrangement

### 3.2.4 Campus Folk / 校园民谣

- BPM：80–110
- 适合：毕业、青春、同学、校园回忆
- 关键词：campus folk, acoustic guitar, youthful vocal, nostalgic, simple melody

### 3.2.5 Singer-songwriter / 唱作人风格

- BPM：65–100
- 适合：人生表达、亲密叙事、自白
- 乐器：piano or guitar, minimal band
- 关键词：singer-songwriter, introspective lyrics, intimate vocal, minimal arrangement

### 3.2.6 Folk-rock / 民谣摇滚

- BPM：90–125
- 适合：叙事、时代感、励志
- 关键词：folk-rock, guitar-driven, storytelling, warm harmonies, steady drums

### 3.2.7 Country Folk / 乡村民谣

- BPM：75–115
- 适合：家庭、故乡、公路、普通人故事
- 乐器：acoustic guitar, banjo, pedal steel
- 关键词：country folk, Americana roots, heartfelt storytelling

---

## 3.3 Rock & Metal / 摇滚与金属类

### 3.3.1 Soft Rock / 软摇滚

- BPM：80–115
- 适合：情感、人生、怀旧
- 关键词：soft rock, warm guitars, smooth drums, emotional vocal

### 3.3.2 Classic Rock / 经典摇滚

- BPM：100–140
- 适合：复古、热血、公路感
- 关键词：classic rock, electric guitar riffs, steady drums, vintage tone

### 3.3.3 Hard Rock / 硬摇滚

- BPM：110–155
- 适合：力量、热血、反抗
- 乐器：heavy guitar riffs, loud drums, bass
- 人声：raspy male vocal, powerful vocal
- 关键词：hard rock, heavy riffs, powerful drums, raw energy

### 3.3.4 Arena Rock / 竞技场摇滚

- BPM：95–135
- 适合：体育、活动开场、团队、品牌
- 关键词：arena rock, soaring chorus, big drums, crowd-ready anthem

### 3.3.5 Stadium Anthem / 体育场主题歌

- BPM：95–130
- 适合：世界杯、体育、团队、赛事
- 关键词：stadium anthem, group vocals, chant chorus, powerful drums, uplifting energy

### 3.3.6 Alternative Rock / 另类摇滚

- BPM：90–140
- 适合：青年、城市、情绪、独立表达
- 关键词：alternative rock, layered guitars, emotional vocal, modern rock texture

### 3.3.7 Indie Rock / 独立摇滚

- BPM：100–145
- 适合：青年、城市、校园、文艺
- 关键词：indie rock, jangly guitars, raw drums, casual vocal, urban energy

### 3.3.8 Britpop / 英伦摇滚

- BPM：95–135
- 适合：青春、怀旧、城市、足球文化
- 关键词：Britpop, guitar-driven, anthemic chorus, nostalgic 1990s swagger

### 3.3.9 Grunge Rock / 垃圾摇滚

- BPM：90–140
- 适合：压抑、反叛、青春痛感
- 声音：distorted guitar, raw drums, gritty vocal
- 关键词：grunge rock, distorted guitars, angst, raw emotional energy

### 3.3.10 Punk Rock / 朋克摇滚

- BPM：150–190
- 适合：反叛、速度、青春、态度
- 关键词：punk rock, fast tempo, raw guitars, shouty vocals, rebellious

### 3.3.11 Pop-punk / 流行朋克

- BPM：140–180
- 适合：校园、青春、热血、短视频
- 关键词：pop-punk, energetic guitars, catchy chorus, youthful vocals

### 3.3.12 Emo Rock / 情绪摇滚

- BPM：90–150
- 适合：青春伤感、情绪爆发、个人叙事
- 关键词：emo rock, emotional vocals, layered guitars, dramatic chorus

### 3.3.13 Post-punk / 后朋克

- BPM：110–160
- 适合：冷感、城市、复古、暗色影像
- 声音：angular guitars, driving bass, dry drums
- 关键词：post-punk, moody bassline, cold atmosphere, angular guitar

### 3.3.14 New Wave / 新浪潮

- BPM：100–140
- 适合：80s 复古、时尚、都市
- 关键词：new wave, stylish synths, clean guitars, retro pop-rock energy

### 3.3.15 Psychedelic Rock / 迷幻摇滚

- BPM：70–130
- 适合：梦境、实验、复古、长段落
- 关键词：psychedelic rock, fuzz guitar, swirling organ, hypnotic, dreamy

### 3.3.16 Progressive Rock / 前卫摇滚

- BPM：自由 / 80–140
- 适合：复杂叙事、史诗、概念作品
- 关键词：progressive rock, complex structure, dramatic shifts, art-rock atmosphere

### 3.3.17 Art Rock / 艺术摇滚

- BPM：70–130
- 适合：高级、实验、概念化表达
- 关键词：art rock, experimental texture, poetic lyrics, bold arrangement

### 3.3.18 Blues Rock / 蓝调摇滚

- BPM：80–130
- 适合：公路、沧桑、复古、人生
- 关键词：blues rock, gritty guitar solo, shuffle groove, soulful vocal

### 3.3.19 Southern Rock / 南方摇滚

- BPM：90–140
- 适合：公路、美国南方、粗粝故事
- 关键词：southern rock, slide guitar, bluesy riffs, rural grit

### 3.3.20 Garage Rock / 车库摇滚

- BPM：120–170
- 适合：粗糙、年轻、复古、现场感
- 关键词：garage rock, raw guitars, lo-fi recording, energetic drums

### 3.3.21 Shoegaze Rock / 盯鞋摇滚

- BPM：70–120
- 适合：梦幻、朦胧、情绪墙
- 声音：reverb guitars, distortion wash, airy vocal
- 关键词：shoegaze, wall of sound, hazy guitars, ethereal vocal

### 3.3.22 Post-rock / 后摇

- 是否适合纯器乐：非常适合
- BPM：60–120
- 适合：人生叙事、纪录片、情绪递进、体育慢镜头
- 关键词：post-rock, clean delay guitars, emotional build-up, cinematic drums, instrumental climax

### 3.3.23 Math Rock / 数学摇滚

- 是否适合纯器乐：非常适合
- BPM：90–150
- 适合：年轻、清爽、复杂律动、城市感
- 关键词：math rock, clean guitar tapping, odd rhythms, intricate, bright

### 3.3.24 Industrial Rock / 工业摇滚

- BPM：90–150
- 适合：暗黑、机械、反乌托邦、科技压力
- 关键词：industrial rock, distorted drums, dark synths, aggressive guitars, mechanical texture

### 3.3.25 Rap-rock / 说唱摇滚

- BPM：90–130
- 适合：运动、热血、态度、年轻品牌
- 关键词：rap-rock, heavy guitars, rap verses, shouted chorus, hybrid beats

### 3.3.26 Nu Metal / 新金属

- BPM：90–130
- 适合：愤怒、压抑、运动、高冲击
- 声音：down-tuned guitars, rap vocals, electronic elements
- 关键词：nu metal, down-tuned riffs, hybrid rap vocals, aggressive drums

### 3.3.27 Heavy Metal / 重金属

- BPM：100–160
- 适合：力量、战斗、英雄感
- 人声：powerful male vocal, gritty vocal
- 关键词：heavy metal, heavy riffs, powerful drums, dramatic energy

### 3.3.28 Thrash Metal / 激流金属

- BPM：150–220
- 适合：极高能量、速度、攻击性
- 关键词：thrash metal, fast palm-muted riffs, aggressive drums, intense energy

### 3.3.29 Power Metal / 力量金属

- BPM：130–190
- 适合：史诗、英雄、游戏、奇幻、热血
- 关键词：power metal, soaring vocals, fast guitars, epic chorus, heroic atmosphere

### 3.3.30 Glam Metal / 华丽金属

- BPM：100–150
- 适合：80s、舞台感、夸张、派对
- 关键词：glam metal, flashy guitars, big chorus, 1980s arena energy

### 3.3.31 Progressive Metal / 前卫金属

- BPM：复杂 / 90–180
- 适合：概念、复杂结构、史诗
- 关键词：progressive metal, complex rhythms, heavy riffs, cinematic structure

### 3.3.32 Metalcore / 金属核

- BPM：120–180
- 适合：爆发、极端情绪、现代重型
- 关键词：metalcore, breakdowns, screamed verses, melodic chorus, heavy drums

### 3.3.33 Doom Metal / 厄运金属

- BPM：50–90
- 适合：沉重、黑暗、压迫、末日感
- 关键词：doom metal, slow heavy riffs, dark atmosphere, massive low-end

### 3.3.34 Post-metal / 后金属

- BPM：60–120
- 适合：暗色电影感、史诗递进、器乐重型
- 关键词：post-metal, atmospheric heavy guitars, slow build, cinematic heaviness

---

## 3.4 R&B / Soul 类

### 3.4.1 R&B

- BPM：65–100
- 适合：爱情、夜晚、都市、成熟情绪
- 关键词：smooth R&B, soulful vocal, warm bass, soft groove

### 3.4.2 Contemporary R&B / 当代 R&B

- BPM：65–105
- 声音：minimal beats, lush vocals, modern production
- 关键词：contemporary R&B, intimate vocal, polished beat, late-night mood

### 3.4.3 Pop-R&B

- BPM：80–115
- 适合：大众流行、爱情、短视频
- 关键词：pop-R&B, smooth groove, catchy chorus, polished vocal

### 3.4.4 Neo-soul

- BPM：70–100
- 适合：高级、慵懒、成熟、都市夜晚
- 关键词：neo-soul, jazzy chords, warm bass, soulful vocal, organic groove

### 3.4.5 Quiet Storm

- BPM：60–85
- 适合：夜晚、浪漫、低声、私密感
- 关键词：quiet storm, slow R&B groove, intimate vocal, soft electric piano

### 3.4.6 New Jack Swing

- BPM：100–115
- 适合：复古、律动、活力、90s 感
- 关键词：new jack swing, rhythmic vocals, funk-infused beats, 1990s groove

### 3.4.7 Soul

- BPM：70–115
- 关键词：soul, gospel influence, emotional delivery, rich vocal, warm groove

### 3.4.8 Motown Soul

- BPM：90–125
- 适合：复古、明亮、合唱、60s 感
- 关键词：Motown soul, polished harmonies, upbeat rhythm, classic elegance

### 3.4.9 Funk-soul

- BPM：95–125
- 关键词：funk-soul, horn stabs, rhythmic groove, dance-driven, soulful vocal

### 3.4.10 Alternative R&B

- BPM：60–100
- 适合：暗色、实验、都市、年轻高级感
- 关键词：alternative R&B, atmospheric synths, minimal beat, moody vocal

---

## 3.5 Hip-hop / Rap 类

### 3.5.1 Hip-hop

- BPM：75–105
- 关键词：hip-hop beat, deep bass, rhythmic flow, urban storytelling

### 3.5.2 Boom Bap

- BPM：80–95
- 声音：dusty drums, chopped samples, head-nod groove
- 关键词：boom bap, 90s East Coast feel, gritty drums, sample-based

### 3.5.3 Trap

- BPM：130–150 或 half-time 65–75
- 声音：808 bass, hi-hats, sparse melody
- 关键词：trap beat, 808 bass, rapid hi-hats, dark synths

### 3.5.4 Trap Pop

- BPM：130–150 或 half-time
- 适合：短视频、潮流、年轻流行
- 关键词：trap pop, melodic vocal, 808 drums, catchy hook

### 3.5.5 Drill

- BPM：135–150
- 适合：冷感、紧张、街头、暗黑
- 关键词：drill beat, sliding 808, sparse dark melody, tense rhythm

### 3.5.6 G-Funk

- BPM：85–100
- 声音：funk bass, whistle synth lead, laid-back drums
- 关键词：G-Funk, West Coast groove, smooth synth lead, relaxed flow

### 3.5.7 Jazz Rap

- BPM：75–100
- 适合：高级、知识感、城市、轻松
- 关键词：jazz rap, jazzy samples, smooth flow, mellow bass

### 3.5.8 Lo-fi Hip-hop

- BPM：65–90
- 适合：学习、陪伴、夜晚、放松
- 关键词：lo-fi hip-hop, dusty drums, warm keys, vinyl crackle, loopable

### 3.5.9 Conscious Rap

- BPM：75–105
- 适合：社会议题、个人表达、深度文本
- 关键词：conscious rap, storytelling lyrics, thoughtful flow, soulful beat

### 3.5.10 Rap-rock

- 见 Rock & Metal

---

## 3.6 Electronic Song Styles / 电子歌曲类

### 3.6.1 Electronic Pop

- BPM：100–130
- 适合：科技、时尚、品牌、年轻
- 关键词：electronic pop, crisp beat, synth-driven, clean vocal

### 3.6.2 House Pop

- BPM：120–128
- 适合：轻舞曲、活动、品牌、短视频
- 关键词：house pop, four-on-the-floor beat, bright piano chords, catchy vocal

### 3.6.3 Future Bass Pop

- BPM：130–160
- 适合：明亮、年轻、短视频、情绪提升
- 关键词：future bass pop, bright synth drops, emotional vocal chops, uplifting chorus

### 3.6.4 EDM Pop

- BPM：120–140
- 适合：节日、活动、派对、运动
- 关键词：EDM pop, festival energy, big drop, powerful hook

### 3.6.5 Synthwave Pop

- BPM：80–110
- 适合：80s 复古、霓虹、科技怀旧
- 关键词：synthwave pop, retro synths, gated drums, neon atmosphere

### 3.6.6 Dark Synthpop

- BPM：80–120
- 适合：夜晚、暗色、冷感、科技
- 关键词：dark synthpop, moody male vocal, industrial textures, electronic depth

### 3.6.7 Electropop Ballad

- BPM：70–100
- 适合：未来感情歌、冷暖结合
- 关键词：electropop ballad, emotional vocal, soft synth pads, electronic drums

---

## 3.7 Dance / Disco / Funk 类

### 3.7.1 Funk

- BPM：95–125
- 关键词：funk groove, slap bass, syncopated guitar, horn stabs

### 3.7.2 Funk-pop

- BPM：100–125
- 关键词：funk-pop, tight bassline, catchy vocal, upbeat rhythm

### 3.7.3 Disco

- BPM：105–130
- 关键词：disco, four-on-the-floor, string stabs, funky bass, dance floor energy

### 3.7.4 Disco-funk

- BPM：105–125
- 关键词：disco-funk, brass hits, party groove, vibrant rhythm

### 3.7.5 Nu-disco

- BPM：105–125
- 关键词：nu-disco, modern disco groove, glossy synths, stylish bassline

### 3.7.6 Euro-pop

- BPM：110–130
- 关键词：Euro-pop, lush harmonies, bright synths, polished playful sound

---

## 3.8 Jazz / Vocal / Lounge 类

### 3.8.1 Jazz Pop

- BPM：70–120
- 适合：高级感、城市、咖啡馆、夜晚
- 关键词：jazz pop, smooth chords, elegant vocal, warm atmosphere

### 3.8.2 Vocal Jazz

- BPM：60–120
- 关键词：vocal jazz, expressive vocal, piano trio, intimate lounge

### 3.8.3 Lounge Pop

- BPM：70–110
- 关键词：lounge pop, relaxed mood, light jazz, classy atmosphere

### 3.8.4 Crooner Style

- BPM：60–110
- 关键词：crooner vocal style, orchestral swing, romantic classy mood

### 3.8.5 Swing / Big Band

- BPM：120–180
- 关键词：big band swing, brass section, walking bass, lively rhythm

### 3.8.6 Smooth Jazz

- BPM：70–110
- 关键词：smooth jazz, saxophone melody, soft drums, elegant background

### 3.8.7 Jazz Fusion

- BPM：90–140
- 关键词：jazz fusion, complex chords, electric piano, funk bass, instrumental solos

### 3.8.8 Acid Jazz / Nu Jazz

- BPM：90–125
- 关键词：acid jazz, nu jazz, funky groove, electronic textures, stylish urban feel

---

## 3.9 Country / Americana 类

### 3.9.1 Country

- BPM：75–125
- 关键词：country, acoustic guitar, heartfelt storytelling, twangy vocal

### 3.9.2 Country Ballad

- BPM：65–95
- 关键词：country ballad, warm acoustic guitar, heartbreak, intimate vocal

### 3.9.3 Country-pop

- BPM：85–120
- 关键词：country-pop, polished chorus, acoustic layers, heartfelt vocal

### 3.9.4 Americana

- BPM：70–120
- 关键词：Americana, rootsy guitars, organic drums, storytelling lyrics

### 3.9.5 Heartland Rock

- BPM：90–130
- 关键词：heartland rock, working-class storytelling, gravel vocal, steady drums

### 3.9.6 Bluegrass

- BPM：110–180
- 关键词：bluegrass, banjo, fiddle, mandolin, fast acoustic picking

---

## 3.10 Latin / Reggae / World 类

### 3.10.1 Latin Pop

- BPM：95–125
- 适合：夏日、世界杯、派对、国际化
- 关键词：Latin pop, tropical rhythm, warm guitar, danceable groove

### 3.10.2 Reggaeton

- BPM：85–105
- 关键词：reggaeton rhythm, dembow beat, latin percussion, danceable

### 3.10.3 Bossa Nova

- BPM：90–130
- 关键词：bossa nova, soft nylon guitar, breezy rhythm, relaxed summer mood

### 3.10.4 Samba Pop

- BPM：100–140
- 关键词：samba pop, Brazilian percussion, upbeat rhythm, festive energy

### 3.10.5 Salsa Pop

- BPM：150–220
- 关键词：salsa pop, brass section, latin percussion, energetic dance rhythm

### 3.10.6 Afrobeat

- BPM：95–120
- 关键词：Afrobeat, polyrhythmic percussion, warm bass, sunny groove

### 3.10.7 Reggae

- BPM：70–95
- 关键词：reggae, offbeat guitar, laid-back groove, warm bass

### 3.10.8 Dancehall

- BPM：90–110
- 关键词：dancehall, Caribbean rhythm, energetic vocal, bass-heavy beat

### 3.10.9 World Fusion

- BPM：自由 / 80–130
- 关键词：world fusion, global percussion, hybrid instruments, multicultural texture

---

## 3.11 Chinese / 东方 / 国风类

### 3.11.1 Chinese Traditional Pop / 国风流行

- BPM：70–115
- 乐器：guzheng, pipa, erhu, dizi, Chinese percussion
- 关键词：Chinese traditional pop, poetic lyrics, oriental atmosphere, modern pop arrangement

### 3.11.2 古风 Ballad

- BPM：60–95
- 适合：古风、情感、影视、文旅
- 关键词：Chinese ancient-style ballad, guzheng, dizi, poetic vocal, elegant melody

### 3.11.3 Modern Chinese Folk-pop / 新国风

- BPM：75–115
- 关键词：modern Chinese folk-pop, traditional instruments with modern drums, cinematic strings

### 3.11.4 Chinese R&B with Traditional Instruments / 中国风 R&B

- BPM：65–100
- 关键词：Chinese R&B, guzheng motifs, smooth groove, poetic vocal

### 3.11.5 Chinese Opera-inspired Pop / 戏腔融合

- BPM：70–120
- 关键词：Chinese opera-inspired vocal, modern pop arrangement, dramatic oriental mood

### 3.11.6 Jiangnan Folk-inspired Pop / 江南民谣

- BPM：70–105
- 适合：江南、水乡、文旅、温柔城市
- 关键词：Jiangnan folk-inspired pop, soft dizi, acoustic guitar, gentle female vocal

### 3.11.7 Guochao Electronic / 国潮电子

- BPM：95–130
- 适合：国潮品牌、城市宣传、年轻感
- 关键词：Chinese electronic pop, traditional motifs, modern synths, punchy drums

---

## 3.12 Cinematic / Stage & Screen 类

### 3.12.1 Cinematic Pop

- BPM：70–120
- 适合：公众号视频、品牌、人生叙事
- 关键词：cinematic pop, emotional piano, strings build-up, wide soundstage

### 3.12.2 Orchestral Pop

- BPM：65–115
- 关键词：orchestral pop, lush strings, emotional vocal, dramatic chorus

### 3.12.3 Trailer Music

- BPM：80–140
- 适合：预告片、体育、品牌大片
- 关键词：trailer music, epic drums, risers, cinematic brass, dramatic climax

### 3.12.4 Emotional Score

- BPM：60–100
- 关键词：emotional score, soft piano, strings, subtle percussion, heartfelt mood

### 3.12.5 Corporate Cinematic Anthem

- BPM：90–125
- 适合：企业宣传、发布会、品牌片
- 关键词：corporate cinematic anthem, inspiring piano, uplifting strings, polished production

### 3.12.6 Sports Cinematic Anthem

- BPM：95–130
- 关键词：sports cinematic anthem, big drums, choir, brass, heroic build-up

---

## 3.13 Children’s / Educational 类

### 3.13.1 Children’s Song

- BPM：90–130
- 关键词：children’s song, bright melody, simple lyrics, playful rhythm

### 3.13.2 Educational Song

- BPM：90–125
- 关键词：educational song, easy-to-remember chorus, clear vocal, simple structure

### 3.13.3 Cartoon Theme Song

- BPM：110–150
- 关键词：cartoon theme song, playful instruments, energetic vocal, memorable hook

### 3.13.4 Children’s Choir

- BPM：80–125
- 关键词：children’s choir, bright harmonies, warm arrangement, family-friendly

---

# 4. Modern Instrumental Genre Library / 现代流行器乐曲风库

> 说明：这里的“纯器乐”不是古典交响乐，而是现代流行语境里的 instrumental music：短视频 BGM、品牌背景音乐、Lo-fi 学习音乐、Post-rock 情绪器乐、Synthwave 复古器乐、Instrumental hip-hop beat、Corporate background music 等。

---

## 4.1 Lo-fi / Chill / Study Instrumental

### 4.1.1 Lo-fi Hip-hop Instrumental

- BPM：65–90
- 用途：学习、工作、夜晚、陪伴、直播背景
- 主乐器：soft piano, mellow keys, dusty drums, warm bass
- 质感：vinyl crackle, tape saturation, bedroom feel
- 关键词：instrumental only, no vocals, lo-fi hip-hop beat, cozy, warm, loopable

示例：

```text
Instrumental only, no vocals. Warm lo-fi hip-hop beat at 78 BPM, dusty drums, mellow piano chords, soft bass, subtle vinyl crackle, cozy late-night study atmosphere, loop-friendly structure with gentle variations.
```

### 4.1.2 Chillhop Instrumental

- BPM：75–95
- 用途：咖啡馆、Vlog、轻松工作
- 关键词：chillhop instrumental, jazzy piano, soft drums, relaxed groove

### 4.1.3 Jazz-hop Instrumental

- BPM：75–95
- 用途：高级学习、城市夜晚、播客背景
- 关键词：jazz-hop instrumental, jazzy chords, upright bass, boom bap drums

### 4.1.4 Downtempo Instrumental

- BPM：70–100
- 用途：放松、影像、夜晚
- 关键词：downtempo instrumental, soft beats, atmospheric pads, relaxed pace

### 4.1.5 Trip-hop Instrumental

- BPM：65–95
- 用途：暗色都市、悬疑、电影感
- 关键词：trip-hop instrumental, moody bass, dusty drums, cinematic darkness

### 4.1.6 Ambient Pop Instrumental

- BPM：60–90
- 用途：治愈、情绪、空间感
- 关键词：ambient pop instrumental, soft piano, airy pads, gentle pulse, emotional atmosphere

---

## 4.2 Urban Beat / Instrumental Hip-hop

### 4.2.1 Instrumental Hip-hop Beat

- BPM：75–105
- 用途：城市短视频、潮流、播客、街头感
- 关键词：instrumental hip-hop beat, deep bass, rhythmic drums, urban texture

### 4.2.2 Boom Bap Instrumental

- BPM：80–95
- 关键词：boom bap instrumental, dusty drums, chopped samples, 90s head-nod groove

### 4.2.3 Trap Instrumental

- BPM：130–150 或 half-time
- 用途：运动、潮流、科技、短视频
- 关键词：trap instrumental, 808 bass, rapid hi-hats, dark synth melody, no vocals

### 4.2.4 Drill Instrumental

- BPM：135–150
- 关键词：drill instrumental, sliding 808, sparse melody, dark tense atmosphere

### 4.2.5 G-Funk Instrumental

- BPM：85–100
- 用途：阳光、复古、轻松、城市
- 关键词：G-Funk instrumental, smooth synth lead, deep bass, laid-back West Coast groove

### 4.2.6 Future Beats

- BPM：90–115
- 用途：潮流、创意、科技、短视频
- 关键词：future beats, chopped vocal textures, bouncy drums, colorful synth chords

---

## 4.3 Electronic Instrumental

### 4.3.1 Synthwave Instrumental

- BPM：80–110
- 用途：科技、复古未来、夜景、游戏
- 关键词：synthwave instrumental, analog synths, gated drums, neon retro-futuristic atmosphere

### 4.3.2 Chillwave Instrumental

- BPM：75–100
- 用途：夏天、怀旧、Vlog、梦幻
- 关键词：chillwave instrumental, washed synths, soft drums, hazy nostalgic mood

### 4.3.3 Future Bass Instrumental

- BPM：130–160
- 用途：年轻、短视频、积极情绪
- 关键词：future bass instrumental, bright synth drops, sidechain chords, uplifting energy

### 4.3.4 House Instrumental

- BPM：120–128
- 用途：活动、时尚、轻舞曲背景
- 关键词：house instrumental, four-on-the-floor kick, clean bassline, danceable groove

### 4.3.5 Techno Instrumental

- BPM：124–140
- 用途：科技、冷感、潮流、夜店
- 关键词：techno instrumental, driving kick, arpeggiated synth, hypnotic minimal groove

### 4.3.6 Ambient Electronic

- BPM：自由 / 60–90
- 用途：冥想、空间、科技展厅、背景
- 关键词：ambient electronic, atmospheric pads, slow evolving textures, minimal rhythm

### 4.3.7 Minimal Electronic

- BPM：90–125
- 用途：科技产品、高级品牌、发布会
- 关键词：minimal electronic instrumental, clean pulses, sparse synths, premium futuristic feel

### 4.3.8 IDM-inspired Instrumental

- BPM：90–140
- 用途：实验、科技、创意影像
- 关键词：IDM-inspired instrumental, glitch drums, detailed synth textures, complex rhythm

### 4.3.9 Dubstep Instrumental

- BPM：140 或 half-time 70
- 用途：游戏、动作、强冲击短视频
- 关键词：dubstep instrumental, heavy bass wobble, half-time drums, aggressive drop

### 4.3.10 Drum and Bass Instrumental

- BPM：170–180
- 用途：高速运动、游戏、剪辑
- 关键词：drum and bass instrumental, fast breakbeats, deep bass, high-energy motion

---

## 4.4 Guitar / Band Instrumental

### 4.4.1 Post-rock Instrumental

- BPM：60–120
- 用途：人生叙事、纪录片、体育慢镜头、情绪递进
- 关键词：post-rock instrumental, clean delay guitars, slow build, cinematic climax, no vocals

### 4.4.2 Math Rock Instrumental

- BPM：90–150
- 用途：年轻、清爽、复杂节奏、城市
- 关键词：math rock instrumental, clean guitar tapping, odd rhythms, bright energetic texture

### 4.4.3 Indie Rock Instrumental

- BPM：100–140
- 用途：Vlog、校园、城市、轻运动
- 关键词：indie rock instrumental, jangly guitars, live drums, casual upbeat energy

### 4.4.4 Surf Rock Instrumental

- BPM：120–160
- 用途：海边、复古、夏天、运动
- 关键词：surf rock instrumental, reverb guitar, driving drums, sunny beach vibe

### 4.4.5 Funk Rock Instrumental

- BPM：95–125
- 用途：活力、品牌、运动、时尚
- 关键词：funk rock instrumental, slap bass, tight drums, groovy guitar riffs

### 4.4.6 Acoustic Guitar Instrumental

- BPM：70–110
- 用途：旅行、生活方式、温暖、治愈
- 关键词：acoustic guitar instrumental, warm fingerpicking, light percussion, organic travel mood

### 4.4.7 Piano Pop Instrumental

- BPM：65–105
- 用途：情绪短片、个人故事、温暖背景
- 关键词：piano pop instrumental, emotional piano motif, soft strings, gentle drums

---

## 4.5 Lifestyle / Commercial Instrumental

### 4.5.1 Corporate Pop Instrumental

- BPM：100–125
- 用途：企业宣传、产品视频、品牌片
- 乐器：piano, guitar, soft synth, claps
- 关键词：corporate pop instrumental, uplifting, clean, optimistic, polished

### 4.5.2 Uplifting Corporate Instrumental

- BPM：105–130
- 用途：发布会、企业年会、产品展示
- 关键词：uplifting corporate instrumental, inspiring piano, steady drums, positive energy

### 4.5.3 Lifestyle Vlog Music

- BPM：90–120
- 用途：Vlog、旅行、生活方式
- 关键词：lifestyle vlog music, sunny guitar, light beat, friendly, casual

### 4.5.4 Fashion Groove Instrumental

- BPM：100–125
- 用途：时尚、品牌、走秀、潮流短视频
- 关键词：fashion groove instrumental, stylish bassline, minimal drums, confident feel

### 4.5.5 Tech Product Background

- BPM：90–125
- 用途：科技产品、App 展示、发布会
- 关键词：tech product background, minimal synth, pulse bass, clean futuristic texture

### 4.5.6 Podcast Intro Music

- BPM：90–120
- 用途：播客、节目片头
- 关键词：podcast intro music, short memorable motif, clean beat, branded sound

### 4.5.7 Logo Sting

- 时长：5–10 秒
- 用途：品牌片头、频道包装
- 关键词：short logo sting, clean synth hit, memorable brand cue, polished ending

---

## 4.6 Cinematic / Emotional Instrumental

### 4.6.1 Cinematic Pop Instrumental

- BPM：70–120
- 用途：公众号视频、人生叙事、品牌片
- 关键词：cinematic pop instrumental, emotional piano, strings build-up, polished drums

### 4.6.2 Emotional Piano Instrumental

- BPM：60–90
- 用途：亲情、回忆、温暖、感人短片
- 关键词：emotional piano instrumental, gentle melody, soft strings, heartfelt atmosphere

### 4.6.3 Documentary Background Score

- BPM：60–110
- 用途：纪录片、人物故事、城市宣传
- 关键词：documentary background score, subtle piano, ambient texture, emotional realism

### 4.6.4 Inspirational Instrumental

- BPM：90–125
- 用途：企业、教育、成长、演讲
- 关键词：inspirational instrumental, uplifting piano, warm strings, steady build

### 4.6.5 Epic Hybrid Instrumental

- BPM：90–140
- 用途：预告片、游戏、体育、高燃视频
- 关键词：epic hybrid instrumental, orchestral drums, synth bass, brass, cinematic climax

---

## 4.7 Sports / Action Instrumental

### 4.7.1 Sports Highlight Instrumental

- BPM：110–145
- 用途：体育剪辑、比赛集锦、球队宣传
- 关键词：sports highlight instrumental, powerful drums, electric guitars, rising energy

### 4.7.2 Workout Electronic Instrumental

- BPM：125–150
- 用途：健身、跑步、运动短视频
- 关键词：workout electronic instrumental, driving beat, aggressive synth bass, high energy

### 4.7.3 Stadium Percussion Instrumental

- BPM：95–130
- 用途：赛事开场、体育宣传
- 关键词：stadium percussion instrumental, big drums, crowd claps, chant-like rhythm, no vocals

### 4.7.4 Action Trailer Instrumental

- BPM：100–150
- 用途：动作剪辑、预告片、游戏
- 关键词：action trailer instrumental, hybrid drums, risers, impacts, intense build-up

---

## 4.8 Chinese / Oriental Instrumental

### 4.8.1 Chinese Cinematic Instrumental

- BPM：60–110
- 用途：文旅、城市宣传、纪录片
- 乐器：guzheng, erhu, dizi, cinematic strings
- 关键词：Chinese cinematic instrumental, oriental atmosphere, guzheng motif, emotional strings

### 4.8.2 Guofeng Electronic Instrumental

- BPM：90–130
- 用途：国潮品牌、城市宣传、短视频
- 关键词：Guofeng electronic instrumental, Chinese instruments, modern synth bass, punchy drums

### 4.8.3 Jiangnan Ambient Instrumental

- BPM：60–90
- 用途：江南、水乡、文旅、茶馆
- 关键词：Jiangnan ambient instrumental, soft dizi, guzheng, flowing water atmosphere, gentle pads

### 4.8.4 Chinese Percussion Fusion

- BPM：90–140
- 用途：活动开场、国潮、体育、仪式感
- 关键词：Chinese percussion fusion, big drums, modern bass, powerful rhythmic build

---

# 5. Era-based Style Enhancers / 年代风格增强器

年代风格不一定单独作为曲风，而是可以作为 Prompt 增强器：

```text
with a nostalgic 1980s synth-pop texture
with a 1990s Britpop-inspired guitar-driven sound
with a 1970s disco-funk groove
with a 2000s Y2K dance-pop production style
```

## 5.1 1950s

- rockabilly
- early rock & roll
- doo-wop
- crooner jazz pop
- boogie-woogie R&B
- country ballad

关键词：

```text
1950s rockabilly, doo-wop harmonies, crooner vocal, boogie-woogie piano, vintage tape sound
```

## 5.2 1960s

- British pop-rock
- Motown soul
- psychedelic rock
- surf pop
- folk protest
- vocal group harmony

关键词：

```text
1960s Motown soul, surf pop harmonies, psychedelic organ, folk protest acoustic guitar
```

## 5.3 1970s

- hard rock
- glam rock
- soft rock
- funk-disco
- singer-songwriter
- folk-jazz
- soul-funk

关键词：

```text
1970s disco-funk groove, glam rock theatrical energy, soft rock storytelling, soul-funk horns
```

## 5.4 1980s

- synth-pop
- dance-pop
- arena rock
- power ballad
- new wave
- dark synthpop
- glam metal

关键词：

```text
1980s synth-pop texture, gated drums, arena rock chorus, power ballad vocal, new wave synths
```

## 5.5 1990s

- grunge
- Britpop
- alt-rock
- G-Funk
- East Coast rap
- pop-R&B
- industrial rock

关键词：

```text
1990s grunge guitars, Britpop swagger, G-Funk bassline, pop-R&B harmonies, industrial rock texture
```

## 5.6 2000s

- Y2K dance-pop
- pop-R&B
- emo pop-punk
- rap-rock
- nu-metal
- electro-pop

关键词：

```text
2000s Y2K dance-pop, glossy production, emo pop-punk guitars, nu-metal hybrid beats
```

## 5.7 2010s

- EDM pop
- tropical house
- trap pop
- indie pop
- future bass
- bedroom pop
- alt-R&B

关键词：

```text
2010s EDM pop drop, tropical house rhythm, trap pop drums, bedroom pop intimacy
```

## 5.8 2020s

- hyperpop
- TikTok pop
- alt-pop
- lo-fi beats
- phonk
- amapiano-influenced pop
- AI-friendly short hook structure

关键词：

```text
2020s alt-pop production, short-video hook, hyperpop texture, lo-fi beat, punchy viral chorus
```

---

# 6. Scene-to-Genre Recommendation Map / 场景到曲风推荐

| 用户场景 | 推荐带人声曲风 | 推荐纯器乐曲风 |
|---|---|---|
| 朋友圈个人歌曲 | Chinese pop ballad / folk-pop | piano pop instrumental / acoustic guitar instrumental |
| 小红书短视频 | modern pop / electro-pop / dance-pop | future bass instrumental / lifestyle vlog music |
| 品牌宣传 | cinematic pop / electronic pop / corporate anthem | corporate pop instrumental / tech product background |
| 体育赛事 | stadium anthem / arena rock / Latin pop | sports highlight instrumental / epic hybrid instrumental |
| 世界杯主题 | Latin pop / stadium anthem / cinematic pop | Latin groove instrumental / stadium percussion instrumental |
| 城市宣传 | cinematic pop / Chinese traditional pop | Chinese cinematic instrumental / corporate cinematic |
| 文旅宣传 | Chinese traditional pop / world fusion | Jiangnan ambient instrumental / Chinese cinematic instrumental |
| 创业故事 | pop-rock / cinematic pop / folk-pop | inspirational instrumental / cinematic pop instrumental |
| 中年人生 | Chinese pop ballad / soft rock / acoustic folk | emotional piano instrumental / post-rock instrumental |
| 毕业季 | folk-pop / campus folk / pop-rock | acoustic guitar instrumental / piano pop instrumental |
| 婚礼 | romantic pop ballad / R&B / acoustic folk | piano pop instrumental / bossa nova instrumental |
| 儿童课程 | children’s song / cartoon theme song | children’s playful instrumental |
| 科技产品 | synth-pop / electronic pop | minimal electronic / tech product background |
| 高级感视频 | jazz pop / cinematic pop | nu jazz instrumental / minimal electronic |
| 夜晚城市 | smooth R&B / lo-fi pop / synth-pop | trip-hop instrumental / lo-fi hip-hop instrumental |
| 学习工作 | 不推荐人声优先 | lo-fi hip-hop / chillhop / ambient pop instrumental |
| 播客片头 | vocal jingle 可选 | podcast intro music / logo sting |
| 健身运动 | EDM pop / rap-rock / hard rock | workout electronic / sports highlight instrumental |

---

# 7. BPM Reference / BPM 参考

| 用户说法 | 大致 BPM | 适合曲风 |
|---|---:|---|
| 很慢 / 深情慢歌 | 60–75 | 抒情、钢琴、ambient |
| 慢速 | 70–85 | 民谣、R&B、lo-fi |
| 舒缓中速 | 85–100 | 城市流行、轻民谣 |
| 中速 | 100–115 | Pop、品牌歌、校园歌 |
| 明快 | 115–128 | Dance-pop、house pop |
| 快节奏 | 128–145 | EDM、运动、trap pop |
| 很燃 / 高能 | 145–170 | Punk、metal、运动剪辑 |
| 高速电子 | 170–180 | Drum and bass |

---

# 8. Vocal Reference / 人声参考

| 中文描述 | Prompt 标签 | 适合场景 |
|---|---|---|
| 温暖男声 | warm male vocal | 城市、亲情、成长 |
| 成熟男声 | mature emotional male vocal | 中年、故事感 |
| 沙哑男声 | slightly raspy male vocal | 摇滚、人生、沧桑 |
| 清澈男声 | clear young male vocal | 校园、青春 |
| 温柔女声 | soft female vocal | 治愈、爱情 |
| 清澈女声 | clear female vocal | 青春、明亮 |
| 空灵女声 | ethereal female vocal | 梦幻、国风、电影感 |
| 有力量女声 | powerful female vocal | 励志、热血 |
| 少年感人声 | youthful vocal | 校园、短视频 |
| 低沉男声 | deep male vocal | 叙事、孤独 |
| 合唱 | group vocals / choir | 体育、品牌、仪式感 |
| 儿童合唱 | children’s choir | 儿童、教育 |
| 说唱人声 | rap vocal | Hip-hop、态度 |
| 旁白式 | spoken-word vocal | 叙事、短片 |
| 男女对唱 | male and female duet | 爱情、剧情 |

---

# 9. Instrumentation Reference / 乐器与声音元素

## 9.1 常见现代流行乐器

```text
piano
acoustic guitar
electric guitar
bass
drums
strings
synth pads
synth lead
808 bass
brass
choir
hand claps
percussion
ukulele
electric piano
organ
saxophone
```

## 9.2 中国 / 东方元素

```text
guzheng
pipa
erhu
dizi
xiao
Chinese percussion
opera-inspired vocal ornament
pentatonic melody
```

## 9.3 电子 / 质感元素

```text
analog synths
drum machines
sidechain compression
sub bass
arpeggiated synth
glitch percussion
vinyl crackle
tape saturation
ambient pads
riser
impact
```

---

# 10. Prompt Formula / Prompt 公式

## 10.1 带人声歌曲 Style Prompt 公式

```text
Create a [language] [genre] song with a [mood] atmosphere.
Use [vocal style] vocals.
The tempo should be around [BPM] BPM.
The arrangement should include [instruments].
Start with [intro arrangement], then build into [chorus arrangement].
The emotional curve should move from [starting emotion] to [ending emotion].
The chorus should be [catchy / powerful / warm / cinematic / suitable for group singing].
The song is intended for [use case].
Avoid [unwanted elements].
```

## 10.2 纯器乐 Style Prompt 公式

```text
Create an instrumental-only [genre] track for [use case].
No vocals, no lyrics.
Mood: [mood].
Tempo: around [BPM] BPM.
Main instruments: [instruments].
Groove: [groove description].
Texture: [production texture].
Arrangement: [loop-based / gradual build / cinematic progression].
Energy curve: [steady / rising / dynamic].
Make it [loop-friendly / background-friendly / cinematic / high-energy].
Avoid [unwanted elements].
```

## 10.3 Lyrics Box 前置标签公式

```text
[Style: ...]
[Vocal: ...]
[Tempo: ...]
[Arrangement: ...]
[Mood: ...]
[Theme: ...]
[Use Case: ...]
```

## 10.4 纯器乐 Prompt 固定词

```text
instrumental only
no vocals
no lyrics
loop-friendly
background music
subtle variations
clean mix
polished production
seamless ending
```

---

# 11. Safety / Copyright Prompt Rules

Skill 不应直接生成以下表达：

```text
sound exactly like [artist]
copy the melody of [song]
use [artist]'s voice
clone [artist]'s vocal tone
rewrite [existing lyrics] with small changes
```

应改写为抽象风格：

```text
nostalgic 1990s Britpop-inspired guitar sound
cinematic stadium anthem with group vocals
warm acoustic folk-pop storytelling style
1980s synth-pop texture with gated drums
Chinese R&B with poetic lyrics and traditional instrument motifs
```

---

# 12. v0.2 更新摘要

本版相对 v0.1 的主要变化：

1. 将曲风库拆分为：
   - Vocal Song Genre Library
   - Modern Instrumental Genre Library
2. 大幅细化 Rock / Metal，包括 post-rock、math rock、shoegaze、nu metal、power metal、metalcore 等。
3. 细化 Pop、R&B、Hip-hop、Electronic、Jazz、Latin、Chinese / 国风等分类。
4. 新增现代流行器乐库，覆盖 Lo-fi、Chillhop、Instrumental hip-hop、Synthwave、Corporate BGM、Post-rock、Tech Product Background 等。
5. 增加“带人声歌曲 / 纯器乐”的交互路由逻辑。
6. 增加纯器乐 Prompt 字段公式。
7. 增加场景到曲风的推荐映射。
8. 增加年代风格增强器：1950s–2020s。
