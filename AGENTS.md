# AI Project Instructions — AI 專案工作規則

## Shared Management Rules — 共用管理規則

- 本倉庫固定代號是 P015；先讀 README.md、HANDOFF.md、PROJECT.json 與本次任務相關原始檔。
- 對話、交接與一般文件使用繁體中文；既有專案規格優先保留。天問 ASRPRO 程式內中文字依其專案規範使用簡體中文。
- 開始時確認實際倉庫、分支、commit SHA 與工作目錄變更；分辨文件記載、已實作與已執行驗證。
- 依當次使用者任務與工具環境規則工作；在授權範圍內完成修改、提交、推送或發布，保留他人尚未提交的變更。
- 需要並行修改時使用獨立分支與工作目錄；以任務或 PR 記錄範圍，不假設交接文件具有自動鎖。
- 有修改時更新 HANDOFF.md，記錄版本依據、修改路徑、驗證結果、限制與下一步；只閱讀時在回答中提供摘要即可。
- 長期決策與現場流程分別保存於 docs/DECISIONS.md、docs/RUNBOOK.md；文件只建立已知規格，未知欄位明確標註。
- 圖片、模型與大型內嵌資料先參考 docs/FILE-MAP.md；僅讀取本次需要的段落，避免把大型二進位或 base64 整份載入上下文。
- 密碼與金鑰以環境或平台秘密管理，範例使用虛構個人資料；保留現有倉庫與資料的存取界線。
- GitHub Pages 已啟用的倉庫，改名或搬動入口前先核對網站、QR code、kiosk 與引用；本次管理整理保留現有部署入口。

## Project Rules — 本專案規則

- 硬體與通訊紀錄分別在 docs/HARDWARE.md、docs/PROTOCOL.md；開發沿革與未入庫版本在 docs/DEVELOPMENT-NOTES.md。
- index.html 約 450 KB／11,008 行，先看 docs/FILE-MAP.md 的行號索引再按段讀取。
- 交付維持單檔 HTML（`index.html`），不拆成多檔或引入建置流程；外部程式庫目前只有 Tailwind CDN。
- 介面文字與提示使用繁體中文。
- 每次修改 HTML 後檢查：`<div>` 開關數量平衡、無重複 id、全部 `<script>` 可被 JS 解析（Node.js 檢查即可）。
- 畫布座標（左上原點、列優先）與實體燈號（依起點角落與 S 型走線）必須分開處理：繪圖一律用畫布座標，只在輸出 Arduino 或 WebSerial 時經 `canvasToLedIndex()`／`xyToLedIndex()` 轉換。改動走線邏輯要同步修改「產生 Arduino」「接收端程式」「WebSerial」三處並用實際燈號表核對。
- 「新增影格」是空白影格，「複製影格」才帶入內容；兩者不可共用同一函式路徑。
- 設定與動畫存在 localStorage（`led_matrix_config_v3`、`led_matrix_frames_{COLS}x{ROWS}`）；改資料結構時保留舊資料的讀取相容。
