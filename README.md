# <img src="images/logo.png" width="35" height="35"> Axon Bodycam Recorder

A realistic bodycam overlay application for FiveM roleplay, designed to simulate an authentic law enforcement bodycam experience with automatic recording management.

---

## 🆕 What's New

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

**This application may be flagged by antivirus software as a potential threat. This is a FALSE POSITIVE.**

### Why does this happen?
- This app is built with **Electron** (the same framework used by Discord, VS Code, Slack, etc.)
- The installer is **not code-signed** (code signing certificates cost $200-400/year)
- Antivirus software often flags unsigned applications as suspicious, even when they're completely safe
- This is extremely common with independent/hobby software projects

### What to do:
1. **Add an exception** in your antivirus for the installer and installation folder
2. **Windows Defender**: Click "More info" → "Run anyway" when the SmartScreen popup appears
3. The app does NOT contain any malware, spyware, or malicious code

---

## 📥 Installation

1. Go to the [**Releases**](https://github.com/Sharky999/Axon-Bodycam/releases) page
2. Download the latest `Axon Bodycam Recorder Setup x.x.x.exe`
3. Run the installer (you may need to bypass antivirus warnings - see above)
4. The app will install and launch automatically
5. Follow the license activation steps below

---

## 🔑 License Activation

This application requires a license key to use.
This is to prevent people from sharing this without my permission.
However it is a free application so once you receive a key you have access to the app forever.

**To get a license key:**
1. Contact **shrky999** on Discord
2. Request a license key
3. Enter the key in the activation window
4. Click "Activate License" (requires internet connection)

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
- Internet connection (for license activation and Evidence.com interface)
- ~200MB disk space

---

## 📞 Support

For support, license keys, or questions:
- Discord: **shrky999**

---

*This is a fan-made project for FiveM roleplay purposes. Not affiliated with Axon Enterprise, Inc.*
