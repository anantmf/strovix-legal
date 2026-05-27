# Strovix - Testing with Public IPTV M3U URLs

## Quick Start: Testing with Public IPTV Playlists

This guide shows how to test the app using **publicly available IPTV m3u playlists** - no credentials required.

---

## Part 1: Adding a Public IPTV M3U Portal

### Step 1: Launch the App
1. Install and open **Strovix**
2. You will see the **Home Screen** with "No portal selected"
3. Tap **"Switch portal"** button (top right)

### Step 2: Add Portal Screen
You will see the **Portal Management Screen**
- If this is your first portal, you'll see an **"Add Portal"** or **"+"** button
- Tap it

### Step 3: Portal Configuration Form
The **Add Portal Screen** will display input fields:

### Step 4: Enter the Public IPTV M3U URL

**In the "Portal URL" field, copy and paste:**
```
https://iptv-org.github.io/iptv/index.m3u
```

**Leave these fields EMPTY:**
- Username: (blank)
- Password: (blank)
- MAC Address: (can be auto-populated or blank)

**Your screen should look like:**
```
┌─────────────────────────────────┐
│  Add New Portal                 │
├─────────────────────────────────┤
│  Portal URL                     │
│  https://iptv-org.github.io/iptv/│
│  index.m3u                      │
│                                 │
│  Username                       │
│  [ ]  (EMPTY)                   │
│                                 │
│  Password                       │
│  [ ]  (EMPTY)                   │
│                                 │
│  MAC Address                    │
│  [ ]  (auto)                    │
│                                 │
│              [Cancel] [Connect] │
└─────────────────────────────────┘
```

### Step 5: Connect to Portal
1. Tap the **"Connect"** button
2. The app will:
   - Download the m3u playlist
   - Parse the channel list
   - Show a loading indicator
3. Wait 3-5 seconds for the connection to complete

### Step 6: Success Screen
After successful connection, you will return to the **Home Screen** and see:
- Portal name displays: "iptv-org" or similar
- Content sections populated:
  - "Continue watching" (empty on first load)
  - "Recently watched live channels" (empty on first load)
  - "Favorites" (empty on first load)
  - "Live categories" (populated with channel categories)
 
Now you can test functionality of the app.
