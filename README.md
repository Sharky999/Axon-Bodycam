# <img src="images/logo.png" width="35" height="35"> Axon Bodycam Recorder

A **free** realistic bodycam overlay application for FiveM roleplay, designed to simulate an authentic law enforcement bodycam experience with automatic recording management.

**🎉 100% Free** - No license keys, no subscriptions, no paywalls. Just download and use!

<a href="https://ko-fi.com/sharkyaxon"><img src="https://ko-fi.com/img/githubbutton_sm.svg" alt="Support me on Ko-fi"></a>

---

## 🆕 What's New

### Version 1.1.4
- **Confirm Before Stop** - New optional feature that shows a confirmation popup before stopping recording. Prevents accidental stops when typing in-game (pressing Q in chat/reports). Enable with `confirmBeforeStop: true` in config. Default: off.

### Version 1.1.3
- **Category Folders** - New optional feature to automatically organize recordings into subfolders by category (e.g., `Traffic Stop/`, `Arrest/`). Enable with `enableCategoryFolders: true` in config. Only works when `enableReportTag` is also enabled.

### Version 1.1.0
- **Now 100% Free!** - No license keys required. Just download and use.
- **Smaller Installer** - Reduced from ~400MB to ~100MB by removing unnecessary build dependencies.
- **Improved Auto-Updates** - Better GitHub release integration for seamless updates.

### Version 1.0.7
- **OBS Browser Source Support** - Game Capture users can now use the overlay! Enable `enableCaptureWindow` in config and add `http://localhost:47890/overlay` as a Browser Source in OBS with true transparency.
- **"CHECK BROWSER" Notification** - When Evidence.com upload opens, an orange notification appears on the overlay reminding you to check your browser.
- **Auto-Config Migration** - New config options are automatically added to existing user configs on update.

---

## 📸 Screenshots

| Overlay Example | Recording Active | Muted State | Evidence Upload |
|:---:|:---:|:---:|:---:|
| ![Overlay](images/Example1%20Bodycamoverlay.png) | ![Recording](images/Whenrecordingexmp2.png) | ![Muted](images/MutedExample3.png) | ![Evidence Upload](images/ReportnumExample4.png) |

---

## ⚠️ Important: Antivirus False Positive Warning

**This application may be flagged by antivirus software as a "keylogger" or "info stealer". This is a FALSE POSITIVE.**

### Why does this happen?

#### 🔑 "Keylogger" Detection
This app uses **global hotkeys** that work even when you're in a game. To do this, it uses low-level keyboard hooks - the **same Windows API** that real keyloggers use. Antivirus software cannot tell the difference between:
- ✅ Our legitimate use (detecting when you press Q to start recording)
- ❌ A malicious keylogger (recording everything you type)

**The app only listens for YOUR configured hotkeys (Q, F9, F10, F11 by default). It does NOT record, store, or transmit any keystrokes.**

#### 📦 Unsigned Application
- The installer is **not code-signed** (certificates cost $200-400/year)
- This app is built with **Electron** (same framework as Discord, VS Code, Slack)
- Antivirus flags unsigned apps as suspicious, even when completely safe
- This is extremely common with independent/hobby software projects

#### 🔍 What gets flagged
| Detection Name | Why It's Wrong |
|----------------|----------------|
| Keylogger | We only listen for hotkeys, not all keystrokes |
| Info Stealer | We don't collect or send any personal data |
| Trojan | The code is open source - inspect it yourself! |

### What to do:
1. **Add an exception** in your antivirus for the installer and installation folder:
   - Installer: `Axon Bodycam Recorder Setup x.x.x.exe`
   - Install folder: `C:\Users\[You]\AppData\Local\Programs\axon-bodycam-recorder\`
2. **Windows Defender**: Click "More info" → "Run anyway" when SmartScreen appears
3. **VirusTotal**: Many engines flag it, but major ones (Microsoft, ESET, Kaspersky) typically don't

---

## 📥 Installation

1. Go to the [**Releases**](https://github.com/Sharky999/Axon-Bodycam/releases) page
2. Download the latest `Axon Bodycam Recorder Setup x.x.x.exe`
3. Run the installer (you may need to bypass antivirus warnings - see above)
4. The app will install and launch automatically
5. Configure your settings and you're ready to go!

---

## ⚙️ Setup & Configuration

### OBS Studio Setup (Required)

This app integrates with OBS Studio for recording. You need:

1. **Install OBS Studio** if you haven't already
2. **Enable OBS WebSocket:**
   - Go to `Tools` → `WebSocket Server Settings`
   - Check "Enable WebSocket Server"
   - Set a password (remember this!)
   - Default port is `4455`

3. **Enable Replay Buffer:**
   - Go to `Settings` → `Output` → `Replay Buffer`
   - Check "Enable Replay Buffer"
   - Set replay buffer length (recommended: 30-60 seconds)

4. **Set Recording Path:**
   - Go to `Settings` → `Output` → `Recording`
   - Set your desired recording path

5. **Recording Settings**
    - Go to `Settings` → `Output` → `Recording` (This is NOT where the finished bodycam evidences will be - they will be located in the config.json outputFolder) 
    - Set the encoder to `NVIDIA NVENC H.264` or the x264 CPU encoder for non-NVIDIA users
    - Set Recording Format to `MPEG-4 (.mp4)`
    - Set Audio Encoder to `FFmpeg AAC`

### Application Configuration

After first launch, a `config.json` file is created in:
```
C:\Users\[YourName]\AppData\Roaming\axon-bodycam-recorder\config.json
```

Edit this file to customize:

```json
{
  "player": "YOUR NAME",
  "agency": "YOUR DEPARTMENT",
  "callsign": "[000]",
  "outputFolder": "C:\\Videos\\Bodycam",
  "beepVolume": 0.5,
  "obsWebSocketPort": 4455,
  "obsWebSocketPassword": "your-obs-password",
  "enableReportTag": true,
  "enableRecordingLog": true,
  "enableCaptureWindow": false,
  "enableCategoryFolders": false,
  "confirmBeforeStop": false,
  "screenScale": 0.75,
  "evidenceCategories": [
    "Traffic Stop",
    "Arrest",
    "Use of Force",
    "Pursuit",
    "Investigation",
    "Domestic",
    "Community Contact",
    "Training",
    "Other"
  ],
  "keybinds": {
    "toggleRecording": "Q",
    "toggleMute": "F9",
    "powerOff": "F10",
    "toggleMoveMode": "F11"
  }
}
```

| Setting | Description |
|---------|-------------|
| `player` | Your character/officer name displayed on overlay |
| `agency` | Your department name displayed on overlay |
| `callsign` | Your unit callsign (e.g., "[301]") |
| `outputFolder` | Where merged recordings are saved |
| `beepVolume` | Volume of tones (0.0 - 1.0) |
| `obsWebSocketPort` | OBS WebSocket port (default: 4455) |
| `obsWebSocketPassword` | Your OBS WebSocket password |
| `enableReportTag` | Enable/disable Evidence.com upload prompt (true/false) |
| `enableRecordingLog` | Enable/disable recording log file (true/false) |
| `enableCaptureWindow` | Enable OBS Browser Source server for Game Capture users (true/false) |
| `enableCategoryFolders` | Organize recordings into subfolders by category (requires `enableReportTag: true`) |
| `confirmBeforeStop` | Show confirmation popup before stopping recording (prevents accidental stops) |
| `screenScale` | Size of the bodycam screen overlay (0.5 - 1.5) |
| `evidenceCategories` | Custom categories for the Evidence.com dropdown |
| `keybinds` | Custom keybindings (see Keybindings section) |

---

## ✨ Features

### 🎬 Realistic Bodycam Overlay
- Displays officer name, agency, callsign, and timestamp
- Shows recording status (REC indicator with duration)
- Authentic bodycam screen graphic

### 🔊 Realistic Audio Tones
- Power on/off tones
- Recording start/stop beeps
- Mute toggle feedback

### 📁 Evidence.com Style Upload
After each recording, a browser window opens with an **Evidence.com-style interface** where you can:
- Enter a report/case number
- Select an incident category (Traffic Stop, Arrest, Use of Force, etc.)
- Add detailed notes about the incident
- All information is logged to your Recording Log

**Benefits:**
- Looks and feels like the real Axon Evidence.com
- Can minimize the browser to look up report numbers
- All fields are optional - click "Skip" to save without details
- Automatically renames and organizes footage by report number
- Orange "CHECK BROWSER" notification appears on overlay when upload is ready

### 🛑 Confirm Before Stop (New in 1.1.4)
When enabled, pressing your recording key while recording will show a confirmation popup asking "End Recording?" instead of immediately stopping. This prevents accidental recording stops when typing in-game (chat, reports, etc.).

**Setup:**
1. Set `"confirmBeforeStop": true` in your `config.json`
2. When you press Q (or your recording key) while recording, a popup appears
3. Press **Enter** or click **Yes** to stop recording
4. Press **Escape** or click **No** to continue recording

**Note:** This is disabled by default to maintain current behavior for existing users.

### 📂 Category Folders (New in 1.1.3)
When enabled, recordings are automatically organized into subfolders based on the category you select in Evidence.com.

**Setup:**
1. Set `"enableCategoryFolders": true` in your `config.json`
2. Make sure `"enableReportTag": true` is also set (required)
3. When you stop recording, select a category in Evidence.com
4. Your recording will be saved in a subfolder named after the category

**Example folder structure:**
```
C:\Videos\Bodycam\
├── Traffic Stop\
│   └── 24-12345 - 2025-12-28_14-30-00.mp4
├── Arrest\
│   └── 24-67890 - 2025-12-28_15-45-00.mp4
├── Use of Force\
│   └── 24-11111 - 2025-12-28_16-00-00.mp4
└── Recording Log.txt
```

**Note:** If no category is selected, the recording saves to the root output folder as usual.

### 📝 Recording Log
- Automatically logs all recordings to `Recording Log.txt` in your output folder
- Each entry includes: date/time, player, agency, duration, filename, report number, category, and notes
- Can be toggled on/off via `enableRecordingLog` in config
- Example log entry:
  ```
  [12/19/2025 08:30:45 PM] B. MASON - ALABAMA SHERIFFS OFFICE | Duration: 02:35 | File: 25-1234 - 2025-12-19_20-30-45.mp4 | Report #: 25-1234 | Category: Traffic Stop | Notes: Vehicle stop on Main St, driver cited for speeding
  ```

### 🎥 Automatic Recording Management
- Integrates with OBS replay buffer
- Automatically merges buffer (pre-recording) with main recording
- Saves everything to your configured output folder

### 🖥️ Customizable Overlays
- Two overlay windows: info display + bodycam screen
- Fully repositionable with move mode
- Stays on top of fullscreen games
- Adjustable scale

### 🔄 Automatic Updates
- App automatically checks for updates on startup
- Prompts you when a new version is available
- One-click download and install

### 🎮 OBS Browser Source (For Game Capture Users)
If you use **Game Capture** instead of Display Capture, you can now add the overlay as a Browser Source!

**Setup:**
1. Set `"enableCaptureWindow": true` in your `config.json`
2. Restart the Bodycam app
3. In OBS: **Sources** → **Add** → **Browser**
4. **URL**: `http://localhost:47890/overlay`
5. **Width**: Your screen width (e.g., 1920)
6. **Height**: Your screen height (e.g., 1080)
7. Add this **Custom CSS**:
   ```css
   body { background-color: rgba(0,0,0,0); }
   ```
8. Click **OK** and position the Browser Source above your Game Capture

**Benefits:**
- True transparency (no green screen needed!)
- Overlay positions match your config settings
- Updates in real-time (recording status, timer, muted indicator)
- Works alongside the normal overlay for Display Capture users

---

## ⌨️ Keybindings

All keybinds can be customized in your `config.json` file. Default keybinds:

| Key | Action |
|-----|--------|
| `Q` | Toggle recording on/off |
| `F9` | Toggle mute |
| `F10` | Power off and exit application |
| `F11` | Toggle move mode (reposition overlays) |

### Custom Keybinds Example
To change keybinds, edit the `keybinds` section in your `config.json`:
```json
{
  "keybinds": {
    "toggleRecording": "R",
    "toggleMute": "F8",
    "powerOff": "F12",
    "toggleMoveMode": "F7"
  }
}
```

### Supported Key Names
| Key Type | Examples |
|----------|----------|
| Letters | `A`, `B`, `Q`, `R`, etc. |
| Function Keys | `F1`, `F2`, ... `F12` |
| Special Keys | `Delete`, `Backspace`, `Insert`, `Home`, `End`, `Space` |
| With Modifiers | `Ctrl+M`, `Alt+F4`, `Shift+F9`, `Ctrl+Shift+R` |

**Tip:** Avoid keys commonly used in games (WASD, E, R, Shift, Ctrl) for the recording toggle.

### Move Mode
1. Press your move mode key (default: `F11`) to enable move mode
2. Drag either overlay to your desired position
3. Press the key again or click to save positions
4. Positions are saved and remembered

---

## 🔧 Troubleshooting

### "INITIALIZING..." stuck on screen
- Make sure OBS is running
- Check OBS WebSocket is enabled and password matches config
- Verify OBS WebSocket port matches config (default: 4455)

### Recording not merging properly
- Ensure OBS Replay Buffer is enabled
- Check that your output folder exists and is writable
- Make sure OBS is recording to a compatible format (MP4 with AAC audio)

### Overlay not appearing over game
- The overlay uses "screen-saver" level always-on-top
- Some games with aggressive anti-cheat may block overlays
- Try running the game in borderless windowed mode

### Screen shows "REC FAILED"
- Ensure you disable recording keybinds in OBS settings
- Ensure you disable Replay keybinds in OBS settings

### Evidence.com page not opening
- Make sure you have a default browser set
- Check that port 47891 is not blocked by firewall
- The page will timeout after 5 minutes if not submitted

### Browser Source not showing in OBS
- Make sure the Bodycam app is running
- Verify `enableCaptureWindow` is set to `true` in config
- Try opening `http://localhost:47890/overlay` in your browser first
- Click "Refresh cache of current page" in OBS Browser Source properties
- Ensure the Browser Source dimensions match your screen size

---

## 📋 Requirements

- Windows 10/11
- OBS Studio with WebSocket plugin
- Internet connection (for Evidence.com interface and auto-updates)
- ~200MB disk space

---

## 📞 Support

For support or questions:
- Discord Server: **[Join Here](https://discord.gg/ErTSasyX)**
- Discord: **shrky999**

If you enjoy this free app, consider supporting development:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/sharkyaxon)

---

*This is a fan-made project for FiveM roleplay purposes. Not affiliated with Axon Enterprise, Inc.*
