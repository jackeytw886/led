# Development Notes — P015 開發沿革與資料移轉

來源：Claude 專案「矩陣燈板專用區」的對話與專案記憶（2026-01 ～ 2026-04）。以下區分「倉庫內可驗證」與「僅對話紀錄」。

## 版本沿革

| 時間 | 版本／成果 | 是否在倉庫 |
| --- | --- | --- |
| 2026-01 | 40×8（5 片 8×8）英文跑馬燈與文字特效網頁；多片面板編排工具（每片獨立尺寸與走線、JSON 匯入匯出） | 否（對話輸出） |
| 2026-01 | 576 顆（24×24）WebSerial 控制網頁＋Arduino Mega 雙腳位韌體，20 種燈效 | 否（對話輸出） |
| 2026-02-21 | LED Matrix Animator Pro 單檔 HTML，經 EZPage 部署 | **是**：`index.html` |
| 2026-04 | 增強版 HTML（見下） | 否 |
| 2026-04 | Python NiceGUI 移植版（見下） | 否 |

## 2026-04 增強版 HTML（尚未入庫）

對話紀錄中的功能，相對於倉庫版本的差異：

- 主畫布加入文字工具；文字與圖章都改成**浮動預覽**：滑鼠拖曳移動、滾輪縮放（圖章 0.5×～8×）、方向鍵微調、Enter 套用、Esc 取消。
- 主畫布復原／重做（倉庫版只有影格編輯器內有）。
- 修正「＋ 新增影格」會帶入目前內容的錯誤：`addFrame(blank)` 與 `duplicateCurrentFrame()` 分開。
- 「快速動畫」與「遊戲」從下方分頁移到主工具列，與圖章、文字並列；快捷鍵 G、Q。
- 圖章庫擴充為 25 類 × 20 個 = 500 個，新增類別含彩色數字、字母 A–T、形狀、愛心、星星、工具、服飾、樂器、運動、標誌、醫療、太空、商業等。
- 走線多一個「Z 字型（單向）」選項，方向描述與接收端程式同步更新。
- 當時驗證：DIV 平衡、無重複 id、JS 可解析。

## Python NiceGUI 移植版（尚未入庫）

主要需求：文字工具可使用作業系統已安裝的字型。6 個模組：

| 模組 | 內容 |
| --- | --- |
| `font_manager.py` | 掃描 Windows／macOS／Linux 字型目錄（.ttf/.otf/.ttc/.otc），讀取顯示名稱，CJK 字型優先 |
| `text_renderer.py` | PIL `ImageFont.truetype` 繪製灰階後二值化成像素；相容新版 `getbbox()` 與舊版 `getsize()` |
| `matrix_core.py` | `MatrixConfig` dataclass、`FrameStore`、`xy_to_led_index`（與 HTML 版相同的 S 型轉換） |
| `stamp_library.py` | 500 個圖章，格式與 HTML 版相同 |
| `arduino_codegen.py` | 產生 FastLED C++（PROGMEM 影格資料） |
| `led_matrix_app.py` | NiceGUI 主程式：SVG 畫布與滑鼠事件、文字／圖章浮動預覽、影格縮圖（PIL）、JSON 快照復原、GIF／Arduino／JSON 匯出匯入 |

當時已通過整合測試；原檔位於當次對話的雲端工作區，已無法從這裡取得。

## 開發習慣

- 小步迭代、每次都給可執行的成品；說明精簡。
- 介面文字繁體中文。
- HTML 每次修改後用 Node.js 檢查 DIV 平衡、重複 id、JS 解析。
- HTML 版與 Python 版功能平行開發，資料格式（圖章、影格 JSON、座標轉換）保持一致。
