# 🅿️ openclaw-parking-query

全台即時停車查詢 OpenClaw Skill，透過 Telegram、LINE 或 iMessage 傳送定位點或 Google Maps 網址，即可查詢附近有空位的停車場並附上一鍵導航連結。

**🔥 最新版本 v1.2.0 更新：**
* 🚀 **原生 OpenClaw 外掛支援**：新增 `openclaw.plugin.json`，支援直接透過 ClawHub 安裝，不需再手動修改 `openclaw.json`。
* ✨ **Markdown 輸出優化**：將原本冗長的網址升級為乾淨的 Inline Links（[🍎 Apple Maps 導航]）。
* 🗺️ **Google Maps 解析強化**：支援更精準的轉址解析，並在無座標時自動 fallback 使用 Nominatim 進行地址反解。
* 🏙️ **雙北跨區智慧搜尋**：人在台北市邊界時，會自動聯集新北市的即時停車資料。

[English Documentation](README.en.md) | 繁體中文

## 功能示範

```
你：[傳送定位點]

助理：
🅿️ 附近 500 公尺 有空位的停車場（Taipei）

### 1. 信義廣場地下停車場
**空位**：`41` 個 ｜ **距離**：`103` 公尺
📍 信義路5段11號地下
[🍎 Apple Maps 導航](https://...) ｜ [🗺️ Google Maps 導航](https://...)

### 2. 三張里地下停車場
**空位**：`60` 個 ｜ **距離**：`301` 公尺
...
```

## 特色

- **雙模式自動判斷**：訊息含時間詞（「明天」、「下午」等）→ 未來模式，只列停車場位置；純定位 → 即時模式，顯示空位數
- **三種輸入格式**：Telegram / LINE 定位點、Google Maps 短網址（`maps.app.goo.gl/xxx`）、完整 Google Maps URL
- **智慧搜尋半徑**：先搜 500 公尺，若無結果自動擴展至 1 公里
- **原生支援**：完美整合 OpenClaw 2026 架構，配置簡單

## 前置需求

### 1. OpenClaw

請先安裝並設定 [OpenClaw](https://github.com/openclaw/openclaw)。

### 2. TDX API 金鑰（免費）

前往 [tdx.transportdata.tw](https://tdx.transportdata.tw) 註冊帳號，取得 `Client ID` 與 `Client Secret`。

### 3. Python 套件

```bash
pip3 install requests
```

## 安裝

### 方式一：透過 ClawHub (推薦)

```bash
clawhub install openclaw-parking-query
```

安裝後，請在 OpenClaw 的 Control UI (網頁儀表板) 的 Plugins 頁面中，為此技能填入 `TDX_CLIENT_ID` 與 `TDX_CLIENT_SECRET`。

### 方式二：手動安裝

```bash
# 1. clone 到 OpenClaw skills 目錄
git clone https://github.com/Harperbot/openclaw-parking-query.git ~/.openclaw/skills/parking_query

# 2. 透過 CLI 或是網頁介面設定金鑰

# 3. 重啟 gateway
openclaw gateway restart
```

## License

MIT