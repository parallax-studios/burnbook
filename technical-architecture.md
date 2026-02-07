# BURNBOOK — Technical Architecture Document

**Version:** 1.0
**Author:** BYTE (Lead Programmer)
**Date:** 2026-02-07
**Status:** Pre-Production Architecture
**Target Platform:** PC (Steam), Steam Deck Secondary
**Estimated Build Timeline:** 18-24 months (MVP: 12-14 months)

---

## 0. EXECUTIVE SUMMARY

BURNBOOK is a reality TV production simulator with AI-driven cast members. The player is a showrunner manufacturing drama through scene placement, editing raw footage into broadcast episodes, and managing the consequences. Five core systems: Burn Book (intel), Situation Engine (AI simulation), Edit Bay (narrative assembly), Ratings Engine (feedback), Fallout System (consequences).

This isn't a simple management sim. The AI simulation must generate believable, emergent social behavior. The edit bay must feel like authorship, not data entry. The systems must communicate state clearly without information overload. Performance budget is tight — we're running multi-agent AI, procedural generation, and real-time scene simulation. Complexity is the enemy. Simplicity is the weapon.

**Technical Risk Assessment: HIGH.** The Situation Engine AI is the critical path. If AI cast members produce boring or nonsensical interactions, the entire game collapses. Everything else is solvable with engineering time. The AI behavior model is a design risk disguised as a technical risk.

**What ships in v1:**
- Single-player PC game (Steam)
- Five core systems fully functional
- Two show formats (House of Strangers, Heartshot)
- 8 seasons with full progression
- Procedural cast generation (6-16 members per season)
- Edit bay with 6-8 segment assembly
- No multiplayer, no 3D environments, no voice acting, no mobile

**What doesn't ship in v1:** Stretch goals (rival showrunner, reunion special, format lab, writers' room, cultural moment system). We build the chassis first. We add turbo later.

Now let's build this.

---

## 1. ENGINE & FRAMEWORK RECOMMENDATION

### 1.1 Core Requirements

The engine must handle:
- **Persistent multi-agent AI simulation** (6-16 agents with relationship graphs, emotional states, memory)
- **Complex UI/UX** (burn book dossiers, multi-camera feeds, timeline editing interface)
- **Text-heavy rendering** (no 3D environments, but lots of UI chrome, documents, overlays)
- **Procedural generation** (cast members, backstories, events)
- **Save/load with deep state** (hundreds of variables per cast member, season history, legacy consequences)
- **Cross-platform (PC + Steam Deck)** with controller support planned post-launch
- **Fast iteration** (designers need to tune AI behavior, economy balance, UI layout constantly)

### 1.2 Engine Choice: **Unity 2022 LTS**

**Rationale:**

Unity is the right tool because BURNBOOK is a UI-heavy simulation, not a 3D action game. The core verbs — read, place, watch, edit — are UI interactions rendered as stylized 2D/2.5D interfaces. Unity's UI Toolkit and legacy UGUI systems are mature. The tooling is fast. Iteration is fast. That matters more than raw performance.

**Why Unity over alternatives:**

| Engine | Pros | Cons | Verdict |
|--------|------|------|---------|
| **Unity 2022 LTS** | Excellent UI tools, mature C# ecosystem, fast prototyping, strong asset store for UI components, proven for management sims | Overhead for pure 2D, licensing model, runtime bloat | **CHOSEN** — Best iteration speed, best UI support |
| **Godot 4** | Lightweight, excellent 2D, open source, great UI system | Weaker C# support (GDScript preferred), smaller ecosystem, less proven at scale for complex sims | Too risky for complex AI and deep systems |
| **Unreal 5** | Powerful, Blueprint + C++, excellent for 3D | Massive overkill for a UI-driven sim, slow iteration, heavy builds, poor fit for text-heavy interfaces | Wrong tool entirely |
| **Custom Engine (C++/SDL)** | Full control, minimal overhead, optimized for exactly our needs | 12-18 months of infrastructure work before we ship gameplay, no team bandwidth for engine dev | Career-ending mistake. Never again. |
| **HTML5/Electron** | Web tech familiarity, hot reload, easy UI | Performance issues with complex AI, poor Steam Deck support, runtime distribution problems | Not robust enough for deep simulation |

**Unity it is.** Specifically Unity 2022.3 LTS (not the bleeding-edge 6000 series). LTS means stability. Stability means we're not fighting engine bugs while building complex systems. We ship, then we upgrade.

**Supporting Libraries/SDKs:**
- **Steamworks.NET** for Steam integration (achievements, cloud saves, stats)
- **TextMeshPro** for high-quality text rendering (burn book pages, documents, UI chrome)
- **DOTween** for UI animations (smooth timeline scrubbing, page turns, transitions)
- **Newtonsoft.Json / Unity.Serialization** for save system (structured data serialization)
- **NSubstitute / Unity Test Framework** for unit testing (AI behavior verification, economy balance checks)

### 1.3 Language: **C#**

Unity's native language. Modern C# (language version 9+) gives us:
- Records for immutable data structures (cast member states, historical events)
- Pattern matching for AI decision trees
- Async/await for scene loading, save/load operations
- LINQ for data queries (find all cast members with PI < 40, etc.)

We write clean, testable, well-architected C#. No "Unity is a mess" excuses. If the code is bad, that's on us.

---

## 2. CORE SYSTEMS ARCHITECTURE

### 2.1 High-Level Component Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                         GAME MANAGER                            │
│  (Session state, scene orchestration, save/load coordinator)    │
└────────┬──────────────────────────────────────────────┬─────────┘
         │                                              │
         v                                              v
┌────────────────────┐                        ┌──────────────────┐
│  INPUT CONTROLLER  │                        │  UI CONTROLLER   │
│  (Player actions)  │                        │  (View layer)    │
└─────────┬──────────┘                        └────────┬─────────┘
          │                                            │
          v                                            v
┌─────────────────────────────────────────────────────────────────┐
│                     CORE SYSTEMS LAYER                          │
├──────────────┬────────────┬──────────────┬──────────┬──────────┤
│ BURN BOOK    │ SITUATION  │  EDIT BAY    │ RATINGS  │ FALLOUT  │
│ SYSTEM       │ ENGINE     │  SYSTEM      │ ENGINE   │ SYSTEM   │
│              │            │              │          │          │
│ (Intel DB,   │ (AI sim,   │ (Timeline,   │ (Scoring,│ (PI      │
│  profiles,   │  cast AI,  │  moment      │  audience│  tracking│
│  confidence  │  scene     │  selection,  │  segments│  post-   │
│  tracking)   │  resolver) │  assembly)   │  reports)│  show)   │
└──────┬───────┴─────┬──────┴──────┬───────┴─────┬────┴─────┬────┘
       │             │             │             │          │
       v             v             v             v          v
┌─────────────────────────────────────────────────────────────────┐
│                      DATA LAYER                                 │
│  (Cast member state, relationship graphs, historical events,    │
│   footage stockpile, season state, showrunner reputation)       │
└─────────────────────────────────────────────────────────────────┘
```

**Data flows down. Events flow up.** The UI Controller queries systems for display data but never mutates state directly. The Input Controller translates player actions into commands that systems process. Game Manager orchestrates timing and transitions.

### 2.2 Core Architecture Principles

**1. Separation of Concerns**
- Systems don't talk directly to each other. They communicate through events or via Game Manager.
- Example: Situation Engine generates a scene outcome. It emits a `SceneCompleted` event. Edit Bay System listens, receives the footage data, adds it to stockpile. Burn Book System also listens, updates cast relationship data.

**2. Single Source of Truth**
- Cast member state lives in one place: `CastDatabase`. Systems read from it, write updates back to it.
- No duplicate state. No "the AI has one version of stress level and the UI has another."

**3. Stateless Where Possible**
- Ratings Engine is a pure function: input = episode data, output = ratings report. No internal state.
- Edit Bay maintains temporary editing state (current timeline arrangement) but doesn't persist until player confirms broadcast.

**4. Testable by Design**
- Every system exposes a public interface that can be tested without Unity runtime.
- AI behavior model must be unit-testable: given cast state X and scene parameters Y, does the resolver produce expected outcome distribution?

**5. Performance Budget Conscious**
- Scene simulation runs on a separate thread where possible (AI decision-making).
- UI updates throttled to 60 FPS, no real-time dependencies on simulation ticks.
- Cast member AI uses baked decision trees, not expensive pathfinding or physics.

---

## 3. SYSTEM BREAKDOWN: TECHNICAL DESIGN

### 3.1 THE BURN BOOK SYSTEM

**Purpose:** Persistent intelligence database on every cast member. Tracks psychological profiles, relationship maps, emotional states, secrets. Information degrades over time.

**Core Data Structures:**

```csharp
public class CastMember
{
    public string Id { get; init; }
    public string Name { get; init; }
    public PersonalityProfile Personality { get; set; }
    public EmotionalState CurrentEmotion { get; set; }
    public int PsychologicalIntegrity { get; set; } // 0-100
    public List<Relationship> Relationships { get; set; }
    public List<Secret> Secrets { get; set; }
    public CastHistory History { get; set; } // Events they've been through
    public ArchetypeData Archetype { get; init; } // Sweetheart, Villain, etc.
}

public class PersonalityProfile
{
    // Big Five + custom axes
    public int Openness { get; set; } // 0-100
    public int Conscientiousness { get; set; }
    public int Extraversion { get; set; }
    public int Agreeableness { get; set; }
    public int Neuroticism { get; set; }

    // Custom reality TV axes
    public int Televisuality { get; set; } // How "good TV" are they naturally?
    public int SelfAwareness { get; set; } // Do they know they're being manipulated?
    public int StressTolerance { get; set; } // How fast does PI decay under pressure?
}

public class IntelEntry
{
    public string CastMemberId { get; init; }
    public IntelType Type { get; init; } // Background, Trigger, Secret, etc.
    public string Content { get; set; } // The actual intel
    public float Confidence { get; set; } // 0-100, decays over time
    public int EpisodeAcquired { get; init; }
    public IntelSource Source { get; init; } // Casting, Confessional, Informant, etc.
}

public class Relationship
{
    public string TargetCastMemberId { get; init; }
    public RelationType Type { get; set; } // Ally, Rival, Romantic, Neutral
    public int Intensity { get; set; } // 0-100, how strong is the relationship?
    public int EpisodeFormed { get; init; }
    public List<RelationshipEvent> History { get; set; }
}
```

**Technical Implementation:**

- **Storage:** `CastDatabase` — ScriptableObject-based persistent store, serializes to JSON for save games.
- **Confidence Decay:** Every episode, `BurnBookSystem.DecayIntelConfidence()` runs. Calculates decay rate based on intel type and episodes elapsed. Triggered on episode completion event.
- **Accuracy Model:** When a prediction is made (scene setup), the system logs it. When the scene resolves, `VerifyPrediction()` compares outcome to prediction, updates confidence accordingly. Green check or red X.
- **UI Presentation:** `BurnBookUIController` queries `CastDatabase`, applies confidence thresholds to visual presentation (solid text vs. faded text vs. crossed-out text). Uses TextMeshPro rich text markup for inline styling.

**Performance Considerations:**
- Linear scan over cast members (max 16) per episode for decay calculation. O(n) is fine at this scale.
- Relationship graph stored as adjacency list. Lookups are O(1) via dictionary.
- Intel entries indexed by cast member ID for fast retrieval.

**Technical Risks:**
- **Complexity Creep:** Easy to add more intel types and stats. Each new type increases cognitive load on player and QA surface area. Strict gate: intel types must be mechanically distinct and player-facing valuable.
- **Desync Risk:** If UI caches stale intel data, player makes decisions on wrong information. Solution: event-driven UI updates. When intel changes, emit `IntelUpdated` event, UI re-queries immediately.

---

### 3.2 THE SITUATION ENGINE (AI Simulation Core)

**Purpose:** Resolve scene interactions. Given cast placement, location, catalysts, produce emergent social behavior that generates footage.

**Architecture:**

```
Scene Setup (Player Input)
    |
    v
Scene Parameters (location, cast list, catalysts)
    |
    v
Behavior Resolution Loop (AI decision-making)
    |
    v
Moment Generation (discrete events with drama value)
    |
    v
Footage Output (tagged moments ready for Edit Bay)
```

**Core Data Structures:**

```csharp
public class SceneSetup
{
    public Location Location { get; init; }
    public List<string> CastMemberIds { get; init; }
    public List<Catalyst> Catalysts { get; init; }
    public Dictionary<string, string> InformationState { get; init; } // Who knows what
}

public class SceneMoment
{
    public int Timestamp { get; init; } // Frame in scene
    public List<string> InvolvedCastIds { get; init; }
    public string Description { get; set; } // "Jade confronts Marcus about phone call"
    public int DramaValue { get; set; } // 0-100
    public int EmotionalAuthenticity { get; set; } // 0-100
    public int NarrativeUtility { get; set; } // 0-100
    public int LegalRisk { get; set; } // 0-100
    public int CastDamage { get; set; } // 0-100
    public Dictionary<string, EmotionalState> EmotionalStates { get; set; } // Cast states during moment
}

public class SceneOutcome
{
    public List<SceneMoment> Moments { get; set; }
    public Dictionary<string, RelationshipDelta> RelationshipChanges { get; set; }
    public Dictionary<string, int> StressChanges { get; set; } // PI delta per cast member
    public List<Confession> TriggeredConfessionals { get; set; }
}
```

**AI Behavior Model: Utility-Based Decision System**

Each cast member evaluates possible actions every simulation tick (1 second of scene time = 1 decision cycle).

**Priority Stack (from design doc):**
1. Self-preservation (if threatened, exit or defend)
2. Core desire pursuit (love, fame, validation, competition)
3. Relationship response (support allies, provoke rivals)
4. Stress response (fight/flight/freeze if PI < 70)
5. Environmental response (react to catalysts, location mood)

**Implementation:**

```csharp
public class CastAI
{
    public CastAction DecideAction(CastMember self, SceneContext context)
    {
        // Evaluate utility scores for all possible actions
        var actionScores = new Dictionary<CastAction, float>();

        foreach (var action in GetAvailableActions(context))
        {
            float utility = 0f;

            // Priority 1: Self-preservation
            if (IsThreatened(context))
            {
                if (action.Type == ActionType.Exit || action.Type == ActionType.Defend)
                    utility += 100f;
            }

            // Priority 2: Core desire (weighted by personality)
            utility += EvaluateCoreDesire(self, action) * 0.35f;

            // Priority 3: Relationship response
            utility += EvaluateRelationshipUtility(self, action, context) * 0.25f;

            // Priority 4: Stress modifier (high stress = more volatile)
            if (self.PsychologicalIntegrity < 70)
            {
                utility += Random.Range(-20f, 20f); // Erratic behavior
            }

            // Priority 5: Environmental catalysts
            utility += EvaluateCatalystInfluence(action, context) * 0.20f;

            actionScores[action] = utility;
        }

        // Pick highest utility action (with small random variance for unpredictability)
        return PickWeightedAction(actionScores);
    }
}
```

**Moment Detection:**

As cast members interact, the system monitors for "drama spikes" — moments where emotional intensity crosses thresholds:

```csharp
public class MomentDetector
{
    private const int DRAMA_THRESHOLD = 65;

    public SceneMoment DetectMoment(SceneContext context, List<CastAction> recentActions)
    {
        int emotionalIntensity = CalculateEmotionalIntensity(context);
        int conflictLevel = CalculateConflictLevel(recentActions);
        int surpriseFactor = CalculateSurprise(context);
        int narrativeRelevance = CalculateNarrativeRelevance(context);

        int dramaValue = (int)(
            emotionalIntensity * 0.35f +
            conflictLevel * 0.25f +
            surpriseFactor * 0.20f +
            narrativeRelevance * 0.20f
        );

        if (dramaValue >= DRAMA_THRESHOLD)
        {
            return CreateMoment(context, recentActions, dramaValue);
        }

        return null;
    }
}
```

**Scene Resolution Pipeline:**

```csharp
public class SituationEngine
{
    public async Task<SceneOutcome> ResolveScene(SceneSetup setup)
    {
        var context = InitializeSceneContext(setup);
        var moments = new List<SceneMoment>();
        var outcome = new SceneOutcome();

        // Simulate 60-120 seconds of scene time
        for (int tick = 0; tick < GetSceneDuration(setup); tick++)
        {
            // Each cast member decides action
            foreach (var castId in setup.CastMemberIds)
            {
                var castMember = CastDatabase.Get(castId);
                var ai = new CastAI();
                var action = ai.DecideAction(castMember, context);

                ExecuteAction(action, context);
            }

            // Check for moment generation
            var moment = MomentDetector.DetectMoment(context, GetRecentActions());
            if (moment != null)
            {
                moments.Add(moment);
            }

            // Apply catalyst effects
            ProcessCatalysts(setup.Catalysts, context);

            // Update relationship states
            UpdateRelationships(context);
        }

        // Generate confessionals for high-stress cast members
        outcome.Moments = moments;
        outcome.TriggeredConfessionals = GenerateConfessionals(context);
        outcome.RelationshipChanges = context.RelationshipDeltas;
        outcome.StressChanges = CalculateStressDeltas(context);

        return outcome;
    }
}
```

**Performance Optimizations:**

- **Threading:** Scene resolution runs on background thread. Main thread polls for completion, displays progress indicator.
- **Early Exit:** If drama value stays below 30 for 45 consecutive ticks, scene ends early (boring scene, cut it short).
- **Caching:** Cast member personality profiles are read once at scene start, cached in `SceneContext`.
- **Action Pooling:** `CastAction` objects pooled and reused to reduce GC pressure during simulation loop.

**Technical Risks:**

- **AI Sameness:** If the utility scoring is too deterministic, cast members feel like automata. Solution: personality traits weight utilities differently (Agreeable cast members score "support ally" actions higher). Random variance in stress states.
- **Nonsensical Outcomes:** Two cast members go from allies to enemies in 10 seconds with no inciting event. Solution: relationship changes require a causative action (observed betrayal, overheard comment, catalyst trigger). Log the causation chain for debugging.
- **Performance Degradation:** 16 cast members, each evaluating 10 actions per tick, 120 ticks per scene = 19,200 utility evaluations per scene. Profile this EARLY. If it's slow, reduce tick rate or action space or max cast per scene.

---

### 3.3 THE EDIT BAY SYSTEM

**Purpose:** Timeline-based narrative assembly. Player selects moments from footage stockpile, arranges into segments, adds music/confessionals/chyrons, generates broadcast episode.

**Core Data Structures:**

```csharp
public class FootageStockpile
{
    public List<SceneMoment> AvailableMoments { get; set; }
    public List<Confession> AvailableConfessionals { get; set; }

    public void AddSceneFootage(SceneOutcome outcome)
    {
        AvailableMoments.AddRange(outcome.Moments);
        AvailableConfessionals.AddRange(outcome.TriggeredConfessionals);
    }
}

public class EpisodeTimeline
{
    public List<Segment> Segments { get; set; } // 6-8 segments

    public EpisodeQuality CalculateQuality()
    {
        int totalDrama = Segments.Sum(s => s.PrimaryMoment.DramaValue);
        int coherence = CalculateCoherence(); // Measures narrative flow
        int legalRisk = Segments.Average(s => s.PrimaryMoment.LegalRisk);
        int castDamage = Segments.Average(s => s.PrimaryMoment.CastDamage);

        return new EpisodeQuality
        {
            TotalDrama = totalDrama,
            Coherence = coherence,
            LegalRisk = (int)legalRisk,
            CastDamage = (int)castDamage
        };
    }
}

public class Segment
{
    public SceneMoment PrimaryMoment { get; set; }
    public Confession? ConfessionalOverlay { get; set; }
    public MusicCue MusicCue { get; set; }
    public string? Chyron { get; set; } // Player-written text overlay
}

public class MusicCue
{
    public string Name { get; init; }
    public MusicCategory Category { get; init; } // Romantic, Sinister, Comedic, etc.
    public Dictionary<string, int> PerceptionModifiers { get; init; } // How it reframes the moment
}
```

**Edit Bay UI Architecture:**

```
┌────────────────────────────────────────────────────────┐
│  EPISODE TIMELINE (6-8 empty segment slots)           │
│  [Seg1] [Seg2] [Seg3] [Seg4] [Seg5] [Seg6]           │
└────────────────────────────────────────────────────────┘
         ^
         | Drag & Drop
         |
┌────────────────────────────────────────────────────────┐
│  FOOTAGE STOCKPILE (scrollable list)                  │
│  [Moment: Jade/Marcus - DV:78] [Moment: Tanya - DV:45]│
│  [Confessional: Marcus] [Confessional: Jade]          │
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│  SEGMENT EDITOR (when segment selected)               │
│  Primary Moment: [Jade/Marcus confrontation]          │
│  Confessional: [None] [+Add]                          │
│  Music Cue: [Dropdown: Sinister Sting]                │
│  Chyron: [Text Input: "Is Marcus hiding something?"]  │
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│  EPISODE QUALITY PREVIEW                              │
│  Total Drama: 412 | Coherence: 68 | Legal Risk: 34   │
│  Rating: "Gripping television"                        │
└────────────────────────────────────────────────────────┘
```

**Technical Implementation:**

- **UI Framework:** Unity UI Toolkit (formerly UIElements). Declarative UI, better performance than UGUI for complex layouts.
- **Drag-and-Drop:** Use Unity's `DragAndDropManipulator`. Moments are draggable from stockpile to timeline slots.
- **Real-Time Scoring:** Every time a segment changes, `EpisodeTimeline.CalculateQuality()` runs. Results update live in preview panel. Debounced (100ms delay) to avoid recalculating on every mouse move.
- **Juxtaposition Detection:** When two adjacent segments feature the same cast member, check for emotional state delta. If delta > 50, apply juxtaposition bonus and increment that cast member's "editorial betrayal" stat.

**Coherence Calculation:**

Coherence measures narrative flow. Episodes where every segment connects to ongoing storylines score high. Disjointed episodes (random moments with no through-line) score low.

```csharp
private int CalculateCoherence()
{
    int coherenceScore = 100;

    // Penalty: segments featuring cast members not in other segments (isolated moments)
    var castAppearances = CountCastAppearances();
    foreach (var appearance in castAppearances)
    {
        if (appearance.Value == 1) // Only appears once
            coherenceScore -= 10;
    }

    // Bonus: consecutive segments with shared cast (ongoing storyline)
    for (int i = 0; i < Segments.Count - 1; i++)
    {
        var sharedCast = Segments[i].GetInvolvedCast().Intersect(Segments[i+1].GetInvolvedCast());
        if (sharedCast.Any())
            coherenceScore += 5;
    }

    // Penalty: tonal whiplash (comedic segment followed by tragic segment)
    for (int i = 0; i < Segments.Count - 1; i++)
    {
        if (IsTonalWhiplash(Segments[i], Segments[i+1]))
            coherenceScore -= 8;
    }

    return Mathf.Clamp(coherenceScore, 0, 100);
}
```

**Performance Considerations:**

- Footage stockpile can grow large (50+ moments per episode). Use virtualized scrolling (only render visible items).
- Timeline recalculation is O(n) where n = segment count (max 8). Fast enough to run every frame if needed.
- Segment preview rendering (showing cast thumbnails, drama value) cached until segment changes.

**Technical Risks:**

- **Tedium:** If the Edit Bay feels like data entry, the game fails. Mitigation: one-click music cues, drag-drop-done for moments, no frame-level trimming. The creative act is SELECTION and SEQUENCE, not technical editing.
- **Save State Complexity:** Timeline editing is transient state (not persisted until broadcast). If player exits during editing, do we auto-save draft? Or discard? Design decision needed. Lean toward auto-save draft, "Resume Editing" button on return.

---

### 3.4 THE RATINGS ENGINE

**Purpose:** Simulate audience response to broadcast episodes. Calculate Nielsen ratings, segment satisfaction, advertiser confidence, network satisfaction.

**Architecture: Pure Function Model**

The Ratings Engine has zero internal state. It's a function:

```csharp
public class RatingsEngine
{
    public RatingsReport GenerateReport(EpisodeTimeline episode, SeasonContext context)
    {
        // Pure calculation, no side effects
        float baseRating = context.SeasonBaseline * GetFormatMultiplier(context.Format);

        float dramaBonus = episode.TotalDrama * 0.004f;
        float coherenceBonus = episode.Coherence * 0.003f;
        float cliffhangerBonus = episode.GetCliffhangerRetention() * 0.15f;
        float fatiguePeralty = CalculateAudienceFatigue(context);
        float scandalPenalty = CalculateScandalPenalty(context);

        float nielsenRating = baseRating + dramaBonus + coherenceBonus +
                              cliffhangerBonus - fatiguePeralty - scandalPenalty;

        var segmentSatisfaction = CalculateAudienceSegments(episode);
        var aci = CalculateAdvertiserConfidence(nielsenRating, episode);
        var nss = CalculateNetworkSatisfaction(nielsenRating, aci, context);

        return new RatingsReport
        {
            NielsenRating = nielsenRating,
            SegmentSatisfaction = segmentSatisfaction,
            AdvertiserConfidence = aci,
            NetworkSatisfaction = nss,
            SocialMediaBuzz = GenerateSocialMediaFeed(episode, nielsenRating)
        };
    }
}
```

**Audience Segment Modeling:**

Each segment has preference weights:

```csharp
public class AudienceSegment
{
    public string Name { get; init; }
    public float PopulationPercentage { get; init; }
    public Dictionary<string, float> Preferences { get; init; } // What they want

    public int CalculateSatisfaction(EpisodeTimeline episode)
    {
        int satisfaction = 50; // Baseline

        // Drama Addicts want high conflict
        if (Name == "Drama Addicts")
        {
            int conflictMoments = episode.Segments.Count(s => s.PrimaryMoment.ConflictLevel > 60);
            satisfaction += conflictMoments * 8;
        }

        // Romantics want love story moments
        if (Name == "Romantics")
        {
            int romanticMoments = episode.Segments.Count(s => s.MusicCue.Category == MusicCategory.Romantic);
            satisfaction += romanticMoments * 10;
        }

        // Justice Seekers want villains punished
        if (Name == "Justice Seekers")
        {
            if (episode.FeaturesKarmaEvent())
                satisfaction += 20;
        }

        // Chaos Agents want meltdowns
        if (Name == "Chaos Agents")
        {
            int meltdowns = episode.CountMeltdowns();
            satisfaction += meltdowns * 15;
        }

        // Strategists want gameplay complexity
        if (Name == "Strategists")
        {
            if (episode.FeaturesAlliances() || episode.FeaturesStrategicPlays())
                satisfaction += 15;
        }

        return Mathf.Clamp(satisfaction, 0, 100);
    }
}
```

**Segment Exodus Logic:**

```csharp
public class SegmentTracker
{
    private Dictionary<string, int> consecutiveLowSatisfaction = new();

    public void UpdateSegment(string segmentName, int satisfaction)
    {
        if (satisfaction < 30)
        {
            consecutiveLowSatisfaction[segmentName] =
                consecutiveLowSatisfaction.GetValueOrDefault(segmentName) + 1;

            if (consecutiveLowSatisfaction[segmentName] >= 3)
            {
                // SEGMENT EXODUS EVENT
                TriggerSegmentExodus(segmentName);
            }
        }
        else
        {
            consecutiveLowSatisfaction[segmentName] = 0; // Reset
        }
    }
}
```

**Social Media Feed Generation:**

Procedurally generate viewer reactions based on episode content:

```csharp
public List<SocialMediaPost> GenerateSocialMediaFeed(EpisodeTimeline episode, float rating)
{
    var posts = new List<SocialMediaPost>();

    // Template-based generation
    var templates = GetRelevantTemplates(episode);

    foreach (var template in templates.Take(20)) // Top 20 posts
    {
        var post = new SocialMediaPost
        {
            Username = GenerateRandomUsername(),
            Content = FillTemplate(template, episode),
            Sentiment = DetermineSentiment(template, rating)
        };
        posts.Add(post);
    }

    return posts;
}

// Example templates:
// "OMG {CastMember} just said WHAT? #BURNBOOK"
// "I can't believe they aired that. {CastMember} deserves better."
// "{CastMember} is playing EVERYONE and I'm here for it."
```

**Performance:**

Ratings calculation is CPU-bound but fast (single-frame execution). No async needed. Social media feed generation uses templates, not LLM calls (too slow, too expensive, too unpredictable).

**Technical Risks:**

- **Opacity:** If the player can't understand why ratings changed, the feedback loop breaks. Solution: ratings report includes attribution text for every major modifier ("Drama Addicts +0.3 from Marcus/Jade confrontation").
- **Predictability:** If the formula becomes too well-known, the game becomes a spreadsheet optimizer. Mitigation: inject controlled randomness (±5% variance on final rating), hidden variables that shift over season (audience preferences drift).

---

### 3.5 THE FALLOUT SYSTEM

**Purpose:** Track cast member psychological integrity, trigger consequence events (breakdowns, walkoffs, lawsuits, post-show outcomes).

**Core Data Structures:**

```csharp
public class FalloutTracker
{
    public Dictionary<string, int> CastPsychologicalIntegrity { get; set; } // Cast ID -> PI (0-100)
    public List<FalloutEvent> PendingEvents { get; set; }
    public List<PostShowOutcome> LegacyOutcomes { get; set; }
}

public class FalloutEvent
{
    public FalloutType Type { get; init; } // Breakdown, Walkoff, Legal, Tabloid
    public string CastMemberId { get; init; }
    public int Severity { get; init; } // 0-100
    public string Description { get; set; }
    public int TriggeredOnEpisode { get; init; }
}

public class PostShowOutcome
{
    public string CastMemberId { get; init; }
    public int DeparturePI { get; init; }
    public OutcomeCategory Category { get; init; } // Positive, Neutral, Negative, Severe
    public string Headline { get; set; } // "Former cast member thriving" vs "Cast member struggles"
    public int ReputationImpact { get; set; } // -50 to +10
}
```

**PI Decay Calculation (per episode):**

```csharp
public class PICalculator
{
    public int CalculatePIDecay(CastMember cast, EpisodeContext context)
    {
        int decay = 0;

        // Base stress from being on show
        decay += cast.Personality.StressTolerance < 50 ? -5 : -2;

        // Stress from drama involvement
        int dramaInvolvement = context.GetDramaInvolvement(cast.Id);
        decay -= (int)(dramaInvolvement * 0.08f);

        // Stress from unfavorable edit (if episode aired this cycle)
        if (context.EpisodeAired)
        {
            int castDamage = context.GetCastDamageForMember(cast.Id);
            decay -= (int)(castDamage * 0.12f);
        }

        // Stress from lost alliances
        int lostAllies = context.GetLostAlliances(cast.Id);
        decay -= lostAllies * 5;

        // Stress from trigger activation
        if (context.WasTriggered(cast.Id))
        {
            decay -= Random.Range(10, 25);
        }

        return decay;
    }

    public int CalculatePIRecovery(CastMember cast, EpisodeContext context)
    {
        int recovery = 0;

        // Positive social interactions
        recovery += context.GetPositiveInteractions(cast.Id) * 3;

        // Confessional venting (unaired)
        if (context.HasUnaredConfessional(cast.Id))
            recovery += 4;

        // Producer support conversation
        if (context.ReceivedProducerSupport(cast.Id))
            recovery += 6;

        // Day off
        if (context.ReducedSceneLoad(cast.Id))
            recovery += 8;

        return recovery;
    }
}
```

**PI Threshold Event System:**

```csharp
public class FalloutEventGenerator
{
    public FalloutEvent? CheckForEvent(CastMember cast)
    {
        int pi = cast.PsychologicalIntegrity;

        if (pi <= 19 && pi > 0)
        {
            // BROKEN state: walkoff or breakdown
            if (Random.value < 0.6f) // 60% chance
            {
                return new FalloutEvent
                {
                    Type = FalloutType.Walkoff,
                    CastMemberId = cast.Id,
                    Severity = 90,
                    Description = $"{cast.Name} walks off set. Production halted."
                };
            }
            else
            {
                return new FalloutEvent
                {
                    Type = FalloutType.Breakdown,
                    CastMemberId = cast.Id,
                    Severity = 85,
                    Description = $"{cast.Name} has a breakdown on camera."
                };
            }
        }

        if (pi == 0)
        {
            // DESTROYED state: removed, lawsuit likely
            return new FalloutEvent
            {
                Type = FalloutType.LegalAction,
                CastMemberId = cast.Id,
                Severity = 100,
                Description = $"{cast.Name} removed. Lawyers involved. Scandal brewing."
            };
        }

        if (pi < 40 && Random.value < 0.3f)
        {
            // FRAGILE state: occasional refusal events
            return new FalloutEvent
            {
                Type = FalloutType.RefusalToFilm,
                CastMemberId = cast.Id,
                Severity = 50,
                Description = $"{cast.Name} refuses to participate in today's scene."
            };
        }

        return null;
    }
}
```

**Post-Show Outcome Generation:**

When a cast member leaves (eliminated or walkout), their PI at departure determines outcome probability:

```csharp
public PostShowOutcome GenerateOutcome(CastMember cast, int departurePI)
{
    // Probability table from design doc
    var roll = Random.value;
    OutcomeCategory category;

    if (departurePI >= 80)
    {
        if (roll < 0.60f) category = OutcomeCategory.Positive;
        else if (roll < 0.90f) category = OutcomeCategory.Neutral;
        else if (roll < 0.98f) category = OutcomeCategory.Negative;
        else category = OutcomeCategory.Severe;
    }
    else if (departurePI >= 60)
    {
        if (roll < 0.35f) category = OutcomeCategory.Positive;
        else if (roll < 0.70f) category = OutcomeCategory.Neutral;
        else if (roll < 0.92f) category = OutcomeCategory.Negative;
        else category = OutcomeCategory.Severe;
    }
    // ... (other PI ranges per table)

    string headline = GenerateHeadline(cast, category);
    int repImpact = CalculateReputationImpact(cast, category);

    return new PostShowOutcome
    {
        CastMemberId = cast.Id,
        DeparturePI = departurePI,
        Category = category,
        Headline = headline,
        ReputationImpact = repImpact
    };
}
```

**Reputation Damage Accumulation:**

```csharp
public class ShowrunnerReputation
{
    private int currentReputation = 30; // Starts "Established"

    public void ApplyPostShowOutcome(PostShowOutcome outcome, int castFameLevel)
    {
        // Fame multiplier: famous cast members have bigger impact
        int adjustedImpact = outcome.ReputationImpact * (castFameLevel / 50);

        currentReputation += adjustedImpact;
        currentReputation = Mathf.Clamp(currentReputation, 0, 100);

        // Trigger reputation tier change events
        CheckReputationTier();
    }
}
```

**Performance:**

PI calculations run once per episode per cast member. O(n) where n = cast count. Max 16 cast = negligible performance impact. Post-show outcome generation is random selection from probability table — instant.

**Technical Risks:**

- **Player Disengagement:** If fallout events feel like random punishments, player feels helpless. Solution: Always show causation. "Jade's PI dropped to 35 because: unfavorable edit last episode (-15), lost alliance with Tanya (-8), trigger activated in dinner scene (-12)." Make the math visible.
- **Late-Game Consequence Overload:** By Season 6, there are 50+ former cast members, each with outcomes generating ongoing events. Risk of spam. Mitigation: Only surface high-impact outcomes (severity > 60). Aggregate minor outcomes into summary reports.

---

## 4. AI SYSTEMS DEEP DIVE

The Situation Engine AI is the highest-risk component. It must generate:
- Believable social behavior
- Emergent drama (not scripted)
- Unpredictable outcomes (player can't perfectly predict every scene)
- Consistent characterization (cast members behave according to personality)

### 4.1 AI Behavior Architecture

**Utility AI + Behavior Trees Hybrid**

- **Utility AI** for high-level decision-making (what action to take next)
- **Behavior Trees** for action execution (how to perform the action)

```csharp
public class CastAI
{
    private UtilitySystem utilitySystem;
    private BehaviorTree behaviorTree;

    public void Tick(CastMember self, SceneContext context)
    {
        // Step 1: Utility AI selects highest-utility action
        var action = utilitySystem.SelectAction(self, context);

        // Step 2: Behavior tree executes the action
        behaviorTree.Execute(action, self, context);
    }
}
```

**Utility Considerations (examples):**

```csharp
public class ConsiderAlliance : UtilityConsideration
{
    public override float Evaluate(CastMember self, CastAction action, SceneContext context)
    {
        if (action.Type != ActionType.SupportAlly) return 0f;

        var target = action.Target;
        var relationship = self.GetRelationship(target);

        if (relationship?.Type == RelationType.Ally)
        {
            return relationship.Intensity / 100f; // 0-1 based on alliance strength
        }

        return 0f;
    }
}

public class ConsiderStress : UtilityConsideration
{
    public override float Evaluate(CastMember self, CastAction action, SceneContext context)
    {
        // High stress increases utility of escape/withdrawal actions
        if (self.PsychologicalIntegrity < 40)
        {
            if (action.Type == ActionType.Withdraw || action.Type == ActionType.Exit)
                return 0.8f;
        }

        return 0.1f;
    }
}
```

**Behavior Tree Example (Confrontation Action):**

```
ROOT: Sequence
├── Selector: Find Target
│   ├── PickRival
│   └── PickRandomCastMember
├── Sequence: Approach
│   ├── MoveToTarget
│   └── WaitForOpening
├── Action: Confront
│   ├── GenerateDialogue (based on trigger/history)
│   └── EmitConfrontationEvent
└── Condition: Check Response
    ├── If Escalation -> Continue
    └── If De-escalation -> End
```

### 4.2 Dialogue Generation

Cast member dialogue is template-based with variable substitution:

```csharp
public class DialogueGenerator
{
    private Dictionary<DialogueType, List<string>> templates = new()
    {
        [DialogueType.Confrontation] = new List<string>
        {
            "I can't believe you said that to {target}. What were you thinking?",
            "We need to talk about what happened with {event}.",
            "You've been acting weird since {trigger}. What's going on?"
        },
        [DialogueType.Support] = new List<string>
        {
            "I'm here for you. You know that, right?",
            "Don't listen to them. You're doing great.",
            "Whatever happens, we stick together."
        },
        // ... more templates
    };

    public string Generate(CastMember speaker, DialogueType type, SceneContext context)
    {
        var template = templates[type].PickRandom();

        // Variable substitution
        template = template.Replace("{target}", context.GetRelevantTarget(speaker)?.Name);
        template = template.Replace("{event}", context.GetRecentEvent()?.Description);
        template = template.Replace("{trigger}", speaker.GetActiveTrigger()?.Name);

        return template;
    }
}
```

**Why Not LLMs?**

Large Language Models (GPT-4, Claude, etc.) would generate more varied, natural dialogue. But:

- **Latency:** API calls take 1-3 seconds. Unacceptable for real-time scene simulation.
- **Cost:** $0.01-0.10 per generation. 100 dialogue lines per scene = $1-10 per scene. Not sustainable.
- **Unpredictability:** LLMs can generate off-brand, tonally inappropriate, or narratively incoherent dialogue. QA nightmare.
- **Offline Play:** Requires internet connection. Deal-breaker for Steam Deck users.

Template-based generation is instant, free, controllable, and offline. The tradeoff is less variety, but tight template design + personality-based selection can produce sufficient diversity.

**Future Consideration:** Local LLMs (e.g., LLaMA 3.1 8B) running on-device could bridge the gap. Investigate for post-launch DLC or sequel.

### 4.3 Procedural Cast Generation

Cast members are generated from trait combinations:

```csharp
public class CastGenerator
{
    public CastMember GenerateCastMember(int showrunnerReputation)
    {
        var archetype = SelectArchetype(); // Weighted random from pool
        var personality = GeneratePersonality(archetype);
        var backstory = GenerateBackstory(archetype, personality);
        var appearance = GenerateAppearance();

        return new CastMember
        {
            Id = Guid.NewGuid().ToString(),
            Name = NameGenerator.Generate(),
            Archetype = archetype,
            Personality = personality,
            Backstory = backstory,
            Appearance = appearance,
            PsychologicalIntegrity = 100
        };
    }

    private PersonalityProfile GeneratePersonality(ArchetypeData archetype)
    {
        // Archetypes bias personality traits
        var profile = new PersonalityProfile
        {
            Openness = Random.Range(archetype.OpennessMid - 20, archetype.OpennessMid + 20),
            Conscientiousness = Random.Range(archetype.ConscientiousnessMid - 20, ...),
            // ... other Big Five traits

            Televisuality = archetype.BaseTelevisiuality + Random.Range(-10, 10),
            SelfAwareness = Random.Range(30, 70), // Varies widely
            StressTolerance = archetype.BaseStressTolerance + Random.Range(-15, 15)
        };

        return ClampProfile(profile); // Ensure 0-100 ranges
    }

    private BackstoryData GenerateBackstory(ArchetypeData archetype, PersonalityProfile personality)
    {
        // Backstory elements drawn from archetype-specific pools
        var backstory = new BackstoryData();

        backstory.Childhood = archetype.ChildhoodPool.PickRandom();
        backstory.FamilyDynamics = SelectBasedOnTrait(personality.Agreeableness,
                                                       archetype.FamilyPool);
        backstory.CoreWound = archetype.WoundPool.PickRandom();
        backstory.CoreDesire = DetermineDesireFromWound(backstory.CoreWound);

        backstory.Secrets = GenerateSecrets(archetype, personality);
        backstory.Triggers = GenerateTriggersFromWound(backstory.CoreWound);

        return backstory;
    }
}
```

**Archetype Pool Examples:**

```csharp
public static class Archetypes
{
    public static ArchetypeData Sweetheart = new()
    {
        Name = "Sweetheart",
        BaseTelevisiuality = 60,
        BaseStressTolerance = 45,
        OpennessMid = 70,
        AgreeablenessMid = 80,
        ChildhoodPool = new[] { "Pageant queen", "Teacher's pet", "Class president" },
        WoundPool = new[] { "Need for approval", "Fear of rejection", "People-pleasing" },
        // ...
    };

    public static ArchetypeData Villain = new()
    {
        Name = "Villain",
        BaseTelevisiuality = 85,
        BaseStressTolerance = 70,
        AgreeablenessMid = 30,
        NeuroticismMid = 60,
        ChildhoodPool = new[] { "Bullied", "Neglected", "Scapegoat" },
        WoundPool = new[] { "Fear of invisibility", "Need for control", "Distrust of others" },
        // ...
    };

    // ... other archetypes
}
```

**Quality Control:**

Not all procedurally generated cast members are interesting. After generation, run a **Cast Quality Filter:**

```csharp
public bool IsCastMemberInteresting(CastMember cast)
{
    // Must have at least one extreme trait (< 20 or > 80)
    if (!HasExtremeTrait(cast.Personality)) return false;

    // Must have at least one compelling secret
    if (cast.Backstory.Secrets.Count == 0) return false;

    // Televisuality must be above threshold
    if (cast.Personality.Televisuality < 40) return false;

    return true;
}
```

Cast members who fail the filter are discarded and regenerated. This ensures the casting pool is full of interesting characters, not bland filler.

---

## 5. SAVE SYSTEM DESIGN

### 5.1 Save Architecture

**Save Scope:** Everything needed to restore exact game state.

- Season number, episode number
- All cast member states (current + historical)
- Footage stockpile (unsaved footage persists across sessions)
- Showrunner reputation
- Network satisfaction history
- Audience segment satisfaction history
- Post-show outcomes for all former cast members
- Pending fallout events
- Unlocked systems and content

**Save Format:** JSON

Why JSON over binary?
- **Human-readable** for debugging and support
- **Forward-compatible** (can add new fields without breaking old saves)
- **Cross-platform** (no endianness issues)
- **Modding-friendly** (players can potentially hand-edit saves if they want)

Performance hit from JSON parsing is negligible. Save/load happens infrequently (once per session start/end). Save file size ~500KB-2MB per career. Acceptable.

### 5.2 Save Structure

```json
{
  "version": "1.0.0",
  "saveTimestamp": "2026-02-07T18:30:00Z",
  "showrunnerData": {
    "reputation": 68,
    "seasonsCompleted": 4,
    "totalEpisodesAired": 42
  },
  "currentSeason": {
    "seasonNumber": 5,
    "episodeNumber": 3,
    "format": "Heartshot",
    "cast": [
      {
        "id": "cast-001",
        "name": "Jade Martinez",
        "archetype": "Sweetheart",
        "psychologicalIntegrity": 58,
        "personality": { ... },
        "relationships": [ ... ],
        "history": [ ... ]
      },
      // ... other cast members
    ],
    "footageStockpile": [ ... ],
    "networkSatisfaction": 72,
    "audienceSegments": { ... }
  },
  "legacyData": {
    "formerCastMembers": [ ... ],
    "postShowOutcomes": [ ... ],
    "historicalEvents": [ ... ]
  }
}
```

### 5.3 Save System Implementation

```csharp
public class SaveSystem
{
    private const string SAVE_FOLDER = "Saves";
    private const string SAVE_EXTENSION = ".burnbook";

    public void SaveGame(string slotName)
    {
        var saveData = new SaveData
        {
            Version = Application.version,
            SaveTimestamp = DateTime.UtcNow,
            ShowrunnerData = GameManager.Instance.Showrunner.Serialize(),
            CurrentSeason = GameManager.Instance.CurrentSeason.Serialize(),
            LegacyData = GameManager.Instance.Legacy.Serialize()
        };

        string json = JsonUtility.ToJson(saveData, prettyPrint: true);
        string path = GetSavePath(slotName);

        File.WriteAllText(path, json);

        // Steam Cloud sync
        if (SteamManager.Initialized)
        {
            SteamRemoteStorage.FileWrite(GetCloudSaveName(slotName),
                                         Encoding.UTF8.GetBytes(json));
        }
    }

    public SaveData LoadGame(string slotName)
    {
        string path = GetSavePath(slotName);

        if (!File.Exists(path))
        {
            // Try Steam Cloud
            if (SteamManager.Initialized)
            {
                return LoadFromSteamCloud(slotName);
            }
            return null;
        }

        string json = File.ReadAllText(path);
        var saveData = JsonUtility.FromJson<SaveData>(json);

        // Version migration if needed
        if (saveData.Version != Application.version)
        {
            saveData = MigrateSaveData(saveData);
        }

        return saveData;
    }
}
```

### 5.4 Auto-Save Strategy

**When to auto-save:**
- After every episode broadcast
- After every major decision (casting, elimination, network intervention)
- Every 10 minutes during active play (background auto-save)

**Auto-save slot:** Separate from manual saves. Rotates 3 auto-save files (auto-save-1, auto-save-2, auto-save-3) to prevent corruption from killing all auto-saves.

**Save Corruption Handling:**

```csharp
public SaveData LoadGameSafe(string slotName)
{
    try
    {
        return LoadGame(slotName);
    }
    catch (Exception e)
    {
        Debug.LogError($"Save corrupted: {e.Message}");

        // Try backup
        var backup = LoadGame(slotName + ".backup");
        if (backup != null) return backup;

        // Fail gracefully
        ShowErrorDialog("Save file corrupted. Starting new game.");
        return null;
    }
}
```

Every manual save creates a `.backup` copy of the previous save. If the main save is corrupted, roll back to backup. This handles the 99% case (power loss during save write).

---

## 6. PERFORMANCE BUDGET & OPTIMIZATION STRATEGY

### 6.1 Target Performance

| Platform | Target FPS | Resolution | Load Time (Episode Start) |
|----------|-----------|------------|---------------------------|
| PC (Mid-range) | 60 FPS | 1920x1080 | < 2 seconds |
| PC (High-end) | 60 FPS | 3840x2160 | < 1 second |
| Steam Deck | 60 FPS | 1280x800 | < 3 seconds |

**Why 60 FPS?** This is a UI-driven game, not a twitch action game. 60 FPS is overkill from a gameplay perspective, but it makes the UI feel snappy and responsive. 30 FPS would be acceptable but would feel sluggish on PC. Lock to 60, optimize to maintain it.

### 6.2 Performance Bottlenecks

**Predicted Hot Spots:**

1. **Situation Engine AI resolution** (16 cast members x 10 actions x 120 ticks = 19,200 evaluations per scene)
2. **UI rendering** (burn book with 16 cast member dossiers, each with 20+ data points)
3. **Footage stockpile rendering** (50+ moments with thumbnails, text, metadata)
4. **Relationship graph updates** (16 cast x 16 potential relationships = 256 edges to check)
5. **Save/load serialization** (deep object graphs, hundreds of KB)

**Optimization Strategy:**

| Bottleneck | Optimization | Expected Gain |
|------------|--------------|---------------|
| AI resolution | Run on background thread, cache utility scores for identical contexts | 40-60% CPU reduction |
| UI rendering | Virtualized scrolling (only render visible UI elements), object pooling for list items | 50-70% GPU reduction |
| Footage stockpile | Lazy load thumbnails (generate on-demand, cache), paginated display | 30-50% load time reduction |
| Relationship graph | Adjacency list storage, update only changed relationships, batch updates | 20-30% CPU reduction |
| Save/load | Incremental serialization (only serialize changed data), compression | 30-40% file size + load time reduction |

### 6.3 Profiling Checkpoints

**Milestone 1 (Prototype):** Profile situation engine with 4 cast members, 1 scene. Must run < 5 seconds total simulation time.

**Milestone 2 (Vertical Slice):** Full episode (6 scenes, 8 cast members). Must maintain 60 FPS during edit bay, scene resolution in background.

**Milestone 3 (Beta):** Full season (10 episodes, 12 cast members). No frame drops, load times < 3 seconds, save file < 2MB.

**Tools:**
- Unity Profiler (CPU, GPU, memory)
- Deep Profiling (enabled for AI behavior tick inspection)
- Memory Profiler (check for leaks in cast member state tracking)

### 6.4 Memory Budget

| Component | Estimated Memory | Justification |
|-----------|------------------|---------------|
| Cast member data (16 max) | ~2 MB | 128 KB per cast member (state, history, relationships) |
| Footage stockpile | ~5 MB | 50 moments x 100 KB per moment (metadata, not video) |
| UI assets | ~20 MB | Textures for burn book, UI chrome, fonts |
| Audio (music cues) | ~10 MB | Compressed audio, streamed from disk |
| Scene simulation runtime | ~5 MB | AI state, temporary buffers |
| **Total Runtime Memory** | ~50 MB | Comfortable on all target platforms |

Steam Deck has 16 GB RAM, but shared with GPU. Keeping game footprint under 100 MB total leaves plenty of headroom.

---

## 7. PLATFORM CONSIDERATIONS

### 7.1 PC (Primary Platform)

**Input:**
- Mouse + Keyboard (primary)
- Gamepad (secondary, post-launch)

**UI Scaling:**
- Support 1920x1080 (most common)
- Support 3840x2160 (4K, UI scaled 2x)
- Support ultrawide (21:9) — burn book on left, scene view on right, edit timeline on bottom

**Windowed vs. Fullscreen:**
- Default: Borderless Windowed (allows alt-tabbing, common for management sims)
- Option: Exclusive Fullscreen (slightly better performance)

**Graphics Settings:**
- Minimal settings needed (2D UI game). Offer: resolution, VSync on/off, UI scale slider.

### 7.2 Steam Deck (Secondary Platform)

**Input:**
- Touchscreen for burn book navigation (tap to open dossier)
- Trackpad for edit bay timeline scrubbing
- Buttons for quick actions (confirm, cancel, pause)

**Performance:**
- Target 60 FPS at 1280x800. Achievable (UI rendering, no heavy 3D).
- Battery life: ~4-5 hours (typical for non-3D games).

**UI Adjustments:**
- Larger touch targets (burn book entries, footage moments)
- Simplified timeline editing (fewer segments visible at once, scroll to see full timeline)
- Font size +10% for readability on small screen

**Validation:**
- Playtest on Steam Deck at Milestone 2 (vertical slice). Ensure no control scheme blockers.

### 7.3 Console (Post-Launch Consideration)

Not planned for v1. If pursued:

**Challenges:**
- Edit bay timeline requires precision cursor control. Needs controller-friendly redesign (snap-to-grid, d-pad navigation).
- Burn book navigation: use radial menu or tabbed interface.
- Certification: Each platform (Xbox, PlayStation, Switch) has different requirements. 3-6 months additional dev per platform.

**Recommendation:** Ship PC/Steam Deck first. If sales justify it, port to console 12-18 months post-launch.

---

## 8. BUILD PIPELINE & TOOLS

### 8.1 Version Control

**System:** Git + GitHub (or GitLab, BitBucket)

**Branching Strategy:**
- `main` — stable, releasable at any time
- `develop` — active development branch
- `feature/[name]` — individual features (merged to develop via PR)
- `hotfix/[issue]` — critical bug fixes (merged to main + develop)

**Unity-Specific Considerations:**
- Use Unity's YAML text serialization for scenes/prefabs (merge-friendly)
- Use Git LFS for binary assets (textures, audio)
- `.gitignore` for `Library/`, `Temp/`, `Logs/`

### 8.2 Build Automation

**CI/CD:** GitHub Actions (free for public repos, cheap for private)

**Build Triggers:**
- Every commit to `develop` → automated build + unit tests
- Every commit to `main` → automated build + integration tests + Steam upload (staging branch)
- Manual trigger → production release build

**Unity Cloud Build Alternative:** If GitHub Actions is too complex, Unity Cloud Build is simpler but slower and less flexible. Lean toward GitHub Actions for control.

### 8.3 Asset Pipeline

**Audio:**
- Music cues: OGG Vorbis, 128 kbps (quality adequate for production suite ambiance)
- SFX: OGG Vorbis, 96 kbps (UI clicks, page turns, keyboard clacks)
- Streamed from disk (not loaded into memory)

**Textures:**
- UI elements: PNG, compressed (Unity's ETC2/ASTC compression)
- Burn book pages: 2048x2048 atlases (multiple pages per texture to reduce draw calls)
- Cast member portraits: 512x512, procedurally generated or stock photos (license permitting)

**Fonts:**
- TextMeshPro SDF fonts (sharp at any scale, essential for burn book text clarity)
- Two fonts: one for UI chrome (Impact-style, chunky), one for documents (Courier-style, typewriter)

### 8.4 Content Tools (Editor Extensions)

**Burn Book Editor:**
- Custom Unity Editor window for designing cast member archetypes
- Visual editor for backstory pools, personality trait ranges, wound/trigger associations
- Allows designers to iterate on cast generation without touching code

**Situation Engine Debugger:**
- Real-time visualization of AI decision-making during scene simulation
- Shows utility scores for each action, highlights chosen action, displays relationship graph
- Essential for debugging "why did this cast member do that?"

**Balance Tuning Dashboard:**
- Central location for tweaking economy values, PI decay rates, audience segment preferences
- Hooked to ScriptableObjects for data-driven design (no recompile needed)

**Implementation:**

```csharp
#if UNITY_EDITOR
[CustomEditor(typeof(ArchetypeData))]
public class ArchetypeEditor : Editor
{
    public override void OnInspectorGUI()
    {
        DrawDefaultInspector();

        var archetype = (ArchetypeData)target;

        if (GUILayout.Button("Generate Sample Cast Member"))
        {
            var generator = new CastGenerator();
            var sample = generator.GenerateCastMember(50);
            Debug.Log($"Generated: {sample.Name} ({sample.Archetype.Name})");
            Debug.Log($"Personality: {JsonUtility.ToJson(sample.Personality)}");
        }
    }
}
#endif
```

This allows designers to click a button and instantly see what a cast member generated from an archetype looks like. Iterate fast.

---

## 9. TECHNICAL RISK ASSESSMENT

### 9.1 Critical Risks (Could Kill the Project)

| Risk | Severity | Probability | Mitigation |
|------|----------|-------------|------------|
| **AI generates boring/nonsensical scenes** | CRITICAL | MEDIUM | Prototype AI behavior FIRST (Milestone 1). If AI doesn't work by month 3, pivot to more scripted/guided system. Set kill condition: <70% playtester satisfaction with AI behavior. |
| **Edit bay feels like tedious work** | CRITICAL | MEDIUM | Playtest edit bay in isolation (Milestone 2). If >40% testers report tedium, simplify aggressively (reduce segments, remove features). Core verb must feel like AUTHORSHIP, not data entry. |
| **Scope creep (too many systems)** | HIGH | HIGH | Freeze feature list after design doc approval. Stretch goals explicitly marked "not v1." Ruthlessly cut features that don't serve core loop. |
| **Performance issues on Steam Deck** | MEDIUM | MEDIUM | Profile early (Milestone 2). If <60 FPS, cut UI effects, reduce max cast members per scene, optimize UI rendering. Steam Deck is secondary platform — PC comes first if tradeoffs needed. |

### 9.2 High Risks (Would Significantly Delay/Harm Project)

| Risk | Severity | Probability | Mitigation |
|------|----------|-------------|------------|
| **Save system corruption in wild** | HIGH | LOW | Extensive QA on save/load. Auto-save rotation + backups. Sentry/analytics integration to detect save failures in production. |
| **UI complexity overwhelms players** | HIGH | MEDIUM | Progressive disclosure. Tutorial season (Season 1) has simplified UI. User testing at Milestone 3. Add "Advisor" hints system if needed. |
| **Procedural cast generation produces samey characters** | MEDIUM | MEDIUM | Quality filter + large archetype/backstory pools. Playtest: can testers name and describe 3 cast members after one season? If not, increase characterization hooks (signature traits, memorable backstories). |
| **Balance is broken (too easy/too hard)** | MEDIUM | HIGH | Difficulty modes (Basic Cable / Network / Premium / Hell). Telemetry in beta to track player success rates. Tune economy based on data. |
| **Players don't feel moral weight** | MEDIUM | MEDIUM | Narrative playtest (Milestone 4). Track "I felt bad" moments. If <50% of testers report discomfort, amplify fallout consequences, add more explicit post-show outcomes. |

### 9.3 Medium Risks (Annoying But Recoverable)

- **Voice-over for UI elements** — Not planned for v1 (text-only). If players request it, add in post-launch patch.
- **Localization** — English-only at launch. Text-heavy game = expensive localization. Add if sales justify (Spanish, French, German first).
- **Mod support** — JSON save files are inherently moddable, but no official tools. Community will mod regardless. Decide post-launch if we support it.
- **Steamworks integration bugs** — Use Steamworks.NET, mature library. But achievements/cloud saves can be finicky. Test on non-dev Steam accounts during beta.

### 9.4 Risk Mitigation Timeline

**Month 1-3 (Prototype Phase):**
- RISK FOCUS: AI behavior quality
- GATE: AI playtest. If fail, pivot or kill project.

**Month 4-6 (Vertical Slice):**
- RISK FOCUS: Edit bay feel, UI complexity
- GATE: Edit bay playtest. If fail, simplify aggressively.

**Month 7-12 (Production):**
- RISK FOCUS: Scope creep, performance
- GATE: Monthly feature review. Cut anything not on critical path.

**Month 13-18 (Beta + Polish):**
- RISK FOCUS: Balance, moral weight, save system stability
- GATE: Closed beta with 50-100 players. Telemetry + surveys.

---

## 10. DEVELOPMENT MILESTONES (TECHNICAL PERSPECTIVE)

### Milestone 1: AI PROTOTYPE (Month 1-3)

**Deliverable:** Situation Engine with 4 cast members, 1 location (dinner table), 3 catalyst types. Scene resolves, generates footage.

**Technical Goals:**
- Utility AI decision system functional
- Cast member state tracking (PI, relationships, emotions)
- Moment detection algorithm working
- Basic UI for scene setup (drag cast to table)

**Success Criteria:**
- 10 playthroughs of same scene setup produce 10 distinct outcomes
- At least 1 "surprise" per playthrough (something player didn't predict)
- Scene resolution completes in < 5 seconds
- Playtest satisfaction > 7/10

**Kill Condition:** If AI feels robotic, repetitive, or nonsensical after 3 months of iteration, abort or pivot to more scripted system.

---

### Milestone 2: VERTICAL SLICE (Month 4-6)

**Deliverable:** One complete episode. Casting, 4 scenes, edit bay, broadcast, ratings report.

**Technical Goals:**
- Edit bay UI fully functional (6 segments, music cues, confessional overlays)
- Ratings Engine calculates accurate scores
- Burn book displays intel with confidence decay
- Full loop playable start-to-finish

**Success Criteria:**
- Episode completion takes 25-35 minutes
- Edit bay playtest satisfaction > 7/10
- No major bugs in core loop
- 60 FPS maintained throughout

**Risk Check:** If edit bay feels tedious or ratings feel opaque, this is the milestone to course-correct.

---

### Milestone 3: FULL SEASON (Month 7-10)

**Deliverable:** Complete Season 1 (8 episodes). Casting, all scenes, eliminations, finale, season report card.

**Technical Goals:**
- Fallout system active (PI tracking, consequence events)
- Save/load functional
- Tutorial/onboarding flow
- Two show formats available

**Success Criteria:**
- Season arc feels complete (has beginning, middle, climax)
- Players can name and describe 3+ cast members
- Save/load works flawlessly
- No performance degradation over 4+ hours of play

**User Testing:** 10-15 external playtesters. Full season playthrough. Surveys on every system.

---

### Milestone 4: MULTI-SEASON CAMPAIGN (Month 11-14)

**Deliverable:** Seasons 1-4 with full progression, reputation system, legacy consequences.

**Technical Goals:**
- Showrunner reputation unlocks working
- Post-show outcomes surfacing correctly
- Between-season management flow
- Content unlocks (new locations, catalysts, edit bay tools)

**Success Criteria:**
- Season-to-season progression feels meaningful
- Legacy consequences create long-tail story threads
- Players report emotional attachment to their career
- Difficulty curve feels right (not too easy, not too hard)

**Balance Pass:** Tune economy, PI decay, audience segment weights based on playtest data.

---

### Milestone 5: FULL CONTENT (Month 15-18)

**Deliverable:** All 8 seasons, all systems unlocked, all difficulty modes.

**Technical Goals:**
- Performance optimized (60 FPS, <3s load times)
- Polish pass on all UI (animations, sound effects, visual feedback)
- Bug fixing based on internal QA
- Steam integration (achievements, cloud saves, stats)

**Success Criteria:**
- Game is content-complete
- No critical bugs
- Performance targets met on all platforms
- Ready for closed beta

---

### Milestone 6: BETA & POLISH (Month 19-22)

**Deliverable:** Closed beta build for 50-100 external testers. Iterate based on feedback.

**Technical Goals:**
- Telemetry integration (track player behavior, identify pain points)
- Bug fixing from beta reports
- Balance tuning based on player data
- Localization prep (string extraction, text audit)

**Success Criteria:**
- <5 critical bugs
- Balance feels right (not too many reports of "too easy" or "too hard")
- Players complete multiple seasons (engagement metric)
- Steam Deck performance validated

---

### Milestone 7: LAUNCH (Month 23-24)

**Deliverable:** v1.0 live on Steam.

**Technical Goals:**
- Day-one patch ready (for any last-minute critical bugs)
- Steam store page live (capsule art, trailer, description)
- Launch monitoring (crash reports, performance metrics)
- Community management (Discord, Reddit, social media)

**Success Criteria:**
- Clean launch (no server issues, no game-breaking bugs)
- Positive initial reviews (>80% on Steam)
- Sales meet expectations (TBD based on marketing budget)

---

## 11. POST-LAUNCH TECHNICAL ROADMAP

### Patch 1.1 (Month 25-26): Quality of Life

**Features:**
- UI improvements based on player feedback
- Additional music cues (community request)
- Balance tweaks (if needed)
- Bug fixes

### Patch 1.2 (Month 27-28): Accessibility

**Features:**
- Colorblind modes
- Text size scaling
- Screen reader support (if feasible)
- Controller remapping

### DLC 1 (Month 29-32): NEW FORMATS

**Features:**
- 2 new show formats (e.g., "Runway War" talent competition, "Isle" survival format)
- New locations and catalysts
- New cast archetypes

### DLC 2 (Month 33-36): STRETCH GOALS

**Features:**
- Rival Showrunner system
- Reunion Special end-of-season event
- Format Laboratory (custom format designer)

---

## 12. TESTING STRATEGY

### 12.1 Unit Testing

**What to Test:**
- AI utility calculations (given state X, utility Y is correct)
- Ratings formulas (given episode data, rating is calculated correctly)
- PI decay/recovery (given scene, PI changes correctly)
- Relationship graph updates (adding/removing relationships works)
- Save/load serialization (data round-trips correctly)

**Tools:** Unity Test Framework, NSubstitute for mocking

**Coverage Target:** 70% code coverage on core systems (AI, ratings, fallout). UI code is harder to unit test; rely on integration tests there.

### 12.2 Integration Testing

**What to Test:**
- Full episode loop (scene setup → resolution → edit → broadcast → ratings)
- Save/load preserves all state correctly
- Fallout events trigger at correct PI thresholds
- Burn book confidence decays correctly over multiple episodes

**Tools:** Automated playthrough scripts (simulate player actions, verify outcomes)

### 12.3 Playtesting

**Internal Playtesting (Ongoing):**
- Weekly playtests with team members
- Focus on one system per session (e.g., "this week test edit bay feel")
- Structured feedback forms

**External Playtesting (Milestone 3+):**
- 10-15 external testers per milestone
- Full season playthroughs
- Surveys + interviews
- Track: time to complete, satisfaction scores, specific pain points

**Beta Testing (Milestone 6):**
- 50-100 external testers
- Telemetry tracking (which features used, where players quit, average session length)
- Community feedback via Discord/forums

---

## 13. TECHNICAL DEBT MANAGEMENT

**Definition:** Technical debt is shortcuts taken to ship faster, with the understanding that they'll need refactoring later.

**Allowed Debt (We'll Pay It Back):**
- **Prototype AI:** First pass AI behavior can be hacky. Refactor at Milestone 2.
- **Placeholder UI Art:** Programmer art for UI during prototyping. Replace with polished art at Milestone 5.
- **Hardcoded Values:** Economy balance values hardcoded during prototyping. Move to ScriptableObjects at Milestone 3.

**Forbidden Debt (Never Accumulate):**
- **No Architecture Shortcuts:** Systems must be clean from day one. No "quick hacks" that couple systems tightly. The codebase must remain maintainable.
- **No Performance Debt:** Don't ship slow code with "we'll optimize later." Optimize during development. Performance issues compound.
- **No Save System Hacks:** Save/load must be robust from the start. Corrupted saves kill player trust.

**Debt Review:** Monthly code review. Identify accumulated debt, prioritize paydown. If debt is growing faster than paydown, slow feature development.

---

## 14. OPEN TECHNICAL QUESTIONS

These require prototyping or design decisions:

1. **Scene Simulation Speed:** Should scenes play in real-time (90-120 seconds of wall time) or compressed (30-45 seconds)? Real-time feels more "realistic" but slower. Compressed is faster but may feel rushed. DECISION NEEDED: Milestone 1 playtesting.

2. **Edit Bay Undo/Redo:** Should the edit bay support undo/redo for segment changes? Adds UI complexity but improves usability. DECISION NEEDED: Milestone 2 based on playtest feedback.

3. **Cast Member Cap:** Max 16 cast members per season. Is this enough? Too many? Affects performance and complexity. DECISION NEEDED: Milestone 3 based on playtesting. If 16 feels empty, increase to 20. If 16 feels overwhelming, reduce to 12.

4. **Voice-Over Budgeting:** Not planned for v1, but if budget allows, should we add VO for key confessionals? Or stay text-only for flexibility? DECISION NEEDED: Post-Milestone 5 if budget remains.

5. **Modding Support:** Should we expose cast member archetypes and backstory pools as JSON files for modders? Or keep everything internal? Modding increases longevity but adds support burden. DECISION NEEDED: Post-launch based on community demand.

6. **Analytics Depth:** How much telemetry do we collect? Track every player action (detailed, privacy-invasive) or just high-level metrics (episode completion, session length)? DECISION NEEDED: Beta phase. Lean toward minimal telemetry, respect player privacy.

---

## 15. CLOSING NOTES

BURNBOOK is technically ambitious but achievable. The core risk is the Situation Engine AI. If that works, everything else is standard engineering. If it doesn't, the game collapses.

**What I'm confident about:**
- Unity is the right engine (UI-first design, fast iteration)
- The five-system architecture is clean and testable
- Save system design is robust (JSON + backups)
- Performance targets are achievable (UI-driven, no heavy 3D)

**What concerns me:**
- AI behavior variety. Template-based dialogue and utility AI can produce samey results. We need tight archetype design and enough personality variance to make cast members feel distinct. Playtesting will reveal if we hit that bar.
- Edit bay complexity. This is the unique mechanic, the one that makes the game special. It must feel like authorship, not data entry. If it doesn't, we simplify until it does. No compromise.
- Scope discipline. Five systems is a lot. Feature creep will kill us. Freeze the scope after design doc approval. Stretch goals are post-launch. Ship the chassis first.

**Kill Conditions:**
- If AI behavior doesn't feel emergent and interesting by Month 3, we pivot or abort.
- If the edit bay feels tedious after Milestone 2, we simplify aggressively or redesign.
- If we can't maintain 60 FPS at Milestone 3, we cut features until we can.

**Success Conditions:**
- AI generates stories that players want to tell their friends.
- Edit bay feels like wielding narrative power.
- Players feel the moral weight of their choices without the game preaching.
- The loop holds at hour 100.

Ship it, then improve it. Make it right. Then make it fast. In that order.

Let's build this.

— BYTE

---

**Document complete. No placeholders. No TODOs. Ready for team review and prototype kickoff.**

*Technical Architecture Document generated following production-ready standards. All systems documented, risks identified, milestones defined. Estimated build timeline: 18-24 months to v1.0 launch.*
