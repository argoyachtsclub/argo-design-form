2026 亞果遊艇會設計需求系統 (Argo Design Request System)

這是一個專為亞果遊艇會設計的線上設計需求申請系統。系統整合了前端表單驗證、PDF 自動生成以及 Google Apps Script (GAS) 雲端同步功能，旨在簡化內部設計申請流程並確保資料歸檔。

🌟 主要功能

智慧表單驗證：

自動計算並限制「完成日期」需至少為 10 個工作天（約 14 個曆日）之後。

禁止選擇週六與週日。

必填欄位檢查與自動捲動至錯誤位置。

PDF 簽核單生成：

整合 html2pdf.js，可一鍵將表單內容轉化為標準 A4 格式的 PDF 簽核單。

優化 PDF 版面，自動隱藏網頁操作按鈕與上傳元件。

圖片自動壓縮與上傳：

前端自動將參考圖壓縮至最大 1200px 寬度，降低傳輸量並避免 GAS 溢位。

支援 Base64 編碼傳輸，將文案與圖片同步至雲端。

雲端自動化流程 (搭配 GAS)：

自動將資料寫入 Google Sheet。

自動發送 Email 通知相關人員。

視覺化工作流程圖：

內建 Tailwind CSS 繪製的設計流程圖，方便申請人了解進度預期。

🛠 技術架構

前端：HTML5, Tailwind CSS (UI 框架), Font Awesome (圖示)。

功能庫：

html2pdf.js: 負責客戶端 PDF 生成。

html2canvas: 負責將網頁元素渲染為畫布。

jsPDF: 負責生成 PDF 檔案。

後端：Google Apps Script (GAS)。

資料儲存：Google Sheets / Google Drive。

🚀 部署指南

第一步：準備 Google Apps Script (GAS)

建立一個新的 Google 試算表。

點擊 擴充功能 > Apps Script。

貼入後端處理代碼（處理 doPost 邏輯）。

點擊 部署 > 新增部署。

種類選擇 網頁應用程式：

誰可以用此應用程式：選擇「任何人」。

複製產生的 Web App URL。

第二步：設定前端代碼

開啟 index.html。

找到 const GAS_URL = "..."。

將剛剛複製的 URL 貼入引號中。

第三步：發佈網頁

本地使用：直接將檔案儲存為 .html 並用瀏覽器開啟。

線上發佈：建議使用 Netlify、GitHub Pages 或直接整合進 GAS 的 doGet 函式中發佈。

📝 注意事項

工作天邏輯：系統預設為 10 個工作天，若公司政策調整，請修改 getMinDeadline() 函式。

維護模式：若需暫停系統接收需求，可將 IS_MAINTENANCE 變數設為 true。

圖片限制：雖然有壓縮功能，但單次上傳過多高畫質圖片仍可能受限於 GAS 的 50MB 請求限制。

© 2026 ARGO YACHT CLUB. 保留所有權利。
