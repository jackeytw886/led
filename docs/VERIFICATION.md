# Verification — P015 驗證方式

本次已核對：倉庫身分、預設分支、基準 SHA、檔案樹及現有文件，以及 index.html 中設定、轉換、輸出與 WebSerial 函式的位置。發布或硬體功能需由實際執行結果確認。

## 入口與環境

- 入口：`index.html`。
- 依 README 的使用方式啟動；WebSerial 需 Chrome 或 Edge。
- 檢查畫面載入、主要操作、資料保存／重開後狀態，並記錄環境與可重現步驟。
- 使用實體裝置時，另外核對板卡、接線、供電、有效電位及通訊格式。

## 每次修改 index.html 後

- `<div>` 與 `</div>` 數量相同。
- 沒有重複的 `id`。
- 抽出全部 `<script>` 內容，以 Node.js `new Function()` 或 `node --check` 確認可解析。

## 功能驗證

- 設定矩陣尺寸與走線後，點格確認燈號提示符合實體燈號表（見 docs/HARDWARE.md 核對點）。
- 繪製數格、新增空白影格、複製影格、播放，重開頁面確認 localStorage 還原。
- 產生 Arduino 程式並編譯上傳；用 WebSerial 三種格式各送一次測試圖樣，觀察燈板。
- 分段控制：確認各腳位負責的燈號範圍與實際一致。

## 本次驗證結果

- 管理檔案與 JSON 結構：提交前檢查；提交後核對 Git tree 與原檔 blob。
- 座標轉換：Node.js 對 `xyToLedIndex()` 跑 40×8 左下起點垂直全部 320 點，與 docs/HARDWARE.md 公式一致（程式比對）。
- index.html：未修改。
- 功能測試：本次未執行。
- 實機測試：本次未執行。

## 2026-10-18 第二輪核對結果（Claude）

基準：`5d5a36ddbc9d575c2b04552b994997e093b7fdc7`。環境：Node.js 22、Playwright Chromium（無頭、swiftshader）。

| 項目 | 結果 |
| --- | --- |
| `<div>` 開關數量 | ❌ HTML 區 138 開 ／ 139 關，多出的 `</div>` 在第 515 行（腳本內的樣板字串另有 13／13，平衡） |
| 重複 id | ❌ `saveStatus`（第 550、846 行） |
| `<script>` 解析 | ✅ `node --check` 通過 |
| 無頭瀏覽器載入 | ✅ 約 3 秒，無主控台錯誤；畫布 64 格（預設 8×8） |
| 外部請求 | 只有 `cdn.tailwindcss.com`（測試時已攔截，樣式未載入但不影響 JS） |
| WebSerial 實機 | 未執行 |
