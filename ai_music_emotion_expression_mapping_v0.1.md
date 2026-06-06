# AI Music Emotion & Musical Expression Mapping Library v0.1

> Purpose: This library helps an interactive AI music prompt skill translate user emotion words such as “warm”, “lonely”, “cinematic”, “uplifting”, “healing”, “epic”, or “premium” into concrete AI music prompt instructions.
>
> It is designed for both:
>
> 1. vocal songs with lyrics
> 2. modern instrumental music / background music

---

## 1. How to Use This Library

Emotion is one of the most important inputs in AI music generation. Users often describe a desired feeling, but AI music tools need more concrete musical instructions.

This library converts emotion into:

- tempo / BPM
- rhythm density
- harmony and chord color
- instrumentation
- arrangement density
- vocal delivery
- production texture
- energy curve
- prompt keywords
- use-case recommendations

The skill should not simply copy the user's emotional word into the final prompt. It should translate that word into musical decisions.

Example:

User says:

> I want it to feel warm but a little sad.

The skill should translate this into:

```text
warm, bittersweet, medium-slow tempo, piano and acoustic guitar, soft drums, gentle strings, natural emotional vocal, restrained verse, uplifting chorus
```

---

## 2. Core Emotional Dimensions

For prompt generation, emotion can be mapped through two main dimensions:

### 2.1 Valence

Valence describes whether the feeling is positive, negative, or mixed.

| Valence | Typical User Words | Prompt Direction |
|---|---|---|
| Positive | happy, bright, hopeful, joyful | major key feeling, upbeat tempo, clear vocal, bright instruments |
| Negative | sad, lonely, dark, painful | minor key feeling, slower tempo, sparse arrangement, darker timbre |
| Mixed | bittersweet, nostalgic, warm sadness | major/minor ambiguity, medium tempo, soft textures, emotional vocal |

### 2.2 Arousal

Arousal describes energy level.

| Arousal | Typical User Words | Prompt Direction |
|---|---|---|
| Low | calm, peaceful, healing, ambient | slow tempo, soft dynamics, sparse drums, pads, piano |
| Medium | warm, emotional, romantic, reflective | medium tempo, steady groove, moderate arrangement |
| High | energetic, powerful, epic, angry, triumphant | faster tempo, strong drums, dense arrangement, big chorus |

### 2.3 Practical Mapping

| Emotion Type | Valence | Arousal | Musical Strategy |
|---|---:|---:|---|
| Healing | positive | low | soft, warm, spacious |
| Melancholic | negative | low-medium | slower, minor color, emotional vocal |
| Uplifting | positive | medium-high | gradual build, stronger chorus |
| Epic | positive / heroic | high | orchestral drums, choir, wide mix |
| Angry / intense | negative | high | distorted guitars, aggressive drums, sharp vocals |
| Nostalgic | mixed | medium | vintage texture, warm harmonies, moderate tempo |

---

## 3. Emotion-to-Music Mapping Table

### 3.1 Warm / 温暖

| Field | Recommendation |
|---|---|
| BPM | 75–105 |
| Rhythm | gentle groove, soft drums, light percussion |
| Harmony | warm major chords, occasional bittersweet color |
| Instruments | piano, acoustic guitar, soft strings, mellow bass |
| Vocal | warm male vocal, soft female vocal, natural emotional vocal |
| Arrangement | restrained verse, fuller chorus, smooth build |
| Production | clean, intimate, warm, organic |
| Good For | personal stories, family, friendship, daily life, brand warmth |
| Prompt Keywords | warm, heartfelt, intimate, soft piano, acoustic guitar, gentle strings, natural vocal |

Example prompt phrase:

```text
warm and heartfelt atmosphere, medium-slow tempo, soft piano and acoustic guitar, gentle strings in the chorus, natural emotional vocal
```

---

### 3.2 Healing / 治愈

| Field | Recommendation |
|---|---|
| BPM | 60–90 |
| Rhythm | light, slow, non-intrusive |
| Harmony | simple major chords, soft suspended chords |
| Instruments | piano, clean guitar, pads, soft bells, light percussion |
| Vocal | soft female vocal, clear young vocal, breathy vocal |
| Arrangement | minimal, airy, slowly unfolding |
| Production | spacious, clean, soothing |
| Good For | sleep, study, emotional comfort, lifestyle videos |
| Prompt Keywords | healing, soothing, gentle, airy, soft textures, peaceful, comforting |

Example prompt phrase:

```text
healing and soothing mood, slow tempo, airy pads, soft piano, gentle percussion, spacious mix, peaceful emotional tone
```

---

### 3.3 Melancholic / 伤感

| Field | Recommendation |
|---|---|
| BPM | 60–85 |
| Rhythm | sparse drums, slow pulse, minimal percussion |
| Harmony | minor key feeling, descending progressions |
| Instruments | piano, cello, soft strings, acoustic guitar |
| Vocal | emotional male vocal, breathy female vocal, restrained delivery |
| Arrangement | quiet verse, emotional chorus, not too dense |
| Production | intimate, dark-warm, close vocal |
| Good For | heartbreak, farewell, regret, late-night songs |
| Prompt Keywords | melancholic, emotional, minor-key feeling, slow piano, intimate vocal, soft strings |

Example prompt phrase:

```text
melancholic pop ballad with slow piano, soft strings, intimate emotional vocal, restrained verses and a quietly powerful chorus
```

---

### 3.4 Bittersweet / 苦甜感

| Field | Recommendation |
|---|---|
| BPM | 75–100 |
| Rhythm | steady, gentle, not too slow |
| Harmony | mixed major/minor color, nostalgic progressions |
| Instruments | piano, acoustic guitar, warm synth pad, strings |
| Vocal | mature emotional vocal, warm but restrained |
| Arrangement | starts reflective, chorus becomes hopeful |
| Production | warm, cinematic, slightly nostalgic |
| Good For | memory, growing up, middle age, hometown, goodbye |
| Prompt Keywords | bittersweet, nostalgic, warm sadness, reflective, hopeful chorus |

Example prompt phrase:

```text
bittersweet and reflective mood, warm piano and acoustic guitar, nostalgic chord colors, restrained vocal, chorus opens into hope
```

---

### 3.5 Lonely / 孤独

| Field | Recommendation |
|---|---|
| BPM | 60–90 |
| Rhythm | sparse pulse, minimal drums, room for silence |
| Harmony | minor or ambiguous harmony |
| Instruments | solo piano, ambient pad, clean electric guitar, distant strings |
| Vocal | low male vocal, breathy female vocal, intimate vocal |
| Arrangement | lots of space, minimal layers, slow build |
| Production | atmospheric, distant, late-night |
| Good For | city night, solitude, introspection, emotional narration |
| Prompt Keywords | lonely, sparse, late-night, atmospheric, distant, intimate, minimal |

Example prompt phrase:

```text
lonely late-night atmosphere, sparse piano and ambient pads, minimal drums, intimate low vocal, spacious mix
```

---

### 3.6 Nostalgic / 怀旧

| Field | Recommendation |
|---|---|
| BPM | 75–115 |
| Rhythm | steady, familiar, moderate groove |
| Harmony | classic pop progressions, warm chords |
| Instruments | piano, clean guitar, vintage synths, soft drums |
| Vocal | warm vocal, crooner style, mature emotional vocal |
| Arrangement | classic verse-chorus structure, memorable hook |
| Production | vintage texture, tape warmth, retro reverb |
| Good For | childhood, youth, old friends, hometown, retro content |
| Prompt Keywords | nostalgic, vintage, retro texture, warm tape sound, classic pop feel |

Example prompt phrase:

```text
nostalgic retro pop feeling, warm tape texture, clean guitar, soft drums, memorable chorus, emotional vocal
```

---

### 3.7 Hopeful / 希望感

| Field | Recommendation |
|---|---|
| BPM | 85–120 |
| Rhythm | steady, forward-moving |
| Harmony | major key feeling, rising progressions |
| Instruments | piano, guitar, strings, soft drums, light synths |
| Vocal | clear vocal, warm emotional vocal, group vocals in final chorus |
| Arrangement | gradual build, bigger final chorus |
| Production | open, bright, uplifting |
| Good For | recovery, new beginning, graduation, brand optimism |
| Prompt Keywords | hopeful, uplifting, rising, open, positive, inspiring |

Example prompt phrase:

```text
hopeful and uplifting mood, medium tempo, rising chord progression, piano and guitar, drums and strings building into a bright final chorus
```

---

### 3.8 Uplifting / 振奋

| Field | Recommendation |
|---|---|
| BPM | 100–130 |
| Rhythm | driving rhythm, steady drums |
| Harmony | bright major chords |
| Instruments | drums, piano, guitar, synths, strings, claps |
| Vocal | powerful vocal, group backing vocals |
| Arrangement | clear build, strong chorus, energetic bridge |
| Production | polished, wide, radio-friendly |
| Good For | brand, campaigns, sports, graduation, corporate videos |
| Prompt Keywords | uplifting, inspiring, energetic, driving drums, big chorus, positive |

Example prompt phrase:

```text
uplifting pop anthem with driving drums, bright piano, energetic guitar, wide chorus, inspiring group backing vocals
```

---

### 3.9 Bright / 明亮

| Field | Recommendation |
|---|---|
| BPM | 105–130 |
| Rhythm | light, bouncy, upbeat |
| Harmony | major chords, simple catchy progression |
| Instruments | ukulele, guitar, bright piano, claps, light synths |
| Vocal | clear young vocal, cheerful vocal |
| Arrangement | hook appears early, short intro |
| Production | clean, sunny, playful |
| Good For | short videos, children, lifestyle, travel |
| Prompt Keywords | bright, cheerful, sunny, playful, catchy, light percussion |

Example prompt phrase:

```text
bright and cheerful pop track, upbeat tempo, catchy melody, hand claps, light guitar, sunny youthful vocal
```

---

### 3.10 Romantic / 浪漫

| Field | Recommendation |
|---|---|
| BPM | 65–100 |
| Rhythm | gentle groove, smooth feel |
| Harmony | lush chords, warm progressions |
| Instruments | piano, acoustic guitar, strings, soft R&B drums |
| Vocal | soft female vocal, smooth male vocal, duet |
| Arrangement | intimate verse, lush chorus |
| Production | warm, polished, close vocal |
| Good For | love songs, weddings, anniversaries |
| Prompt Keywords | romantic, tender, intimate, smooth, lush, heartfelt |

Example prompt phrase:

```text
romantic and tender pop ballad, smooth vocal, warm piano, acoustic guitar, soft strings, intimate verse and lush chorus
```

---

### 3.11 Dreamy / 梦幻

| Field | Recommendation |
|---|---|
| BPM | 60–100 |
| Rhythm | soft pulse, floating groove |
| Harmony | suspended chords, reverb-heavy harmony |
| Instruments | synth pads, reverb guitar, soft piano, bells |
| Vocal | ethereal female vocal, airy vocal |
| Arrangement | floating layers, slow development |
| Production | reverb, delay, wide stereo space |
| Good For | fantasy, romance, night, visual content |
| Prompt Keywords | dreamy, ethereal, floating, reverb, atmospheric, soft synth pads |

Example prompt phrase:

```text
dreamy ethereal atmosphere, floating synth pads, reverb guitar, soft piano, airy female vocal, spacious mix
```

---

### 3.12 Cinematic / 电影感

| Field | Recommendation |
|---|---|
| BPM | 65–120 |
| Rhythm | slow build or dramatic pulse |
| Harmony | emotional progressions, suspended tension |
| Instruments | piano, cinematic strings, orchestral percussion, brass, choir |
| Vocal | emotional vocal or wordless choir |
| Arrangement | gradual build, dramatic climax, wide outro |
| Production | wide, deep, dramatic, trailer-like if needed |
| Good For | video, documentary, brand film, personal story |
| Prompt Keywords | cinematic, emotional build, orchestral strings, wide soundstage, dramatic climax |

Example prompt phrase:

```text
cinematic emotional pop arrangement, piano intro, orchestral strings, deep drums, gradual build toward a dramatic final chorus
```

---

### 3.13 Epic / 史诗感

| Field | Recommendation |
|---|---|
| BPM | 80–130 |
| Rhythm | big drums, marching pulse, strong downbeats |
| Harmony | heroic, grand, rising |
| Instruments | orchestral percussion, brass, strings, choir, taiko drums |
| Vocal | choir, group vocals, powerful lead vocal |
| Arrangement | huge build, climax, final chorus or finale |
| Production | massive, wide, powerful |
| Good For | sports, games, trailers, ceremony, heroic themes |
| Prompt Keywords | epic, heroic, massive drums, choir, orchestral, triumphant, grand |

Example prompt phrase:

```text
epic heroic anthem with massive drums, orchestral strings, brass, choir, rising energy, powerful final climax
```

---

### 3.14 Powerful / 有力量

| Field | Recommendation |
|---|---|
| BPM | 95–145 |
| Rhythm | strong drums, driving rhythm |
| Harmony | bold, stable, rising |
| Instruments | electric guitar, drums, bass, brass, synth layers |
| Vocal | powerful male vocal, powerful female vocal, group chant |
| Arrangement | strong chorus, punchy transitions |
| Production | loud, polished, impactful |
| Good For | sports, campaigns, motivational songs |
| Prompt Keywords | powerful, bold, strong drums, anthemic, energetic, impactful |

Example prompt phrase:

```text
powerful anthemic arrangement, driving drums, electric guitars, bold vocal delivery, big memorable chorus
```

---

### 3.15 Energetic / 高能

| Field | Recommendation |
|---|---|
| BPM | 120–160 |
| Rhythm | fast groove, dance rhythm, active percussion |
| Harmony | bright or intense |
| Instruments | synths, drums, bass, electric guitar, percussion |
| Vocal | energetic vocal, chant, rap vocal |
| Arrangement | short intro, fast build, strong drop or chorus |
| Production | loud, punchy, modern |
| Good For | short videos, sports, workouts, parties |
| Prompt Keywords | energetic, high-energy, fast-paced, punchy drums, driving bass, explosive chorus |

Example prompt phrase:

```text
high-energy modern pop track, fast tempo, punchy drums, driving bass, bright synths, explosive chorus
```

---

### 3.16 Calm / 平静

| Field | Recommendation |
|---|---|
| BPM | 50–80 |
| Rhythm | minimal or no drums |
| Harmony | soft, slow-moving |
| Instruments | piano, ambient pads, acoustic guitar, soft strings |
| Vocal | soft, breathy, restrained |
| Arrangement | sparse, slow, gentle |
| Production | spacious, quiet, soothing |
| Good For | meditation, sleep, background music, reflective scenes |
| Prompt Keywords | calm, peaceful, minimal, soft piano, ambient pads, gentle, spacious |

Example prompt phrase:

```text
calm peaceful instrumental, slow tempo, soft piano, ambient pads, minimal percussion, spacious and soothing atmosphere
```

---

### 3.17 Premium / 高级感

| Field | Recommendation |
|---|---|
| BPM | 75–115 |
| Rhythm | restrained, clean, not too busy |
| Harmony | jazz-influenced chords, elegant progressions |
| Instruments | piano, upright bass, brushed drums, muted guitar, subtle synths |
| Vocal | smooth vocal, elegant vocal, restrained delivery |
| Arrangement | minimal but refined, careful transitions |
| Production | clean, polished, high-end, tasteful |
| Good For | luxury brand, fashion, coffee, city night, premium video |
| Prompt Keywords | elegant, premium, refined, tasteful, minimal, polished, jazz-influenced |

Example prompt phrase:

```text
elegant premium jazz-pop atmosphere, refined piano chords, brushed drums, upright bass, smooth restrained vocal, polished high-end production
```

---

### 3.18 Tech / 科技感

| Field | Recommendation |
|---|---|
| BPM | 90–125 |
| Rhythm | precise, pulsing, clean |
| Harmony | minimal, modern, sometimes minor |
| Instruments | synth pulses, digital pads, electronic drums, sub bass |
| Vocal | optional, clean vocal or no vocal |
| Arrangement | minimal, modular, clear build |
| Production | clean, futuristic, premium, digital |
| Good For | product video, AI, software, startup, tech brand |
| Prompt Keywords | futuristic, clean, minimal electronic, pulsing synths, digital texture, premium tech |

Example prompt phrase:

```text
clean futuristic electronic instrumental, pulsing synths, minimal beat, digital textures, premium tech product background
```

---

### 3.19 Suspense / 悬疑

| Field | Recommendation |
|---|---|
| BPM | 60–100 |
| Rhythm | slow pulse, ticking percussion, sparse hits |
| Harmony | minor, dissonant, unresolved tension |
| Instruments | low strings, dark synths, piano pulses, sub bass |
| Vocal | usually no vocals, or whispered spoken word if needed |
| Arrangement | gradual tension, no big release unless requested |
| Production | dark, spacious, tense |
| Good For | mystery, documentary, crime, dramatic video |
| Prompt Keywords | suspenseful, tense, dark, pulsing, mysterious, unresolved, cinematic |

Example prompt phrase:

```text
suspenseful cinematic instrumental, dark synth pulses, low strings, sparse percussion, unresolved tension, mysterious atmosphere
```

---

### 3.20 Playful / 俏皮

| Field | Recommendation |
|---|---|
| BPM | 100–135 |
| Rhythm | bouncy, light, syncopated |
| Harmony | bright major chords |
| Instruments | ukulele, pizzicato strings, claps, toy piano, bells |
| Vocal | cheerful vocal, children’s choir if needed |
| Arrangement | short, catchy, simple |
| Production | light, fun, colorful |
| Good For | children, ads, lifestyle, cute short videos |
| Prompt Keywords | playful, cute, bouncy, cheerful, fun, bright, simple melody |

Example prompt phrase:

```text
playful cheerful pop track, bouncy rhythm, ukulele, hand claps, toy piano, bright simple melody
```

---

## 4. Emotion-to-Use-Case Mapping

| Use Case | Recommended Emotions | Avoid |
|---|---|---|
| Short video BGM | bright, catchy, energetic, dreamy, healing | slow build with no hook |
| Personal story | warm, bittersweet, reflective, hopeful | overly commercial energy |
| Brand promo | uplifting, premium, bright, tech, cinematic | too sad, too dark |
| Luxury / fashion | premium, elegant, cool, minimal | overly busy, childish |
| Tech product | futuristic, clean, minimal, premium | acoustic-only rustic sound |
| Sports / competition | powerful, epic, energetic, triumphant | too soft, too slow |
| World Cup / football | epic, energetic, hopeful, Latin, stadium | intro too long, no chorus/chant |
| Wedding / anniversary | romantic, warm, tender, hopeful | aggressive drums |
| Graduation | bittersweet, hopeful, uplifting, nostalgic | too dark or cynical |
| Study / work BGM | calm, healing, lo-fi, warm, steady | vocals, big drops |
| Vlog / travel | bright, breezy, relaxed, nostalgic | dense dramatic climax |
| Documentary | cinematic, reflective, suspenseful, emotional | overly pop hook unless requested |
| Children’s education | playful, bright, simple, warm | dark, complex, intense |

---

## 5. Emotion-to-Instrumentation Quick Map

| Emotion | Primary Instruments | Avoid |
|---|---|---|
| Warm | piano, acoustic guitar, strings | harsh synths, aggressive drums |
| Healing | soft piano, pads, bells | loud snares, distorted guitars |
| Sad | piano, cello, soft strings | bright claps, bouncy rhythm |
| Bittersweet | piano, guitar, warm synths | overly dark drone |
| Lonely | solo piano, ambient pad, clean guitar | crowded arrangement |
| Nostalgic | vintage synth, clean guitar, warm drums | modern harsh EDM drops |
| Hopeful | piano, guitar, strings, drums | unresolved dark ending |
| Uplifting | drums, piano, guitar, strings | overly sparse arrangement |
| Bright | ukulele, claps, light synths | heavy low-end |
| Romantic | piano, strings, R&B drums | distorted guitars unless rock ballad |
| Dreamy | pads, reverb guitar, bells | dry production |
| Cinematic | strings, piano, orchestral drums | small mono mix |
| Epic | brass, choir, big drums, strings | weak drums |
| Powerful | electric guitar, drums, bass | thin rhythm section |
| Calm | piano, pads, soft guitar | high energy percussion |
| Premium | jazz piano, brushed drums, upright bass | cheap synth presets |
| Tech | synth pulse, electronic drums, sub bass | rustic acoustic-only sound |
| Suspense | low strings, dark synth, piano pulse | cheerful major chords |
| Playful | ukulele, claps, toy piano | dark pads, heavy reverb |

---

## 6. Emotion-to-Vocal Delivery Map

| Emotion | Recommended Vocal |
|---|---|
| Warm | natural emotional vocal, warm male vocal, soft female vocal |
| Healing | breathy soft vocal, clear gentle vocal |
| Sad | restrained emotional vocal, intimate vocal |
| Bittersweet | mature emotional vocal, reflective delivery |
| Lonely | low intimate vocal, breathy vocal, close-mic vocal |
| Nostalgic | warm mature vocal, retro crooner style if needed |
| Hopeful | clear vocal, uplifting final chorus |
| Uplifting | powerful vocal, group backing vocals |
| Bright | clear youthful vocal, cheerful delivery |
| Romantic | tender vocal, smooth R&B vocal, duet |
| Dreamy | ethereal female vocal, airy vocal |
| Cinematic | emotional lead vocal, wordless choir |
| Epic | choir, group chant, powerful lead |
| Powerful | strong vocal, raspy rock vocal, anthem vocal |
| Energetic | punchy vocal, rap vocal, chant vocal |
| Calm | soft restrained vocal, or instrumental only |
| Premium | smooth elegant vocal, restrained delivery |
| Tech | clean modern vocal, vocoder light texture, or no vocal |
| Suspense | no vocal, whispered spoken word only if needed |
| Playful | cheerful vocal, children’s choir |

---

## 7. Emotion-to-Arrangement Density

| Emotion | Arrangement Density | Development Strategy |
|---|---|---|
| Warm | medium | add strings and drums in chorus |
| Healing | low | keep spacious, subtle variations |
| Sad | low-medium | emotional but not crowded |
| Bittersweet | medium | start reflective, chorus opens |
| Lonely | low | leave silence and room tone |
| Nostalgic | medium | classic verse-chorus, vintage texture |
| Hopeful | medium-high | gradual build to final chorus |
| Uplifting | high | full chorus, group backing |
| Bright | medium | short intro, hook early |
| Romantic | medium | lush chorus, intimate verse |
| Dreamy | low-medium | layered reverb and pads |
| Cinematic | medium-high | slow build, dramatic climax |
| Epic | high | massive percussion, choir, brass |
| Powerful | high | strong rhythm section |
| Energetic | high | fast transitions, drop or big chorus |
| Calm | very low | minimal, ambient, slow changes |
| Premium | low-medium | refined, uncluttered |
| Tech | low-medium | precise, modular, clean |
| Suspense | low-medium | tension without full release |
| Playful | medium | short motifs, simple repetition |

---

## 8. Emotion Prompt Word Bank

### Positive / Bright

```text
bright, cheerful, sunny, joyful, playful, catchy, optimistic, youthful, lighthearted, feel-good
```

### Warm / Human

```text
warm, heartfelt, intimate, sincere, comforting, gentle, organic, natural, human, tender
```

### Sad / Reflective

```text
melancholic, bittersweet, reflective, lonely, fragile, intimate, restrained, emotional, late-night
```

### Hope / Growth

```text
hopeful, uplifting, inspiring, rising, resilient, forward-moving, encouraging, open, positive
```

### Powerful / Epic

```text
powerful, epic, heroic, triumphant, massive, cinematic, bold, anthemic, stadium-sized, grand
```

### Dream / Space

```text
dreamy, ethereal, floating, atmospheric, spacious, reverb-heavy, celestial, hazy, immersive
```

### Premium / Modern

```text
premium, elegant, refined, clean, minimal, polished, tasteful, sophisticated, high-end, stylish
```

### Dark / Suspense

```text
dark, tense, suspenseful, mysterious, brooding, ominous, unresolved, pulsing, cinematic tension
```

### Tech / Future

```text
futuristic, digital, sleek, precise, minimal electronic, pulsing, synthetic, clean, innovative
```

---

## 9. Emotion Conflict Rules

Some user requests may contain emotional conflicts. The skill should resolve them instead of blindly combining incompatible terms.

### 9.1 Warm + Sad

Use:

```text
bittersweet, warm sadness, emotional but hopeful
```

Avoid:

```text
happy and sad at the same time
```

### 9.2 Epic + Healing

Use:

```text
cinematic healing, spacious orchestral build, emotional but gentle
```

Avoid overly massive battle drums unless the user wants grandeur.

### 9.3 Premium + Playful

Use:

```text
stylish playful, light luxury, elegant upbeat groove
```

Avoid childish toy sounds unless requested.

### 9.4 Tech + Warm

Use:

```text
warm futuristic, human-centered tech, soft synths with organic piano
```

Avoid cold industrial textures unless requested.

### 9.5 Sad + Energetic

Use:

```text
emotional fast pop-rock, bittersweet dance-pop, high-energy heartbreak song
```

This is good for breakup dance-pop, pop-punk, or emo rock.

### 9.6 Calm + Short Video Hook

Use:

```text
gentle but catchy hook, soft loop-friendly melody
```

Avoid long slow intros.

---

## 10. Vocal Song Emotion Prompt Formulas

### 10.1 General Formula

```text
Create a [genre] song with a [emotion] mood. Use [vocal style] vocals. The tempo should be [BPM / tempo feel]. The arrangement should include [instruments]. Start with [intro arrangement], then build into [chorus arrangement]. The emotional curve should move from [starting emotion] to [ending emotion]. The chorus should feel [chorus emotion]. The song is intended for [use case].
```

### 10.2 Warm Personal Song

```text
Create a warm and heartfelt Chinese pop ballad. Use natural emotional male vocals. Medium-slow tempo, soft piano and acoustic guitar in the verse, with gentle strings and soft drums entering in the chorus. The emotional curve should move from quiet reflection to hopeful acceptance. The chorus should be memorable, sincere, and suitable for personal sharing.
```

### 10.3 Epic Sports Song

```text
Create an epic stadium anthem with a triumphant and energetic mood. Use powerful group vocals and chant-like backing vocals. Medium-fast tempo, driving drums, electric guitars, brass, and orchestral percussion. The song should build quickly into a big chorus suitable for crowd singing and sports highlight videos.
```

### 10.4 Premium Brand Song

```text
Create a premium and uplifting cinematic pop song. Use clean modern vocals with restrained emotional delivery. Medium tempo, elegant piano, subtle synth textures, polished drums, and cinematic strings. The arrangement should feel refined, optimistic, and high-end, suitable for a brand film.
```

---

## 11. Instrumental Emotion Prompt Formulas

### 11.1 General Instrumental Formula

```text
Create a [genre] instrumental track with a [emotion] mood. Instrumental only, no vocals, no rap, no spoken words. The tempo should be [BPM / tempo feel]. Use [main instruments] with [production texture]. The arrangement should [arrangement strategy]. Make it [loop-friendly / suitable for background music / suitable for video editing].
```

### 11.2 Lo-fi Healing Instrumental

```text
Create a healing lo-fi hip-hop instrumental. Instrumental only, no vocals, no rap, no spoken words. Slow tempo around 75 BPM, soft piano chords, mellow bass, dusty drums, vinyl crackle, and warm tape texture. Keep the arrangement calm, loop-friendly, and suitable for studying or late-night background music.
```

### 11.3 Tech Product Instrumental

```text
Create a clean futuristic electronic instrumental for a tech product video. Instrumental only, no vocals. Medium tempo around 105 BPM, pulsing synths, minimal electronic drums, soft sub bass, digital textures, and a polished premium mix. The arrangement should feel modern, precise, optimistic, and non-intrusive.
```

### 11.4 Cinematic Emotional Instrumental

```text
Create a cinematic emotional instrumental. Instrumental only, no vocals. Slow-to-medium tempo, soft piano intro, warm strings, subtle orchestral percussion, and a gradual emotional build. The track should feel reflective at first, then hopeful and wide in the final section, suitable for documentary or personal story videos.
```

---

## 12. Fixed Negative Prompts by Emotion

These can be added when needed.

| Target Emotion | Negative Prompt |
|---|---|
| Healing | avoid aggressive drums, harsh synths, loud drops |
| Warm | avoid cold industrial textures, harsh distortion |
| Sad | avoid cheerful claps, playful ukulele |
| Premium | avoid childish sounds, cheap synth presets, overly busy arrangement |
| Tech | avoid rustic folk-only instrumentation unless hybrid requested |
| Epic | avoid thin drums, small arrangement |
| Calm | avoid vocals, big drops, intense percussion |
| Instrumental BGM | no vocals, no rap, no spoken words, no lead singing |
| Short video hook | avoid long intro, bring the hook early |
| Brand music | avoid overly sad mood, avoid dark unresolved ending |

---

## 13. Skill Routing Logic

### 13.1 If the User Gives Only an Emotion

Example:

> I want something healing.

Ask:

```text
Do you want a vocal song or an instrumental background track?
What is the use case: short video, personal song, brand, study, event, or something else?
```

### 13.2 If the User Gives Theme + Emotion

Example:

> A song about middle-aged people still trying, warm but sad.

Infer:

```text
Theme: middle-aged people still trying
Emotion: bittersweet, warm sadness, hopeful
Recommended genre: Chinese pop ballad / acoustic folk-pop
BPM: 75–95
Vocal: mature emotional male vocal or soft female vocal
Arrangement: piano + acoustic guitar + strings, restrained verse, hopeful chorus
```

### 13.3 If the User Gives Scene + Emotion

Example:

> Background music for a tech product video, premium and futuristic.

Infer:

```text
Type: instrumental
Genre: minimal electronic / corporate electronic
BPM: 95–115
Instruments: synth pulses, soft electronic drums, sub bass, digital pads
Mood: premium, clean, futuristic
Negative: no vocals, no rap, no spoken words
```

### 13.4 If User Requests Multiple Emotions

Choose one primary emotion and one secondary emotion.

Example:

> Warm, lonely, hopeful.

Use:

```text
Primary: warm
Secondary: lonely + hopeful
Prompt: warm and lonely at first, gradually becoming hopeful
Energy curve: intimate verse -> uplifting chorus
```

---

## 14. Quick Reference: Emotion to Prompt Keywords

| Chinese Emotion | English Prompt Keywords |
|---|---|
| 温暖 | warm, heartfelt, intimate, gentle, organic |
| 治愈 | healing, soothing, peaceful, comforting, airy |
| 伤感 | melancholic, emotional, intimate, minor-key feeling |
| 苦甜 | bittersweet, nostalgic, reflective, hopeful |
| 孤独 | lonely, sparse, late-night, atmospheric |
| 怀旧 | nostalgic, retro, vintage, warm tape texture |
| 希望 | hopeful, uplifting, rising, open, positive |
| 振奋 | inspiring, uplifting, energetic, driving |
| 明亮 | bright, cheerful, sunny, youthful |
| 浪漫 | romantic, tender, lush, smooth, intimate |
| 梦幻 | dreamy, ethereal, floating, atmospheric |
| 电影感 | cinematic, emotional build, dramatic, wide |
| 史诗感 | epic, heroic, massive, triumphant |
| 有力量 | powerful, bold, anthemic, impactful |
| 高能 | energetic, fast-paced, punchy, explosive |
| 平静 | calm, peaceful, minimal, spacious |
| 高级感 | premium, elegant, refined, polished |
| 科技感 | futuristic, clean, digital, sleek |
| 悬疑 | suspenseful, tense, mysterious, dark |
| 俏皮 | playful, cute, bouncy, cheerful |

---

## 15. Notes for Skill Implementation

When the final skill generates a prompt:

1. Do not treat emotion as a decorative adjective only.
2. Convert emotion into tempo, instrumentation, vocal delivery, and arrangement density.
3. If the user requests instrumental music, remove all vocal fields and add `instrumental only, no vocals`.
4. If the user requests background music, prioritize non-intrusive arrangement and loopability.
5. If the user requests a song for sharing, prioritize chorus memorability and emotional clarity.
6. If emotions conflict, create an emotional arc rather than stacking all emotions together.
7. Always map at least one emotional word to a concrete musical behavior.

---

## 16. Version Notes

v0.1 includes:

- core emotional dimensions
- emotion-to-BPM mapping
- emotion-to-instrumentation mapping
- emotion-to-vocal mapping
- emotion-to-arrangement-density mapping
- vocal song prompt formulas
- instrumental prompt formulas
- emotion conflict rules
- skill routing logic

Future versions can add:

- Chinese lyric language style mapping
- emotion-to-rhyme strategy
- emotion-to-song-structure mapping
- platform-specific Suno / Udio parameter suggestions
- commercial scene-specific emotion presets
