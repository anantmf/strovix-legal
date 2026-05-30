# Setting up OpenSubtitles in Strovix

Strovix can search and download subtitles directly from **OpenSubtitles.com** while you're watching something. To do that, the app needs **your own** OpenSubtitles **API key** (and ideally a free account login too).

This guide walks you through it end-to-end. Should take about 5 minutes.

---

## Why do I need my own API key?

OpenSubtitles requires every app that talks to their API to identify itself with a per-developer (or per-user) consumer key. Sharing a single key across thousands of users would get it rate-limited and revoked instantly, so Strovix doesn't ship one. You get your own — it's free — and you control the daily download quota tied to it.

**With just an API key** (anonymous): a small daily download quota (a handful of subs per day).

**With API key + username + password**: a much larger daily quota (usually 20–100 downloads/day depending on your account tier). Recommended.

---

## Step 1 — Create a free OpenSubtitles.com account

1. Open <https://www.opensubtitles.com/en/users/sign_up> in a browser.
2. Sign up with an email + password.
3. Open the confirmation email they send you and click the link to verify.

> ⚠ **Important:** OpenSubtitles has **two** sites that look similar:
> - **opensubtitles.com** ← the modern one with the REST API. *This is the one you want.*
> - **opensubtitles.org** ← the legacy site with the old XML-RPC API. **Don't use this one.**
>
> If you accidentally sign up on `.org`, your credentials won't work in Strovix.

Save your username and password — you'll need both in Step 3.

---

## Step 2 — Get your API key

1. Sign in at <https://www.opensubtitles.com/>.
2. Open the developer area: <https://www.opensubtitles.com/en/consumers>
3. Click **"+ NEW CONSUMER"** (or "Register a new consumer" — wording changes occasionally).
4. Fill in the form:
   - **Name** — anything you like, e.g. `Strovix Personal` or your name. **Remember this exact string — you'll paste it into Strovix in Step 3 as the User-Agent.**
   - **Description** — short note, e.g. "Personal use with Strovix IPTV player".
   - **Website / Homepage** — optional. You can leave it blank or put any URL.
5. Submit. The page reloads showing your new consumer.
6. Click on the consumer's name → you'll see a long string labeled **API key**.
7. **Copy that API key.** Treat it like a password — don't share it publicly.

---

## Step 3 — Enter the credentials into Strovix

1. Open Strovix.
2. Go to **Settings**.
3. Scroll to the **Subtitles (OpenSubtitles)** section and expand it.
4. Fill in the fields:

   | Field | What to put in |
   |---|---|
   | **OpenSubtitles API key** | The long API key string from Step 2. **Required.** |
   | **OpenSubtitles username (optional)** | Your `.com` account username from Step 1. *Recommended.* |
   | **OpenSubtitles password (optional)** | Your `.com` account password from Step 1. *Recommended.* |
   | **Preferred subtitle language** | An ISO-639-1 code: `en` for English, `es` for Spanish, `fr` for French, `de` for German, `it`, `pt`, `ru`, `ar`, `hi`, `ja`, `zh`, etc. Default is `en`. |
   | **App User-Agent** | The **exact** consumer name you registered in Step 2. If you used the default consumer name, leave this as `Strovix v1.0`. **This must match what's on your OpenSubtitles consumer dashboard or the API will reject your requests.** |

5. Tap **"Test OpenSubtitles connection"**.
   - ✅ "Connection looks good" → you're done.
   - ❌ Error message → see Troubleshooting below.

---

## Step 4 — Use it during playback

1. Start playing any movie or episode.
2. Open the in-player menu (icon row on TV, or tap the screen to bring up the chrome on phone).
3. Tap **SUBTITLES**.
4. Tap **"Search & download subtitles…"** at the bottom of the list.
5. The subtitle search dialog opens with your content's title pre-filled. Adjust if needed.
6. Pick a result from the list — Strovix downloads it and switches to it automatically.

Subtitles you download are **remembered per movie / episode** — the next time you play that title, Strovix auto-selects the same track.

You can also **adjust the timing** of any track inside the SUBTITLES menu using the **−0.5s / −0.1s / Reset / +0.1s / +0.5s** buttons. Useful when subs are out of sync with the audio.

---

## Where credentials are stored

Your API key, username, and password are stored **locally on your device** in the app's private storage (AsyncStorage), not on any remote server (unless you've enabled Cloud Sync, in which case they roam between **your** devices via your private Neon-backed account).

They are **not encrypted at rest** inside the app sandbox — this matches how most apps store API tokens. On a rooted / jailbroken device anyone with full filesystem access could read them, so:

- Don't reuse a password you care about for your OpenSubtitles account.
- If you suspect a leak, log in at opensubtitles.com → developer consumers → revoke the API key and generate a new one.

---

## Troubleshooting

### "Connection looks good" doesn't appear / error says **401 Unauthorized**

- Your **API key** is wrong or doesn't match the User-Agent.
- Double-check: copy the API key fresh from the consumer dashboard, and make sure the **App User-Agent** in Strovix is **exactly** the consumer name (case-sensitive, including spaces and version numbers).
- If your consumer is named `My App 1.0` on opensubtitles.com, the User-Agent field in Strovix must say `My App 1.0` — not `MyApp1.0`, not `My App 1`, exactly that.

### Error says **403 Forbidden** or **You are not logged in**

- You're trying to download but no username / password is set.
- Add your account credentials (Step 3) and tap Test again.

### Error says **429 Too Many Requests** / **Quota exceeded**

- You've hit your daily download limit.
- Without login: very low quota (anonymous tier).
- With login: usually 20–100/day depending on account age.
- VIP accounts on opensubtitles.com get a higher limit — that's a paid tier on their site, totally optional.
- Quotas reset at 00:00 UTC.

### Error says **Wrong username or password**

- The username / password is for **opensubtitles.com**, not `.org`. Make sure you created the account on the right site.
- Try logging in via the web at <https://www.opensubtitles.com/> with the exact same credentials to confirm they work.

### Search returns no results even though I know the movie has subtitles

- Try a shorter or more generic search query (just the title, no year).
- Change the **Preferred subtitle language** field to the language you actually want.
- Some very new releases simply don't have subs uploaded yet.

### Subtitles download but don't appear on screen

- Make sure the track is actually selected (a `✓` shows next to the active one in the SUBTITLES menu).
- Check the **Subtitle delay** isn't pushed way out of sync — tap "Reset to 0" in the menu.
- A few uploaded subs are mislabeled or in the wrong format. Try a different result.

---

## Privacy

- Strovix sends your API key and (if provided) your account credentials **only** to `api.opensubtitles.com` — nowhere else.
- No analytics, no telemetry, no third-party identifiers tied to your subtitle activity.
- You can audit every HTTP request the app makes from **Settings → Advanced → Request log**.

---

That's it. Once it's set up you'll basically forget about it — open the menu, search, pick a subtitle, watch. Enjoy.
