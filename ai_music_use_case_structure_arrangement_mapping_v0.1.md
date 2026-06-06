# AI Music Use Case, Song Structure & Arrangement Mapping Library v0.1

> Purpose: This library helps an interactive AI music prompt skill translate a user's use case into a concrete song or instrumental structure, with arrangement instructions for each section.
>
> This is not just a song-structure library. It is a **scene-driven structure + arrangement decision library**.
>
> It supports both:
>
> 1. vocal songs with lyrics
> 2. modern instrumental music / background music

---

## 1. Core Design Logic

A user usually does not know how to describe music structure. They say things like:

- “I want a short-video song.”
- “I want a brand theme song.”
- “I want World Cup-style music.”
- “I want background music for a tech product video.”
- “I want study BGM.”
- “I want a personal song for Moments / social sharing.”

The skill should translate the use case into:

```text
Track Type
Recommended Length
Hook Placement
Song / Track Structure
Section-by-Section Arrangement Plan
Energy Curve
Vocal or Instrumental Strategy
Best Genres
Best BPM Range
Prompt Keywords
Avoid / Negative Prompt
```

The key rule:

```text
Do not output section tags alone. Always combine structure with arrangement behavior.
```

Weak output:

```text
[Intro]
[Verse]
[Chorus]
[Bridge]
[Final Chorus]
[Outro]
```

Better output:

```text
[Intro - soft piano motif and ambient pad, intimate mood]
[Verse 1 - sparse piano and acoustic guitar, close emotional vocal]
[Pre-Chorus - add light drums, warm bass, and subtle rising strings]
[Chorus - full drums, bass, strings, memorable emotional hook]
[Bridge - breakdown to piano and vocal only]
[Final Chorus - wider strings, stronger drums, backing vocals]
[Outro - return to the piano motif, warm resolved ending]
```

---

## 2. Vocal Song vs Instrumental Routing

Before selecting a structure, the skill should identify the track type.

### 2.1 Vocal Song

Use when the user wants:

- a complete song
- lyrics
- a theme song
- a personal song
- a brand song
- a graduation song
- a wedding song
- a sports anthem with vocals
- a short-video hook song with singing

Main control fields:

```text
lyrics
vocal style
hook
chorus
section tags
emotional arc
arrangement build
```

### 2.2 Modern Instrumental Track

Use when the user wants:

- background music
- BGM
- study music
- work music
- product video music
- brand film background
- Vlog music
- sports highlight instrumental
- podcast intro
- logo sting
- instrumental only music

Main control fields:

```text
instrumental only
no vocals
main motif
groove
texture
arrangement variation
loopability
background usability
```

Fixed negative prompt when instrumental:

```text
instrumental only, no vocals, no rap, no spoken words, no lead singing
```

---

## 3. Section Function Dictionary

### 3.1 Vocal Song Sections

| Section Tag | Lyric Function | Arrangement Function | Common Arrangement Moves |
|---|---|---|---|
| [Intro] | Set mood before lyrics | Establish sound world or motif | piano motif, guitar riff, synth pad, chant, drum pickup |
| [Verse] | Storytelling and setup | Keep arrangement restrained, leave room for lyrics | sparse piano/guitar, minimal drums, close vocal |
| [Verse 1] | First scene / emotional setup | Lowest or low-medium density | soft chords, light texture |
| [Verse 2] | Continue or deepen story | Slightly more movement than Verse 1 | add bass, light drums, harmonies, fills |
| [Pre-Chorus] | Build tension before chorus | Increase energy and expectation | add drums, bass, rising strings, riser, harmony lift |
| [Chorus] | Core message and hook | Open arrangement, higher energy | full drums, bass, strings, backing vocals, strong melody |
| [Post-Chorus] | Extend hook after chorus | Reinforce motif or chant | synth hook, vocal chop, repeated phrase, instrumental hook |
| [Hook] | Catchiest phrase or riff | Immediate attention-grabber | vocal hook, signature riff, beat already present |
| [Refrain] | Repeated lyrical or melodic idea | Light repetition, memory anchor | short recurring phrase |
| [Bridge] | Contrast / turning point | Change texture, harmony, or density | breakdown, new chords, stripped section, key lift |
| [Breakdown] | Reduce energy for contrast | Remove drums or reduce layers | vocal + piano, pads only, bass drop-out |
| [Instrumental Break] | Non-lyrical musical section | Showcase motif or instrumental color | guitar solo, sax solo, synth lead, string interlude |
| [Solo] | Instrumental feature | Adds personality and style | guitar solo, sax solo, piano solo, synth solo |
| [Final Chorus] | Final emotional release | Highest density and widest mix | full band, choir, ad-libs, bigger drums |
| [Outro] | Close the song | Resolve or fade | solo piano ending, final hook repeat, fade out, final hit |
| [Chant] | Crowd / group phrase | Creates collective energy | stadium chant, claps, drums |
| [Group Vocal] | Collective singing | Adds scale and unity | choir, backing vocals, crowd vocals |
| [Spoken Word] | Narration or poetic line | Creates intimacy or documentary feel | soft pad, minimal piano underneath |

---

### 3.2 Instrumental Sections

| Section Tag | Musical Function | Common Arrangement Moves |
|---|---|---|
| [Intro] | Establish texture and motif | filtered synth, soft piano, guitar motif, ambience |
| [Main Theme] | Present main melodic idea | lead piano/guitar/synth motif, clear rhythm |
| [Main Loop] | Stable background groove | drums, bass, chord loop, subtle motif |
| [Variation] | Keep repetition interesting | add percussion, counter-melody, small fills |
| [Subtle Variation] | Non-intrusive development | texture change, light arpeggio, background pads |
| [Breakdown] | Reduce energy | remove drums, leave pads/motif |
| [Build-Up] | Increase tension | riser, snare roll, added layers, filter opening |
| [Climax] | Highest energy / emotional payoff | full drums, bass, strings, lead melody |
| [Drop] | Electronic energy release | full beat, bass drop, synth lead |
| [Final Impact] | Last strong hit | final downbeat, cymbal crash, orchestral hit |
| [Loop Ending] | Seamless repeat | return to main motif, no hard resolution |
| [Logo Hit] | Brand ending | short resolved final note or impact |
| [Outro] | Close or fade | fade, soft ending, final motif |

---

### 3.3 Electronic Music Sections

| Section Tag | Function | Arrangement Strategy |
|---|---|---|
| [Ambient Intro] | Set atmosphere | pads, texture, filtered drums |
| [Groove] | Establish rhythm | kick, bassline, percussion |
| [Build-Up] | Prepare drop | riser, snare roll, filter sweep |
| [Drop] | Energy release | full beat, bass, lead synth |
| [Breakdown] | Reset energy | remove drums, pads/chords |
| [Second Build] | Rebuild tension | stronger riser, more layers |
| [Final Drop] | Biggest release | fuller drums, wider synths |
| [Outro] | DJ-friendly or fade ending | reduce layers, keep pulse |

---

### 3.4 Sports / Chant Sections

| Section Tag | Function | Arrangement Strategy |
|---|---|---|
| [Intro - Stadium Chant] | Immediate identity | crowd chant, claps, drums |
| [Verse - Percussion Groove] | Rhythmic vocal setup | drums, bass, guitar/brass support |
| [Pre-Chorus - Rising Crowd] | Build anticipation | snare build, brass stabs, group shouts |
| [Chorus - Group Vocal] | Crowd-singing hook | choir, chants, full drums |
| [Post-Chorus - Chant Hook] | Repeatable chant | wordless hook, crowd call-response |
| [Bridge - Clap Breakdown] | Participation moment | claps, drums, vocal call-response |
| [Final Chorus - Crowd Chant] | Biggest collective release | choir, brass, percussion, crowd |
| [Outro - Final Chant] | Memorable ending | final phrase, drum hit |

---

## 4. Field Schema for Each Use Case

Every use case template should use this schema:

```text
Use Case ID:
Chinese Name:
Track Type:
Recommended Length:
Hook Placement:
Lyrics Density:
Energy Curve:
Recommended Structure:
Arrangement Plan:
  - Intro:
  - Verse / Main Section:
  - Pre-Chorus / Build:
  - Chorus / Climax:
  - Bridge / Breakdown:
  - Final Section:
  - Outro:
Vocal Strategy:
Instrumental Strategy:
Best Genres:
Best BPM Range:
Prompt Keywords:
Negative Prompt / Avoid:
Example Structure Prompt:
```

---

## 5. Vocal Song Use-Case Templates

### 5.1 Short Video Hook Song

- Use Case ID: `short_video_hook_song`
- Chinese Name: 短视频 Hook 歌曲
- Track Type: vocal song
- Recommended Length: 20–45 seconds
- Hook Placement: first 3–8 seconds
- Lyrics Density: low to medium; short, memorable phrases
- Energy Curve: immediate hook → catchy chorus → loop-friendly ending
- Best Genres: modern pop, dance-pop, electro-pop, trap pop, folk-pop, pop-rock
- Best BPM Range: 105–135 BPM

Recommended Structure:

```text
[Hook]
[Verse]
[Chorus]
[Outro]
```

Arrangement Plan:

- Intro: usually no long intro; start with vocal hook, signature riff, or beat.
- Hook: catchiest vocal phrase appears immediately; rhythm already present.
- Verse: 2–4 short lines; keep beat light but moving.
- Chorus: full beat, bright chords, layered vocal, repeatable hook.
- Outro: quick loop-friendly ending, repeat hook phrase or leave open cadence.

Vocal Strategy:

```text
clear vocal, catchy delivery, strong melodic hook, youthful or natural tone
```

Instrumental Strategy:

```text
short intro, active beat, simple chord loop, bright production
```

Prompt Keywords:

```text
short intro, hook arrives immediately, catchy chorus, loop-friendly, suitable for short video, memorable phrase
```

Avoid:

```text
long intro, slow build, complex verse, hook after 30 seconds, too many lyrics
```

Example Structure Prompt:

```text
[Hook - start immediately with the catchiest vocal phrase and a light beat]
[Verse - short 2-line setup, minimal but moving rhythm]
[Chorus - full beat, bright chords, layered vocals, repeatable hook]
[Outro - loop-friendly ending with the hook phrase]
```

---

### 5.2 Personal Story Song

- Use Case ID: `personal_story_song`
- Chinese Name: 朋友圈 / 个人故事歌
- Track Type: vocal song
- Recommended Length: 1:30–3:00
- Hook Placement: chorus within 35–50 seconds
- Lyrics Density: medium; concrete images and emotional lines
- Energy Curve: quiet reflection → emotional release → warm ending
- Best Genres: Chinese pop ballad, folk-pop, acoustic folk, soft rock, cinematic pop
- Best BPM Range: 70–100 BPM

Recommended Structure:

```text
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Bridge]
[Final Chorus]
[Outro]
```

Arrangement Plan:

- Intro: soft piano or acoustic guitar motif; intimate and warm.
- Verse 1: sparse piano/guitar, close emotional vocal, minimal percussion.
- Pre-Chorus: add light drums, bass warmth, subtle string rise.
- Chorus: full but not too loud; drums, bass, strings, memorable emotional hook.
- Verse 2: bring back groove from chorus, add small fills or harmonies.
- Bridge: breakdown to piano and vocal only; lyrical reflection.
- Final Chorus: wider strings, stronger drums, optional backing vocals.
- Outro: return to piano/guitar motif, warm resolved ending.

Vocal Strategy:

```text
natural emotional vocal, warm male vocal, soft female vocal, mature storytelling delivery
```

Instrumental Strategy:

```text
piano, acoustic guitar, soft drums, warm bass, gentle strings
```

Prompt Keywords:

```text
intimate verse, emotional chorus, warm ending, personal storytelling, natural vocal
```

Avoid:

```text
overly commercial energy, aggressive drums, abstract slogans, crowded arrangement
```

---

### 5.3 Brand Theme Song

- Use Case ID: `brand_theme_song`
- Chinese Name: 品牌主题歌
- Track Type: vocal song
- Recommended Length: 1:00–2:30
- Hook Placement: chorus within 30–45 seconds
- Lyrics Density: medium-low; brand idea should sound natural, not slogan-heavy
- Energy Curve: confident intro → inspiring chorus → memorable ending
- Best Genres: cinematic pop, modern pop, electronic pop, corporate pop, pop-rock
- Best BPM Range: 95–125 BPM

Recommended Structure:

```text
[Intro]
[Verse]
[Pre-Chorus]
[Chorus]
[Bridge]
[Final Chorus]
[Outro]
```

Arrangement Plan:

- Intro: clean motif that can become brand identity; piano, guitar, or synth.
- Verse: clear vocal, light rhythm, lyrics introduce brand emotion or user story.
- Pre-Chorus: add drums and rising harmony to create optimism.
- Chorus: polished full arrangement, memorable brand-friendly hook.
- Bridge: short contrast; can reduce to piano/synth before final lift.
- Final Chorus: bigger backing vocals, wider mix, stronger rhythm.
- Outro: resolved ending with repeatable phrase or logo-friendly final note.

Vocal Strategy:

```text
clean modern vocal, confident but natural delivery, uplifting backing vocals
```

Instrumental Strategy:

```text
polished drums, piano, subtle synths, guitars, strings depending on brand tone
```

Prompt Keywords:

```text
uplifting, brandable hook, polished production, inspiring chorus, clean modern sound
```

Avoid:

```text
too sad, too dark, too many corporate slogans, unresolved ending
```

---

### 5.4 Corporate / Annual Event Song

- Use Case ID: `corporate_annual_event_song`
- Chinese Name: 企业宣传 / 年会歌曲
- Track Type: vocal song
- Recommended Length: 1:30–3:00
- Hook Placement: chorus within 40 seconds
- Lyrics Density: medium-low; simple, positive, collective
- Energy Curve: positive opening → group chorus → celebratory ending
- Best Genres: corporate pop, pop-rock, uplifting pop, stadium-lite anthem
- Best BPM Range: 105–128 BPM

Recommended Structure:

```text
[Intro]
[Verse]
[Pre-Chorus]
[Chorus - Group Vocal]
[Verse 2]
[Bridge]
[Final Chorus - Group Vocal]
[Outro]
```

Arrangement Plan:

- Intro: bright piano/guitar/synth motif, energetic but clean.
- Verse: simple groove, clear lead vocal.
- Pre-Chorus: add claps, drums, and rising chords.
- Chorus: group vocals, strong but accessible melody.
- Verse 2: more percussion and bass than Verse 1.
- Bridge: short breakdown with clap rhythm or spoken slogan-like line.
- Final Chorus: bigger group vocal, full drums, celebratory ending.
- Outro: repeat key phrase, final hit.

Vocal Strategy:

```text
clear lead vocal, group backing vocals, collective feeling
```

Instrumental Strategy:

```text
drums, piano, guitar, claps, synths, optional brass
```

Prompt Keywords:

```text
uplifting corporate anthem, group vocals, positive energy, celebratory chorus
```

Avoid:

```text
too serious, too dark, overly complex lyrics, weak chorus
```

---

### 5.5 Sports / World Cup Anthem

- Use Case ID: `sports_world_cup_anthem`
- Chinese Name: 体育赛事 / 世界杯主题歌
- Track Type: vocal song
- Recommended Length: 1:30–3:00
- Hook Placement: chant or rhythm motif within first 10 seconds
- Lyrics Density: medium-low; repeated phrases, easy to sing
- Energy Curve: chant intro → rising verse → huge chorus → crowd finale
- Best Genres: stadium anthem, arena rock, Latin pop, cinematic pop, pop-rock, dance-pop
- Best BPM Range: 100–130 BPM

Recommended Structure:

```text
[Intro - Stadium Chant]
[Verse - Percussion Groove]
[Pre-Chorus - Rising Crowd]
[Chorus - Group Vocal]
[Post-Chorus - Chant Hook]
[Bridge - Clap Breakdown]
[Final Chorus - Crowd Chant]
[Outro - Final Chant]
```

Arrangement Plan:

- Intro: stadium chant, crowd claps, big drums or brass motif.
- Verse: rhythmic vocal, percussion-driven groove, bass and guitar support.
- Pre-Chorus: rising drums, brass stabs, group backing vocals.
- Chorus: full stadium anthem, group vocals, powerful drums, simple repeated hook.
- Post-Chorus: chant phrase or wordless crowd hook.
- Bridge: breakdown with claps, drums, and call-response.
- Final Chorus: bigger choir, brass, percussion, crowd chant, full energy.
- Outro: final chant or drum hit.

Vocal Strategy:

```text
powerful lead vocal, group vocals, crowd chant, call-and-response
```

Instrumental Strategy:

```text
big drums, brass, electric guitar, bass, percussion, choir, Latin percussion if needed
```

Prompt Keywords:

```text
stadium anthem, crowd chant, group vocals, powerful drums, repeatable chorus, sports energy
```

Avoid:

```text
quiet intro, weak drums, complex lyrics, chorus that is hard to sing
```

---

### 5.6 Graduation Song

- Use Case ID: `graduation_song`
- Chinese Name: 毕业季歌曲
- Track Type: vocal song
- Recommended Length: 2:00–3:30
- Hook Placement: chorus within 40–60 seconds
- Lyrics Density: medium; school memories and farewell imagery
- Energy Curve: nostalgia → farewell → hopeful future
- Best Genres: folk-pop, campus folk, Chinese pop ballad, pop-rock
- Best BPM Range: 75–110 BPM

Recommended Structure:

```text
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Bridge]
[Final Chorus - Group Vocal]
[Outro]
```

Arrangement Plan:

- Intro: acoustic guitar or piano motif, nostalgic tone.
- Verse 1: light guitar/piano, minimal percussion, concrete campus images.
- Pre-Chorus: add bass and light drums, emotional lift.
- Chorus: full but warm; strings or backing vocals enter.
- Verse 2: more rhythmic movement, group harmony hints.
- Bridge: stripped-down reflection, maybe only piano and vocal.
- Final Chorus: group vocals, wider strings, hopeful release.
- Outro: soft ending with repeated line or school-bell-like motif.

Vocal Strategy:

```text
clear youthful vocal, warm group backing, natural emotional delivery
```

Instrumental Strategy:

```text
acoustic guitar, piano, light drums, strings, group vocals
```

Prompt Keywords:

```text
nostalgic graduation song, hopeful final chorus, campus memories, group vocal ending
```

Avoid:

```text
too dark, too commercial, overly adult sadness, aggressive sound
```

---

### 5.7 Wedding / Anniversary Song

- Use Case ID: `wedding_anniversary_song`
- Chinese Name: 婚礼 / 纪念日歌曲
- Track Type: vocal song
- Recommended Length: 2:00–3:30
- Hook Placement: chorus within 45 seconds
- Lyrics Density: medium-low; tender and specific
- Energy Curve: intimate → romantic → warm final chorus
- Best Genres: romantic pop ballad, R&B ballad, acoustic folk-pop, piano ballad
- Best BPM Range: 65–100 BPM

Recommended Structure:

```text
[Intro]
[Verse 1]
[Chorus]
[Verse 2]
[Bridge]
[Final Chorus]
[Outro]
```

Arrangement Plan:

- Intro: soft piano or acoustic guitar, romantic motif.
- Verse 1: intimate vocal, minimal rhythm.
- Chorus: warm strings, soft drums, emotional but gentle melody.
- Verse 2: add bass and subtle harmony.
- Bridge: tender breakdown, maybe duet or harmony.
- Final Chorus: fuller strings and backing vocals, romantic resolution.
- Outro: soft final line, piano or guitar ending.

Vocal Strategy:

```text
tender vocal, smooth male/female vocal, duet if requested
```

Instrumental Strategy:

```text
piano, acoustic guitar, soft strings, light R&B drums
```

Prompt Keywords:

```text
romantic, tender, intimate, warm final chorus, wedding-friendly
```

Avoid:

```text
aggressive drums, dark lyrics, tragic ending, overly dramatic tension
```

---

### 5.8 Birthday / Blessing Song

- Use Case ID: `birthday_blessing_song`
- Chinese Name: 生日 / 祝福歌曲
- Track Type: vocal song
- Recommended Length: 30–120 seconds
- Hook Placement: within 10–20 seconds
- Lyrics Density: low; clear blessing phrases
- Energy Curve: warm opening → cheerful chorus → friendly ending
- Best Genres: bright pop, acoustic pop, children’s pop, folk-pop
- Best BPM Range: 90–125 BPM

Recommended Structure:

```text
[Intro]
[Verse]
[Chorus]
[Repeat Chorus]
[Outro]
```

Arrangement Plan:

- Intro: friendly motif, light piano/guitar/ukulele.
- Verse: short blessing setup, simple rhythm.
- Chorus: memorable blessing line, claps or light percussion.
- Repeat Chorus: reinforce the blessing phrase.
- Outro: warm final line.

Vocal Strategy:

```text
cheerful vocal, warm natural delivery, group vocal if family/friends
```

Instrumental Strategy:

```text
ukulele, piano, acoustic guitar, hand claps, soft drums
```

Prompt Keywords:

```text
warm birthday song, cheerful blessing, simple catchy chorus, family-friendly
```

Avoid:

```text
too long, sad tone, complex metaphors, intense drums
```

---

### 5.9 Children’s Educational Song

- Use Case ID: `children_educational_song`
- Chinese Name: 儿童教育歌曲
- Track Type: vocal song
- Recommended Length: 30–90 seconds
- Hook Placement: first 5–10 seconds
- Lyrics Density: low; simple, repetitive, easy to remember
- Energy Curve: cheerful from start to end
- Best Genres: children’s song, playful pop, cartoon theme
- Best BPM Range: 90–130 BPM

Recommended Structure:

```text
[Intro]
[Verse]
[Chorus]
[Repeat Chorus]
[Outro]
```

Arrangement Plan:

- Intro: bright motif, bells/ukulele/claps.
- Verse: simple teaching point, short lines.
- Chorus: repeated key learning phrase.
- Repeat Chorus: reinforce memory.
- Outro: friendly ending or call-and-response.

Vocal Strategy:

```text
cheerful vocal, children’s choir, simple call-and-response
```

Instrumental Strategy:

```text
ukulele, hand claps, toy piano, bells, light drums
```

Prompt Keywords:

```text
children’s educational song, simple lyrics, playful, bright melody, easy to remember
```

Avoid:

```text
complex metaphors, dark mood, long bridge, intense bass
```

---

### 5.10 Article-to-Song Adaptation

- Use Case ID: `article_to_song_adaptation`
- Chinese Name: 公众号文章 / 观点内容改编歌曲
- Track Type: vocal song
- Recommended Length: 1:30–3:00
- Hook Placement: chorus within 45 seconds
- Lyrics Density: medium-high, but lines must remain singable
- Energy Curve: idea setup → emotional summary → memorable conclusion
- Best Genres: Chinese pop ballad, folk-pop, cinematic pop, spoken-word pop
- Best BPM Range: 70–110 BPM

Recommended Structure:

```text
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Bridge]
[Final Chorus]
[Outro]
```

Arrangement Plan:

- Intro: mood-setting motif that matches article tone.
- Verse 1: turn article situation into concrete scene.
- Pre-Chorus: condense tension or question from the article.
- Chorus: summarize the core insight emotionally.
- Verse 2: second example or deeper angle.
- Bridge: reflection or turning point.
- Final Chorus: repeat the article’s emotional conclusion in a memorable way.
- Outro: leave one quotable final line.

Vocal Strategy:

```text
natural storytelling vocal, mature emotional delivery, optional spoken-word intro
```

Instrumental Strategy:

```text
depends on article tone; often piano, guitar, strings, soft drums
```

Prompt Keywords:

```text
story-driven, reflective, article-inspired, emotional summary, singable lines
```

Avoid:

```text
essay-like long lines, slogan stacking, too many concepts, no concrete imagery
```

---

### 5.11 City / Cultural Tourism Song

- Use Case ID: `city_cultural_tourism_song`
- Chinese Name: 城市 / 文旅宣传歌曲
- Track Type: vocal song
- Recommended Length: 1:30–3:00
- Hook Placement: chorus within 40–50 seconds
- Lyrics Density: medium; place names and images should be poetic, not list-like
- Energy Curve: scenic opening → emotional identity → expansive final chorus
- Best Genres: Chinese traditional pop, cinematic pop, folk-pop, world fusion
- Best BPM Range: 75–115 BPM

Recommended Structure:

```text
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Bridge]
[Final Chorus]
[Outro]
```

Arrangement Plan:

- Intro: local color motif, traditional instrument or cinematic piano.
- Verse 1: scenic images, restrained arrangement.
- Pre-Chorus: add percussion or strings, emotional lift.
- Chorus: open, memorable city identity phrase.
- Verse 2: add more rhythmic movement and local texture.
- Bridge: instrumental break with regional instrument.
- Final Chorus: full arrangement, choir or backing vocal.
- Outro: return to local motif.

Vocal Strategy:

```text
clear emotional vocal, poetic delivery, optional group backing
```

Instrumental Strategy:

```text
piano, strings, Chinese instruments, regional percussion, cinematic drums
```

Prompt Keywords:

```text
city anthem, cultural tourism, poetic imagery, cinematic Chinese pop, local musical color
```

Avoid:

```text
tourism slogan list, too many place names, generic stock music feel
```

---

### 5.12 Healing Emotional Song

- Use Case ID: `healing_emotional_song`
- Chinese Name: 情绪疗愈歌曲
- Track Type: vocal song
- Recommended Length: 1:30–3:30
- Hook Placement: chorus within 45–60 seconds
- Lyrics Density: medium-low; simple comforting language
- Energy Curve: soft comfort → gentle hope → peaceful ending
- Best Genres: healing pop, acoustic folk-pop, piano ballad, ambient pop
- Best BPM Range: 60–90 BPM

Recommended Structure:

```text
[Intro]
[Verse 1]
[Chorus]
[Verse 2]
[Bridge]
[Final Chorus]
[Outro]
```

Arrangement Plan:

- Intro: soft piano, ambient pad, gentle texture.
- Verse 1: intimate vocal, minimal accompaniment.
- Chorus: gentle lift, light strings or warm harmonies.
- Verse 2: add subtle percussion or bass warmth.
- Bridge: very soft breakdown, comforting line.
- Final Chorus: slightly fuller but still gentle.
- Outro: peaceful fade or soft final chord.

Vocal Strategy:

```text
soft vocal, breathy delivery, clear gentle tone
```

Instrumental Strategy:

```text
soft piano, pads, acoustic guitar, light strings, minimal percussion
```

Prompt Keywords:

```text
healing, soothing, gentle, comforting, peaceful, soft final chorus
```

Avoid:

```text
loud drums, dramatic climax, aggressive vocal, harsh synths
```

---

## 6. Instrumental Use-Case Templates

### 6.1 Short Video BGM

- Use Case ID: `short_video_bgm`
- Chinese Name: 短视频 BGM
- Track Type: instrumental
- Recommended Length: 15–60 seconds
- Hook Placement: first 3–8 seconds
- Energy Curve: immediate identity → small variation → seamless loop
- Best Genres: lo-fi, electro-pop instrumental, chillhop, future bass, funk groove
- Best BPM Range: 85–130 BPM

Recommended Structure:

```text
[Intro]
[Main Hook]
[Variation]
[Loop Ending]
```

Arrangement Plan:

- Intro: very short; start with beat, motif, or recognizable sound.
- Main Hook: simple instrumental melody or rhythmic motif.
- Variation: add small percussion, counter-melody, or texture shift.
- Loop Ending: return to main motif without hard finality.

Instrumental Strategy:

```text
instrumental only, no vocals, no rap, no spoken words, short intro, loop-friendly
```

Prompt Keywords:

```text
short video BGM, hook arrives early, instrumental hook, loop-friendly, clear beat
```

Avoid:

```text
vocals, long build, complex changes, sudden dramatic ending
```

---

### 6.2 Study / Work BGM

- Use Case ID: `study_work_bgm`
- Chinese Name: 学习 / 工作 BGM
- Track Type: instrumental
- Recommended Length: 2:00–5:00 or loopable
- Hook Placement: subtle motif, not distracting
- Energy Curve: stable and calm
- Best Genres: lo-fi hip-hop, chillhop, ambient pop, piano instrumental, downtempo
- Best BPM Range: 60–90 BPM

Recommended Structure:

```text
[Intro]
[Main Loop]
[Subtle Variation]
[Breakdown]
[Main Loop Return]
[Outro]
```

Arrangement Plan:

- Intro: soft piano chords, vinyl texture, or ambient pad.
- Main Loop: mellow drums, warm bass, simple piano/guitar motif.
- Subtle Variation: add light keys, small percussion, or background texture.
- Breakdown: remove drums briefly, keep pad and main motif.
- Main Loop Return: bring drums and bass back gently.
- Outro: fade or loop-friendly ending.

Instrumental Strategy:

```text
instrumental only, no vocals, non-intrusive, steady groove, subtle variations, loop-friendly
```

Prompt Keywords:

```text
study background music, calm, non-intrusive, subtle variation, warm lo-fi texture
```

Avoid:

```text
vocals, sudden drops, dramatic transitions, big chorus, aggressive drums
```

---

### 6.3 Brand Film Background Music

- Use Case ID: `brand_film_background_music`
- Chinese Name: 品牌宣传片背景音乐
- Track Type: instrumental
- Recommended Length: 60–120 seconds
- Hook Placement: recognizable motif within 10–15 seconds
- Energy Curve: clean opening → confident build → uplifting climax
- Best Genres: corporate pop instrumental, cinematic pop instrumental, uplifting electronic
- Best BPM Range: 90–125 BPM

Recommended Structure:

```text
[Intro]
[Build]
[Main Theme]
[Climax]
[Outro]
```

Arrangement Plan:

- Intro: clean piano or minimal synth motif, premium brand identity.
- Build: add soft pulse, bass, light percussion, sense of progress.
- Main Theme: introduce memorable melody, polished drums and warm harmony.
- Climax: cinematic strings, bigger drums, wider mix, uplifting feeling.
- Outro: resolved ending, logo-friendly final note or hit.

Instrumental Strategy:

```text
instrumental only, polished, optimistic, leave room for voiceover, premium mix
```

Prompt Keywords:

```text
brand film background music, uplifting corporate, premium, clean build, inspiring climax
```

Avoid:

```text
too sad, too busy, cheap stock music feel, too many lead melodies fighting voiceover
```

---

### 6.4 Tech Product Background Music

- Use Case ID: `tech_product_background_music`
- Chinese Name: 科技产品背景音乐
- Track Type: instrumental
- Recommended Length: 45–120 seconds
- Hook Placement: subtle motif within 10–15 seconds
- Energy Curve: precise → optimistic → premium
- Best Genres: minimal electronic, tech product background, synth-pop instrumental, corporate electronic
- Best BPM Range: 90–125 BPM

Recommended Structure:

```text
[Intro]
[Pulse Groove]
[Build]
[Main Theme]
[Outro]
```

Arrangement Plan:

- Intro: clean digital texture, soft synth pulse.
- Pulse Groove: minimal beat, sub bass, precise rhythmic movement.
- Build: add arpeggio, brighter synth layers, slight lift.
- Main Theme: memorable but not distracting synth/piano motif.
- Outro: clean resolved ending, logo-friendly.

Instrumental Strategy:

```text
instrumental only, clean futuristic, minimal electronic, premium, non-intrusive
```

Prompt Keywords:

```text
tech product background, futuristic, clean, pulsing synths, digital texture, premium
```

Avoid:

```text
rustic acoustic-only, overly emotional strings, club drop, aggressive bass
```

---

### 6.5 Vlog / Travel BGM

- Use Case ID: `vlog_travel_bgm`
- Chinese Name: Vlog / 旅行生活方式 BGM
- Track Type: instrumental
- Recommended Length: 30–120 seconds
- Hook Placement: light motif within first 10 seconds
- Energy Curve: relaxed and breezy
- Best Genres: acoustic instrumental, bossa nova instrumental, chillhop, lifestyle pop
- Best BPM Range: 85–120 BPM

Recommended Structure:

```text
[Intro]
[Main Groove]
[Variation]
[Outro]
```

Arrangement Plan:

- Intro: light guitar, ukulele, or piano motif.
- Main Groove: soft beat, warm bass, breezy melody.
- Variation: small percussion, hand claps, or second guitar line.
- Outro: gentle close or loop-friendly ending.

Instrumental Strategy:

```text
instrumental only, sunny, relaxed, friendly, lifestyle background
```

Prompt Keywords:

```text
travel vlog BGM, breezy, sunny, relaxed groove, acoustic texture, lifestyle
```

Avoid:

```text
dramatic climax, heavy drums, dark mood, too cinematic
```

---

### 6.6 Documentary / Character Story Score

- Use Case ID: `documentary_character_story_score`
- Chinese Name: 纪录片 / 人物故事配乐
- Track Type: instrumental
- Recommended Length: 1:00–3:00
- Hook Placement: emotional motif within 20–30 seconds
- Energy Curve: reflective opening → emotional build → restrained resolution
- Best Genres: cinematic emotional instrumental, piano score, ambient pop, orchestral pop instrumental
- Best BPM Range: 60–100 BPM

Recommended Structure:

```text
[Intro]
[Main Theme]
[Development]
[Emotional Build]
[Resolution]
[Outro]
```

Arrangement Plan:

- Intro: soft piano, ambient texture, documentary tone.
- Main Theme: simple motif, emotionally clear.
- Development: add strings, low percussion, or subtle guitar.
- Emotional Build: widen strings, add deeper bass or percussion.
- Resolution: reduce density, leave emotional space.
- Outro: soft final chord or unresolved reflective ending if needed.

Instrumental Strategy:

```text
instrumental only, emotional, cinematic, restrained, leave room for narration
```

Prompt Keywords:

```text
documentary score, emotional build, reflective piano, warm strings, restrained climax
```

Avoid:

```text
overly pop chorus, too loud, too busy, distracting lead melody
```

---

### 6.7 Sports Highlight Instrumental

- Use Case ID: `sports_highlight_instrumental`
- Chinese Name: 体育剪辑 / 高光集锦配乐
- Track Type: instrumental
- Recommended Length: 30–120 seconds
- Hook Placement: strong rhythm or impact within first 5–10 seconds
- Energy Curve: tension → impact → bigger final hit
- Best Genres: sports highlight instrumental, cinematic action, trap instrumental, arena rock instrumental
- Best BPM Range: 100–150 BPM

Recommended Structure:

```text
[Intro]
[Build-Up]
[Drop / Main Impact]
[Breakdown]
[Final Impact]
[Outro]
```

Arrangement Plan:

- Intro: punchy hit, drum motif, or tense pulse.
- Build-Up: rising percussion, bass, guitar/synth/brass layers.
- Drop / Main Impact: full drums, bass, impacts, lead motif.
- Breakdown: reduce energy briefly for edit contrast.
- Final Impact: bigger drums, brass/guitar/synth, wide mix.
- Outro: strong final hit or cut-friendly ending.

Instrumental Strategy:

```text
instrumental only, powerful rhythm, high-impact, edit-friendly, strong hits
```

Prompt Keywords:

```text
sports highlight music, powerful drums, cinematic action, impact hits, high-energy build
```

Avoid:

```text
slow mellow intro, weak rhythm, no impact points, overly soft instrumentation
```

---

### 6.8 Podcast Intro / Logo Sting

- Use Case ID: `podcast_intro_logo_sting`
- Chinese Name: 播客片头 / Logo Sting
- Track Type: instrumental
- Recommended Length: 5–15 seconds for logo sting; 10–30 seconds for podcast intro
- Hook Placement: immediate motif
- Energy Curve: quick identity → resolved ending
- Best Genres: minimal electronic, corporate pop, jazz pop, acoustic logo, synth logo
- Best BPM Range: flexible; usually 90–125 BPM feel

Recommended Structure:

```text
[Signature Motif]
[Short Build]
[Logo Hit]
```

Arrangement Plan:

- Signature Motif: 2–4 note identity, immediately recognizable.
- Short Build: one quick swell or rhythmic movement.
- Logo Hit: clean final resolved note, hit, or chord.

Instrumental Strategy:

```text
instrumental only, concise, memorable, brandable, clean ending
```

Prompt Keywords:

```text
podcast intro, logo sting, short signature motif, brandable, resolved final hit
```

Avoid:

```text
long development, unresolved ending, too many instruments, vocals
```

---

### 6.9 Fashion / Lifestyle Background

- Use Case ID: `fashion_lifestyle_background`
- Chinese Name: 时尚 / 生活方式背景音乐
- Track Type: instrumental
- Recommended Length: 30–120 seconds
- Hook Placement: groove within first 5–10 seconds
- Energy Curve: stylish steady groove → subtle variations → clean ending
- Best Genres: nu jazz instrumental, fashion groove, minimal house, disco-funk instrumental, chill electronic
- Best BPM Range: 95–125 BPM

Recommended Structure:

```text
[Intro]
[Groove]
[Variation]
[Breakdown]
[Groove Return]
[Outro]
```

Arrangement Plan:

- Intro: clean bassline, muted guitar, or stylish synth.
- Groove: drums, bass, minimal chord pattern.
- Variation: add percussion, synth stab, or guitar lick.
- Breakdown: reduce drums briefly for edit contrast.
- Groove Return: bring back rhythm with more polish.
- Outro: clean fade or final groove hit.

Instrumental Strategy:

```text
instrumental only, stylish, minimal, polished, groove-based
```

Prompt Keywords:

```text
fashion background music, stylish groove, minimal, polished, elegant, modern lifestyle
```

Avoid:

```text
overly emotional melody, childish sounds, cluttered arrangement
```

---

### 6.10 Meditation / Sleep Ambient

- Use Case ID: `meditation_sleep_ambient`
- Chinese Name: 冥想 / 睡眠氛围音乐
- Track Type: instrumental
- Recommended Length: 3:00–10:00 or loopable
- Hook Placement: no strong hook
- Energy Curve: extremely stable, slow evolution
- Best Genres: ambient, ambient electronic, soft piano ambient, healing soundscape
- Best BPM Range: no strict BPM or 50–70 BPM feel

Recommended Structure:

```text
[Ambient Intro]
[Soft Main Texture]
[Subtle Evolution]
[Calm Return]
[Fade Out]
```

Arrangement Plan:

- Ambient Intro: pads, nature texture, soft drone.
- Soft Main Texture: long sustained tones, soft piano or bells.
- Subtle Evolution: barely noticeable harmonic or texture changes.
- Calm Return: simplify back to main texture.
- Fade Out: very soft ending or loop-friendly fade.

Instrumental Strategy:

```text
instrumental only, no vocals, no drums or minimal pulse, calm, spacious, sleep-friendly
```

Prompt Keywords:

```text
meditation ambient, sleep music, spacious pads, soft texture, slow evolution, peaceful
```

Avoid:

```text
strong beat, sudden change, vocals, bright hook, dramatic climax
```

---

## 7. Length & Hook Placement Reference

| Use Case | Recommended Length | Hook / Main Motif Placement |
|---|---:|---|
| Short video hook song | 20–45 sec | 3–8 sec |
| Short video BGM | 15–60 sec | 3–8 sec |
| Personal story song | 1:30–3:00 | chorus 35–50 sec |
| Brand theme song | 1:00–2:30 | chorus 30–45 sec |
| Corporate / annual event song | 1:30–3:00 | chorus within 40 sec |
| Sports / World Cup anthem | 1:30–3:00 | chant within 10 sec |
| Graduation song | 2:00–3:30 | chorus 40–60 sec |
| Wedding song | 2:00–3:30 | chorus within 45 sec |
| Birthday song | 30–120 sec | 10–20 sec |
| Children’s educational song | 30–90 sec | 5–10 sec |
| Study / work BGM | 2:00–5:00 or loop | no strong hook |
| Brand film BGM | 60–120 sec | motif 10–15 sec |
| Tech product BGM | 45–120 sec | motif 10–15 sec |
| Documentary score | 1:00–3:00 | motif 20–30 sec |
| Sports highlight instrumental | 30–120 sec | impact 5–10 sec |
| Podcast intro / logo sting | 5–30 sec | immediate |

---

## 8. Scene-to-Structure Quick Map

| User Scene | Track Type | Structure |
|---|---|---|
| 短视频歌曲 | vocal | [Hook] [Verse] [Chorus] [Outro] |
| 朋友圈个人歌 | vocal | [Intro] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Bridge] [Final Chorus] [Outro] |
| 品牌主题歌 | vocal | [Intro] [Verse] [Pre-Chorus] [Chorus] [Bridge] [Final Chorus] [Outro] |
| 体育 / 世界杯 | vocal | [Intro - Stadium Chant] [Verse] [Pre-Chorus] [Chorus - Group Vocal] [Post-Chorus] [Bridge] [Final Chorus] [Outro] |
| 毕业歌 | vocal | [Intro] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Bridge] [Final Chorus - Group Vocal] [Outro] |
| 婚礼歌 | vocal | [Intro] [Verse 1] [Chorus] [Verse 2] [Bridge] [Final Chorus] [Outro] |
| 儿童教育 | vocal | [Intro] [Verse] [Chorus] [Repeat Chorus] [Outro] |
| 短视频 BGM | instrumental | [Intro] [Main Hook] [Variation] [Loop Ending] |
| 学习 BGM | instrumental | [Intro] [Main Loop] [Subtle Variation] [Breakdown] [Main Loop Return] [Outro] |
| 品牌片 BGM | instrumental | [Intro] [Build] [Main Theme] [Climax] [Outro] |
| 科技产品 BGM | instrumental | [Intro] [Pulse Groove] [Build] [Main Theme] [Outro] |
| 运动剪辑 | instrumental | [Intro] [Build-Up] [Drop / Main Impact] [Breakdown] [Final Impact] [Outro] |

---

## 9. Scene-to-Arrangement Quick Map

| Scene | Arrangement Priority |
|---|---|
| Short video | hook early, short intro, loop-friendly |
| Personal story | intimate verse, emotional chorus, warm ending |
| Brand theme | polished build, brandable hook, positive ending |
| Corporate event | group vocal, claps, celebratory final chorus |
| Sports anthem | chant, big drums, group vocal, repeatable hook |
| Graduation | nostalgic intro, hopeful group final chorus |
| Wedding | tender intro, romantic strings, warm final chorus |
| Children’s song | simple melody, playful instruments, repetition |
| Article adaptation | turn concept into emotional chorus |
| City tourism | local motif, cinematic expansion |
| Study BGM | stable loop, subtle variation, no vocals |
| Tech product | minimal synth pulse, clean build, leave space |
| Brand film BGM | premium motif, steady uplift, resolved logo ending |
| Documentary | restrained emotional build, narration-friendly |
| Sports highlight | edit-friendly impacts, tension and release |
| Podcast / logo | immediate motif, short build, final hit |

---

## 10. Negative Structure Rules

| Scene | Avoid |
|---|---|
| Short video | long intro, hook too late, slow cinematic build |
| Brand promo | too sad, too dark, unresolved ending |
| Sports anthem | weak drums, complex lyrics, no chant |
| Study BGM | vocals, drops, big chorus, sudden changes |
| Wedding | aggressive drums, dark lyrics, tragic ending |
| Children’s song | complex metaphors, long bridge, dark mood |
| Tech product | rustic acoustic-only, club drop, cluttered mix |
| Documentary | loud pop hook, distracting lead melody |
| Logo sting | long development, unresolved ending |
| Instrumental BGM | vocals, rap, spoken words unless requested |
| Background music with voiceover | busy lead melody, dense vocals, harsh transients |

---

## 11. Prompt Formula

### 11.1 Vocal Song Structure + Arrangement Formula

```text
Use the following song structure and arrangement plan:

[Intro - {intro arrangement}]
[Verse 1 - {verse arrangement, vocal focus}]
[Pre-Chorus - {build strategy}]
[Chorus - {full arrangement, hook strategy}]
[Verse 2 - {slightly expanded verse arrangement}]
[Bridge - {contrast or breakdown}]
[Final Chorus - {largest arrangement, emotional payoff}]
[Outro - {ending strategy}]

The arrangement should move from {starting energy} to {ending energy}. The hook should appear {hook placement}. The song is intended for {use case}.
```

### 11.2 Instrumental Structure + Arrangement Formula

```text
Create a {genre} instrumental track for {use case}.

Instrumental only, no vocals, no rap, no spoken words.

Use the following structure:

[Intro - {texture / motif}]
[Main Theme - {main melody / groove}]
[Variation - {subtle change}]
[Breakdown - {reduced energy}]
[Final Section - {climax or return}]
[Outro / Loop Ending - {ending behavior}]

The arrangement should be {energy curve}, with {instrumentation}. Make it {loop-friendly / narration-friendly / edit-friendly / brandable}.
```

### 11.3 Short-Video Hook Formula

```text
Create a short, catchy {genre} track for short videos. The hook should arrive within the first 3–8 seconds. Use a short intro, clear rhythm, memorable melodic phrase, and loop-friendly ending.
```

### 11.4 Brand Film Formula

```text
Create a polished {genre} background track for a brand film. Start with a clean motif, build gradually with subtle rhythm and harmonic layers, reach an uplifting climax, and end with a resolved logo-friendly final note. Leave room for voiceover.
```

### 11.5 Sports Anthem Formula

```text
Create a powerful stadium anthem. Start with a chant or percussion motif, build with drums and brass, use group vocals in the chorus, add a chant-like post-chorus, and finish with a full crowd-style final chorus.
```

---

## 12. Skill Routing Logic

### 12.1 If User Gives Only a Scene

Example:

> I want music for a tech product video.

Infer:

```text
Track Type: instrumental
Use Case: tech product background music
Structure: [Intro] [Pulse Groove] [Build] [Main Theme] [Outro]
Arrangement: minimal synth pulse, clean beat, digital texture, premium mix
Negative: instrumental only, no vocals
```

### 12.2 If User Gives Scene + Wants Lyrics

Example:

> I want a tech product theme song with lyrics.

Infer:

```text
Track Type: vocal song
Use Case: brand theme song / tech brand song
Structure: [Intro] [Verse] [Pre-Chorus] [Chorus] [Bridge] [Final Chorus] [Outro]
Arrangement: clean electronic pop, synth pulse, polished drums, inspiring chorus
```

### 12.3 If User Says “BGM”

Default to instrumental:

```text
instrumental only, no vocals, no rap, no spoken words
```

Then select use-case structure.

### 12.4 If User Says “主题曲”

Default to vocal song unless they specify instrumental.

### 12.5 If User Says “短视频”

Ask or infer:

```text
Do they want a vocal hook or instrumental BGM?
```

If unclear, generate two options:

1. vocal hook version
2. instrumental BGM version

### 12.6 If User Says “学习 / 工作 / 睡眠”

Always default to instrumental.

Use:

```text
non-intrusive, stable, loop-friendly, no vocals
```

### 12.7 If User Says “品牌宣传”

Ask or infer whether it is:

1. brand theme song with lyrics
2. background music for brand film

If unclear, default to background music for brand film and offer theme-song alternative.

---

## 13. Integration with Other Libraries

This library should call:

```text
Genre Library → choose genre
Rhythm / BPM Library → choose tempo
Vocal Library → choose vocal style
Instrumentation Library → choose instruments
Emotion Mapping Library → choose emotional curve
Use Case Structure Library → choose section structure and arrangement plan
```

Recommended order:

```text
Use Case → Track Type → Structure → Arrangement Plan → Genre → BPM → Vocal / No Vocal → Instrumentation → Emotion Curve → Final Prompt
```

---

## 14. Version Notes

v0.1 includes:

- vocal song vs instrumental routing
- section function dictionary
- scene-based structure templates
- section-by-section arrangement planning
- hook placement reference
- length reference
- negative structure rules
- prompt formulas
- skill routing logic

Future versions can add:

- platform-specific structure tags for Suno / Udio
- 15-second / 30-second / 60-second variations
- detailed Chinese lyric section templates
- arrangement density levels
- transition FX library
- voiceover-friendly background music presets
- multi-version output templates
