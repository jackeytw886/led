# File Map — P015 檔案地圖

核對基準：`e89078c510ef8888ea5383d7027614167fa670c9`。下表列出整理前檔案，大小來自 Git tree；新增管理文件另列於文末。

| 路徑 | 大小（bytes） | 類型 |
| --- | ---: | --- |
| [README.md](../README.md) | 31 | md |
| [index.html](../index.html) | 451007 | html |

## index.html 行號索引（11,008 行）

| 約略行號 | 區段 |
| ---: | --- |
| 1～855 | HTML 介面（設定面板、工具列、影格區、WebSerial 面板）；Tailwind CDN |
| 858～981 | 基本設定變數（ROWS、COLS、START_CORNER、FIRST_DIR、LED_TYPE、分段腳位）與分段控制 |
| 991～1035 | `xyToLedIndex()`、`canvasToLedIndex()`：畫布座標 → 實體燈號 |
| 1036～1200 | 格點建立、`applyConfig()`、繪製、清除、填滿 |
| 1203～1410 | 影格：`addFrame`、`duplicateFrame`、刪除、多選、反轉、縮圖 |
| 1411～2200 | 影格編輯器：工具、填滿、復原／重做、選取、平移、翻轉、旋轉、複製貼上、匯出圖片 |
| 2201～3290 | `STAMP_LIBRARY` 圖章資料與圖章放置 |
| 3295～3975 | 播放、文字工具、`CHAR_LIBRARY`、文字特效產生 |
| 3975～4236 | 燈光特效產生 |
| 4237～9387 | `GAME_EFFECTS` 與遊戲動畫產生（大量資料，按需讀取） |
| 9455～9730 | 動畫儲存到 localStorage、檔案匯入匯出 |
| 9730～10110 | 設定存取、`exportJSON()`、`generateCpp()`（Arduino FastLED）、`importData()` |
| 10114～10570 | WebSerial：連線、`buildFrameData()`、即時同步、播放到裝置、測試圖樣 |
| 10574～11008 | `generateReceiverCode()` 接收端程式與初始化 |

## 管理入口

README.md、AGENTS.md、HANDOFF.md、PROJECT.json、CLAUDE.md、GEMINI.md、.github/copilot-instructions.md、docs/VERIFICATION.md。

## 專案資料（自 Claude 專案「矩陣燈板專用區」移入）

docs/DEVELOPMENT-NOTES.md、docs/DECISIONS.md、docs/HARDWARE.md、docs/PROTOCOL.md。
