# AI 音乐 Prompt Skill：曲风库（Genre Library）v0.1

> 用途：本文件用于交互式 AI 音乐 Prompt Skill。它不是音乐百科全书，而是一个“Prompt 可用”的曲风素材库，用来把用户的模糊表达转译为 Suno / Udio / 类 Suno AI 音乐软件可理解的生成指令。

---

## 0. 设计原则

### 0.1 曲风库不是给用户看的完整菜单
普通用户不一定理解 Britpop、G-Funk、new jack swing、synthwave 等术语。因此交互时只展示少量易懂选项，例如：

- 中文流行
- 民谣
- 摇滚
- 电子
- R&B
- 说唱
- 国风
- 电影感
- 体育主题曲
- 复古
- 爵士
- 拉丁
- 儿童歌

Skill 内部再把这些用户语言转译成更专业的 Prompt 标签。

### 0.2 每个曲风都要服务最终 Prompt
最终 Prompt 一般由以下字段组成：

```text
Genre + Era + Mood + Vocal + Instrumentation + Rhythm/BPM + Production Texture + Use Case
```

例如：

```text
Chinese pop ballad, warm and cinematic, 82 BPM, mature emotional male vocal, piano intro, acoustic guitar, soft drums and strings in the chorus, intimate verse, uplifting final chorus, suitable for short video and personal sharing.
```

### 0.3 避免直接模仿真实歌手
曲风库可以参考某个年代、某类声音、某种编曲传统，但最终 Prompt 应避免：

```text
像某某歌手一样唱
复制某首歌旋律
克隆某位歌手声音
```

应改成：

```text
nostalgic 1980s synth-pop texture
1990s Britpop-inspired guitar-driven sound
cinematic stadium anthem with crowd chant chorus
warm acoustic folk-pop with storytelling lyrics
```

---

## 1. 曲风库数据结构

每个曲风建议使用以下字段：

```text
Genre ID:
中文名：
英文 Prompt 标签：
一级分类：
年代属性：
适合主题：
适合场景：
情绪关键词：
BPM 范围：
人声建议：
常见乐器：
编曲特点：
制作质感：
Prompt 关键词：
示例 Style Prompt：
```

---

## 2. 一级曲风分类

第一版建议采用以下 14 个大类：

1. Pop / 流行
2. Folk / 民谣
3. Rock / 摇滚
4. R&B / Soul
5. Hip-hop / Rap
6. Electronic / 电子
7. Dance / Disco / Funk
8. Jazz / Vocal / Easy Listening
9. Country / Americana
10. Latin / Reggae / World
11. Chinese / 东方 / 国风
12. Cinematic / Stage & Screen
13. Children’s / Educational
14. Era-based / 年代风格

---

## 3. 第一版优先收录曲风清单

第一版不追求穷尽所有音乐类型，优先收录高频、适合 AI 生成、适合中文用户理解与调用的曲风。

```text
Chinese pop
Chinese pop ballad
Mandopop
modern pop
dance-pop
electro-pop
synth-pop
pop-rock
power ballad
folk-pop
acoustic folk
indie folk
classic rock
hard rock
arena rock
indie rock
Britpop
grunge rock
punk rock
emo rock
R&B
smooth R&B
pop-R&B
soul
neo-soul
Motown soul
funk
disco
disco-funk
hip-hop
rap
trap
trap pop
G-Funk
lo-fi hip-hop
EDM
house
techno
ambient
synthwave
jazz pop
vocal jazz
lounge pop
country-pop
Americana
Latin pop
reggaeton
bossa nova
Chinese traditional pop
cinematic pop
epic orchestral
stadium anthem
children’s song
```

---

# 4. 曲风大类与 Prompt 素材

## 4.1 Pop / 流行类

### 用户可见名称

- 中文流行
- 中文流行抒情
- 现代流行
- 电子流行
- 舞曲流行
- 青春流行
- 流行摇滚
- 情绪大歌

### 内部 Prompt 标签

```text
Chinese pop
Mandopop
Chinese pop ballad
modern pop
dance-pop
electro-pop
synth-pop
teen pop
pop-rock
power ballad
vocal pop
```

### 适合主题

- 爱情
- 亲情
- 成长
- 城市生活
- 中年人生
- 毕业
- 个人故事
- 品牌宣传
- 短视频传播

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| 中文流行抒情 | 70–95 |
| 现代流行 | 90–120 |
| Dance-pop | 110–128 |
| Synth-pop | 95–125 |
| Power ballad | 65–90 |
| Pop-rock | 100–140 |

### 人声建议

```text
warm male vocal
soft female vocal
clear young vocal
mature emotional vocal
powerful female vocal
```

### 常见乐器 / 编曲

```text
piano
acoustic guitar
soft drums
bass
strings
synth pads
hand claps
layered backing vocals
```

### Prompt 关键词

```text
catchy melody, radio-friendly, memorable chorus, polished production, emotional vocal, clean arrangement, melodic hook
```

### 示例 Style Prompt

```text
Create a Chinese pop ballad with a warm emotional atmosphere, 82 BPM, mature male vocal, piano intro, acoustic guitar in the verses, soft drums and cinematic strings in the chorus. The song should feel intimate at first and gradually become uplifting, with a memorable chorus suitable for short-video sharing.
```

---

## 4.2 Folk / 民谣类

### 用户可见名称

- 民谣
- 独立民谣
- 校园民谣
- 原声民谣
- 叙事民谣

### 内部 Prompt 标签

```text
folk
folk-pop
acoustic folk
indie folk
campus folk
storytelling folk
country folk
```

### 适合主题

- 青春
- 毕业
- 远方
- 旅行
- 故乡
- 人生故事
- 普通人的生活
- 自我和解

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| acoustic folk | 70–95 |
| folk-pop | 80–110 |
| indie folk | 75–105 |
| campus folk | 85–115 |

### 人声建议

```text
warm male vocal
clear young male vocal
soft female vocal
natural intimate vocal
```

### 常见乐器 / 编曲

```text
acoustic guitar
fingerpicked guitar
piano
light percussion
harmonica
soft strings
```

### Prompt 关键词

```text
acoustic guitar, warm vocal, intimate, storytelling, organic texture, simple arrangement, heartfelt lyrics
```

### 示例 Style Prompt

```text
Create a warm acoustic folk-pop song, 86 BPM, natural intimate vocal, acoustic guitar-driven arrangement, light percussion, simple piano accents, and heartfelt storytelling lyrics. The mood should feel sincere, nostalgic, and quietly hopeful.
```

---

## 4.3 Rock / 摇滚类

### 用户可见名称

- 经典摇滚
- 硬摇滚
- 流行摇滚
- 体育摇滚
- 英伦摇滚
- 独立摇滚
- 朋克摇滚
- 情绪摇滚
- 迷幻摇滚

### 内部 Prompt 标签

```text
classic rock
hard rock
pop-rock
arena rock
indie rock
Britpop
grunge rock
punk rock
emo rock
psychedelic rock
art rock
folk-rock
funk-rock
```

### 适合主题

- 奋斗
- 体育
- 比赛
- 反抗
- 青春
- 时代感
- 创业
- 不服输
- 团队精神

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| classic rock | 100–140 |
| hard rock | 110–150 |
| arena rock | 95–135 |
| punk rock | 150–190 |
| grunge rock | 90–130 |
| Britpop | 95–130 |
| emo rock | 120–160 |

### 人声建议

```text
raspy male vocal
powerful male vocal
raw emotional vocal
anthemic group vocal
female rock vocal
```

### 常见乐器 / 编曲

```text
electric guitar riffs
distorted guitar
power chords
bass
drums
crash cymbals
crowd chant
backing vocals
```

### Prompt 关键词

```text
electric guitar riffs, powerful drums, anthemic chorus, raw energy, driving rhythm, distorted guitars, stadium-ready hook
```

### 示例 Style Prompt

```text
Create an arena rock anthem, 118 BPM, powerful raspy male vocal, electric guitar riffs, driving drums, bass, and a big sing-along chorus. The verses should feel determined and the chorus should explode with stadium energy, suitable for sports highlights or an event opening.
```

---

## 4.4 R&B / Soul 类

### 用户可见名称

- R&B
- 都市 R&B
- Soul
- Neo-soul
- 复古灵魂乐
- 流行 R&B

### 内部 Prompt 标签

```text
R&B
smooth R&B
pop-R&B
soul
neo-soul
Motown soul
funk-soul
new jack swing
```

### 适合主题

- 爱情
- 夜晚
- 都市情绪
- 暧昧
- 成熟关系
- 孤独
- 高级感

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| smooth R&B | 65–95 |
| pop-R&B | 75–105 |
| neo-soul | 70–95 |
| Motown soul | 90–120 |
| new jack swing | 100–115 |

### 人声建议

```text
smooth male vocal
soft female vocal
soulful vocal
sultry female vocal
falsetto male vocal
rich harmony vocals
```

### 常见乐器 / 编曲

```text
electric piano
warm bass
tight drums
snap percussion
soul guitar
strings
backing harmonies
```

### Prompt 关键词

```text
smooth groove, soulful vocal, warm bass, emotional delivery, rich harmonies, late-night mood, polished R&B production
```

### 示例 Style Prompt

```text
Create a smooth pop-R&B song, 88 BPM, soulful male vocal with warm harmonies, electric piano, soft drums, deep bass, and a late-night urban atmosphere. The chorus should be romantic and memorable, with polished modern production.
```

---

## 4.5 Hip-hop / Rap 类

### 用户可见名称

- 说唱
- Hip-hop
- Trap
- 潮流说唱
- Lo-fi 说唱
- 说唱摇滚

### 内部 Prompt 标签

```text
hip-hop
rap
trap
trap pop
boom bap
East Coast rap
West Coast rap
G-Funk
jazz rap
rap-rock
lo-fi hip-hop
```

### 适合主题

- 态度表达
- 城市故事
- 青年文化
- 品牌潮流
- 个人宣言
- 街头感
- 短视频

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| boom bap | 80–100 |
| West Coast rap | 85–105 |
| G-Funk | 85–100 |
| trap | 130–150 或 half-time 65–75 |
| lo-fi hip-hop | 65–90 |
| rap-rock | 95–140 |

### 人声建议

```text
confident rap vocal
laid-back rap vocal
fast rap delivery
spoken-word vocal
melodic rap vocal
autotuned vocal
```

### 常见乐器 / 编曲

```text
808 drums
deep bass
boom bap drums
sampled piano
synth bass
vinyl texture
lo-fi drums
electric guitar for rap-rock
```

### Prompt 关键词

```text
tight beat, deep bass, rhythmic flow, urban storytelling, confident delivery, 808 drums, melodic hook
```

### 示例 Style Prompt

```text
Create a melodic trap-pop track, 140 BPM with a half-time feel, deep 808 bass, crisp trap drums, atmospheric synths, and confident melodic rap vocals. The hook should be catchy and suitable for short video use.
```

---

## 4.6 Electronic / 电子类

### 用户可见名称

- 电子流行
- EDM
- House
- Techno
- 氛围电子
- Synthwave
- 未来感电子

### 内部 Prompt 标签

```text
electronic pop
synth-pop
EDM
house
techno
trance
ambient
chillout
future bass
drum and bass
dubstep
synthwave
vaporwave
```

### 适合主题

- 科技
- 未来
- 品牌
- 活动
- 运动
- 短视频
- 年轻感
- 夜晚城市

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| electronic pop | 95–125 |
| synth-pop | 95–125 |
| EDM / house | 120–130 |
| techno | 124–140 |
| future bass | 130–160 |
| drum and bass | 170–180 |
| ambient | 可不写 BPM |

### 人声建议

```text
clear female vocal
airy vocal
processed vocal
vocoder texture
falsetto male vocal
minimal vocal
```

### 常见乐器 / 编曲

```text
synth pads
synth lead
electronic drums
pulsing bass
sidechain compression
arpeggiator
riser
energetic drop
```

### Prompt 关键词

```text
synth-driven, electronic drums, pulsing bass, atmospheric pads, futuristic texture, energetic drop, glossy production
```

### 示例 Style Prompt

```text
Create a bright electronic pop song, 122 BPM, clear female vocal, pulsing synth bass, electronic drums, shimmering synth pads, and a catchy chorus. The production should feel modern, clean, youthful, and suitable for a technology brand video.
```

---

## 4.7 Dance / Disco / Funk 类

### 用户可见名称

- Disco
- Funk
- 复古舞曲
- 迪斯科放克
- 快乐派对风

### 内部 Prompt 标签

```text
disco
disco-funk
funk
funk-pop
dance-pop
nu-disco
Euro-pop
```

### 适合主题

- 派对
- 快乐
- 品牌活动
- 短视频
- 复古
- 夏天
- 年会
- 活动开场

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| disco | 105–125 |
| disco-funk | 105–125 |
| funk-pop | 95–120 |
| nu-disco | 110–125 |
| dance-pop | 110–128 |

### 人声建议

```text
bright female vocal
playful male vocal
group vocals
falsetto harmonies
energetic vocal
```

### 常见乐器 / 编曲

```text
funky bassline
clean guitar
brass hits
hand claps
four-on-the-floor drums
strings
rhythm guitar
```

### Prompt 关键词

```text
funky bassline, danceable groove, brass hits, hand claps, glossy production, upbeat energy, retro dancefloor
```

### 示例 Style Prompt

```text
Create a 1970s-inspired disco-funk song, 116 BPM, funky bassline, brass hits, hand claps, clean rhythm guitar, and energetic group vocals. The song should feel joyful, danceable, retro, and suitable for a party or brand campaign.
```

---

## 4.8 Jazz / Vocal / Easy Listening 类

### 用户可见名称

- 爵士流行
- 咖啡馆爵士
- Lounge
- 复古人声
- 大乐队 Swing
- 高级感流行

### 内部 Prompt 标签

```text
jazz pop
vocal jazz
lounge pop
big band swing
crooner vocal style
easy listening
swing
smooth jazz
```

### 适合主题

- 高级感
- 城市夜晚
- 咖啡馆
- 浪漫
- 复古
- 品牌质感
- 酒店 / 餐厅 / 生活方式

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| jazz pop | 70–110 |
| lounge pop | 70–100 |
| vocal jazz | 65–110 |
| swing | 120–160 |
| smooth jazz | 70–105 |

### 人声建议

```text
warm crooner vocal
velvet male vocal
soft female jazz vocal
smooth vocal
classy vocal delivery
```

### 常见乐器 / 编曲

```text
piano
upright bass
jazz drums
brass section
saxophone
strings
brush drums
```

### Prompt 关键词

```text
smooth jazz chords, warm crooner vocal, orchestral swing, elegant mood, classy lounge atmosphere, soft brass
```

### 示例 Style Prompt

```text
Create a classy jazz pop song, 92 BPM, warm crooner-style male vocal, piano, upright bass, soft brushed drums, and light brass. The mood should feel elegant, romantic, and suitable for a late-night city lounge.
```

---

## 4.9 Country / Americana 类

### 用户可见名称

- 乡村
- 乡村流行
- 美式公路感
- Americana
- 南方摇滚

### 内部 Prompt 标签

```text
country
country ballad
country-pop
Americana
heartland rock
southern rock
bluegrass
```

### 适合主题

- 人生故事
- 故乡
- 旅行
- 家庭
- 普通人叙事
- 公路感
- 离别

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| country ballad | 70–90 |
| country-pop | 85–115 |
| Americana | 75–110 |
| heartland rock | 95–125 |
| bluegrass | 120–170 |

### 人声建议

```text
warm male vocal
twangy vocal
heartfelt female vocal
gritty storytelling vocal
```

### 常见乐器 / 编曲

```text
acoustic guitar
banjo
fiddle
pedal steel guitar
drums
bass
harmonica
```

### Prompt 关键词

```text
acoustic guitar, twangy vocal, heartfelt storytelling, warm Americana roots, steady rhythm, open-road feeling
```

### 示例 Style Prompt

```text
Create a warm country-pop song, 96 BPM, heartfelt storytelling vocal, acoustic guitar, light drums, pedal steel guitar, and a nostalgic open-road atmosphere. The chorus should feel hopeful and easy to sing along.
```

---

## 4.10 Latin / Reggae / World 类

### 用户可见名称

- 拉丁流行
- Reggaeton
- Bossa Nova
- 雷鬼
- Afrobeat
- 世界音乐融合

### 内部 Prompt 标签

```text
Latin pop
reggaeton
salsa pop
bossa nova
samba
Afrobeat
reggae
dancehall
world fusion
```

### 适合主题

- 夏天
- 旅行
- 世界杯
- 派对
- 海边
- 轻松
- 国际化
- 运动

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| bossa nova | 90–130 |
| reggaeton | 85–105 |
| Latin pop | 95–125 |
| reggae | 70–95 |
| Afrobeat | 95–120 |
| samba | 95–130 |

### 人声建议

```text
warm male vocal
bright female vocal
group vocals
playful vocal
bilingual vocal
```

### 常见乐器 / 编曲

```text
latin percussion
nylon guitar
brass
syncopated drums
congas
shakers
tropical synths
```

### Prompt 关键词

```text
latin percussion, danceable rhythm, tropical mood, warm guitar, syncopated groove, summer energy
```

### 示例 Style Prompt

```text
Create a Latin pop stadium song, 108 BPM, bilingual hook, warm male and female vocals, Latin percussion, brass, tropical guitar, and a danceable rhythm. The chorus should feel joyful, global, and suitable for a sports celebration.
```

---

## 4.11 Chinese / 东方 / 国风类

### 用户可见名称

- 国风流行
- 古风
- 新国风
- 中国风 R&B
- 东方电影感
- 江南民谣
- 国潮品牌歌

### 内部 Prompt 标签

```text
Chinese traditional pop
Chinese ancient-style ballad
modern Chinese folk-pop
Chinese R&B with traditional instruments
cinematic Chinese orchestral pop
Chinese world fusion
Chinese opera-inspired pop
Jiangnan folk-inspired pop
```

### 适合主题

- 文旅
- 城市宣传
- 传统文化
- 节日
- 江南
- 水乡
- 国潮品牌
- 历史故事
- 东方美学

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| 古风抒情 | 65–90 |
| 国风流行 | 75–110 |
| 中国风 R&B | 75–100 |
| 东方电影感 | 60–110 |
| 国潮电子 | 95–125 |

### 人声建议

```text
clear female vocal
ethereal female vocal
warm male vocal
Chinese opera-inspired vocal
soft duet vocal
```

### 常见乐器 / 编曲

```text
guzheng
pipa
erhu
dizi
Chinese percussion
cinematic strings
piano
modern drums
synth pads
```

### Prompt 关键词

```text
guzheng, pipa, erhu, dizi, Chinese percussion, cinematic strings, poetic lyrics, oriental atmosphere, modern pop fusion
```

### 示例 Style Prompt

```text
Create a cinematic Chinese traditional pop song, 82 BPM, clear ethereal female vocal, guzheng, pipa, dizi, piano, cinematic strings, and soft modern drums. The song should feel poetic, elegant, and suitable for cultural tourism or a city image video.
```

---

## 4.12 Cinematic / Stage & Screen 类

### 用户可见名称

- 电影感
- 史诗感
- 纪录片配乐
- 品牌大片
- 体育史诗
- 管弦流行

### 内部 Prompt 标签

```text
cinematic pop
epic orchestral
trailer music
orchestral pop
emotional score
documentary score
cinematic stadium anthem
corporate cinematic anthem
```

### 适合主题

- 品牌宣传
- 体育
- 公众号视频
- 纪录片
- 城市宣传
- 人生叙事
- 企业年会
- 重大事件

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| emotional score | 60–90 |
| cinematic pop | 75–110 |
| epic orchestral | 80–120 |
| trailer music | 90–140 |
| cinematic stadium anthem | 95–130 |

### 人声建议

```text
emotional male vocal
ethereal female vocal
choir
group vocals
minimal vocal
```

### 常见乐器 / 编曲

```text
cinematic strings
orchestral percussion
piano
brass
choir
epic drums
synth pads
wide soundstage
```

### Prompt 关键词

```text
cinematic strings, orchestral build-up, emotional piano, epic drums, wide soundstage, dramatic climax, inspirational mood
```

### 示例 Style Prompt

```text
Create a cinematic pop anthem, 92 BPM, emotional male vocal, piano intro, cinematic strings, orchestral percussion, choir layers in the final chorus, and a wide inspirational soundstage. The song should build from intimate storytelling to a powerful climax.
```

---

## 4.13 Children’s / Educational 类

### 用户可见名称

- 儿童歌
- 亲子歌
- 教育歌
- 动画主题曲
- 儿童合唱

### 内部 Prompt 标签

```text
children’s song
family-friendly children’s pop
educational song
cartoon theme song
children’s choir
lullaby
sing-along song
```

### 适合主题

- 儿童教育
- 课程
- 亲子
- 节日活动
- 幼儿园
- 小学
- 动画
- 课堂记忆

### BPM 参考

| 子风格 | 建议 BPM |
|---|---:|
| lullaby | 50–75 |
| children’s song | 90–130 |
| educational song | 90–120 |
| cartoon theme song | 110–140 |

### 人声建议

```text
children’s choir
bright female vocal
playful male vocal
group sing-along vocal
```

### 常见乐器 / 编曲

```text
ukulele
piano
hand claps
xylophone
light drums
whistle
children’s choir
```

### Prompt 关键词

```text
bright melody, simple lyrics, playful rhythm, children’s choir, ukulele, hand claps, easy to sing along
```

### 示例 Style Prompt

```text
Create a playful children’s educational song, 110 BPM, bright female vocal and children’s choir, ukulele, piano, hand claps, simple drums, and a cheerful sing-along chorus. The lyrics should be simple, repetitive, and easy for children to remember.
```

---

# 5. Era-based / 年代风格增强器

年代风格不一定单独作为曲风，而更适合做“声音质感增强器”。

## 5.1 1950s

### Prompt 方向

```text
rockabilly
doo-wop
early rock & roll
boogie-woogie
crooner vocal
orchestral swing
country ballad
```

### 常见声音特征

```text
male crooner vocals, harmony vocals, sax stabs, piano-driven rhythm, 12-bar rhythm, romantic tone, early rock energy
```

### 可用表达

```text
with a nostalgic 1950s doo-wop harmony texture
with early rock & roll energy and sax stabs
with warm crooner vocals and orchestral swing
```

---

## 5.2 1960s

### Prompt 方向

```text
British pop-rock
Motown soul
psychedelic rock
surf pop
folk protest
folk-rock
bubblegum pop-rock
```

### 常见声音特征

```text
layered vocal harmonies, jangly guitars, organ textures, gospel power, surf-pop brightness, acoustic protest tone
```

### 可用表达

```text
with a 1960s Motown-inspired soul groove
with British pop-rock harmonies and jangly guitars
with psychedelic rock textures and moody organ
```

---

## 5.3 1970s

### Prompt 方向

```text
soft rock
glam rock
funk-disco fusion
disco-pop
singer-songwriter
folk-jazz fusion
country-rock
```

### 常见声音特征

```text
funky bass, horns, falsetto harmonies, acoustic layers, soft rock storytelling, disco sparkle, theatrical vocals
```

### 可用表达

```text
with a 1970s disco-funk groove
with warm 1970s soft rock storytelling
with glam rock theatrical energy and layered harmonies
```

---

## 5.4 1980s

### Prompt 方向

```text
synth-pop
dance-pop
arena rock
power ballad
new wave pop
heartland rock
new jack swing
```

### 常见声音特征

```text
bright synths, gated drums, soaring choruses, echo guitars, polished production, dramatic vocal delivery
```

### 可用表达

```text
with a nostalgic 1980s synth-pop texture
with 1980s arena rock energy and soaring chorus
with polished 1980s power ballad production
```

---

## 5.5 1990s

### Prompt 方向

```text
grunge rock
alt-rock
Britpop
G-Funk
East Coast rap
West Coast rap
pop-R&B
rap-rock
```

### 常见声音特征

```text
distorted guitars, raw emotional vocals, anthemic guitar-driven chorus, deep bass, smooth flow, soulful beats, R&B harmonies
```

### 可用表达

```text
with a 1990s Britpop-inspired guitar-driven sound
with 1990s G-Funk deep bass and laid-back groove
with 1990s pop-R&B harmonies and emotional ballad texture
```

---

## 5.6 2000s / Y2K

### Prompt 方向

```text
Y2K dance-pop
pop-R&B
electro-pop
emo pop-punk
rap-rock
Southern rap
piano-led R&B ballad
```

### 常见声音特征

```text
glossy production, club energy, emotional pop harmonies, fast guitars, hybrid beats, polished R&B groove, autotuned vocal textures
```

### 可用表达

```text
with a glossy 2000s Y2K dance-pop production style
with 2000s pop-R&B groove and smooth vocal harmonies
with 2000s emo pop-punk guitars and anthemic hooks
```

---

# 6. 场景到曲风的推荐映射

| 用户场景 | 推荐曲风 |
|---|---|
| 朋友圈个人歌曲 | Chinese pop ballad / folk-pop / acoustic folk |
| 小红书短视频 | modern pop / electro-pop / lo-fi pop / dance-pop |
| 品牌宣传 | cinematic pop / electronic pop / corporate anthem |
| 体育赛事 | stadium anthem / arena rock / Latin pop / cinematic orchestral |
| 世界杯主题 | Latin pop / stadium anthem / cinematic pop / dance-pop |
| 城市宣传 | cinematic pop / Chinese traditional pop / orchestral pop |
| 文旅宣传 | Chinese traditional pop / world fusion / cinematic Chinese pop |
| 创业故事 | pop-rock / cinematic pop / folk-pop |
| 中年人生 | Chinese pop ballad / acoustic folk / soft rock |
| 毕业季 | folk-pop / campus folk / pop-rock |
| 婚礼 | romantic pop ballad / R&B / acoustic folk |
| 儿童课程 | children’s song / playful pop / children’s choir |
| 科技产品 | synth-pop / electronic pop / future bass |
| 高级感视频 | jazz pop / cinematic pop / ambient pop |
| 夜晚城市 | smooth R&B / lo-fi hip-hop / synth-pop |
| 年会开场 | dance-pop / stadium anthem / cinematic pop |
| 纪录片 | documentary score / cinematic pop / ambient |

---

# 7. 用户不懂曲风时的推荐话术

## 7.1 用户说“不知道什么风格合适”

```text
我建议你可以从这 3 个方向里选：

1. 中文流行抒情：最稳妥，适合大众传播和情感表达。
2. 民谣流行：更真诚，适合个人故事和生活感。
3. 电影感流行：更高级，适合视频、公众号或品牌感表达。
```

## 7.2 用户说“我要世界杯感觉”

```text
这个主题可以考虑 4 个方向：

1. 体育主题曲 / Stadium anthem：适合热血、合唱、赛事感。
2. Latin pop：适合夏天、国际化、节奏感和庆典感。
3. Cinematic orchestral pop：适合史诗、回忆、燃情剪辑。
4. Arena rock：适合球场、呐喊、团队精神。
```

## 7.3 用户说“我要复古”

```text
你想要哪种复古？

1. 70s disco-funk：跳舞、快乐、派对感。
2. 80s synth-pop：霓虹、电子、怀旧。
3. 90s Britpop / grunge：青春、反叛、吉他。
4. 2000s Y2K dance-pop：明亮、潮流、短视频。
```

## 7.4 用户说“我要高级感”

```text
高级感可以有 3 个方向：

1. Jazz pop / lounge pop：城市、咖啡馆、夜晚、精致。
2. Cinematic pop：更像电影片尾曲或品牌大片。
3. Smooth R&B：都市、夜晚、成熟、柔和律动。
```

---

# 8. 曲风选择逻辑

## 8.1 信息不足时

如果用户只提供主题，不提供风格：

```text
先根据主题推荐 3 个曲风方向，不直接生成最终 Prompt。
```

例如：

```text
主题：中年人还在努力生活
推荐：Chinese pop ballad / acoustic folk / cinematic pop
```

## 8.2 信息足够时

如果用户已经提供：

```text
主题 + 场景 + 风格 + 情绪
```

则直接生成最终 Prompt，不继续追问。

## 8.3 用户选择“多风格版本”时

默认生成 3 个版本：

```text
1. 大众流行版
2. 短视频传播版
3. 电影感高级版
```

必要时可以根据主题替换：

- 世界杯：体育主题曲 / 拉丁流行 / 电影史诗
- 品牌：现代电子 / 电影感 / 年轻流行
- 个人故事：流行抒情 / 民谣 / 轻摇滚

---

# 9. Prompt 生成公式

## 9.1 Style Prompt 公式

```text
Create a [language] [genre] song with a [mood] atmosphere. 
Use [vocal type] vocals. 
The tempo should be around [BPM]. 
The arrangement should include [instruments]. 
Start with [intro arrangement], then build into [chorus arrangement]. 
The emotional curve should move from [starting emotion] to [ending emotion]. 
The chorus should be [catchy / powerful / warm / cinematic / suitable for group singing]. 
The song is intended for [use case]. 
Avoid [unwanted elements].
```

## 9.2 Lyrics Box 公式

```text
[Style: ...]
[Vocal: ...]
[Tempo: ...]
[Arrangement: ...]
[Mood: ...]
[Theme: ...]

[Intro]
...

[Verse 1]
...

[Pre-Chorus]
...

[Chorus]
...

[Verse 2]
...

[Bridge]
...

[Final Chorus]
...

[Outro]
...
```

---

# 10. 示例：曲风条目标准格式

## Genre ID: chinese_pop_ballad

```text
中文名：中文流行抒情
英文标签：Chinese pop ballad / Mandopop ballad
一级分类：Pop
年代属性：Modern
适合主题：爱情、亲情、成长、城市生活、中年人生
适合场景：朋友圈、短视频、个人纪念、公众号配乐
情绪：warm, emotional, bittersweet, hopeful
BPM：70–95
人声：warm male vocal, soft female vocal, mature emotional vocal
乐器：piano, acoustic guitar, strings, soft drums
编曲：piano intro, restrained verse, strings and drums in chorus
Prompt 关键词：emotional Chinese pop ballad, warm piano, cinematic strings, memorable chorus
```

### 示例 Style Prompt

```text
Create a Chinese pop ballad with a warm and emotional atmosphere, 82 BPM, mature emotional male vocal, piano intro, acoustic guitar in the verses, soft drums and cinematic strings in the chorus. The song should start intimate and gradually become uplifting, with a memorable chorus suitable for short-video sharing.
```

---

## Genre ID: stadium_anthem

```text
中文名：体育主题曲 / 球场圣歌
英文标签：stadium anthem / sports anthem / arena rock anthem
一级分类：Cinematic / Rock / Sports
年代属性：Modern
适合主题：世界杯、比赛、团队、胜利、梦想、体育精神
适合场景：体育赛事、活动开场、宣传片、短视频剪辑
情绪：powerful, uplifting, triumphant, epic
BPM：95–130
人声：powerful male vocal, group vocals, choir, crowd chant
乐器：powerful drums, electric guitar, brass, strings, choir
编曲：鼓点开场，主歌推进，副歌加入合唱和球场呐喊，结尾大合唱
Prompt 关键词：stadium chant, powerful drums, anthemic chorus, group vocals, triumphant energy
```

### 示例 Style Prompt

```text
Create a cinematic stadium anthem, 112 BPM, powerful male lead vocal with group vocals, electric guitars, brass, epic drums, and crowd chant elements. The chorus should be simple, memorable, and suitable for singing together in a stadium. The mood should be triumphant, emotional, and energetic.
```

---

## Genre ID: cinematic_chinese_pop

```text
中文名：东方电影感流行
英文标签：cinematic Chinese orchestral pop
一级分类：Chinese / Cinematic
年代属性：Modern
适合主题：文旅、城市、传统文化、人生叙事、东方美学
适合场景：城市宣传片、文旅宣传、公众号视频、品牌片
情绪：elegant, cinematic, poetic, emotional, expansive
BPM：65–105
人声：clear female vocal, ethereal female vocal, warm male vocal
乐器：guzheng, pipa, erhu, dizi, piano, cinematic strings, soft drums
编曲：东方乐器点题，钢琴铺底，弦乐推进，副歌打开空间感
Prompt 关键词：oriental atmosphere, cinematic strings, guzheng, pipa, poetic lyrics, wide soundstage
```

### 示例 Style Prompt

```text
Create a cinematic Chinese orchestral pop song, 78 BPM, ethereal female vocal, guzheng, pipa, dizi, piano, cinematic strings, and soft modern drums. The song should feel poetic, elegant, and emotionally expansive, suitable for a cultural tourism video or city image film.
```

---

# 11. 参考来源

- AllMusic Genres: 用于参考一级音乐分类体系，例如 Blues、Classical、Country、Electronic、Folk、International、Jazz、Latin、Pop/Rock、R&B、Rap、Reggae、Stage & Screen、Vocal 等大类。
- Travis Nicholson, Complete List of Prompts & Styles for Suno AI Music: 用于参考 Suno Prompt 风格表达方式。
- 《Decades - Suno AI Prompts.pdf》：用于参考 1950s–2000s 的年代风格提示词表达，例如 rockabilly、doo-wop、Motown、psychedelic rock、funk-disco、arena rock、grunge、G-Funk、Y2K dance-pop 等。

---

# 12. 后续扩展计划

下一版可以继续补充：

1. `bpm_library.md`：节奏 / BPM / 场景映射库
2. `vocal_library.md`：人声与嗓音描述库
3. `instrumentation_library.md`：乐器与编曲素材库
4. `mood_library.md`：情绪与音乐表达映射库
5. `use_case_library.md`：使用场景与歌曲结构映射库
6. `prompt_templates.md`：Style Prompt / Lyrics Box / Iteration Prompt 模板库
7. `genre_library.json`：将本 Markdown 转换为结构化数据，供 Claude Code / Codex 调用
