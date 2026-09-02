# JetBrains AI Assistant 企業級介紹 Portal - 專案開發進度與接續指南

> **專案名稱**：JetBrains AI Assistant Enterprise Portal  
> **專案代理**：迪凱科技 AHASoft (JetBrains 台灣官方授權代理商)  
> **線上即時預覽 (Firebase Hosting)**：[https://jetbrains-ai-assistant-portal.web.app](https://jetbrains-ai-assistant-portal.web.app)  
> **Firebase Project ID**：`jetbrains-ai-assistant-portal`  
> **最新修訂時間**：2026-09-02  

---

## 📋 專案目錄結構 (Project Directory)

```text
JetBrains-AI-Assistant-Portal/
├── public/
│   ├── index.html               # 實際部署至 Firebase Hosting 的主要頁面 (包含全響應式排版與防快取)
│   └── logo-white.png           # 頂部凍結列左側 JetBrains 白底官方 Logo 圖示
├── dekai_jetbrains_ai_portal.html # 本地開發與備用原始 HTML 模板
├── firebase.json                # Firebase Hosting 部署設定 (含 Cache-Control: no-cache 防暫存標頭)
├── .firebaserc                  # Firebase 專案關聯對應設定
├── .gitignore                   # Git 版本控制忽略清單 (.firebase/, node_modules/ 等)
└── PROJECT_DEVELOPMENT_PROGRESS.md # 本開發進度與接續指南 MD 檔案
```

---

## 🎯 核心功能與優化完成項目 (Completed Features)

### 1. 品牌視覺與頂部凍結列 (Branding & Header)
- **官方 Logo 整合**：頂部凍結列 (Sticky Top Nav) 左側嵌入官方 JetBrains 白底標誌 (`logo-white.png`)，符合企業級質感。
- **高光動畫**：簡報目錄與大綱加入 `text-glow` 漸層光澤與脈衝動畫點 (`animate-ping`)。

### 2. 雙端響應式排版 (Responsive Mobile & Desktop Optimization)
- **電腦版 (Desktop / Laptop)**：
  - 字體大幅調大 (`text-2xl` 至 `text-7xl`)，適合簡報與大螢幕閱讀。
  - 右側設有專屬 `01 ~ 06` 懸浮快捷導覽 Dock。
  - 設定 `scroll-margin-top: 220px`，確保點擊目錄導航時，區塊標題完美停留於頂部凍結列下方，完全不被遮擋。
- **手機版 (Mobile Device)**：
  - 頂部 Navbar 縮減至極簡 `56px` 高度。
  - 取消手機版「目錄區塊大張雙重凍結」，目錄跟隨頁面自然滾動，消除 40% 的螢幕遮擋問題。
  - 新增螢幕底部極簡圓角膠囊按鈕 (`01` `02` `03` `04` `05` `06`)，方便手機單手一鍵快速切換區段。

### 3. 全重防快取與暫存機制 (Anti-Caching Strategy)
- **Firebase 伺服器層**：`firebase.json` 配置 `Cache-Control: no-cache, no-store, must-revalidate, max-age=0`。
- **HTML 層**：`<head>` 包含防快取 Meta 標籤。
- **微型刷新按鈕**：右上角與頁尾皆提供 `🔄 強制載入最新版` / `刷新` 按鈕，點擊時透過 `?refresh=timestamp` 強制重新載入伺服器最新版本。

### 4. 簡報 6 大核心商務內容區塊 (Core Sections)
1. **01. 產品簡介**：強調金融與證券 90%+ 市場佔有率、PSI 靜態分析防幻覺、與獨立 CLI (如 Claude Code) 比較表格、JetBrains 2026 年度報告預覽與連結。
2. **02. 產品優勢**：抽象語法樹 (PSI) 靜態檢查、Smart Debugging 診斷擷取 Stack Trace、一鍵生成 Git & Test。
3. **03. 計費與模型優勢**：同一平台原生支援 Claude 3.5 Sonnet, GPT-4o, Gemini 1.5 Pro, Mellum (自研) 自由切換。
4. **04. 帳務管理優勢**：JetBrains Central Console 統一 AI Credits 積分、精準組織權限控管與審計報表。
5. **05. 安全可信度聲明**：控制面/數據面分離、100% No-Training 零訓練承諾、30 天自動銷毀與 SOC 2 Type II / GDPR 驗證，並附上 Trust Center 連結。
6. **06. 在地服務 (迪凱科技 AHASoft)**：
   - 散買/代購 4 大痛點與 Central Console 解法（互動跳出卡片）。
   - 代支代付業務窘境心聲與迪凱在地服務優勢。
   - **30 天 Enterprise 企業試用 Modal**：包含完整 6 大表單欄位（公司名稱、聯絡人姓名、公司 Mail、預計試用人數、預計試用天數、得知管道）。

---

## 🚀 到公司接續處理指南 (GitHub & Deployment Commands)

目前本專案已在本地完成 `git init` 與本地 Commit。若您要推送到您個人的 GitHub 儲存庫，請依照以下步驟操作：

### 1. 推送到 GitHub (First-Time GitHub Push)

在公司或本地開啟 Terminal / Command Prompt，執行以下指令：

```bash
# 1. 切換至專案目錄
cd C:\Users\User\.gemini\antigravity\brain\cebfe850-edaa-4bde-aa18-447bd515eeb1\scratch\JetBrains-AI-Assistant-Portal

# 2. 在 GitHub 建立新的 Repository 後，新增 Remote (請替換為您的 GitHub 網址)
git remote add origin https://github.com/<YOUR_GITHUB_USERNAME>/JetBrains-AI-Assistant-Portal.git

# 3. 將預設分支命名為 main 並推送到 GitHub
git branch -M main
git push -u origin main
```

---

### 2. 在公司電腦 Pull 並繼續修改與更新部署 (Office Workflow)

在公司電腦複製與修改後重新部署至 Firebase：

```bash
# 複製專案至公司電腦
git clone https://github.com/<YOUR_GITHUB_USERNAME>/JetBrains-AI-Assistant-Portal.git
cd JetBrains-AI-Assistant-Portal

# 修改完 public/index.html 後提交
git add .
git commit -m "update: 調整產品簡介與樣式"
git push

# 重新部署至 Firebase Hosting (線上即時生效)
firebase deploy --only hosting
```

---

## 🔗 重要相關連結與背書資料

- **正式上線 Portal 網址**：`https://jetbrains-ai-assistant-portal.web.app`
- **JetBrains Trust Center**：`https://trust-center.jetbrains.com/`
- **JetBrains 2026 Annual Report**：`https://www.jetbrains.com/lp/annualreport-2026/`
- **Business Lean In**：`https://www.jetbrains.com/business/#lean-in`
- **AI Chat Docs**：`https://www.jetbrains.com/help/ai-assistant/ai-chat.html`
- **JetBrains AI Service Agreement**：`https://www.jetbrains.com/legal/docs/terms/jetbrains-ai-service/`
- **JetBrains Console Docs**：`https://www.jetbrains.com/help/jetbrains-console/about-jetbrains-console.html`
- **AI Credits Terms 1.0**：`https://www.jetbrains.com/legal/docs/terms/jetbrains-ai-credits/1.0/`

---
*本進度報告由 Antigravity AI 自動生成打包，祝您商務簡報與後續開發順利成功！*
