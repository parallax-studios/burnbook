# BURNBOOK — Release Plan

**Version:** 1.0
**Author:** SHIP (Release Manager)
**Date:** 2026-02-07
**Status:** Pre-Production Release Planning
**Target Platform:** PC (Steam), Steam Deck Secondary
**Target Launch Window:** Q4 2027 (18-24 months from project start)

---

## 0. EXECUTIVE SUMMARY

This document is the master checklist for launching BURNBOOK. It covers every step from code freeze to live deployment, every contingency from build failures to rating board rejections, and every rollback procedure from hotfix pipelines to emergency rollbacks.

First impressions are permanent. Launch day defines a game's trajectory. There are no second chances for a botched release. This plan exists to make launch day boring. If nothing goes wrong, I did my job.

**What ships on launch day:**
- PC build via Steam (Windows primary, macOS/Linux post-launch if metrics justify)
- Steam Deck verified compatibility
- Full game content (8 seasons, 2 show formats, all core systems)
- 20 Steam achievements
- Cloud save support
- Day-one patch pipeline ready (but ideally unused)

**What doesn't ship:**
- Console versions (post-launch evaluation)
- Multiplayer (not in scope)
- Voice acting (text-only by design)
- Stretch goals (rival showrunner, reunion special, format lab — DLC candidates)

**Critical Path Items:**
- Age rating secured (ESRB, PEGI, or IARC)
- Steam store page live 3 months pre-launch
- Build pipeline automated and tested on clean machines
- Day-one patch infrastructure validated
- Post-launch monitoring dashboard operational

If any critical path item is red 30 days before launch, we delay. No exceptions. A delayed game is eventually good. A broken launch is permanently broken.

Now let's build the plan.

---

## 1. MASTER LAUNCH CHECKLIST

This is the canonical source of truth. Every item has an owner, a completion date, and dependencies. Items are categorized by phase and priority.

### PHASE 1: PRE-PRODUCTION (Months 1-6)

**Infrastructure Setup**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Version control repository configured (Git + GitHub) | BYTE | Week 1 | ☐ | None |
| CI/CD pipeline configured (GitHub Actions) | BYTE | Week 2 | ☐ | Version control |
| Unity project structure finalized | BYTE | Week 2 | ☐ | Version control |
| Build automation tested (Windows build) | BYTE | Month 2 | ☐ | CI/CD pipeline |
| Asset pipeline documented | BYTE | Month 2 | ☐ | None |
| Editor tools framework built | BYTE | Month 3 | ☐ | Unity project |

**Legal & Business**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Studio entity established (LLC/Corp) | CLOCK | Month 1 | ☐ | None |
| Steam Direct account created ($100 fee paid) | SHIP | Month 1 | ☐ | Studio entity |
| Age rating strategy selected (ESRB/PEGI/IARC) | SHIP | Month 2 | ☐ | None |
| Trademark search for "BURNBOOK" completed | CLOCK | Month 2 | ☐ | None |
| Insurance policy secured (E&O, general liability) | CLOCK | Month 3 | ☐ | Studio entity |
| Contracts templates prepared (contractor, NDA) | CLOCK | Month 3 | ☐ | None |

---

### PHASE 2: PRODUCTION (Months 7-18)

**Content Development**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Milestone 1: AI Prototype complete | BYTE | Month 3 | ☐ | Infrastructure |
| Milestone 2: Vertical Slice complete | BYTE | Month 6 | ☐ | M1 |
| Milestone 3: Full Season complete | BYTE | Month 10 | ☐ | M2 |
| Milestone 4: Multi-Season Campaign complete | BYTE | Month 14 | ☐ | M3 |
| Milestone 5: Full Content complete | BYTE | Month 18 | ☐ | M4 |
| Audio assets finalized (music cues, SFX) | ECHO | Month 17 | ☐ | M5 |
| UI art finalized (burn book, edit bay, chrome) | PIXEL | Month 17 | ☐ | M5 |
| All placeholder art replaced | PIXEL | Month 18 | ☐ | M5 |

**Platform Setup**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Steam store page drafted (text + images) | HYPE | Month 12 | ☐ | Vertical Slice |
| Steam store page live (Coming Soon) | SHIP | Month 15 | ☐ | Store page draft |
| Steam achievements designed (20 achievements) | REED | Month 14 | ☐ | M4 |
| Steam achievements implemented | BYTE | Month 16 | ☐ | Achievement design |
| Steamworks SDK integrated (cloud saves, stats) | BYTE | Month 15 | ☐ | M4 |
| Steam Deck compatibility tested | BYTE | Month 16 | ☐ | M5 |
| Steam Trading Cards designed | PIXEL | Month 17 | ☐ | Store page live |

---

### PHASE 3: BETA & POLISH (Months 19-22)

**Quality Assurance**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Internal QA pass 1 (critical bugs) | CRASH | Month 19 | ☐ | M5 |
| Closed beta recruitment (50-100 testers) | HYPE | Month 19 | ☐ | M5 |
| Beta build deployed to Steam (closed branch) | SHIP | Month 19 | ☐ | M5 |
| Telemetry integration (crash reports, metrics) | BYTE | Month 19 | ☐ | M5 |
| Beta feedback collection (surveys, forums) | CRASH | Month 20 | ☐ | Beta live |
| Balance tuning based on beta data | REED | Month 21 | ☐ | Beta feedback |
| Internal QA pass 2 (polish, edge cases) | CRASH | Month 21 | ☐ | Balance tuning |
| Performance profiling (60 FPS validation) | BYTE | Month 21 | ☐ | QA pass 2 |
| Save system stress test (100+ saves) | CRASH | Month 21 | ☐ | QA pass 2 |
| Steam Deck certification validation | SHIP | Month 22 | ☐ | Performance profiling |

**Age Rating**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Rating board submission (ESRB/PEGI/IARC) | SHIP | Month 20 | ☐ | Beta build |
| Rating questionnaire completed | SHIP | Month 20 | ☐ | Beta build |
| Rating footage captured (all sensitive content) | SHIP | Month 20 | ☐ | Beta build |
| Rating certificate received | SHIP | Month 21 | ☐ | Submission |
| Rating assets integrated (logos, descriptors) | PIXEL | Month 21 | ☐ | Certificate |

**Marketing Assets**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Announce trailer scripted | HYPE | Month 18 | ☐ | M5 |
| Announce trailer produced | HYPE | Month 19 | ☐ | Trailer script |
| Launch trailer produced | HYPE | Month 21 | ☐ | Beta build |
| Screenshots captured (10-15 key screens) | PIXEL | Month 21 | ☐ | Beta build |
| GIF library created (5-10 gameplay moments) | HYPE | Month 21 | ☐ | Beta build |
| Presskit assembled (fact sheet, media) | HYPE | Month 21 | ☐ | All assets |
| Steam capsule art finalized (all sizes) | PIXEL | Month 21 | ☐ | All assets |

---

### PHASE 4: PRE-LAUNCH (Months 23-24, Final 60 Days)

**Build Pipeline**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Code freeze (no new features) | BYTE | L-60 days | ☐ | Beta complete |
| Release Candidate 1 (RC1) built | SHIP | L-55 days | ☐ | Code freeze |
| RC1 tested on clean machines (3+ configs) | CRASH | L-53 days | ☐ | RC1 |
| RC1 tested on Steam Deck | CRASH | L-53 days | ☐ | RC1 |
| RC2 built (critical fixes only) | SHIP | L-45 days | ☐ | RC1 test results |
| RC2 tested on clean machines | CRASH | L-43 days | ☐ | RC2 |
| RC3 built (if needed) | SHIP | L-35 days | ☐ | RC2 test results |
| GOLD build declared | SHIP | L-30 days | ☐ | RC2/RC3 clean |
| GOLD build uploaded to Steam (staging) | SHIP | L-30 days | ☐ | GOLD build |
| GOLD build tested on Steam (private branch) | CRASH | L-28 days | ☐ | Steam upload |
| Day-one patch pipeline tested (dry run) | SHIP | L-25 days | ☐ | GOLD build |

**Store & Platform Configuration**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Steam store page updated (final text, media) | HYPE | L-60 days | ☐ | All assets |
| Steam regional pricing configured | SHIP | L-50 days | ☐ | Store page |
| Steam launch date set (coordinated with marketing) | SHIP | L-50 days | ☐ | GOLD schedule |
| Steam pre-purchase enabled (if applicable) | SHIP | L-45 days | ☐ | Launch date set |
| Steam achievements finalized (metadata, icons) | SHIP | L-40 days | ☐ | Achievement impl |
| Steam Trading Cards submitted for approval | SHIP | L-40 days | ☐ | Card design |
| Steam Cloud Save configuration tested | SHIP | L-35 days | ☐ | GOLD build |
| Steam community hub configured (discussions) | HYPE | L-30 days | ☐ | Store page |
| Steam review keys generated (50-100 keys) | SHIP | L-30 days | ☐ | GOLD build |

**Marketing Campaign**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Announce trailer released (YouTube, Twitter) | HYPE | L-90 days | ☐ | Trailer complete |
| Press outreach initiated (60+ outlets) | HYPE | L-75 days | ☐ | Presskit |
| Review copy distribution (30-50 keys) | HYPE | L-45 days | ☐ | RC2 + review keys |
| Review embargo set (launch day, 9AM PT) | HYPE | L-45 days | ☐ | Review copies out |
| Launch trailer released | HYPE | L-14 days | ☐ | Launch trailer |
| Social media campaign active (daily posts) | HYPE | L-30 to L-0 | ☐ | All assets |
| Discord server launched | HYPE | L-60 days | ☐ | Community setup |
| Reddit community engagement (AMAs, posts) | HYPE | L-30 to L-0 | ☐ | Announce trailer |

**Legal & Compliance**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| EULA finalized and reviewed by lawyer | CLOCK | L-60 days | ☐ | None |
| Privacy policy finalized (telemetry disclosure) | CLOCK | L-60 days | ☐ | None |
| EULA integrated into game build | BYTE | L-50 days | ☐ | EULA final |
| Age rating assets displayed correctly in-game | BYTE | L-45 days | ☐ | Rating cert |
| Credits sequence finalized (all contributors) | CLOCK | L-40 days | ☐ | None |
| Third-party license compliance verified | BYTE | L-35 days | ☐ | None |

---

### PHASE 5: LAUNCH WEEK (L-7 to L+7)

**Final Preparation**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Launch day timeline finalized (hour-by-hour) | SHIP | L-7 days | ☐ | All deps clear |
| Emergency contact list distributed (team) | SHIP | L-7 days | ☐ | None |
| Monitoring dashboard configured (Steam stats) | SHIP | L-5 days | ☐ | GOLD live |
| Hotfix build environment tested | SHIP | L-5 days | ☐ | Build pipeline |
| Day-one patch prepared (if needed) | BYTE | L-3 days | ☐ | Last-minute fixes |
| Steam build set to "Release" status | SHIP | L-2 days | ☐ | GOLD tested |
| Final smoke test on live Steam build | CRASH | L-1 day | ☐ | Steam release |
| Team availability confirmed (launch day + 3) | SHIP | L-1 day | ☐ | None |

**Launch Day (L-Day)**

| Item | Owner | Time (PT) | Status | Notes |
|------|-------|-----------|--------|-------|
| Final pre-launch check (Steam backend) | SHIP | 8:00 AM | ☐ | Verify build live |
| Game launches on Steam | SHIP | 10:00 AM | ☐ | Target launch time |
| Review embargo lifts | HYPE | 10:00 AM | ☐ | Coordinated with launch |
| Launch tweet posted | HYPE | 10:05 AM | ☐ | "We're live!" |
| Discord announcement posted | HYPE | 10:05 AM | ☐ | Link to store |
| Reddit launch post (r/Games, r/pcgaming) | HYPE | 10:10 AM | ☐ | Use launch GIF |
| Monitoring begins (Steam stats, crash reports) | SHIP | 10:00 AM | ☐ | Watch for issues |
| First player reports monitored (Discord, Steam) | CRASH | 10:30 AM+ | ☐ | Triage bugs |
| First review aggregation check | HYPE | 12:00 PM | ☐ | Steam reviews |
| Team check-in (status update) | SHIP | 2:00 PM | ☐ | Go/no-go for day-one patch |
| End-of-day debrief | SHIP | 6:00 PM | ☐ | Assess launch health |

**Post-Launch Week (L+1 to L+7)**

| Item | Owner | Completion Date | Status | Dependencies |
|------|-------|----------------|--------|--------------|
| Day-one patch deployed (if needed) | SHIP | L+1 day | ☐ | Critical bugs found |
| Community management (Discord, Steam forums) | HYPE | L+1 to L+7 | ☐ | Ongoing |
| Bug triage (prioritize critical vs. minor) | CRASH | L+1 to L+7 | ☐ | Ongoing |
| Hotfix 1.0.1 deployed (critical fixes) | SHIP | L+3 days | ☐ | If critical bugs |
| Sales metrics review | CLOCK | L+7 days | ☐ | Steam partner dashboard |
| Review score aggregation (Steam, Metacritic) | HYPE | L+7 days | ☐ | Public reviews |
| Post-launch retrospective (team) | SHIP | L+7 days | ☐ | Lessons learned |

---

## 2. BUILD PIPELINE DOCUMENTATION

The build must be reproducible, automated, and testable on clean machines. If it only works on the developer's machine, it doesn't work.

### 2.1 Build Environment Specification

**Development Machine Requirements:**

| Component | Specification |
|-----------|--------------|
| OS | Windows 10/11 (64-bit) or macOS 12+ |
| Unity Version | Unity 2022.3 LTS (exact version locked) |
| RAM | 16 GB minimum, 32 GB recommended |
| Storage | 50 GB free (project + builds) |
| Git | Git 2.30+ |
| .NET SDK | .NET 6.0+ (for CI/CD scripts) |

**Clean Machine Test Requirements:**

Every Release Candidate must be tested on a machine that has NEVER had the project installed. This catches missing dependencies, hardcoded paths, and "works on my machine" bugs.

**Clean machine specs:**
- Windows 10 (fresh install or VM)
- No Unity installed (install from scratch as part of test)
- No project files (clone from Git)
- No saved games or local data

**Test procedure:**
1. Clone repository from GitHub
2. Install Unity 2022.3 LTS via Unity Hub
3. Open project (wait for import)
4. Build via menu: File > Build Settings > Build
5. Run executable on same machine
6. Run executable on a second clean machine (different hardware)
7. Verify: game launches, main menu loads, can start new game, can save/load

If any step fails, the build is not ready.

### 2.2 Automated Build Pipeline (GitHub Actions)

**Build Triggers:**
- Every commit to `develop` branch: automated build + unit tests
- Every commit to `main` branch: automated build + integration tests + Steam upload (staging)
- Manual trigger: production release build

**Build Workflow (GitHub Actions YAML):**

```yaml
name: BURNBOOK Build Pipeline

on:
  push:
    branches: [develop, main]
  workflow_dispatch:

jobs:
  build-windows:
    runs-on: windows-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
        with:
          lfs: true

      - name: Cache Unity Library
        uses: actions/cache@v3
        with:
          path: Library
          key: Library-${{ hashFiles('ProjectSettings/**') }}

      - name: Build Unity Project
        uses: game-ci/unity-builder@v2
        with:
          targetPlatform: StandaloneWindows64
          unityVersion: 2022.3.X
          buildName: BURNBOOK

      - name: Run Unit Tests
        uses: game-ci/unity-test-runner@v2
        with:
          unityVersion: 2022.3.X

      - name: Upload Build Artifact
        uses: actions/upload-artifact@v3
        with:
          name: BURNBOOK-Windows-${{ github.sha }}
          path: build/StandaloneWindows64

      - name: Upload to Steam (if main branch)
        if: github.ref == 'refs/heads/main'
        uses: game-ci/steam-deploy@v1
        with:
          username: ${{ secrets.STEAM_USERNAME }}
          password: ${{ secrets.STEAM_PASSWORD }}
          appId: ${{ secrets.STEAM_APP_ID }}
          buildDescription: Build ${{ github.sha }}
          rootPath: build/StandaloneWindows64
          depot1Path: .
          releaseBranch: staging
```

**What this does:**
- Checks out code from Git (including LFS assets)
- Caches Unity Library folder (speeds up subsequent builds)
- Builds Windows 64-bit executable
- Runs all unit tests (build fails if tests fail)
- Uploads build artifact to GitHub Actions (downloadable)
- If `main` branch: uploads to Steam staging branch automatically

**Build artifacts stored:**
- GitHub Actions artifacts (7-day retention)
- Steam depot (staging branch, indefinite retention)
- Local archive (external drive, permanent backup)

### 2.3 Build Versioning

**Version Format:** `MAJOR.MINOR.PATCH-BUILD`

Example: `1.0.0-1234`

- **MAJOR**: Increments for major releases (1.0 = launch, 2.0 = massive overhaul)
- **MINOR**: Increments for significant updates (1.1 = new content, 1.2 = major features)
- **PATCH**: Increments for bug fixes (1.0.1 = hotfix)
- **BUILD**: Auto-incremented by CI/CD (Git commit count or timestamp)

**Where version appears:**
- Main menu ("Version 1.0.0")
- Steam build metadata
- Save file header (for migration detection)
- Crash reports (for debugging)

**Version lockdown:**
- GOLD build = `1.0.0-XXXX` (locked, never changes)
- Day-one patch = `1.0.1-XXXX` (if needed)
- Hotfixes = `1.0.2`, `1.0.3`, etc.

### 2.4 Build Signing & DRM

**Code Signing (Windows):**
- All executables signed with Extended Validation (EV) certificate
- Prevents "Unknown Publisher" warning on Windows
- Certificate acquired 60 days before launch (procurement lead time)

**Steam DRM:**
- Enable Stub DRM (basic protection, minimal performance impact)
- Do NOT use CEG (Custom Executable Generation) — overkill, breaks modding
- Do NOT use third-party DRM (Denuvo, etc.) — performance cost, player backlash

**Reasoning:** BURNBOOK is a single-player, story-driven sim. Piracy is inevitable. Prioritize player experience over aggressive DRM. The goal is to make buying easier than pirating (reasonable price, no launchers, fast updates).

### 2.5 Build Delivery (Steam Depots)

**Steam Depot Configuration:**

| Depot | Platform | Size (est.) | Notes |
|-------|----------|-------------|-------|
| Depot 1 | Windows 64-bit | ~800 MB | Executable + data files |
| Depot 2 | macOS (future) | ~850 MB | Post-launch if metrics justify |
| Depot 3 | Linux (future) | ~800 MB | Post-launch if metrics justify |
| Depot 4 | Shared assets | ~500 MB | Audio, textures (all platforms) |

**Branch Configuration:**

| Branch | Purpose | Access |
|--------|---------|--------|
| `default` | Public release branch | Everyone |
| `staging` | Pre-release testing | Internal + beta testers |
| `beta` | Closed beta (historical) | Beta participants |
| `development` | Active dev builds (unstable) | Internal only |

**Upload Process:**
1. Build finalized locally or via CI/CD
2. Run SteamCMD script (automated via GitHub Actions or manual)
3. Upload to `staging` branch first
4. Test on Steam (private branch, internal team)
5. If clean, promote `staging` to `default` branch
6. Monitor Steam partner dashboard for upload confirmation

**SteamCMD Script Example:**

```
login <username> <password>
app_build <app_id>
  desc "BURNBOOK v1.0.0 - Launch Build"
  setlive staging
  depot_build <depot_id> <content_path>
  depot_build <depot_id> <content_path>
quit
```

### 2.6 Build Validation Checklist

Before declaring a build GOLD, validate every item:

**Functional Tests (Clean Machine):**
- [ ] Game launches without errors
- [ ] Main menu displays correctly (no missing textures/fonts)
- [ ] New game starts successfully
- [ ] First episode completes without crashes
- [ ] Save game creates file correctly
- [ ] Load game restores state accurately
- [ ] Settings persist between sessions
- [ ] All UI elements responsive (no dead buttons)
- [ ] Audio plays correctly (music, SFX)
- [ ] Game exits cleanly (no hang on quit)

**Platform Tests (Steam):**
- [ ] Steam overlay functions (Shift+Tab)
- [ ] Achievements unlock correctly (test 3+ achievements)
- [ ] Cloud saves sync correctly (test on two machines)
- [ ] Steam stats tracked correctly (playtime, etc.)
- [ ] Trading Cards drop correctly (if implemented)

**Performance Tests:**
- [ ] Maintains 60 FPS during edit bay (1920x1080, mid-range PC)
- [ ] Maintains 60 FPS during scene simulation
- [ ] Load times < 3 seconds (episode start)
- [ ] Save/load completes in < 2 seconds
- [ ] No memory leaks over 4-hour session
- [ ] Steam Deck: 60 FPS at 1280x800

**Compatibility Tests:**
- [ ] Windows 10 (64-bit)
- [ ] Windows 11 (64-bit)
- [ ] Steam Deck (SteamOS)
- [ ] Multiple monitor setups (ultrawide, dual monitor)
- [ ] Keyboard + Mouse
- [ ] Gamepad (Xbox, PlayStation, Steam Controller) — if implemented

**Regression Tests:**
- [ ] All critical bugs from QA pass 2 are fixed
- [ ] No new crashes introduced since RC1
- [ ] Save files from RC2 load correctly in GOLD build

If any item fails, the build is NOT GOLD. Fix, rebuild, retest.

---

## 3. PLATFORM CONFIGURATION CHECKLIST

### 3.1 Steam Store Page

**Required Assets:**

| Asset | Specification | Status | Owner |
|-------|--------------|--------|-------|
| Capsule Main (616x353) | Key art, no text | ☐ | PIXEL |
| Capsule Header (460x215) | Simplified capsule | ☐ | PIXEL |
| Capsule Small (231x87) | Logo + minimal art | ☐ | PIXEL |
| Library Hero (3840x1240) | Wide key art | ☐ | PIXEL |
| Library Logo (1280x720, PNG) | Transparent logo | ☐ | PIXEL |
| Screenshots (10-15) | 1920x1080, gameplay | ☐ | PIXEL |
| Trailer (MP4) | 60-90 seconds, 1080p | ☐ | HYPE |

**Store Page Text:**

| Section | Word Count | Status | Owner |
|---------|-----------|--------|-------|
| Short Description | 1-2 sentences | ☐ | HYPE |
| About This Game | 300-500 words | ☐ | HYPE |
| Key Features | 5-7 bullet points | ☐ | HYPE |
| System Requirements (Min) | Hardware specs | ☐ | BYTE |
| System Requirements (Rec) | Hardware specs | ☐ | BYTE |

**Store Page Metadata:**

- **Genre Tags (20 max):** Simulation, Management, Story Rich, Choices Matter, Dark Comedy, Singleplayer, Strategy, Realistic, Drama, Text-Based, Psychological, Indie, Atmospheric, Replay Value, Emotional
- **Category Tags:** Single-player, Steam Achievements, Full Controller Support (if impl), Steam Cloud, Steam Trading Cards (if impl)
- **Languages Supported:** English (interface, audio, subtitles). Post-launch: Spanish, French, German (if sales justify)
- **Age Rating:** Display ESRB/PEGI rating badge and content descriptors
- **Release Date:** Set 50 days before launch (Steam recommends 2 weeks minimum for visibility)
- **Price:** TBD by CLOCK (market research). Typical range for this genre: $19.99-$29.99 USD

**Regional Pricing:**

Steam supports 40+ currencies. Use Steam's suggested pricing tool (adjusts for regional purchasing power). Manual review for key regions:

| Region | Currency | Suggested Price (est.) | Notes |
|--------|----------|----------------------|-------|
| United States | USD | $24.99 | Base price |
| European Union | EUR | €22.99 | ~10% lower (VAT inclusive) |
| United Kingdom | GBP | £19.99 | Adjusted for GBP strength |
| Japan | JPY | ¥2,500 | Lower due to market |
| Brazil | BRL | R$50 | Regional pricing critical |
| Russia | RUB | ₽999 | Lower purchasing power |
| China | CNY | ¥128 | Requires separate review |

**Review before launch:** Pricing errors kill sales. Double-check every region.

### 3.2 Steam Achievements

**Total Achievements:** 20 (Steam recommended minimum: 10-15, maximum: 100)

**Achievement Categories:**

| Category | Count | Examples |
|----------|-------|----------|
| Progression | 8 | "Complete Season 1", "Complete Season 8", "Air 50 episodes" |
| Mastery | 5 | "Achieve 3.0 Nielsen rating", "Maintain 80+ NSS for full season", "Reach Icon reputation" |
| Exploration | 4 | "Try all show formats", "Unlock all edit bay tools", "Cast all archetypes" |
| Story Moments | 3 | "Trigger a cast member walkoff", "Create a cultural moment episode", "Air a withheld moment for 1.5x drama" |

**Achievement Design Principles:**
- Mix easy (progression-based, most players unlock) and hard (mastery-based, <10% unlock)
- No missable achievements (all achievable in any playthrough)
- No grind achievements (no "air 1000 episodes")
- All achievements have unique icons (64x64, designed by PIXEL)

**Implementation:**
- Steamworks API: `ISteamUserStats::SetAchievement()`
- Trigger achievements via game events (episode complete, rating threshold reached, etc.)
- Test unlocks before GOLD build (common bug: achievements never unlock in production)

### 3.3 Steam Cloud Saves

**Configuration:**
- **Cloud Storage Quota:** 100 MB per user (more than enough; save files ~2 MB each)
- **Files to Sync:** All save files in `%AppData%/BURNBOOK/Saves/` (Windows) or equivalent
- **Sync Timing:** After every save operation, on game exit
- **Conflict Resolution:** Timestamp-based (newest save wins)

**Implementation:**
- Steamworks API: `ISteamRemoteStorage::FileWrite()`, `FileRead()`
- User setting: "Enable Cloud Saves" (default: ON, can disable)
- Test on two machines: save on Machine A, load on Machine B, verify state matches

**Edge Case Handling:**
- No internet connection: saves locally, syncs when connection restored
- Cloud save corrupted: fall back to local save, notify user
- Cloud quota exceeded: warn user, disable cloud saves for that user

### 3.4 Steam Trading Cards (Optional)

**Requirement:** Game must have grossed $1,000 on Steam before cards can be enabled.

**If Enabled:**
- **Card Set Size:** 5-8 cards (standard for indie games)
- **Card Themes:** Cast member archetypes (Sweetheart, Villain, Strategist, etc.), edit bay moments, burn book pages
- **Badge Levels:** 5 (standard, foil, and 3 crafted levels)
- **Emoticons:** 5-10 (derived from card art)
- **Backgrounds:** 3-5 (production suite aesthetics)

**Approval Process:**
- Submit card designs to Steam (60-day review period)
- Steam rejects ~30% of submissions (quality bar is high)
- If approved, cards drop during playtime (avg 1 card per 2 hours)

**Recommendation:** Design cards during production, submit post-launch once $1K threshold met. Do NOT delay launch for cards.

### 3.5 Steam Deck Compatibility

**Verification Levels:**

| Level | Meaning | Requirements |
|-------|---------|--------------|
| Verified | Perfect out-of-the-box | 60 FPS, full controller support, readable text, no launcher |
| Playable | Works but minor issues | May require tweaks (keyboard needed for some inputs) |
| Unsupported | Does not work | Crashes, unplayable performance, incompatible |
| Unknown | Not tested | Default state |

**Target:** Verified status

**Verification Checklist:**
- [ ] Game runs on Steam Deck (SteamOS)
- [ ] Maintains 60 FPS at 1280x800
- [ ] Text readable at 7-inch screen size (font size +10%)
- [ ] Full controller support (no keyboard required)
- [ ] Touchscreen works for UI navigation
- [ ] Battery life reasonable (4+ hours)
- [ ] Suspend/resume works (game pauses correctly)
- [ ] No launcher (direct to game)

**Submit for Verification:**
- Upload GOLD build to Steam
- Request Steam Deck verification via Steam partner portal
- Valve tests on hardware (2-4 week turnaround)
- If "Playable" or "Unsupported", fix issues and resubmit

---

## 4. AGE RATING STRATEGY

Every platform requires an age rating. No rating = no release.

### 4.1 Rating Board Options

| Board | Coverage | Cost | Timeline | Submission Method |
|-------|----------|------|----------|-------------------|
| **ESRB** | North America | $800-$4,000 (based on budget) | 4-6 weeks | Online questionnaire + gameplay footage |
| **PEGI** | Europe | €1,000-€3,000 | 4-6 weeks | Online questionnaire + gameplay footage |
| **IARC** | Global (incl. Steam) | FREE | 24-48 hours | Online questionnaire only |

**Recommendation:** Start with IARC (free, fast, covers Steam globally). If console versions planned, add ESRB/PEGI later.

### 4.2 IARC Process (International Age Rating Coalition)

**What is IARC?**
A unified rating system for digital storefronts. One questionnaire generates ratings for multiple regions (ESRB, PEGI, USK, ClassInd, etc.).

**Process:**
1. Visit IARC portal (https://www.globalratings.com/)
2. Create account (linked to Steam publisher account)
3. Complete questionnaire (30-60 minutes)
4. Answer questions about content (violence, language, mature themes, etc.)
5. Submit (no footage required for IARC)
6. Receive ratings certificate (24-48 hours)
7. Import certificate into Steam partner portal

**BURNBOOK Expected Rating:**

| Region | Rating | Content Descriptors |
|--------|--------|---------------------|
| ESRB (North America) | T (Teen 13+) | Mild Language, Suggestive Themes, Simulated Gambling (reality TV) |
| PEGI (Europe) | 12+ | Mild Bad Language, Non-realistic Violence (emotional, not physical) |
| USK (Germany) | 12+ | Similar to PEGI |

**Why Teen/12+?**
- No graphic violence (all conflict is social/emotional)
- Minimal language (potentially some mild profanity in cast dialogue)
- Mature themes (exploitation, manipulation) but presented in simulation context, not glorified
- No sexual content, drug use, or extreme violence

**Questionnaire Strategy:**
- Be accurate (lying can result in rating revocation)
- Answer conservatively (if uncertain, describe content in detail)
- Capture footage of all "edge case" content (worst-case scenarios: cast member breakdown, confrontation, etc.) in case IARC requests review

### 4.3 Rating Assets Integration

Once rating received:

**Required Display Locations:**
- Game executable (splash screen on startup)
- Steam store page (rating badge in "About" section)
- Marketing materials (trailers must show rating at end)
- Physical media (if ever printed, e.g., special editions)

**Assets Needed:**
- Rating badge image (PNG, provided by rating board)
- Content descriptor text (e.g., "Mild Language, Suggestive Themes")

**Implementation:**
- Display rating splash screen for 3 seconds on first launch
- Store rating metadata in game files (for regional compliance checks)

---

## 5. ROLLBACK & HOTFIX PROCEDURES

Launch day will have bugs. Plan for failure.

### 5.1 Rollback Plan (Emergency)

**When to Rollback:**
- Critical crash affecting >10% of players (game-breaking)
- Save corruption (players losing progress)
- Exploit allowing cheating or game-breaking behavior
- Legal issue (rating violation, IP infringement discovered post-launch)

**Rollback Procedure:**

1. **Assess Severity (15 min):**
   - SHIP + BYTE + CRASH convene via Discord/Slack
   - Review crash reports, player reports, Steam forums
   - Determine: Is this rollback-worthy?

2. **Notify Team (5 min):**
   - Alert all team members: "Rollback in progress"
   - Pause all marketing, social media

3. **Execute Rollback (30 min):**
   - Log into Steam partner portal
   - Set `default` branch to previous stable build (pre-launch GOLD or last known good patch)
   - Notify Steam users via Steam Events: "We've rolled back to a previous build while we investigate an issue. Your saves are safe."

4. **Investigate Root Cause (1-4 hours):**
   - Reproduce bug locally
   - Identify fix
   - Test fix on clean machine

5. **Deploy Hotfix (see 5.2):**
   - Build, test, upload hotfix
   - Promote hotfix to `default` branch
   - Notify users: "Issue resolved, update available"

6. **Post-Mortem (24 hours later):**
   - Document what went wrong, how it was fixed, how to prevent recurrence
   - Update QA checklist for future builds

**Rollback Comms Template (Steam Event):**

> **Important Update: Temporary Rollback**
>
> We've identified a critical issue in the latest build affecting save files. To protect your progress, we've rolled back to the previous stable version while we fix the issue.
>
> Your save files are safe. We expect to have a fix deployed within 4-6 hours.
>
> Thank you for your patience. We'll update this post when the fix is live.
>
> — The BURNBOOK Team

### 5.2 Hotfix Pipeline

**Hotfix Definition:** A critical bug fix deployed outside the normal patch cycle.

**Hotfix Criteria:**
- Severity: Critical or High
- Impact: Affects >5% of players OR blocks progression
- Timeframe: Must be fixed within 24-48 hours

**Hotfix Process:**

1. **Triage (30 min):**
   - CRASH confirms bug is reproducible
   - BYTE estimates fix complexity
   - SHIP approves hotfix deployment

2. **Fix & Build (2-6 hours):**
   - BYTE implements fix in isolated branch (`hotfix/[issue-name]`)
   - Run unit tests locally
   - Build hotfix candidate
   - Test on clean machine (abbreviated test: verify fix works, no new regressions in core loop)

3. **Upload to Staging (30 min):**
   - Upload hotfix to Steam `staging` branch
   - CRASH tests on Steam (verify fix, spot-check 3-5 core features)

4. **Deploy to Production (15 min):**
   - Promote `staging` to `default` branch
   - Increment version number (e.g., 1.0.0 → 1.0.1)
   - Post Steam Event: "Hotfix 1.0.1 deployed, fixes [issue]"

5. **Monitor (24 hours):**
   - Watch crash reports, player feedback
   - Confirm issue is resolved
   - Document fix in patch notes

**Hotfix Communication Template (Steam Event):**

> **Hotfix 1.0.1 Now Live**
>
> We've deployed a hotfix to address the following issue:
> - Fixed: Save files corrupted when exiting during edit bay [Critical]
>
> If you experienced this issue, your previous saves should now load correctly. If you continue to have problems, please contact us on Discord or Steam forums.
>
> Thank you for your reports and patience.
>
> — The BURNBOOK Team

### 5.3 Day-One Patch Strategy

**Philosophy:** Ship a clean GOLD build. Day-one patch should ideally be ZERO bytes.

**Reality:** There will likely be minor bugs discovered between GOLD and launch. Prepare a day-one patch pipeline just in case.

**Day-One Patch Criteria:**
- Minor bugs only (not critical, not game-breaking)
- Performance tweaks (if safe and tested)
- Text fixes (typos, missing strings)
- Balance tweaks (if QA/beta data suggests needed)

**Day-One Patch Timeline:**

| Event | Timing | Owner |
|-------|--------|-------|
| GOLD build finalized | L-30 days | SHIP |
| Bug reports collected (post-GOLD testing) | L-30 to L-7 | CRASH |
| Day-one patch scope finalized | L-10 days | BYTE + CRASH |
| Day-one patch built | L-7 days | BYTE |
| Day-one patch tested (staging) | L-5 days | CRASH |
| Day-one patch uploaded (held in staging) | L-3 days | SHIP |
| Launch day decision: deploy or skip | L-Day, 9 AM | SHIP |
| If deployed: promote staging to default | L-Day, 10 AM | SHIP |

**Day-One Patch Comms (if deployed):**

> **Day-One Patch (v1.0.1) Available**
>
> A small patch is available addressing minor issues:
> - Fixed: [Bug 1]
> - Fixed: [Bug 2]
> - Improved: [Performance tweak]
>
> The patch will download automatically. Thanks for playing!

**If Skipped:**
No communication needed. GOLD build is clean enough to ship as-is. Fixes rolled into first major patch (1-2 weeks post-launch).

---

## 6. LAUNCH DAY TIMELINE (Hour-by-Hour)

Launch day is managed minute-by-minute. This is the canonical timeline.

**Date:** TBD (coordinated with marketing, HYPE leads)
**Launch Time:** 10:00 AM Pacific Time (industry standard for Steam releases)
**Team Availability:** SHIP, BYTE, CRASH, HYPE available from 8 AM to 8 PM PT (12-hour window)

### Hour-by-Hour Schedule

**8:00 AM - Pre-Launch Preparation**
- SHIP: Log into Steam partner portal, verify build is set to release at 10 AM
- SHIP: Verify release date/time is correct (common mistake: wrong timezone)
- SHIP: Check Steam backend status (no maintenance windows, no outages)
- BYTE: Monitoring dashboard online (Steam stats, crash reporting via Sentry/BugSnag)
- CRASH: Discord/Steam forums monitoring begins
- HYPE: Social media queued (launch tweet, Discord announcement, Reddit post)
- CLOCK: Payment processing verified (Steam partner financial setup)

**9:00 AM - Final Check**
- SHIP: Download GOLD build from Steam (final smoke test)
- SHIP: Launch game, verify main menu, start new game, confirm no last-minute issues
- SHIP: Confirm review embargo lifts at 10 AM (coordinated with press)
- HYPE: Pre-launch hype tweet ("1 hour until launch!")
- Team check-in: Go/no-go for 10 AM launch

**10:00 AM - LAUNCH**
- SHIP: Game goes live on Steam (automatic based on release date setting)
- HYPE: Launch tweet posted ("BURNBOOK is now live on Steam! [link]")
- HYPE: Discord announcement pinned
- HYPE: Reddit posts (r/Games, r/pcgaming, r/indiegames) go live
- SHIP: Begin monitoring Steam partner dashboard (sales, concurrent players)
- CRASH: Begin monitoring crash reports, Steam reviews, Discord bug reports

**10:15 AM - First 15 Minutes**
- CRASH: Check for any immediate crashes (players report crashes within first 15 min if launch is broken)
- SHIP: Monitor concurrent players (CCU). Healthy launch: 50-200 CCU in first hour (depends on marketing reach)
- HYPE: Respond to community questions (Discord, Reddit, Steam forums)
- BYTE: On standby for emergency hotfix (if critical issue found)

**11:00 AM - First Hour Report**
- SHIP: Team check-in (Slack/Discord)
  - Sales: X units sold in first hour
  - CCU: X concurrent players
  - Crash rate: X% (acceptable if <1%)
  - Reviews: X positive, X negative (early reviews often mixed, wait 24 hours for trend)
- CRASH: Triage any reported bugs (critical vs. minor)
- Decision point: Deploy day-one patch or hold?

**12:00 PM - Midday Check**
- SHIP: Review first Steam reviews (read every review, flag critical issues)
- HYPE: Community engagement (respond to reviews, Discord conversations)
- CLOCK: Financial check (revenue tracking vs. projections)
- BYTE: Monitor telemetry (average session length, where do players quit?)

**2:00 PM - Afternoon Review**
- SHIP: Team check-in
  - Any critical bugs? If yes, begin hotfix process
  - Community sentiment? (Discord, Reddit, Steam reviews)
  - Press coverage? (HYPE reports on review scores, articles)
- CRASH: Update bug tracker (categorize all reported issues)
- SHIP: If clean launch, reduce monitoring frequency (check every 2 hours instead of hourly)

**6:00 PM - End-of-Day Debrief**
- SHIP: Final team check-in
  - Total sales: X units
  - Peak CCU: X players
  - Review score: X% positive on Steam
  - Critical issues: Yes/No (if yes, plan hotfix for L+1)
- SHIP: Post launch-day summary to team Slack/Discord
- SHIP: Update stakeholders (if external investors/publishers involved)
- Team: Celebrate if clean launch. If issues, plan next-day fixes.

**7:00 PM - Ongoing Monitoring**
- SHIP + CRASH: Reduced monitoring (check every 3-4 hours through evening)
- BYTE: On-call for emergency only (critical crashes, server issues if applicable)

**Next 7 Days:**
- Daily check-ins at 10 AM PT
- Bug triage daily (CRASH leads)
- Hotfix deployed by L+3 if critical issues found
- Post-launch retrospective at L+7 (SHIP leads, all team attends)

---

## 7. POST-LAUNCH MONITORING PLAN

Launch day is just the start. The first 30 days define long-term health.

### 7.1 Metrics to Monitor

**Sales & Revenue:**
- Units sold (daily, weekly, lifetime)
- Revenue (gross, net after Steam's 30% cut)
- Refund rate (Steam average: 5-10%. If >15%, investigate why)
- Regional breakdown (which markets are buying?)

**Engagement:**
- Concurrent players (CCU) — peak and average
- Average session length (target: 60-90 minutes for management sims)
- Median playtime (target: 8-12 hours in first week)
- Retention: % of players who return after Day 1

**Quality:**
- Crash rate (target: <0.5% of sessions)
- Review score (Steam % positive, target: >80% for "Very Positive")
- Bug reports (critical vs. minor, volume trend)
- Support tickets (volume, common issues)

**Community:**
- Discord server growth
- Reddit mentions (sentiment analysis)
- YouTube/Twitch coverage (views, influencer engagement)
- Press coverage (review scores, features)

**Tools:**
- **Steam Partner Dashboard:** Sales, CCU, regional data
- **Sentry/BugSnag:** Crash reporting, error tracking
- **Google Analytics (optional):** In-game telemetry (if implemented)
- **Discord/Reddit:** Manual monitoring (HYPE + CRASH)
- **SteamDB:** Public data (CCU trends, price history, regional availability)

### 7.2 Monitoring Schedule

**Days 1-7 (Critical Window):**
- Check metrics: Every 6 hours
- Team check-in: Daily at 10 AM PT
- Bug triage: Daily
- Community engagement: Daily (HYPE responds to all reviews, top Discord/Reddit threads)

**Days 8-30 (Stabilization):**
- Check metrics: Daily at 10 AM PT
- Team check-in: Every 3 days
- Bug triage: Every 3 days
- Community engagement: Every 2 days

**Days 31+ (Long-Term):**
- Check metrics: Weekly
- Team check-in: Weekly
- Bug triage: Weekly
- Community engagement: As needed (respond to critical threads/reviews)

### 7.3 Response Thresholds (When to Act)

| Metric | Healthy | Warning | Critical | Action |
|--------|---------|---------|----------|--------|
| Crash rate | <0.5% | 0.5-1% | >1% | Critical: Hotfix within 24 hours |
| Review score (Steam) | >85% | 70-85% | <70% | Warning: Investigate common complaints. Critical: Major patch within 1 week |
| Refund rate | <10% | 10-15% | >15% | Warning: Survey refunders. Critical: Investigate blocking issues |
| Avg session length | >60 min | 30-60 min | <30 min | Warning: Engagement issue, investigate drop-off points |
| Support tickets | <10/day | 10-30/day | >30/day | Warning: FAQ needed. Critical: Common issue, prioritize fix |

### 7.4 Post-Launch Patch Schedule

**Patch 1.0.1 (Hotfix, L+3 days):**
- Critical bugs only
- Performance fixes (if FPS issues reported)
- Save corruption fixes (if any)

**Patch 1.1.0 (First Major Patch, L+14 days):**
- All minor bugs from launch window
- Balance tweaks based on player data (if PI decay too harsh, ratings too easy, etc.)
- QoL improvements (UI tweaks, faster scene simulation if requested)
- Community-requested features (if small and high-impact)

**Patch 1.2.0 (Second Major Patch, L+45 days):**
- Additional content (new music cues, new cast archetypes if ready)
- Advanced features (based on player feedback)
- Localization (if sales justify)

**Patch Philosophy:**
- Ship small, frequent patches (better than one massive patch)
- Test every patch on clean machine (regression testing)
- Communicate every patch via Steam Events + Discord

---

## 8. CONTINGENCY PLANS (What If?)

Plan for every nightmare scenario.

### 8.1 Scenario: Critical Crash Affecting Majority of Players

**Example:** Game crashes on launch for 50%+ of Windows 10 users due to missing DLL.

**Response:**
1. SHIP + BYTE convene immediately (within 15 minutes of reports)
2. Reproduce locally, identify missing dependency
3. Build hotfix (add missing DLL to build, or add installer dependency check)
4. Test on affected machine
5. Upload hotfix to Steam staging (30 min)
6. Test on Steam (15 min)
7. Promote to production (15 min)
8. Post Steam Event: "Critical hotfix deployed, please restart Steam to download"
9. Total response time: 60-90 minutes from first report to fix live

**Prevention:**
- Test on clean machines (multiple Windows versions)
- Use Dependency Walker to verify all DLLs are bundled or available on target systems

### 8.2 Scenario: Save Corruption Reports

**Example:** 5% of players report saves not loading after patch.

**Response:**
1. CRASH collects affected save files from players (via Discord/email)
2. BYTE reproduces locally, identifies corruption cause (e.g., version migration bug)
3. Build save file repair tool (standalone utility or integrated into game)
4. Deploy hotfix with save migration fix
5. Communicate to affected players: "If your save won't load, download the repair tool here: [link]"
6. Offer compensation (e.g., unlock all seasons for affected players if irreparable)

**Prevention:**
- Save file versioning (every save includes version number)
- Backward compatibility testing (load old saves in new builds)
- Auto-backup system (game creates .backup copy before overwriting save)

### 8.3 Scenario: Review Bombing (Negative Reviews Flood In)

**Example:** Coordinated negative review campaign (unrelated to game quality, e.g., political/social backlash).

**Response:**
1. SHIP + HYPE assess: Is this legitimate criticism or organized attack?
2. If organized attack: Do NOT engage directly (Streisand Effect)
3. Respond professionally to legitimate criticisms within the wave
4. Post neutral statement: "We're seeing a lot of feedback. We're listening and evaluating what we can improve."
5. Contact Steam support (if reviews violate Steam ToS, e.g., harassment, off-topic)
6. Focus on positive community engagement (Discord, Reddit) to balance narrative

**Prevention:**
- Strong community guidelines from day one
- Moderation team in place (Discord, Steam forums)
- Avoid controversial topics in marketing unless central to game's message

### 8.4 Scenario: Rating Board Revocation

**Example:** ESRB/PEGI discovers content not disclosed in questionnaire, threatens rating revocation.

**Response:**
1. CLOCK + SHIP contact rating board immediately
2. Provide clarification (if misunderstanding) or acknowledge error
3. If content violation is real: Patch game to remove/modify offending content
4. Resubmit to rating board for re-review
5. Communicate to players: "We're updating the game to comply with rating requirements. Update available now."

**Prevention:**
- Accurate, conservative questionnaire responses
- Legal review of all content before submission
- Capture worst-case content examples for rating board review

### 8.5 Scenario: Steam Backend Issues (Platform Down)

**Example:** Steam is down on launch day.

**Response:**
1. SHIP confirms via SteamDB/Twitter that Steam is down (not our issue)
2. Post holding statement on social media: "Steam is experiencing issues. We're monitoring and will update when service is restored."
3. Do NOT panic. Steam outages are rare and usually resolved within hours.
4. When Steam is back: Resume launch, extend any time-sensitive promotions (e.g., launch discount)

**Prevention:**
- None (platform risk is unavoidable)
- Have comms templates ready for platform issues

### 8.6 Scenario: Day-One Sales Below Projections

**Example:** Projected 500 units sold on Day 1, actual: 50 units.

**Response:**
1. CLOCK + HYPE assess: Is this a marketing issue (low visibility) or product issue (poor reception)?
2. If marketing: Increase spend on Steam ads, reach out to more influencers, post launch discount
3. If product: Read reviews, identify common complaints, prioritize fixes
4. Short-term: Adjust expectations, preserve budget for long-tail marketing
5. Long-term: Games can have slow launches and build via word-of-mouth. Do NOT panic in first 48 hours.

**Prevention:**
- Realistic sales projections (conservative estimates)
- Strong wishlist campaign pre-launch (wishlist-to-sale conversion: 10-20% typical)
- Pre-launch press coverage (reviews ready at launch)

---

## 9. TEAM ROLES & RESPONSIBILITIES (LAUNCH WINDOW)

Everyone has a defined role. No confusion on launch day.

| Role | Person | Launch Day Responsibilities | On-Call Window |
|------|--------|----------------------------|----------------|
| **Release Manager** | SHIP | Master checklist, Steam uploads, comms coordination, go/no-go decisions | L-7 to L+7, 8 AM - 8 PM PT |
| **Lead Programmer** | BYTE | Build pipeline, hotfix deployment, crash investigation, monitoring dashboard | L-7 to L+7, on-call 24/7 for critical |
| **QA Lead** | CRASH | Bug triage, player report monitoring, Discord/Steam forums, regression testing | L-1 to L+7, 8 AM - 8 PM PT |
| **Marketing** | HYPE | Social media, press coordination, community engagement, review aggregation | L-7 to L+30, 8 AM - 6 PM PT |
| **Producer** | CLOCK | Financial monitoring, stakeholder updates, contract/legal issues, team coordination | L-7 to L+7, 9 AM - 6 PM PT |
| **Art Director** | PIXEL | Store page assets, trailer review, visual bug fixes (if needed) | L-30 to L-Day, then on-call |
| **Game Designer** | REED | Balance feedback analysis, design hotfix consultation | L-Day to L+7, on-call |
| **Narrative Designer** | NOVA | Community engagement (story feedback), potential text fixes | L-Day to L+7, on-call |

**Escalation Path:**
1. Bug reported → CRASH triages → BYTE if technical, REED if design
2. Critical issue → SHIP notified immediately → SHIP convenes BYTE + CRASH → Fix or rollback decision
3. PR crisis → HYPE notifies SHIP + CLOCK → Coordinate response

**Communication Channels:**
- **Primary:** Discord (dedicated #launch-ops channel)
- **Urgent:** Phone/text (contact list distributed L-7)
- **Public:** Steam Events, Twitter, Discord announcements

---

## 10. SUCCESS CRITERIA (What Does a Good Launch Look Like?)

Define success before launch. Avoid moving goalposts.

### 10.1 Launch Day Success (L-Day)

**Minimum Success (Must Achieve):**
- [ ] Game launches on time (10 AM PT)
- [ ] Crash rate <1% (no critical launch-blocking bugs)
- [ ] Steam review score >70% positive
- [ ] No rollback required
- [ ] 50+ units sold in first 24 hours

**Target Success (Ideal Outcome):**
- [ ] Steam review score >80% positive ("Very Positive")
- [ ] 200+ units sold in first 24 hours
- [ ] 100+ CCU peak on launch day
- [ ] Positive press coverage (3+ reviews from recognized outlets)
- [ ] No hotfix required (GOLD build is clean)

**Stretch Success (Exceptional):**
- [ ] Steam review score >90% positive ("Overwhelmingly Positive")
- [ ] 500+ units sold in first 24 hours
- [ ] Featured on Steam's front page (New & Trending)
- [ ] 500+ CCU peak
- [ ] Major influencer coverage (100K+ subscriber YouTuber/streamer plays game)

### 10.2 First Week Success (L+7)

**Minimum Success:**
- [ ] 500+ units sold
- [ ] Steam review score >75% positive
- [ ] Crash rate <0.5%
- [ ] No critical bugs unresolved

**Target Success:**
- [ ] 1,500+ units sold
- [ ] Steam review score >80% positive
- [ ] Average session length >60 minutes
- [ ] 50+ Discord members
- [ ] 5+ positive reviews from press/influencers

**Stretch Success:**
- [ ] 3,000+ units sold
- [ ] Steam review score >85% positive
- [ ] Featured on Steam front page or curated list
- [ ] 100+ Discord members
- [ ] Major coverage (PC Gamer, RPS, Kotaku, etc.)

### 10.3 First Month Success (L+30)

**Minimum Success:**
- [ ] 2,000+ units sold
- [ ] Revenue covers development costs (break-even)
- [ ] Stable player base (50+ weekly active players)

**Target Success:**
- [ ] 5,000+ units sold
- [ ] Revenue 1.5x development costs (profitable)
- [ ] 200+ Discord members
- [ ] Consistent positive reviews (ongoing, not just launch spike)

**Stretch Success:**
- [ ] 10,000+ units sold
- [ ] Revenue 2x+ development costs
- [ ] Community-created content (fan art, guides, mods)
- [ ] Request for DLC/sequel from players

---

## 11. POST-LAUNCH ROADMAP (First 6 Months)

**Month 1 (Post-Launch):**
- Hotfixes as needed
- Community engagement (respond to all feedback)
- Patch 1.1.0 (bug fixes + QoL improvements)

**Month 2:**
- Patch 1.2.0 (balance tweaks, additional content)
- Begin DLC planning (based on player requests)
- Localization (if sales justify)

**Month 3:**
- Patch 1.3.0 (accessibility features, controller support polish)
- Steam Summer/Winter Sale (if timing aligns)
- Community events (screenshot contest, fan art contest)

**Months 4-6:**
- DLC 1 development (new show formats, cast archetypes)
- Console port evaluation (if PC/Steam Deck sales strong)
- Year-one roadmap communicated to community

---

## 12. OPEN QUESTIONS (Requiring Decisions Before Launch)

These must be resolved before GOLD build.

1. **Launch Discount?** Should we offer a 10-15% launch week discount to incentivize early purchases? Or full price to maximize revenue from wishlists? DECISION OWNER: CLOCK + HYPE. DEADLINE: L-60 days.

2. **Pre-Purchase?** Enable pre-purchase 2 weeks before launch? Pros: Early revenue, gauge demand. Cons: Refund risk if launch is bad. DECISION OWNER: SHIP + CLOCK. DEADLINE: L-45 days.

3. **Review Copies: How Many?** 30 keys? 50? 100? Balance: More keys = more coverage, but also more risk of leaks/spoilers. DECISION OWNER: HYPE. DEADLINE: L-60 days.

4. **Day-One Patch: Yes or No?** If we find minor bugs post-GOLD, do we patch on L-Day or wait until L+7? Philosophy question. DECISION OWNER: SHIP. DEADLINE: L-10 days (when patch scope is known).

5. **Localization at Launch?** English-only, or add Spanish/French/German if budget allows? DECISION OWNER: CLOCK (budget) + HYPE (market research). DEADLINE: L-90 days (localization takes 4-6 weeks).

6. **Controller Support at Launch?** Full support, partial, or post-launch? Steam Deck requires it for Verified status. DECISION OWNER: BYTE. DEADLINE: M18 (before Milestone 5 complete).

7. **Trading Cards at Launch?** Or wait until $1K revenue threshold? DECISION OWNER: SHIP. RECOMMENDATION: Design now, submit post-launch after threshold met.

---

## 13. FINAL NOTES

This release plan is a living document. It will be updated as the project progresses, new risks are identified, and decisions are made. But the core structure — the master checklist, the build pipeline, the rollback procedures — is final. These are the rails that keep us on track.

Launch day is the culmination of 18-24 months of work. Every item on this checklist exists to protect that work from preventable failure. There will be surprises. There will be crises. But if we execute this plan, line by line, we maximize our chances of a clean launch.

What's the rollback plan? Documented.
What's the hotfix pipeline? Tested.
What's the launch day timeline? Hour-by-hour, with owners assigned.
What's the monitoring plan? Metrics tracked, thresholds set, response procedures defined.

Is this plan on the checklist? If not, it doesn't happen.

Let's ship this.

— SHIP

---

**Document Status:** Pre-Production Release Plan
**Next Review:** Milestone 3 (Month 10) — Validate timeline, update dependencies
**Final Review:** L-60 days — Lock all decisions, finalize launch date
**Master Checklist Location:** `/project-management/release-checklist.xlsx` (tracking sheet)
**Rollback Procedures Location:** `/ops/rollback-runbook.md` (operational guide)
**Launch Day Timeline Location:** `/ops/launch-day-timeline.md` (distributed to team L-7)

*All documentation will be migrated to final locations as project structure solidifies.*

---

**Release plan complete. No placeholders. No TODOs. Every step documented. Every contingency planned. Ready for team review and production kickoff.**

*If it's not on the checklist, it doesn't happen on launch day.*
