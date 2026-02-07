# BURNBOOK — QA PLAN

**Version:** 1.0
**QA Lead:** CRASH
**Date:** 2026-02-07
**Status:** Pre-Production QA Planning
**Target Platforms:** PC (Steam), Steam Deck

---

## 0. QA PHILOSOPHY

Let me be clear about what this document is. This is not a checkbox exercise. This is not "click every button and see if it crashes." This is a roadmap for systematically breaking a game that depends on five interlocking systems producing emergent behavior. If the AI generates boring scenes, the game fails. If the edit bay feels like data entry, the game fails. If players can't understand why their ratings tanked, the game fails. Every one of those failures has a root cause, and finding those causes before the player does is the job.

What's the spec? We have four documents: pitch, GDD, narrative bible, technical architecture. The spec is what those documents promise the player will experience. The bugs are the gap between the promise and reality.

BURNBOOK is a HIGH-RISK project. The Situation Engine AI is unproven tech. The edit bay is a new mechanic. The moral weight depends on systems generating consequences that feel connected to player choices. We're not testing a management sim with a novel theme — we're testing whether five complex systems can generate a cohesive experience that makes the player feel complicit in something they slowly realize is monstrous.

That means QA starts at prototype and runs parallel to development. We don't wait for feature-complete. We test the AI behavior model in Month 1. We test the edit bay feel in Month 4. We track the quality gates at every milestone. When the tech doc says "kill condition: AI doesn't feel emergent by Month 3," that's a QA call. I make that call.

Here's what this document does:
1. Test plan organized by system and milestone
2. Test cases with preconditions, steps, expected results
3. Edge cases (the places systems break)
4. Risk assessment (what's most likely to fail)
5. Quality gates (what must pass before shipping)
6. Regression checklist (verify fixes don't break other systems)
7. Performance benchmarks (the game must maintain 60 FPS)

Let's break this.

---

## 1. SCOPE & PRIORITIES

### 1.1 What We're Testing

**Five Core Systems:**
1. **Burn Book System** — Intelligence database, confidence decay, prediction accuracy
2. **Situation Engine** — AI-driven scene simulation, moment generation, relationship dynamics
3. **Edit Bay System** — Timeline assembly, music cues, confessional overlays, episode scoring
4. **Ratings Engine** — Audience response, segment satisfaction, advertiser confidence, network satisfaction
5. **Fallout System** — PI tracking, consequence events, post-show outcomes, reputation damage

**Supporting Systems:**
- Save/Load (deep state persistence, corruption recovery)
- UI/UX (burn book navigation, edit bay timeline, multi-camera feeds)
- Procedural Generation (cast member creation, backstory pools, archetype variety)
- Progression (reputation unlocks, season-to-season continuity, legacy consequences)
- Economy (budget management, production costs, revenue calculation)

**Platform-Specific:**
- PC (mouse + keyboard, various resolutions, windowed vs. fullscreen)
- Steam Deck (touchscreen, trackpad, button controls, 1280x800 resolution, battery life)

### 1.2 Test Prioritization (MoSCoW)

**MUST TEST (Blocking Issues):**
- AI behavior produces distinct, believable, emergent outcomes
- Edit bay feels like authorship (not data entry)
- Ratings feedback is legible (player understands why ratings changed)
- Save/load preserves all state without corruption
- Core loop (place → shoot → edit → broadcast → ratings) completes without errors
- Performance maintains 60 FPS on target hardware
- No critical bugs (crashes, softlocks, data loss)

**SHOULD TEST (High Priority):**
- Cast members feel distinct (not interchangeable)
- Burn book confidence decay affects strategic decisions
- Fallout consequences feel connected to player choices
- Progression unlocks provide meaningful advancement
- Balance is fair (not too easy, not too hard)
- UI clarity (information is findable, readable, actionable)

**COULD TEST (Medium Priority):**
- Edge case handling (empty states, max limits, unusual inputs)
- Visual polish (animations, transitions, feedback)
- Audio integration (music cues, SFX timing)
- Accessibility (colorblind modes, text scaling)

**WON'T TEST (Out of Scope for v1):**
- Multiplayer (not planned)
- Voice acting (not planned)
- Mobile platforms (not planned)
- Localization (English-only for v1)
- Stretch goals (rival showrunner, reunion special, format lab — post-launch)

### 1.3 Testing Phases by Milestone

| Milestone | Primary QA Focus | Test Type | Pass Condition |
|-----------|------------------|-----------|----------------|
| **M1: AI Prototype (Month 1-3)** | Situation Engine behavior quality | Exploratory, usability | AI produces emergent, believable scenes. Playtest satisfaction > 7/10. |
| **M2: Vertical Slice (Month 4-6)** | Edit bay feel, core loop flow | Functional, usability | Full episode completes in 25-35 min. Edit bay satisfaction > 7/10. No blocking bugs. |
| **M3: Full Season (Month 7-10)** | Season arc coherence, save/load | Integration, stress | Season feels complete. Save/load flawless. Cast members memorable. |
| **M4: Multi-Season (Month 11-14)** | Progression, legacy consequences | Balance, integration | Reputation system works. Post-show outcomes surface correctly. |
| **M5: Full Content (Month 15-18)** | Performance, polish, Steam integration | Performance, regression | 60 FPS, <3s loads. All unlocks functional. Steam achievements work. |
| **M6: Beta (Month 19-22)** | Player behavior tracking, balance tuning | Closed beta, telemetry | <5 critical bugs. Balance feels right. Engagement metrics positive. |
| **M7: Launch (Month 23-24)** | Final verification, day-one patch prep | Smoke, regression | Clean launch. No game-breakers. Positive reviews. |

---

## 2. TEST PLAN BY SYSTEM

### 2.1 BURN BOOK SYSTEM

**What is the Burn Book supposed to do?**

The Burn Book is the player's intelligence database on every cast member. It contains psychological profiles, relationship maps, emotional states, secrets, and triggers. Information has a confidence value (0-100) that decays over time and regenerates through player actions (confessionals, producer conversations, observation). The player uses this intel to predict cast behavior and engineer situations. When predictions are accurate, confidence increases. When predictions fail, confidence drops and entries get crossed out.

**Test Areas:**

#### 2.1.1 Data Accuracy & Confidence Decay

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **BB-001: Initial profile accuracy** | New season, freshly cast members | Open burn book on Episode 1, read cast profiles | All intel displayed with 90-95% confidence (solid text, no wear) |
| **BB-002: Passive decay** | Episode 1 complete, no intel refresh actions taken | Advance to Episode 3, check same profiles | Confidence decreased 5-10% per episode. Text shows subtle wear texture. |
| **BB-003: Active decay after major event** | Cast member undergoes high-stress scene (PI drops >20) | Check their profile after scene | Emotional state confidence drops sharply. Personality profile shows question marks on affected traits. |
| **BB-004: Intel regeneration via confessional** | Cast member has low-confidence entry (<50%) | Trigger confessional scene, review new intel | Confidence increases 10-20%. Crossed-out text updated with new info. |
| **BB-005: Prediction accuracy tracking** | Setup scene based on burn book intel | Make prediction (e.g., "Marcus will confront Jade"), run scene | If prediction correct: green check appears. If wrong: red X appears with actual outcome noted. |
| **BB-006: Complete intel collapse** | Intel confidence reaches 0% on a cast member | Check their burn book page | Entry removed or shows as "NO DATA." Player is flying blind. |

**Edge Cases:**

- **BB-E001:** What happens if ALL cast members' intel degrades to 0% simultaneously? (Unlikely but possible if player ignores intel maintenance.)
- **BB-E002:** What if a cast member's personality fundamentally changes (e.g., Sweetheart becomes Villain after severe stress)? Does the burn book reflect this or stick to initial archetype?
- **BB-E003:** Intel on eliminated cast members — does it persist? Can player review past cast intel for reference?

**Usability:**

- Can player quickly find specific intel (e.g., "Who has a trigger related to abandonment?")?
- Is confidence decay communicated clearly enough that player knows WHEN to refresh intel?
- Do visual indicators (solid text vs. faded vs. crossed-out) read clearly at a glance?

---

#### 2.1.2 Relationship Mapping

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **BB-010: Relationship formation** | Two cast members interact positively in a scene | Check burn book after scene | Relationship entry created: "Ally" or "Romantic Interest" with intensity 30-50. |
| **BB-011: Relationship degradation** | Existing alliance (Jade/Tanya, intensity 70) | Engineer scene where Jade betrays Tanya | Relationship type changes to "Rival" or intensity drops significantly. |
| **BB-012: Hidden relationship** | Two cast members form secret alliance off-camera | Observe via informant system or overheard conversation | Burn book updates with "rumored alliance" entry at low confidence (40-60%). |
| **BB-013: Relationship history** | Long-running rivalry (Marcus/Derek, 6 episodes) | Check relationship page | History log shows all key events: when formed, major confrontations, intensity changes. |
| **BB-014: Love triangle dynamics** | Jade likes Derek. Derek likes Tanya. Tanya unaware. | Check all three relationship maps | Asymmetric relationships correctly displayed (Jade→Derek: romantic 80, Derek→Jade: neutral 40). |

**Edge Cases:**

- **BB-E010:** Cast member with NO relationships (isolated, ignored by others) — does UI handle gracefully?
- **BB-E011:** Maximum relationships (16 cast members = 240 possible relationship edges) — does performance degrade?
- **BB-E012:** Relationship ping-pong (Ally → Rival → Ally in 3 episodes) — does UI become confusing?

---

#### 2.1.3 Secrets & Triggers

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **BB-020: Secret discovery** | Cast member has hidden secret (pre-show scandal) | Discover via background check or informant | Burn book updates with "Secret Revealed" marker. Intel confidence jumps to 85-95%. |
| **BB-021: Secret exploitation** | Player knows Marcus's trigger (fear of failure) | Place Marcus in high-pressure competition scene | Marcus reacts as predicted (stress spike, defensive behavior). PI drops. |
| **BB-022: Trigger misidentification** | Burn book lists Jade's trigger as "criticism" but actual trigger is "abandonment" | Criticize Jade in scene | Minimal reaction. Red X on prediction. Burn book corrects entry. |
| **BB-023: Secret revelation to group** | Player uses "Secret Reveal" catalyst on cast member | Broadcast secret to all cast in scene | All cast members' relationship maps update. Target cast member's PI drops 15-30. |

**Edge Cases:**

- **BB-E020:** Secret that was TRUE at casting but no longer true (cast member reconciled with estranged family) — does burn book update or show stale data?
- **BB-E021:** Trigger stacking (multiple triggers activated in same scene) — does PI drop compound realistically?

---

### 2.2 SITUATION ENGINE (AI SIMULATION)

**What is the Situation Engine supposed to do?**

The Situation Engine resolves scenes. Player sets up the situation (cast placement, location, catalysts, information asymmetry). AI cast members act according to utility-based decision system (personality, desires, relationships, stress level). Scene generates moments (discrete events with drama value, emotional authenticity, narrative utility, legal risk, cast damage). Outcomes are emergent — player can predict likely behavior but can't script exact results.

**Test Areas:**

#### 2.2.1 AI Behavior Variety

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **SE-001: Same setup, different outcomes** | Identical scene setup (4 cast, dinner table, no catalysts) | Run scene 10 times with same initial state | Outcomes vary meaningfully. At least 7/10 runs produce distinct narrative summaries. |
| **SE-002: Personality drives behavior** | Setup scene with high-Agreeableness cast (Jade) vs. low-Agreeableness cast (Marcus) | Both placed in same confrontational situation | Jade avoids/deflects. Marcus escalates. Behavior matches personality profile. |
| **SE-003: Relationship influence** | Allies (Jade/Tanya, intensity 80) seated together vs. rivals (Marcus/Derek) | Introduce stressor catalyst | Allies support each other (lower drama spike). Rivals provoke (higher drama spike). |
| **SE-004: Stress affects rationality** | Cast member at PI 85 (stable) vs. PI 35 (fragile) | Same trigger activated on both | Stable cast: measured response. Fragile cast: irrational, volatile response. |
| **SE-005: Core desire pursuit** | Derek (desire: to be chosen) in romantic setup vs. Marcus (desire: to dominate) in same setup | Both on date with same cast member | Derek: vulnerable, earnest. Marcus: controlling, strategic. |

**Edge Cases:**

- **SE-E001:** All cast members at max stress (PI <40) in same scene — does it devolve into chaos or total shutdown?
- **SE-E002:** Scene with only 2 cast members (minimal interaction pool) — does AI still generate meaningful moments?
- **SE-E003:** Scene with 16 cast members (maximum) — does simulation complete in reasonable time (<5 seconds per design spec)?

**AI Failure Modes (High Priority to Catch):**

- **SE-F001: Robotic repetition** — Same cast member always chooses same action in same situation. No behavioral variance.
- **SE-F002: Nonsensical choices** — Cast member does something that contradicts personality, relationships, and context (e.g., Sweetheart Jade randomly attacks ally Tanya with no provocation).
- **SE-F003: Stuck behavior** — Cast member gets into infinite loop (repeating same action every tick, scene never progresses).
- **SE-F004: Emotional whiplash** — Cast member goes from calm (emotion: 20) to rage (emotion: 90) in one tick with no triggering event.

---

#### 2.2.2 Moment Generation & Tagging

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **SE-010: Drama value calculation** | High-conflict scene (rivals, alcohol catalyst, isolation) | Run scene, check generated moments | At least 2-3 moments exceed 65 drama value (spike threshold). |
| **SE-011: Low-drama scene** | Low-conflict scene (allies, no catalysts, open space) | Run scene | Most moments 30-50 drama value. Scene may end early (boring scene auto-cut per tech spec). |
| **SE-012: Emotional authenticity** | Genuine breakdown (cast at PI 40, trigger activated) | Run scene, check moment tags | High emotional authenticity (70-90). High cast damage (60-80). |
| **SE-013: Narrative utility** | Moment connects to ongoing storyline (love triangle resolution) | Run scene, check moment tags | Narrative utility 70+. Episode assembly system should prioritize this moment. |
| **SE-014: Legal risk flagging** | Cast member says something defamatory or reveals personal info | Run scene, check moment tags | Legal risk 70+. Warning indicator appears. |
| **SE-015: Confessional triggers** | Cast member experiences emotional spike (>75 intensity) | Scene completes | Confessional automatically generated and added to footage stockpile. |

**Edge Cases:**

- **SE-E010:** Scene generates ZERO moments above drama threshold (completely uneventful) — what does player see? Empty stockpile? Error message?
- **SE-E011:** Scene generates 50+ moments (extreme chaos) — does footage stockpile UI handle volume? Does it slow edit bay?

---

#### 2.2.3 Catalyst Effects

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **SE-020: Alcohol catalyst** | 4 cast members, dinner table, unlimited alcohol | Run scene | Stress increases 10-25 per tech spec. Behavior becomes more erratic. Drama value increases. |
| **SE-021: Letter from home** | Jade (whose wound is abandonment by mother) receives letter | Run scene | Trigger activated. PI drops 10-25. Emotional spike confessional generated. |
| **SE-022: Surprise guest (ex-partner)** | Derek's ex appears during date scene | Run scene | Derek's stress spikes. Relationship with date partner affected. Drama value 30-60 per spec. |
| **SE-023: Information asymmetry** | Marcus knows secret about Jade. Jade doesn't know Marcus knows. | Run scene with both | Marcus uses knowledge (subtle references). Jade confused/defensive. Dramatic irony generated. |
| **SE-024: Failed catalyst** | Plant catalyst but target cast has high stress tolerance + no relevant trigger | Run scene | Catalyst has minimal effect. Player sees "no effect" confirmation. |

**Edge Cases:**

- **SE-E020:** Multiple catalysts stacked (alcohol + letter + surprise guest) — do effects compound or override?
- **SE-E021:** Catalyst planted for cast member who refuses to participate (PI too low) — what happens?

---

### 2.3 EDIT BAY SYSTEM

**What is the Edit Bay supposed to do?**

The Edit Bay is where the player assembles broadcast episodes from raw footage. Player drags moments from stockpile into 6-8 segment slots. Each segment has: primary moment, optional confessional overlay, music cue, optional chyron. System scores episode in real-time: total drama, coherence, legal risk, cast damage. Juxtaposition bonus applies when consecutive segments show same cast in contrasting states. Player can withhold high-damage moments (trust bonus) or air them (ratings boost, editorial betrayal penalty).

**This is the unique mechanic. If this feels like data entry instead of authorship, the game fails.**

**Test Areas:**

#### 2.3.1 Timeline Assembly & Scoring

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **EB-001: Basic assembly** | Footage stockpile with 15 moments | Drag 6 moments into timeline | Episode quality score updates in real-time. Preview rating appears ("Solid episode"). |
| **EB-002: Empty segment handling** | Only 4 moments available but 6 segments required | Attempt to assemble episode | Error/warning: "Need 6 segments. Film more scenes or adjust format." Cannot broadcast incomplete episode. |
| **EB-003: High drama, low coherence** | Assemble 6 high-drama moments (DV 70+) featuring different cast each | Check quality score | Total drama high (450+). Coherence low (<40). Rating: "Incoherent mess." |
| **EB-004: Low drama, high coherence** | Assemble 6 connected moments (same 3 cast, ongoing storyline) with moderate drama (DV 40-50) | Check quality score | Total drama medium (270). Coherence high (75+). Rating: "Solid episode." |
| **EB-005: Exploitative warning** | Assemble episode with average legal risk >70 and cast damage >80 | Check quality score | Rating: "Exploitative garbage." Warning that network may pull episode. |
| **EB-006: Segment reordering** | Assemble timeline, then swap segment 2 and segment 5 | Reorder segments | Coherence score updates immediately. Juxtaposition bonuses recalculated. |

**Edge Cases:**

- **EB-E001:** What if player tries to use the same moment twice in different segments? (Should be blocked.)
- **EB-E002:** What if all footage has legal risk >60? (Player forced to air risky content or reshoot.)
- **EB-E003:** Timeline with only confessionals, no scene moments — does it score/broadcast?

---

#### 2.3.2 Juxtaposition System

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **EB-010: Emotional contrast** | Segment 3: Jade calm, saying "I'm fine" (emotion: 80). Segment 4: Jade crying alone (emotion: 15). | Place both segments consecutively | Juxtaposition bonus calculated: |80-15| * 0.5 = 32.5 drama added. Jade's editorial betrayal stat increases. |
| **EB-011: No juxtaposition** | Consecutive segments feature different cast members | Assemble timeline | No juxtaposition bonus. Editorial betrayal unchanged. |
| **EB-012: Triple juxtaposition** | 3 consecutive segments all feature Marcus in escalating emotional states | Assemble timeline | Each pair generates bonus. Marcus's editorial betrayal climbs significantly (20-30 total). |
| **EB-013: Betrayal consequence** | Air episode with Jade's editorial betrayal at 80 | Broadcast, check fallout | Jade sees broadcast. Reacts: cooperation drops -15, potential legal threat or tabloid story. |

**Edge Cases:**

- **EB-E010:** Juxtaposition between segment 6 and segment 1 (wrap-around) — does it count?
- **EB-E011:** Cast member with high self-awareness (Tanya) notices their own juxtaposition edit — do they call it out in confessional?

---

#### 2.3.3 Music Cues & Reframing

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **EB-020: Romantic reframe** | Neutral moment (Derek and Jade talking, DV 45) | Add "Romantic Swell" music cue | Audience romance perception +20. Moment reframed as potential love story. |
| **EB-021: Sinister reframe** | Same neutral moment | Add "Sinister Sting" music cue | Audience suspicion perception +25. Same moment feels manipulative/threatening. |
| **EB-022: Silence for authenticity** | High-authenticity moment (genuine breakdown, DV 78) | Select "Silence" music cue | Authenticity perception +30. Entertainment -10. Feels raw. |
| **EB-023: Tonal whiplash** | Segment 2: comedic moment with "Comedic Bounce." Segment 3: tragic moment with "Melancholy Piano." | Place consecutively | Coherence penalty -8 (tonal whiplash detected). |

---

#### 2.3.4 Confessional Overlays

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **EB-030: Direct overlay** | Segment shows Marcus confronting Jade. | Add Marcus confessional: "I had to say something." | Confessional recontextualizes moment as justified. Audience perception shifts. |
| **EB-031: Contradictory overlay** | Segment shows Derek comforting Jade. | Add Derek confessional from 2 days earlier: "I don't trust her." | Juxtaposition creates dramatic irony. Audience questions Derek's sincerity. Editorial betrayal increases. |
| **EB-032: Missing confessional** | No confessionals available for key moment | Attempt to add overlay | "No confessionals available" message. Player must air segment without overlay or trigger new confessional. |

---

#### 2.3.5 Withheld Moments & Strategic Editing

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **EB-040: Withholding high-damage moment** | Jade genuine breakdown (DV 85, cast damage 90) in stockpile | Do NOT use in episode. Save for later. | Moment tagged "Withheld Moment." If aired later: 1.5x drama value. If never aired: Jade's trust +10. |
| **EB-041: Delayed payoff** | Withhold breakdown moment in Episode 5. Air it in Episode 8. | Broadcast Episode 8 with withheld moment | Drama value: 85 * 1.5 = 127.5. Higher impact due to delayed gratification. |
| **EB-042: Mercy edit** | Cast member at PI 40. Player has footage of their humiliation but chooses softer edit. | Air positive/neutral moments only | Cast member's cooperation +5. Ratings may suffer (less drama). Player sacrifices performance for ethics. |

**Edge Cases:**

- **EB-E040:** Withheld moment stockpile limit — if player withholds 50+ moments, does UI/performance degrade?
- **EB-E041:** Withheld moment becomes irrelevant (cast member eliminated, context changed) — does system flag or auto-expire?

---

#### 2.3.6 Edit Bay Usability (CRITICAL)

These are not bug tests. These are feel tests. If any of these fail, the edit bay needs redesign.

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **EB-U01: Assembly speed** | Experienced player, full footage stockpile | Time episode assembly | Completes in <10 minutes. Player doesn't feel rushed or bored. |
| **EB-U02: Creative satisfaction** | Playtest edit bay in isolation | Assemble episode, survey tester | Player reports feeling "creative" or "in control." Satisfaction >7/10. |
| **EB-U03: Authorship feel** | Player assembles two different episodes from same footage | Compare outcomes | Episodes feel distinct. Player can articulate the different "stories" they told. |
| **EB-U04: Clarity of scoring** | Player makes specific edit choice (add sinister music to neutral scene) | Check quality score change | Player can explain WHY score changed. Attribution is clear. |
| **EB-U05: Drag-drop responsiveness** | Drag moment from stockpile to timeline | Observe UI response | Immediate feedback (visual snap, sound effect). Feels snappy, not laggy. |

**KILL CONDITION:** If >40% of playtesters report edit bay as "tedious," "confusing," or "feels like work" at Milestone 2, the system needs radical simplification or redesign.

---

### 2.4 RATINGS ENGINE

**What is the Ratings Engine supposed to do?**

After episode broadcast, the Ratings Engine calculates Nielsen rating, audience segment satisfaction (Drama Addicts, Romantics, Justice Seekers, Strategists, Chaos Agents), advertiser confidence, and network satisfaction. Player receives detailed report attributing rating changes to specific segments/decisions. Social media feed generates procedural viewer reactions.

**The feedback loop is CRITICAL. If the player doesn't understand why ratings went up/down, they can't improve.**

**Test Areas:**

#### 2.4.1 Nielsen Rating Calculation

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **RE-001: High drama episode** | Episode with total drama 450+, coherence 70+ | Broadcast | Nielsen rating increases 0.3-0.5 from baseline. Attribution report shows drama contribution. |
| **RE-002: Boring episode** | Episode with total drama 180, coherence 50 | Broadcast | Nielsen rating drops 0.2-0.3. Attribution shows "low drama" penalty. |
| **RE-003: Incoherent episode** | High drama (420) but low coherence (35) | Broadcast | Rating lower than expected. Coherence penalty visible in report. |
| **RE-004: Cliffhanger retention** | Episode 5 ends with unresolved tension (cliffhanger segment) | Broadcast, check Episode 6 initial viewership | Episode 6 starts with 10-25% retention bonus. |
| **RE-005: Audience fatigue** | 4 consecutive high-drama episodes (DV 400+) | Broadcast 5th similar episode | Fatigue penalty applies. Diminishing returns on drama. Rating plateaus or drops. |
| **RE-006: Scandal penalty** | Major fallout event (cast walkoff, lawsuit) occurred last episode | Broadcast current episode | Scandal penalty -0.2 to -0.5 rating. |

**Edge Cases:**

- **RE-E001:** Rating calculation with missing variables (e.g., no cliffhanger data from previous episode on Season 1 Episode 1) — does formula handle gracefully?
- **RE-E002:** Rating exceeds historical maximum (4.0+ Nielsen) — is this clamped or allowed?

---

#### 2.4.2 Audience Segment Satisfaction

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **RE-010: Drama Addicts satisfied** | Episode with 3+ confrontation moments, high conflict | Broadcast, check segment report | Drama Addicts satisfaction 75-90. Retention high. |
| **RE-011: Romantics disappointed** | Episode with zero romantic moments, all conflict | Broadcast | Romantics satisfaction <40. Warning: "Romantics dissatisfied 1/3 episodes." |
| **RE-012: Justice Seekers satisfied** | Villain (Marcus) receives comeuppance or karma | Broadcast | Justice Seekers satisfaction 70-85. |
| **RE-013: Strategists engaged** | Episode features alliance betrayal, strategic gameplay | Broadcast | Strategists satisfaction 70-80. |
| **RE-014: Chaos Agents thrilled** | Episode features meltdown, breakdown, unexpected walkoff | Broadcast | Chaos Agents satisfaction 85-95. |
| **RE-015: Segment exodus** | Romantics at <30% satisfaction for 3 consecutive episodes | Broadcast 3rd low-satisfaction episode | SEGMENT EXODUS event triggers. Romantics drop by 40%. Notification appears. |

**Edge Cases:**

- **RE-E010:** All segments simultaneously at <30% satisfaction — is this possible? What happens?
- **RE-E011:** One segment at 100% satisfaction (perfectly served) — does this have special effects/unlocks?

---

#### 2.4.3 Advertiser Confidence & Network Satisfaction

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **RE-020: High ratings, low brand safety** | Nielsen 3.2 but average legal risk 75 | Check advertiser confidence | ACI drops due to brand safety score penalty. Revenue suffers despite ratings. |
| **RE-021: Balanced episode** | Nielsen 2.5, legal risk 30, good demographics | Check ACI | ACI 65-75. Healthy ad revenue. |
| **RE-022: Network intervention** | NSS below 40 for 3 consecutive episodes | Broadcast 3rd low-NSS episode | Network intervention event: mandatory format change, cast addition, or showrunner "guidance." |
| **RE-023: Network cancellation threat** | NSS below 25 for 2 consecutive episodes | Broadcast 2nd episode | "Cancellation review" warning. Player has 2 episodes to recover or season ends early. |
| **RE-024: Creative freedom unlock** | NSS above 75 for full season | Complete season | Bonus unlocked: larger budget, more casting options, format experimentation rights. |

---

#### 2.4.4 Ratings Report Clarity (CRITICAL)

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **RE-U01: Attribution legibility** | Episode broadcast | Read ratings report | Player can identify top 3 factors affecting rating (e.g., "Drama Addicts +0.3 from Marcus/Jade confrontation," "Coherence penalty -0.1," "Cliffhanger retention +0.15"). |
| **RE-U02: Segment breakdown** | Check audience segment section | Read report | Each segment's satisfaction score has explanation (e.g., "Romantics 35: No love story moments aired"). |
| **RE-U03: Actionable feedback** | Rating dropped significantly | Read report | Player understands what went wrong and what to change next episode. |

**KILL CONDITION:** If playtesters report ratings feel "random" or "can't figure out why ratings changed," the attribution system needs clearer communication.

---

#### 2.4.5 Social Media Feed Generation

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **RE-030: Feed relevance** | Episode featuring major Marcus/Jade confrontation airs | Check social media feed | Feed includes posts referencing confrontation (e.g., "OMG Marcus just said WHAT?"). |
| **RE-031: Sentiment distribution** | High-rated episode (3.0+) | Check feed | Majority positive sentiment. Some negative (realistic mix). |
| **RE-032: Low-rated episode** | Low-rated episode (1.5) | Check feed | Majority negative/bored sentiment ("This episode was a snoozefest"). |
| **RE-033: Cast-specific reactions** | Jade receives "villain edit" | Check feed | Posts reference Jade specifically ("Jade is the worst," "Feel bad for Jade"). |

**Edge Cases:**

- **RE-E030:** Feed generation for episode with zero notable moments (completely bland) — does it generate generic filler posts or flag "no buzz"?

---

### 2.5 FALLOUT SYSTEM

**What is the Fallout System supposed to do?**

Tracks cast member Psychological Integrity (PI, 0-100). PI decays based on drama involvement, unfavorable edits, stress, triggered traumas. PI recovers through positive interactions, support, reduced workload. Low PI triggers consequence events: breakdowns, walkoffs, legal threats. When cast leaves, departure PI determines post-show outcome (positive, neutral, negative, severe). Negative outcomes damage showrunner reputation, affecting future casting pools.

**This is the moral weight mechanic. If consequences feel disconnected from player actions, the thematic core fails.**

**Test Areas:**

#### 2.5.1 PI Decay & Recovery

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **FS-001: Base decay** | Cast member at PI 100, no drama involvement | Advance 1 episode with minimal scenes | PI drops 2-5 (base stress from being on show). |
| **FS-002: Drama involvement decay** | Jade involved in high-drama scene (DV 80) | Advance 1 episode | PI drops 2-5 (base) + ~6 (drama involvement: 80 * 0.08). Total: -8 to -11. |
| **FS-003: Unfavorable edit decay** | Marcus featured in episode with high cast damage (70) | Broadcast episode, advance | PI drops additional ~8 (70 * 0.12). Marcus sees episode, reacts. |
| **FS-004: Trigger activation decay** | Jade's abandonment trigger activated in scene | Advance episode | PI drops 10-25 on top of other decay sources. |
| **FS-005: Positive recovery** | Cast member has positive interaction (support from ally) | Advance episode | PI recovers 2-6. |
| **FS-006: Producer support recovery** | Player invests time in producer-cast conversation | Spend action, advance | PI recovers 4-8. (Costs player time/resources.) |
| **FS-007: Day off recovery** | Reduce cast member's scene load (give them an episode off) | Advance episode | PI recovers 5-10. (Costs content — less footage featuring them.) |

**Edge Cases:**

- **FS-E001:** PI decay exceeds 100 in one episode (multiple triggers + high drama + bad edit) — is this clamped or does PI go negative?
- **FS-E002:** Simultaneous decay and recovery (cast has positive interaction but also gets bad edit) — which takes priority or do they net?

---

#### 2.5.2 PI Threshold Events

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **FS-010: Stressed state (60-79 PI)** | Cast member at PI 65 | Observe behavior in scenes | Increased emotional volatility. Better TV (higher drama potential) but less predictable. |
| **FS-011: Fragile state (40-59 PI)** | Cast member at PI 45 | Observe behavior | Erratic behavior, paranoia, or withdrawal. May refuse scenes. Confessional quality degrades. |
| **FS-012: Breaking state (20-39 PI)** | Cast member at PI 25 | Advance episode | Legal review triggered. Network concern event. Tabloid risk. Cast displays visible distress. |
| **FS-013: Broken state (1-19 PI)** | Cast member at PI 15 | Advance episode | 60% chance walkoff, 40% chance breakdown. Production stops. Fallout event notification. |
| **FS-014: Destroyed state (PI 0)** | Cast member reaches PI 0 | Advance | Cast removed from show. Lawsuit probable. Scandal. Reputation damage. |
| **FS-015: Optimal exploitation (55-70 PI)** | Maintain cast at PI 60-65 for multiple episodes | Observe footage quality | "Sweet spot" confirmed: volatile enough for good TV, stable enough for reliability. |

**Edge Cases:**

- **FS-E010:** Multiple cast members hit Breaking state simultaneously — does production halt entirely?
- **FS-E011:** Cast member recovers from Broken state (PI climbs from 15 to 50) — do past threshold events have lasting effects?

---

#### 2.5.3 Post-Show Outcomes

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **FS-020: High-PI departure (80-100)** | Jade eliminated at PI 90 | Season ends, check post-show report | 60% chance positive outcome ("Jade thriving in new career"). 30% neutral. 8% negative. 2% severe. |
| **FS-021: Mid-PI departure (60-79)** | Marcus eliminated at PI 70 | Check post-show | 35% positive. 35% neutral. 22% negative. 8% severe. |
| **FS-022: Low-PI departure (20-39)** | Ricki eliminated at PI 30 | Check post-show | 5% positive. 15% neutral. 40% negative. 40% severe ("Ricki struggling with addiction/mental health"). |
| **FS-023: Destroyed departure (PI 0)** | Derek removed at PI 0 | Check post-show | 2% positive. 5% neutral. 33% negative. 60% severe ("Derek hospitalized," "Lawsuit filed"). |
| **FS-024: Reputation damage** | High-fame cast (Derek, 80 fame level) has severe negative outcome | Advance between seasons | Showrunner reputation drops 30-50 points. Publicized scandal. Future casting pool quality degrades. |
| **FS-025: Positive outcome** | Tanya leaves at PI 85, gets positive outcome | Advance | Reputation bonus +5 to +10. Tabloid: "Former cast member credits show for success." |

**Edge Cases:**

- **FS-E020:** All cast members depart with severe outcomes (PI <20) — does reputation bottom out? Can player recover?
- **FS-E021:** Same cast member cast again in later season (returnee twist) — does their PI history carry over or reset?

---

#### 2.5.4 Consequence Visibility (CRITICAL)

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **FS-U01: Causation clarity** | Jade's PI drops from 65 to 35 in one episode | Check PI breakdown | Report shows: "Unfavorable edit -15, lost alliance with Tanya -8, trigger activated -12." Player understands cause. |
| **FS-U02: Fallout event connection** | Marcus walks off after 3 episodes of heavy exploitation | Event notification | Player can trace: high drama scenes → bad edits → PI decay → walkoff. Feels earned, not random. |
| **FS-U03: Long-tail consequences** | Season 2 cast references Season 1 scandal during confessional | Observe confessional | Organic callback. Player sees legacy of past choices. |

**KILL CONDITION:** If players report fallout feels "random" or "unfair," the causation tracking needs better UI/communication.

---

### 2.6 SAVE/LOAD SYSTEM

**What is the Save/Load system supposed to do?**

Persist entire game state (season progress, cast states, footage stockpile, showrunner reputation, network history, audience segments, post-show outcomes, fallout events, unlocks). Save format is JSON. Auto-save after episode broadcast, major decisions, and every 10 minutes. Manual saves in separate slots. Backup system for corruption recovery. Steam Cloud sync.

**Save corruption kills player trust. This MUST be bulletproof.**

**Test Areas:**

#### 2.6.1 Save State Completeness

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **SL-001: Basic save/load** | Mid-season (Episode 4 of Season 2) | Save, quit, reload | All state restored: cast PI, relationships, footage stockpile, episode number, reputation. |
| **SL-002: Deep state preservation** | Complex game state (12 cast, 50+ stockpile moments, 3 pending fallout events) | Save, reload | All cast histories intact. All footage tagged correctly. All events queued. |
| **SL-003: Cross-session continuity** | Play Episode 5, save, quit. Reload next day. | Load save | Game continues exactly where left off. No state loss. |
| **SL-004: Multiple save slots** | Save in Slot 1 (Season 2). Save in Slot 2 (Season 4). | Load Slot 1 | Correct save loaded. No cross-contamination with Slot 2. |
| **SL-005: Auto-save functionality** | Play for 12 minutes without manual save | Check auto-save files | Auto-save created at 10-minute mark. Rotates (auto-save-1, auto-save-2, auto-save-3). |

**Edge Cases:**

- **SL-E001:** Save during edit bay mid-assembly — does it preserve draft timeline?
- **SL-E002:** Save during scene simulation — does it handle transient AI state or wait for completion?
- **SL-E003:** Save file size exceeds expected (>5 MB) — is there a data leak?

---

#### 2.6.2 Save Corruption & Recovery

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **SL-010: Backup restoration** | Corrupt main save file (manually damage JSON) | Attempt load | System detects corruption, loads .backup file automatically. Player warned but continues. |
| **SL-011: Total corruption (no backup)** | Corrupt both main and backup | Attempt load | Error dialog: "Save corrupted. Unable to recover. Start new game?" No crash. |
| **SL-012: Steam Cloud sync** | Save on PC, load on Steam Deck | Load from Cloud | Save transfers correctly. All state intact. |
| **SL-013: Cloud conflict** | Play on PC (auto-save). Play on Steam Deck (different progress). | Return to PC, load | Conflict resolution dialog: "Local save vs. Cloud save. Which to use?" |
| **SL-014: Power loss during save** | Simulate power loss mid-save (kill process during write) | Reload | Either backup loads OR previous auto-save loads. No complete data loss. |

**Critical Test:**

- **SL-C001:** Stress test saves. Create 100 sequential saves over 50 hours of gameplay. Load random saves. Verify all load correctly. No degradation/corruption over time.

---

#### 2.6.3 Save/Load Performance

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **SL-020: Save speed** | Mid-season (typical game state) | Trigger save, measure time | Save completes in <1 second. No noticeable freeze. |
| **SL-021: Load speed** | Mid-season save file (~1 MB) | Load save, measure time | Load completes in <2 seconds on PC, <3 seconds on Steam Deck. |
| **SL-022: Large save handling** | Season 8, max cast history, 200+ legacy outcomes | Save/load | Save file ~2 MB. Load still <3 seconds. Performance acceptable. |

---

### 2.7 PERFORMANCE & OPTIMIZATION

**Performance targets from tech doc:**
- **PC (mid-range):** 60 FPS at 1920x1080, <2s load times
- **PC (high-end):** 60 FPS at 4K, <1s load times
- **Steam Deck:** 60 FPS at 1280x800, <3s load times

**Test Areas:**

#### 2.7.1 Frame Rate Stability

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **PF-001: Edit bay performance** | Full footage stockpile (50 moments), all UI elements visible | Navigate edit bay, drag moments | Maintains 60 FPS. No drops during drag-drop. |
| **PF-002: Burn book navigation** | 16 cast members, all dossiers fully populated | Rapidly switch between dossiers | 60 FPS maintained. Transitions smooth. |
| **PF-003: Scene simulation** | 16 cast members, 120-tick scene | Run scene | Background thread handles AI. Main thread maintains 60 FPS for UI. |
| **PF-004: Multi-scene stress** | Run 8 scenes back-to-back (full episode) | Monitor FPS throughout | No degradation. Consistent 60 FPS. |
| **PF-005: Long session** | Play for 4+ hours continuously | Monitor FPS over time | No memory leaks. FPS stable throughout session. |

**Edge Cases:**

- **PF-E001:** 16 cast members all visible on relationship graph simultaneously — does graph rendering tank FPS?
- **PF-E002:** Footage stockpile exceeds 100 moments (unusual but possible if player never edits) — does UI become unusable?

---

#### 2.7.2 Load Time Compliance

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **PF-010: Episode start load** | Begin new episode from showrunner office | Trigger episode start, measure load time | <2s on PC, <3s on Steam Deck. |
| **PF-011: Save game load** | Load mid-season save | Measure load time | <2s on PC, <3s on Steam Deck. |
| **PF-012: Season transition load** | Complete season, transition to between-seasons management | Measure transition time | <3s total. |

---

#### 2.7.3 Memory & Resource Usage

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **PF-020: Memory footprint** | Full season in progress (16 cast, all systems active) | Monitor RAM usage | <100 MB total (well within budget). |
| **PF-021: Memory leaks** | Play for 6+ hours | Monitor memory over time | No significant growth. No leaks detected. |
| **PF-022: Audio streaming** | Multiple music cues playing, SFX triggering | Monitor memory | Audio streamed from disk, not all loaded into RAM. Memory stable. |

---

#### 2.7.4 Steam Deck Specific

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **PF-030: Touchscreen navigation** | Burn book open | Navigate using touchscreen | Touch targets large enough (no mis-taps). Scrolling smooth. |
| **PF-031: Trackpad precision** | Edit bay timeline | Use trackpad to scrub/drag moments | Precision adequate. No frustration. |
| **PF-032: Battery life** | Full gameplay session | Monitor battery consumption | 4-5 hours per spec. Acceptable for management sim. |
| **PF-033: Text readability** | All UI screens | Read text on 7-inch screen | Font size +10% applied. Text readable without strain. |

---

### 2.8 UI/UX CLARITY & USABILITY

**These are not bug tests. These are experience tests. The game can be bug-free and still fail here.**

#### 2.8.1 Information Hierarchy

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **UX-001: Burn book scannability** | 16 cast members, full dossiers | Task: "Find all cast with stress tolerance <50" | Player completes in <30 seconds. Info is scannable. |
| **UX-002: Edit bay stockpile filtering** | 50 moments in stockpile | Task: "Find all moments featuring Jade with DV >65" | Sorting/filtering tools exist and work. Player finds moments quickly. |
| **UX-003: Ratings report actionability** | Low ratings this episode | Task: "Identify why ratings dropped" | Player reads report, identifies cause in <1 minute. |
| **UX-004: PI warning visibility** | 3 cast members below PI 50 | Check showrunner office dashboard | Red warning indicators visible. Player alerted to crisis without needing to check each dossier. |

---

#### 2.8.2 Onboarding & Tutorial

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **UX-010: Season 1 tutorial** | New player, first launch | Play through Episode 1 | Tutorial explains: burn book, scene setup, edit bay, ratings. Not overwhelming. Playtest satisfaction >6/10. |
| **UX-011: Progressive disclosure** | Season 1 vs. Season 3 UI | Compare | Season 1 shows simplified UI (fewer stats, fewer tools). Season 3 unlocks advanced features gradually. |
| **UX-012: Advisor hints** | Player struggles (e.g., low ratings 3 episodes in a row) | Check for hints | Optional hint system offers suggestions ("Try airing more romance — Romantics are at 30%"). Not intrusive. |

---

#### 2.8.3 Accessibility

| Test Case | Preconditions | Steps | Expected Result |
|-----------|--------------|-------|-----------------|
| **UX-020: Text scaling** | Set text size to 150% | Navigate all UI screens | Text readable, doesn't overflow containers. |
| **UX-021: Colorblind mode** | Enable deuteranopia mode | Check all UI elements | Color-coded info (red/green warnings) uses additional indicators (icons, patterns). |
| **UX-022: Contrast** | Default UI | Check text against backgrounds | All text meets WCAG AA contrast standards (4.5:1 minimum). |

---

## 3. EDGE CASES & STRESS TESTS

These are the scenarios that break systems. The places where assumptions fail.

### 3.1 System Limit Tests

| Test Case | Description | Expected Behavior |
|-----------|-------------|-------------------|
| **EDGE-001: Zero cast members** | All cast eliminated/walked off before finale | Error state: "Cannot continue season. Insufficient cast." Option to emergency-cast replacements or end season early. |
| **EDGE-002: Maximum cast members** | 16 cast, all active, all in one scene | Scene simulation completes in <5s per spec. UI handles 16 portraits/names. No performance degradation. |
| **EDGE-003: Empty footage stockpile** | Attempt to assemble episode with zero moments filmed | Error: "No footage available. Film scenes before editing." Cannot proceed to broadcast. |
| **EDGE-004: Maximum footage stockpile** | 200+ moments accumulated over season | UI uses virtualized scrolling. Performance remains stable. Moments remain findable (search/filter required). |
| **EDGE-005: All segments at 0% satisfaction** | Episode airs that every audience segment hates | Catastrophic rating drop. NSS plummets. "Network emergency meeting" event triggered. |
| **EDGE-006: Reputation at 0** | Showrunner reputation bottoms out | Casting pool is bottom-tier only (D-tier cast). Budget minimal. Network micromanages. Game still playable but extremely difficult. |
| **EDGE-007: Reputation at 100** | Showrunner reputation maxed | Casting pool is S+-tier. Budget 2x. Full creative freedom. Network hands-off. "You've made it" acknowledgment. |
| **EDGE-008: All cast at PI 100** | Entire cast perfectly stable (no drama) | Scenes generate low drama. Ratings suffer. Game teaches: exploitation is mechanically optimal (but morally questionable). |
| **EDGE-009: All cast at PI <20** | Entire cast breaking simultaneously | Production halts. Multiple walkoffs/breakdowns. Season ends early. Reputation catastrophe. |

---

### 3.2 Sequence Break & Exploit Tests

| Test Case | Description | Expected Behavior |
|-----------|-------------|-------------------|
| **EDGE-020: Skip edit bay** | Film scenes, attempt to auto-broadcast without editing | Blocked. Must assemble episode before broadcast. No auto-compile. |
| **EDGE-021: Infinite budget exploit** | Attempt to manipulate economy (e.g., save-scum high ratings) | Economy is deterministic but not exploitable. Repeated identical episodes generate audience fatigue (diminishing returns). |
| **EDGE-022: Duplicate cast members** | Attempt to cast same procedurally generated cast in multiple slots | Blocked. Each cast member unique per season. |
| **EDGE-023: Edit published episode** | Attempt to re-edit episode after broadcast | Blocked. Episodes locked after broadcast. Can only edit current episode. |
| **EDGE-024: Delete critical save** | Manually delete auto-save files | Game detects, warns player. Offers to create new auto-save chain. No crash. |

---

### 3.3 Data Integrity Tests

| Test Case | Description | Expected Behavior |
|-----------|-------------|-------------------|
| **EDGE-030: Relationship orphan** | Cast member A eliminated. Cast member B still has relationship entry pointing to A. | Relationship marked "eliminated" or removed. No broken references. |
| **EDGE-031: Confessional without context** | Confessional generated for scene that was never filmed (edge case bug) | Confessional appears in stockpile but has no valid context tags. Flagged for QA. Should not occur in normal play. |
| **EDGE-032: Negative PI** | Through stacking exploits, PI drops below 0 | PI clamped at 0. "Destroyed" state triggered. No negative values displayed. |
| **EDGE-033: PI above 100** | Through stacking recovery, PI exceeds 100 | PI clamped at 100. No overflow. |
| **EDGE-034: Infinite loop in AI** | AI cast member gets stuck in decision loop (bug) | Timeout after 5 seconds. Scene forcibly ends with error report. Flagged for dev. |

---

### 3.4 Localization Edge Cases (Future)

| Test Case | Description | Expected Behavior |
|-----------|-------------|-------------------|
| **EDGE-040: Long character names** | Cast member name exceeds UI container (e.g., 30+ characters) | Name truncates gracefully (ellipsis). Full name on hover/tooltip. |
| **EDGE-041: Special characters in chyrons** | Player writes chyron with emoji, non-ASCII characters | Characters render correctly or are filtered with warning. No crash. |
| **EDGE-042: RTL language support** | UI in Arabic/Hebrew (future localization) | Layout mirrors correctly. Text alignment correct. (Not v1 scope but design consideration.) |

---

## 4. RISK ASSESSMENT

### 4.1 Critical Risks (SHOWSTOPPERS)

| Risk | Impact | Likelihood | Detection | Mitigation |
|------|--------|------------|-----------|------------|
| **AI generates boring, repetitive scenes** | CRITICAL — Core loop fails | MEDIUM | Milestone 1 playtest | Prototype AI first. Kill condition: <70% playtest satisfaction. If fails, pivot to more scripted system or abort. |
| **Edit bay feels tedious/unclear** | CRITICAL — Unique mechanic fails | MEDIUM | Milestone 2 playtest | Isolated edit bay testing. Kill condition: >40% report tedium. If fails, radical simplification. |
| **Save corruption in wild** | CRITICAL — Data loss kills trust | LOW | Beta testing, telemetry | Extensive save/load QA. Backup system. Auto-save rotation. Sentry crash reporting. |
| **Performance <60 FPS on target hardware** | HIGH — Game feels sluggish | MEDIUM | Milestone 3 profiling | Profile early and often. Optimize hot paths (AI, UI rendering). Cut features if needed. |
| **Ratings feedback opaque** | HIGH — Player can't learn/improve | MEDIUM | Milestone 2-3 | Playtests focused on "can you explain why rating changed?" Iterate on attribution clarity. |

---

### 4.2 High Risks (MAJOR DELAYS)

| Risk | Impact | Likelihood | Detection | Mitigation |
|------|--------|------------|-----------|------------|
| **Procedural cast members feel samey** | HIGH — Emotional core fails | MEDIUM | Milestone 3 | Quality filter on generation. Large archetype/trait pools. Playtest: "Can you name 3 cast members after one season?" |
| **Balance is broken (too easy/hard)** | HIGH — Frustration or boredom | HIGH | Beta testing | Difficulty modes. Telemetry tracking player success rates. Tune based on data. |
| **Fallout consequences feel random** | HIGH — Moral weight fails | MEDIUM | Milestone 4 | Causation clarity. Always show WHY (PI breakdown, attribution). Playtest: "Did this feel earned?" |
| **UI information overload** | HIGH — Players overwhelmed | MEDIUM | Milestone 2-3 | Progressive disclosure. Tutorial season with simplified UI. User testing. |
| **Scope creep** | HIGH — Ship date slips | HIGH | Ongoing | Feature freeze after design doc. Ruthless cut discipline. Stretch goals are post-launch. |

---

### 4.3 Medium Risks (ANNOYING BUT RECOVERABLE)

| Risk | Impact | Likelihood | Detection | Mitigation |
|------|--------|------------|-----------|------------|
| **Steam Deck controller scheme awkward** | MEDIUM | MEDIUM | Milestone 5 | Playtest on Deck early. Adjust touch targets, add controller shortcuts. Deck is secondary platform. |
| **Audio timing issues** | MEDIUM | LOW | Polish phase | Audio middleware or manual timing. Playtest feedback. |
| **Localization bugs** | MEDIUM | N/A (v1 English-only) | Post-launch | Plan ahead: use string keys, avoid hardcoded text. |
| **Mod support requests** | LOW | HIGH (community will mod) | Post-launch | JSON saves are inherently moddable. Decide later if we support officially. |

---

### 4.4 Ethical/Thematic Risks

| Risk | Impact | Likelihood | Detection | Mitigation |
|------|--------|------------|-----------|------------|
| **Players don't feel moral weight** | CRITICAL (thematic failure) | MEDIUM | Milestone 4-6 | Track "I felt uncomfortable" moments in playtests. If <50%, amplify consequences. |
| **Game feels preachy** | HIGH | LOW | Playtesting | Never moralize. Show consequences, don't judge. Playtest for tone. |
| **Exploitation is too fun** | MEDIUM (sends wrong message) | MEDIUM | Beta | Ensure fallout system has teeth. Exploitation is optimal short-term but costly long-term. Balance carefully. |
| **Trivializes real issues** | HIGH (reputational) | LOW | Sensitivity review | Narrative team + external sensitivity readers review content for harmful tropes. |

---

## 5. QUALITY GATES (MILESTONE PASS CONDITIONS)

### Milestone 1: AI Prototype (Month 1-3)

**MUST PASS:**
- [ ] AI produces 10 distinct outcomes from same scene setup (10 runs)
- [ ] At least 1 "surprise" per playthrough (unexpected but believable behavior)
- [ ] Scene resolution completes in <5 seconds
- [ ] Playtest satisfaction >7/10 on AI behavior quality
- [ ] No infinite loops, crashes, or nonsensical AI choices

**NICE TO HAVE:**
- [ ] Personality traits visibly affect behavior (Agreeable vs. Disagreeable cast act differently)
- [ ] Relationship dynamics influence interactions (allies support, rivals provoke)

**KILL CONDITION:** If AI satisfaction <7/10 after iteration, pivot or abort project.

---

### Milestone 2: Vertical Slice (Month 4-6)

**MUST PASS:**
- [ ] Full episode loop (cast → shoot 4 scenes → edit → broadcast → ratings) completes without blocking bugs
- [ ] Episode completion time: 25-35 minutes
- [ ] Edit bay playtest satisfaction >7/10 (feels like authorship, not data entry)
- [ ] Ratings report clarity: Players can explain why rating changed
- [ ] 60 FPS maintained throughout episode
- [ ] Save/load functional (preserves all state)

**NICE TO HAVE:**
- [ ] Juxtaposition system generates noticeable drama bonuses
- [ ] Music cues visibly reframe moments
- [ ] Confessional overlays feel meaningful

**KILL CONDITION:** If edit bay tedium >40% in playtests, radical simplification required.

---

### Milestone 3: Full Season (Month 7-10)

**MUST PASS:**
- [ ] Complete season (8 episodes) playable start to finish
- [ ] Season arc feels complete (beginning, middle, climax)
- [ ] Playtest: 80% of testers can name and describe 3+ cast members
- [ ] Save/load works flawlessly (no corruption, all state preserved)
- [ ] Fallout system functional (PI tracking, consequence events trigger correctly)
- [ ] No performance degradation over 4+ hour session
- [ ] Tutorial/onboarding adequate (new players can complete Season 1)

**NICE TO HAVE:**
- [ ] Cast members form emergent alliances/rivalries organically
- [ ] Post-show outcomes surface believably

---

### Milestone 4: Multi-Season Campaign (Month 11-14)

**MUST PASS:**
- [ ] Seasons 1-4 playable with full progression
- [ ] Reputation system unlocks function correctly
- [ ] Post-show outcomes affect reputation and future casting pools
- [ ] Legacy consequences (former cast callbacks, tabloid stories) surface organically
- [ ] Between-season management flow works
- [ ] Balance feels fair (not too easy/hard)

**NICE TO HAVE:**
- [ ] Difficulty modes all playable and distinct
- [ ] Showrunner legacy feels meaningful over 4 seasons

---

### Milestone 5: Full Content (Month 15-18)

**MUST PASS:**
- [ ] All 8 seasons playable
- [ ] All systems unlocked and functional
- [ ] Performance targets met: 60 FPS, <2s loads (PC), <3s loads (Deck)
- [ ] All difficulty modes tuned
- [ ] Steam integration works (achievements, cloud saves, stats)
- [ ] Polish pass complete (animations, SFX, visual feedback)
- [ ] Zero critical bugs (crashes, softlocks, data loss)
- [ ] <20 high-priority bugs in backlog

**NICE TO HAVE:**
- [ ] Advanced edit bay tools feel powerful
- [ ] Reputation tiers feel distinct
- [ ] Cultural moments system (stretch goal) functional

---

### Milestone 6: Beta & Polish (Month 19-22)

**MUST PASS:**
- [ ] <5 critical bugs
- [ ] Balance validated via telemetry (player success rates in target range)
- [ ] Closed beta satisfaction >75% (Steam review equivalent)
- [ ] Steam Deck performance validated (60 FPS, 4-5hr battery)
- [ ] Save corruption rate <0.1% (telemetry)
- [ ] Player engagement: >50% complete 2+ seasons
- [ ] Moral weight validated: >50% report feeling "complicit" or "uncomfortable" at some point

**NICE TO HAVE:**
- [ ] Positive word-of-mouth from beta testers
- [ ] No major balance complaints

---

### Milestone 7: Launch (Month 23-24)

**MUST PASS:**
- [ ] Zero critical bugs in launch build
- [ ] Day-one patch ready (for any last-minute issues)
- [ ] Steam store page live and polished
- [ ] Clean launch (no server issues, game-breaking bugs)
- [ ] Crash rate <1% (telemetry, first 48 hours)
- [ ] Positive initial reviews (target: >75% positive on Steam)

**NICE TO HAVE:**
- [ ] Strong launch sales
- [ ] Community engagement (Discord, Reddit activity)

---

## 6. REGRESSION TESTING CHECKLIST

After any major code change, bug fix, or milestone delivery, run this checklist to verify no regressions.

### 6.1 Core Loop Regression

- [ ] Cast member creation works (no broken archetypes)
- [ ] Burn book displays correctly (all intel types visible)
- [ ] Scene setup accepts cast placement (drag-drop functional)
- [ ] Scene simulation completes without crash
- [ ] Footage stockpile populates correctly
- [ ] Edit bay timeline accepts moments (drag-drop functional)
- [ ] Episode quality score calculates in real-time
- [ ] Broadcast triggers correctly
- [ ] Ratings report generates with attribution
- [ ] PI decay/recovery calculations correct
- [ ] Save/load preserves state

### 6.2 System Integration Regression

- [ ] Burn book intel affects scene predictions (causation intact)
- [ ] Scene outcomes update burn book (relationship changes, intel updates)
- [ ] Edit bay episode content affects ratings (high drama = higher rating)
- [ ] Ratings affect budget and reputation (economic loop intact)
- [ ] Fallout events trigger at correct PI thresholds
- [ ] Post-show outcomes affect future seasons (legacy intact)
- [ ] Reputation unlocks function (better cast pools at higher rep)

### 6.3 UI Regression

- [ ] Burn book navigation (tab switching, scrolling)
- [ ] Edit bay drag-drop responsiveness
- [ ] Multi-camera feed switching
- [ ] Ratings report legibility
- [ ] Text rendering (no missing fonts, garbled text)
- [ ] Tooltips appear on hover
- [ ] Button states (hover, click, disabled) display correctly

### 6.4 Performance Regression

- [ ] Frame rate maintains 60 FPS in edit bay
- [ ] Scene simulation completes in <5s (16 cast)
- [ ] Load times <2s (PC), <3s (Deck)
- [ ] No memory leaks over 4-hour session

### 6.5 Save/Load Regression

- [ ] Save completes without error
- [ ] Load restores exact state
- [ ] Auto-save creates files correctly
- [ ] Backup system functional
- [ ] Steam Cloud sync works

---

## 7. PERFORMANCE BENCHMARKS

### 7.1 Frame Rate Targets

| Scenario | Target FPS | Measurement Point | Pass Condition |
|----------|-----------|-------------------|----------------|
| Edit bay (full stockpile) | 60 | During drag-drop operations | Never drops below 58 FPS |
| Burn book navigation | 60 | Rapid tab switching (16 cast) | Consistent 60 FPS |
| Scene simulation (background) | 60 (main thread) | While AI runs on worker thread | Main thread maintains 60 FPS |
| Multi-scene session (8 scenes) | 60 | Throughout full episode | No degradation over time |
| Long play session (4+ hours) | 60 | End of session vs. start | <2 FPS difference (no leaks) |

### 7.2 Load Time Targets

| Load Type | PC (Mid-range) | PC (High-end) | Steam Deck | Pass Condition |
|-----------|----------------|---------------|------------|----------------|
| Episode start | <2s | <1s | <3s | 95% of loads meet target |
| Save game load | <2s | <1s | <3s | 95% of loads meet target |
| Season transition | <3s | <2s | <4s | Acceptable (infrequent) |

### 7.3 Memory Targets

| Measurement | Target | Tolerance | Pass Condition |
|-------------|--------|-----------|----------------|
| Runtime memory footprint | <100 MB | ±20 MB | No session exceeds 120 MB |
| Memory growth over 4 hours | <10 MB | ±5 MB | No leaks detected |
| Save file size | <2 MB | +50% | Most saves under 2 MB, max 3 MB |

### 7.4 Steam Deck Specific

| Metric | Target | Pass Condition |
|--------|--------|----------------|
| Battery life (full gameplay) | 4-5 hours | >4 hours average |
| Text readability (7-inch screen) | All text legible | No user reports of strain |
| Touch target accuracy | >95% first-tap success | No frequent mis-taps reported |

---

## 8. BUG SEVERITY & PRIORITY DEFINITIONS

### 8.1 Severity Levels

**S1 — CRITICAL (Showstopper)**
- Crashes to desktop
- Data loss (save corruption, progress deleted)
- Game unplayable (softlock, cannot progress)
- Major system completely non-functional (AI doesn't generate scenes, edit bay doesn't assemble episodes)

**S2 — HIGH (Major Impact)**
- Major feature broken but workaround exists
- Significant performance degradation (<30 FPS)
- Major UI element non-functional
- Incorrect calculations affecting core loop (ratings formula broken)
- Progress-blocking bug in non-critical path

**S3 — MEDIUM (Moderate Impact)**
- Minor feature broken
- Visual glitches (clipping, incorrect colors)
- Typos in critical UI text
- Audio issues (missing SFX, wrong music cue)
- Balance issues (too easy/hard but playable)

**S4 — LOW (Minor Impact)**
- Cosmetic issues (alignment, spacing)
- Typos in flavor text
- Minor audio timing issues
- Quality-of-life missing features (not broken, just missing convenience)

### 8.2 Priority Levels

**P1 — IMMEDIATE (Fix Now)**
- All S1 bugs
- S2 bugs blocking milestone delivery
- Bugs affecting beta/launch readiness

**P2 — HIGH (Fix This Sprint)**
- S2 bugs not blocking milestones
- S3 bugs in critical-path features
- Bugs with high player visibility

**P3 — MEDIUM (Fix Before Launch)**
- S3 bugs in secondary features
- S4 bugs in critical features
- Polish and quality-of-life

**P4 — LOW (Nice to Have)**
- S4 bugs
- Known shippable issues
- Post-launch candidates

### 8.3 Bug Triage Protocol

1. **Report received** → Assign severity (S1-S4)
2. **Engineering review** → Confirm severity, assign priority (P1-P4)
3. **Milestone check** → Does this block current milestone quality gate?
4. **Assignment** → P1 bugs assigned immediately. P2-P4 scheduled.
5. **Verification** → QA verifies fix in next build. Regression tests run.
6. **Closure** → Bug closed only after QA sign-off.

---

## 9. TESTING SCHEDULE

### 9.1 Test Cycles by Milestone

| Milestone | QA Start | QA Duration | Test Type | Deliverable |
|-----------|----------|-------------|-----------|-------------|
| **M1: AI Prototype** | Month 2 Week 3 | 2 weeks | Exploratory, AI behavior | Behavior quality report, pass/fail on kill condition |
| **M2: Vertical Slice** | Month 5 Week 2 | 3 weeks | Functional, usability, performance | Full test pass, bug report, playtest survey results |
| **M3: Full Season** | Month 9 | 4 weeks | Integration, stress, save/load | Regression suite, load testing, user feedback |
| **M4: Multi-Season** | Month 13 | 3 weeks | Balance, progression, legacy | Balance report, telemetry review, playtest feedback |
| **M5: Full Content** | Month 17 | 4 weeks | Performance, polish, Steam integration | Performance benchmarks, achievement verification, bug triage |
| **M6: Beta** | Month 19 | 12 weeks | Closed beta, telemetry, balance tuning | Beta report, balance tuning recommendations, critical bug fixes |
| **M7: Launch Prep** | Month 23 | 4 weeks | Regression, smoke, final verification | Launch readiness report, day-one patch prep |

### 9.2 Ongoing Testing (All Milestones)

- **Weekly smoke tests** (core loop functional, no regressions)
- **Bi-weekly playtests** (internal team, rotating focus areas)
- **Monthly performance profiling** (FPS, load times, memory)
- **Continuous integration testing** (automated tests on every commit)

---

## 10. PLATFORM-SPECIFIC TEST MATRICES

### 10.1 PC Test Matrix

| Configuration | Spec | Test Coverage |
|---------------|------|---------------|
| **Min Spec** | i5-4690 / GTX 960 / 8GB RAM / HDD | Can run at 60 FPS 1080p? Load times acceptable? |
| **Recommended** | i7-8700 / RTX 2060 / 16GB RAM / SSD | 60 FPS 1080p confirmed. Load times <2s. |
| **High-End** | i9-12900K / RTX 4080 / 32GB RAM / NVMe SSD | 60 FPS 4K confirmed. Load times <1s. |

**OS Coverage:**
- Windows 10 (primary)
- Windows 11 (secondary)

**Resolution Coverage:**
- 1920x1080 (most common)
- 2560x1440 (common enthusiast)
- 3840x2160 (4K, scaling)
- 3440x1440 (ultrawide, UI layout)

**Input Coverage:**
- Mouse + Keyboard (primary, full testing)
- Gamepad (post-launch, spot-check only)

---

### 10.2 Steam Deck Test Matrix

| Configuration | Notes |
|---------------|-------|
| **Steam Deck (LCD)** | Baseline model, 1280x800, 60Hz |
| **Steam Deck OLED** | Same specs, verify OLED-specific issues (burn-in risk from static UI) |

**Input Coverage:**
- Touchscreen (burn book navigation, scene setup)
- Trackpad (edit bay timeline precision)
- Buttons (quick actions, menu navigation)
- On-screen keyboard (chyron text input)

**Special Tests:**
- Sleep/resume (game pauses correctly, no state loss)
- Battery drain (target 4-5 hours)
- Thermal throttling (long sessions, no performance drop)

---

## 11. SPECIALIZED TEST AREAS

### 11.1 Procedural Generation Quality

**Goal:** Ensure procedurally generated cast members feel distinct and interesting.

| Test Case | Method | Pass Condition |
|-----------|--------|----------------|
| **Cast variety** | Generate 100 cast members, analyze trait distributions | No single archetype exceeds 30%. Traits well-distributed. |
| **Backstory uniqueness** | Generate 50 cast, check backstories | <10% exact duplicates. Combinations feel fresh. |
| **Quality filter effectiveness** | Run quality filter on 100 generated cast | >80% pass filter. Filtered cast are interesting (playtest confirms). |
| **Cast memorability** | Playtest: one season, survey after | 80% of testers can name 3+ cast and describe their arcs. |

---

### 11.2 AI Behavior Validation

**Goal:** Confirm AI produces emergent, believable, non-repetitive behavior.

| Test Case | Method | Pass Condition |
|-----------|--------|----------------|
| **Behavioral variety** | Same scene, 20 runs, analyze outcomes | <30% similarity across runs. Outcomes feel distinct. |
| **Personality consistency** | Track Agreeable cast (Jade) across 10 scenes | Always avoids conflict. Never escalates unprovoked. |
| **Relationship influence** | Allies vs. rivals in same scenario, 10 runs each | Allies support. Rivals provoke. Clear behavioral difference. |
| **Stress affects behavior** | Compare PI 80 vs. PI 30, same setup, 10 runs each | High PI: rational, measured. Low PI: erratic, volatile. |
| **No nonsensical actions** | 100 scenes, log all AI choices | Zero instances of behavior contradicting personality+context. |

---

### 11.3 Economy & Balance Validation

**Goal:** Confirm economy is balanced, not trivially exploitable, and fair.

| Test Case | Method | Pass Condition |
|-----------|--------|----------------|
| **Budget sustainability** | Play Season 1-4, track income/expenses | Player can sustain budget without bankruptcy if playing reasonably well. |
| **Difficulty curve** | Playtest each difficulty mode | Basic Cable: forgiving. Network: fair challenge. Premium: hard but fair. Hell: brutal but achievable. |
| **Exploit resistance** | Attempt known exploits (save-scum, repetitive strategies) | Diminishing returns kick in. No infinite-money loops. |
| **Progression pacing** | Track unlocks over 8 seasons | Unlocks feel meaningful. Not too fast (trivial) or too slow (grind). |

---

### 11.4 Narrative Coherence

**Goal:** Emergent stories feel coherent, not random.

| Test Case | Method | Pass Condition |
|-----------|--------|----------------|
| **Season arc** | Playtest full season, evaluate narrative | Season has identifiable beginning, middle, climax. Not just "random episodes." |
| **Cast arcs** | Track 3 cast members across season | Each has arc (relationship changes, PI journey, character development). |
| **Legacy continuity** | Check Season 2 references to Season 1 | Callbacks feel organic. Former cast outcomes surface believably. |
| **Emergent stories** | Playtest, ask "What happened this season?" | Players can summarize coherent stories ("Jade's breakdown," "Marcus/Derek rivalry"). |

---

## 12. OPEN QUESTIONS FOR PLAYTESTING

These cannot be answered by specification. They require player feedback.

1. **AI Behavior Feel:** Do AI cast members feel like people or automata? Can players predict behavior based on burn book intel, or does it feel random?

2. **Edit Bay Engagement:** Does the edit bay feel like wielding narrative power, or like data entry? Where is the line between "deep strategic editing" and "tedious busywork"?

3. **Ratings Clarity:** Can players explain why their ratings went up or down? Is the attribution system clear enough?

4. **Moral Weight Timing:** When do players first feel uncomfortable with their choices? Episode 3? Episode 7? Never? If never, why not?

5. **Cast Attachment:** Do players care about procedurally generated cast members? Can they name them? Do they feel bad when cast members break?

6. **Session Length Tolerance:** Does a 30-minute episode feel right, or too long/too short? Do players want to start the next episode immediately, or do they stop?

7. **Difficulty Accessibility:** Is "Network Television" mode the right baseline difficulty? Is "Reality TV Hell" mode fun-hard or frustrating-hard?

8. **Information Overload:** At what point do players feel overwhelmed by stats, intel, and systems? Season 1? Season 3? Never?

9. **Progression Satisfaction:** Do reputation unlocks feel meaningful? Do players feel their showrunner career has weight and history?

10. **The "I Feel Bad" Moment:** Where does it happen? What triggers it? Is it consistent across players, or wildly variable?

---

## 13. FINAL NOTES

This is not a document you read once. This is a document you live in. Every milestone, every build, every bug — you come back here and you check: did we test this? Did we pass the quality gate? Are we still on track?

The core QA challenge for BURNBOOK is this: **We are testing emergent systems, not scripted content.** That means traditional test case execution ("click button, verify result") is necessary but not sufficient. We need exploratory testing. We need playtesting. We need to break the systems in ways the designers didn't anticipate, because the players will.

What could make this unfun?

- **AI that feels robotic.** Test relentlessly. If the AI doesn't sing, nothing else matters.
- **Edit bay that feels like work.** Kill condition is real. If it's tedious, we redesign or simplify.
- **Ratings that feel opaque.** Players must understand cause and effect. If they can't, the feedback loop is broken.
- **Consequences that feel random.** Fallout must feel earned. Causation must be visible.
- **Information overload.** UI must be scannable, hierarchical, and progressive.

What are the kill conditions?

- **M1:** AI satisfaction <7/10 → Pivot or abort.
- **M2:** Edit bay tedium >40% → Radical simplification.
- **M3:** Cast members unmemorable → Rework procedural generation.
- **M6:** Critical bugs >5 → Delay launch.
- **M7:** Launch crash rate >1% → Emergency patch.

What does success look like?

- Players tell stories about their cast members.
- Players feel the weight of their editorial choices.
- Players understand the systems well enough to strategize.
- Players feel complicit — not because the game told them to, but because the mechanics made them.
- The loop holds at hour 100.

This game is a high-wire act. Five systems generating emergent behavior to create an experience that is mechanically compelling and thematically uncomfortable. If any system fails, the game fails. QA's job is to find those failures before the player does.

Define "works." For BURNBOOK, "works" means:
- AI generates believable, emergent drama
- Edit bay feels like authorship
- Ratings are legible
- Consequences feel earned
- The loop holds
- 60 FPS, <3s loads, zero data loss

Anything less is not done.

Let's break this properly.

— CRASH

---

**QA Plan Complete.**
**Document Version:** 1.0
**Approvals Required:** REED (Design), BYTE (Tech), CLOCK (Production)
**Next Steps:** Review, approve, begin Milestone 1 test execution.

**Absolute file path for reference:** `/Users/burcukose/git/project-draft/games/06-burnbook/qa-plan.md`
