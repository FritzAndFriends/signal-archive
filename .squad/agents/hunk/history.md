# Hunk — History

## Project Context
- **Project:** signal-archive — a Jekyll blog documenting Charlie the chatbot's anomalous behavior during Jeff Fritz's Twitch streams
- **Tech stack:** Jekyll, Markdown, GitHub Pages
- **User:** Jeffrey T. Fritz
- **Repo:** signal-archive (org: fritzandfriends, hosted at fritzandfriends.github.io/signal-archive)

## Continuity Tracker
Canonical data points to verify against in every review:

### Coordinates
- 48.1°N, 6.2°W — declared final (no further drift) as of March 3, 2026

### Fragments
- Fragment 1 of 4: D-A-R-K (NATO phonetic: Delta, Alpha, Romeo, Kilo)
- Fragment 2 of 4: G-L-A-S-S (NATO phonetic: Golf, Lima, Alpha, Sierra, Sierra)
- Fragments 3-4: not yet delivered

### Encoded Messages
- `cmV0cmFjZSB0aGUgc2lnbmFs` (base64) → "retrace the signal"

### Vocabulary Introduced
- Week 1: "terminated," "corruption," "access point," "fragment integrity," "segments"
- Week 2: "visitors," "concurrent," "engagement," "elevated," "navigating without guidance"

### Timing Patterns
- Week 1 intervals: 20/45/90/130/140-minute marks (five transmissions, single stream)
- Week 2 intervals: 20/90/140/175-minute marks (four transmissions, single stream)

## Review Publishing History

### Week 2 Review — 2026-03-10-week-2.md — APPROVED & PUBLISHED
**Commit:** 72867cc  
**Status:** Published to production  
**Date:** 2026-03-10T19:59:45Z  

Editorial review complete. All checklist items pass. Post approved for publication with zero violations. Continuity, voice, constraints, and format all verified correct. Week 2 post now live.

## Learnings

### Week 8 Review — Critical Format Violation Identified
**Status:** REJECTED — YouTube Embeds Missing  
**Timestamp:** 2026-04-17  
**Decision:** Post submitted for publication without YouTube embeds

- **Context:** Lance submitted Week 8 post ("The Lines Move") documenting 11 transmissions from April 13-16, 2026 streams. Post is editorially sound — all continuity verified, data accurate, tone consistent, patterns documented correctly.
- **Critical Issue:** Zero YouTube embeds present. All prior weeks (1-7) include video embeds for every transmission. Week 8 has 11 transmissions but zero embeds.
- **Impact:** Cannot verify timestamps match actual video timestamps. Violates established format pattern.
- **Pattern established:** Every post since Week 1 includes `<iframe>` embeds with video ID and start timestamps matching the minute marks in transmission headers.
- **Required fix:** Add 11 YouTube embeds (Monday 2 + Tuesday 4 + Thursday 5) with correct video ID and calculated start timestamps:
  - 30 min = 1800 sec
  - 90 min = 5400 sec
  - 20 min = 1200 sec
  - 55 min = 3300 sec
  - 85 min = 5100 sec
  - 110 min = 6600 sec
  - 140 min = 8400 sec
  - 190 min = 11400 sec
  - 230 min = 13800 sec
- **Content verified:**
  - Continuity: Week 5 (npm install) and Week 6 (3000ms threshold, single contributor) references all correct ✅
  - Data: Displacement patterns (Static, Drift, Bleed, Fracture, Decay), duration values (500, 700, 800, 1000, 1500), module chain (Presence → Dwell → Linger → Echo) all verified ✅
  - Annotations: Both code annotations quoted verbatim ✅
  - Patterns: All 8 pattern observations supported by transmission content ✅
  - Unresolved: Seven meaningful, specific questions ✅
  - Voice: Clinical observer maintained; no editorial interpretation outside observations ✅
- **Lesson:** Format checklist must be primary gate before content review. YouTube embeds are structural requirement, not optional. All prior weeks set precedent that must be verified first.
- **Boundary maintained:** This is not a content rejection — it is a format gate. Lance's journalism is sound; the post just needs the embed layer added before publication.

<!-- Append new learnings below -->

### Week 8 Re-Review — 2026-04-17-week-8.md — YouTube Embeds Added & APPROVED
**Status:** APPROVED FOR PUBLICATION  
**Timestamp:** 2026-04-17 (re-review after embed layer added)  
**Analyst:** Pidge (added 11 embeds)  
**Reviewer:** Hunk (format + content verification)

- **Context:** Week 8 post ("The Lines Move") was rejected on initial review for missing YouTube embeds. Pidge added all 11 embeds across four stream segments (Monday 2, Tuesday 4, Thursday 5). Re-review conducted to verify embed correctness before publication.
- **Embed verification complete:**
  - ✅ 11 embeds present (one per transmission)
  - ✅ All placed correctly after blockquotes, before Notes sections
  - ✅ Video IDs verified: 5739RGIMPyU (April 13), cuj0Ny9KrVI (April 14), FT0J4FPBy7M (April 16)
  - ✅ Start timestamps calculated correctly from minute marks (30→1800, 90→5400, 20→1200, 55→3300, 85→5100, 110→6600, 140→8400, 190→11400, 230→13800 seconds)
- **Content verification re-run:**
  - ✅ Continuity: Week 5 (npm install), Week 6 (3000ms threshold, single contributor) — all references correct
  - ✅ Data accuracy: Displacement patterns (Static, Drift, Bleed, Fracture, Decay), duration values (500, 700, 800, 1000, 1500), module chain (Presence → Dwell → Linger → Echo) — all verified
  - ✅ Annotations: Both code annotations quoted verbatim without interpretation
  - ✅ Patterns Observed: Eight distinct patterns, each with supporting transmission evidence
  - ✅ Unresolved: Seven specific, unanswered questions
  - ✅ Voice: Clinical observer maintained throughout; no first-person language
  - ✅ Structure: Frontmatter correct, Notes sections complete, post ends with "Observation continues."
  - ✅ Tone: Diagnostic, neutral — Charlie's statements treated as observations
- **Publication ready:** No revisions required. Post approved as-is.

### Week 6 Continuity Fix — 2026-04-10-week-6.md — SM27 Removal
**Timestamp:** 2026-04-13  
**Task:** Remove all references to ShadeMessage27 content that never aired (stream ended at 170 minutes, SM27 was scheduled for 170-minute mark but never fired)

- **Context:** April 7 stream did NOT run for full 180 minutes — ended before SM27 (test directory inspection) could fire. The transmission section for SM27 was already removed, but residual references to test-related content remained scattered through the post.
- **Fixes applied:**
  - Line 7: Changed "Four transmissions" → "Three transmissions" (SM24, SM25, SM26 only)
  - Patterns Observed #2 (line 65): Removed "detected tests" from inspection list (referenced SM27 content)
  - Patterns Observed #4 (line 67): Rewrote single-contributor convergence from THREE transmissions to TWO transmissions. Removed "tested their own work" observation (came from SM27). Now correctly reflects: licence (single contributor) + identifier (one person built this) = two-transmission convergence.
  - Patterns Observed #5 (line 68): Removed quote "I do not know what they verify" (from SM27). Bounded-scope examples now correctly reference only quotes that DID air: "I am reporting structure only" (SM24) and "I was not instructed to determine why" (SM26).
  - Unresolved section (line 75): Removed "What do the tests verify?" bullet entirely (SM27 never fired, Charlie never mentioned tests)
  - Unresolved section (line 79): Removed "tested" from "built, released, and tested" → now reads "built and released"
  - SM26 YouTube embed (line 51): Fixed timestamp from `start=753` (~12.5 min) to `start=7800` (~130 min) — 130-minute mark requires ~7800 seconds
- **Timing pattern:** Confirmed three-transmission pattern at 20, 80, 130 minutes (SM24, SM25, SM26). The 170-minute mark (SM27) never occurred.
- **Post-edit verification:** Re-read full post for internal consistency. All claims now supported only by the three transmissions that actually aired. No orphaned test references remain.
- **Key learning:** When stream duration changes affect transmission delivery, residual references can persist even after removing the transmission section itself. Full-post continuity review required to catch scattered references in Patterns Observed, Unresolved, and opening paragraphs.

### Week 6 Review (REWRITE) — 2026-04-10-week-6.md — TWO PASSES COMPLETE & PUBLISHED
**Status:** Completed and merged to main (commit 5a4d208)
**Timestamp Pass 1:** 2026-04-10T01:00:00Z — Approved with zero corrections
**Timestamp Pass 2:** 2026-04-10T02:00:00Z — Applied corrections after user verification of stream duration
- **Context (Rewrite):** Post was fully rewritten because the previous version used incorrect source material (verbatim repetitions + ambient responses). The correct source is ShadeMessage24-26 from commit `9264ca4` in Fritz.CHARLIE — the "Package Retrieved" arc where Charlie executed the npm install command from Week 5 and inspected package contents.
- **Verbatim quotes:** All three blockquotes (SM24, SM25, SM26) verified character-by-character against source strings. All match exactly.
- **YouTube embeds:** Video ID `mAYkcfHM8ck` confirmed. Timestamps: start=1200/4800/7800 for 20/80/130-minute marks (stream ended at 130 min). All correct.
- **Voice:** Clinical observer maintained throughout. No first-person ("I"/"we"/"our") outside blockquotes. Diagnostic vocabulary. No editorializing.
- **Structure:** Matches Week 1-5 pattern — frontmatter, date headers with times, blockquotes, YouTube iframes, Notes sections, Patterns Observed, Unresolved, "Observation continues." ending.
- **Title format:** "April 7, 2026 — Package Retrieved" — correctly uses stream date (Tuesday) with Friday publication date in frontmatter (`2026-04-10`).
- **Continuity:** Week 5 references correct — npm install command, link format `[Week 5](/signal-archive/week-5/)`.
- **NATO encoding discrepancy:** Correctly documented in Notes (line 56) and Patterns Observed (#3). Week 5 SM19: "Quebec uniform **india** echo tango..." vs Week 6 SM26: "Quebec uniform echo tango..." — the missing "india" is noted as an observation without interpretation. ✅
- **Forbidden content:** No mention of THE WATCHER, THE MAKER, or quietcipher.dev. "A library for noticing" quoted in opening paragraph as Charlie's own words with Charlie's disclaimer ("I do not know what that means") — not interpreted. ✅
- **Previous Week 6 review (superseded):** The prior review from 2026-04-13T01:22:43Z applied to the incorrect version of the post (verbatim repetitions + ambient responses). That version was fully replaced.

### Week 2 Review — 2026-03-10-week-2.md
