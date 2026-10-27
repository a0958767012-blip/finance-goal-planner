# 目標理財試算器（PV・FV・PMT）

用現值（PV）、終值（FV）與每期存款（PMT）規劃理財目標的純靜態網站，無需建置。

功能：求每月該存多少（PMT）、期末會有多少（FV）、現在要投入多少（PV）；含通膨換算、成長圖、敏感度分析與逐年明細。

## 網站如何使用
1. 選一個目標：購屋頭期款、子女教育金、創業基金、緊急預備金、夢想旅行，或自訂。
2. 選你想求的答案：每月該存多少（PMT）、最後會有多少（FV）、現在要投入多少（PV）。
3. 輸入目標金額、年數、報酬率、通膨率、現有資金與每月投入。
4. 查看結果、成長圖、敏感度表與逐年明細，調整假設再比較。

## 專案結構
```
finance-goal-planner/
├── index.html         ← 網站本體（在最上層，直接拖曳資料夾即可部署）
├── _headers
├── .github/workflows/deploy.yml   （選用）
├── wrangler.toml
├── package.json
├── LICENSE
└── README.md
```

## 一、上傳到 GitHub
1. 在 GitHub 建立新的空儲存庫（例如 finance-goal-planner，不要勾選初始化 README）。
2. 在本資料夾執行：
```
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<你的帳號>/finance-goal-planner.git
git push -u origin main
```
（也可以直接在 GitHub 網頁用 Add file → Upload files 拖曳上傳。）

## 二、部署到 Cloudflare Pages
### 方法 A：連接 GitHub（推薦，之後每次 push 自動更新）
1. Cloudflare 後台 → Workers & Pages → Create → Pages → Connect to Git。
2. 授權並選擇 finance-goal-planner 儲存庫。
3. 設定：
   - Production branch：main
   - Framework preset：None
   - Build command：留空
   - Build output directory：留空（或填 /）
4. 按 Save and Deploy，完成後取得 xxx.pages.dev 網址。

### 方法 A2：直接上傳資料夾（不經 GitHub）
Workers & Pages → Create → Pages → Upload assets，把整個 finance-goal-planner 資料夾拖進去即可（index.html 位於最上層）。

### 方法 B：指令部署
```
npm run deploy
```
首次會要求登入 Cloudflare。

### 方法 C：GitHub Actions 手動部署
設定 deploy.yml 內註明的兩個 Secrets，再到 GitHub 的 Actions 頁面手動執行。

## 本機預覽
```
npm run dev
```
或直接用瀏覽器開啟 index.html。

## 備註
- 使用 Google Fonts，載入不到時自動改用系統字型。
- 使用者輸入只存在自己瀏覽器的 localStorage，不會上傳。
- 本工具僅為試算，不構成投資建議。
