---
description: VAN QA 常見驗證修正工具
globs: van-qa-utils/common-fixes.md
alwaysApply: false
---

# VAN QA：常見驗證修正

> **重點摘要：** 本元件提供 QA 驗證過程中常見問題的修正方法。

## 🧪 依類別分類的常見 QA 驗證修正

### 相依套件問題

| 問題                 | 修正方法                                           |
| -------------------- | -------------------------------------------------- |
| **缺少 Node.js**     | 從 https://nodejs.org/ 下載並安裝 Node.js          |
| **npm 版本過舊**     | 執行 `npm install -g npm@latest` 進行更新          |
| **缺少套件**         | 執行 `npm install` 或 `npm install [package-name]` |
| **套件版本衝突**     | 調整 package.json 版本並執行 `npm install`         |
| **相依套件解析問題** | 執行 `npm cache clean -f` 後再嘗試安裝             |

### 設定檔問題

| 問題                      | 修正方法                                                                                  |
| ------------------------- | ----------------------------------------------------------------------------------------- |
| **JSON 格式無效**         | 使用 JSON 驗證工具（如 jsonlint）檢查語法                                                 |
| **缺少 React 外掛**       | 於 vite.config.js 新增 `import react from '@vitejs/plugin-react'` 及 `plugins: [react()]` |
| **TypeScript 設定不相容** | 以正確的 React 設定更新 `tsconfig.json`                                                   |
| **版本參照不一致**        | 確保所有設定檔版本一致                                                                    |
| **設定檔缺少必要欄位**    | 於設定檔中補齊必要欄位                                                                    |

### 環境問題

| 問題             | 修正方法                                                                                                                                       |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **權限被拒**     | 以管理員身份執行終端機（Windows）或使用 sudo（Mac/Linux）                                                                                      |
| **埠已被佔用**   | 關閉佔用該埠的進程：`netstat -ano \| findstr :PORT`，再用 `taskkill /F /PID PID`（Windows）或 `lsof -i :PORT`，再用 `kill -9 PID`（Mac/Linux） |
| **缺少建構工具** | 安裝所需命令列工具（git、node 等）                                                                                                             |
| **環境變數問題** | 設定所需環境變數：`$env:VAR_NAME = "value"`（PowerShell）或 `export VAR_NAME="value"`（Bash）                                                  |
| **磁碟空間不足** | 釋放磁碟空間，清理 npm/套件快取檔案                                                                                                            |

### 建構測試問題

| 問題             | 修正方法                                               |
| ---------------- | ------------------------------------------------------ |
| **建構失敗**     | 檢查控制台中的具體錯誤訊息                             |
| **測試失敗**     | 確認最小化設定是否正確                                 |
| **路徑問題**     | 確保路徑分隔符正確（Windows 用 `\`，Mac/Linux 用 `/`） |
| **缺少相依套件** | 確認所有必要相依套件已安裝                             |
| **腳本權限**     | 確保腳本檔案有執行權限（Unix 下執行 chmod +x）         |

## 📝 問題診斷程序

### 1. 相依套件診斷

```powershell
# 找出衝突的相依套件
npm ls [package-name]

# 檢查過時套件
npm outdated

# 檢查安全性漏洞
npm audit
```

### 2. 設定檔診斷

```powershell
# 列出所有設定檔
Get-ChildItem -Recurse -Include "*.json","*.config.js" | Select-Object FullName

# 找出 tsconfig.json 缺少的參照
if (Test-Path "tsconfig.json") {
    $tsconfig = Get-Content "tsconfig.json" -Raw | ConvertFrom-Json
    if (-not $tsconfig.compilerOptions.jsx) {
        Write-Output "tsconfig.json 缺少 jsx 設定"
    }
}
```

### 3. 環境診斷

```powershell
# 檢查佔用埠的進程（Windows）
netstat -ano | findstr ":3000"

# 列出環境變數
Get-ChildItem Env:

# 檢查磁碟空間
Get-PSDrive C | Select-Object Used,Free
```

**下一步：** 返回驗證流程或依照上方建議進行修正。
