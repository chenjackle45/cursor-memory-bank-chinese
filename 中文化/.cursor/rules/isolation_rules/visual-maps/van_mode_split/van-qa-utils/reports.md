---
description: VAN QA 驗證報告工具
globs: van-qa-utils/reports.md
alwaysApply: false
---

# VAN QA：驗證報告

> **重點摘要：** 本元件包含 QA 驗證流程結束時產生的完整成功與失敗報告格式。

## 📋 完整成功報告格式

四大驗證點皆通過後，產生此成功報告：

```
╔═════════════════════ 🔍 QA 驗證報告 ══════════════════════╗
│ 專案： [專案名稱] | 時間戳： [當前日期/時間]            │
├───────────────────────────────────────────────────────────┤
│ 1️⃣ 相依套件：✓ 相容                                       │
│ 2️⃣ 設定檔：✓ 有效且相容                                   │
│ 3️⃣ 環境：✓ 就緒                                           │
│ 4️⃣ 最小建構：✓ 成功且通過                                 │
├───────────────────────────────────────────────────────────┤
│ 🚨 最終判定：通過                                         │
│ ➡️ 可進入 BUILD 模式                                      │
╚═══════════════════════════════════════════════════════════╝
```

### 成功報告產生範例：

```powershell
function Generate-SuccessReport {
    param (
        [string]$ProjectName = "Current Project"
    )

    $timestamp = Get-Date -Format "yyyy-MM-dd HH:mm:ss"

    $report = @"
╔═════════════════════ 🔍 QA 驗證報告 ══════════════════════╗
│ 專案： $ProjectName | 時間戳： $timestamp            │
├───────────────────────────────────────────────────────────┤
│ 1️⃣ 相依套件：✓ 相容                                       │
│ 2️⃣ 設定檔：✓ 有效且相容                                   │
│ 3️⃣ 環境：✓ 就緒                                           │
│ 4️⃣ 最小建構：✓ 成功且通過                                 │
├───────────────────────────────────────────────────────────┤
│ 🚨 最終判定：通過                                         │
│ ➡️ 可進入 BUILD 模式                                      │
╚═══════════════════════════════════════════════════════════╝
"@

    # 儲存驗證狀態（供 BUILD 模式阻擋機制使用）
    "PASS" | Set-Content -Path "memory-bank\.qa_validation_status"

    return $report
}
```

## ❌ 失敗報告格式

若任一驗證步驟失敗，產生此詳細失敗報告：

```
⚠️⚠️⚠️ QA 驗證失敗 ⚠️⚠️⚠️

在進入 BUILD 模式前，必須先解決以下問題：

1️⃣ 相依套件問題：
- [相依套件問題詳細描述]
- [建議修正方法]

2️⃣ 設定檔問題：
- [設定檔問題詳細描述]
- [建議修正方法]

3️⃣ 環境問題：
- [環境問題詳細描述]
- [建議修正方法]

4️⃣ 建構測試問題：
- [建構測試問題詳細描述]
- [建議修正方法]

⚠️ 在解決這些問題之前，BUILD 模式將被阻擋。
修正問題後請輸入 'VAN QA' 重新驗證。
```

### 失敗報告產生範例：

```powershell
function Generate-FailureReport {
    param (
        [string[]]$DependencyIssues = @(),
        [string[]]$ConfigIssues = @(),
        [string[]]$EnvironmentIssues = @(),
        [string[]]$BuildIssues = @()
    )

    $report = @"
⚠️⚠️⚠️ QA 驗證失敗 ⚠️⚠️⚠️

在進入 BUILD 模式前，必須先解決以下問題：

"@

    if ($DependencyIssues.Count -gt 0) {
        $report += @"
1️⃣ 相依套件問題：
$(($DependencyIssues | ForEach-Object { "- $_" }) -join "`n")

"@
    }

    if ($ConfigIssues.Count -gt 0) {
        $report += @"
2️⃣ 設定檔問題：
$(($ConfigIssues | ForEach-Object { "- $_" }) -join "`n")

"@
    }

    if ($EnvironmentIssues.Count -gt 0) {
        $report += @"
3️⃣ 環境問題：
$(($EnvironmentIssues | ForEach-Object { "- $_" }) -join "`n")

"@
    }

    if ($BuildIssues.Count -gt 0) {
        $report += @"
4️⃣ 建構測試問題：
$(($BuildIssues | ForEach-Object { "- $_" }) -join "`n")

"@
    }

    $report += @"
⚠️ 在解決這些問題之前，BUILD 模式將被阻擋。
修正問題後請輸入 'VAN QA' 重新驗證。
"@

    # 儲存驗證狀態（供 BUILD 模式阻擋機制使用）
    "FAIL" | Set-Content -Path "memory-bank\.qa_validation_status"

    return $report
}
```

**下一步（成功時）：** 載入 `van-qa-utils/mode-transitions.md` 以處理 BUILD 模式切換。
**下一步（失敗時）：** 載入 `van-qa-utils/common-fixes.md` 取得修正指引。
