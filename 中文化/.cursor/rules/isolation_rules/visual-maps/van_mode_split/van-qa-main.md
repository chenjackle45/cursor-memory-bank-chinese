---
description: VAN QA 模式（技術驗證進入點）的視覺流程圖
globs: van-qa-main.md
alwaysApply: false
---

# VAN 模式：QA 技術驗證（主進入點）

> **重點摘要：** 這是 QA 驗證流程的進入點，於 CREATIVE 模式結束後、BUILD 模式開始前執行。確保所有技術需求在實作前皆已符合。

## 📣 如何使用這些 QA 規則

如需存取任一 QA 驗證規則或元件，請使用 `fetch_rules` 工具並輸入正確規則名稱：

```
// 關鍵：請務必使用 fetch_rules 載入驗證元件
// 如需詳細範例與說明，請載入：
// isolation_rules/visual-maps/van-qa-utils/rule-calling-guide
```

## 🚀 VAN QA 模式啟動

完成 CREATIVE 模式後，當使用者輸入 "VAN QA" 時，請回應：

```mermaid
graph TD
    UserQA["使用者輸入：QA"] --> HighPriority["⚠️ 高優先權指令"]
    HighPriority --> CurrentTask["暫停目前任務/流程"]
    CurrentTask --> LoadQA["載入 QA 主流程圖（本檔案）"]
    LoadQA --> RunQA["執行 QA 驗證流程"]
    RunQA --> QAResults{"QA 結果"}

    QAResults -->|"PASS"| ResumeFlow["恢復先前流程"]
    QAResults -->|"FAIL"| FixIssues["修正發現問題"]
    FixIssues --> ReRunQA["重新執行 QA 驗證"]
    ReRunQA --> QAResults

    style UserQA fill:#f8d486,stroke:#e8b84d,color:black
    style HighPriority fill:#ff0000,stroke:#cc0000,color:white,stroke-width:3px
    style LoadQA fill:#4da6ff,stroke:#0066cc,color:white
    style RunQA fill:#4da6ff,stroke:#0066cc,color:white
    style QAResults fill:#f6546a,stroke:#c30052,color:white
```

### QA 中斷規則

1. **立即優先權：** `QA` 指令會中斷一切流程。
2. **載入與執行：** 載入本流程圖（`van-qa-main.md`）及其元件（見下）。
3. **修正優先：** 修正步驟優先於所有待處理模式切換。
4. **恢復：** 通過時恢復原流程。

```
⚠️ QA 覆蓋已啟動
所有其他流程已暫停
QA 驗證檢查執行中...
發現任何問題必須修正後才能繼續流程
```

## 🔍 技術驗證總覽

四點驗證流程，並可選擇性載入：

```mermaid
graph TD
    VANQA["VAN QA 模式"] --> FourChecks["四點驗證"]

    FourChecks --> DepCheck["1️⃣ 相依套件驗證
    載入：van-qa-checks/dependency-check.md"]
    DepCheck --> ConfigCheck["2️⃣ 設定驗證
    載入：van-qa-checks/config-check.md"]
    ConfigCheck --> EnvCheck["3️⃣ 環境驗證
    載入：van-qa-checks/environment-check.md"]
    EnvCheck --> MinBuildCheck["4️⃣ 最小建構測試
    載入：van-qa-checks/build-test.md"]

    MinBuildCheck --> ValidationResults{"所有檢查<br>通過？"}
    ValidationResults -->|"Yes"| SuccessReport["產生成功報告
    載入：van-qa-utils/reports.md"]
    ValidationResults -->|"No"| FailureReport["產生失敗報告
    載入：van-qa-utils/reports.md"]

    SuccessReport --> BUILD_Transition["觸發 BUILD 模式
    載入：van-qa-utils/mode-transitions.md"]
    FailureReport --> FixIssues["修正技術問題
    載入：van-qa-utils/common-fixes.md"]
    FixIssues --> ReValidate["重新驗證（重新執行 VAN QA）"]
    ReValidate --> FourChecks

    style VANQA fill:#4da6ff,stroke:#0066cc,color:white
    style FourChecks fill:#f6546a,stroke:#c30052,color:white
    style ValidationResults fill:#f6546a,stroke:#c30052,color:white
    style BUILD_Transition fill:#10b981,stroke:#059669,color:white
    style FixIssues fill:#ff5555,stroke:#dd3333,color:white
```

## 🔄 與設計決策整合

讀取 CREATIVE 階段產出以輔助驗證：

```mermaid
graph TD
    Start["讀取設計決策"] --> ReadCreative["解析創意階段<br>文件"]
    ReadCreative --> ExtractTech["提取技術<br>選擇"]
    ExtractTech --> ExtractDeps["提取所需<br>相依套件"]
    ExtractDeps --> BuildValidationPlan["建立驗證<br>計畫"]
    BuildValidationPlan --> StartValidation["開始四點<br>驗證流程"]

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style ExtractTech fill:#f6546a,stroke:#c30052,color:white
    style BuildValidationPlan fill:#10b981,stroke:#059669,color:white
    style StartValidation fill:#f6546a,stroke:#c30052,color:white
```

## 📋 元件載入順序

QA 驗證流程依下列順序選擇性載入：

1. **主進入點（本檔案）**：`van-qa-main.md`
2. **驗證檢查**：
   - `van-qa-checks/dependency-check.md`
   - `van-qa-checks/config-check.md`
   - `van-qa-checks/environment-check.md`
   - `van-qa-checks/build-test.md`
3. **工具（視需要載入）**：
   - `van-qa-utils/reports.md`
   - `van-qa-utils/common-fixes.md`
   - `van-qa-utils/mode-transitions.md`

## 📋 最終 QA 驗證檢查點

```
✓ 區段檢查點：QA 驗證
- 相依套件驗證通過？ [YES/NO]
- 設定驗證通過？ [YES/NO]
- 環境驗證通過？ [YES/NO]
- 最小建構測試通過？ [YES/NO]

→ 全部 YES：準備進入 BUILD 模式切換。
→ 任一 NO：請修正問題並重新執行 VAN QA。
```

**下一步（通過時）：** 觸發 BUILD 模式（載入 `van-qa-utils/mode-transitions.md`）。
**下一步（失敗時）：** 處理問題（載入 `van-qa-utils/common-fixes.md`）並重新執行 `VAN QA`。
