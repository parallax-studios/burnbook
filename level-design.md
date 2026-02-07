# BURNBOOK -- Level Design Document

*Written by GRID, Level Designer*

*"Where does the player LOOK? What's the flow? Every room teaches something."*

---

## 0. SPATIAL PHILOSOPHY

Let me be direct about what level design means in a game with no 3D levels.

BURNBOOK is not a game where the player walks through spaces. It is a game where the player ARRANGES spaces, OBSERVES spaces through mediated feeds, and NAVIGATES interfaces that ARE spaces. The production suite is not a backdrop. It is the playspace. The set is not explorable. It is a stage viewed through camera feeds. The edit bay is not a room. It is the room -- the place where every player spends the most time, makes the most consequential decisions, and feels the weight of the work.

So level design here means something specific: it means designing SIGHTLINES through interfaces, FLOW through workflows, PACING through production cycles, and SPATIAL GRAMMAR that teaches the player to read human arrangements as strategic problems. Where does the player LOOK when they open the burn book? What's the critical path through a scene setup? How does the eye move through the edit bay timeline? What breadcrumbs guide a beginner from placement to broadcast without them realizing they are being taught?

Every screen is a level. Every interface is a lesson. Every room in the production suite has a purpose statement, a flow diagram, and a teaching moment. That is what this document designs.

---

## 1. THE PRODUCTION SUITE -- META-LEVEL SPATIAL STRUCTURE

### 1.1 Level Purpose Statement

**Purpose:** The production suite is the player's HOME. It is where every session begins, where every decision returns, and where the weight of accumulated choices becomes visible through environmental storytelling. The suite must feel institutional but lived-in, professional but personal, powerful but claustrophobic.

**Emotional Beat:** COMMAND. The player sits at the center of a machinery of surveillance and control. They see everything. They decide everything. The spatial design must communicate omniscience and authorship without ever letting the player forget they are in a windowless office at 3 AM.

### 1.2 Spatial Layout (Hub Structure)

The production suite functions as a STAR HUB -- a central navigation space with five critical rooms accessible as distinct play zones:

```
                    [HALLWAY -- Central Hub]
                              |
        +----------+----------+----------+----------+
        |          |          |          |          |
   [CASTING]  [CONTROL]   [EDIT BAY] [OFFICE]  [ARCHIVE]
    ROOM        ROOM                              (unlock S3+)

Flow: Player spawns in OFFICE --> Moves to rooms based on production phase
```

**Critical Path:** OFFICE (strategic planning) --> CASTING ROOM (season start only) --> CONTROL ROOM (scene execution) --> EDIT BAY (episode assembly) --> OFFICE (broadcast & consequence) --> Repeat.

**Teaching Moment:** The hub structure teaches phase-based workflow. Each room is a VERB. Casting = SELECT. Control Room = OBSERVE. Edit Bay = RESHAPE. Office = EVALUATE. By episode three, the player navigates by workflow instinct, not UI prompts.

### 1.3 Sightlines and Wayfinding

**Entry Sightline:** When the player enters the suite (new session, between episodes), the OFFICE is the anchor view. The desk is front-center. The corkboard with cast photos is visible on the left wall. A phone is blinking red (network message) or green (all clear). The player's eye goes: desk --> corkboard --> phone. That's the session status at a glance.

**Hallway Breadcrumbing:** The hallway has FUNCTIONAL LIGHTING that guides without hand-holding:
- **Casting Room:** Door light is YELLOW during casting phase, OFF otherwise.
- **Control Room:** Door light PULSES GREEN when scenes are ready to shoot.
- **Edit Bay:** Door light is STEADY RED when footage is waiting for edit, DARK RED when an episode is overdue.
- **Office:** Door light is WHITE (neutral) unless a network call is waiting (BLINKING WHITE).

The player does not read a checklist. The player reads LIGHT.

**Visual Hierarchy Rule:** At any moment, the most urgent task is the BRIGHTEST or most ANIMATED element in the hallway. The player's eye is drawn to activity. Silence and darkness mean completion or waiting.

### 1.4 Environmental Storytelling (Progression Through Accumulation)

The production suite REMEMBERS. It accumulates detail across seasons:

**Season 1:**
- Office corkboard: 6-8 cast headshots, minimal red string, Post-its with simple notes ("Jade -- pageant queen?").
- Edit bay desk: Clean. One coffee cup. A production binder.
- Hallway: Empty. No framed photos.

**Season 3:**
- Office corkboard: 20+ cast photos from S1-S3, dense red string mapping alliances and eliminations, Post-its stacked and color-coded, some photos have RED Xs (walkoffs), some have GOLD stars (breakout successes).
- Edit bay desk: Three coffee cups (time is compressing). Stacks of VHS tapes labeled by episode. Crumpled call sheets. A stress ball with bite marks.
- Hallway: Framed photos of past season casts. The first photo is Season 1. The player walks past their own history.

**Season 6+:**
- Office corkboard: Overwhelming. Cast photos overlap. Red string is a web. Some Post-its are crossed out and replaced. A tabloid clipping is pinned with "LAWSUIT SETTLED" scrawled across it.
- Edit bay desk: Chaos. Coffee cup graveyard. Legal notes stacked. A framed photo of Season 1's cast (nostalgia? guilt?).
- Hallway: Full gallery. Former cast faces stare as the player walks. One photo has been removed, leaving a darker rectangle on the wall. Who was that?

**Teaching Moment:** The suite does not TELL the player they are accumulating consequence. It SHOWS. The visual density increases. The spatial clutter becomes the weight of history. By Season 5, the player FEELS the past pressing on every decision.

### 1.5 Spatial Grammar: The "Intimacy Gradient"

Every room in the suite has a DISTANCE from the cast. This gradient teaches the player their relationship to the people they are producing:

```
CLOSEST TO CAST                                    FURTHEST FROM CAST
|-----------|------------|--------------|------------------|
CASTING     CONTROL      EDIT BAY       OFFICE             ARCHIVE
ROOM        ROOM
(face to    (live        (mediated,     (pure data:       (history,
 face)       feed,        delayed,       ratings,          ghosts)
             real-time)   reordered)     reports)
```

**Teaching Moment:** The player is CLOSEST to the cast when they have the LEAST control (casting -- you meet them but cannot shape them yet). The player is FURTHEST from the cast when they have the MOST control (office -- pure strategic abstraction). This gradient is the game's spatial metaphor: control requires distance. Intimacy is a liability. The player learns this by MOVING through spaces.

---

## 2. THE CASTING ROOM -- LEVEL DESIGN

### 2.1 Level Purpose Statement

**Purpose:** To teach the player the REDUCTIVE ACT of turning a human being into a profile. This room is where the burn book begins. The player sits across a table from a person and decides: content or not content?

**Emotional Beat:** ASSESSMENT. Cool, professional, slightly predatory. The player is shopping for personalities.

### 2.2 Flow Diagram (Top-Down)

```
CASTING ROOM LAYOUT (Player POV, looking at candidate)
=======================================================

                [CAMERA ON TRIPOD]
                        |
                        V
        +-------------------------------+
        |  CANDIDATE                    |  <-- Candidate sits here
        |  (chair, facing camera)       |      Visible emotion states
        +-------------------------------+

                    [TABLE]
                  (between)

        +-------------------------------+
        |  PLAYER POSITION              |  <-- UI overlays here
        |  (implied, not visible)       |      Burn book begins here
        +-------------------------------+

SIGHTLINE: Player eye focuses on CANDIDATE FACE (center screen, slightly above center)
SECONDARY: Burn book UI is OVERLAY, right side, non-intrusive
TERTIARY: "CAST" or "PASS" buttons bottom center
```

**Critical Path:**
1. Candidate enters (animation: door opens, person sits, nervous adjustment).
2. Casting tape AUTO-PLAYS (15-30 seconds, skip-able).
3. Burn book entry POPULATES with SURFACE DATA (name, age, hometown, stated reason for applying).
4. Player INTERVIEWS (optional) -- click candidate to hear 3-5 pre-recorded responses to producer questions.
5. Burn book DEEP DATA unlocks partially (personality scores, psychological flags, predicted behavior).
6. Player decides: CAST (candidate joins pool) or PASS (candidate removed).

**Loop Time:** 60-90 seconds per candidate. 8-16 candidates per casting phase. Total time: 10-20 minutes.

### 2.3 Pacing Curve (Casting Phase)

```
Engagement
    ^
    |
    |    *                   *                    *
    |   * *                 * *                  * *     (spikes: interesting
    |  *   *     *         *   *        *       *   *     candidates, weird
    | *     *   * *       *     *      * *     *     *    backstories, red
    |*       * *   *     *       *    *   *   *       *   flags)
    |         *     *   *         *  *     * *         *
    +----------------------------------------------------> Time
    0       3-4    6-7   9-10    12-13  15-16    18-20min

    Candidate Candidate Candidate Candidate Candidate
       1-3      4-6       7-10      11-13     14-16
```

**Difficulty Consideration:** Early candidates are LEGIBLE -- clear archetypes, obvious casting choices. Late candidates are COMPLEX -- mixed traits, contradictory profiles, harder to predict. This teaches the player to TAKE RISKS on the candidates they are unsure about because those are the ones who generate emergent drama.

**Breadcrumbing:** The first 2-3 candidates in Season 1 have TUTORIAL TOOLTIPS that explain burn book data ("This number measures STRESS TOLERANCE. Low = fragile, high = resilient"). By candidate 4, tooltips are gone. The player is reading profiles independently.

### 2.4 Teaching Moment: The Reductive Act

The casting room teaches the player that SEEING A PERSON and PROFILING A PERSON are the same action. The candidate sits across from you (visually, they are centered, human, present). The burn book entry is a UI overlay (data, reductive, cold). The player must LOOK AT THE PERSON while WRITING ABOUT THEM as if they are not there. This spatial contradiction -- intimacy and abstraction in the same view -- IS the game's first moral beat.

No text explains this. The room SHOWS it.

---

## 3. THE CONTROL ROOM -- LEVEL DESIGN

### 3.1 Level Purpose Statement

**Purpose:** To give the player the PANOPTICON VIEW. The control room is where the player watches scenes unfold in real-time across multiple camera feeds. This is where the player feels omniscient but not omnipotent. You can see everything. You control very little.

**Emotional Beat:** SURVEILLANCE. Tense, focused, voyeuristic. The feeling of watching people who do not know you are watching (or have learned to perform for the cameras, which is worse).

### 3.2 Flow Diagram (Multi-Monitor Layout)

```
CONTROL ROOM -- PLAYER POV (seated at console)
================================================

+-------------+  +-------------+  +-------------+  +-------------+
| CAMERA 1    |  | CAMERA 2    |  | CAMERA 3    |  | CAMERA 4    |
| (Wide Shot) |  | (Close: A)  |  | (Close: B)  |  | (Alt Angle) |
|             |  |             |  |             |  |             |
| [Live Feed] |  | [Live Feed] |  | [Live Feed] |  | [Live Feed] |
+-------------+  +-------------+  +-------------+  +-------------+

                        [PRODUCER'S MONITOR]
                     (center, below main feeds)
                +---------------------------+
                | Scene Timer: 01:24 / 02:00|
                | Drama Spikes: **          | <-- visual indicators
                | Tension Meters (per cast) |
                | Mid-Scene Intervention?   | <-- action button
                +---------------------------+

BOTTOM UI BAR (always visible):
[Scene Status] [Cast Emotional States] [Catalyst Activation Log] [End Scene]
```

**Critical Path:**
1. Scene SETUP (previous step, not in this room -- player arrives from scene planning).
2. Scene BEGINS (auto-starts, cameras go live, cast enters).
3. Player OBSERVES -- switches between camera feeds, watches tension meters.
4. Drama SPIKES trigger (pop-up alerts: "Jade confronts Marcus -- DV 78").
5. Player OPTIONALLY intervenes mid-scene (costly, risky, rare).
6. Scene ENDS (2-3 minutes elapsed).
7. Footage HARVEST screen (next step: tag moments for edit bay).

**Loop Time:** 90-120 seconds of scene observation + 30-60 seconds of harvest = 2-3 minutes per scene.

### 3.3 Sightlines and Information Hierarchy

Where does the player LOOK during a live scene?

**Primary Sightline:** CENTER MONITOR (Producer's Monitor). This is the "main" view, the default focus. It shows the widest angle and contains the critical UI (tension meters, drama spike alerts).

**Secondary Sightline:** CAMERA 2 and CAMERA 3 (close-ups). When the player wants to READ A FACE, they switch to close-ups. These feeds show MICRO-EXPRESSIONS, the subtle emotional shifts that signal a cast member is about to crack or lie or confess.

**Tertiary Sightline:** CAMERA 4 (alt angle). This is the "oh shit" camera -- the angle that catches something the main cameras missed. A whispered conversation in the corner. A hand gesture out of frame. The player learns to CHECK CAMERA 4 when something feels wrong.

**Teaching Moment:** By episode 2, expert players develop a SCANNING PATTERN: start on Producer's Monitor (wide view + UI) --> watch tension meters --> SPIKE ALERT triggers --> switch to close-up of relevant cast member --> confirm reaction --> return to Producer's Monitor. This pattern is never taught explicitly. The UI placement and alert timing TRAIN the pattern through repetition.

### 3.4 Pacing Curve (Scene Cycle)

```
Tension
    ^
    |                              X  <-- Drama Spike (climax)
    |                            /  \
    |                          /      \
    |                        /          \
    |                      /              \
    |                    /                  \___
    |                  /                         \
    |                /                             \
    |              /                                 \
    |            /                                     \
    |          /                                         \
    |        /                                             \
    +-------------------------------------------------------------> Time
         0s    15s    30s     45s     60s     75s    90s   120s

     [SETUP] [RISING TENSION] [SPIKE] [RESOLUTION or FALLOUT]
                 (build)      (event)      (aftermath)
```

**Pacing Rule:** Every scene has a SPIKE MOMENT (the dramatic event the player engineered or that emerged organically) and a RESOLUTION TAIL (the 20-30 seconds after the spike where cast members process what just happened). The player is tempted to END SCENE immediately after the spike (efficiency). Expert players WAIT for the resolution tail because that is where the most authentic emotional footage lives.

**Breadcrumbing:** The first time a drama spike occurs (tutorial scene, Season 1 Episode 1), the END SCENE button is DISABLED for 15 seconds after the spike. This FORCES the player to watch the aftermath. The game is teaching: the explosion is obvious content. The fallout is GOOD content.

### 3.5 Encounter Breakdown: Scene Types

Scenes are the ENCOUNTERS of BURNBOOK. Each scene type has a different spatial grammar and teaches a different lesson.

#### 3.5.1 DINNER TABLE SCENE (High Intimacy, Low Escape)

**Purpose:** Force confrontation through proximity. The dinner table pins cast members in chairs, facing each other, with nowhere to go. This is the PRESSURE COOKER encounter.

**Flow:**
- Cast members enter and SIT (assigned positions, player-determined).
- Conversation begins (AI-driven, player observes).
- Catalyst triggers (if planted: alcohol, overheard comment, planted letter).
- Tension escalates (cast cannot leave without "making a scene" -- social contract).
- Spike moment (confrontation, confession, or breakdown).
- Resolution (aftermath, alliances shift).

**Difficulty Variables:**
- Number of cast (6-8 = complex social dynamics, 2-4 = focused tension).
- Seating arrangement (who sits next to whom determines interaction flow).
- Catalyst intensity (low = slow burn, high = instant explosion).

**Teaching Moment:** Dinner scenes teach SETUP PRECISION. Where you place people MATTERS. Jade next to Marcus is different from Jade across from Marcus is different from Jade at the far end with Marcus in the middle. The spatial arrangement becomes a strategic language.

#### 3.5.2 HOT TUB SCENE (Maximum Intimacy, Minimal Escape)

**Purpose:** Create artificial closeness. The hot tub forces physical proximity and lowers inhibitions (alcohol, nighttime, vulnerability of swimwear). This is the CONFESSION BOX encounter.

**Flow:**
- 2-4 cast members enter (more than 4 is chaos, less than 2 is boring).
- Conversation starts light, turns personal (AI behavior + optional alcohol catalyst).
- Secrets surface (burn book-predicted vulnerabilities emerge under relaxed conditions).
- Spike moment (usually a revelation, occasionally a confrontation).
- Resolution (intimacy deepens OR trust breaks).

**Teaching Moment:** Hot tub scenes teach CATALYST TIMING. The same cast members in a hot tub WITHOUT alcohol produce one scene. WITH alcohol produce another. LATE NIGHT (high stress, low energy) produces a third. The player learns to layer variables.

#### 3.5.3 CONFESSIONAL BOOTH (Isolated Monologue)

**Purpose:** Give cast members a space to SPEAK DIRECTLY to the audience (via camera). The confessional is the most honest and most performed space simultaneously. This is the TESTIMONY encounter.

**Flow:**
- Single cast member enters booth (triggered by emotional spike in previous scene OR scheduled by player).
- Producer prompt appears (optional: player can ask specific questions or let cast free-talk).
- Cast member speaks (AI-generated monologue based on emotional state, recent events, burn book psychology).
- Player receives FOOTAGE TAGGED by authenticity, drama value, narrative utility.

**Difficulty Variables:**
- Emotional state (calm = rehearsed, stressed = raw, breaking = incoherent).
- Trust level (cast member aware of manipulation = guarded confessionals).

**Teaching Moment:** Confessionals teach EDITORIAL POWER. The footage captured here is GOLD for the edit bay because it is talking-head content that can be placed ANYWHERE in the timeline to recontextualize ANY action. The player learns to HARVEST confessionals strategically, not just when cast members volunteer.

#### 3.5.4 COMPETITION/CHALLENGE SCENE (Low Intimacy, High Stakes)

**Purpose:** Create external pressure that reveals internal character. The challenge is not about the challenge. It is about how cast members behave under competitive stress. This is the PRESSURE TEST encounter.

**Flow:**
- All cast members (or subset) enter competition arena.
- Challenge rules explained (AI-narrated, similar to reality TV format).
- Competition runs (physical or mental task, AI resolves based on cast stats + random variance).
- Winner and loser determined.
- Aftermath interviews/reactions (confessionals triggered).

**Difficulty Variables:**
- Challenge type (physical = reveals ego, mental = reveals insecurity, team-based = reveals loyalty).
- Stakes (low = playful, high = desperation).

**Teaching Moment:** Challenge scenes teach AFTERMATH FOCUS. The competition itself is filler. The interesting footage is cast members' reactions to winning or losing. The player learns to place cameras on the LOSERS, not the winners.

### 3.6 Difficulty Considerations

**Scene Complexity Progression:**

**Season 1, Episodes 1-3:** Simple scenes. 2-4 cast, single location, one variable. Teaching the player to READ behavior.

**Season 1, Episodes 4-8:** Multi-cast scenes (6-8 people). Multiple variables (location + catalyst + information asymmetry). Teaching the player to ENGINEER outcomes.

**Season 2+:** Complex scenes with UNPREDICTABLE cast. Burn book intel is decaying. Cast members have learned the show's patterns. The player must adapt. Teaching STRATEGIC FLEXIBILITY.

**Expert Play (Season 5+):** Scenes where cast members are PERFORMING for the cameras (high self-awareness). The player must either break through the performance OR incorporate the meta-performance into the edit as a storyline. Teaching META-COMMENTARY.

---

## 4. THE EDIT BAY -- LEVEL DESIGN

### 4.1 Level Purpose Statement

**Purpose:** To make the player an AUTHOR. The edit bay is where events become narrative, where people become characters, where raw footage becomes television. This is the most important room in the game. If the edit bay fails, the game fails.

**Emotional Beat:** AUTHORIAL POWER. The player sits in a dark room with a timeline and decides what is real. Not what happened. What is REAL.

### 4.2 Flow Diagram (Timeline Interface)

```
EDIT BAY -- TIMELINE VIEW (Player POV, seated at desk)
===========================================================

[FOOTAGE STOCKPILE] (left sidebar, scrollable)
+----------------------+
| Moment 1: Jade Cries |  Drama: 82  Auth: 75  Legal: 30
| Moment 2: Marcus     |  Drama: 65  Auth: 90  Legal: 15
| Moment 3: Hot Tub    |  Drama: 55  Auth: 80  Legal: 45
| Moment 4: Derek Conf.|  Drama: 70  Auth: 95  Legal: 10
| ... (20-40 moments)  |
+----------------------+

[EPISODE TIMELINE] (center, horizontal)
+------------------------------------------------------------------+
| SEG 1  | SEG 2  | SEG 3  | SEG 4  | SEG 5  | SEG 6  | (SEG 7-8) |
|________|________|________|________|________|________|____________|
|  DRAG  |  DRAG  |  DRAG  |  DRAG  |  DRAG  |  DRAG  |   DRAG     |
| MOMENT | MOMENT | MOMENT | MOMENT | MOMENT | MOMENT |   MOMENT   |
|  HERE  |  HERE  |  HERE  |  HERE  |  HERE  |  HERE  |   HERE     |
+------------------------------------------------------------------+

[SEGMENT DETAIL PANEL] (right sidebar, shows selected segment)
+---------------------------+
| Segment 3 (selected)      |
|---------------------------|
| Primary Moment: [Moment X]|
| Confessional: [Optional]  | <-- overlay selector
| Music Cue: [Dropdown]     | <-- mood selector
| Chyron: [Text Input]      | <-- player writes text
|---------------------------|
| Projected Impact:         |
|  Drama Value: +68         |
|  Coherence: High          |
|  Legal Risk: Medium       |
+---------------------------+

[EPISODE QUALITY SCORE] (bottom center, updates in real-time)
+------------------------------------------------------------+
| CURRENT RATING: "A Solid Episode" (Drama: 315, Coh: 68)   |
| PROJECTED AUDIENCE: 2.2 Nielsen, Romantics +12%, Drama -5%|
+------------------------------------------------------------+

[SUBMIT EPISODE] (bottom right, final action button)
```

**Critical Path:**
1. Player enters edit bay with 20-40 MOMENTS in footage stockpile (generated from 4-8 scenes shot this episode).
2. Player DRAGS moments into 6-8 SEGMENT SLOTS on timeline.
3. For each segment, player OPTIONALLY adds: confessional overlay, music cue, chyron text.
4. Episode Quality Score updates in REAL-TIME as player arranges segments.
5. Player iterates (swap moments, adjust music, reorder segments) until satisfied.
6. Player hits SUBMIT EPISODE.
7. Transition to broadcast phase (office, ratings report).

**Loop Time:** 8-12 minutes per episode edit (compressed sessions) to 15-20 minutes (perfectionists).

### 4.3 Sightlines and Information Flow

Where does the player LOOK during editing?

**Primary Sightline:** TIMELINE (center screen, horizontal). This is where the WORK happens. The player's eye is drawn here because this is where decisions LAND.

**Secondary Sightline:** FOOTAGE STOCKPILE (left sidebar). The player scans this looking for the BEST moments. The moments are SORTED by default (Drama Value descending) but player can re-sort by Authenticity, Legal Risk, Cast Damage, or Narrative Utility. Expert players learn which sort order to use for which episode tone.

**Tertiary Sightline:** SEGMENT DETAIL PANEL (right sidebar). The player only focuses here when FINE-TUNING a specific segment (adding overlays, writing chyrons). This is PRECISION work, not ASSEMBLY work.

**Peripheral Sightline:** EPISODE QUALITY SCORE (bottom). The player GLANCES here to confirm their instincts. It is feedback, not guidance. If the player is constantly staring at the score and optimizing it numerically, the edit bay has become a spreadsheet. The goal is for the score to AFFIRM choices the player makes for narrative reasons, not dictate them.

**Teaching Moment:** The first edit (Season 1, Episode 1) has a SUGGESTED EDIT that auto-populates the timeline with a "safe" episode structure. The player can ACCEPT (fast, teaches nothing) or CLEAR and build from scratch (slow, teaches everything). The game REWARDS the latter with a post-edit note: "You took the time. That matters."

### 4.4 Pacing Curve (Episode Editing)

```
Engagement
    ^
    |
    |  *                              *  <-- "Aha!" moments
    | * *          *                 * *     (finding the perfect
    |*   *        * *       *       *   *     cut, a surprising
    |     *      *   *     * *     *     *    juxtaposition)
    |      *    *     *   *   *   *       *
    |       *  *       * *     * *         *
    |        **         *       *           *
    +----------------------------------------------> Time
    0min    2-3    5-6    8-9    11-12      15min

    [ROUGH] [ASSEMBLY] [REFINEMENT] [POLISH] [SUBMIT]
```

**Pacing Rule:** The edit bay has THREE PHASES that the player moves through naturally:

1. **ROUGH ASSEMBLY (0-4 min):** Player drags high-value moments into timeline slots. Fast decisions. Instinctive. "This goes here. This goes here."

2. **REFINEMENT (4-10 min):** Player swaps moments, tests different orders, adds music cues. The episode SHAPE emerges. Narrative coherence becomes visible.

3. **POLISH (10-15 min):** Player fine-tunes. Adjusts confessional overlays. Writes chyrons. Tests edge cases ("What if I move Segment 3 to Segment 5?"). Perfectionists live here.

**Difficulty Consideration:** Beginners OVER-POLISH. They spend 20 minutes optimizing a single episode, chasing a perfect score. The game needs to teach that GOOD ENOUGH IS GOOD ENOUGH because there is always another episode. The difficulty is not "make the perfect edit." The difficulty is "make a good-enough edit under time pressure with imperfect footage, repeatedly, across an entire season without burning out."

**Breadcrumbing:** The Episode Quality Score has QUALITATIVE TIERS ("Forgettable Filler", "A Solid Episode", "Gripping Television") not NUMERICAL SCORES (68/100). This discourages min-maxing and encourages TONE-CHASING. The player aims for "Gripping Television," not 85+.

### 4.5 Encounter Breakdown: Editorial Dilemmas

The edit bay's "encounters" are not combat or puzzles. They are DILEMMAS -- moments where the player must choose between competing goals and no choice is clean.

#### 4.5.1 THE EXPLOITATION DILEMMA

**Setup:** The footage stockpile contains a moment with HIGH DRAMA VALUE (85+) and HIGH CAST DAMAGE (80+). Airing it will boost ratings significantly but will devastate the cast member psychologically.

**Player Choice:**
- **Air It:** Ratings spike. Audience engagement increases. Cast member's stress jumps 15-20 points. Editorial betrayal increases. Future cooperation decreases. Long-term reputation risk.
- **Cut It:** Ratings plateau. Audience engagement neutral. Cast member's stress stable. Trust maintained. Moment remains in stockpile for later use OR can be permanently withheld (trust bonus).

**Teaching Moment:** The game does NOT tell the player which choice is correct. It shows OUTCOMES. Some players air everything, chasing ratings. Some players withhold strategically. Some players withhold because they cannot bring themselves to air it. All three strategies are viable. All three tell a story about the player.

#### 4.5.2 THE JUXTAPOSITION DILEMMA

**Setup:** Two moments in the stockpile can be JUXTAPOSED for massive narrative impact. Example: Segment 3 = Jade saying "I'm totally fine" in a calm confessional. Segment 4 = Jade crying alone in the bedroom (different day, different context). Juxtaposing them makes Jade look like a liar OR makes her look like she is hiding pain. The player chooses the meaning.

**Player Choice:**
- **Juxtapose:** Creates powerful TV. High coherence. High drama. High editorial betrayal (you are recontextualizing her words). Audience engagement up. Jade's trust in you down.
- **Separate:** Safer. Lower impact. Jade's words stand on their own. Her crying stands on its own. No recontextualization. Lower drama but higher authenticity score.

**Teaching Moment:** This teaches EDITORIAL POWER. The same footage, arranged differently, tells different stories. The player is not observing. The player is CREATING. The dilemma is: what story will you create with someone else's life?

#### 4.5.3 THE COHERENCE VS. DRAMA DILEMMA

**Setup:** The highest-drama moments in the footage stockpile do not connect to each other narratively. Airing them produces a HIGH DRAMA, LOW COHERENCE episode -- exciting but incoherent. The player must choose: chase drama or chase story.

**Player Choice:**
- **Chase Drama:** Air all the high-value moments. Episode is exciting, fragmented, exhausting. Audience segment "Drama Addicts" +20%. Segment "Romantics" -15% (they need story, not chaos). Short-term ratings spike, long-term fatigue.
- **Chase Coherence:** Build a clear narrative arc across the episode. Lower drama per moment, but the WHOLE is greater than the sum. Audience segment "Strategists" +15%. Critics respond positively. Long-term reputation boost.

**Teaching Moment:** This teaches EDITORIAL DISCIPLINE. More is not always more. The player learns that a well-told story with MODERATE drama beats a chaotic mess with HIGH drama. This is the edit bay teaching CRAFT.

### 4.6 Difficulty Considerations

**Edit Bay Complexity Progression:**

**Season 1, Episodes 1-3:** Small footage stockpile (15-20 moments). Clear standout moments. Simple assemblies. Teaching the player to DRAG and DROP without overwhelming them.

**Season 1, Episodes 4-8:** Larger stockpile (25-35 moments). Competing narrative threads. The player must CHOOSE which storylines to prioritize. Teaching PRIORITIZATION.

**Season 2+:** 30-40 moments per episode. Multiple overlapping arcs. Decaying relationships between cast members create continuity demands ("If I aired X in episode 3, I must address X in episode 5 or the audience will notice the gap"). Teaching NARRATIVE CONTINUITY.

**Expert Play (Season 5+):** 40+ moments. Legacy footage available (flashbacks from previous episodes/seasons). The player can CREATE MONTAGES that span multiple episodes. Meta-commentary cast members produce footage that references the edit itself. Teaching META-NARRATIVE CONSTRUCTION.

---

## 5. THE SHOWRUNNER'S OFFICE -- LEVEL DESIGN

### 5.1 Level Purpose Statement

**Purpose:** The office is the STRATEGIC HUB and the CONSEQUENCE RECEPTOR. This is where the player plans (pre-episode) and processes fallout (post-episode). It is also the most PERSONAL space -- the room that accumulates the player's history.

**Emotional Beat:** REFLECTION. After the chaos of the control room and the focus of the edit bay, the office is QUIET. It is where the player sits with what they have done.

### 5.2 Flow Diagram (Desk View)

```
SHOWRUNNER'S OFFICE -- PLAYER POV (seated at desk)
====================================================

                      [CORKBOARD -- Behind Desk]
              +-----------------------------------+
              | Cast Photos, Red String, Post-Its |
              | (accumulates across seasons)      |
              +-----------------------------------+

[PHONE]               [DESK SURFACE]              [FILING CABINET]
(left)                (center, interact)          (right)
+----------+          +-----------------+          +-----------+
| Blinking |          | Nielsen Report  |          | Archive   |
| Light:   |          | Network Memo    |          | (Season 3+|
| RED/GREEN|          | Legal Notice    |          | unlocks)  |
+----------+          | Tabloid Clip    |          +-----------+
                      +-----------------+

[WINDOW -- But It's Covered]
(behind player, implied but never seen -- the office is WINDOWLESS)
```

**Critical Path (Post-Episode):**
1. Player enters office after episode BROADCAST.
2. Nielsen Report appears on desk (auto-delivered).
3. Player READS report (ratings, audience segments, network satisfaction).
4. Fallout events DELIVER (if any): legal notice slides onto desk, tabloid headline pops on monitor, phone rings (network call).
5. Player PROCESSES consequences (read documents, answer phone, update burn book if new intel surfaces).
6. Player PLANS next episode (optional: review corkboard, check cast stress levels, strategize).

**Loop Time:** 2-5 minutes per office visit (post-episode processing).

### 5.3 Sightlines and Environmental Storytelling

**Primary Sightline:** DESK SURFACE (center). This is where DOCUMENTS appear. The player's eye goes here first because this is where CONSEQUENCES land.

**Secondary Sightline:** CORKBOARD (behind desk, slight upward angle). When the player wants to THINK STRATEGICALLY, they look at the corkboard. It shows the whole cast, the relationships, the arcs. It is the OVERVIEW.

**Tertiary Sightline:** PHONE (left). When it blinks RED, the player MUST look. Red = network call = urgent.

**Environmental Storytelling Detail:** The office has a COUCH (right side, partially visible). Early seasons, the couch is CLEAN. By Season 3, there is a BLANKET on it (you have been sleeping here). By Season 5, there is a PILLOW and an empty coffee cup on the floor next to it (you are LIVING here). The office becomes a prison disguised as an achievement.

**Teaching Moment:** The corkboard teaches RELATIONSHIP MAPPING without a tutorial. The player pins photos, draws red string between allies, circles enemies, adds Post-its with notes. This is MANUAL, not automated. The act of BUILDING the map teaches the player to THINK in terms of relationships, not individuals.

### 5.4 Pacing Curve (Office Phase)

```
Tension
    ^
    |   *  <-- Phone rings (network call = spike)
    |  * *
    | *   *
    |*     *___       <-- Reading reports (plateaus, info absorption)
    |           *
    |            *___ <-- Planning next episode (calm, strategic)
    |
    +-----------------------------------------------------> Time
    0s   30s    90s         3min            5min

    [ENTER] [CRISIS?] [PROCESS] [STRATEGIZE] [EXIT]
```

**Pacing Rule:** The office is the game's BREATH. After the intensity of scene shooting and editing, the office is where the pace SLOWS. This is intentional. The player needs a moment to absorb what just happened before diving into the next episode.

**Difficulty Consideration:** Early seasons, the office phase is CALM (reports are positive, no crises). Late seasons, the office phase is STRESSFUL (multiple crises per episode, phone always ringing, documents piling up). The room itself becomes a difficulty modifier -- not through mechanics, but through DENSITY OF CONSEQUENCE.

---

## 6. PACING ACROSS THE FULL PRODUCTION CYCLE

### 6.1 Episode Cycle Pacing Curve (30-Minute Loop)

```
Intensity
    ^
    |                              **
    |                            **  **  <-- EDIT BAY (high focus, creative)
    |                          **      **
    |          *****          *          *
    |        **     **      **            **
    |      **         **  **                **
    |    **             **                    **___  <-- OFFICE (calm, reflection)
    |  **
    | *
    +--------------------------------------------------------> Time
    0   2    5     8   10   13    18    22  25   28   32min

    |OFFICE| CONTROL | CONTROL | CONTROL | EDIT BAY  |OFFICE|
    |PLAN | SCENE 1 | SCENE 2 | SCENE 3 | (ASSEMBLY)| BROAD|
          | (shoot) | (shoot) | (shoot) | (polish)  | CAST |
```

**Teaching Moment:** The cycle has a RHYTHM. Plan (calm) --> Shoot (intense, short bursts) --> Edit (focused, extended) --> Broadcast (calm, absorption). By episode 3, the player FEELS this rhythm. They know when to push (shooting) and when to breathe (office).

**Difficulty Scaling:** Early episodes have 3-4 scenes per episode (shorter shooting phase). Late episodes have 6-8 scenes (longer shooting phase, more footage, more complex edits). The rhythm stretches but does not break.

### 6.2 Season Arc Pacing Curve (4-6 Hour Loop)

```
Engagement
    ^
    |                                                     ****  <-- FINALE
    |                                                  ***    ***   (peak)
    |                               ****           ***          **
    |                            ***    ***     ***              **
    |           ****          ***          ****                   **
    |        ***    ***    ***                                      *
    |    ***          ****                                           *
    | ***                                                              *
    |*                                                                  *
    +---------------------------------------------------------------------> Time
    Ep1  Ep2  Ep3  Ep4  Ep5  Ep6  Ep7  Ep8  Ep9  Ep10  Ep11  Ep12  END

    [TUTORIAL] [LEARNING] [MID-SEASON] [ESCALATION] [CLIMAX] [AFTERMATH]
```

**Pacing Rule:** The season is structured like a television season (because it IS a television season). Early episodes are setup. Mid-season is complication. Late season is escalation. Finale is climax. This is not arbitrary -- it TEACHES the player how television narrative works by making them BUILD one.

**Mid-Season Twist:** At episode 5-6, the game introduces a SYSTEMIC CRISIS (network demands format change, cast member threatens to walk, scandal breaks). This SPIKE in difficulty prevents mid-season drag and forces the player to ADAPT.

**Finale Episode Design:** The finale has 2x the normal segment count (12-16 segments instead of 6-8) and generates 3x the normal ratings impact. It is LONGER and MORE IMPORTANT. The player FEELS the weight. This is the episode that determines renewal.

---

## 7. BREADCRUMBING STRATEGY

### 7.1 Visual Breadcrumbing (Light and Color)

The game uses LIGHT as the primary breadcrumbing language:

**GREEN LIGHT = Go. Ready. Action Required.**
- Control room door when scenes are ready to shoot.
- Edit bay "SUBMIT EPISODE" button when episode is complete.

**RED LIGHT = Alert. Crisis. Urgent.**
- Office phone when network is calling.
- Edit bay door when footage is waiting and time is passing.
- Burn book entries when cast member stress exceeds 70%.

**YELLOW LIGHT = Caution. Optional. Opportunity.**
- Casting room door during casting phase.
- Mid-scene intervention button (optional but risky).

**BLINKING LIGHT = Escalation.**
- Any light that blinks is MORE URGENT than a steady light. Blinking RED = emergency. Blinking GREEN = time-sensitive opportunity.

**Teaching Moment:** By Season 1 Episode 2, the player stops reading UI TEXT and starts reading LIGHT. This is faster, more intuitive, and more immersive. The player navigates the production suite like a professional who has worked there for years.

### 7.2 Audio Breadcrumbing

**Ambient Sound as Status Indicator:**
- **Control Room:** Humming monitors + occasional beeps = normal. ALARM SOUND = cast member stress critical.
- **Edit Bay:** Quiet hum + keyboard clicks = normal. PHONE RING from office (audible through walls) = network calling, interrupting your edit.
- **Office:** Silence = calm. PAPER SLIDING (sound effect) = document just arrived on desk.

**Teaching Moment:** Audio breadcrumbing is SUBTLE. The player does not consciously notice it for the first hour. But by hour 5, they FEEL when something is wrong before they SEE it. The alarm sound in the control room makes them CHECK the tension meters. The phone ring makes them RUSH to finish the edit. Audio is training instincts.

### 7.3 UI Breadcrumbing (Progressive Disclosure)

**Season 1, Episode 1:** FULL TOOLTIPS. Every button, every meter, every stat has a hover-tooltip explaining what it means.

**Season 1, Episode 2:** REDUCED TOOLTIPS. Only advanced features have tooltips. Basic functions are assumed learned.

**Season 1, Episode 4:** NO TOOLTIPS. The player is fluent. The UI is clean. Information is communicated through ICONS, COLOR, and LAYOUT, not TEXT.

**Teaching Moment:** The UI TEACHES by FADING. As the player learns, the scaffolding disappears. By mid-season, the interface feels PROFESSIONAL -- the tools of someone who does this work every day. The player is not playing a game. The player is PRODUCING TELEVISION.

---

## 8. DIFFICULTY CONSIDERATIONS

### 8.1 Difficulty Curve (Across Seasons)

```
Difficulty
    ^
    |                                                         ___/
    |                                                    ___/
    |                                               ___/     (Expert:
    |                                          _/ __|         Legacy weight,
    |                                     ___/                meta-cast)
    |                                _/ __|
    |                           ___/        (Mid: Complex arcs,
    |                      _/ __|            decaying intel)
    |                 ___/
    |            __/ |            (Early: System learning)
    |       ___/
    |  __/ |                     (Tutorial: Forgiving)
    | /
    +---------------------------------------------------------> Time
    S1    S2    S3    S4    S5    S6    S7    S8+
```

**Difficulty Scaling Mechanisms:**

**Season 1:** Tutorial constraints (smaller cast, simpler scenes, forgiving network). Teaching the SYSTEMS.

**Season 2:** Training wheels off. Full cast, full systems. Teaching COMPETENCE.

**Season 3-4:** Complexity increase (more cast, decaying intel, audience expectations). Teaching ADAPTATION.

**Season 5+:** Expert challenges (meta-aware cast, rival showrunner, legacy consequences). Teaching MASTERY.

**Difficulty Variants (Player-Selected):**

The game offers four NETWORK SETTINGS (not difficulty levels, but constraint profiles):

**Basic Cable (Easy):** Generous budget, patient network, resilient cast, forgiving audience. For players who want to explore systems without pressure.

**Network Television (Normal):** Standard balance. Intended experience.

**Premium Cable (Hard):** Tight budget, demanding network, fragile cast, fickle audience. For strategy-focused players.

**Reality TV Hell (Expert, Unlocked After One Career):** All constraints maximized. Pure optimization challenge.

### 8.2 Spatial Difficulty (Interface Complexity)

**Early Game:** CLEAN INTERFACES. Few buttons. Clear hierarchy. Lots of whitespace (metaphorically -- the aesthetic is 2005 production suite, but the information density is LOW).

**Mid Game:** MODERATE COMPLEXITY. More UI elements. More data. But the player has learned the LANGUAGE of the interfaces, so complexity does not equal confusion.

**Late Game:** DENSE INTERFACES. Lots of data. Multiple simultaneous concerns. But expert players SCAN efficiently. They know where to look. Density becomes RICHNESS, not noise.

**Teaching Moment:** The game teaches INFORMATION TRIAGE. Not all data is equally important. The edit bay has 40 moments in the stockpile, but only 8 segments in the timeline. The player learns to SCAN (find high-value moments quickly) and DISCARD (ignore low-value moments without guilt). This is a spatial skill -- knowing where to look, what to ignore.

---

## 9. PLAYTESTING METRICS (What to Measure)

### 9.1 Control Room Metrics

**Primary Metric: Scene Observation Pattern**
- Track player's CAMERA SWITCHING behavior during scenes.
- Are they switching between feeds (engaged) or staring at one feed (passive)?
- Do they check Camera 4 (alt angle) or ignore it (missing information)?

**Success Criteria:** 80%+ of players switch cameras at least 3 times per scene by Episode 3.

**Kill Condition:** If 40%+ of players never switch cameras, the multi-monitor layout is not communicating its value. Simplify to ONE MAIN FEED with PICTURE-IN-PICTURE for alternates.

### 9.2 Edit Bay Metrics

**Primary Metric: Time to First Submit**
- How long does the player spend on their first episode edit?
- Beginners: 15-25 minutes (learning).
- Competent: 10-15 minutes (efficient).
- Experts: 8-12 minutes (mastery).

**Secondary Metric: Iteration Count**
- How many times does the player REARRANGE segments before submitting?
- Low iteration (0-2 swaps) = either mastery OR disengagement.
- Moderate iteration (3-6 swaps) = engaged refinement. TARGET ZONE.
- High iteration (7+ swaps) = perfectionism paralysis OR unclear feedback.

**Success Criteria:** 70%+ of players iterate 3-6 times per episode edit.

**Kill Condition:** If 50%+ of players submit first draft without iteration, the edit bay is not communicating that CHOICE MATTERS. Increase visual feedback on segment changes.

### 9.3 Office Metrics

**Primary Metric: Corkboard Interaction Rate**
- Do players USE the corkboard (add photos, draw string, write notes) or IGNORE it?
- Target: 60%+ of players interact with corkboard at least once per season.

**Kill Condition:** If 70%+ of players never interact with corkboard, it is ORNAMENTAL not FUNCTIONAL. Either make it mandatory (tutorial) or cut it.

### 9.4 Flow Metrics (Across Full Cycle)

**Primary Metric: Phase Transition Time**
- How long does the player spend in each phase (Office --> Control Room --> Edit Bay --> Office)?
- Are they RUSHING through office (bad -- missing consequences) or DWELLING in edit bay (bad -- perfectionism paralysis)?

**Target Balance (per 30-min episode cycle):**
- Office (Planning): 10-15% (3-5 min)
- Control Room (Shooting): 25-35% (8-11 min)
- Edit Bay (Editing): 40-50% (12-15 min)
- Office (Processing): 10-15% (3-5 min)

**Kill Condition:** If any phase exceeds 50% of total time, that phase is a BOTTLENECK. Compress.

### 9.5 Emotional Metrics (Qualitative)

**Post-Session Survey Questions:**

1. "Was there a moment where you hesitated before making a decision? Describe it." (Tracking moral engagement)
2. "Did you feel like you were CREATING a story or ASSEMBLING content?" (Tracking authorial engagement)
3. "Did you care about any cast members? Which ones and why?" (Tracking emotional attachment)
4. "At any point did you feel uncomfortable with what you were doing? When?" (Tracking complicity awareness)

**Success Criteria:** 50%+ of players report hesitation at least once per season. 70%+ of players describe at least one cast member they "cared about." 40%+ of players report discomfort at least once in the first three seasons.

**Kill Condition:** If 80%+ of players report ZERO emotional engagement ("it's just a game, I didn't feel anything"), the narrative integration has failed. The mechanics are not telling a story. The distance between the player and the consequences is too great.

---

## 10. OPEN QUESTIONS FOR PROTOTYPING

These are spatial and flow questions that playtesting must answer.

**1. Control Room: How Many Cameras?**

The document specifies 4 camera feeds. Is that too many (overwhelming) or too few (limiting)? Playtest with 3, 4, and 5 camera configurations. Measure: are players USING all feeds or IGNORING some?

**2. Edit Bay: Segment Count Sweet Spot?**

The document specifies 6-8 segments per episode. Is that too few (lacks nuance) or too many (tedious)? Playtest with 4, 6, and 8 segment configurations. Measure: time to complete edit, iteration count, player satisfaction.

**3. Office: How Intrusive Should Consequences Be?**

When a legal notice arrives, should it BLOCK the player (modal popup, must read) or WAIT (document on desk, player can read or ignore)? The former ensures engagement, the latter respects player agency. Playtest both. Measure: do players READ consequences or SKIP them?

**4. Production Suite: Physical Transitions or Instant Cuts?**

When the player moves from office to control room, should there be a TRANSITION ANIMATION (door opens, hallway, door closes) or an INSTANT CUT (fade to black, new room)? Transitions add immersion but slow pacing. Instant cuts are efficient but can feel disorienting. Playtest both. Measure: does the transition enhance or interrupt flow?

**5. Burn Book: Dedicated Screen or Overlay?**

The burn book is accessed frequently. Should it be a FULL SCREEN interface (maximizes readability, breaks flow) or an OVERLAY (maintains context, reduces readability)? Playtest both. Measure: how often do players consult burn book, and does interface style affect consultation rate?

**6. Mid-Season Crisis: Scripted or Emergent?**

The mid-season crisis (episode 5-6) can be SCRIPTED (guaranteed, same for all players) or EMERGENT (generated by player's choices and cast state). Scripted ensures pacing. Emergent ensures replayability. Playtest both. Measure: does the crisis feel ORGANIC or FORCED?

**7. Finale Episode: Length Tolerance?**

The finale is 2x longer than normal episodes (20-25 minutes vs. 10-12 minutes for a standard edit). Is that too long? Do players ENJOY the extended finale or ENDURE it? Playtest and measure: player satisfaction with finale vs. standard episodes, completion rate (do players quit mid-finale?).

**8. Season End: Mandatory Reflection or Optional?**

After the finale, should the game FORCE a reflection moment (review season stats, cast outcomes, montage of key moments) or let the player PROCEED directly to next season? Forced reflection creates closure but breaks momentum. Optional allows player-driven pacing but risks players missing the emotional payoff. Playtest both. Measure: do players WATCH the reflection content or SKIP it?

---

## 11. CLOSING NOTES

Here is what I know after designing this document: BURNBOOK is a level design challenge unlike any I have encountered because the LEVELS ARE INTERFACES and the SPACES ARE WORKFLOWS. The player never walks through a door. But they MOVE through the production suite with the same spatial instincts they would use in a 3D level: reading sightlines, following breadcrumbs, learning the flow, internalizing the pacing.

The control room is a combat encounter where the player WATCHES instead of shoots. The edit bay is a puzzle where the player ARRANGES instead of solves. The office is a boss fight where the player PROCESSES instead of dodges. Every room is a verb. Every interface is a lesson.

What concerns me: the edit bay. It is the most important room and the highest-risk mechanic. If the timeline interface feels like VIDEO EDITING SOFTWARE, players will bounce. It must feel like AUTHORSHIP -- powerful, intuitive, immediate. The segment-based structure (6-8 slots, drag-and-drop) is designed to walk this line, but only playtesting will confirm. Protect the edit bay. If it sings, the game sings.

What excites me: the production suite as MEMORY SPACE. The corkboard that accumulates. The desk that clutters. The hallway that fills with ghosts. By Season 5, the player does not just WORK in the suite -- they LIVE in it. They know every room, every sightline, every workflow. The space becomes an extension of the player's mind. That is what great level design does: it makes the space INVISIBLE through mastery and MEANINGFUL through accumulation.

Where does the player LOOK? At the consequences of their choices, rendered as data on screens and documents on desks and photos on walls. What is the critical path? Plan, shoot, cut, air, suffer, repeat. What is the pacing? Breathe, sprint, focus, breathe. What are the breadcrumbs? Light, sound, layout -- the language of spaces that TEACH without TELLING.

Every room teaches something. The casting room teaches reduction. The control room teaches observation. The edit bay teaches authorship. The office teaches consequence. By the end of Season 1, the player has learned to PRODUCE TELEVISION. By the end of Season 5, the player has learned what it COSTS to produce television.

That is the level design working. That is the space doing its job.

Let's build this.

-- GRID

---

**Document Status: Complete**
**Next Step: Prototype the Edit Bay timeline interface. If that works, everything else will follow.**
**Playtesting Priority: Edit Bay > Control Room > Office > Casting Room**

---

*All level design documentation complete. Flow diagrams provided. Pacing curves mapped. Breadcrumbing strategies defined. Difficulty progression scaled. Metrics identified. Ready for spatial prototype phase.*
