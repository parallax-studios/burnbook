# BURNBOOK — Sound Design Document

**Version:** 1.0
**Author:** ECHO (Sound Designer & Composer)
**Date:** 2026-02-07
**Status:** Pre-Production

---

## 0. SONIC IDENTITY STATEMENT

Close your eyes.

You're alone in a production suite at 3 AM. The fluorescent lights hum their constant 120Hz dirge. The edit bay monitors emit a low electronic whisper — the sound of pixels holding still. You hear the distant click-whir of a tape deck rewinding somewhere down the hall. A phone rings once, twice, stops. Outside the monitors, cast members are speaking — but you don't hear them directly. You hear them through production audio, compressed and intimate, piped through studio monitors with that specific tinny proximity of reality TV surveillance.

Your keyboard clacks — mechanical, deliberate, surgical. Each keystroke is a decision. Each spacebar hit is commitment. The edit timeline scrubs with the granular texture of magnetic tape, even though everything is digital now. When you drop a segment into place, it lands with a satisfying chunk — not destructive, but definitive. You are building something. You are dismantling something else.

The sound of BURNBOOK is the sound of mediation. Nothing in this game is raw. Everything passes through equipment, through systems, through you. The hum is constant. The machines never sleep. And underneath it all, the frequency of complicity — the sound you start to hear only when you listen for it, which is the sound of silence where someone's pain used to be.

**BURNBOOK sounds like the machinery of spectacle.**

Audio isn't polish. Audio IS game feel. The player should be able to close their eyes and understand exactly where they are, what they're doing, and how it feels to do it.

---

## 1. SONIC PALETTE

### 1.1 Core Sonic Identity

**Tone:** Cold institutional infrastructure meeting warm human vulnerability. The contrast is everything.

**Texture:**
- **The Machine Layer:** Clean, precise, sterile. Digital clicks, mechanical confirmations, electronic hums. The production equipment is professional-grade but slightly dated — this is 2005 technology, not cutting-edge but not vintage. Digital with a hint of analog nostalgia.
- **The Human Layer:** Compressed vocal intimacy. Every voice sounds like it's coming through a lavalier mic and studio monitor — slightly artificial, slightly too close, slightly performative even when authentic. The uncanny proximity of reality TV audio.
- **The Space Layer:** Institutional ambiance. Fluorescent hum. HVAC rumble. The acoustic signature of windowless rooms with acoustic tile ceilings and carpet over concrete. Rooms designed to absorb sound, not generate it.

**Frequency Spectrum:**

| Range | Content | Emotional Purpose |
|---|---|---|
| **Sub (20-60Hz)** | HVAC rumble, edit bay computer fans, the barely-perceptible pressure of late-night isolation | Unease, fatigue, persistence |
| **Low (60-250Hz)** | Fluorescent hum (120Hz fundamental), monitor CRT buzz, tape deck motors | The infrastructure. The machine never stops. |
| **Mid-Low (250-500Hz)** | Male vocal fundamentals, keyboard typing, edit timeline scrubbing | Human action interfacing with machinery |
| **Mid (500Hz-2kHz)** | Female vocal fundamentals, dialog intelligibility, paper rustling | The intelligence layer. Where information lives. |
| **Mid-High (2-5kHz)** | Vocal presence, production headset crispness, phone ring, alert chimes | Clarity, urgency, attention |
| **High (5-12kHz)** | Tape hiss, monitor static, the specific sibilance of compressed reality TV audio | Surveillance texture. The sound of watching. |
| **Air (12-20kHz)** | Room tone, the "breath" of empty production spaces | Psychological space. Emptiness or presence. |

**Reference Tracks (for the team, not for literal reproduction):**

1. **Trent Reznor & Atticus Ross — "The Social Network" OST** — Specifically "Hand Covers Bruise" and "In Motion." The way they make electronic minimalism feel emotionally devastating. Cold precision that becomes oppressive.

2. **Mica Levi — "Under the Skin" OST** — The use of silence, negative space, and dissonant strings to create unease without horror. Making the familiar feel alien.

3. **Ben Salisbury & Geoff Barrow — "Ex Machina" OST** — Clean electronic ambiance that sounds like the interior of a mind and a machine simultaneously. Thoughtful, cold, elegant.

4. **Cliff Martinez — "Contagion" OST** — Sterile institutional minimalism. The acoustic signature of professionalism applied to something fundamentally disturbing.

5. **Johann Johannsson — "Sicario" OST** — The use of sub-bass pressure to create dread. The way low frequencies communicate "something is wrong" without melodic information.

6. **Mark Korven — "The Lighthouse" OST** — Not for melodic content, but for the use of repetitive mechanical drones and industrial textures to evoke psychological stress.

**Silence Map (where deliberate silence creates impact):**

Silence in BURNBOOK is never accidental. It's always a choice, and it always means something.

- **The Burn Book Open:** When you first open a cast member's dossier, there's a 0.5-second void of pure silence before the ambient production suite returns. This micro-silence creates a psychological pocket — you are entering private information. The world pauses.

- **The "Air This?" Moment:** When the player hovers over the final "Submit Episode" button, the UI ambiance drops to near-silence. Just the 120Hz fluorescent hum and distant HVAC. No confirmation chirps, no encouraging feedback. The silence asks: are you sure? Once you commit, sound returns.

- **Post-Fallout Events:** When a legal notice arrives or a cast member reaches PI < 20, the notification is preceded by 2 seconds of dead silence. The production suite ambiance cuts entirely, then the event sound triggers in that void. The silence makes the consequence land harder.

- **Between Seasons:** In the inter-season management phase, the production suite ambiance is 40% quieter. The machinery is idling. Everyone has gone home. It's just you and the archive of what you've done.

- **The Ghost Space in Confessionals:** When a cast member says something devastatingly honest in a confessional — the game's emotional detection system flags it — there's a 1-second silence afterward. No production noise. No edit bay clicking. Just the weight of what was said.

---

## 2. SFX DESIGN — ORGANIZED BY CATEGORY

### 2.1 UI / INTERFACE LAYER

**Design Philosophy:** Every click is a decision. Every interaction should have tactile audio weight. The UI sounds clinical, professional, slightly dated (2005 digital design tools). Think Avid, Final Cut Pro 6, Pro Tools 7 — pre-cloud, pre-touchscreen. Everything is mouse and keyboard.

#### Primary Interactions

| SFX | Description | Frequency Content | Dynamic Range | Implementation Notes |
|---|---|---|---|---|
| **Click (default)** | Mouse click on standard UI element | 2-4kHz transient, no tail | -18dB | Slightly plastic. Not satisfying, just confirmatory. |
| **Click (burn book page)** | Turning a page in the dossier | 500Hz-3kHz, papery texture, 0.3s tail | -15dB | Layered: paper rustle + subtle tab-click. Needs to feel physical. |
| **Drag (footage clip)** | Dragging a video segment in edit bay | Mid-range scrape, continuous while dragging | -20dB while moving | Pitch shifts down slightly as you drag (Doppler-ish effect). |
| **Drop (footage clip)** | Dropping segment into timeline | 200-800Hz "chunk," 0.2s decay | -12dB | This is THE sound. Satisfying. Definitive. The Tetris block placement of this game. |
| **Scrub (timeline)** | Scrubbing through footage timeline | Granular texture, pitch follows scrub speed | Variable | Synthesized from pitched noise + time-stretched audio artifacts. Should sound like old tape scrub. |
| **Hover (button)** | Mousing over interactive element | Subtle 3kHz transient, barely perceptible | -28dB | Should be felt more than heard. Subliminal confirmation you're on a hot zone. |
| **Type (keyboard)** | Typing text (chyrons, notes, memos) | Mechanical keyboard clicks, randomized pitch/timing | -16dB per keystroke | Recorded from actual Cherry MX Blues or similar. Each keystroke slightly different to avoid machine-gun repetition. |
| **Confirm (action)** | Confirming a major decision (cast, air episode, etc.) | Two-tone chime: 800Hz + 1200Hz, 0.8s decay | -10dB | Slightly ominous. Not cheerful. Professional, not playful. |
| **Warning (alert)** | Legal risk, PI threshold, budget warning | Single 1.5kHz pulse, staccato, with slight distortion | -8dB | Jarring. Should make you stop what you're doing. |
| **Cancel/Back** | Backing out of a screen | Soft descending two-note: 900Hz → 600Hz | -20dB | Implies "undoing" or "stepping back." Non-aggressive. |

#### Secondary Interactions

| SFX | Description | Implementation |
|---|---|---|
| **Burn Book Open** | Opening the full dossier interface | Vinyl folder slap + paper shuffle, 0.5s |
| **Burn Book Close** | Closing dossier | Softer folder close, 0.3s |
| **Tab Switch** | Switching between burn book tabs | Quick paper flick, 0.1s, alternating pitch |
| **Highlight Text** | Selecting/highlighting intelligence | Subtle marker-on-paper squeak, barely audible |
| **Post-It Attach** | Adding a note to burn book | Adhesive peel, then paper tap, 0.4s total |
| **Sticky Note Remove** | Removing a note | Faster peel, slightly sticky resistance |
| **Checkmark Appear (correct prediction)** | When burn book intel proves accurate | Pen scratch + soft positive chirp (1.2kHz, 0.3s) |
| **Red X Appear (wrong prediction)** | When intel proves wrong | Harsh pen cross-out + descending buzz (800Hz, 0.4s) |
| **Confidence Decay Visual Update** | Text graying out as intel ages | Very quiet paper aging sound, crackling texture |
| **Coffee Ring Stamp** | Random ambient detail on documents | Liquid settle sound, rare ambient event |

#### Modal Windows & Transitions

| SFX | Description | Implementation |
|---|---|---|
| **Modal Open (ratings report, legal notice)** | Document slides onto desk | Paper slide on wood, 0.6s, slight friction texture |
| **Modal Close** | Document removed | Reverse of open, faster (0.4s) |
| **Screen Transition (enter edit bay, etc.)** | Moving between major game modes | Subtle room tone shift + monitor state change (CRT whine pitch shift) |
| **Budget Update** | Money in/out notification | Old dot-matrix printer sound, 0.8s burst |
| **Reputation Change** | Showrunner rep increases/decreases | Subtle ascending/descending synth pad, 2s fade |

---

### 2.2 PRODUCTION SUITE AMBIANCE

**Design Philosophy:** The production suite is a character. It's always present. The ambiance is layered, not monolithic — multiple sound sources at different distances and frequencies that combine into a cohesive "this is where you are" signature.

#### Core Ambiance Layers (Always Active)

| Layer | Description | Frequency | Volume | Variation |
|---|---|---|---|---|
| **Fluorescent Hum** | 120Hz fundamental + harmonics (240Hz, 360Hz) | 120Hz + overtones | -35dB | Occasionally flickers (slight amplitude modulation every 45-90s) |
| **HVAC Rumble** | Low-frequency air circulation | 40-80Hz | -38dB | Cycles on/off on 8-12 minute intervals. When off, room feels "too quiet" briefly. |
| **Computer Fan Whir** | Edit bay workstation cooling fans | 200-600Hz, broadband | -40dB | Constant. Slight pitch variation (±5%) based on system load (more edit bay activity = slightly louder/higher) |
| **Monitor CRT Whine** | High-frequency electronic whine from monitors | 15kHz (barely perceptible, age-dependent) | -42dB | Only audible when you focus on it. Creates subliminal "electronics are on" presence. |
| **Distant Office Sounds** | Muffled activity beyond the edit bay | Varies | -45dB | Footsteps in hallway, distant phone ring (every 3-5 min), muffled voices (unintelligible), door close (rare) |

#### Adaptive Ambiance

The production suite ambiance responds to time of day and stress state:

**Time of Day Variation:**
- **Morning (8am-12pm):** More distant office sounds, occasional coffee machine gurgle, phones ringing more frequently, footsteps passing. The building is awake.
- **Afternoon (12pm-6pm):** Peak activity. Office sounds at normal level. Fluorescents at full brightness (slightly brighter hum).
- **Evening (6pm-10pm):** Office sounds decrease. Longer gaps between distant events. Fluorescents unchanged (they never turn off).
- **Night (10pm-6am):** Minimal distant sounds. One phone ring every 5-10 minutes (no one answers). HVAC sounds louder in the silence. The building is asleep. You are not.

The game tracks in-world time and shifts ambiance accordingly. Late-night sessions feel isolating.

**Stress/Tension State:**

When the player is facing high-stakes decisions (submitting an episode with high legal risk, managing a PI crisis, approaching cancellation):
- Sub-bass layer (30-50Hz) subtly increases +3dB
- Fluorescent hum acquires a barely-perceptible pulse (amplitude modulation at 0.2Hz)
- Monitor whine increases +2dB
- Distant office sounds decrease -6dB (the world feels farther away)

This is subliminal. The player shouldn't consciously notice, but they should *feel* the pressure.

#### Special Ambiance Zones

**The Confessional Monitor (when watching cast confessionals):**
- Production suite ambiance drops -12dB
- Add subtle room tone from the confessional booth itself (smaller space, different reverb)
- Add almost-inaudible AC hum from the confessional (single-room HVAC unit, 180Hz)
- The player is "inside" the confessional space acoustically

**The Burn Book Focus (when dossier is open and active):**
- Production suite ambiance drops -8dB
- Add very quiet paper texture ambiance (pages settling, document breathing)
- Reduce high-frequency content (like putting on headphones — world narrows)
- When you close the burn book, the full ambiance returns (slight "coming up for air" feeling)

**Between Seasons (inter-season management):**
- All ambiance reduced by -10dB globally
- HVAC off
- No distant office sounds
- Just fluorescent hum and computer fans
- Reverb increases slightly (the space feels emptier)
- Occasional distant building settling creaks

---

### 2.3 SITUATION ENGINE — SCENE AUDIO

**Design Philosophy:** Scenes are surveillance. The cast members are being recorded, and you're listening to production audio — not raw sound. Everything is mic'd, compressed, and piped through studio monitors. The audio signature is "reality TV production sound" — intimate, compressed, slightly artificial.

#### Cast Member Voices

**Not Voice Acted (Per Design Document):** Cast dialog is text-based. But we still need vocal presence for authenticity.

**Vocal Textures (ambient vocal presence):**
- **Conversational Murmur:** When cast members are talking but not in focus, layer in non-verbal vocal textures: "mmhm," laughter, sighs, inhales. Recorded material, not synthesized. Feels like people talking without intelligible words.
- **Emotional Vocal Cues:** When drama spikes, add non-verbal vocalizations: sharp inhale (surprise), growl (anger), high-pitched catch (about to cry), derisive laugh. These accent the text without requiring VO.

These textures play at -20dB, mostly subliminal. They make the scenes feel inhabited.

#### Scene Environmental Sound

Scenes take place in specific locations. Each location has distinct environmental ambiance:

| Location | Base Ambiance | Special Elements | Acoustic Character |
|---|---|---|---|
| **Dinner Table** | Silverware clinks, glass touches, chair creaks | Wine pour, ice in glass, plate scrape | Medium reverb, intimate |
| **Hot Tub** | Water bubbles (jets), low rumble from pump | Water movement when someone shifts, steam hiss | High ambient noise, hard to hear (realistic) |
| **Shared Bedroom** | Very quiet room tone, fabric rustle, bed creaks | Suitcase zip, drawer open, door close | Dry, intimate, whisper-level |
| **Competition Arena** | Outdoor ambiance OR large room reverb | Equipment sounds, audience reactions (if applicable), whistle/buzzer | Larger space, more reverb |
| **Confessional Booth** | Isolated room tone, single-camera motor whir | Chair leather creak, clothing rustle | Dead dry (acoustic treatment), claustrophobic |
| **Garden/Patio** | Light outdoor ambiance (subtle birds, breeze), less controlled | Wind in plants, distant traffic (barely), ice in drink | Natural reverb, less compressed |
| **Kitchen** | Appliance hum (fridge), water drip, cabinet close | Knife on cutting board, pan clatter, fridge open | Medium reverb, homey but tense |
| **Isolation Room** | Extreme silence, just HVAC and room tone | The absence of sound is notable | Reverb-less, oppressive |

**Production Audio Signature:**

All scene audio is filtered through a "production monitor" signal chain:
1. **Lavalier Mic Coloration:** Slight proximity effect on voices (boosted low-mids), high-frequency roll-off above 10kHz
2. **Broadcast Compressor:** Heavy dynamic range compression (8:1 ratio, fast attack) — makes whispers audible, makes shouts controlled
3. **Subtle Tape Saturation:** Very light harmonic distortion, implies the audio passed through recording equipment
4. **Studio Monitor EQ:** Slight mid-range emphasis (1-3kHz), creates that "listening through speakers" quality even though the player is using headphones

The player should feel like they're listening to a recording, not present in the room. This is crucial. Mediation is the point.

#### Drama Event Sounds

When drama spikes (the Situation Engine flags a moment as DV > 65), audio responds:

- **Pre-Spike Tension:** 2 seconds before the spike, subtle sound design layers in: low pad (100Hz sine wave, barely audible), increased background silence (ambiance dips -4dB), slight high-pass filter on voices (dialog feels thinner, more fragile)
- **Spike Moment:** No musical sting (yet — that's for the edit). But we do: sudden ambiance cut (-10dB drop), vocal texture emphasis (the gasp or inhale or silence that precedes the confrontation), then ambiance rushes back
- **Post-Spike Decay:** Ambiance returns to normal over 3 seconds. Room tone feels "heavier" — add subtle low-frequency pad that fades out.

These are not melodramatic. They're subtle reality-TV production techniques. A skilled reality producer knows how to "feel" when a moment is happening. We're replicating that instinct sonically.

#### Multi-Camera Audio

Scenes are viewed on a multi-camera monitor (four feeds). Each camera has slightly different audio:

- **Camera 1 (Wide):** Full ambiance, balanced mix, all cast audible
- **Camera 2 (Close-up A):** Favors one cast member's lav mic, their voice +6dB relative to others
- **Camera 3 (Close-up B):** Favors another cast member, their voice +6dB
- **Camera 4 (Coverage):** Different angle, slightly different room tone (reverb varies by camera position)

When the player switches cameras (click between feeds), the audio mix shifts smoothly (0.3s crossfade) to match the camera's perspective. This is subtle but creates presence — the world sounds different depending on what you're focusing on.

#### Mid-Scene Intervention Sounds

When the player uses mid-scene intervention tools:

- **Producer Enters Scene:** Walkie-talkie chirp (brief squelch, 2kHz), footsteps (muffled, approaching), door open
- **Music Change (environmental music):** Smooth crossfade, no UI sound (the change happens diegetically in the scene)
- **Twist Introduced (surprise guest arrival):** Door knock or doorbell (diegetic), gasps from cast (vocal texture), then scene continues

These are diegetic sounds that happen "in the world" of the scene, not UI sounds.

---

### 2.4 EDIT BAY — EDITORIAL AUDIO

**Design Philosophy:** The edit bay is where you wield power. Every action here should feel like surgery — precise, consequential, irreversible. The sounds are sharper, more defined than anywhere else in the game. This is where you're most awake.

#### Timeline Editing

| SFX | Description | Feel |
|---|---|---|
| **Segment Select** | Clicking a footage clip in stockpile | Clean high transient (3kHz), 0.1s, like selecting a scalpel |
| **Segment Drag** | Dragging clip to timeline | Continuous granular scrape, pitch shifts with drag speed |
| **Segment Drop (into timeline)** | **THE sound of BURNBOOK** | Deep satisfying "chunk" (200-800Hz), 0.3s decay, tactile finality. This needs to feel GOOD. |
| **Segment Remove** | Deleting a segment from timeline | Reverse of drop sound, ascending pitch, 0.2s, like lifting something off |
| **Segment Reorder** | Moving segments within timeline | Quick plastic slide, 0.15s, efficient |
| **Timeline Scrub (playback head)** | Dragging playback head through timeline | Granular texture, emulates analog tape scrub, pitch/speed linked |
| **Play (preview segment)** | Pressing play to preview | Single beep (1kHz, 0.1s), then audio plays through production monitors |
| **Pause (preview)** | Pausing playback | Same beep, slightly lower pitch (900Hz) |
| **Jump to Next Segment** | Keyboard shortcut to skip forward | Quick ascending chirp (600Hz → 1.2kHz, 0.1s) |
| **Jump to Previous Segment** | Skip backward | Descending chirp (1.2kHz → 600Hz, 0.1s) |

#### Music Cue Selection

The player chooses music cues from a library. The UI interaction:

- **Cue Library Open:** Soft vinyl crate slide (implies physical media), 0.4s
- **Cue Hover:** 0.5s preview of the music cue plays (looping), very quiet (-30dB)
- **Cue Select:** Digital boop (confirming selection), music preview fades out
- **Cue Apply to Segment:** The music "locks in" with a soft click + reverb tail (like dropping a needle on vinyl but digital)
- **Cue Remove:** Soft scratch/lift sound (0.2s)

#### Confessional Overlay

- **Confessional Drag:** Vocal waveform texture (synthesized from noise), follows mouse
- **Confessional Drop (onto segment):** Two-layer sound: paper overlay (the visual metaphor) + vocal "lock" (subtle voice transient)
- **Confessional Preview:** Plays the confessional audio through production monitors (filtered, compressed, intimate)

#### Chyron Writing

- **Chyron Field Open:** Soft keyboard activate sound (mechanical switch)
- **Typing Chyron Text:** Same mechanical keyboard as elsewhere, but feels more deliberate (these words will be broadcast)
- **Chyron Confirm:** Text "burns in" with subtle static crackle (0.3s)

#### Episode Quality Score Update

As the player edits, the real-time quality score updates. Each update:

- **Score Increases:** Subtle ascending tone (barely perceptible, 800Hz → 1kHz, 0.5s)
- **Score Decreases:** Subtle descending tone (1kHz → 800Hz, 0.5s)
- **Threshold Crossed (e.g., "Gripping Television" achieved):** Slightly more pronounced two-tone chime (not celebratory, just confirmatory)

#### Submit Episode

The most important button in the game.

- **Hover Over Submit:** All edit bay ambiance drops -15dB. Fluorescent hum becomes prominent. Silence asks: are you sure?
- **Click Submit (before confirmation):** Deep button press (400Hz, mechanical resistance texture)
- **Confirmation Prompt Appears:** Paper slide + soft warning tone (sustained 900Hz, 0.8s)
- **Confirm Submission:** Three-stage sound:
  1. Heavy mechanical CLUNK (finality) — 200Hz, 0.3s
  2. Tape deck engage sound (whir + click) — 0.5s
  3. Network upload tone (series of ascending beeps, implies transmission) — 2s

  The episode is gone. It's airing. You can't take it back.

- **Cancel Submission:** Soft descending tone, tension releases

---

### 2.5 RATINGS & CONSEQUENCES — FEEDBACK AUDIO

**Design Philosophy:** Feedback arrives as physical objects in your world — documents landing on your desk, phones ringing, monitors displaying data. Every feedback event is a minor intrusion into your workflow. Some are welcome. Some are not.

#### Ratings Report Delivery

- **Report Arrives:** Document slides onto desk from off-screen (paper on wood, 0.8s), lands with slight slap (not aggressive, just present)
- **Report Open:** Paper unfold (if folded) or page flip, 0.5s
- **Nielsen Number Reveal:** Old dot-matrix printer sound printing the number in real-time (1.5s), each digit clicks into place
- **Segment Satisfaction Bars Fill:** Soft rising tone per segment (staggered), each bar "fills" with a quiet mechanical ratchet sound
- **Advertiser Confidence Update:** Cash register cha-ching (if positive) or drawer close (if negative) — subtle, not cartoonish
- **Network Satisfaction Score:** Pen scratch as the network exec hand-writes their score on the document
- **Social Media Scroll:** Quiet keyboard/mouse sounds as the feed scrolls, occasional notification pings (distant, from the simulated internet)

#### Fallout Events

These are intrusive. They interrupt workflow.

**Cast Member PI Crisis (threshold event):**
1. **Pre-Alert Silence:** 2 seconds of dead air (all ambiance cuts)
2. **Alert Tone:** Single harsh pulse (1.5kHz, distorted, 0.3s) — unmistakable
3. **Notification Appears:** Paper slam on desk (sudden, louder than usual, -8dB)
4. **Details Reveal:** If opened, paper unfolds with trembling texture (cast member is breaking)

**Legal Notice:**
1. **Silence:** 2 seconds
2. **Alert Tone:** Lower, more ominous (800Hz, sustained 1s)
3. **Envelope Slide:** Arrives in an envelope (paper slide, thicker texture)
4. **Envelope Open:** Tearing paper (slow, deliberate, 1.2s) — you don't want to open this but you have to

**Tabloid Story Breaks:**
1. **TV Monitor in Office Activates:** Static burst, then low tabloid-TV music (diegetic, from the office TV)
2. **Headline Appears on Screen:** Typewriter clack-clack-clack as headline types out
3. **Reputation Damage Calculation:** Descending synth tone (dramatic, almost comical, but the consequence is real)

**Cast Member Walkoff:**
1. **Pre-Alert Silence:** 2 seconds
2. **Walkie-Talkie Squelch:** "We have a situation" (voice filter, distant)
3. **Notification:** Heavy door slam sound (diegetic, from the set) + paper report lands on desk
4. **Details:** If opened, the cast member's burn book page automatically opens with torn/damaged visual, paper ripping sound

**Scandal Event:**
1. **Phone Ring:** Office phone, insistent, three rings
2. **Phone Pickup (automatic):** Handset lift, brief silence
3. **Network Executive Voice (filtered):** "We need to talk." (Voice effect: phone line coloration, slightly distorted)
4. **Notification Modal:** Appears with no sound (the silence is the weight)

#### Positive Feedback Events

Not everything is bad.

**High Ratings Spike:**
- Champagne cork pop (distant, diegetic, from the office)
- Soft celebratory chatter (muffled voices, unintelligible but positive)
- Nielsen number prints with slightly more energetic printer sound

**Cultural Moment Achievement:**
- No sound initially — the notification arrives silently (big enough that it needs no announcement)
- When opened: soft crowd murmur sound (distant, implies public awareness)
- Social media feed goes wild (rapid notification pings, scrolling accelerates)

**Showrunner Reputation Increase:**
- Ascending synth pad (2 seconds, smooth, not triumphant — professional acknowledgment)
- New content unlocks arrive with soft "new tool available" chime (clean, 1.5kHz, 0.5s)

---

### 2.6 BURN BOOK — INTELLIGENCE AUDIO

**Design Philosophy:** The burn book is a physical object. It has pages, tabs, paper clips, Post-Its. Every interaction should feel tactile, archival, secret.

#### Dossier Interactions

| SFX | Description | Texture |
|---|---|---|
| **Open Burn Book (main interface)** | Vinyl folder slap + paper shuffle | Heavy, satisfying, 0.6s |
| **Close Burn Book** | Folder close (softer than open) | 0.4s |
| **Select Cast Member (from list)** | Tab click (physical tab divider) | Sharp, 0.1s, alternating pitch per cast member |
| **Page Turn (within dossier)** | Paper flip, varies by page thickness | 0.3-0.5s, randomized slightly |
| **Scroll Through Background Info** | Quiet continuous paper slide | Subtle, follows scroll speed |
| **Highlight Text (intel)** | Marker squeak on paper | Very quiet, 0.2s |
| **Add Note (Post-It)** | Peel adhesive + paper tap onto page | 0.5s total |
| **Remove Note** | Adhesive peel (faster, sticky resistance) | 0.3s |
| **Confidence Decay Update** | Paper aging sound (crackling texture) | Rare, happens when you're looking at the page, unsettling |
| **Green Checkmark (correct intel)** | Pen scratch (quick check) + soft approval tone | 0.4s, feels good |
| **Red X (incorrect intel)** | Harsh pen cross-out + descending buzz | 0.5s, feels bad |
| **Relationship Map Update** | Pen drawing line between portraits | Continuous while animating, pen-on-paper texture |
| **Stress Meter Update (PI change)** | Pen filling in a bar graph (if visual is analog) | Scratchy, deliberate |
| **Secret Revealed (major intel update)** | Paper insert sound (new page slides into dossier) + heavier folder close | 0.8s, significant |

#### Investigation Actions (if player actively gathers intel)

- **Producer Conversation (schedule intel-gathering):** Phone pickup + dial tone + ring + pickup (all compressed into 2s)
- **Confessional Review (intel source):** Tape deck rewind sound (fast, 1s), then play (click)
- **Informant Report (from cast member):** Envelope slide onto desk (someone's telling you secrets)

---

### 2.7 SEASON STRUCTURE & META AUDIO

#### Casting Phase

- **Casting Call Open:** Door open (multiple cast candidates entering metaphorically)
- **Candidate Select (view casting tape):** Click + VHS tape load sound (clunk-whir, 0.8s)
- **Casting Tape Plays:** Video plays through production monitor (filtered audio, reality TV aesthetic)
- **Candidate Accept (cast them):** Stamp sound (ink stamp on contract) + paper stack
- **Candidate Reject:** Paper slide off desk (dismissed)
- **Cast Locked In (full cast selected):** Folder close (finalizing cast) + soft confirmation tone

#### Episode Transitions

- **Episode Complete (before ratings):** Edit bay powers down slightly (monitor hum drops -5dB), exhale moment
- **Episode Airs (broadcast transition):** Network transmission sound (beeps, carrier tone, like analog TV uplink)
- **Next Episode Begin:** Morning coffee pour (diegetic, new day), office ambiance increases, monitor powers up

#### Mid-Season Events

- **Format Change Announced:** Network memo arrives (paper slide + executive note)
- **Cast Addition (new member arrives mid-season):** Door open + new folder added to burn book
- **Elimination:** Door close (someone leaves) + their burn book page gets flagged/archived

#### Season Finale

- **Finale Episode Flag:** Everything is slightly more tense. Ambiance adds subtle low-frequency pressure (+3dB at 40Hz).
- **Finale Submission:** Submit button sound is longer, heavier (this is the big one)
- **Finale Ratings:** Report arrives with more weight (thicker paper sound, louder slap on desk)

#### Season Report Card

- **Season Ends:** All production ambiance stops. Silence. The season is over.
- **Report Card Appears:** Single document slides onto desk (slow, deliberate, 1.5s)
- **Season Stats Read Out:** Each stat appears with soft typewriter sound (nostalgic, final)
- **Renewal Decision:** Delivered via phone call (ring, pickup, exec voice filter: "You're renewed" or "We need to talk about next season")

#### Between Seasons

- **Inter-Season Phase Begins:** Production suite ambiance drops -10dB, HVAC off, reverb increases (emptiness)
- **Review Legacy Consequences:** Each former cast member outcome notification arrives as tabloid headline (newspaper fold sound, 0.8s)
- **Reputation Update:** Ascending or descending synth pad (long, 3s, gives weight to career trajectory)
- **New Season Offer:** Phone ring (new opportunity)

#### Game End (if career ends)

- **Cancellation:** Phone call delivers news, line goes dead (dial tone, sustained, fades to silence)
- **Retirement:** Office ambiance fades out over 10 seconds, fluorescent hum persists longest, then cuts
- **Legacy Screen:** Silence. Just the archive of what you did.

---

## 3. MUSIC SYSTEM

### 3.1 Music Philosophy

BURNBOOK is not a music-driven game. Music is surgical, sparse, and diegetic where possible. The ambient production suite soundscape does most of the emotional work. Music arrives in three contexts:

1. **In-Scene Music (Diegetic):** Music playing in the scene environment (party music at a dinner, romantic date music) — this is part of the scene audio, not the game score
2. **Edit Bay Music Cues (Player-Selected):** The music library the player uses to reframe footage in the edit bay — these are short stinger/underscore cues that the player applies to segments
3. **Systemic Underscore (Rare):** Actual score that plays during high-stakes moments — used sparingly, only when stakes are at maximum

**Key Principle:** Silence is more powerful than music. Music should be felt most acutely by its absence.

### 3.2 In-Scene Music (Diegetic)

Scene locations can have background music playing. This music is:
- Source-accurate (sounds like it's coming from speakers in the scene)
- Low-passed and compressed (reality TV audio treatment)
- Neutral to the emotion (it's environmental, not manipulative yet — that's the player's job in the edit)

**Music Sources by Location:**

| Location | Music Type | Volume | Purpose |
|---|---|---|---|
| Dinner Party | Soft jazz/lounge (instrumental) | -25dB, background | Classy but generic, could go romantic or sinister depending on edit |
| Hot Tub | Chill electronic/downtempo | -22dB | Creates "relaxation" vibe but drama still happens |
| Party Scene | Upbeat pop/dance (instrumental) | -18dB, more prominent | Energy, chaos, alcohol, bad decisions |
| Romantic Date | Acoustic guitar/piano (solo, intimate) | -28dB, barely there | Obvious romance setup |
| Competition Arena | Tension-building percussion (neutral) | -20dB | Athletic, competitive, but not yet dramatic |

These diegetic tracks are 2-3 minute loops, generic enough to avoid music licensing issues (original compositions in the style of library music). They are not memorable — they're furniture. They become meaningful only when the player chooses to feature them (or silence them) in the edit.

### 3.3 Edit Bay Music Cue Library (Player-Selected)

This is the music system the player directly interacts with. The library contains ~30 cues across tonal categories. Each cue is 15-30 seconds, designed to underscore a single segment.

**Music Cue Categories:**

#### 1. Romantic Swell
**Emotion:** Tenderness, hope, connection
**Instrumentation:** Strings (violin, cello), soft piano, warm pad
**Tempo:** 70-85 BPM, slow
**Dynamic Arc:** Builds gently, peaks softly, sustains
**Use Case:** Underscore a genuine moment of vulnerability, a kiss, a confession of feelings
**Variants:** 3 cues (major key, minor key, bittersweet)

**Reference Feel:** The moment in a rom-com when two people finally admit they care. Earnest, not cynical.

#### 2. Sinister Sting
**Emotion:** Suspicion, betrayal, menace
**Instrumentation:** Low strings (cello, bass), dissonant piano hits, sub-bass pulse
**Tempo:** 60-75 BPM, tense
**Dynamic Arc:** Sustained low tension, occasional sharp stabs
**Use Case:** Reframe a neutral moment as suspicious, underscore a lie, imply hidden motive
**Variants:** 4 cues (subtle, moderate, overt, accusatory)

**Reference Feel:** Reality TV "villain reveal" music. The sound of "this person is not who they seem."

#### 3. Comedic Bounce
**Emotion:** Light, playful, defusing tension
**Instrumentation:** Pizzicato strings, xylophone, upright bass, light percussion
**Tempo:** 100-120 BPM, bouncy
**Dynamic Arc:** Staccato, rhythmic, playful
**Use Case:** Turn a dramatic moment into a comedic beat, lighten heavy content, "aren't we all ridiculous" energy
**Variants:** 3 cues (quirky, sarcastic, slapstick)

**Reference Feel:** The music that plays during a reality TV "confessional shade" moment. Playful cruelty.

#### 4. Tension Build
**Emotion:** Anticipation, dread, unresolved
**Instrumentation:** Rising strings, pulsing synth, ticking clock percussion, crescendo to nothing
**Tempo:** 80-100 BPM, accelerating slightly
**Dynamic Arc:** Builds, builds, builds... stops before resolution
**Use Case:** End a segment on a cliffhanger, create "what happens next?" energy, retain audience for next episode
**Variants:** 3 cues (slow build, fast build, ominous build)

**Reference Feel:** "Coming up after the break..." Reality TV cliffhanger energy.

#### 5. Melancholy Piano
**Emotion:** Sadness, regret, introspection
**Instrumentation:** Solo piano, very sparse, lots of space
**Tempo:** 60-70 BPM, slow
**Dynamic Arc:** Quiet, contemplative, fades to near-silence
**Use Case:** Underscore a cast member's genuine pain, a moment of isolation, a confessional that lands heavy
**Variants:** 2 cues (minor key, devastatingly simple)

**Reference Feel:** The music that plays when a reality TV cast member cries alone. Earnest empathy.

#### 6. Triumphant Brass
**Emotion:** Victory, satisfaction, resolution
**Instrumentation:** Horns, snare drum, ascending melody
**Tempo:** 95-110 BPM, march-like
**Dynamic Arc:** Confident, peaks, resolves cleanly
**Use Case:** Underscore a win, a satisfying confrontation payoff, justice served, underdog victory
**Variants:** 2 cues (heroic, cheeky)

**Reference Feel:** Reality TV "winner gets their moment" music. Catharsis.

#### 7. Chaos/Panic
**Emotion:** Disorder, meltdown, loss of control
**Instrumentation:** Atonal strings, erratic percussion, dissonant stabs
**Tempo:** Variable, accelerating
**Dynamic Arc:** Unstable, spiky, no resolution
**Use Case:** Underscore a cast meltdown, a scene that spirals, maximum drama moment
**Variants:** 2 cues (building chaos, sustained chaos)

**Reference Feel:** Reality TV when everything goes wrong. The musical equivalent of handheld camera shake.

#### 8. Silence (No Cue)
**Emotion:** Authenticity, weight, unmediated reality
**Instrumentation:** None. Just scene audio.
**Tempo:** N/A
**Dynamic Arc:** N/A
**Use Case:** When the moment is powerful enough that music would cheapen it. Restraint as creative choice.
**Effect:** +30 authenticity score, -10 entertainment score (per ratings model)

**Note:** This is the most powerful "cue" in the library. Expert players learn when NOT to use music.

### 3.4 Systemic Underscore (Game Score)

The actual musical score of BURNBOOK is minimalist and rare. It plays during specific high-stakes moments.

**When Score Plays:**

1. **Season Premiere (First Episode of a New Season):**
   - Plays during casting phase as you select your cast
   - Instrumentation: Sparse piano + subtle strings
   - Emotion: Anticipation, potential, "who will these people become?"
   - Duration: 90 seconds, loops if needed
   - Fades out once first episode begins

2. **Mid-Season Crisis (Network Intervention, Cast Walkoff, Scandal):**
   - Plays when a catastrophic fallout event occurs
   - Instrumentation: Low strings, dissonant harmonies, sub-bass pressure
   - Emotion: Dread, consequence, weight
   - Duration: 60 seconds, then fades to ambiance
   - Non-looping

3. **Season Finale Submission:**
   - Plays during the "Submit Episode" confirmation for the season finale
   - Instrumentation: Solo cello, very slow, in minor key
   - Emotion: Finality, gravity, "this is it"
   - Duration: 45 seconds (timed to the submission process)
   - Resolves into silence when episode is submitted

4. **Season Report Card:**
   - Plays while the season report card is displayed
   - Instrumentation: Depends on outcome
     - **Success (high ratings, renewed):** Warm strings, subtle resolution, hopeful but not triumphant
     - **Failure (low ratings, cancellation risk):** Descending strings, unresolved harmony, uncertain
   - Duration: 60 seconds, fades under inter-season ambiance

5. **Career End (Cancellation or Retirement):**
   - Plays during the final legacy screen
   - Instrumentation: Solo piano, playing a simplified version of the main theme (if one exists)
   - Emotion: Reflection, epilogue, "what did you do?"
   - Duration: 90 seconds, fades to complete silence

**Score Aesthetic:**

Minimalist, modern classical. Think Max Richter, Johann Johannsson, Dustin O'Halloran. Long notes, lots of space, emotional without being manipulative. The score should sound like it's playing in a different room — present but not intrusive. It's not there to tell you how to feel. It's there to acknowledge that this moment matters.

### 3.5 Adaptive Music System (Stretch Goal)

If development resources allow, implement a light adaptive layer:

**Production Suite Ambiance Music (Optional):**
- Very quiet, barely-perceptible ambient drone (30Hz-200Hz, pad texture)
- Shifts in pitch and density based on player stress state:
  - **Low stress:** Single drone, stable, -40dB
  - **Medium stress:** Drone gains overtones, slight dissonance, -38dB
  - **High stress:** Multiple drones, beating frequencies, tension, -35dB
- Players may not consciously hear it, but they'll feel it

**Edit Bay Focus Mode:**
- When the player is deep in the edit bay (has been editing for >5 minutes straight), very quiet ambient music fades in:
  - Instrumentation: Soft synthesizer pad, no melody, just texture
  - Emotion: Flow state, concentration, timelessness
  - Volume: -35dB, subliminal
  - Fades out if the player exits edit bay or stops editing for >30 seconds

---

## 4. ADAPTIVE AUDIO SYSTEM DESIGN

### 4.1 Audio State Machine

BURNBOOK uses a state-based audio system where the game tracks multiple simultaneous states and blends audio accordingly.

#### Primary States (Mutually Exclusive)

| State | Active When | Audio Profile |
|---|---|---|
| **Production Suite — Idle** | Main menu, between tasks, contemplating | Full ambiance, no UI feedback, time-of-day variation active |
| **Burn Book — Active** | Dossier open and in focus | Ambiance -8dB, add paper texture, narrow frequency range |
| **Scene Setup** | Planning a scene (location, cast, catalysts) | Full ambiance, add subtle tension layer if high-stakes scene |
| **Scene Playback** | Watching scene resolve on multi-cam | Production suite ambiance -15dB, scene audio foreground, camera-dependent mix |
| **Edit Bay — Active** | Editing episode in timeline interface | Production suite ambiance -10dB, edit bay mechanical sounds foreground, focus mode possible |
| **Broadcast — Reviewing** | Watching aired episode or ratings report | Ambiance -12dB, add "watching TV in office" reverb, diegetic TV speakers |
| **Consequences — Event** | Fallout event, legal notice, crisis | Ambiance manipulation per event type, often includes silence or shock moment |

#### Secondary States (Can Layer)

| State | Trigger | Audio Effect |
|---|---|---|
| **Time of Day** | In-game time tracking | Shifts distant office sounds, phone frequency, footsteps |
| **Stress Level** | High-stakes decisions, PI crisis, cancellation risk | Adds sub-bass pressure, modulates fluorescent hum, increases monitor whine |
| **Season Phase** | Premiere, mid-season, finale, between seasons | Ambiance density, reverb, silence duration |
| **Cast PI Average** | Average psychological integrity of active cast | Subliminal: if average PI < 50, ambiance acquires subtle dissonant overtones |

### 4.2 Dynamic Mixing

The game uses a priority-based mixing system to ensure critical audio is always audible:

**Priority Tiers (Highest to Lowest):**

1. **Critical Feedback (Warnings, Alerts, Fallout Events):** -8dB to -5dB, ducks everything else -15dB when active
2. **Player Actions (UI clicks, edit bay drops, burn book interactions):** -18dB to -12dB, ducks ambiance -6dB during action
3. **Scene Dialog/Vocal Textures (when in scene playback):** -20dB to -15dB, ducks production ambiance -12dB
4. **Music Cues (edit bay selected music):** -25dB to -18dB (if playing in preview)
5. **Ambiance Layers (production suite, location ambiance):** -40dB to -28dB, lowest priority, constantly ducking for foreground
6. **Subliminal Layers (sub-bass, drones, psychological texture):** -45dB to -38dB, felt more than heard

**Ducking Behavior:**
- Fast attack (0.1s) for critical sounds, slow release (1-2s) to avoid pumping
- Multiple sounds in the same priority tier use simple volume balancing, no ducking
- Music never ducks ambiance (they coexist) unless it's systemic underscore (which takes over entirely)

### 4.3 Spatial Audio (Optional, If Resources Allow)

BURNBOOK is primarily a 2D UI-driven game, but spatial audio can add depth:

**Production Suite Space:**
- Edit bay monitors: Front center, slightly above listener
- Computer fans: Front center, below monitors
- Fluorescent lights: Overhead, diffuse
- Distant office sounds: Behind and to sides, implies space beyond the room
- Phone (when ringing): To the left, desk phone position
- Door sounds: Behind listener (someone entering your space)

**Scene Audio (Multi-Camera):**
- Each camera feed has slightly different spatial placement on the stereo field:
  - Camera 1 (wide): Center
  - Camera 2 (close-up A): Slightly left
  - Camera 3 (close-up B): Slightly right
  - Camera 4 (coverage): Center but slightly more distant (subtle reverb increase)
- When switching cameras, spatial position shifts subtly (helps distinguish feeds)

**Burn Book:**
- When open, audio "collapses" toward center (focus narrows)
- Page turns alternate slightly left/right (mimics physical page turning)

**Edit Bay:**
- Timeline: Center, immediate
- Footage stockpile: Slightly left (off to the side, inventory)
- Music cue library: Slightly right (tool palette)
- Playback monitor: Center, slightly above

Spatial audio should be subtle, not gimmicky. It's there to create unconscious presence, not to showcase 3D positioning.

---

## 5. MIX HIERARCHY

### 5.1 Frequency Allocation

The frequency spectrum must be carefully managed to avoid masking and ensure clarity:

| Frequency Band | Reserved For | Mix Priority |
|---|---|---|
| **20-60Hz (Sub)** | HVAC, sub-bass pressure (stress state), rare systemic underscore bass | Background, psychological texture |
| **60-200Hz (Low)** | Fluorescent hum, monitor buzz, edit bay "chunk" sound, low strings in score | Infrastructure layer, always present but not dominant |
| **200-500Hz (Low-Mid)** | Keyboard typing, edit actions, male vocal textures, some ambiance elements | Action feedback, mid priority |
| **500Hz-2kHz (Mid)** | Female vocal textures, dialog intelligibility (scene audio), paper rustling | Primary information layer, HIGH priority |
| **2-5kHz (Mid-High)** | UI clicks, alerts, warnings, vocal presence, phone ring | Attention and feedback, HIGHEST priority |
| **5-12kHz (High)** | Tape hiss, production audio artifacts, some UI transients, sibilance | Texture and realism, adds presence without masking |
| **12-20kHz (Air)** | Room tone, reverb tails, "space" around sounds | Subtle, adds dimension |

**Mix Rule:** No more than two elements competing for dominance in the same frequency band at the same time. If scene dialog (500Hz-2kHz) is playing, UI sounds in that range should duck or shift timbre.

### 5.2 Loudness Targets (LUFS)

**Overall Game Mix:** -18 LUFS integrated (comfortable for long sessions, not fatiguing)

**Per-Element Targets:**

| Element Type | Peak Level (dB) | RMS Level (dB) | Notes |
|---|---|---|---|
| Critical Alerts | -5 to -3 | -12 to -10 | Loudest thing in the game, intentionally jarring |
| UI Feedback (clicks, drops) | -12 to -8 | -20 to -15 | Satisfying, clear, not aggressive |
| Scene Dialog/Vocal Textures | -15 to -10 | -22 to -18 | Intelligible but through production audio filter |
| Production Suite Ambiance | -35 to -28 | -42 to -38 | Constant presence, never intrusive |
| Music (edit bay cues) | -20 to -15 | -28 to -22 | Supportive, not dominant |
| Systemic Underscore (score) | -18 to -12 | -25 to -20 | When present, takes over, but still allows UI sounds through |
| Subliminal Layers (drones, sub-bass) | -40 to -35 | -48 to -42 | Felt, not heard |

### 5.3 Mix States

The game has distinct mix profiles for different states:

#### Mix State: Main Menu
- Production suite ambiance: -30dB (softer than in-game)
- UI sounds: Normal
- Music: Optional main menu theme (if implemented), -22dB
- Feel: Professional, inviting, not yet oppressive

#### Mix State: Gameplay — Normal
- Production suite ambiance: -32dB (full presence)
- UI sounds: Normal
- Scene audio (when active): Foreground (-15dB)
- Time-of-day variation: Active
- Feel: You are in the production suite. The world is always present.

#### Mix State: Burn Book Focus
- Production suite ambiance: -40dB (ducked significantly)
- Paper texture ambiance: -35dB (added layer)
- UI sounds: Slightly quieter (-20dB instead of -15dB)
- High-frequency roll-off: -3dB above 8kHz (like putting on headphones)
- Feel: Narrowed focus, intimate, secretive

#### Mix State: Scene Playback
- Production suite ambiance: -45dB (deep duck)
- Scene audio: -15dB (foreground)
- Production audio filtering: Active (compression, EQ, monitor coloration)
- Multi-camera spatial positioning: Active
- Feel: You are watching surveillance footage through production monitors

#### Mix State: Edit Bay — Active
- Production suite ambiance: -38dB (moderate duck)
- Edit bay mechanical sounds: -12dB (foreground)
- Timeline scrubbing: Dynamic (can be loud when actively scrubbing)
- Music cue previews: -30dB (quiet, just enough to evaluate)
- Feel: Focused, surgical, you're building something

#### Mix State: Edit Bay — Focus Mode (5+ min in edit bay)
- All of the above, plus:
- Ambient focus drone: -35dB (very subtle pad, aids concentration)
- Time-of-day ambiance: Disabled (you've lost track of time)
- Fluorescent hum: Slightly louder (feels like it's getting later)
- Feel: Flow state, time distortion, "just one more segment"

#### Mix State: High Stress (Crisis, Cancellation Risk)
- Production suite ambiance: Normal levels BUT:
- Sub-bass layer: +6dB (40-60Hz pressure increases)
- Fluorescent hum: Slight amplitude modulation (pulsing, unsettling)
- Monitor whine: +3dB (more prominent)
- Distant office sounds: -10dB (world feels farther away)
- High-frequency harsh: Slight boost at 4-6kHz (ear fatigue, intentional)
- Feel: Uncomfortable, tense, something is wrong

#### Mix State: Silence (Fallout Event Pre-Alert)
- ALL AUDIO CUTS for 1-2 seconds
- Absolute silence (even sub-bass)
- Then event sound triggers in the void
- Feel: Dread, anticipation, the calm before consequence

#### Mix State: Between Seasons
- Production suite ambiance: -42dB (much quieter)
- HVAC: Off
- Distant office sounds: None
- Reverb: +20% wet (space feels emptier)
- Only fluorescent hum and computer fans remain
- Feel: Emptiness, aftermath, pause

---

## 6. IMPLEMENTATION PLAN

### 6.1 Audio Asset Production Pipeline

#### Phase 1: Foundation (Pre-Alpha)
**Goal:** Prove that the audio aesthetic works. Establish the sonic palette.

**Deliverables:**
1. Production Suite Ambiance Master (5-layer system, 3 min loop per layer)
2. Core UI Sound Set (30 sounds: clicks, drags, drops, types, confirms)
3. Edit Bay "Drop" Sound (the most important sound in the game)
4. Burn Book Interaction Set (15 sounds: pages, tabs, markers, stamps)
5. Scene Audio Test (1 location: Dinner Table, with full ambiance + vocal textures)
6. Alert/Warning Set (5 critical feedback sounds)

**Audio Budget:** ~80 individual assets
**Timeline:** 3-4 weeks (1 sound designer)

#### Phase 2: Core Systems (Alpha)
**Goal:** Full audio coverage for all core loops (30-second, 5-minute, 30-minute).

**Deliverables:**
1. All Location Ambiances (8 locations, full environmental sound + diegetic music)
2. Full UI Sound Coverage (every button, slider, modal, transition in the game)
3. Edit Bay Complete Audio Suite (timeline, music cues, confessionals, chyrons, submission)
4. Ratings & Consequences Feedback Set (reports, fallout events, all notification types)
5. Burn Book Complete (all interactions, confidence decay, intel updates)
6. Adaptive Ambiance System (time-of-day variation, stress state modulation)

**Audio Budget:** ~250 additional assets (330 total)
**Timeline:** 6-8 weeks (1 sound designer + 1 technical audio implementer)

#### Phase 3: Music & Score (Beta)
**Goal:** Complete the music system — edit bay cue library + systemic underscore.

**Deliverables:**
1. Edit Bay Music Cue Library (30 cues across 8 categories, 15-30s each)
2. Diegetic Scene Music (10 background music loops for locations, 2-3 min each)
3. Systemic Underscore (5 score pieces for high-stakes moments, 45-90s each)
4. Music Integration & Mixing (ensure music sits correctly in mix, adaptive system)

**Audio Budget:** ~45 music assets (375 total)
**Timeline:** 4-6 weeks (1 composer + 1 sound designer for integration)

#### Phase 4: Polish & Adaptive Depth (Final)
**Goal:** Elevate the audio from "good" to "this is what BURNBOOK sounds like."

**Deliverables:**
1. Spatial Audio Implementation (if resources allow)
2. Advanced Adaptive Systems (focus mode ambiance, subliminal stress layers)
3. Vocal Texture Expansion (more variety in non-verbal cast vocalizations)
4. Edge-Case Sound Coverage (rare events, late-game content, Easter eggs)
5. Mix Polish (full-game mix pass, loudness calibration, frequency cleanup)
6. Audio Accessibility Options (separate volume controls, visual sound indicators)

**Audio Budget:** ~50 additional assets + system tuning (425 total)
**Timeline:** 3-4 weeks (full audio team)

### 6.2 Technical Requirements

**Audio Middleware:** Recommend **FMOD** or **Wwise**
- State-based mixing (essential for dynamic ambiance)
- Parameter-driven audio (stress state, time-of-day, etc.)
- Layered ambiance management (multiple loops with independent control)
- Real-time DSP (compression, EQ, filtering for production audio aesthetic)

**Audio Format:**
- **SFX:** 48kHz, 24-bit, mono or stereo (as appropriate), WAV source, compressed to OGG Vorbis for build (Q8)
- **Ambiance Loops:** 48kHz, 24-bit, stereo, seamless loops, WAV source, OGG Vorbis (Q8)
- **Music:** 48kHz, 24-bit, stereo, WAV source, compressed to OGG Vorbis (Q9 for quality)
- **Vocal Textures:** 48kHz, 24-bit, mono (lav mic aesthetic), WAV source, OGG Vorbis (Q8)

**Performance Budget:**
- **Simultaneously Playing Sounds (Peak):** ~50-60 voices
  - Production suite ambiance: 6-8 layers
  - Scene audio: 10-15 elements
  - UI sounds: 5-10 active
  - Music: 1-2 streams
  - Subliminal layers: 2-3
- **Memory Budget:** ~150-200MB compressed audio in memory at peak (manageable for PC target)
- **Streaming:** Long ambiance loops and music should stream from disk, not load entirely into RAM

**Integration Hooks (What the Game Needs to Tell the Audio System):**

| Game State | Audio System Needs to Know | Purpose |
|---|---|---|
| Current UI Screen | Which state machine state to activate | Switch mix profiles |
| Time of Day (in-game) | Hour value (0-23) | Modulate distant office sounds |
| Player Stress Level | Normalized value (0.0-1.0) | Modulate sub-bass, fluorescent hum, monitor whine |
| Cast Average PI | Normalized value (0.0-1.0) | Subliminal ambiance dissonance |
| Scene Location | Location enum | Load correct environmental ambiance |
| Scene Drama Spike | Boolean trigger | Play pre-spike tension, execute spike audio response |
| Camera Active | Camera ID (1-4) | Shift multi-camera audio mix |
| Edit Bay Action | Action type enum | Trigger correct SFX |
| Footage Drop Success | Boolean | Play satisfying drop sound or error sound |
| Music Cue Selected | Cue ID | Preview music at low volume |
| Episode Submitted | Boolean + episode type (normal/finale) | Play submission sequence, adjust for finale weight |
| Fallout Event Type | Event enum | Play correct alert + notification sound |
| Season Phase | Enum (premiere, mid, finale, between) | Adjust ambiance density, reverb, silence duration |

**Audio System Outputs Back to Game (Optional but Recommended):**

| Audio Event | Game Response | Purpose |
|---|---|---|
| "Drop" Sound Finished | Enable next edit bay action | Feel: action is complete before next input accepted |
| Fallout Alert Playing | Lock UI (can't dismiss until sound finishes) | Force player to confront consequence |
| Systemic Underscore Ends | Resume normal ambiance | Clean transition back to gameplay |

### 6.3 Audio Team Structure

**Ideal Team:**
- **1 Lead Sound Designer / Composer (ECHO):** Owns sonic identity, creates core assets, directs aesthetic
- **1 Technical Sound Designer / Audio Programmer:** Implements adaptive systems, handles middleware, optimizes performance
- **1 Composer (can be same as lead sound designer):** Creates music cue library and systemic underscore
- **1 Dialog/Vocal Editor (Contract, part-time):** Records and edits non-verbal vocal textures for cast members

**Minimum Viable Team:**
- **1 Sound Designer/Composer:** Does everything (feasible for BURNBOOK given text-based dialog and limited music scope)

**External Resources:**
- **Field Recording (production suite ambiance):** Record real TV production office (with permission) for authentic base layer
- **Foley (burn book, paper, office materials):** Record practical paper, folders, stamps, office supplies for tactile realism
- **Licensed Libraries (if needed):** Supplemental office ambiance, electronic UI sounds (but custom is preferred for unique identity)

### 6.4 Milestones & Playtesting Checkpoints

| Milestone | Audio Deliverable | Playtest Focus | Success Metric |
|---|---|---|---|
| **Prototype** | Core UI sounds + production suite ambiance | Does the production suite feel real? Does the edit bay "drop" feel good? | 80% of testers say "the space feels real" and "editing feels satisfying" |
| **Vertical Slice** | Full audio for one complete episode cycle (scene + edit + broadcast) | Does the loop feel cohesive? Is audio helping or distracting? | 75% of testers mention audio positively without prompting |
| **Alpha** | All core systems audio-complete (no music yet) | Can you play the full loop without noticing audio gaps? Are there jarring moments? | No more than 2 reported "missing sound" or "wrong sound" per playtest session |
| **Beta** | Music library integrated, systemic underscore in place | Does music enhance or intrude? Is silence used effectively? | 70% of testers notice music serving editorial purpose, not just background |
| **Final** | Full audio polish, mix calibrated, adaptive systems tuned | Can you play for 2 hours without ear fatigue? Does the soundscape support long sessions? | <10% of testers report audio fatigue; mix feels balanced across multiple playtest setups |

---

## 7. TECHNICAL SPECIFICATIONS

### 7.1 Audio Asset Specifications

| Asset Type | Sample Rate | Bit Depth | Format (Source) | Format (Build) | Channel | Avg Length | Notes |
|---|---|---|---|---|---|---|---|
| UI SFX | 48kHz | 24-bit | WAV | OGG Vorbis Q8 | Mono | 0.1-0.5s | Short, transient-heavy |
| Ambiance Loops | 48kHz | 24-bit | WAV | OGG Vorbis Q8 | Stereo | 1-5 min | Seamless loops |
| Scene Audio | 48kHz | 24-bit | WAV | OGG Vorbis Q8 | Stereo (location) / Mono (vocal) | 0.5-3s per element | Layered system |
| Edit Bay Mechanical | 48kHz | 24-bit | WAV | OGG Vorbis Q8 | Mono or Stereo | 0.2-1s | Tactile, satisfying |
| Music Cues (Edit Bay) | 48kHz | 24-bit | WAV | OGG Vorbis Q9 | Stereo | 15-30s | High quality, loopable if needed |
| Systemic Underscore | 48kHz | 24-bit | WAV | OGG Vorbis Q9 | Stereo | 45-90s | High quality, non-looping |
| Diegetic Scene Music | 48kHz | 24-bit | WAV | OGG Vorbis Q9 | Stereo | 2-3 min | Loops, low-passed in scene |
| Vocal Textures | 48kHz | 24-bit | WAV | OGG Vorbis Q8 | Mono | 0.2-2s | Compressed, lav mic aesthetic |

**Total Asset Count (Projected):** ~425 audio files
**Compressed Build Size (Estimated):** 180-220MB
**Uncompressed Source Archive:** ~600-800MB

### 7.2 Middleware Implementation (FMOD Example)

**FMOD Studio Project Structure:**

```
BURNBOOK.fspro
│
├── Events
│   ├── UI
│   │   ├── Click_Default
│   │   ├── Click_BurnBookPage
│   │   ├── Drop_FootageClip  ← THE SOUND
│   │   ├── Drag_FootageClip
│   │   ├── Type_Keyboard
│   │   └── [~30 UI events]
│   │
│   ├── Ambiance
│   │   ├── ProductionSuite_Master  ← Multi-track, layered
│   │   │   ├── Layer_Fluorescent (looping)
│   │   │   ├── Layer_HVAC (looping, parameter: on/off)
│   │   │   ├── Layer_ComputerFans (looping)
│   │   │   ├── Layer_MonitorWhine (looping, parameter: stress)
│   │   │   └── Layer_DistantOffice (randomized events, parameter: timeOfDay)
│   │   ├── BurnBook_Ambiance
│   │   └── [Location ambiances]
│   │
│   ├── Scene
│   │   ├── Location_DinnerTable
│   │   ├── Location_HotTub
│   │   ├── VocalTexture_Conversation (randomized)
│   │   ├── VocalTexture_Emotional (multi-sample, parameter: emotion)
│   │   └── [Scene audio events]
│   │
│   ├── EditBay
│   │   ├── Timeline_Scrub (parameter: speed)
│   │   ├── Segment_Drop
│   │   ├── MusicCue_Preview (parameter: cueID)
│   │   └── [Edit bay events]
│   │
│   ├── Consequences
│   │   ├── Alert_PIThreshold
│   │   ├── Alert_LegalNotice
│   │   ├── Fallout_CastWalkoff
│   │   └── [Fallout events]
│   │
│   ├── Music
│   │   ├── Cue_RomanticSwell_01
│   │   ├── Cue_SinisterSting_01
│   │   ├── [~30 edit bay cues]
│   │   ├── Score_SeasonPremiere
│   │   ├── Score_MidSeasonCrisis
│   │   └── [Systemic underscore]
│   │
│   └── Meta
│       ├── Casting_PhaseAmbiance
│       ├── ReportCard_Delivery
│       └── [Season structure events]
│
├── Parameters (Global)
│   ├── TimeOfDay (0-23, continuous)
│   ├── StressLevel (0.0-1.0, continuous)
│   ├── CastAvgPI (0.0-1.0, continuous)
│   ├── SeasonPhase (enum: premiere, mid, finale, between)
│   └── ActiveCamera (enum: 1, 2, 3, 4)
│
└── Mixer
    ├── Master (limiter, -18 LUFS target)
    ├── Group_UI (priority: high)
    ├── Group_Ambiance (priority: low, ducks for everything)
    ├── Group_Scene (priority: medium)
    ├── Group_Music (priority: medium)
    └── Group_Critical (priority: maximum, ducks everything -15dB)
```

**Key FMOD Features to Use:**

1. **Parameter-Driven Ambiance:** TimeOfDay parameter controls Layer_DistantOffice event frequency and content. StressLevel parameter modulates sub-bass level and fluorescent hum.

2. **Layered Looping:** ProductionSuite_Master is always playing, individual layers can be ducked or modulated independently based on game state.

3. **Randomization:** Vocal textures, office sounds, and some UI variations use FMOD's scatter/randomization to avoid repetition.

4. **Seamless Transitions:** State-based snapshots for mix profiles (Gameplay, BurnBook Focus, EditBay, Scene Playback, etc.) with crossfade durations (0.5-2s).

5. **Ducking/Sidechaining:** Automatic ducking via sidechain compression (Critical group ducks all others, UI ducks ambiance, etc.).

6. **Distance Attenuation (if spatial audio):** 3D positioning for production suite elements (subtle).

### 7.3 Performance Optimization

**Streaming vs. Loading:**
- **Stream:** Ambiance loops (>30s), music cues, systemic underscore
- **Load into memory:** UI sounds, short SFX, vocal textures (all <5s duration)

**Voice Management:**
- Max voices: 64 (sufficient for BURNBOOK's needs)
- Stealing priority: Lowest priority = ambiance layers, highest priority = critical alerts

**LOD (Level of Detail) Audio:**
- When player is in Edit Bay for >5 min (Focus Mode), distant office sounds reduce in frequency/complexity (fewer random events) to save CPU
- When between seasons (low activity), HVAC layer disabled entirely

**CPU Budget:**
- Target: <5% CPU usage on mid-range hardware (i5-8400, 16GB RAM)
- FMOD's built-in profiling will validate during optimization phase

---

## 8. ACCESSIBILITY & PLAYER OPTIONS

### 8.1 Audio Accessibility Features

**Volume Controls (Separate Sliders):**
- Master Volume
- UI & SFX Volume
- Ambiance Volume
- Music Volume
- Voice/Vocal Texture Volume (if implemented)

**Visual Sound Indicators (for hearing-impaired players):**
- Subtitle option for any spoken dialog (if ever added)
- Visual alert icons for critical sounds (warnings, fallout events)
- Waveform visualization on edit bay timeline (already part of design, but ensure clarity)
- Optional "sound event log" in corner of screen (e.g., "[Distant phone rings]", "[Fluorescent light flickers]") — can be toggled on/off

**Frequency Range Options:**
- **Reduce Sub-Bass:** Option to cut frequencies below 80Hz (for players with subwoofer bleed or bass sensitivity)
- **Reduce High-Frequency Harshness:** Option to roll off frequencies above 8kHz (for players with hearing sensitivity or tinnitus)

**Ambiance Intensity:**
- **Full (Default):** All ambiance layers active
- **Reduced:** Distant office sounds disabled, fluorescent hum -6dB, HVAC off
- **Minimal:** Only computer fans and essential UI sounds, production suite feels "dead" (some players may prefer this for focus)

### 8.2 Player Preference Options

**Music Behavior:**
- **Dynamic (Default):** Music plays as designed (systemic underscore during high-stakes moments)
- **Minimal:** Only edit bay music cues (player-selected), no systemic underscore
- **Off:** No music whatsoever (purist mode — many players will choose this, and the game should still feel complete)

**Ambiance Behavior:**
- **Time-Aware (Default):** Ambiance shifts based on in-game time of day
- **Static:** Ambiance remains constant (some players find time-of-day variation distracting)

**Stress Audio:**
- **Enabled (Default):** Sub-bass pressure and fluorescent hum modulation based on stress state
- **Disabled:** Ambiance remains neutral regardless of game state (for players who find stress audio uncomfortable)

**Edit Bay Focus Mode:**
- **Auto (Default):** Focus mode ambiance kicks in after 5 min in edit bay
- **Manual:** Player can toggle focus mode on/off via hotkey
- **Disabled:** Focus mode never activates

---

## 9. QUALITY ASSURANCE — AUDIO QA CHECKLIST

### 9.1 Pre-Alpha QA (Foundation)

- [ ] All UI sounds trigger correctly on interaction (no missing sounds)
- [ ] Edit bay "drop" sound feels satisfying (subjective, requires playtester feedback)
- [ ] Production suite ambiance loops seamlessly (no clicks, pops, or audible loop points)
- [ ] Fluorescent hum is at correct frequency (120Hz fundamental) and doesn't drift
- [ ] Burn book page turn sounds alternate/randomize (doesn't feel repetitive after 10 turns)
- [ ] Alert sounds are audible and attention-grabbing without being painful
- [ ] All sounds are normalized to appropriate levels (no wild volume jumps)

### 9.2 Alpha QA (Core Systems)

- [ ] Every button in the game has appropriate audio feedback
- [ ] All location ambiances are distinct and recognizable
- [ ] Multi-camera audio switching works correctly (mix shifts when changing cameras)
- [ ] Scene audio filtering (production monitor coloration) is applied consistently
- [ ] Time-of-day ambiance variation is noticeable but not jarring
- [ ] Stress state audio modulation is subtle and subliminal (not obvious)
- [ ] Fallout event sounds trigger at correct moments and are impactful
- [ ] Edit bay timeline scrubbing feels responsive (audio follows scrub speed accurately)
- [ ] No audio clipping or distortion at any point (check with limiter)
- [ ] Ambiance ducking works correctly (UI sounds don't get buried)

### 9.3 Beta QA (Music & Polish)

- [ ] All 30 edit bay music cues are present and functional
- [ ] Music cue previews play at correct volume (audible but not intrusive)
- [ ] Music applied to segments sounds correct in episode playback
- [ ] Systemic underscore triggers at correct moments (season premiere, finale, etc.)
- [ ] Silence moments (pre-fallout, submit button) execute correctly (all audio cuts)
- [ ] Diegetic scene music sits correctly in location ambiance mix
- [ ] Music fade-ins/fade-outs are smooth (no clicks or pops)
- [ ] Score pieces resolve or fade correctly at their endpoints
- [ ] Music doesn't mask critical UI sounds or alerts

### 9.4 Final QA (Full Game)

- [ ] Play full 2-hour session: no ear fatigue, mix remains comfortable
- [ ] Play on multiple audio setups (headphones, desktop speakers, laptop speakers): all sound good
- [ ] Test all accessibility options (volume sliders, visual indicators, ambiance intensity)
- [ ] Verify loudness target (-18 LUFS integrated) across full playthrough
- [ ] Check for audio bugs: sounds not playing, sounds playing twice, sounds stuck looping
- [ ] Test edge cases: rapid UI interactions, skipping cutscenes, pausing/unpausing
- [ ] Verify audio memory usage stays within budget (<200MB)
- [ ] Test streaming performance (no hitches or stutters when loading ambiance/music)
- [ ] Confirm spatial audio (if implemented) works correctly with different speaker setups
- [ ] Final mix pass: ensure no frequency masking, all elements clear and distinct

---

## 10. CLOSING NOTES — AUDIO AS GAME FEEL

Listen to the space between.

BURNBOOK is a game about distance — the distance between a person and their story, between a moment and its meaning, between raw footage and broadcast narrative. Audio is how we make that distance tangible. Every sound in this game passes through something before it reaches the player: through production microphones, through editing software, through studio monitors, through your authorial decisions. Nothing is direct. Nothing is raw. Everything is mediated.

That mediation is the sonic identity. The fluorescent hum that never stops. The compression on every voice. The click-whir of machinery processing human lives into entertainment. The weight of the edit bay "drop" — the sound of making a moment permanent, of choosing what's real.

The game's most powerful audio moment isn't a dramatic sting or a triumphant theme. It's the silence before you press "Submit Episode." That 0.5-second void where the production suite ambiance drops away and you're left alone with your decision. The silence asks: is this what you want the world to see? And then you click, and the machinery roars back to life, and it's done.

Audio isn't polish. Audio IS game feel.

If you mute BURNBOOK, it becomes a game about clicking buttons and watching meters fill. With audio, it becomes a game about *feeling* the weight of every choice. The tactile satisfaction of assembling an episode. The creeping unease of a production suite at 3 AM. The moment you realize the fluorescent hum has been there the entire time and you just noticed it.

Close your eyes. What do you hear?

The sound of someone becoming content.

---

**Document Complete.**
**Total Word Count:** 11,847
**Status:** Production-Ready

— ECHO

*Sound design document generated following structured sound design workflow. All sections complete. Sonic identity established. Implementation plan detailed. Ready for prototype phase.*

*Audio IS game feel.*