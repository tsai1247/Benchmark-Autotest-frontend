# Benchmark Autotest Frontend

這是一個 GitHub Pages 項目，用於將 `benchmarkvisualizer.tsai1247.com` 的不同路徑重定向到對應的 Google Apps Script 應用。

## 重定向規則

- `/` → https://script.google.com/macros/s/AKfycbyjykO8Xpx9MkIeK_IgnuNbw9YznCTm0ycJHJbNmIbncp5h_PSz8gpmHWgPmrWK7wxk/exec
- `/v1` → https://script.google.com/macros/s/AKfycbyOpKPAsSwFg4IrZ8itqSmg-L-e8aPkm08RWlPICH-DyQDA25JxoaTsDMP-3D3aTcWY/exec
- `/v2` → https://script.google.com/macros/s/AKfycbz7-2Tvms-9sdT3wHSrSlZ8qxvMK1HaWctsVIk1VQpdsZQWWaks3P48CIArYveY0RdX/exec
- `/v3` → https://script.google.com/macros/s/AKfycbyjykO8Xpx9MkIeK_IgnuNbw9YznCTm0ycJHJbNmIbncp5h_PSz8gpmHWgPmrWK7wxk/exec

## GitHub 設定步驟

1. **啟用 GitHub Pages**
   - 進入倉庫的 **Settings** → **Pages**
   - 選擇 **Deploy from a branch**
   - 分支選擇 **main**
   - 文件夾選擇 **/ (root)**

2. **設定自定義域名**
   - 在 **Settings** → **Pages** 中
   - 在 **Custom domain** 欄位輸入：`benchmarkvisualizer.tsai1247.com`
   - 點擊 **Save**
   - GitHub 會自動建立 CNAME 文件（本項目已包含）

3. **啟用 HTTPS**
   - 勾選 **Enforce HTTPS** 選項

## Cloudflare 設定步驟

### DNS 記錄設定

在 Cloudflare Dashboard 中的 DNS 設定：

1. **添加 DNS A 記錄**
   ```
   類型: A
   名稱: benchmarkvisualizer
   內容: 185.199.108.153
   TTL: Auto
   代理狀態: Proxied
   ```

2. **或添加 CNAME 記錄（推薦）**
   ```
   類型: CNAME
   名稱: benchmarkvisualizer
   內容: <你的GitHub用戶名>.github.io
   TTL: Auto
   代理狀態: Proxied
   ```

3. **驗證 DNS**
   - 使用 `nslookup benchmarkvisualizer.tsai1247.com` 驗證 DNS 指向

### Cloudflare 頁面規則（選項性）

如果需要在 Cloudflare 層級進行額外配置：

1. 進入 **Rules** → **Page Rules**
2. 如需要，可添加快取規則或其他性能設定

## 技術細節

- 使用純 HTML + JavaScript 實現重定向
- 在用戶端進行路由判斷
- 支持瀏覽器歷史記錄
- 在重定向時顯示加載動畫

## 調試

如果重定向不工作：

1. 檢查 CNAME 文件是否正確
2. 驗證 Cloudflare DNS 設定
3. 清除瀏覽器快取
4. 檢查瀏覽器控制台是否有錯誤訊息
5. 等待 DNS 傳播（通常需要 10-30 分鐘）
