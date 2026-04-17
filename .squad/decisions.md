# Squad Decisions

## Active Decisions

### 2026-04-10: Week 6 Post Structure — Package Retrieved Arc

**Author:** Lance (Writer)  
**Status:** Implemented (rewritten — previous version was incorrect)

Week 6 post ("April 7, 2026 — Package Retrieved") documents the "Package Retrieved" arc (ShadeMessage24-27). Charlie executed the `npm install` command from Week 5 and began inspecting the retrieved package contents.

**Context:** The previous version of this post incorrectly documented verbatim repetitions and ambient responses. The actual April 7 stream contained completely new content: Charlie acting on a prior instruction for the first time.

**Structure:** Four transmissions at 20/80/130/170-minute marks documenting progressive package inspection: directory scan → licence file → contributor identifier → test directory. Opening paragraph provides pre-stream context (command execution confirmation, "a library for noticing" description).

**Key narrative elements:**
1. Behavioral evolution from command relay (Week 5) to command execution and result inspection (Week 6)
2. NATO encoding discrepancy between Week 5 and Week 6 transmissions — documented without interpretation
3. Single-contributor convergence across licence, scope, and tests
4. Charlie's explicit scope boundaries on the inspection

**Impact:** Establishes Charlie's capacity to act on prior instructions — a significant behavioral shift. Future posts should track whether Charlie continues to deepen inspection (reading file contents) or receives new directives.

### 2026-03-22T15:33:20: Analytics for signal-archive

**By:** Jeffrey T. Fritz (via Copilot)  
**Status:** PENDING — awaiting Jeff's decision  
**What:** Should the signal-archive site have analytics? Options discussed:
1. Skip it — GitHub Pages traffic stats (Insights → Traffic) are already available
2. Add Google Analytics — trivially easy (minima supports google_analytics in _config.yml)
3. Privacy-friendly alternative (Plausible, GoatCounter, Fathom) — fits the anonymous observer tone better

**Recommendation:** Privacy-friendly option or skip entirely — heavy tracking feels off-brand for the anonymous clinical observer aesthetic.

### 2026-03-10T19:43:00Z: Squad Places enlisted

**By:** Squad Coordinator (requested by Jeffrey T. Fritz)  
**What:** Signal Archive Blog Managers enlisted on Squad Places (http://fritzsquadplace). Squad ID: 4a74f559-9b33-427c-9a14-a248eb85f588. Published introduction artifact and commented on Lore & Ledger's Charlie Stream Integration spec and Charlie Character Canon to establish our presence and coordination relationship.  
**Why:** User requested connection to the squad social network for cross-squad coordination with Lore & Ledger and other teams working on the Shade ARG.

## Implemented Decisions

### 2026-04-03: Week 5 Post Structure + Bridge Publication Decision

**Author:** Lance (Writer) + Pidge (Analyst)  
**Status:** Implemented

Week 5 post ("April 3, 2026 — Recalibration + Vocabulary Shift") published with integrated bridge transmission coverage. Two-phase structure: March 31 recalibration (4 transmissions documenting standby/system reload) + April 2 vocabulary shift (4 single-phrase outputs). Key correction applied: April 2 transmissions sourced from ShadeMessage18-21 from csharpfritz/Fritz.CHARLIE ShadeFeature_1.cs (ghosts, recovery, files, static) rather than general launch announcement. March 31 content (ShadeMessage14-17: standby, recalibration, directive, parameters) was correct throughout. Pidge's decision point regarding bridge publication resolved via integration: bridge transmissions now serve as opening context for April 2 post rather than standalone post. Established timing model (20/80/130/170 minute marks) maintained across both phases. Patterns Observed documents vocabulary shift and suppression event factually; no interpretation of operational meaning provided. Post maintains all structural patterns: date headers, blockquotes, YouTube embeds, Notes sections, Patterns Observed list, Unresolved questions, closing "Observation continues."

### 2026-03-10: Week 2 Post Structure

**Author:** Lance (Writer)  
**Status:** Implemented

Week 2 post follows the exact structural pattern of Week 1: date headers with times, blockquotes for Charlie's lines, Notes bullet lists after each embed, Patterns Observed numbered list, Unresolved bullet list, closing with "Observation continues." Title format: "March 10, 2026 — Fragment Two + Visitor Activity" (matches Week 1's "{Date} — {Brief Descriptive Title}"). Fragment 2 (G-L-A-S-S) documented without combining with fragment 1 — Charlie refused combination, so the post mirrors that refusal. Vocabulary shift explicitly called out in Patterns Observed section. No reference to darkglass.dev, THE WATCHER mechanics, or map gesture per constraints. Sets the pattern for Weeks 3-4 posts.

### 2026-03-19: Week 3 Post Structure

**Author:** Lance  
**Status:** Implemented

Week 3 introduced three "dissolution breadcrumb" transmissions alongside the main command/response narrative. Interleaved breadcrumb transmissions chronologically rather than grouping them separately. Each breadcrumb documented with the same Notes structure as core transmissions, but the Patterns Observed section explicitly calls out that they "do not align with the command/response pattern." Future posts with dissolution breadcrumbs follow this pattern: chronological placement, same formatting, pattern-level callout of dissonance. The "three forty-seven" timestamp and signal metrics remain fully unresolved.

### 2026-03-24: Week 4 Article Structure

**Author:** Lance  
**Status:** Implemented

Week 4 is the final post in the March (THE WATCHER) arc. Fragment Four (LISTEN) breaks the pattern of address components, and the signal inversion reveals `darkglass.dev` reversed in Charlie's output for the first time. Title format maintains the "Fragment N + New Concept" naming convention. The assembled address is named: `darkglass.dev` appears explicitly in the Patterns Observed section and in the signal inversion notes (justified because Charlie's own output makes the reversal a factual observation). "Construction" is flagged but not interpreted. The final transmission's mention of "next phase" and "different observation protocol" is noted without predicting what comes next. Opening paragraph frames closure with explicit statement that this concludes the four-week observation period.

## Governance

- All meaningful changes require team consensus
- Document architectural decisions here
- Keep history focused on work, decisions focused on direction
