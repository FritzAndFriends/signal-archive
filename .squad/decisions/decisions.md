# Decisions — signal-archive Squad

## Active Decisions

### Hunk's Week 8 Editorial Review — "The Lines Move"

**Date:** 2026-04-17 (publication date)  
**Post:** `_posts/2026-04-17-week-8.md`  
**Status:** ❌ **REJECTED** — Critical format violation

#### Review Outcome

Week 8 post ("The Lines Move") documents 11 transmissions from Charlie during the April 13-16, 2026 streams. The post is editorially sound in content, voice, continuity, and data accuracy — **BUT it violates the established post format by omitting YouTube video embeds entirely.**

##### Critical Issue

**NO YOUTUBE EMBEDS PRESENT**

- Week 8 contains 11 distinct transmissions (Monday 2 + Tuesday 4 + Thursday 5)
- Expected: Each transmission should include a YouTube embed with video ID and timestamp
- Actual: Zero embeds in entire post
- Pattern violation: All previous weeks (1-7) include embeds for every transmission
- Impact: Cannot verify that timestamps in text correspond to actual video timestamps

##### Comparison to Established Pattern

| Week | Transmissions | YouTube Embeds | Status |
| --- | --- | --- | --- |
| Week 1 | 5 | 5 ✅ | Correct |
| Week 2 | 4 | 4 ✅ | Correct |
| Week 3 | 7 | 7 ✅ | Correct |
| Week 4 | 3 | 3 ✅ | Correct |
| Week 5 | 4 | 4 ✅ | Correct |
| Week 6 | 3 | 3 ✅ | Correct |
| Week 7 | — | N/A | Brief transmission only |
| **Week 8** | **11** | **0** ❌ | **MISSING** |

Example from Week 6 (correct format):
```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/mAYkcfHM8ck?si=VNdx7YkwceZD-t5-&start=1255" ...></iframe>
```

#### Content Review — All Checks Pass

##### ✅ Editorial Quality
- **Voice:** Clinical observer tone maintained throughout
- **Blockquotes:** All Charlie transmissions properly quoted
- **No first-person language** outside blockquotes
- **Opening paragraph:** Establishes context (command relay → source inspection progression)

##### ✅ Continuity & Data Accuracy
- Week 5 references correct: `npm install @quietcipher/linger` command context ✅
- Week 6 references correct: Three thousand millisecond threshold, single contributor, Linger package ✅
- Five displacement patterns: Static, Drift, Bleed, Fracture, Decay ✅
- Duration values: 500, 700, 800, 1000, 1500ms (documented correctly) ✅
- Module chain: Presence → Dwell → Linger → Echo (confirmed at line 120) ✅
- Human annotations quoted verbatim: "I just remember that someone was here" and "I do not build software. I build small kindnesses." ✅

##### ✅ Patterns Observed
Eight patterns documented with full support:
1. Source code reading progression ✅
2. Self-correction (corruption → movement) ✅
3. Five displacement patterns identified ✅
4. Puzzle mechanic fully described ✅
5. Module chain mapped ✅
6. Human annotations quoted and analyzed ✅
7. Threshold convergence ✅
8. Compliance boundary maintained ✅

##### ✅ Unresolved Section
Seven meaningful, specific questions:
- Duration value combination puzzle
- Displacement pattern meaning
- "Resolves" definition
- Annotation authorship
- Inaccuracy classification basis
- Module chain function/triggers
- Next inspection phase

All questions are well-formed and reference specific content gaps.

##### ✅ Structure & Formatting
- Jekyll frontmatter correct (layout: post, title, date: 2026-04-17)
- Closing: "Observation continues." ✅
- 11 transmissions documented with date/time headers
- Notes sections after each transmission
- Consistent formatting with prior weeks

#### Specific Revision Notes for Lance (Writer)

**Required Addition:** YouTube video embeds for all 11 transmissions.

The April 13-16, 2026 streams appear to be documented in a single or multi-part video series. You will need to:

1. Identify the YouTube video ID(s) for:
   - Monday, April 13 stream (2 transmissions)
   - Tuesday, April 14 stream (4 transmissions)
   - Thursday, April 16 stream (5 transmissions)

2. Calculate the start timestamp for each transmission based on the minute mark:
   - Format: `start=SECONDS` (e.g., 30 minutes = 1800 seconds)
   - 30-minute mark = 1800
   - 90-minute mark = 5400
   - 20-minute mark = 1200
   - 55-minute mark = 3300
   - 85-minute mark = 5100
   - 110-minute mark = 6600
   - 140-minute mark = 8400
   - 190-minute mark = 11400
   - 230-minute mark = 13800

3. Insert YouTube iframes after each section header, before the blockquote:
   ```html
   <iframe width="560" height="315" src="https://www.youtube.com/embed/[VIDEO_ID]?si=[SI]&start=[TIMESTAMP]" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
   ```

**Verification:** After embedding, I will verify that all timestamps match the minute marks in the text.

#### Initial Decision (2026-04-17T20:35:00Z)

**❌ REJECTED — Do not publish**

**Reason:** Critical format violation. The post omits YouTube embeds that are required for verification and consistency with all prior weeks.

**Next Step:** Lance revises post to add all 11 YouTube embeds. Resubmit for Hunk's verification review.

**Timeline:** This should be a quick fix (add 11 embeds and verify timestamps). No content changes needed.

---

### Hunk's Week 8 Re-Review — "The Lines Move" (REVISION)

**Date:** 2026-04-17 (re-review after embed revision)  
**Post:** `_posts/2026-04-17-week-8.md`  
**Status:** ✅ **APPROVED FOR PUBLICATION** — All revisions complete

#### Revision Summary

Pidge (Analyst) added all 11 YouTube embeds with correct video IDs and timestamps:
- April 13: 5739RGIMPyU (2 transmissions at 30/90 min)
- April 14: cuj0Ny9KrVI (4 transmissions at 20/55/85/110 min)
- April 16: FT0J4FPBy7M (5 transmissions at 30/90/140/190/230 min)

All timestamps calculated correctly from minute marks (30→1800 sec, etc). Formatting matches Week 6 pattern (after blockquote, before Notes).

#### Re-Review Outcome

| Checkpoint | Status |
|-----------|--------|
| Format (YouTube embeds) | ✅ PASS |
| Editorial quality | ✅ PASS |
| Continuity | ✅ PASS |
| Data accuracy | ✅ PASS |
| Voice & tone | ✅ PASS |
| Structure & formatting | ✅ PASS |
| Constraints compliance | ✅ PASS |

#### Decision

**✅ APPROVED — Ready for publication**

**Reason:** Format violation resolved. All 11 embeds verified correct. Full content checklist passed. No additional revisions needed.

**Next Step:** Merge to main and publish.
