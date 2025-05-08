---
description: VAN QA 環境驗證流程圖
globs: van-qa-checks/environment-check.md
alwaysApply: false
---

# VAN QA：環境驗證

> **重點摘要：** 本元件驗證建構環境已正確設定，並具備所需工具與權限。

## 3️⃣ 環境驗證流程

```mermaid
graph TD
    Start["環境驗證"] --> CheckEnv["檢查建構環境"]
    CheckEnv --> VerifyBuildTools["驗證建構工具"]
    VerifyBuildTools --> ToolsStatus{"建構工具<br>可用？"}

    ToolsStatus -->|"是"| CheckPerms["檢查權限<br>與存取"]
    ToolsStatus -->|"否"| InstallTools["安裝所需<br>建構工具"]
    InstallTools --> RetryTools["重新驗證"]
    RetryTools --> ToolsStatus

    CheckPerms --> PermsStatus{"權限<br>足夠？"}
    PermsStatus -->|"是"| EnvSuccess["環境驗證通過<br>✅ 通過"]
    PermsStatus -->|"否"| FixPerms["修正權限<br>問題"]
    FixPerms --> RetryPerms["重新檢查<br>權限"]
    RetryPerms --> PermsStatus

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style EnvSuccess fill:#10b981,stroke:#059669,color:white
    style ToolsStatus fill:#f6546a,stroke:#c30052,color:white
    style PermsStatus fill:#f6546a,stroke:#c30052,color:white
```

### 環境驗證實作範例：

```powershell
# 範例：驗證網頁專案環境
function Validate-Environment {
    $requiredTools = @(
        @{Name = "git"; Command = "git --version"},
        @{Name = "node"; Command = "node --version"},
        @{Name = "npm"; Command = "npm --version"}
    )

    $missingTools = @()
    $permissionIssues = @()

    # 檢查建構工具
    foreach ($tool in $requiredTools) {
        try {
            Invoke-Expression $tool.Command | Out-Null
        } catch {
            $missingTools += $tool.Name
        }
    }

    # 檢查專案目錄寫入權限
    try {
        $testFile = ".__permission_test"
        New-Item -Path $testFile -ItemType File -Force | Out-Null
        Remove-Item -Path $testFile -Force
    } catch {
        $permissionIssues += "目前目錄（無寫入權限）"
    }

    # 檢查 3000 埠口是否可用（常用於開發伺服器）
    try {
        $listener = New-Object System.Net.Sockets.TcpListener([System.Net.IPAddress]::Loopback, 3000)
        $listener.Start()
        $listener.Stop()
    } catch {
        $permissionIssues += "3000 埠口（已被佔用或存取被拒）"
    }

    # 顯示結果
    if ($missingTools.Count -eq 0 -and $permissionIssues.Count -eq 0) {
        Write-Output "✅ 環境驗證成功"
        return $true
    } else {
        if ($missingTools.Count -gt 0) {
            Write-Output "❌ 缺少工具: $($missingTools -join ', ')"
        }
        if ($permissionIssues.Count -gt 0) {
            Write-Output "❌ 權限問題: $($permissionIssues -join ', ')"
        }
        return $false
    }
}
```

## 📋 環境驗證檢查點

```
✓ 檢查點：環境驗證
- 所需建構工具皆已安裝？ [是/否]
- 專案目錄權限足夠？ [是/否]
- 所需埠口可用？ [是/否]

→ 若皆為「是」：繼續進行最小建構測試。
→ 若有「否」：請先修正環境問題再繼續。
```

**下一步（通過時）：** 載入 `van-qa-checks/build-test.md`。
**下一步（失敗時）：** 請參考 `van-qa-utils/common-fixes.md` 以修正環境問題。
