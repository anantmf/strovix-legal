# Strovix — Beta Tester Invitation

Thanks for helping me test Strovix! This is a modern IPTV player built for people who already have a portal subscription (Stalker / MAG / Xtream / M3U) and want a single app that plays well on **phone, tablet, and Android TV / Fire TV**.

Below is everything you can poke at, plus a checklist of what I'd love feedback on.

---

## What is Strovix?

A native React Native app that connects to your existing IPTV provider and plays:

- **Live TV** channels with EPG (program guide)
- **Movies (VOD)** — full catalog with metadata, posters, ratings
- **Series & Episodes** — multi-season hierarchy with episode picker

It runs the **same codebase** on phone, tablet, and Android TV. The TV build understands the D-pad / remote.

---

## Supported Portals & Formats

You can connect Strovix to:

- **Stalker / MAG portals** (standard `load.php`)
- **Generic portals** (`portal.php` variant for non-standard implementations)
- **M3U playlists** (plain `.m3u` / `.m3u8` URLs)

Auto-detect figures out which one your URL is when you set up a profile.

**Stream protocols played:** HLS (`.m3u8`), MPEG-TS, progressive MP4 / MKV, and anything ExoPlayer can decode (H.264, H.265 / HEVC, VP9, AAC, MP3, Opus, MP2 audio via FFmpeg renderer).

---

## Multi-Profile

You can save multiple portals at once and switch between them. Each profile stores:

- Portal URL + MAC address (for Stalker)
- Device ID, serial, signature (advanced — optional override)
- Concurrent fetch threads (1–N; default 5)
- Preferred timezone (for accurate EPG times)
- Display name
- Cached login token (skips re-handshake on next launch)

---

## Catalog Browsing

### Home Screen
- **Continue Watching** rail — 12 most recent VOD / episodes, newest first
- **Favorites** rail — live, movies, and series you've starred
- **Recent Live Channels** — last 12 channels you watched
- Recommended categories carousel

### Catalog Screen (per type)
- Category sidebar with two sort modes:
  - **Recent-first** — categories you've visited float to the top
  - **Alphabetical**
- Synthetic **★ Favorites** and **↻ Continue** rows pinned at the very top
- Adult / censored category filtering (hidden by default)
- Per-type sorts:
  - **IPTV** — by channel number, or A–Z
  - **VOD / Series** — recently added, A–Z, by year, by rating
- Infinite scroll with "Page X of Y" indicator
- Per-category client-side search
- **TV layout**: 4-column grid with an always-visible info pane on the right

### Universal Search
- Searches across IPTV / Movies / Series in parallel
- Per-type toggle (defaults: VOD + Series on, IPTV off because matches get noisy)
- Per-type "Load more" pagination
- Remembers your enabled types

### Series Detail
- Season picker (remembers your last viewed season per series)
- Episode list with download status icons
- Favorite toggle on the series
- Queue an episode for offline download

---

## The Player

**Playback speeds (VOD only):**
`0.5× · 0.75× · 1× · 1.25× · 1.5× · 1.75× · 2× · 2.5× · 3×`

**Configurable skip increments — back and forward independent:**
`10s · 15s · 30s · 1m · 2m · 5m · 10m · 15m · 30m`

You adjust them with inline **−** / **+** buttons directly under each skip button on the transport row (D-pad reachable on TV).

**Draggable thumb on mobile / tablet**
Medium blue dot on the seek bar. Drag it to scrub. Tap anywhere on the bar to seek directly.

**TV D-pad seek bar**
When the seek bar is focused: LEFT / RIGHT seeks by your current increment, OK commits immediately, BACK cancels and restores playback state.

**Aspect ratio** — Fit, Fill, Stretch (cycle via in-player menu).

**Mute** button.

**External player launch** — VLC, MX Player Free, MX Player Pro, system chooser, or a custom Android package name. Passes the resume position + title + headers as an Intent.

---

## Subtitles

This is one of the most feature-rich parts of the app.

**Formats supported:**
- **SRT** (SubRip)
- **VTT** (WebVTT)
- **TTML / DFXP / XML**

**Sources:**
- **Embedded tracks** that the stream itself advertises
- **OpenSubtitles.com** — search and download from inside the player
- **Local file** picker (Android) — load an SRT / VTT from your device
- **Remote URL** — paste an HTTP(S) link to a subtitle file

**Per-content persistence** — your subtitle choice for a movie / episode is remembered. Next time you play it, your track is auto-selected.

**Subtitle delay (offset)** — slide cues earlier or later in 0.1 s and 0.5 s steps from MENU → SUBTITLES.

**OpenSubtitles credentials** are entered once in Settings (see the separate `OPENSUBTITLES_SETUP.md` guide).

---

## Downloads (Offline Playback)

Long-press a VOD tile or hit the download button on a series episode to queue it.

- Status: queued → downloading → completed (or failed / paused)
- Configurable max concurrent downloads (default 1)
- Optional Wi-Fi only toggle
- Downloads screen with active / completed / failed counts, total storage used
- Bulk "clear all completed" with confirmation
- Offline playback works **without portal connection** — content plays straight from disk, posters and titles preserved

---

## Form Factor Support

| Device | What's tuned for it |
|---|---|
| Android phone | Portrait + landscape, status bar auto-hides in player, swipe-friendly hit targets, bottom-sheet menus |
| Android tablet | Landscape-primary, multi-column grids, right-side menu drawer |
| Android TV / Fire TV | D-pad, 4-column grids, info pane, focus-aware Pressables, TVFocusGuideView focus trapping, Leanback launcher entry, 320×180 banner asset |
| iOS phone | Portrait + landscape (no native brightness — uses dim overlay) |
| iOS tvOS | Apple TV 4th gen+ via Siri Remote |

**OS requirements:** Android 11+ (API 30+), iOS / tvOS 13+.

---

## TV-Specific Features

- D-pad navigation across the entire app (Home, Catalog, Search, Player, Settings)
- TV-specific Pressable with working `onFocus` / `onBlur` (this is patched in our `TVPressable` component because RN-tvOS 0.81 doesn't dispatch focus events through the regular bridge)
- **Focus styles:** Classic, High Contrast, Neon (Settings → UI)
- Optional D-pad haptic feedback
- **TV Focus Debug Overlay** — yellow outline around the focused view, tag name, bounds, and last 10 focus transitions (Settings → Playback → "Show focus debug overlay")
- Hardware media keys (PLAY / PAUSE / NEXT / PREV) routed to the playback controller
- Channel zap on the live HIDDEN chrome (LEFT / RIGHT changes channel)
- BACK button: first press hides chrome, second press exits

---

## Settings (Highlights)

**Playback**
- Use Internal Player v2 (beta) — on / off
- Use VLC fallback adapter — on / off
- External player target: System chooser / VLC / MX Free / MX Pro / Custom package
- Always open externally — on / off
- Seek back step / forward step (independent)
- Show focus debug overlay (TV)

**UI**
- Theme — dark / light / slate / OLED
- TV focus style — classic / high-contrast / neon
- D-pad haptics — on / off

**Subtitles**
- OpenSubtitles API key
- OpenSubtitles username + password (optional but recommended — boosts your daily quota)
- Preferred subtitle language (ISO-639-1: `en`, `es`, `fr`, …)
- App User-Agent (defaults to `Strovix v1.0`; only change if you registered a different consumer name)
- **Test OpenSubtitles connection** button

**Catalog**
- Category sort mode — recent-first / alphabetical
- Per-type sort overrides (IPTV / VOD / Series)
- Hide adult / censored content — on / off (default: on)

**Backup**
- Export backup (JSON: profiles + settings + favorites + resume history)
- Import backup with per-section checkboxes (settings only, profiles only, all)
- Save backup to Downloads folder

**Cloud Sync (optional)**
- Neon-based account: profiles + settings + favorites + watch history roam across your devices
- Manual "Sync now" button
- Sign in / sign out

**Ads**
- Watch a rewarded video → **4-hour ad-free window**, synced to cloud so unlocking on your phone also disables ads on your TV

**Advanced**
- Request log: enable, console mirror, full-body capture
- Export logs as **HAR 1.2** (Chrome DevTools / Fiddler / Postman compatible) or plain text
- Portal account info (subscription status, MAC, login)
- Factory reset

---

## Diagnostics

If something breaks, please grab one of these so I can debug:

- **Stream URL** — in the player, open MENU → DIAGNOSTICS → tap "Stream URL" (copies the resolved playable URL)
- **Request log** — Settings → Advanced → Request log → export HAR (or text)
- **Focus debug overlay** — Settings → Playback (TV only)
- **Player error banner** — appears centered in the player with a "Go back" button if a stream fails

---

## Persistence — What's Saved Where

Everything is stored locally on your device. With cloud sync enabled, the important slices roam through a cloud acrosss devices.

- **Profiles** (portals, active profile)
- **Settings** (every preference above)
- **Favorites** (per-profile, per-type)
- **Continue Watching** (resume position + duration + item snapshot)
- **Catalog cache** (categories, paging state, last category visited, last season per series)
- **EPG cache** (program listings with auto-refresh debounce)
- **Subtitles** (selected track per content, local files, remote URLs)
- **Downloads** (queue with status / progress / file paths)
- **Cloud auth token** (when signed in)


---

## Known Limitations (v2.0)

A few things are stubbed in the new player and will land in v2.1:

- **Audio track switching** — UI shows a placeholder "Coming soon" row
- **Manual quality / bitrate selector** — "Auto" only for now
- **Episodes menu inside the player** — currently routes you back to the Series Detail screen (works but extra tap)

Other notes:
- **No casting / Chromecast** support yet
- **No Picture-in-Picture** yet
- **No web build** (a stub exists; phone / tablet / TV are the targets)
- Internal Player v2 is **off by default** during the v2.0 smoke test — flip the toggle in Settings → Playback

---

## What I'd Love You to Test (Beta Checklist)

Copy this into a text file or just keep it open while you play.

- [ ] **Setup**: add your portal (Stalker / generic / M3U). Did auto-detect pick the right type? Did login work first try?
- [ ] **Multiple profiles**: add a second profile and switch between them.
- [ ] **Live TV**: zap channels (prev / next within a category). Does the EPG "Now / Next" look right for your timezone?
- [ ] **VOD**: play a movie, scrub with the dot, tap-to-seek anywhere on the bar.
- [ ] **Resume**: kill the app mid-movie, relaunch, check that "Continue Watching" remembers your position.
- [ ] **Series**: open a series, switch seasons, pick an episode, come back later — does it return you to the same season?
- [ ] **Skip steps**: change the back / forward increments using the inline **−** / **+** buttons (try the extremes: 10 s and 30 m). On TV, can you reach them with D-pad DOWN?
- [ ] **Playback speed**: cycle from 1× up to 3× on a VOD. Speed should reset when you start a new title.
- [ ] **Subtitles**: enter your OpenSubtitles credentials (separate guide), search for a movie's subs from inside the player, download, play. Try the delay adjuster.
- [ ] **Aspect ratio**: cycle Fit / Fill / Stretch on a movie that isn't 16:9.
- [ ] **Brightness / mute** (phone): try the brightness slider (Android only — iOS uses an overlay) and mute button.
- [ ] **External player**: set "VLC" as your external target and play something. Does the resume position carry over?
- [ ] **Downloads**: queue a movie, kill Wi-Fi, can you still play it? Cancel an in-progress download. Clear all completed.
- [ ] **Favorites**: star a movie, a series, and a channel. Restart the app — are they still starred?
- [ ] **TV D-pad**: navigate everything with only the remote. Anywhere you can't reach a button? Anywhere focus gets lost?
- [ ] **TV focus debug overlay**: enable it in Settings → Playback. Anything weird in the focus history?
- [ ] **Broken channels**: when a live stream fails, does the channel get marked? Does it recover when it works again?
- [ ] **Backup**: export a backup JSON, factory reset, re-import. Did everything come back?
- [ ] **Cloud sync** (optional): sign in on phone + TV, change a setting on one, verify it shows up on the other.
- [ ] **Ads** (if you see them): does the rewarded video actually unlock a 4-hour ad-free window? Does it sync to your other device?
- [ ] **Universal search**: search a title that exists in both your VOD and series catalogs. Are the per-type buckets correct?
- [ ] **Censored content toggle**: with the toggle off, are adult categories visible? Toggle on — do they disappear instantly without a portal refetch?

---

## Reporting Bugs

If something goes wrong, please send me:

1. **Device + OS version** (e.g. "Pixel 7, Android 14" or "Fire TV Stick 4K, Fire OS 7")
2. **Portal type** (Stalker / generic / M3U)
3. **What you did** (steps to reproduce, even rough)
4. **What you expected** vs **what happened**
5. **If a stream issue**: the **Stream URL** from MENU → DIAGNOSTICS in the player
6. **If a network issue**: an **HAR export** from Settings → Advanced → Request log

Screenshots and screen recordings are gold. Don't worry about polish — even a paragraph of "hey this broke when I did X" is hugely useful.

---

## Thanks

Genuinely — beta testing is unglamorous work and you're saving me from shipping bugs to a wider audience. If you find a really weird edge case, I want to hear about it. Have fun!
