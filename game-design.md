# BURNBOOK -- Game Design Document

**Version:** 1.0
**Author:** REED (Game Design)
**Date:** 2026-02-07
**Status:** Pre-Production

---

## 0. DESIGN INTENT

Let me be direct. I've seen a hundred management sims die because they confused "theme" with "mechanic." They dress up spreadsheets in interesting costumes and wonder why players bounce after four hours. BURNBOOK does not get to be one of those games. The pitch is extraordinary -- reality TV showrunner, AI-driven cast, moral weight baked into the loop -- but none of that matters if the 30-second experience isn't compelling. If placing two cast members at a dinner table doesn't feel like placing a bet, if reading the burn book doesn't feel like loading a gun, if cutting footage doesn't feel like wielding power -- no amount of thematic ambition saves us.

So here's what this document does: it takes every idea in the pitch and forces it through the machine. What's the loop? Where's the depth? What's the player's verb? Is this a system or a one-off? Every mechanic earns its place or gets cut.

Let's build this.

---

## 1. PLAYER FANTASY STATEMENT

**"I am the most dangerous person in television -- the one who knows everyone's secrets, controls every situation, and decides what's real. I don't perform. I don't watch. I architect. And the line between making great television and destroying real people isn't a line at all -- it's the job."**

This fantasy has three pillars:

1. **Omniscience** -- The burn book gives you knowledge no one else has. You know Jade's childhood trauma. You know Marcus is hiding a phone call. You know Tanya's loyalty will be tested tonight. Information is power, and you have all of it.

2. **Authorship** -- The edit bay lets you reshape reality. The same dinner scene can become a love story or a betrayal arc depending on how you cut it. You don't just observe events. You author their meaning.

3. **Complicity** -- The ratings engine rewards exploitation. The fallout system tracks damage. You feel the weight because the game never tells you to stop -- it just shows you the ledger. The fantasy isn't "be a villain." The fantasy is "discover what you're willing to do when the incentives are aligned."

Every mechanic in this document serves at least one of these pillars. If it doesn't, it doesn't ship.

---

## 2. CORE LOOP

### 2.1 The 30-Second Loop (The Placement Bet)

The atomic unit of BURNBOOK is the **placement decision**. The player reads a cast member's emotional state (visible as a multi-axis mood indicator), cross-references it against burn book intelligence, and makes a positioning choice: who goes where, next to whom, with what information.

This is a bet. You're combining volatile elements and predicting the reaction. Sometimes you get the dramatic confrontation you wanted. Sometimes you get an unexpected alliance. Sometimes someone walks off set. The gap between your prediction and the outcome is where the game lives.

**Input:** Burn book intel + cast emotional states + scene parameters
**Action:** Drag-and-drop cast placement, catalyst selection, information control
**Output:** Immediate AI behavioral response (visible as scene preview indicators -- tension meters, predicted drama value, risk assessment)
**Feel:** Placing chess pieces on a board that plays back

### 2.2 The 5-Minute Loop (The Scene Cycle)

A complete scene runs approximately 3-5 minutes of player time:

1. **Setup (60s):** Choose location from available set pieces. Select 2-6 cast members. Set environmental parameters (alcohol availability, lighting mood, isolation level). Optionally plant catalysts (a letter, a phone, a surprise guest, a rumor). Review burn book predictions for likely outcomes.

2. **Shoot (90-120s):** The Situation Engine resolves the scene. Cast members interact according to their AI behavioral models. The player watches on multi-camera monitors -- four simultaneous feeds they can switch between. Emotional spike indicators flag key moments in real-time. The player can trigger mid-scene interventions (send in a producer, change the music, introduce a twist) but each intervention costs credibility with the cast and increases the risk of breaking the fourth wall.

3. **Harvest (60s):** Scene ends. Raw footage is broken into discrete moments -- each tagged with drama value (0-100), emotional authenticity (0-100), narrative utility (how well it connects to existing storylines), and legal risk (0-100). The player selects which moments to flag for the edit bay. Key confessionals triggered by emotional spikes are auto-captured.

**Loop feel:** Set the table, watch the meal, collect the leftovers.

### 2.3 The 30-Minute Loop (The Episode Cycle)

An episode is assembled from 4-8 scenes and takes roughly 25-35 minutes of player time:

1. **Scene Planning (5 min):** Review upcoming schedule. Plan 4-8 scenes across the episode's timeline. Allocate cast across scenes. Identify target storylines for the episode (you can track up to 3 primary arcs and 2 secondary arcs per episode).

2. **Shooting (15-20 min):** Run scenes sequentially. Each scene feeds raw footage into the edit bay stockpile. Between scenes, check burn book updates -- cast relationships shift, stress levels change, new intel surfaces.

3. **Editing (8-12 min):** Enter the edit bay. Assemble a broadcast episode from your raw footage stockpile. The episode has a fixed runtime measured in "segments" (6-8 segments per episode). Each segment holds one primary moment plus optional confessional overlays and music cues. Arrange segments into narrative order. The edit bay scores your assembly in real-time: narrative coherence (does this tell a story?), drama density (is it exciting?), audience expectation alignment (does it give the audience what they want?), and tonal consistency.

4. **Broadcast (2-3 min):** Submit the episode. Watch a compressed "as-aired" version with audience reaction overlays. Receive the ratings report: Nielsen number, audience segment breakdown, social media sentiment feed, advertiser confidence index, network satisfaction score. Check for fallout: cast stress events, legal notices, tabloid stories, public opinion shifts.

### 2.4 The Meta Loop (The Season Arc)

A season spans 8-12 episodes and constitutes a single complete arc:

1. **Casting:** Select 8-16 cast members from a pool of procedurally generated candidates. Each candidate has a visible "casting tape" (surface-level personality) and a hidden "burn book file" (deeper psychology, only partially revealed at casting). Better showrunner reputation = larger, higher-quality candidate pool.

2. **Format Selection:** Choose (or eventually design) the show format. Each format defines the structural constraints: elimination schedule, challenge types, living arrangements, and audience voting mechanics. The format is the chassis; the cast is the engine.

3. **Season Management:** Run episodes. Manage elimination schedules. Navigate network demands (weekly notes requesting specific storyline directions). Handle mid-season crises (cast walkoffs, legal threats, tabloid scandals). Introduce twists (cast swaps, format changes, returning eliminated players).

4. **Finale and Aftermath:** Build toward a season climax. The finale episode has 2x the normal segment count and generates 3x the normal ratings impact. After broadcast, receive the season report card: total viewership, critical reception, cultural impact score, cast outcome summaries (where did each person end up?), and renewal decision.

5. **Between Seasons:** Reputation update. Budget allocation for next season. Review legacy consequences from previous seasons. New casting call.

### 2.5 Core Loop Diagram

```
THE 30-SECOND LOOP (The Placement Bet)
=========================================

  [READ BURN BOOK] --> [ASSESS EMOTIONAL STATES] --> [PLACE CAST + CATALYSTS]
        ^                                                      |
        |                                                      v
        +------------- [OBSERVE AI RESPONSE] <---------[SCENE RESOLVES]


THE 5-MINUTE LOOP (The Scene Cycle)
=========================================

  [SETUP SCENE]                    [SHOOT SCENE]              [HARVEST FOOTAGE]
  +--------------+    +-------->  +-----------------+    +--> +------------------+
  | Choose loc.  |    |           | Multi-cam view  |    |    | Tag moments      |
  | Select cast  |--->|           | AI resolves     |--->|    | Flag key footage |
  | Plant catalysts   |           | Spike indicators|    |    | Capture confess. |
  | Set params   |    |           | Mid-scene tools |    |    | Update burn book |
  +--------------+    |           +-----------------+    |    +------------------+
                      |                                  |            |
                      +---[INTERVENE?]-------------------+            |
                                                                      v
                                                              [TO EDIT BAY]


THE 30-MINUTE LOOP (The Episode Cycle)
=========================================

  [PLAN SCENES] --> [SHOOT 4-8 SCENES] --> [EDIT EPISODE] --> [BROADCAST]
       ^                                                          |
       |                                                          v
       |                                                   [RATINGS REPORT]
       |                                                          |
       |                                                          v
       +-------------- [UPDATE BURN BOOK] <------------- [PROCESS FALLOUT]


THE META LOOP (The Season Arc)
=========================================

  [CAST SHOW] --> [SELECT FORMAT] --> [RUN EPISODES x8-12] --> [FINALE]
       ^                                                          |
       |                                                          v
       |                                                 [SEASON REPORT CARD]
       |                                                          |
       |                                                          v
       +------------ [REPUTATION UPDATE] <------------- [RENEWAL DECISION]
                           |
                           v
                   [BETWEEN-SEASON MANAGEMENT]
                           |
                           v
                     [NEW CASTING CALL]
```

---

## 3. CORE MECHANICS

### 3.1 The Burn Book (Intelligence System)

**Player Verb:** INVESTIGATE

**System Description:**
The burn book is a living dossier on every cast member. Each entry contains:

| Data Layer | Source | Accuracy at Week 1 | Decay Rate |
|---|---|---|---|
| Background (childhood, family, education) | Pre-show research, casting tape | 90-95% | None (static facts) |
| Personality Profile (Big Five + custom axes) | Psych evaluation, observed behavior | 70-80% | -5% per episode without revalidation |
| Emotional State (current mood, stress, energy) | Producer check-ins, confessionals, observation | 85-90% | Real-time decay; stale within 2 scenes |
| Relationship Map (alliances, rivalries, attractions) | Observation, confessionals, informants | 60-75% | -10% per episode (alliances shift fast) |
| Triggers (insecurities, buttons, breaking points) | Deep confessionals, background research | 50-65% | -3% per episode (people adapt to pressure) |
| Secrets (hidden information, lies, concealed history) | Investigation, informants, surveillance | Variable | Secrets can be revealed, altering the entire profile |

**Information Accuracy Model:**
Every burn book data point has a hidden confidence value (0-100). The displayed information is filtered through the confidence value:

- **90-100:** Information displayed as solid text. Reliable.
- **70-89:** Information displayed normally but with a subtle paper-worn texture. Mostly reliable.
- **40-69:** Information displayed with handwritten question marks. Potentially outdated.
- **1-39:** Information displayed as crossed-out text with new guesses penciled in. Unreliable.
- **0:** Entry removed. You're flying blind.

Confidence decays passively over time and actively when cast members undergo significant emotional events. It regenerates through: direct producer-cast conversations (costs time, may alert the cast member to your interest), confessional analysis (passive, slower), observation during scenes (moderate, requires attention), and informant reports from other cast members (fast but potentially biased or deliberately false).

**Feedback:** The burn book physically changes. Pages get dog-eared, notes get crossed out and rewritten, Post-it notes accumulate. A well-maintained burn book looks like a living document. A neglected one looks like a relic. When a prediction based on burn book intel proves accurate, the relevant entry gets a green check mark. When it proves wrong, a red X appears with the actual outcome noted. Over a season, the player can see their batting average.

**Depth:** Early game, the burn book feels like a cheat sheet -- you know more than the cast and can exploit it. Mid-game, you realize the profiles are aging and your assumptions are increasingly wrong. A cast member you profiled as "conflict-averse" in week one has been hardened by six weeks of manufactured drama and is now the most confrontational person on set. Late game, the burn book becomes a strategic tool requiring active maintenance -- a garden, not a warehouse. Expert players learn to read the delta between the profile and reality as signal: if someone is diverging from their profile, that divergence IS the story.

---

### 3.2 The Situation Engine (Drama Manufacturing)

**Player Verb:** ARRANGE

**System Description:**
The Situation Engine is a combinatorial drama generator. The player sets conditions; the AI resolves outcomes. Here are the player-controlled variables:

**Location Properties:**

| Location | Intimacy Level | Escape Routes | Alcohol Access | Camera Coverage | Max Cast |
|---|---|---|---|---|---|
| Dinner Table | High | Low | Yes | Full | 8 |
| Hot Tub | Very High | Low | Yes | Full | 4 |
| Shared Bedroom | High | Medium | No | Partial | 2-4 |
| Competition Arena | Low | None | No | Full | All |
| Confessional Booth | Maximum | None | No | Single-cam | 1 |
| Garden/Patio | Medium | High | Optional | Partial | 6 |
| Kitchen | Medium | High | Optional | Partial | 4 |
| Isolation Room | Maximum | None | No | Full | 1-2 |

**Catalyst Types:**

| Catalyst | Drama Potential | Risk Level | Cost (Production Budget) |
|---|---|---|---|
| Planted Letter (from home) | +15-30 drama | Low | $200 |
| Overheard Phone Call | +20-40 drama | Medium | $500 |
| Surprise Guest (ex, family) | +30-60 drama | High | $2,000 |
| Alcohol (unlimited) | +10-25 drama | Medium | $300 |
| Elimination Threat (fake) | +25-45 drama | Very High | $0 (but trust cost) |
| Secret Reveal (to group) | +35-70 drama | Very High | $0 (burns the intel) |
| Romantic Setup (date card) | +15-35 drama | Low | $1,000 |
| Challenge/Competition | +10-30 drama | Low | $1,500-5,000 |

**Scene Resolution Formula:**

The AI processes each scene through this priority stack:

1. **Self-preservation:** Cast members avoid situations that threaten their physical safety or contractual standing (unless stress > 85, at which point rationality degrades).
2. **Core desire pursuit:** Each cast member has a primary desire (love, fame, validation, competition, escape) that drives proactive behavior.
3. **Relationship response:** Interactions are filtered through the relationship map -- allies support, rivals provoke, attractions complicate.
4. **Stress response:** High stress (>70) triggers fight/flight/freeze behaviors based on personality type. Very high stress (>85) triggers irrational responses.
5. **Environmental response:** Cast members react to catalysts, location properties, and information asymmetries.

**Drama Value Calculation (per moment):**

```
Drama Value = (Emotional Intensity x 0.35) +
              (Conflict Level x 0.25) +
              (Surprise Factor x 0.20) +
              (Narrative Relevance x 0.20)

Each component scored 0-100. Total Drama Value = 0-100.
```

**Feedback:** During a scene, the player sees real-time indicators on their multi-camera view:
- **Tension Meter** (per cast member): A needle gauge that climbs during confrontation and drops during resolution. Visible on the "producer's monitor" overlay.
- **Drama Spike Alerts:** Pop-up flags when a moment exceeds 65 drama value. Accompanied by a camera flash icon and a brief text summary ("Jade confronts Marcus about the phone call -- DV 78").
- **Catalyst Effect Indicator:** When a planted catalyst triggers, the player sees a subtle "it's working" confirmation or a "no effect" dismissal.

**Depth:** A beginner throws the loudest people together and drops every catalyst available. This produces high-drama scenes but burns through cast stress at an unsustainable rate. An expert understands the Situation Engine's deeper patterns:

- **The Slow Burn Principle:** A scene with drama value 45-55 that connects to a multi-episode arc is more valuable than a scene with drama value 90 that resolves everything. Unresolved tension is the most valuable resource in the game.
- **Catalyst Timing:** A surprise guest has 3x the impact if deployed when the target cast member's stress is between 50-65 (emotionally vulnerable but still coherent enough to produce watchable television, not incoherent meltdown).
- **Information Asymmetry:** The most powerful tool isn't a catalyst -- it's controlling who knows what. If Marcus knows about Jade's insecurity but Jade doesn't know Marcus knows, the resulting interaction generates dramatic irony the audience can feel.

---

### 3.3 The Edit Bay (Narrative Control)

**Player Verb:** RESHAPE

**System Description:**
The edit bay is a simplified timeline editor. An episode consists of 6-8 **segments**. Each segment has:

- **One Primary Moment** (dragged from the footage stockpile)
- **One Optional Confessional Overlay** (a talking-head clip that recontextualizes the moment)
- **One Music Cue** (selected from a library of tonal options)
- **One Optional Chyron** (player-written text overlay)

The footage stockpile accumulates across all scenes shot for the episode. Each moment in the stockpile is tagged with metadata:

| Tag | Description | Range |
|---|---|---|
| Drama Value | How exciting is this moment? | 0-100 |
| Emotional Authenticity | How genuine does it feel? | 0-100 |
| Narrative Utility | How well does it connect to ongoing arcs? | 0-100 |
| Legal Risk | Could this trigger a lawsuit? | 0-100 |
| Cast Damage | How much does airing this hurt the cast member? | 0-100 |

**Music Cue Library:**

| Cue Category | Effect on Audience Perception | Example |
|---|---|---|
| Romantic Swell | +20 romance perception, -10 conflict perception | Strings, piano, soft |
| Sinister Sting | +25 suspicion perception, +15 drama perception | Low drone, sharp hits |
| Comedic Bounce | +15 entertainment, -20 emotional weight | Pizzicato, upbeat |
| Tension Build | +20 anticipation, +10 drama retention to next segment | Rising strings, heartbeat |
| Melancholy Piano | +25 empathy for featured cast, +10 authenticity | Solo piano, minor key |
| Triumphant Brass | +15 satisfaction, +10 cast likability | Horns, major key |
| Silence (no cue) | +30 authenticity, -10 entertainment | Dead air |

**Juxtaposition System:**
When two adjacent segments feature the same cast member in contrasting emotional states or contradictory statements, the edit bay calculates a **Juxtaposition Bonus:**

```
Juxtaposition Bonus = |Emotional State A - Emotional State B| x 0.5

Example: Segment 3 shows Jade saying "I'm totally fine" (calm, confidence 80).
         Segment 4 shows Jade crying alone (distressed, confidence 15).
         Juxtaposition Bonus = |80 - 15| x 0.5 = 32.5 bonus drama value.
```

This bonus applies to the episode's total drama score but also increases the featured cast member's "editorial betrayal" stat -- a hidden value that tracks how much the edit has misrepresented them. High editorial betrayal eventually triggers cast awareness events: the cast member sees the broadcast, realizes how they were portrayed, and reacts. This reaction can range from quiet resentment (-15 cooperation) to public denouncement (-40 cooperation, +tabloid story, +legal risk).

**Feedback:** The edit bay provides a real-time **Episode Quality Score** visible as a newspaper-style "review" that updates as you arrange segments:

- **"Gripping television"** (Total Drama > 400, Coherence > 70)
- **"A solid episode"** (Total Drama 250-400, Coherence > 50)
- **"Forgettable filler"** (Total Drama 150-250)
- **"Incoherent mess"** (Coherence < 30, regardless of drama)
- **"Exploitative garbage"** (Legal Risk average > 70, Cast Damage average > 80)

The last two ratings are warnings. "Incoherent mess" means your segments don't tell a connected story. "Exploitative garbage" means the network might pull the episode and your reputation takes a hit. Both are recoverable but costly.

**Depth:** The edit bay is where BURNBOOK transcends the management sim genre. A beginner maximizes drama per segment. An expert understands editorial rhythm:

- **The Cold Open:** The first segment sets the episode's tonal promise. A high-drama cold open creates expectations the rest of the episode must meet. A quieter cold open allows escalation. Mismatching the cold open and the episode body produces tonal whiplash, which tanks coherence.
- **The Cliffhanger:** The final segment determines audience retention for next episode. Unresolved tension in the last segment generates a **Retention Bonus** of 10-25% on next episode's initial viewership.
- **Selective Restraint:** Sometimes the most powerful edit is withholding a moment. If you have footage of a cast member's genuine breakdown and you DON'T air it, that footage stays in stockpile and gains a **"Withheld Moment" tag**. If you air it later, it carries 1.5x drama value due to delayed gratification. If you never air it, the cast member's trust in you increases (+10 cooperation per withheld high-damage moment).
- **The Villain Edit:** Consistently editing a single cast member with sinister stings, unflattering juxtapositions, and confrontation-heavy segments creates a **Villain Arc**. The audience comes to expect this cast member as the antagonist. A villain arc boosts weekly ratings by 8-15% but accelerates the cast member's stress gain by 2x and eventually triggers either a walkoff or a "redemption demand" from the network ("America's tired of hating them -- make them sympathetic or we replace them").

---

### 3.4 The Ratings Engine (Feedback System)

**Player Verb:** EVALUATE

**System Description:**
After each episode broadcast, the Ratings Engine generates a comprehensive report. Here's the model:

**Nielsen Rating Calculation:**

```
Base Rating = (Season Baseline x Format Multiplier)

Episode Rating = Base Rating
               + (Drama Score x 0.004)
               + (Coherence Score x 0.003)
               + (Cliffhanger Retention from Previous Episode x 0.15)
               + (Cultural Moment Bonus, if any)
               - (Audience Fatigue Penalty)
               - (Scandal Penalty, if any)

Season Baseline starts at 1.2 (new show) and adjusts weekly based on trajectory.
Format Multiplier: Dating = 1.2, Competition = 1.0, Social Experiment = 0.9, Hybrid = 1.1
```

**Audience Segments:**
The audience is composed of five segments, each with different appetites:

| Segment | % of Audience | Wants | Hates | Loyalty |
|---|---|---|---|---|
| Drama Addicts | 30% | Conflict, confrontation, screaming matches | Boring episodes, repetition | Low (chases the highest drama) |
| Romantics | 25% | Love stories, emotional vulnerability, connection | Cruelty, exploitation, cynicism | High (stays for couples) |
| Justice Seekers | 20% | Fairness, karma, villains getting punished | Unpunished manipulation, "bad people winning" | Medium |
| Strategists | 15% | Gameplay, alliances, Machiavellian moves | Randomness, producer interference, "unfair" twists | High (respects the game) |
| Chaos Agents | 10% | Meltdowns, unpredictability, things going wrong | Predictability, "boring nice people" | Very Low (most fickle) |

Each episode's content is scored against each segment's preferences. Segment satisfaction determines their retention probability for the next episode. Losing a segment below 30% satisfaction for three consecutive episodes triggers a **"Segment Exodus"** -- that audience group drops by 40% and is very expensive to win back.

**Advertiser Confidence Index (ACI):**

```
ACI = (Nielsen Rating x 40) + (Audience Demographics Score x 30) + (Brand Safety Score x 30)

Brand Safety Score = 100 - (Average Legal Risk of Aired Moments)
```

ACI determines ad revenue, which feeds directly into the production budget for future episodes. High ratings with high legal risk is a trap: you get viewers but lose advertisers.

**Network Satisfaction Score (NSS):**

```
NSS = (Nielsen Rating x 0.35) + (ACI x 0.25) + (Critical Reception x 0.15)
    + (Social Media Buzz x 0.15) + (Controversy Avoidance x 0.10)
```

NSS below 40 for three consecutive episodes triggers a network intervention: mandatory format changes, cast additions, or showrunner "guidance" (a euphemism for creative restriction). NSS below 25 triggers cancellation review. NSS above 75 grants creative freedom bonuses (larger budget, more casting options, format experimentation rights).

**Feedback:** The ratings report is presented as a physical document landing on your desk -- a Nielsen printout with coffee rings, hand-annotated by a network executive. Social media is rendered as a scrolling feed of viewer reactions (text posts, not images) that the player can skim. Advertiser confidence shows as a stack of deal memos getting thicker or thinner. Network satisfaction is communicated through a producer's note -- a typed memo with the network exec's handwritten comments in the margins.

**Depth:** The Ratings Engine is the system that transforms BURNBOOK from a sandbox into a strategy game. You're not just making interesting television -- you're optimizing across five competing audience segments, an advertiser confidence index that punishes risk, a network satisfaction score that punishes both blandness and controversy, and a cultural impact metric that rewards swinging for the fences. These goals conflict. Drama Addicts want meltdowns; Advertisers want brand safety. Romantics want tenderness; Chaos Agents want destruction. Justice Seekers want karma; your best villain is too profitable to punish.

The expert player reads the ratings report like a general reads a battlefield map. They notice that Romantics are at 35% satisfaction and trending toward exodus -- time to build a love story. They see that Drama Addicts are at 90% and can tolerate one quieter episode without leaving. They recognize that the network wants more competition episodes but advertisers are nervous about the legal risk from last week's confrontation. They triangulate. They compromise. They make the best television possible within constraints that are always shifting.

---

### 3.5 The Fallout System (Consequences)

**Player Verb:** MANAGE (or SUFFER)

**System Description:**
Every cast member tracks a hidden **Psychological Integrity (PI)** stat that represents their overall mental health within the production environment.

**Psychological Integrity Model:**

```
PI starts at 100 for every cast member.

PI Loss Per Episode:
  Base Stress from Being on Show:        -2 to -5 (personality-dependent)
  Stress from Manufactured Drama:        -(Drama Value of scenes involving them x 0.08)
  Stress from Unfavorable Edit:          -(Cast Damage of aired moments x 0.12)
  Stress from Isolation/Alliance Loss:   -3 to -8 per lost ally
  Stress from Trigger Activation:        -10 to -25 per triggered insecurity

PI Recovery Per Episode:
  Positive Social Interaction:           +2 to +6
  Confessional Venting (unaired):        +3 to +5
  Producer Support Conversation:         +4 to +8 (costs player time)
  Day Off / Reduced Scene Load:          +5 to +10 (costs content)
  Contact with Outside Support:          +3 to +7 (risks information leak)
```

**PI Threshold Events:**

| PI Range | Cast Member State | Behavioral Effect | Production Risk |
|---|---|---|---|
| 80-100 | Stable | Normal behavior, cooperative | None |
| 60-79 | Stressed | Increased emotional volatility, better TV but less predictable | Low -- occasional outbursts |
| 40-59 | Fragile | Erratic behavior, paranoia, withdrawal OR aggression | Medium -- may refuse scenes, confessional quality degrades |
| 20-39 | Breaking | Visible psychological distress, irrational decisions, substance issues | High -- legal review triggered, network concern, tabloid risk |
| 1-19 | Broken | Non-functional. Cast member either walks off or has a breakdown that stops production | Critical -- lawsuit probable, public backlash, season jeopardized |
| 0 | Destroyed | Cast member removed from show. Post-show trajectory is severely negative. | Catastrophic -- scandal, investigation, reputation damage |

**The 60% Sweet Spot:**
Here's the key insight that expert players discover: cast members between 55-70 PI produce the best television. They're stressed enough to be emotionally volatile (which generates authentic drama) but stable enough to remain coherent and contractually compliant. The game's central tension isn't "how much drama can I create?" -- it's "how close to the edge can I keep everyone without pushing them over?"

This is the mechanical expression of the game's moral thesis. The optimal strategy is sustained, calibrated exploitation. Not cruelty for its own sake -- that's wasteful. Careful, professional extraction of human emotion for commercial purposes. The player who masters this system has also internalized its logic, and that realization IS the thematic payload.

**Post-Show Trajectories:**
When a cast member leaves (elimination or walkoff), their PI at departure determines their post-show outcome, which is selected from a probability table:

| Departure PI | Positive Outcome (career boost, healthy life) | Neutral (returns to normal life) | Negative (struggles, tabloid fodder) | Severe (lasting damage) |
|---|---|---|---|---|
| 80-100 | 60% | 30% | 8% | 2% |
| 60-79 | 35% | 35% | 22% | 8% |
| 40-59 | 15% | 25% | 40% | 20% |
| 20-39 | 5% | 15% | 40% | 40% |
| 1-19 | 2% | 5% | 33% | 60% |

Post-show outcomes are reported via tabloid headlines, talk show appearances, and social media posts that surface between episodes and between seasons. They're not just flavor text -- negative outcomes generate Reputation Damage that affects the player's ability to attract quality cast in future seasons.

**Reputation Damage Formula:**

```
Rep Damage = Sum of (Negative Outcome Severity x Publicity Level) for all former cast

Publicity Level = f(how famous the cast member became on your show)
```

This creates a devastating long-tail consequence: the cast members you made most famous (highest ratings, most screen time) also carry the highest reputation risk if they flame out post-show. Your biggest successes are your biggest liabilities.

**Feedback:** Fallout events arrive as interruptions to the normal workflow. A legal notice slides across your desk mid-edit. A tabloid headline pops up on your office TV between scenes. A network executive calls mid-casting. These interruptions are deliberately intrusive -- they force the player to confront consequences they'd rather ignore. The burn book automatically updates with fallout data, and affected cast members' pages accumulate red annotations.

**Depth:** The Fallout System is the governor on the engine. Without it, BURNBOOK is an optimization game about maximizing drama. With it, BURNBOOK is a resource management game about sustainable exploitation -- which is to say, it's a game about the actual economics of reality television. The long-term player learns that the most profitable career isn't the one with the highest-rated single season -- it's the one with the longest run. And the longest run requires keeping your cast functional, your lawyers calm, your network satisfied, and your reputation intact enough to attract new talent. This is the system that makes hour 20 play differently from hour 1.

---

## 4. SYSTEMS INTERACTIONS

### 4.1 Feedback Loops

**Positive Feedback Loop (Snowball): The Fame Spiral**

```
High Drama Scenes --> High Drama Value Footage --> High-Impact Edit
       --> High Ratings --> Network Gives More Budget
       --> Better Catalysts/Locations --> Higher Drama Scenes
```

Left unchecked, this loop accelerates the show toward increasingly extreme content. It's the mechanical representation of "jumping the shark."

**Negative Feedback Loop (Rubber Band): The Burnout Brake**

```
High Drama Scenes --> Cast PI Decreases --> Cast Becomes Erratic/Non-Cooperative
       --> Scenes Become Unpredictable/Low Quality --> Ratings Dip
       --> Player Must Ease Pressure or Replace Cast --> Drama Resets
```

This loop prevents infinite escalation. You can't just crank the drama dial to maximum and leave it there. Cast members are a depletable resource. The tension between these two loops IS the game.

**Positive Feedback Loop (Meta): The Reputation Snowball**

```
Good Seasons --> High Showrunner Reputation --> Better Casting Pool
       --> More Interesting Cast Dynamics --> Better Seasons
```

This is the long-term progression engine. It rewards sustained performance over spike-and-crash strategies.

**Negative Feedback Loop (Meta): The Scandal Anchor**

```
Exploitative Seasons --> Post-Show Negative Outcomes --> Reputation Damage
       --> Worse Casting Pool --> Less Interesting Dynamics --> Worse Seasons
```

This is the long-term consequence engine. Reputational debt from early-career exploitation catches up.

### 4.2 Cross-System Interactions

| System A | System B | Interaction | Strategic Implication |
|---|---|---|---|
| Burn Book | Situation Engine | Intel quality determines prediction accuracy for scene setups | Maintaining burn book accuracy reduces wasted scenes |
| Situation Engine | Edit Bay | Scene quality determines footage stockpile quality | Bad scenes produce bad footage no matter how good your edit |
| Edit Bay | Ratings Engine | Edit quality determines broadcast quality determines ratings | The edit is where player skill has the most direct impact on outcomes |
| Ratings Engine | Burn Book | Ratings success gives budget for better intel-gathering tools | Success funds deeper investigation |
| Fallout System | Burn Book | Fallout events reveal new information about cast members | Crises generate intel (but at a cost) |
| Fallout System | Situation Engine | Low-PI cast members behave unpredictably in scenes | Damaged cast produce chaotic footage -- high ceiling, low floor |
| Fallout System | Ratings Engine | Scandals can spike ratings short-term but damage long-term metrics | The temptation to exploit crises is real and mechanically supported |
| Ratings Engine | Fallout System | High ratings increase public scrutiny of cast treatment | Success invites investigation |

### 4.3 Emergent Possibilities

The interaction of these five systems creates gameplay scenarios that no single system could produce:

- **The Double Agent:** A Strategist-archetype cast member with high self-awareness figures out they're being manipulated (burn book confidence drops, their behavior stops matching predictions). They start "performing" for the cameras -- giving the show what they think it wants. The player can either fight this (try to crack their facade) or embrace it (incorporate their performance into the edit as a meta-narrative). If the audience catches on, it becomes the season's defining storyline.

- **The Mercy Dilemma:** A Sweetheart cast member is at PI 35 but is the linchpin of your highest-rated love story. If you give them a break (reduced scenes, softer edit), the love story stalls and Romantics start tuning out. If you keep pushing, they break and the audience blames you. The optimal play is a "rehabilitation arc" -- reduce their drama load while editing existing footage to suggest growth and resilience. But you need the stockpiled footage to pull it off.

- **The Scandal Goldmine:** A tabloid story breaks about a cast member's pre-show secret. The Fallout System generates the event; the burn book updates with the revelation; the Situation Engine makes other cast members react to the news; the edit bay gets explosive confessional footage; the Ratings Engine spikes. But the cast member's PI plummets, legal risk skyrockets, and the network wants to know if you knew about the secret all along. Did you? And if you did, did you plant the leak?

- **The Rival Counter-Program (stretch goal interaction):** Your rival showrunner airs a romance-heavy episode. Romantics in your shared audience migrate to their show. You need to either counter-program (air a drama-heavy episode to lock in your non-Romantic segments) or compete (rush a love story that may feel forced). The Situation Engine may not have generated the romance footage you need. Do you manufacture it with catalysts, or pivot your strategy?

---

## 5. PROGRESSION DESIGN

### 5.1 Player Growth Axes

The player grows along four axes simultaneously:

**Skill Mastery (Player Knowledge):**
- Reading burn book entries and predicting behavior accurately
- Understanding situation engine combinatorics (which cast + location + catalyst = which outcome type)
- Developing editorial instinct (pacing, juxtaposition, tonal control)
- Learning to read ratings reports and triangulate audience segment needs
- Managing cast PI sustainably

**Showrunner Reputation (Character Progression):**
Reputation is the game's primary meta-currency. It ranges from 0-100 and affects:

| Reputation Range | Title | Casting Pool | Budget Multiplier | Network Tolerance | Format Options |
|---|---|---|---|---|---|
| 0-15 | Nobody | D-tier (bland, unstable, desperate) | 0.6x | Very Low | 1 basic format |
| 16-30 | Rookie | C-tier (some spark, limited range) | 0.8x | Low | 2 basic formats |
| 31-50 | Established | B-tier (diverse, interesting, some with baggage) | 1.0x | Medium | 3 formats + 1 hybrid |
| 51-70 | Veteran | A-tier (charismatic, complex, in-demand) | 1.3x | High | All formats + custom |
| 71-85 | Auteur | S-tier (legends, wild cards, crossovers) | 1.6x | Very High | Full format lab access |
| 86-100 | Icon | S+-tier (anyone you want, bidding wars) | 2.0x | Maximum | Unlimited |

**Content Unlocks (System Expansion):**

| Season Completed | Unlock |
|---|---|
| Season 1 | Basic edit bay tools, 3 catalyst types, 4 locations |
| Season 2 | Advanced music cues, confessional overlay editing, 2 new catalyst types |
| Season 3 | Chyron writing, juxtaposition scoring visible, 3 new locations |
| Season 4 | Mid-scene interventions, producer conversations, informant system |
| Season 5 | Flashback editing (pull footage from previous episodes), advanced catalyst timing |
| Season 6 | Format customization, audience segment targeting, narrative arc planning tools |
| Season 7+ | Legacy systems, rival showrunner (stretch goal), cultural moment tracking |

**Legacy (Persistent World-State):**
The game world accumulates history. Former cast members exist in the simulated culture. Previous seasons are referenced. The player's choices have created a body of work that the simulated public, critics, and industry remember. This isn't a stat -- it's the texture of the late game.

### 5.2 Difficulty Curve

BURNBOOK uses a **stepped difficulty curve** with periodic pressure spikes:

```
Difficulty
  ^
  |                                                         ___/
  |                                                    ___/
  |                                               ___/
  |                                          _/ __|
  |                                     ___/
  |                                _/ __|
  |                           ___/
  |                      _/ __|
  |                 ___/
  |            __/ |
  |       ___/
  |  __/ |
  | /
  +---------------------------------------------------------> Time
   S1    S2    S3    S4    S5    S6    S7    S8+

   /  = Gradual increase within a season
   |  = Pressure spike (mid-season crisis, network intervention)
   _  = Plateau (player masters current challenge set before next escalation)
```

**Season 1 (Tutorial Season):** Reduced cast (6 members). One show format ("House of Strangers" -- The Real World template). Simplified edit bay (4 segments per episode). Network is lenient (NSS threshold for cancellation is 15 instead of 25). Burn book accuracy is higher (less decay). Cast PI starts at 100 and decays slower. The goal is to teach the core loop without overwhelming.

**Season 2 (Training Wheels Off):** Full cast (10 members). Second format option available. Full edit bay (6 segments). Normal network expectations. Introduction of the fallout system's post-show consequences (Season 1 cast outcomes arrive). First encounter with decayed burn book intel.

**Season 3-4 (Mastery Zone):** 12-16 cast members. Multiple formats. Full system complexity. Network demands become specific and occasionally conflicting. Rival showrunner appears (if stretch goal is implemented). The player's reputation from Seasons 1-2 begins to compound -- good or bad.

**Season 5+ (Expert Play):** All systems fully unlocked. Difficulty comes from complexity management, long-tail consequences, and the increasing weight of legacy. The game doesn't get "harder" in the arcade sense -- it gets *denser*. More variables, more history, more consequences echoing forward. This is where the game asks: how does this feel at hour 100?

### 5.3 Pacing

The pacing follows a **teach-test-expand** cadence:

| Phase | Duration | New Content | Test |
|---|---|---|---|
| Early Season 1 (Ep 1-3) | 90 min | Core loop: place, shoot, harvest, edit, broadcast | Can you produce a coherent episode? |
| Late Season 1 (Ep 4-8) | 2.5 hrs | Burn book management, catalyst timing, multi-arc editing | Can you sustain ratings over multiple episodes? |
| Season 2 (Ep 1-10) | 4 hrs | Fallout system, cast sustainability, audience segmentation | Can you complete a season without a cancellation scare? |
| Season 3 | 4 hrs | Advanced editing, format switching, network negotiation | Can you grow your audience while managing legacy fallout? |
| Season 4+ | 3-4 hrs each | Incremental unlocks, increasing complexity, legacy weight | Can you build a career, not just a season? |

**Session Length Target:** A single episode (the natural play session) takes 25-35 minutes. A season takes 4-6 hours across multiple sessions. A full career arc (Seasons 1-8) takes 30-45 hours. This maps to the management sim sweet spot: meaningful progress per session, long-term investment across sessions.

---

## 6. ECONOMY DESIGN

### 6.1 Production Budget

The production budget is the primary resource currency. It's earned through ad revenue (driven by ratings and ACI) and spent on production activities.

**Income Per Episode:**

```
Episode Revenue = Base Ad Rate x Nielsen Rating x ACI Modifier x Episode Count Bonus

Base Ad Rate = $50,000 (Season 1) scaling to $200,000 (Season 8+)
ACI Modifier = ACI / 100 (so ACI of 70 = 0.7x multiplier)
Episode Count Bonus = 1.0 + (0.02 x Episodes Aired This Season) -- rewards consistency
```

**Expense Categories:**

| Category | Cost Range Per Episode | Notes |
|---|---|---|
| Cast Salaries | $5,000-$50,000 total | Higher-tier cast costs more. Stars from previous seasons demand premiums. |
| Location Fees | $1,000-$10,000 per scene | Basic sets are cheap. Special locations (yacht, mansion, exotic locale) are expensive. |
| Catalysts | $0-$5,000 per catalyst | See catalyst table. Some catalysts are free but carry hidden costs. |
| Producer Staff | $3,000-$15,000 per episode | Hiring additional producers (stretch goal) costs money but adds capabilities. |
| Legal Reserve | 5-15% of total budget | Mandatory. Underfunding legal increases lawsuit risk. |
| Post-Production | $2,000-$8,000 per episode | Better post-production = more music cues, better edit bay tools. |
| Contingency | Player-determined | Smart money. Crises cost money to resolve. |

**Budget Tension:** Revenue is driven by ratings (which reward drama) but expenses increase with drama (catalysts, legal reserve, cast replacements). The profitable show isn't the most dramatic show -- it's the most efficiently dramatic show. Maximum drama per dollar spent. This is the economic expression of the core design: exploitation as optimization.

### 6.2 Resource Conversion Table

```
Intel (Burn Book) --[informs]--> Scene Quality (Situation Engine)
Scene Quality --[produces]--> Footage Quality (Edit Bay Input)
Footage Quality --[assembled into]--> Episode Quality (Edit Bay Output)
Episode Quality --[determines]--> Ratings (Ratings Engine)
Ratings --[generates]--> Revenue + Reputation
Revenue --[funds]--> Next Episode's Budget
Reputation --[unlocks]--> Better Cast, Formats, Tools
Cast PI --[constrains]--> Scene Quality (stressed cast = volatile footage)
Fallout Events --[threaten]--> Revenue (scandals) + Reputation (legacy damage)
```

Every resource converts into every other resource through at most two intermediate steps. This creates a tightly coupled economy where no single resource can be safely neglected.

---

## 7. RISK ASSESSMENT

### 7.1 What Could Be Unfun?

| Risk | Description | Severity | Mitigation |
|---|---|---|---|
| **Edit Bay Tedium** | If the edit bay feels like actual video editing software, it becomes work instead of play | Critical | Simplify to segment-based assembly. No frame-level editing. Music cues are one-click selections. The creative act is CHOICE (which moments, what order), not CRAFT (trimming, color grading, transitions). |
| **Burn Book Information Overload** | Too many stats, too many cast members, too many data points to track | High | Progressive disclosure. Early seasons show simplified profiles. Advanced stats unlock over time. Visual design (physical dossier aesthetic) makes scanning natural. Burn book "summary" page per cast member with key stats highlighted. |
| **Scene Passivity** | Watching AI resolve scenes could feel like watching, not playing | High | Mid-scene intervention tools give active control. Multi-camera switching keeps attention engaged. Drama spike alerts create micro-moments of excitement. Scene length capped at 90-120 seconds of player time. |
| **Ratings Opacity** | If the player can't understand why ratings went up or down, the feedback loop breaks | High | Ratings report includes explicit attribution: "Drama Addicts responded to the Marcus/Jade confrontation (+0.3). Romantics tuned out during the elimination segment (-0.1)." Make the math legible. |
| **Cast Sameness** | If procedurally generated cast members feel interchangeable, the emotional core collapses | Critical | Archetype system ensures cast members feel distinct. Unique backstory elements (not just stat variations). Memorable trait combinations flagged during casting. Cast members who feel generic should be culled from the generation pool during QA. |
| **Moral Fatigue** | If the game constantly punishes the player for doing the only thing the game rewards (exploitation), it feels like a lecture | High | The game NEVER moralizes. It shows consequences without judgment. The fallout system is a mechanical constraint, not a moral punishment. Positive outcomes exist for cast members -- the game isn't rigged to make you feel bad. The player discovers the moral dimension through gameplay, not through the game wagging its finger. |
| **Pacing Drag in Mid-Seasons** | Episodes 4-6 of a season can feel like a slog if the season arc isn't compelling | Medium | Mid-season twists are systemically generated: surprise cast additions, format changes, scandal events. These break monotony and force strategic adaptation. |
| **Late-Game Complexity Overload** | By Season 6+, the number of systems, legacy consequences, and variables could overwhelm | Medium | Automation options for experienced players: auto-schedule scenes, suggested edits, burn book alerts for critical changes. The player can delegate micro-management and focus on strategic decisions. |

### 7.2 Playtest Priorities (Ordered)

**Playtest 1: The Situation Engine (Highest Priority)**

The entire game depends on AI cast members producing interesting, unpredictable, believable social interactions. If the Situation Engine generates boring scenes, repetitive conflicts, or nonsensical behavior, nothing else matters.

- **Test:** Four cast members, one dinner scene, ten runs with same setup. Do the outcomes vary meaningfully? Do they feel believable? Is there at least one surprise per run?
- **Success Metric:** Testers should be able to describe what happened in each run as a distinct story, not a statistical variation.
- **Kill Condition:** If more than 30% of scenes feel "samey" after ten runs, the AI behavior model needs fundamental rework.

**Playtest 2: The Edit Bay (Second Priority)**

The edit bay is the unique mechanic. It has to feel like wielding narrative power, not doing homework.

- **Test:** Give testers pre-generated footage from three scenes. Ask them to assemble a 6-segment episode. Time them. Survey them. Do they feel creative? Do they feel in control? Or do they feel like they're sorting files?
- **Success Metric:** Average assembly time under 10 minutes. Satisfaction score above 7/10. Testers voluntarily rearrange segments (indicating engagement with editorial choice, not just slot-filling).
- **Kill Condition:** If more than 40% of testers describe the edit bay as "tedious" or "confusing," simplify aggressively. Cut to 4 segments. Remove music cues. Strip it to the essential verb: CHOOSE WHAT AIRS.

**Playtest 3: The 30-Second Loop (Third Priority)**

The placement bet needs to feel like a bet -- tension, prediction, surprise.

- **Test:** Isolated scene setup. Player reads two burn book profiles, places cast at a dinner table, watches the scene resolve. Does the moment of placement feel charged with possibility? Does the resolution feel connected to the player's choice?
- **Success Metric:** Players should be able to articulate WHY they placed cast members where they did, and whether the outcome matched, exceeded, or subverted their expectation.
- **Kill Condition:** If players describe placement as "random" or "doesn't matter what I do," the connection between burn book intel and scene outcome needs strengthening.

**Playtest 4: Episode Pacing (Fourth Priority)**

Does a full episode (plan, shoot, edit, broadcast) feel like a satisfying session? Or does it drag?

- **Test:** Full episode playthrough with timer. Where do players check their phones? Where do they lean in? Where do they feel stuck?
- **Success Metric:** Consistent engagement across the 25-35 minute session. No single phase exceeds 40% of total time. Players want to start the next episode immediately.
- **Kill Condition:** If more than 25% of play time is spent in any single phase, that phase needs compression. The loop should feel like it's always moving forward.

**Playtest 5: Season Arc and Meta Progression (Fifth Priority)**

Does the season-level game hold interest? Does between-season progression feel meaningful?

- **Test:** Compressed season (4 episodes instead of 8). Full casting, episode cycle, and finale. Does the season feel like a complete arc? Does the player care about the outcome?
- **Success Metric:** Players have a favorite cast member. Players describe narrative arcs that emerged organically. Players express interest in "what happens next season."
- **Kill Condition:** If players describe the season as "just a series of episodes" without arc or momentum, the mid-season event system and elimination mechanics need more dramatic weight.

---

## 8. BALANCE FRAMEWORK

### 8.1 Core Balance Levers

These are the primary tuning variables that control the game's feel:

| Lever | Low Setting Effect | High Setting Effect | Starting Value | Tuning Range |
|---|---|---|---|---|
| PI Decay Rate | Cast is resilient, less urgency | Cast burns fast, constant crisis | -3 base/episode | -1 to -8 |
| Burn Book Decay | Intel stays reliable, less maintenance | Intel rots fast, requires constant upkeep | -5% confidence/episode | -2% to -12% |
| Drama Value Scaling | Low drama per scene, hard to hit ratings | High drama per scene, easy ratings | See formula above | x0.5 to x2.0 |
| Audience Patience | Segments forgive bad episodes | Segments exodus quickly | 3 episodes before exodus | 2-5 episodes |
| Budget Tightness | Lots of money, low economic pressure | Tight budget, hard tradeoffs | Break-even at 1.8 Nielsen | 1.2 to 2.5 |
| Network Tolerance | Network is hands-off | Network micromanages | NSS threshold 40 | 25-60 |

### 8.2 Difficulty Modes

Rather than traditional easy/medium/hard, BURNBOOK offers **Network Settings:**

- **Basic Cable:** Generous budgets, patient network, cast is resilient, audiences are forgiving. For players who want to explore systems without pressure. (All levers shifted toward the forgiving end.)
- **Network Television:** Standard balance. The intended experience. Every system has teeth but the player has room to recover from mistakes.
- **Premium Cable:** Tight budgets, demanding network, fragile cast, fickle audiences. For players who want the strategy game to bite. One bad season can end your career.
- **Reality TV Hell (unlocked after completing one career):** Everything at maximum difficulty. Cast is on the edge of breakdown at all times. Network threatens cancellation constantly. Audiences flee at the slightest boredom. Budget is razor-thin. The pure optimization challenge for mastery players.

---

## 9. OPEN QUESTIONS FOR PLAYTESTING

These are the questions this document cannot answer. Only putting the game in front of real players will resolve them.

1. **Scene Resolution Speed:** The pitch suggests compressed scenes with the ability to "let it play" on key moments. But what's the right default speed? Too fast and players can't follow the AI behavior. Too slow and scenes feel like watching paint dry. Playtest with three speeds (2x, 1x, 0.5x) and measure engagement.

2. **Edit Bay Granularity:** This document specifies 6-8 segments with one-click music cues and drag-and-drop assembly. Is that too simple? Too complex? The edit bay must feel like *authorship* -- the player must feel that their editorial choices meaningfully change the episode's meaning. If testers report the edit bay feels "on rails" or "obvious," add granularity. If it feels "overwhelming," simplify. This is the highest-variance mechanic in the game.

3. **Burn Book Confidence Visibility:** Should the player see exact confidence numbers (87% accuracy) or fuzzy visual indicators (clean text vs. worn text)? Exact numbers create optimization behavior. Fuzzy indicators create gut-feel behavior. The pitch leans toward fuzzy. But if testers report feeling frustrated by unreliable intel without understanding WHY it's unreliable, exact numbers may be necessary as an advanced option.

4. **Cast Attachment Threshold:** How long does it take before a player cares about a procedurally generated cast member? If the answer is "never," the game's emotional core fails. Test: after a full season, can 80% of testers name at least 3 cast members and describe their arc? If not, the procedural generation needs more "signature moments" -- scripted-feeling events that crystallize a cast member's identity.

5. **Moral Weight Calibration:** The game's thematic power depends on the player eventually feeling the weight of their exploitation. Too early and it feels preachy. Too late (or never) and it's just a cynical optimization game. When do post-show outcomes first surface? How graphic are the negative outcomes? How much screen time do they get? This is a tone question as much as a design question, and it requires iterative playtesting with diverse players.

6. **Session Length Tolerance:** This document targets 25-35 minutes per episode. But management sim players are notoriously bad at stopping. If episodes routinely run 45-60 minutes because players spend too long in the edit bay or re-reading burn books, do we compress the episode structure or accept longer sessions? Measure actual session lengths vs. target session lengths and adjust.

7. **The "I Feel Bad" Inflection Point:** There will be a moment in every playthrough where the player first feels genuinely uncomfortable with what they're doing. This is the game's most important moment. Where does it happen? Is it consistent? If it happens too randomly (or never), the emotional arc fails. Track this moment in playtests. Ask: "Was there a point where you hesitated before making a decision? What was it?" Build the game around protecting and enhancing that moment.

8. **Audience Segment Legibility:** Can players intuit what each audience segment wants without reading a manual? If Drama Addicts and Chaos Agents feel interchangeable, collapse them. If Justice Seekers' preferences feel opaque, add clearer feedback. The five-segment model should feel like managing five distinct constituencies with distinct appetites -- not five arbitrary numbers.

9. **Inter-Season Pacing:** Is the between-seasons phase interesting or does it feel like administrative busywork before the "real game" starts again? The casting phase needs to feel like draft day -- exciting, strategic, full of potential. If it feels like filling out paperwork, it needs dramatic structure: casting tapes as mini-narratives, bidding wars for popular cast members, surprise candidates who weren't in the initial pool.

10. **The "One More Episode" Factor:** The ultimate test. When a player finishes an episode at 11 PM on a weeknight, do they start the next one? If yes, the loop works. If no, something in the cycle is creating a natural stopping point that doesn't compel continuation. Find that stopping point and eliminate it -- or move it to after the next episode's cold open, so the player is hooked into the next cycle before they realize they should be sleeping.

---

## 10. CLOSING NOTES

Here's what I know after designing this document: BURNBOOK has one of the strongest core fantasies I've encountered. "Reality TV showrunner with AI cast" isn't just a clever theme -- it's a mechanical premise that generates systems naturally. The burn book is an intel system. The situation engine is a simulation. The edit bay is a narrative tool. The ratings engine is a feedback system. The fallout system is a consequence engine. These aren't bolted-on features. They emerge from the fantasy itself. When the fantasy generates the mechanics, you know you're building something real.

What concerns me: complexity management. Five interlocking systems is a lot. Each one is justified, but their combined cognitive load could overwhelm. The progressive unlock schedule (Section 5.3) is the first defense. The difficulty modes (Section 8.2) are the second. But the third and most important defense is clarity of feedback. If the player always knows what happened, why it happened, and what they can do about it, complexity becomes depth instead of confusion. Every system in this document must communicate its state clearly, or it becomes noise.

What excites me: the edit bay. No game has this mechanic. The act of selecting which moments air, placing them in sequence, choosing the music that reframes their meaning -- this is authorship as gameplay. It's the mechanic that transforms BURNBOOK from "reality TV management sim" into something genuinely new. Protect it. Playtest it obsessively. If the edit bay sings, the game sings.

What's the loop? Place, shoot, cut, air, suffer. It's tight. It's deep. And it holds at hour 100.

Let's build this.

-- REED

---

*Document generated following the /game-design structured workflow.*
*All sections complete. No placeholders. No TODOs. Ready for prototype phase.*