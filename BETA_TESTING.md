# Strovix — Beta Tester Invitation

Thanks for helping me test Strovix! This is a modern IPTV player built for people who already have a portal subscription (Stalker / MAG / Xtream / M3U) and want a single app that plays well on **Android phones, tablets, and Android TV**.

**📱 Supported Platforms:**
- **Android Phone & Tablet** — Full IPTV streaming with all features
- **Android TV** — Optimized TV experience with remote control support
- **iOS** — Coming soon!

Below is everything you can poke at, plus a checklist of what I'd love feedback on.

strovixapp@gmail.com

---

## What is Strovix?

Strovix connects to your IPTV service and lets you watch:

- **Live TV** channels with a program guide (shows what's on now and coming up)
- **Movies** — browse a full catalog with descriptions, cover art, and ratings
- **TV Series** — watch episodes organized by season

The app works the same way on your phone, tablet, and TV. On Android TV, you control it with your remote.

---

## Supported Services

You can connect Strovix to most major IPTV services. Just paste your service URL and login credentials when setting up a profile. The app automatically detects what type of service you're using.

---

## Multi-Profile

You can save multiple services at once and switch between them. Each profile remembers:

- Your service URL and login
- A display name so you remember which service it is
- Your preferred timezone (for accurate program guides)
- Your login session, so you don't have to sign in again next time

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
- Filter out adult categories if you want (hidden by default)
- Sort by:
  - **Live TV** — by channel number or name
  - **Movies & Series** — by date added, name, year, or rating
- Search within each category
- **TV layout**: 4-column grid with a details panel on the right

### Universal Search
- Search across all your content at once
- Filter which types you want to search (movies, series, live TV)
- Remembers your preferences next time

### Series Detail
- Season picker (remembers your last viewed season per series)
- Episode list with download status icons
- Favorite toggle on the series
- Queue an episode for offline download

---

## The Player

**Playback speeds (VOD only):**
`0.5× · 0.75× · 1× · 1.25× · 1.5× · 1.75× · 2× · 2.5× · 3×`

**Skip forward and backward by:**
`10s · 15s · 30s · 1m · 2m · 5m · 10m · 15m · 30m`

You can customize these times. On TV, you can control them with your remote.

**On phone/tablet:**
Drag the blue dot on the progress bar to jump to any spot. Tap anywhere on the bar to seek.

**On TV:**
Use the left/right buttons on your remote to skip back or forward. Press OK to confirm.

**Aspect ratio** — Fit, Fill, Stretch (adjust in player menu).

**Mute** button.

**Send to another app** — Open the video in VLC or other media players on your device if you prefer.

---

## Subtitles

This is one of the most feature-rich parts of the app.

**Subtitle sources:**
- **Built-in subtitles** from your video
- **OpenSubtitles.com** — search and download subtitles right from the player
- **Your device** — pick a subtitle file from your phone or tablet
- **Online URL** — paste a link to a subtitle file

**Your subtitle choice is remembered** — if you pick a subtitle track for a movie, it automatically plays that track next time.

**Adjust timing** — if subtitles are out of sync, you can shift them earlier or later.

To use OpenSubtitles, add your login once in Settings (see the [OPENSUBTITLES SETUP](https://anantmf.github.io/strovix-legal/OPENSUBTITLES_SETUP) guide).

---

## Downloads (Offline Playback)

Long-press a VOD tile or hit the download button on a series episode to queue it.

- See download progress and status
- Set how many videos can download at once
- Optionally only download over Wi-Fi
- Clear downloaded videos when done
- Play downloaded videos anytime, even offline (no internet needed)

---

## Supported Devices

| Device | Optimized for |
|---|---|
| Android phone | Portait and landscape, touch controls, bottom menus |
| Android tablet | Landscape, multi-column layouts, side menu |
| Android TV / Fire TV | Remote control navigation, 4-column grids with details panel |

---

## TV-Specific Features

- Navigate the entire app with your remote
- **Focus styles:** Classic, High Contrast, Neon — pick what's easiest to see (Settings → UI)
- Optional haptic feedback on your remote
- Use your media remote buttons (play, pause, next, previous)
- On Live TV, left/right arrows change channels
- Press BACK to hide controls, press again to go back

---

## Settings (Highlights)

**Playback**
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
- OpenSubtitles username and password (optional but gives you more searches)
- Preferred subtitle language (English, Spanish, French, etc.)
- **Test your OpenSubtitles connection** button

**Catalog**
- Sort categories by recently visited or alphabetically
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
