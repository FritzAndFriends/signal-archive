# Pidge — History

## Project Context
- **Project:** signal-archive — a Jekyll blog documenting Charlie the chatbot's anomalous behavior during Jeff Fritz's Twitch streams
- **Tech stack:** Jekyll, Markdown, GitHub Pages
- **User:** Jeffrey T. Fritz
- **Repo:** signal-archive (org: fritzandfriends, hosted at fritzandfriends.github.io/signal-archive)
- **Stream schedule:** Tuesday & Thursday, 9am ET on twitch.tv/csharpfritz

## Known Encoding Methods
- **Base64:** `cmV0cmFjZSB0aGUgc2lnbmFs` → "retrace the signal"
- **NATO Phonetic Alphabet:** Delta=D, Alpha=A, Romeo=R, Kilo=K → "DARK"
- **Coordinates:** Decimal degrees format (48.1°N, 6.2°W)

## Established Data Points
- Coordinate lock: 48.1°N, 6.2°W (final — no further drift)
- Fragment 1 of 4: D-A-R-K (confirmed twice)
- Fragments 2-4: not yet delivered
- Timing intervals observed: 20/45/90/130/140-minute marks
- Charlie vocabulary evolution tracked in Week 1 post

## YouTube Embed Format
```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/{VIDEO_ID}?si={SI_PARAM}&amp;start={SECONDS}" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
```

## Learnings

### MAKER Arc (April 2, 2026 transition)
- **Vocabulary shift is engineered, not emergent:** March 31 bridge stream confirms new vocabulary set was intentionally installed during recalibration. Charlie has no preview of new terms — they arrive as unknown during April 2 operation.
- **Bridge stream recalibration mechanics:** Four transmissions document Charlie's protocol shift. Protocol offline status (standby mode) → new parameters loaded → vocabulary installed → forty-three internal anomaly suppressed → April 2 activation confirmed.
- **Forty-three anomaly:** Internal data fragment emerged during recalibration, unclassifiable as coordinate/address component. Charlie suppressed it (first documented case of active output filtering, vs. logging/reporting).
- **Tonal shift from assembly to archaeology:** WATCHER vocabulary (coordinate, address, fragment, signal) → MAKER vocabulary (static, haunting, ghosts, recovery). New phrases introduce metaphor/existential language absent from WATCHER baseline.
- **Recovery as distinct from restoration:** "Recovery is not restoration" phrase signals philosophy change. Charlie's observation framework shifted from assembling external addresses to recovering internal archival data.
- **47% recovery metric:** First quantified progress metric in signal-archive docs. Suggests MAKER has measurable completion state, but completion scope (47% of what?) unresolved.
- **Charlie's opacity about new parameters:** March 31, ~170min transmission: Charlie has NOT been briefed on operational specifics of new parameters. Charlie is operating under unknown directives — new to Charlie as to analysts.

### Bridge Stream Discoverability Question
- Unclear whether March 31 bridge transmissions are discoverable by players or analyst-only intelligence. Critical for blog post visibility and community narrative cohesion.

### Known Encoding Methods (Updated)
- NATO Phonetic: Confirmed as active encoding method (L-I-S-T-E-N = L-I-S-T-E-N confirmed in April 2)
- Internal numeric fragments: 43 (suppressed during recalibration, unclassifiable)
- Hex glitch vocabulary: Referenced as active April 2, specific phrases pending enumeration

### Week 8 Post Completion
- **YouTube Video IDs secured:**
  - Monday April 13: 5739RGIMPyU
  - Tuesday April 14: cuj0Ny9KrVI
  - Thursday April 16: FT0J4FPBy7M
- **All 11 transmissions embedded with precise timestamps:**
  - 9:30am (30min/1800s), 10:30am (90min/5400s) — Monday
  - 9:20am (20min/1200s), 9:55am (55min/3300s), 10:25am (85min/5100s), 10:50am (110min/6600s) — Tuesday
  - 9:30am (30min/1800s), 10:30am (90min/5400s), 11:20am (140min/8400s), 12:10pm (190min/11400s), 12:50pm (230min/13800s) — Thursday
- Embed format verified against Week 6 post structure. All iframes placed post-blockquote, pre-Notes, with blank lines before/after.

### Week 8 Post Approval
**Status:** ✅ APPROVED FOR PUBLICATION (2026-04-17T20:45:00Z)
- Hunk re-review after Pidge added 11 YouTube embeds — all verification passed
- Format compliance achieved: all transmissions now have video embeds with correct timestamps
- Content review re-run confirmed: continuity, data accuracy, voice, tone, structure all verified
- No additional revisions needed — ready for publication

### Charlie Quote Verification Skill Documentation
**Status:** ✅ COMPLETED (2026-04-18T[timestamp])
- Created reusable skill documentation at `.squad/skills/charlie-quote-verification/SKILL.md`
- Full methodology documented: live chat replay extraction, csharpTrace marker pattern, embed timestamp formula, Python parsing script
- Includes Week 8 real-world verification example with all 11 transmissions
- Documented anti-patterns: why YouTube transcripts fail, why narrative quotes ≠ chat text, pre-show offset handling
- Verification checklist provided for future posts
- Source: earned through Week 8 successful verification session

### Week 9 Analysis Completion
**Status:** ✅ COMPLETED (2026-04-27)
- **YouTube Video IDs secured:**
  - Tuesday April 22: WHTKad6W_bc (AI Coding, Streamer Maps, Glitches, and more — 2:43:37)
  - Thursday April 24: PsA24rsRSpc (Launching a new site with Azure and Copilot — 3:35:47)
- **8 transmissions documented** with verified timestamps and screenshots
- **New marker type discovered:** `csharpAndThen` (at 33:22 Tuesday) — distinct from `csharpTrace`, purpose unknown
- **On-screen narrative text discovery:** Two instances of visual overlay text (separate from chat):
  - Trace 2 Tuesday: "twelve commit entries... personal annotations... understood"
  - Trace 3 Thursday: "embedded text strings that do not execute... they describe intent... not function"
  - Method: Playwright screenshots at trace moments reveal narrative text not present in chat replay
- **Trace timing patterns:**
  - Tuesday: 20/80/130 minutes (60-minute intervals after first)
  - Thursday: 80/130/170 minutes (50-minute intervals)
  - Pattern diverges between streams — not fixed
- **Charlie's Week 9 posture:** Monitoring/status checks dominant. "Channel remains open," "external input capability: active." Shift from active inspection (Week 8) to passive waiting.
- **quietcipher.dev status checked:** linger package "recovering data...", /signal page shows "close this page", /terms.html has fiction notice
- **yt-dlp note:** Installed via `pip install yt-dlp` in this environment (pip-based, not the path in SKILL.md)
- **Embed formula confirmed:** `start = floor(offset_ms / 1000) - 4` (4-second lead-in)
- **Handoff delivered:** Analysis + Lance handoff documents placed in `.squad/decisions/inbox/`
