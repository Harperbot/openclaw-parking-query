# 🅿️ openclaw-parking-query

[繁體中文](README.md) | English

A real-time parking query OpenClaw Skill for Taiwan. Send a location pin or a Google Maps URL via Telegram, LINE, or iMessage, and the assistant will instantly reply with nearby available parking lots and one-click navigation links.

**🔥 What's new in v1.2.0:**
* 🚀 **Native OpenClaw Plugin Support**: Added `openclaw.plugin.json`. You can now install it directly via ClawHub and manage API Keys without manually editing `openclaw.json`.
* ✨ **Markdown Output Optimization**: Upgraded lengthy URLs to clean Markdown Inline Links (e.g., `[🍎 Apple Maps Nav]`).
* 🗺️ **Enhanced Google Maps Parsing**: Better redirect resolution and automatic fallback to Nominatim geocoding when coordinates are missing from the URL.
* 🏙️ **Cross-City Smart Search**: Automatically fetches New Taipei City data when you are near the Taipei City border.

## Features

- **Smart Mode Detection**: If your message contains time-related words ("tomorrow", "afternoon"), it switches to Future Mode (shows locations only). Pure location pins trigger Real-time Mode (shows available parking spaces).
- **Three Input Formats**: Supports Telegram/LINE location pins, Google Maps short URLs (`maps.app.goo.gl/xxx`), and full Google Maps URLs.
- **Dynamic Search Radius**: Starts searching within 500 meters; if no results are found, it automatically expands to 1 kilometer.
- **One-Click Navigation**: Every result includes direct links to Apple Maps and Google Maps navigation.
- **Native Support**: Perfectly integrates with the OpenClaw 2026 architecture.

## Prerequisites

### 1. OpenClaw
Please install and configure [OpenClaw](https://github.com/openclaw/openclaw) first.

### 2. TDX API Keys (Free)
Register an account at [tdx.transportdata.tw](https://tdx.transportdata.tw) to obtain your `Client ID` and `Client Secret`.

### 3. Python Packages
```bash
pip3 install requests
```

## Installation

### Method 1: Via ClawHub (Recommended)
```bash
clawhub install openclaw-parking-query
```
After installation, open the OpenClaw Control UI (Web Dashboard), navigate to the Plugins page, and enter your `TDX_CLIENT_ID` and `TDX_CLIENT_SECRET` for this skill.

### Method 2: Manual Installation
```bash
# 1. Clone into your OpenClaw skills directory
git clone https://github.com/Harperbot/openclaw-parking-query.git ~/.openclaw/skills/parking_query

# 2. Configure keys via CLI or the Web UI

# 3. Restart the gateway
openclaw gateway restart
```

## License
MIT