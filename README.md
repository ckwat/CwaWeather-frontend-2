# 年糕 報天氣 — README

## English

### Overview
"Weather Forecast by Linko" is a lightweight, friendly weather web app that fetches regional weather forecasts from a backend API (deployed at Zeabur). The frontend allows users to select one of 22 Taiwanese administrative areas and view the current + near-future forecast, suggestions (e.g., bring umbrella, clothing), and a tidy UI with theme options.

The backend API endpoint used by the frontend:
https://weather-kelvin2.zeabur.app/api/weather/kelvin?location=<URL-ENCODED-LOCATION>

Example:
https://weather-kelvin2.zeabur.app/api/weather/kelvin?location=%E5%B1%8F%E6%9D%B1%E7%B8%A3

### Features
- Selectable location (22 areas) via dropdown in the top-left.
- Requests backend with URL-encoded location parameter.
- Displays a main (hero) card and several mini forecast cards for upcoming time periods.
- Theme switcher: light / kawaii / energetic.
- Simple loading screen and hover interactions.
- Mobile responsive layout.

### Getting Started (Frontend)
1. Place the provided HTML file (the complete page) into your static hosting or project folder (e.g., `index.html`).
2. Ensure the image assets referenced (e.g., `dog.png`, `icon_linko2.png`) are available in the same folder or update paths.
3. Deploy / open the page in a browser. The app will call the backend API automatically on load using the dropdown's selected location (default: 屏東縣).
4. Changing the dropdown triggers a new API call with the selected location encoded via `encodeURIComponent`.

### API
- Endpoint: GET /api/weather/kelvin
- Query: `location` — a region name (Traditional Chinese), URL-encoded.
- Example: `?location=%E5%B1%8F%E6%9D%B1%E7%B8%A3` (屏東縣)

The frontend expects JSON in the shape:
{
  success: true,
  data: {
    city: "屏東縣",
    updateTime: "...",
    forecasts: [
      {
        startTime: "...",
        endTime: "...",
        weather: "...",
        rain: "...",
        minTemp: "...",
        maxTemp: "...",
        comfort: "...",
        windSpeed: "..."
      },
      ...
    ]
  }
}

### Notes for Deployment
- The frontend is static HTML/CSS/JS; you can host it on any static hosting service (Zeabur static site, Netlify, Vercel, GitHub Pages, etc.).
- Ensure CORS is enabled on the backend if hosting frontend and backend on different origins.
- Confirm the backend API base URL is reachable and the API supports the `location` query parameter.

### Troubleshooting
- If forecasts fail to load, check browser console for network errors. Ensure the backend URL is correct and accessible.
- If images or fonts do not load, confirm file paths and network permissions.

---

## 繁體中文 (Traditional Chinese)

### 概述
"年糕 報天氣" 是一個輕量、友善的天氣網頁，透過後端 API（部署於 Zeabur）取得各區域天氣預報。前端提供 22 個台灣縣市的下拉選單，使用者可選擇地區以查看當前與短期預報、穿搭與雨具建議，以及主題切換功能。

前端向後端呼叫的 API 範例（需對地區名稱做 URL 編碼）：
https://weather-kelvin2.zeabur.app/api/weather/kelvin?location=<URL-ENCODED-LOCATION>

範例：
https://weather-kelvin2.zeabur.app/api/weather/kelvin?location=%E5%B1%8F%E6%9D%B1%E7%B8%A3

### 功能
- 左上角下拉選單可選擇 22 個行政區。
- 呼叫後端時會將地區名稱用 URL 編碼後放入 query string 的 `location`。
- 顯示主卡（hero）與多張小卡（稍後預報）。
- 主題切換：淺色 / 可愛 / 活力。
- 簡單的 loading 畫面與滑鼠 hover 動畫。
- 響應式 (RWD) 支援手機與桌面。

### 前端快速上手
1. 將提供的 HTML 檔案放到靜態網站或專案資料夾（例如命名為 `index.html`）。
2. 確認頁面引用的圖片（如 `dog.png`, `icon_linko2.png`）已放在相同目錄或更新路徑。
3. 開啟網頁或部署後，頁面會在載入時以下拉選單預設值（屏東縣）呼叫後端 API。
4. 當使用者改變下拉選單時，前端會使用 `encodeURIComponent` 將地區名稱編碼並呼叫 API。

### API 規格
- 路徑: GET /api/weather/kelvin
- Query: `location` — 區域名稱（繁體中文），需 URL 編碼
- 範例: `?location=%E5%B1%8F%E6%9D%B1%E7%B8%A3`（屏東縣）

前端預期後端回傳 JSON 格式如下：
{
  success: true,
  data: {
    city: "屏東縣",
    updateTime: "...",
    forecasts: [
      {
        startTime: "...",
        endTime: "...",
        weather: "...",
        rain: "...",
        minTemp: "...",
        maxTemp: "...",
        comfort: "...",
        windSpeed: "..."
      },
      ...
    ]
  }
}

### 部署注意事項
- 前端是靜態頁面（HTML/CSS/JS），可部署到任何靜態站台（例如 Zeabur static site、Netlify、Vercel、GitHub Pages 等）。
- 若前後端位於不同網域，請確認後端已啟用 CORS。
- 確認後端 API 的 base URL 可存取，並支援 `location` query 參數。

### 常見問題排查
- 若天氣資料載入失敗，檢查瀏覽器主控台的 network 與錯誤訊息，確認後端 URL 是否正確且可連線。
- 若圖片或字型無法顯示，請確認檔案路徑與權限設置。