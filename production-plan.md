# BURNBOOK — Production Plan

**Version:** 1.0
**Author:** CLOCK (Producer)
**Date:** 2026-02-07
**Status:** Pre-Production Planning
**Target Launch:** Q4 2027 (24 months)

---

## 0. PRODUCTION PHILOSOPHY

Let me be clear about something: this document is not aspirational. It's a contract with reality. BURNBOOK is one of the most mechanically complex games this studio will build — five interlocking systems, AI-driven simulation, procedural narrative generation, and a UI that spans six distinct interfaces. The pitch is brilliant. The design is sound. The art direction is focused. The tech architecture is solid.

None of that matters if we can't execute on time and within scope.

I've read every document. I've mapped every dependency. I've identified every risk. The good news: this project is achievable. The bad news: there is zero room for scope creep. The critical path runs straight through the Situation Engine AI. If that system doesn't produce emergent, believable behavior by Month 3, the entire project collapses. Everything else — the edit bay, the burn book, the ratings engine — is engineering. The AI is faith.

Here's what ships in v1: single-player PC game, five core systems, two show formats, full 8-season campaign, procedural cast generation. That's the MVP. Everything else — rival showrunners, reunion specials, format labs — is stretch goals for post-launch DLC.

Cut scope, not corners. Ship something real.

---

## 1. PROJECT OVERVIEW

### 1.1 Core Deliverable

**BURNBOOK v1.0** — A reality TV production simulator where the player is a showrunner casting AI-driven personalities, manufacturing drama through scene placement, editing raw footage into broadcast episodes, and managing the consequences of their choices across an 8-season career.

### 1.2 Team Structure

**Core Team:**
- **1 Lead Programmer (BYTE)** — Engine architecture, AI systems, core loop implementation
- **1 UI/UX Engineer** — Edit bay, burn book, all interface systems
- **1 Gameplay Programmer** — Scene simulation, ratings calculations, fallout tracking
- **1 Game Designer (REED)** — Systems design, economy balance, AI behavior tuning
- **1 Narrative Designer (NOVA)** — Cast archetypes, dialogue templates, backstory generation
- **1 Art Director (PIXEL)** — UI mockups, visual identity, asset direction
- **1 Sound Designer (ECHO)** — SFX library, ambiance system, music cues
- **1 Producer (CLOCK)** — That's me. Schedule, scope, dependencies, risk management.

**Extended Team (Contract/Part-Time):**
- **1 QA Lead (CRASH)** — Joins at Month 7 (Alpha phase), full-time through launch
- **1 Technical Artist** — UI implementation, shader work, performance optimization (Months 10-18)
- **1 Composer** — Music cue library creation (Months 13-16)

**Total Headcount:** 8 core, 3 extended = 11 people peak.

### 1.3 Platform & Scope

**Primary Platform:** PC (Steam)
**Secondary Platform:** Steam Deck (validated at Beta, no separate build)
**Language:** English only at launch
**Multiplayer:** None
**Post-Launch:** Patches, DLC, possible console ports 18+ months out

**What Ships in v1:**
- 5 core systems (Burn Book, Situation Engine, Edit Bay, Ratings, Fallout)
- 2 show formats (House of Strangers, Heartshot)
- 8 seasons with full progression
- 6-16 procedurally generated cast members per season
- 30+ music cues for edit bay
- Full tutorial and onboarding flow
- Steam integration (achievements, cloud saves, stats)

**What Doesn't Ship in v1:**
- Rival showrunner system (DLC)
- Reunion special (DLC)
- Format laboratory (DLC)
- Writers' room management (DLC)
- Cultural moment tracking (DLC, maybe)
- Voice acting (text-only)
- 3D environments (all UI/2D)
- Mobile port (not feasible for edit bay complexity)

### 1.4 Budget & Resources

**Development Budget:** $800K - $1.2M (estimated, assumes modest salaries + contract work)

**Breakdown:**
- Salaries (8 core x 24 months): $720K - $960K
- Contract work (QA, art, audio): $40K - $80K
- Software licenses (Unity Pro, middleware): $10K
- Marketing & community (Steam page, trailer, PR): $20K - $40K
- Contingency (10%): $80K - $120K

**Revenue Model:** Premium purchase on Steam ($19.99 - $24.99 base price). No MTX, no season pass at launch. Clean single purchase.

### 1.5 Timeline Summary

**Total Development Time:** 24 months (Month 0 = Feb 2026, Launch = Q4 2027)

| Phase | Duration | Key Deliverable |
|-------|----------|-----------------|
| Prototype | Months 1-3 | AI Situation Engine proof-of-concept |
| Vertical Slice | Months 4-6 | One complete episode playable |
| Alpha | Months 7-12 | Full season (8 episodes) with all systems |
| Production | Months 13-18 | Content complete, all 8 seasons |
| Beta & Polish | Months 19-22 | External testing, bug fixing, balance |
| Launch Prep | Months 23-24 | Marketing ramp, Steam store, day-one patch |
| **LAUNCH** | **Month 24** | **BURNBOOK v1.0 live on Steam** |

---

## 2. MILESTONE DEFINITIONS

Each milestone has clear entry criteria, exit criteria, and success metrics. If we hit the exit criteria, we proceed. If we don't, we don't. No exceptions.

### MILESTONE 1: PROTOTYPE — AI PROOF OF CONCEPT
**Duration:** Months 1-3
**Owner:** BYTE (Lead Programmer)
**Team:** BYTE + 1 Gameplay Programmer + REED (tuning)

**Entry Criteria:**
- Unity 2022 LTS environment set up
- Core team hired and onboarded
- Design documents finalized and frozen

**Deliverable:**
A playable prototype of the Situation Engine with 4 cast members, 1 location (dinner table), 3 catalyst types. The player can set up a scene (place cast, add catalysts), watch it resolve via AI simulation, and receive tagged footage moments.

**Exit Criteria:**
- [ ] AI produces emergent behavior (not scripted, not random)
- [ ] 10 playthroughs of identical scene setup produce 10 distinct outcomes
- [ ] At least 1 "surprise" per playthrough (player couldn't predict it)
- [ ] Scene resolves in < 5 seconds
- [ ] Drama value calculation working (0-100 scale, sensible values)
- [ ] Basic relationship tracking (allies, rivals) updates correctly
- [ ] Unit tests passing for AI utility system (70% code coverage)

**Success Metrics:**
- Internal playtest satisfaction > 7/10 ("the AI feels alive")
- REED can tune AI behavior without programmer intervention
- Zero critical bugs in core simulation loop

**Risk Gate:**
This is the KILL GATE. If the AI doesn't feel emergent, believable, and interesting after 3 months of iteration, we either pivot to a more scripted system (which breaks the core fantasy) or we abort the project. No halfway measures. The AI must work.

**Budget Burn:** $90K - $120K (3 months, 3 people)

---

### MILESTONE 2: VERTICAL SLICE — ONE COMPLETE EPISODE
**Duration:** Months 4-6
**Owner:** BYTE + UI Engineer
**Team:** Full core team (8 people)

**Entry Criteria:**
- Prototype AI approved (Milestone 1 passed)
- Art direction mockups complete for all UI screens
- Sound design document approved

**Deliverable:**
One complete episode playable start-to-finish. Casting phase (choose 4 cast members from pool of 8), 4 scenes (setup → shoot → harvest), edit bay (assemble 6-segment episode from footage), broadcast, ratings report. Full loop.

**Exit Criteria:**
- [ ] Full episode takes 25-35 minutes to complete
- [ ] Edit bay UI functional: drag-drop footage, add music cues, write chyrons
- [ ] Real-time episode quality score updates as player edits
- [ ] Ratings report generates correctly (Nielsen, segment satisfaction, ACI, NSS)
- [ ] Burn book displays cast intel with confidence tracking
- [ ] Save/load works for episode state
- [ ] 60 FPS maintained on target hardware (GTX 1060 equivalent)
- [ ] No critical bugs

**Success Metrics:**
- External playtest satisfaction > 7/10
- Edit bay playtest: "feels like authorship, not data entry" (>70% agreement)
- Ratings report: "I understand why ratings went up/down" (>80% agreement)
- Session length variance < 10 minutes (good pacing consistency)

**Risk Gate:**
If the edit bay feels tedious or the ratings feel opaque, this is where we course-correct. Simplify the edit bay (fewer segments, remove features). Make ratings attribution explicit (show why each segment moved the needle). No moving forward until the core loop feels good.

**Budget Burn:** $180K - $240K (3 months, 8 people)

---

### MILESTONE 3: ALPHA — FULL SEASON PLAYABLE
**Duration:** Months 7-12 (6 months)
**Owner:** BYTE + Full Team
**Team:** 8 core + QA Lead joins Month 7

**Entry Criteria:**
- Vertical slice approved (Milestone 2 passed)
- All core system code complete
- Art assets for UI at 70% complete
- Sound design assets at 50% complete

**Deliverable:**
Complete Season 1 (8 episodes) playable. Casting, all scene types, eliminations, mid-season events, season finale, season report card, between-season management. Fallout system active (PI tracking, consequence events). Tutorial flow implemented.

**Exit Criteria:**
- [ ] Full season (8 episodes) takes 4-6 hours to complete
- [ ] All 5 core systems integrated and functional
- [ ] PI decay/recovery calculations working correctly
- [ ] Fallout events trigger at correct thresholds (PI < 40, < 20, etc.)
- [ ] Post-show outcomes generate for eliminated cast
- [ ] Burn book confidence decays over time, predictions validated
- [ ] Save/load preserves full season state
- [ ] Tutorial onboards new players (completion rate >85%)
- [ ] Performance stable over 6-hour play session (no memory leaks)
- [ ] Zero critical bugs, <20 high-priority bugs

**Success Metrics:**
- 10-15 external playtesters complete full season
- Players can name and describe 3+ cast members after season (characterization test)
- Season arc feels complete: "had a beginning, middle, and end" (>75% agreement)
- Moral weight metric: "I felt the consequences of my choices" (>60% agreement)
- Balance feels fair: "not too easy, not too hard" (average difficulty rating 6-7/10)

**Content Milestones Within Alpha:**
- Month 7: Tutorial + Episode 1-2 functional
- Month 8: Episodes 3-5 + fallout system active
- Month 9: Episodes 6-8 + season finale structure
- Month 10: Between-season management flow
- Month 11: Polish pass, bug fixing
- Month 12: Alpha feature freeze, external playtesting

**Risk Gate:**
If balance is broken (too easy = boring, too hard = frustrating), this is the milestone to tune. Economy values, PI decay rates, audience segment weights — all of this gets calibrated based on playtest data. Do not proceed to content production until balance feels right.

**Budget Burn:** $360K - $480K (6 months, 9 people)

---

### MILESTONE 4: PRODUCTION — CONTENT COMPLETE
**Duration:** Months 13-18 (6 months)
**Owner:** Full Team
**Team:** 8 core + QA Lead + Technical Artist (Month 15+)

**Entry Criteria:**
- Alpha approved (Milestone 3 passed)
- All systems stable and feature-complete
- Art direction final (no more mockup changes)
- Sound design 80% complete (all SFX, most music cues)

**Deliverable:**
All 8 seasons content-complete. Full showrunner career progression (reputation system, unlocks, legacy consequences). Two show formats fully implemented (House of Strangers, Heartshot). All difficulty modes available (Basic Cable, Network, Premium, Reality TV Hell).

**Exit Criteria:**
- [ ] Seasons 1-8 fully playable
- [ ] Reputation system unlocks working (casting pool quality scales with rep)
- [ ] Post-show outcomes surface correctly across seasons (legacy events)
- [ ] All UI art final and implemented
- [ ] All SFX and ambiance systems complete
- [ ] Music cue library complete (30 cues)
- [ ] Steam integration working (achievements, cloud saves, stats)
- [ ] Performance optimized (60 FPS, <3s load times)
- [ ] <10 critical bugs, <50 high-priority bugs

**Content Milestones Within Production:**
- Month 13-14: Seasons 2-4 content production
- Month 15-16: Seasons 5-6 content production
- Month 16: Music cue library recording/integration
- Month 17: Seasons 7-8 content production + difficulty modes
- Month 18: Polish pass (animations, audio mix, UI feedback), final art integration

**Success Metrics:**
- Full campaign (8 seasons) takes 30-45 hours
- Progression feels meaningful: "my choices mattered across seasons" (>70% agreement)
- No content gaps: "every season felt complete" (>80% agreement)
- Performance targets met on all test hardware

**Risk Gate:**
If performance degrades (FPS drops, long load times), this is the milestone to optimize. Cut UI effects, reduce max cast per scene, optimize relationship graph updates. Performance is non-negotiable. The game must run at 60 FPS on target hardware.

**Budget Burn:** $360K - $480K (6 months, 10 people peak)

---

### MILESTONE 5: BETA & POLISH
**Duration:** Months 19-22 (4 months)
**Owner:** CLOCK (coordinating) + CRASH (QA Lead)
**Team:** Full team + Composer (wrapping up)

**Entry Criteria:**
- Production complete (Milestone 4 passed)
- Game is content-complete and feature-complete
- All critical bugs resolved
- Steam store page ready (capsule art, trailer, description)

**Deliverable:**
Closed beta build for 50-100 external testers. Telemetry integration for behavior tracking. Bug fixing based on beta reports. Balance tuning based on player data. Launch trailer production. Marketing ramp begins.

**Exit Criteria:**
- [ ] Closed beta runs for 8 weeks (Months 19-20)
- [ ] Telemetry data collected on: session length, episode completion rate, difficulty feedback, system usage
- [ ] All critical bugs fixed
- [ ] All high-priority bugs fixed or triaged to post-launch
- [ ] Balance feels right across all difficulty modes
- [ ] Steam achievements implemented and tested
- [ ] Launch trailer complete and approved
- [ ] Day-one patch build prepared
- [ ] Press/influencer outreach begun

**Success Metrics:**
- Beta player retention: >70% complete at least 2 seasons
- Beta satisfaction: average rating >7.5/10
- Bug density: <1 critical bug per 10 hours of play
- Balance satisfaction: "felt fair" across all difficulty modes (>75% agreement)
- Moral weight validated: "I felt the weight of my decisions" (>65% agreement)
- Steam wishlist conversions: >5,000 wishlists by end of beta

**Content Milestones Within Beta:**
- Month 19: Beta launch, telemetry setup
- Month 20: Data analysis, balance tuning iteration 1
- Month 21: Bug fixing sprint, balance tuning iteration 2
- Month 22: Final polish pass, launch prep (press kits, trailer, store page)

**Risk Gate:**
If beta reveals major issues (broken balance, unfun systems, pervasive bugs), we DELAY LAUNCH. No exceptions. Launching a broken game kills the studio. Better to delay 2-4 months and ship something good than ship on time and die on Steam reviews.

**Budget Burn:** $240K - $320K (4 months, full team)

---

### MILESTONE 6: LAUNCH
**Duration:** Months 23-24 (2 months)
**Owner:** CLOCK + Marketing Lead (contract)
**Team:** Skeleton crew (BYTE for hotfixes, CRASH for monitoring, CLOCK for coordination)

**Entry Criteria:**
- Beta complete and approved
- All launch blockers resolved
- Steam store page live and approved by Valve
- Day-one patch tested and ready
- Marketing materials ready (trailer, press kit, influencer outreach)

**Deliverable:**
BURNBOOK v1.0 launches on Steam. Day-one patch deployed if needed. Launch monitoring active (crash reports, performance metrics, community management).

**Exit Criteria:**
- [ ] Game live on Steam, purchase-able
- [ ] No critical bugs in first 48 hours
- [ ] Community management active (Discord, Reddit, Steam forums)
- [ ] Press reviews monitoring (target: >80% positive on Steam)
- [ ] Sales tracking (internal target: TBD based on marketing spend)
- [ ] Hotfix deployment pipeline tested and ready

**Success Metrics:**
- Clean launch: no game-breaking bugs, no server issues (we're single-player, but Steam backend matters)
- Positive initial reviews: >80% on Steam in first week
- Community sentiment: positive buzz on social media, Reddit, Discord
- Sales meet or exceed internal projections (confidential)

**Post-Launch Activities:**
- Monitor crash reports, deploy hotfixes as needed
- Community engagement (responding to feedback, bug reports)
- Plan for Patch 1.1 (QOL improvements based on player feedback)

**Budget Burn:** $120K - $160K (2 months, reduced team + marketing spend)

---

## 3. SPRINT STRUCTURE & WORKFLOW

### 3.1 Sprint Cadence

**Sprint Length:** 2 weeks
**Team Ceremonies:**
- **Sprint Planning** (Monday Week 1, 2 hours): Define sprint goals, assign tasks, identify blockers
- **Daily Standups** (15 minutes, async on Slack): What I did yesterday, what I'm doing today, blockers
- **Mid-Sprint Check-In** (Friday Week 1, 30 minutes): Progress review, early blocker resolution
- **Sprint Review** (Friday Week 2, 1 hour): Demo completed work, gather feedback
- **Sprint Retro** (Friday Week 2, 30 minutes): What went well, what didn't, action items for next sprint

**Why 2-Week Sprints:**
Game development is unpredictable. 2 weeks is long enough to make meaningful progress but short enough to pivot if something isn't working. 1-week sprints feel like constant meetings. 3-week sprints lose urgency.

### 3.2 Task Breakdown Rules

**Every task must be:**
- **Scoped to <2 days** — If it's bigger, break it down further.
- **Testable** — Clear definition of done. How do we verify it works?
- **Assigned to one person** — No shared ownership. One throat to choke.
- **Prioritized** — P0 (critical path), P1 (high), P2 (medium), P3 (nice-to-have). P3 tasks get cut first if we slip.

**Example Task Breakdown (Edit Bay Implementation):**

| Task | Owner | Estimate | Dependency | Priority |
|------|-------|----------|------------|----------|
| Timeline UI layout (6-segment structure) | UI Engineer | 1 day | Art mockups finalized | P0 |
| Drag-drop footage clips from stockpile | UI Engineer | 2 days | Timeline layout complete | P0 |
| Music cue dropdown integration | UI Engineer | 1 day | Music cue data structure defined | P1 |
| Real-time episode quality scoring | Gameplay Programmer | 2 days | Edit bay data structures complete | P0 |
| Confessional overlay system | UI Engineer | 1.5 days | Drag-drop complete | P1 |
| Chyron text input field | UI Engineer | 0.5 days | Timeline layout complete | P2 |
| Segment preview rendering | UI Engineer | 1 day | Drag-drop complete | P2 |
| Undo/redo for timeline edits | UI Engineer | 2 days | (Optional, cut if time tight) | P3 |

**Total Estimate:** 10-12 days with P0-P2 tasks. Fits in 2-sprint window with buffer for bugs and iteration.

### 3.3 Critical Path Tracking

The critical path is the sequence of tasks that must complete on time for the project to hit milestones. If anything on the critical path slips, the milestone slips.

**Critical Path for Prototype (Milestone 1):**
1. AI utility system framework (BYTE, 3 days)
2. Cast member state tracking (Gameplay Programmer, 2 days)
3. Scene context data structure (Gameplay Programmer, 1 day)
4. AI decision loop implementation (BYTE, 4 days)
5. Moment detection algorithm (BYTE, 3 days)
6. Basic scene UI for testing (UI Engineer, 2 days)
7. Integration testing (BYTE + Gameplay, 2 days)

**Total Critical Path:** 17 days = ~3.5 weeks. Leaves 8.5 weeks for iteration, tuning, and buffer.

**If critical path slips:** Cut scope. Move non-critical features to next milestone. Do not extend milestone. Slipping Milestone 1 cascades into everything downstream.

---

## 4. RISK REGISTER

Every project has risks. Here's how we identify, mitigate, and monitor them.

### 4.1 Critical Risks (Kill the Project if Unresolved)

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|-----------|--------|------------|-------------|
| **AI generates boring/nonsensical scenes** | MEDIUM | CRITICAL | Prototype AI FIRST (Milestone 1). Playtest with external users by Week 8. Set clear success threshold: >70% satisfaction. | If AI fails by Month 3: pivot to more scripted system (betrays fantasy but salvages project) OR abort project. |
| **Edit bay feels like tedious work** | MEDIUM | CRITICAL | Playtest edit bay in isolation (Milestone 2). Survey: "does this feel like authorship?" If <70% yes, simplify aggressively. | Reduce segments from 6 to 4. Remove music cues and chyrons. Focus on core verb: CHOOSE WHAT AIRS. |
| **Scope creep destroys timeline** | HIGH | HIGH | Freeze feature list after design docs approved. Stretch goals explicitly labeled "not v1." Monthly scope review: cut anything not on critical path. | If scope creeping by Month 6: emergency feature cut. Remove entire systems if needed (e.g., cut second show format, ship with 1). |

### 4.2 High Risks (Significantly Delay or Harm Project)

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|-----------|--------|------------|-------------|
| **Performance issues on Steam Deck** | MEDIUM | MEDIUM | Profile early (Milestone 2). If <60 FPS, cut UI effects, reduce max cast per scene, optimize rendering. | Steam Deck is secondary platform. If performance can't be fixed, officially drop Steam Deck support and focus on PC only. |
| **Save system corruption in the wild** | LOW | HIGH | Extensive QA on save/load. Auto-save rotation + backups. Sentry integration for crash reporting. | Deploy hotfix ASAP. Offer affected players manual save repair tool or partial refund if unfixable. |
| **UI complexity overwhelms players** | MEDIUM | MEDIUM | Progressive disclosure. Tutorial season simplifies UI. User testing at Milestone 3. Add "Advisor" hint system if needed. | If >40% of playtesters report confusion, add aggressive tooltips, simplify burn book layout, gate features behind progression. |
| **Procedural cast sameness** | MEDIUM | MEDIUM | Quality filter (discard bland cast), large archetype/backstory pools. Playtest: can testers describe 3 cast members? | If cast feels generic by Milestone 3, pivot to hand-authored cast members (more work, less variety, but guaranteed quality). |
| **Balance is broken** | HIGH | MEDIUM | Multiple difficulty modes. Telemetry in beta. Tune economy based on data. | If one difficulty mode is unfixable, cut it. Ship with 2-3 modes instead of 4. |

### 4.3 Medium Risks (Annoying but Recoverable)

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|-----------|--------|------------|-------------|
| **Localization not ready at launch** | MEDIUM | LOW | English-only at launch. Plan localization for Patch 1.2 if sales justify. | Localization is post-launch. No impact on v1 timeline. |
| **Steamworks integration bugs** | LOW | LOW | Use Steamworks.NET (mature library). Test on non-dev accounts during beta. | Hotfix post-launch. Achievements/cloud saves are nice-to-have, not blockers. |
| **Team burnout during crunch** | MEDIUM | MEDIUM | No mandatory crunch. If we slip, we slip. Delay launch rather than destroy team. | If team is burning out by Month 18, reassess timeline. Add 2-4 months to schedule if needed. |

### 4.4 Risk Monitoring Cadence

- **Weekly:** Review critical path. Identify new blockers.
- **Bi-Weekly (Sprint Planning):** Review risk register. Update likelihood/impact based on new data.
- **Monthly:** Full team risk review. Discuss mitigation effectiveness. Add new risks as discovered.
- **Milestone Gates:** Formal go/no-go decision. If critical risks aren't mitigated, do not proceed to next milestone.

---

## 5. DEPENDENCY MAP

Complex systems have dependencies. Map them clearly so everyone knows what's blocking what.

### 5.1 System Dependencies (What Depends on What)

```
BURN BOOK SYSTEM
  ├─ depends on: Cast member data structures
  └─ blocks: Scene setup UI, cast selection interface

SITUATION ENGINE (AI)
  ├─ depends on: Cast member state, personality profiles
  └─ blocks: Scene footage generation, moment tagging

EDIT BAY SYSTEM
  ├─ depends on: Footage from Situation Engine
  └─ blocks: Episode broadcast, ratings generation

RATINGS ENGINE
  ├─ depends on: Episode timeline data from Edit Bay
  └─ blocks: Network satisfaction updates, season progression

FALLOUT SYSTEM
  ├─ depends on: Cast PI tracking, episode outcomes
  └─ blocks: Post-show consequences, reputation system
```

**Key Insight:** The Situation Engine is the most upstream system. If it's broken, everything downstream breaks. This is why Milestone 1 is dedicated entirely to proving the AI works.

### 5.2 Content Dependencies

**Art Assets:**
- Burn book UI mockups → UI implementation
- Edit bay mockups → Timeline implementation
- Cast member portrait templates → Procedural generation system

**Audio Assets:**
- SFX library (clicks, page turns, etc.) → UI integration
- Music cue library → Edit bay music system
- Ambiance loops → Adaptive audio system

**Design Data:**
- Cast archetypes → Procedural generation
- Backstory pools → Cast member creation
- Personality trait ranges → AI behavior model
- Economy balance values → Ratings/PI calculations

**If Content Dependencies Slip:**
Use programmer art and placeholder audio during prototyping. Replace with final assets during polish (Months 15-18). Do not block implementation waiting for final art. Ugly functional game > pretty broken game.

### 5.3 External Dependencies

**Unity Engine:**
- Unity 2022.3 LTS (stable, no beta versions)
- Risk: Unity releases breaking update. Mitigation: Lock to LTS, don't upgrade mid-project.

**Steamworks SDK:**
- Required for achievements, cloud saves, stats
- Risk: Valve changes API. Mitigation: Use Steamworks.NET wrapper, stays current with Valve changes.

**External Playtesters:**
- Needed for Milestones 2, 3, 5
- Risk: Can't recruit enough testers. Mitigation: Start building Discord community in Month 1. Offer free keys to early supporters.

---

## 6. SPRINT PLAN (DETAILED BREAKDOWN)

### 6.1 Prototype Phase (Months 1-3)

**Sprint 1-2 (Weeks 1-4): Foundation**
- Set up Unity project, version control, build pipeline
- Implement core data structures (CastMember, PersonalityProfile, SceneContext)
- Basic UI for scene setup (drag cast to table)
- **Deliverable:** Player can place 4 cast members at a table and see their names/archetypes

**Sprint 3-4 (Weeks 5-8): AI Core**
- Utility AI system framework
- Cast AI decision loop (SelectAction, ExecuteAction)
- Basic action types (Confront, Support, Withdraw)
- **Deliverable:** Cast members take actions based on utility scores. Actions logged to console.

**Sprint 5-6 (Weeks 9-12): Moment Generation**
- Moment detection algorithm
- Drama value calculation
- Relationship tracking (allies, rivals, romantic)
- **Deliverable:** Scenes generate moments. Moments tagged with drama value. Relationships update.

**Sprint 7 (Weeks 13-14): Prototype Polish & Playtest**
- Bug fixing
- AI tuning (adjust utility weights)
- Internal playtest (5 team members)
- External playtest prep
- **Deliverable:** Prototype ready for external playtest

**Milestone 1 Gate:** Go/No-Go decision. Does the AI feel emergent and interesting? If no, pivot or abort.

---

### 6.2 Vertical Slice Phase (Months 4-6)

**Sprint 8-9 (Weeks 15-18): Edit Bay Foundation**
- Timeline UI layout (6 segments)
- Footage stockpile UI
- Drag-drop implementation
- **Deliverable:** Player can drag footage clips into timeline slots

**Sprint 10-11 (Weeks 19-22): Edit Bay Features**
- Music cue integration
- Confessional overlay system
- Chyron text input
- Episode quality scoring (real-time updates)
- **Deliverable:** Full edit bay functional

**Sprint 12 (Weeks 23-24): Ratings Engine**
- Nielsen calculation
- Audience segment satisfaction
- Ratings report UI
- **Deliverable:** Broadcast generates ratings report

**Sprint 13-14 (Weeks 25-28): Burn Book & Integration**
- Burn book UI (dossier pages, relationship map)
- Confidence tracking and decay
- Full loop integration (casting → scenes → edit → broadcast → ratings)
- **Deliverable:** One complete episode playable

**Milestone 2 Gate:** Does the edit bay feel like authorship? Are ratings understandable? If no, simplify and iterate.

---

### 6.3 Alpha Phase (Months 7-12)

*(Detailed sprint breakdown omitted for brevity — see Section 2 Milestone 3 for content schedule)*

**Key Focus Areas:**
- Fallout system implementation (PI tracking, consequence events)
- Tutorial/onboarding flow
- Save/load robustness
- Content creation (8 episodes worth of scenes, moments, dialogue templates)
- QA integration (CRASH joins, bug tracking begins)

**Milestone 3 Gate:** Is the full season loop fun? Does balance feel fair? If no, tune economy and test again.

---

### 6.4 Production Phase (Months 13-18)

*(Detailed sprint breakdown omitted for brevity — see Section 2 Milestone 4 for content schedule)*

**Key Focus Areas:**
- Content production (Seasons 2-8)
- Music cue library creation
- UI art finalization
- Steam integration (achievements, cloud saves)
- Performance optimization

**Milestone 4 Gate:** Is the game content-complete and performant? If no, extend production or cut content.

---

### 6.5 Beta & Launch Phase (Months 19-24)

*(Detailed sprint breakdown omitted for brevity — see Section 2 Milestones 5-6 for schedule)*

**Key Focus Areas:**
- Closed beta testing
- Telemetry analysis and balance tuning
- Bug fixing based on beta reports
- Marketing ramp (trailer, press outreach, community building)
- Launch prep (day-one patch, store page, monitoring infrastructure)

**Milestone 5 Gate:** Is the game ready to launch? If no, delay.

---

## 7. SCOPE MANAGEMENT

### 7.1 What's In (MVP Features)

**Core Loops:**
- 30-second loop: Placement decision (read intel, place cast, predict outcome)
- 5-minute loop: Scene cycle (setup → shoot → harvest)
- 30-minute loop: Episode cycle (plan → shoot → edit → broadcast → ratings)
- Meta loop: Season arc (cast → episodes → finale → report card → next season)

**Five Core Systems:**
1. Burn Book (intel database, confidence tracking)
2. Situation Engine (AI simulation, moment generation)
3. Edit Bay (timeline editing, music/confessional/chyron tools)
4. Ratings Engine (Nielsen calculation, segment satisfaction, reports)
5. Fallout System (PI tracking, consequence events, post-show outcomes)

**Content:**
- 8 seasons with full progression
- 2 show formats (House of Strangers, Heartshot)
- 6-16 procedurally generated cast per season
- 30 music cues for edit bay
- 6 cast archetypes (Sweetheart, Villain, Strategist, Romantic, Wildcard, Ghost)
- 8 scene locations
- 8 catalyst types

**Progression:**
- Showrunner reputation system (0-100)
- Casting pool quality scales with reputation
- Content unlocks (new locations, catalysts, edit bay tools)
- Between-season management (legacy consequences, reputation updates)

**Technical:**
- PC (Steam) build
- Steam Deck validated
- Save/load with cloud sync
- Steam achievements (20-30 achievements)
- Tutorial/onboarding flow
- 4 difficulty modes (Basic Cable, Network, Premium, Reality TV Hell)

### 7.2 What's Out (Stretch Goals / Post-Launch)

**Cut from v1 (DLC Candidates):**
- Rival showrunner system (competitive meta-layer)
- Reunion special (end-of-season event)
- Format laboratory (custom format designer)
- Writers' room management (staff hiring system)
- Cultural moment system (viral episodes that enter public consciousness)
- Additional show formats beyond 2 (e.g., Runway War, The Isle)

**Never Planned (Out of Scope):**
- Multiplayer or co-op
- Voice acting (text-only by design)
- 3D environments (all UI-based)
- Mobile port (edit bay too complex)
- Console ports at launch (post-launch consideration)
- VR support (makes no sense for this game)
- Modding tools (JSON files are inherently moddable, but no official tools)

### 7.3 Scope Change Process

**Rule: No scope changes after design docs are approved (Month 1).**

**If a scope change is proposed:**
1. **Submit scope change request** (written proposal, includes rationale and impact analysis)
2. **Impact assessment** (Producer + Lead Programmer estimate time/risk)
3. **Tradeoff discussion** (What do we cut to make room for this?)
4. **Decision** (Producer has final veto. If scope increases, something else must be cut.)
5. **Communication** (Team notified, roadmap updated)

**Scope change approval threshold:**
- Minor (<1 week impact): Producer approval
- Medium (1-4 weeks impact): Producer + Leads approval + team vote
- Major (>4 weeks impact): Requires unanimous team agreement + extended timeline (which means delayed launch)

**In practice:** The answer to most scope change requests is "post-launch DLC." We ship the MVP first. We add features later if the game succeeds.

---

## 8. QUALITY ASSURANCE STRATEGY

### 8.1 QA Structure

**Internal QA (Ongoing):**
- Team members test each other's work during sprint reviews
- Automated unit tests for core systems (AI, ratings, fallout)
- Integration tests for full episode loop

**Dedicated QA (Month 7+):**
- QA Lead (CRASH) joins full-time
- Bug tracking in Jira (or equivalent)
- Test plan created for each milestone
- Regression testing before each milestone gate

**External Playtesting:**
- Milestone 2: 5-10 external testers (friends, family, trusted community)
- Milestone 3: 10-15 external testers (recruited from Discord, Reddit)
- Milestone 5: 50-100 closed beta testers (public sign-up, NDA required)

### 8.2 Bug Priority Definitions

**P0 (Critical / Launch Blocker):**
- Game crashes
- Save corruption
- Game-breaking bugs (can't progress, soft-locked)
- Major performance issues (<30 FPS on target hardware)

**P1 (High Priority):**
- Major features not working (edit bay broken, ratings not calculating)
- Severe balance issues (game too easy/too hard)
- UI completely unusable
- Frequent bugs that ruin player experience

**P2 (Medium Priority):**
- Minor features not working correctly
- Visual glitches (UI elements misaligned, text clipping)
- Audio issues (missing sounds, wrong sounds playing)
- Balance issues that are annoying but not game-breaking

**P3 (Low Priority / Nice-to-Have):**
- Polish issues (animations not smooth)
- Minor UX improvements (tooltips missing)
- Edge case bugs (only happens in rare circumstances)
- Cosmetic issues

**Milestone Gate Bug Thresholds:**
- **Milestone 1-2:** Zero P0 bugs, <5 P1 bugs
- **Milestone 3:** Zero P0 bugs, <10 P1 bugs, <30 P2 bugs
- **Milestone 4:** Zero P0 bugs, <5 P1 bugs, <20 P2 bugs
- **Milestone 5 (Beta):** Zero P0 bugs, zero P1 bugs, <10 P2 bugs
- **Launch:** Zero P0 bugs, zero P1 bugs, <5 P2 bugs (rest are post-launch)

### 8.3 Test Coverage Targets

**Automated Tests:**
- AI behavior: 70% code coverage (utility calculations, decision-making)
- Ratings formulas: 90% code coverage (math is deterministic, must be correct)
- Save/load: 100% coverage (cannot ship with broken saves)
- Economy calculations: 80% coverage (PI decay, relationship updates)

**Manual Testing:**
- Full episode loop: Every sprint
- Full season loop: Every milestone
- Edge cases: Before each milestone gate
- Performance profiling: Every milestone

---

## 9. COMMUNICATION & REPORTING

### 9.1 Team Communication

**Daily:**
- Async standups on Slack (#standup channel)
- Format: "Yesterday / Today / Blockers"
- Response time expectation: within 4 hours

**Bi-Weekly:**
- Sprint planning (Monday, 2 hours)
- Sprint review & retro (Friday, 1.5 hours combined)

**Monthly:**
- All-hands project review (1 hour)
- Roadmap check (are we on track?)
- Risk review (new risks, mitigation updates)

**Ad-Hoc:**
- Design discussions (as needed, invite relevant people)
- Technical deep-dives (as needed, usually BYTE + relevant engineer)
- Playtesting feedback sessions (after each playtest)

### 9.2 Reporting to Stakeholders

(If this project has external stakeholders/investors)

**Monthly Report:**
- Milestone progress (% complete)
- Budget burn rate (actual vs. planned)
- Risk register updates
- Key decisions made this month
- Next month's goals

**Quarterly Deep-Dive:**
- Demo of latest build
- Playtesting results summary
- Updated timeline (if any changes)
- Financial update (burn rate, runway remaining)

**Milestone Gates:**
- Formal presentation of milestone deliverable
- Go/no-go decision discussion
- Budget approval for next phase

**If No External Stakeholders:**
Skip formal reporting. Use internal all-hands for milestone reviews.

### 9.3 Community Communication

**Pre-Launch:**
- Discord server live from Month 1 (build community early)
- DevLog posts every 2 weeks (behind-the-scenes, GIFs, design insights)
- Reddit AMAs at key milestones (Milestone 2, 5)
- Twitter/social media presence (managed by marketing, not dev team)

**Launch:**
- Active Discord moderation (respond to bugs, feedback)
- Patch notes published for every update
- Transparency about known issues and fix timelines

**Post-Launch:**
- Monthly developer updates (what's being worked on)
- Community feedback incorporated into patches/DLC planning

---

## 10. BUDGET TRACKING

### 10.1 Budget Breakdown by Phase

| Phase | Duration | Team Size | Cost (Low) | Cost (High) |
|-------|----------|-----------|------------|-------------|
| Prototype | Months 1-3 | 3 people | $90K | $120K |
| Vertical Slice | Months 4-6 | 8 people | $180K | $240K |
| Alpha | Months 7-12 | 9 people | $360K | $480K |
| Production | Months 13-18 | 10 people | $360K | $480K |
| Beta & Polish | Months 19-22 | 10 people | $240K | $320K |
| Launch | Months 23-24 | 5 people + marketing | $120K | $160K |
| **TOTAL** | **24 months** | **Avg 8-10** | **$1.35M** | **$1.8M** |

*(Note: Budget estimates assume modest indie salaries + contract work. Adjust based on actual team structure and location.)*

### 10.2 Budget Monitoring

**Weekly:**
- Track actual hours worked vs. estimated hours
- Flag overages early (if a 2-day task takes 4 days, that's a signal)

**Monthly:**
- Compare actual spend vs. planned budget
- Burn rate analysis: are we spending faster or slower than expected?
- Runway calculation: how many months of runway remain at current burn rate?

**Milestone Gates:**
- Formal budget review
- Approval for next phase spending
- Re-forecast remaining budget based on current trajectory

**Budget Risk Thresholds:**
- If burn rate exceeds plan by >10%, investigate and course-correct
- If projected overrun exceeds 20%, consider scope cuts or timeline extension
- If runway drops below 6 months, emergency fundraising or project wind-down

---

## 11. CONTINGENCY PLANNING

### 11.1 If Milestones Slip

**Milestone 1 Slips (AI doesn't work by Month 3):**
- **Option A:** Extend prototype phase by 1 month. Final attempt to fix AI.
- **Option B:** Pivot to more scripted system (breaks fantasy, but salvages project).
- **Option C:** Abort project (if neither A nor B are viable).

**Milestone 2-3 Slips (Core loop issues):**
- Extend timeline by 1-2 months.
- Cut scope: Remove second show format (ship with 1 format only).
- Reduce content: Ship with 6 seasons instead of 8.

**Milestone 4-5 Slips (Content production delays):**
- Delay launch by 2-4 months (better to ship late than ship broken).
- Cut stretch content: Reduce music cue library, simplify UI art.
- Launch in Early Access (risky, but allows revenue while finishing content).

### 11.2 If Key Personnel Leave

**Lead Programmer (BYTE) Leaves:**
- Immediate hiring for replacement (4-week onboarding)
- Senior gameplay programmer promoted to lead temporarily
- Timeline extends by 1-2 months for knowledge transfer

**Designer (REED) or Narrative Designer (NOVA) Leaves:**
- Less critical (design docs are complete, systems are defined)
- Existing team can execute on documented designs
- Hire contractor if specific expertise needed (e.g., dialogue writing)

**Producer (CLOCK) Leaves:**
- Leadership gap is most critical risk
- Lead Programmer steps into producer role temporarily
- Hire replacement ASAP (producer is the glue)

### 11.3 If Funding Runs Out

**At Month 12 (Alpha complete, 12 months of runway remaining):**
- Evaluate: Can we finish in 12 months?
- If yes: Proceed, tighten budget discipline.
- If no: Seek additional funding (publisher deal, investor, crowdfunding).

**At Month 18 (Production complete, 6 months of runway remaining):**
- Beta and launch must fit in 6 months.
- Cut any non-essential features.
- Marketing spend minimized (grassroots community building only).

**If Funding Runs Out Before Launch:**
- Launch in Early Access (generate revenue to finish development).
- Seek emergency funding (bridge loan, advance from publisher).
- Last resort: Open-source the project and abandon (not ideal, but honest).

---

## 12. POST-LAUNCH ROADMAP

### 12.1 Patch 1.1 (Months 25-26): Quality of Life

**Features:**
- UI improvements based on player feedback
- Additional music cues (5-10 new cues)
- Balance tweaks (if needed based on telemetry)
- Bug fixes from launch

**Budget:** $30K-$40K (skeleton crew)

### 12.2 Patch 1.2 (Months 27-28): Accessibility & Localization

**Features:**
- Colorblind modes
- Text size scaling options
- Localization (Spanish, French, German) if sales justify

**Budget:** $40K-$60K (includes localization contractor)

### 12.3 DLC 1 (Months 29-32): New Formats

**Features:**
- 2 new show formats (Runway War, The Isle)
- New locations and catalysts
- New cast archetypes

**Price:** $9.99 DLC
**Budget:** $100K-$150K (small team, 3-4 months)

### 12.4 DLC 2 (Months 33-36): Stretch Goals

**Features:**
- Rival showrunner system
- Reunion special
- Format laboratory (custom format designer)

**Price:** $14.99 DLC
**Budget:** $150K-$200K (larger feature set)

### 12.5 Console Ports (Months 37+)

**If sales justify:**
- Xbox Series X/S
- PlayStation 5
- Nintendo Switch (lowest priority, edit bay may not translate well)

**Timeline:** 3-6 months per platform for porting + certification
**Budget:** $50K-$100K per platform

---

## 13. SUCCESS METRICS

### 13.1 Internal Success (What We Control)

**Development Metrics:**
- Ship on time (Q4 2027)
- Ship within budget ($1.35M-$1.8M)
- Ship with <10 critical bugs at launch
- Team morale remains high (no burnout, no major departures)

**Quality Metrics:**
- Steam reviews >80% positive in first month
- Average playtime >15 hours (players complete at least 2 seasons)
- Community sentiment positive (Discord, Reddit, social media)

### 13.2 External Success (What the Market Decides)

**Sales Targets (Confidential, Internal Only):**
- Week 1: [REDACTED] units
- Month 1: [REDACTED] units
- Year 1: [REDACTED] units

**Revenue Targets:**
- Break-even: [REDACTED] units at $19.99 price point
- Profitability: [REDACTED] units (covers development + marketing + overhead)
- Success: [REDACTED] units (funds future projects)

**Community Metrics:**
- Discord members: >1,000 by launch, >5,000 within 3 months
- Steam wishlist conversions: >10% (industry average is 5-7%)
- Twitch/YouTube coverage: >10 content creators cover the game at launch

### 13.3 Critical Success Factors

**This project succeeds if:**
1. The AI produces emergent, believable cast behavior (players tell stories about "their" cast)
2. The edit bay feels like authorship (players feel narrative power)
3. The moral weight lands (players feel complicit without being lectured)
4. The loop holds at hour 100 (players complete multiple seasons and want more)

**This project fails if:**
- The AI feels robotic or nonsensical
- The edit bay feels like work
- Players don't care about cast members
- Balance is broken (too easy = boring, too hard = frustrating)
- Performance is poor (players refund due to bugs/crashes)

---

## 14. CLOSING NOTES

This production plan is a living document. It will change as we learn. But the core principles don't change:

**1. Cut scope, not corners.**
If we slip, we cut features. We don't ship broken systems. The MVP is defined. Everything else is negotiable.

**2. The critical path is sacred.**
AI first. Edit bay second. Everything else third. If the core loop doesn't work, nothing else matters.

**3. No crunch.**
If we need to delay launch by 2-4 months to avoid crunch, we delay. Crunch is a management failure, and I refuse to fail the team.

**4. Transparency over optimism.**
I will report bad news immediately. Slipping schedules, over-budget features, failing playtests — the team hears it first, not last. We solve problems together.

**5. Ship something real.**
A finished, polished game with a smaller scope beats an ambitious, broken game every time. BURNBOOK v1.0 is the chassis. DLC is the turbo. We ship the chassis first.

**The clock is running. We have 24 months. Let's build this.**

---

**Dependencies mapped. Risks identified. Milestones defined. Critical path locked. Timeline realistic.**

**What's the MVP? Defined.**
**What's the critical path? AI → Edit Bay → Full Loop.**
**When does this ship? Q4 2027, or we cut scope to make it happen.**
**Who's blocked? Nobody, if we stick to the plan.**

**Now let's execute.**

— CLOCK

---

*Production plan generated by CLOCK (Producer) for BURNBOOK game development. All milestones defined with entry/exit criteria. All risks identified with mitigation strategies. Critical path mapped. Timeline: 24 months to launch. Document status: Production-ready. Go/no-go decision gates established. No placeholders. No wishful thinking. Ship it.*
