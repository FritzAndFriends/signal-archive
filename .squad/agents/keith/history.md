# Keith — History

## Project Context
- **Project:** signal-archive — a Jekyll blog documenting Charlie the chatbot's anomalous behavior during Jeff Fritz's Twitch streams
- **Tech stack:** Jekyll, Markdown, GitHub Pages
- **User:** Jeffrey T. Fritz
- **Repo:** signal-archive (org: fritzandfriends, hosted at fritzandfriends.github.io/signal-archive)
- **Stream schedule:** Tuesday & Thursday, 9am ET on twitch.tv/csharpfritz
- **Community:** Fritz and Friends Discord, #signals channel

## Key Files
- `_posts/` — blog posts in Jekyll format (YYYY-MM-DD-slug.md)
- `_config.yml` — site config, theme: minima, future posts enabled
- `about.md` — site description (clinical, no-editorializing tone)
- `index.md` — homepage

## Voice & Tone
Posts are written by an anonymous observer. Clinical, precise, pattern-tracking. No interpretation — just documentation. Ends with "Observation continues." See charter for full voice reference.

## Established Patterns (from Week 1 post)
- Coordinate lock: 48.1°N, 6.2°W (declared final)
- NATO phonetic fragment: D-A-R-K (fragment 1 of 4)
- Base64 encoded message: "retrace the signal"
- New vocabulary: "terminated," "corruption," "access point," "fragment integrity," "segments"
- Timing intervals: 20/45/90/130/140-minute marks

## Learnings

### Capture Skill Revision (2026-04-27)
- **Problem:** Hunk rejected initial revision because Playwright instructions still focused on chat capture rather than video-element-only. Old methodology captured right-side chat panel alongside video — opposite of new requirement.
- **Solution:** Rewrote `charlie-quote-verification/SKILL.md` Playwright section with:
  - Specific selector guidance: `#movie_player` (primary) and `.html5-main-video` (secondary)
  - Explicit exclusion rules: header, sidebar, chat, recommendations, comments, overlays, page chrome
  - Concrete Playwright code pattern with async/await, headless launch, element waiting, screenshot call
  - What-gets-captured vs what-doesn't-get-captured checklist
  - Tested on live YouTube to verify selector stability
- **Impact:** Future verification work now has clear, actionable guidance for video-element-only screenshots. Cross-referenced from lite-youtube-embed skill for consistency.
- **Team pattern:** When skill rejections cite clarity issues, rewrite with concrete selectors, code examples, and visual checklists rather than abstract descriptions.

### Week 9 Scope Decision (2026-04-18)
- **New constraint relaxed:** User approved quietcipher.dev references in Week 9 post. Prior weeks studiously avoided all mention (conservative gate on ARG-adjacent content). This is strategic permission, not unlimited disclosure — only include if transmissions surface it naturally.
- **Community re-engagement driver:** Interactions on site have "completely stopped." Posts need to surface connections and patterns that pull audience back in.
- **Post continuity model:** Week 8 post ended with "Module analysis complete" but flagged observation continuing. Week 9 should show Charlie's next phase: code execution, testing, or deeper dependency tracing.
- **Pidge's skill formalization:** Charlie Quote Verification Skill (documented Week 8) is now team standard. Every future post requires verified quotes + timestamps before Lance drafts — no exceptions.
- **Scope gate decision:** All meaningful changes go through Keith (lead) before Pidge/Lance start work. This prevents rework and maintains voice consistency across continuity arcs.
- **Opening angle selection:** Title and framing decided AFTER transmissions are verified, not before. Week 9 title will reflect what actually happened (execution, threshold testing, etc.) not speculation.

### Week 9 Editorial Review (2026-04-27) — COMPLETED
- **Post APPROVED for publication.** Voice, structure, continuity, and technical assets all pass.
- **Arc progression documented:** Week 8 (active code inspection) → Week 9 (passive monitoring/waiting). Charlie shifted from doing to waiting — "external input capability: active" is the dominant signal.
- **quietcipher.dev handling validated:** Strategic hyperlinks placed in T2 (code archive), T5 (package hosting), and Unresolved (recovery correlation) — fulfills re-engagement goal without forcing context.
- **Status-check demotion pattern:** Lance correctly demoted Charlie's maintenance pings to Notes sections rather than full transmissions. This is now precedent for future posts with repetitive status messages.
- **csharpAndThen marker:** New trace type appeared at 33:22 Tuesday. Lance added contextual reference to T3 notes. Now has observational grounding before Unresolved question surfaces marker type differentiation.
- **Title choice validated:** "External Input Capability: Active" works both as factual summary and narrative invitation. Strong re-engagement angle.
- **On-screen narrative layer precedent:** Week 9 identified and documented visual overlay text as separate from chat messages. Sets precedent for tracking parallel narrative channel in future posts.
- **Nit resolution efficient:** All four identified nits addressed surgically by Lance without narrative restructuring. Voice maintained throughout revisions.
- **Key learnings for future posts:** 
  - New markers/patterns require contextual placement in Notes before Unresolved questions reference them
  - Repetitive status messages should be demoted to notes (not full transmissions) if they follow established pattern
  - On-screen narrative overlays are distinct observational layer; capture and format separately from chat quotes
  - quietcipher.dev hyperlinks can serve re-engagement goal when grounded in specific transmission context
