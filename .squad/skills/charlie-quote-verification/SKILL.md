---
name: "charlie-quote-verification"
description: "Methodology for verifying Charlie chatbot quotes and timestamps in blog posts using YouTube live chat replay data"
domain: "video-analysis"
confidence: "medium"
source: "earned"
tools:
  - name: "yt-dlp"
    description: "YouTube content downloader with live chat replay extraction capability"
    when: "Extract chat messages and exact timestamps from YouTube video recordings"
  - name: "Playwright"
    description: "Browser automation for visual verification"
    when: "Screenshot YouTube chat replay for visual proof of Charlie's message presence"
---

## Context

When blog posts document Charlie the chatbot's transmissions with timestamps and quotes, we need a verified connection between the text and the actual YouTube stream where Charlie appeared. The challenge: Charlie's messages appear in Twitch chat first, then are relayed to YouTube chat by a restream bot with a specific format. We must extract the exact moment Charlie appeared and verify timestamps are accurate within ~1 minute tolerance. This skill provides the repeatable methodology for Week N verification work.

## Patterns

### Primary Method: Live Chat Replay Download

**Tool:** `yt-dlp` (installed at `C:\Users\jefritz\AppData\Local\Python\pythoncore-3.14-64\Scripts\yt-dlp.exe`)

**Command template:**
```bash
yt-dlp --skip-download --write-sub --sub-lang "live_chat" --sub-format json -o "{output_dir}/{video_id}" "https://www.youtube.com/watch?v={VIDEO_ID}"
```

**Chat JSON file structure:** The output is a JSONL file (one JSON object per line). Each line contains a replay chat item with these key fields:

```json
{
  "replayChatItemAction": {
    "videoOffsetTimeMsec": 1800000,
    "actions": [{
      "addChatItemAction": {
        "item": {
          "liveChatTextMessageRenderer": {
            "message": {
              "runs": [{"text": "...message content..."}]
            },
            "authorName": {
              "simpleText": "username"
            }
          }
        }
      }
    }]
  }
}
```

**Key fields for Charlie verification:**
- `replayChatItemAction.videoOffsetTimeMsec` — milliseconds since video start (THE critical timing field)
- `replayChatItemAction.actions[].addChatItemAction.item.liveChatTextMessageRenderer.message.runs[].text` — message content (concatenate all `runs` to get full text)
- `replayChatItemAction.actions[].addChatItemAction.item.liveChatTextMessageRenderer.authorName.simpleText` — sender name

### Finding Charlie Messages in Chat

**Relay format:** Charlie messages from Twitch (`charliebotai` bot) are relayed to YouTube chat by `@restreambot4225` with this format:
```
[Twitch: charliebotai] {message text}
```

**Search strategy:**
1. Filter the chat JSON for lines containing `"charliebotai"` (case-insensitive)
2. Extract `videoOffsetTimeMsec` from each match
3. Convert milliseconds to seconds and minutes: `seconds = offset_ms / 1000`, `minutes = int(seconds // 60)`

### The csharpTrace Marker Pattern (Critical for Blog Timestamps)

**Pattern:** Chat messages containing the string `csharpTrace` are KEY TIMING MARKERS for when Charlie's narrative appears in the stream.

**Why it matters:** The actual narrative quotes in the blog (e.g., "Anomaly detected...") are authored fiction by the team and do NOT appear verbatim in chat. The `csharpTrace` messages are the closest identifiable signal for when Charlie "appears" or becomes active in the stream context.

**Alignment:** `csharpTrace` timestamps closely match the blog's "X-minute mark" timestamps, typically within ±1 minute tolerance. This is how we verify that a blog post's claimed 30-minute transmission actually occurred near the 30-minute mark in the video.

**Example alignment (Week 8):**
- Blog claims: "30-minute mark"
- Actual `csharpTrace` in chat: 30:12 (1800 seconds) ✅
- Blog claims: "90-minute mark"
- Actual `csharpTrace` in chat: 90:12 (5412 seconds) ✅

### Embedding YouTube Timestamps in Blog Posts

**Formula for embed start parameter:**
```
start = floor(videoOffsetTimeMsec / 1000) - 4
```

**Why -4 seconds?** This gives viewers 3-5 seconds of lead-in before Charlie's message drops in chat. Viewers see the build-up to Charlie's appearance rather than starting in the middle of a message.

**Example:**
- `csharpTrace` at 1800000 ms (30:00) → `start = floor(1800000 / 1000) - 4 = 1796` → embed with `?start=1796`
- Video plays from 29:56, giving 4 seconds before the 30:00 message

**Embed code template (iFrame format used in signal-archive):**
```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/{VIDEO_ID}?si={SI_PARAM}&amp;start={START_SECONDS}" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
```

### Python Script for Extracting Charlie Messages

Use this pattern to extract all `charliebotai` messages from a chat JSON file:

```python
import json

def extract_charlie_messages(chat_json_file):
    results = []
    with open(chat_json_file, 'r', encoding='utf-8') as f:
        for line in f:
            try:
                data = json.loads(line)
            except json.JSONDecodeError:
                continue
            
            actions = data.get('replayChatItemAction', {}).get('actions', [])
            offset_ms = int(data.get('replayChatItemAction', {}).get('videoOffsetTimeMsec', 0))
            
            for action in actions:
                renderer = action.get('addChatItemAction', {}).get('item', {}).get('liveChatTextMessageRenderer', {})
                if renderer:
                    author = renderer.get('authorName', {}).get('simpleText', '')
                    msg_parts = renderer.get('message', {}).get('runs', [])
                    msg = ''.join(part.get('text', '') for part in msg_parts)
                    
                    # Check for Charlie indicators
                    if 'charliebotai' in msg.lower() or 'charliebotai' in author.lower():
                        secs = offset_ms / 1000
                        mins = int(secs // 60)
                        
                        # Flag if this message contains the csharpTrace timing marker
                        has_trace = 'csharpTrace' in msg
                        
                        results.append({
                            'offset_ms': offset_ms,
                            'seconds': secs,
                            'minutes': mins,
                            'minutes_seconds': f"{mins}:{int(secs % 60):02d}",
                            'message': msg,
                            'is_timing_marker': has_trace
                        })
    
    return results
```

### Secondary Method: Playwright Screenshots (Video Element Only)

**Purpose:** Capture visual snapshots of the video player at each transmission moment. Extract **video element only**, explicitly excluding YouTube header, sidebar, chat, recommendations, comments, overlays, and browser chrome.

**Selectors and Element Structure:**
- Primary video element selector: `.html5-main-video` (the actual video `<video>` tag inside the player)
- Player container selector: `#movie_player` (wraps the video with controls)
- **Exclusions:** Do not capture `ytd-player` (outer wrapper), `yt-live-chat-renderer` (chat panel), `ytInitialData` overlays, recommendation sidebar, comment sections, or page header
- For element-screenshot approach: target the player container (`#movie_player`) to include video + native controls but exclude all surrounding UI

**Method:**
1. Navigate to YouTube watch page at specific timestamp: `https://www.youtube.com/watch?v={VIDEO_ID}&t={SECONDS}`
2. Wait for video player to load: `page.wait_for_load_state('networkidle')`
3. **Locate and wait for the video player element** (not the page):
   - Use selector: `page.locator('#movie_player')`
   - Wait for visibility: `await player_locator.wait_for(state='visible')`
4. **Screenshot the player element only** — use Playwright element screenshot (not full page):
   - Call: `await player_locator.screenshot(path=output_path)`
   - This captures ONLY the `#movie_player` div and its contents (video + controls)
   - Everything outside the player (sidebar, chat, header, footer) is excluded
5. Save screenshot with naming convention: `charlie-week{N}-{sequence}-{videoId}-{timestamp}s.png`

**Playwright code pattern:**
```python
import asyncio
from playwright.async_api import async_playwright

async def capture_video_element(video_id: str, start_seconds: int, output_path: str):
    async with async_playwright() as p:
        browser = await p.chromium.launch(headless=True)
        page = await browser.new_page()
        
        # Navigate to YouTube with timestamp
        await page.goto(f"https://www.youtube.com/watch?v={video_id}&t={start_seconds}", wait_until='networkidle')
        
        # Locate the video player container
        player = page.locator('#movie_player')
        
        # Wait for player to be visible and ready
        await player.wait_for(state='visible', timeout=10000)
        
        # Screenshot ONLY the video player element
        # This excludes: header, sidebar, chat panel, recommendations, comments, overlays
        await player.screenshot(path=output_path)
        
        await browser.close()
```

**What the screenshot will contain:**
- ✅ Video playback area
- ✅ Player controls (play/pause, timeline, volume, fullscreen button)
- ✅ Video duration/current time display

**What the screenshot will NOT contain:**
- ❌ YouTube header (logo, search bar, notifications)
- ❌ Chat replay panel (right sidebar)
- ❌ Recommendations sidebar (right panel)
- ❌ Comments section (below video)
- ❌ Video title, description, channel info
- ❌ Browser address bar and tabs

**Key advantage:** Element screenshot isolation gives clean, minimal thumbnails suitable for blog embed covers and visual documentation.

**Limitations:**
- Not suitable for precise timing extraction (visual frame rates vary)
- YouTube player load time can be variable; consider increasing `wait_for` timeout if needed
- Headless mode may render player differently than headed mode (test both if quality issues arise)
- Use for **visual documentation only**; rely on `csharpTrace` markers for timing ground truth

## Examples

### Week 8 Verification Session (Complete Example)

**Context:** Post needed to verify 11 Charlie transmissions embedded in blog with timestamps. Used chat replay method.

**Videos processed:**
- Monday April 13: Video ID `5739RGIMPyU`
  - 30-minute transmission verified at 30:12 (csharpTrace marker aligned) ✅
  - 90-minute transmission verified at 90:12 (csharpTrace marker aligned) ✅
  - Embedded with: `?start=1796` (30:00 - 4s) and `?start=5396` (90:00 - 4s)

- Tuesday April 14: Video ID `cuj0Ny9KrVI`
  - 20-minute transmission verified at 20:48 ✅
  - 55-minute transmission verified at 55:48 ✅
  - 85-minute transmission verified at 85:46 ✅
  - 110-minute transmission verified at 110:46 ✅
  - Embedded with corresponding start parameters

- Thursday April 16: Video ID `FT0J4FPBy7M`
  - ⚠️ First transmission at 46:22, but blog claimed 30-minute mark — 16-minute discrepancy
  - **Root cause:** Pre-show/countdown period offset stream timing relative to expected schedule
  - Remaining transmissions verified: 90:54, 140:16, 190:47, 230:09
  - Embedded all 5 with adjusted start parameters

**Outcome:** All 11 transmissions successfully embedded with verified timestamps.

## Anti-Patterns

### ❌ DO NOT USE: YouTube Auto-Generated Transcripts

**Why:** Auto-generated captions only capture spoken audio (host talking), NOT on-screen text or chat messages. They are completely useless for finding Charlie's text-based chat messages.

**Additional blockers:**
- Manual (CC1) caption tracks often have identical garbled auto-generated content
- YouTube API aggressively rate-limits and IP-blocks transcript requests (blocked after ~3 video fetches)
- `youtube-transcript-api` Python library and `yt-dlp` subtitle downloads are both blocked quickly
- **Verdict:** Completely useless for chat-based content verification. Never attempt this path.

### ❌ Assumption: Narrative Quotes = Exact Chat Text

**Wrong:** The blog posts contain narrative fiction written by the team (e.g., "Anomaly detected in recovery matrix..."). These quotes do NOT appear verbatim in chat. The actual Charlie messages in chat are typically brief (single word, short phrase, encoded data).

**Right:** Verify the **timing** (does a `csharpTrace` marker appear near the claimed minute mark?), not the exact quote text. The narrative quotes are interpretations/context for the reader.

### ❌ No Timestamp Adjustment = Embedded Videos Start at Wrong Moment

**Wrong:** Using `?start={offset_ms / 1000}` directly without the -4 second buffer.

**Right:** Always use `start = floor(offset_ms / 1000) - 4` to give viewers lead-in time.

### ❌ Ignoring Pre-Show Offsets

**Issue:** Countdown periods or pre-show segments can shift the actual timing of stream content relative to the schedule (e.g., Thursday April 16 had a 16-minute pre-show offset).

**Right:** If the first transmission's verified timestamp is significantly off from the blog's expected timestamp, assume a pre-show offset and adjust subsequent expectations accordingly.

## Known Limitations

- **Pre-show/countdown periods:** Stream timing can drift from published schedule. First transmission may be offset significantly; use it as the calibration point.
- **Chat replay file size:** JSON files typically 400-600KB per video — account for download/processing time
- **YouTube API blocking:** Transcript APIs get blocked quickly if hammered. Use live chat replay only.
- **Rate-limiting:** Avoid downloading too many videos in rapid succession (YouTube may throttle)
- **Stream schedule context:** Most streams are Tuesday & Thursday 9am ET on twitch.tv/csharpfritz, but schedule can vary

## Verification Checklist

When verifying a blog post before publication:

- [ ] YouTube video IDs confirmed and accessible
- [ ] Chat replay files downloaded for each video using yt-dlp
- [ ] Charlie messages extracted via `charliebotai` search filter
- [ ] `csharpTrace` markers found for each claimed transmission ±1 minute tolerance
- [ ] Embed start parameters calculated: `floor(offset_ms / 1000) - 4`
- [ ] All embeds placed in blog post post-blockquote, pre-Notes section
- [ ] Blank lines before/after each embed for readability
- [ ] Test embeds in preview to verify correct timestamp playback
- [ ] Optional: Playwright screenshots captured for visual proof (can be stored as notes)
