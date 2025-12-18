# ⬡ Axon Bodycam Recorder

A realistic bodycam overlay application for FiveM roleplay, designed to simulate an authentic law enforcement bodycam experience with automatic recording management.

---

## 📸 Screenshots

| Overlay Example | Recording Active | Muted State |
|:---:|:---:|:---:|
| ![Overlay](images/Example1%20Bodycamoverlay.png) | ![Recording](images/Whenrecordingexmp2.png) | ![Muted](images/MutedExample3.png) |

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

1. Download `Axon Bodycam Recorder Setup 1.0.0.exe` from this repository
2. Run the installer (you may need to bypass antivirus warnings - see above)
3. The app will install and launch automatically
4. Follow the license activation steps below

---

## 🔑 License Activation

This application requires a license key to use.

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
  "screenScale": 0.75
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
| `enableReportTag` | Enable/disable report number prompt (true/false) |
| `screenScale` | Size of the bodycam screen overlay (0.5 - 1.5) |

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

### 📁 Report Number Organizer
- Prompts for a report/case number after each recording
- Automatically renames and organizes footage
- Can be toggled on/off via `enableReportTag` in config
- Perfect for organizing evidence by case number

### 🎥 Automatic Recording Management
- Integrates with OBS replay buffer
- Automatically merges buffer (pre-recording) with main recording
- Saves everything to your configured output folder

### 🖥️ Customizable Overlays
- Two overlay windows: info display + bodycam screen
- Fully repositionable with move mode
- Stays on top of fullscreen games
- Adjustable scale

---

## ⌨️ Keybindings

| Key | Action |
|-----|--------|
| `Q` | Toggle recording on/off |
| `F9` | Toggle mute |
| `F10` | Power off and exit application |
| `F11` | Toggle move mode (reposition overlays) |

### Move Mode (F11)
1. Press `F11` to enable move mode
2. Drag either overlay to your desired position
3. Press `F11` again or click to save positions
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
- Make sure OBS is recording to a compatible format

### Overlay not appearing over game
- The overlay uses "screen-saver" level always-on-top
- Some games with aggressive anti-cheat may block overlays
- Try running the game in borderless windowed mode

---

## 📋 Requirements

- Windows 10/11
- OBS Studio with WebSocket plugin
- Internet connection (for license activation)
- ~200MB disk space

---

## 📞 Support

For support, license keys, or questions:
- Discord: **shrky999**

---

*This is a fan-made project for FiveM roleplay purposes. Not affiliated with Axon Enterprise, Inc.*

