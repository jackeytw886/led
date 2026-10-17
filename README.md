# LED Matrix Animator — LED 矩陣動畫編輯器

<!-- ai-project-management:start -->
## Project Index — 專案管理索引

- **固定代號：P015**（綁定 GitHub 倉庫 ID 1163072466；不隨排序或改名重排）
- **分類：校務與工具（tool）**；標籤：led-matrix, pixel-art。
- **中文用途：LED 矩陣動畫編輯器**——在網頁上繪製逐格動畫，依實體燈板走線轉換燈號，輸出 Arduino（FastLED）程式或經 WebSerial 即時送到燈板。
- **入口：** `index.html`（單檔 HTML，頁面標題 LED Matrix Animator Pro）。
- **發布狀態：** GitHub Pages 已啟用；原有入口：https://jackeytw886.github.io/led 。本次未做完整互動測試。
- **命名處理：** 保留目前倉庫名稱，維持既有網站入口；分類名稱 `tool-led-matrix-animator` 記錄於 PROJECT.json。
- **AI 接手：** 先讀 [AGENTS.md](AGENTS.md)、[HANDOFF.md](HANDOFF.md)、[PROJECT.json](PROJECT.json) 與 [檔案地圖](docs/FILE-MAP.md)。
- **總目錄：** [AI Project Hub](https://github.com/jackeytw886/ai-project-hub)（私人總目錄，依個別帳號權限讀取）。

本次核對的是倉庫、檔案與文件；執行效果、實體接線需由對應驗證紀錄確認。下方保留既有專案說明。
<!-- ai-project-management:end -->

led - Deployed by EZPage

## 功能概要（依 index.html 現行版本）

- 矩陣尺寸、起點角落（左上／右上／左下／右下）、第一方向（垂直／水平）S 型走線設定。
- 燈條型號 WS2812B／WS2811／WS2813／SK6812／APA102、色序、亮度；可分段到多支資料腳位。
- 影格時間軸：新增、複製、刪除、反轉、多選；影格編輯器含筆刷、填滿、吸色、選取、平移、翻轉、旋轉、復原／重做。
- 圖章庫、文字（含字元庫與文字特效）、燈光特效、遊戲動畫產生器。
- 匯出：JSON、圖片、動畫檔；產生 Arduino FastLED 程式（PROGMEM 影格）與 WebSerial 接收端程式。
- WebSerial：二進制／十六進制文字／RGB 文字三種格式即時傳送、測試圖樣、逐顆測試。

## 專案文件

- [docs/DEVELOPMENT-NOTES.md](docs/DEVELOPMENT-NOTES.md)：版本沿革、尚未入庫的新版與 Python 版、開發習慣。
- [docs/DECISIONS.md](docs/DECISIONS.md)：已確立的設計決策與踩過的坑。
- [docs/HARDWARE.md](docs/HARDWARE.md)：搭配過的燈板／控制板與走線紀錄。
- [docs/PROTOCOL.md](docs/PROTOCOL.md)：WebSerial 影格格式。
- [docs/VERIFICATION.md](docs/VERIFICATION.md)：驗證方式與本次結果。
