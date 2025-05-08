---
description: QA 模式
globs: qa-mode-map.md
alwaysApply: false
---

> **重點摘要：** 強化版 QA 模式可於開發任意階段進行全面驗證。它會自動偵測目前階段，驗證記憶體庫一致性、任務追蹤、並執行階段專屬技術驗證，確保專案品質於開發全程皆受控。

## 🔍 強化 QA 模式流程

```mermaid
graph TD
    Start["🚀 啟動 QA 模式"] --> DetectPhase["🧭 階段偵測<br>判斷目前專案階段"]

    %% 階段判斷分支
    DetectPhase --> PhaseDetermination{"目前階段？"}
    PhaseDetermination -->|"VAN"| VANChecks["VAN 階段驗證"]
    PhaseDetermination -->|"PLAN"| PLANChecks["PLAN 階段驗證"]
    PhaseDetermination -->|"CREATIVE"| CREATIVEChecks["CREATIVE 階段驗證"]
    PhaseDetermination -->|"IMPLEMENT"| IMPLEMENTChecks["IMPLEMENT 階段驗證"]

    %% 通用驗證
    DetectPhase --> UniversalChecks["🔍 通用驗證"]
    UniversalChecks --> MemoryBankCheck["1️⃣ 記憶體庫驗證<br>檢查一致性與更新"]
    MemoryBankCheck --> TaskTrackingCheck["2️⃣ 任務追蹤驗證<br>驗證 tasks.md 為唯一依據"]
    TaskTrackingCheck --> ReferenceCheck["3️⃣ 參照驗證<br>檢查文件間交互參照"]

    %% 階段專屬驗證合併
    VANChecks & PLANChecks & CREATIVEChecks & IMPLEMENTChecks --> PhaseSpecificResults["階段專屬結果"]
    ReferenceCheck & PhaseSpecificResults --> ValidationResults{"✅ 所有檢查<br>通過？"}

    %% 結果處理
    ValidationResults -->|"是"| SuccessReport["📝 產生成功報告<br>全部驗證通過"]
    ValidationResults -->|"否"| FailureReport["⚠️ 產生失敗報告<br>並附修正指引"]

    %% 成功路徑
    SuccessReport --> UpdateMB["📚 更新記憶體庫<br>記錄驗證成功"]
    UpdateMB --> ContinueProcess["🚦 繼續：可進行階段流程"]

    %% 失敗路徑
    FailureReport --> IdentifyFixes["🔧 識別需修正項目"]
    IdentifyFixes --> ApplyFixes["🛠️ 執行修正"]
    ApplyFixes --> Revalidate["🔄 重新驗證"]
    Revalidate --> ValidationResults

    %% 樣式
    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style DetectPhase fill:#f6ad55,stroke:#c27022,color:white
    style UniversalChecks fill:#f6546a,stroke:#c30052,color:white
    style MemoryBankCheck fill:#10b981,stroke:#059669,color:white
    style TaskTrackingCheck fill:#10b981,stroke:#059669,color:white
    style ReferenceCheck fill:#10b981,stroke:#059669,color:white
    style ValidationResults fill:#f6546a,stroke:#c30052,color:white
    style SuccessReport fill:#10b981,stroke:#059669,color:white
    style FailureReport fill:#f6ad55,stroke:#c27022,color:white
    style ContinueProcess fill:#10b981,stroke:#059669,color:white,stroke-width:2px
    style IdentifyFixes fill:#f6ad55,stroke:#c27022,color:white
```

## 🧭 階段偵測流程

強化 QA 模式會先判斷目前專案所處階段：

```mermaid
graph TD
    PD["階段偵測"] --> CheckMB["分析記憶體庫檔案"]
    CheckMB --> CheckActive["檢查 activeContext.md<br>取得目前階段"]
    CheckActive --> CheckProgress["檢查 progress.md<br>最近活動"]
    CheckProgress --> CheckTasks["檢查 tasks.md<br>任務狀態"]

    CheckTasks --> PhaseResult{"判斷<br>目前階段"}
    PhaseResult -->|"VAN"| VAN["VAN 階段<br>初始化"]
    PhaseResult -->|"PLAN"| PLAN["PLAN 階段<br>任務規劃"]
    PhaseResult -->|"CREATIVE"| CREATIVE["CREATIVE 階段<br>設計決策"]
    PhaseResult -->|"IMPLEMENT"| IMPLEMENT["IMPLEMENT 階段<br>實作"]

    VAN & PLAN & CREATIVE & IMPLEMENT --> LoadChecks["載入階段專屬<br>驗證檢查"]

    style PD fill:#4da6ff,stroke:#0066cc,color:white
    style PhaseResult fill:#f6546a,stroke:#c30052,color:white
    style LoadChecks fill:#10b981,stroke:#059669,color:white
```

## 📝 通用記憶體庫驗證

此流程確保記憶體庫檔案於各階段皆一致且最新：

```mermaid
graph TD
    MBVS["記憶體庫<br>驗證"] --> CoreCheck["檢查核心檔案存在"]
    CoreCheck --> CoreFiles["驗證必要檔案：<br>projectbrief.md<br>activeContext.md<br>tasks.md<br>progress.md"]

    CoreFiles --> ContentCheck["驗證內容<br>一致性"]
    ContentCheck --> LastModified["檢查最後修改<br>時間戳"]
    LastModified --> CrossRef["驗證交互<br>參照"]

    CrossRef --> ConsistencyCheck{"所有檔案<br>一致？"}
    ConsistencyCheck -->|"是"| PassMB["✅ 記憶體庫<br>驗證通過"]
    ConsistencyCheck -->|"否"| FailMB["❌ 記憶體庫<br>發現不一致"]

    FailMB --> FixSuggestions["產生修正<br>建議"]

    style MBVS fill:#4da6ff,stroke:#0066cc,color:white
    style ConsistencyCheck fill:#f6546a,stroke:#c30052,color:white
    style PassMB fill:#10b981,stroke:#059669,color:white
    style FailMB fill:#ff5555,stroke:#dd3333,color:white
```

## 📋 任務追蹤驗證

此流程驗證 tasks.md 為唯一依據：

```mermaid
graph TD
    TTV["任務追蹤<br>驗證"] --> CheckTasksFile["檢查 tasks.md<br>存在與格式"]
    CheckTasksFile --> VerifyReferences["驗證其他文件<br>對任務的參照"]
    VerifyReferences --> ProgressCheck["檢查與<br>progress.md 一致"]
    ProgressCheck --> StatusCheck["驗證任務狀態<br>正確性"]

    StatusCheck --> TaskConsistency{"任務<br>正確追蹤？"}
    TaskConsistency -->|"是"| PassTasks["✅ 任務追蹤<br>驗證通過"]
    TaskConsistency -->|"否"| FailTasks["❌ 任務追蹤<br>發現問題"]

    FailTasks --> TaskFixSuggestions["產生任務追蹤<br>修正建議"]

    style TTV fill:#4da6ff,stroke:#0066cc,color:white
    style TaskConsistency fill:#f6546a,stroke:#c30052,color:white
    style PassTasks fill:#10b981,stroke:#059669,color:white
    style FailTasks fill:#ff5555,stroke:#dd3333,color:white
```

## 🔄 參照驗證流程

此流程確保文件間交互參照正確：

```mermaid
graph TD
    RV["參照<br>驗證"] --> FindRefs["尋找文件間<br>交互參照"]
    FindRefs --> VerifyRefs["驗證參照<br>正確性"]
    VerifyRefs --> CheckBackRefs["檢查雙向<br>參照"]

    CheckBackRefs --> RefConsistency{"參照<br>一致？"}
    RefConsistency -->|"是"| PassRefs["✅ 參照驗證<br>通過"]
    RefConsistency -->|"否"| FailRefs["❌ 參照<br>發現問題"]

    FailRefs --> RefFixSuggestions["產生參照<br>修正建議"]

    style RV fill:#4da6ff,stroke:#0066cc,color:white
    style RefConsistency fill:#f6546a,stroke:#c30052,color:white
    style PassRefs fill:#10b981,stroke:#059669,color:white
    style FailRefs fill:#ff5555,stroke:#dd3333,color:white
```

## 🚨 階段專屬驗證流程

### VAN 階段驗證

```mermaid
graph TD
    VAN["VAN 階段<br>驗證"] --> InitCheck["檢查初始化<br>完整性"]
    InitCheck --> PlatformCheck["驗證平台<br>偵測"]
    PlatformCheck --> ComplexityCheck["驗證複雜度<br>判斷"]

    ComplexityCheck --> VANConsistency{"VAN 階段<br>完成？"}
    VANConsistency -->|"是"| PassVAN["✅ VAN 階段<br>驗證通過"]
    VANConsistency -->|"否"| FailVAN["❌ VAN 階段<br>發現問題"]

    style VAN fill:#4da6ff,stroke:#0066cc,color:white
    style VANConsistency fill:#f6546a,stroke:#c30052,color:white
    style PassVAN fill:#10b981,stroke:#059669,color:white
    style FailVAN fill:#ff5555,stroke:#dd3333,color:white
```

### PLAN 階段驗證

```mermaid
graph TD
    PLAN["PLAN 階段<br>驗證"] --> PlanCheck["檢查規劃<br>文件"]
    PlanCheck --> TaskBreakdown["驗證任務<br>拆解"]
    TaskBreakdown --> ScopeCheck["驗證範圍<br>定義"]

    ScopeCheck --> PLANConsistency{"PLAN 階段<br>完成？"}
    PLANConsistency -->|"是"| PassPLAN["✅ PLAN 階段<br>驗證通過"]
    PLANConsistency -->|"否"| FailPLAN["❌ PLAN 階段<br>發現問題"]

    style PLAN fill:#4da6ff,stroke:#0066cc,color:white
    style PLANConsistency fill:#f6546a,stroke:#c30052,color:white
    style PassPLAN fill:#10b981,stroke:#059669,color:white
    style FailPLAN fill:#ff5555,stroke:#dd3333,color:white
```

### CREATIVE 階段驗證

```mermaid
graph TD
    CREATIVE["CREATIVE 階段<br>驗證"] --> DesignCheck["檢查設計<br>文件"]
    DesignCheck --> ArchCheck["驗證架構<br>決策"]
    ArchCheck --> PatternCheck["驗證設計<br>模式"]

    PatternCheck --> CREATIVEConsistency{"CREATIVE 階段<br>完成？"}
    CREATIVEConsistency -->|"是"| PassCREATIVE["✅ CREATIVE 階段<br>驗證通過"]
    CREATIVEConsistency -->|"否"| FailCREATIVE["❌ CREATIVE 階段<br>發現問題"]

    style CREATIVE fill:#4da6ff,stroke:#0066cc,color:white
    style CREATIVEConsistency fill:#f6546a,stroke:#c30052,color:white
    style PassCREATIVE fill:#10b981,stroke:#059669,color:white
    style FailCREATIVE fill:#ff5555,stroke:#dd3333,color:white
```

### IMPLEMENT 階段技術驗證

保留原 QA 驗證四點流程：

```mermaid
graph TD
    IMPLEMENT["IMPLEMENT 階段<br>驗證"] --> ReadDesign["讀取設計決策"]
    ReadDesign --> FourChecks["四點技術<br>驗證"]

    FourChecks --> DepCheck["1️⃣ 相依套件<br>驗證"]
    DepCheck --> ConfigCheck["2️⃣ 設定檔<br>驗證"]
    ConfigCheck --> EnvCheck["3️⃣ 環境<br>驗證"]
    EnvCheck --> MinBuildCheck["4️⃣ 最小建構<br>測試"]

    MinBuildCheck --> IMPLEMENTConsistency{"技術<br>前置條件達成？"}
    IMPLEMENTConsistency -->|"是"| PassIMPLEMENT["✅ IMPLEMENT 階段<br>驗證通過"]
    IMPLEMENTConsistency -->|"否"| FailIMPLEMENT["❌ IMPLEMENT 階段<br>發現問題"]

    style IMPLEMENT fill:#4da6ff,stroke:#0066cc,color:white
    style FourChecks fill:#f6546a,stroke:#c30052,color:white
    style IMPLEMENTConsistency fill:#f6546a,stroke:#c30052,color:white
    style PassIMPLEMENT fill:#10b981,stroke:#059669,color:white
    style FailIMPLEMENT fill:#ff5555,stroke:#dd3333,color:white
```

## 📋 通用驗證指令執行

### 記憶體庫驗證指令：

```bash
# 檢查記憶體庫檔案存在與新舊
ls -la memory-bank/
find memory-bank/ -type f -mtime -7 | sort

# 檢查檔案間一致性
grep -r "task" memory-bank/
grep -r "requirement" memory-bank/
```

### 任務追蹤驗證指令：

```bash
# 驗證 tasks.md 是否存在
test -f tasks.md && echo "✅ tasks.md 存在" || echo "❌ tasks.md 缺失"

# 檢查其他檔案對 tasks 的參照
grep -r "Task" --include="*.md" .
grep -r "task" --include="*.md" . | grep -v "tasks.md" | wc -l

# 驗證任務狀態一致性
grep -i "completed\|done\|finished" tasks.md
grep -i "in progress\|started" tasks.md
```

### 參照驗證指令：

```bash
# 尋找檔案間交互參照
grep -r "see\|refer\|reference" --include="*.md" .

# 檢查斷裂參照
for file in $(grep -l "see\|refer\|reference" --include="*.md" .); do
  for ref in $(grep -o '[a-zA-Z0-9_-]*\.md' $file); do
    test -f $ref || echo "❌ 斷裂參照: $ref in $file"
  done
done
```

## 📋 1️⃣ 相依套件驗證流程（原始）

此驗證點確保所有必要套件皆正確安裝。

### 指令執行：

```bash
# 檢查套件是否已安裝
npm list react react-dom tailwindcss postcss autoprefixer

# 驗證套件版本是否符合需求
npm list | grep -E "react|tailwind|postcss"

# 檢查 peer dependency 警告
npm ls --depth=0
```

### 驗證標準：

- 所有必要套件皆已安裝
- 版本需與需求相容
- 無重大 peer dependency 警告
- 必要開發套件需存在

### 常見修正：

- `npm install [缺少套件]` - 安裝缺少套件
- `npm install [套件]@[版本]` - 修正版本不符
- `npm install --save-dev [開發套件]` - 補齊開發相依

## 📝 2️⃣ 設定檔驗證流程（原始）

此驗證點確保設定檔格式正確。

### 指令執行：

```bash
# 檢查 package.json 的 module type
grep "\"type\":" package.json

# 驗證設定檔副檔名與 module type 是否相符
find . -name "*.config.*" | grep -E "\.(js|cjs|mjs)$"

# 測試設定檔語法
node -c *.config.js || node -c *.config.cjs || node -c *.config.mjs
```

### 驗證標準：

- 設定檔副檔名需與 package.json module type 相符
- 檔案語法需正確
- 設定需參照已安裝套件

### 常見修正：

- ES module 專案將 `.js` 改為 `.cjs`
- 修正設定檔語法錯誤
- 設定內容需參照已安裝套件

## 🌐 3️⃣ 環境驗證流程（原始）

此驗證點確保開發環境設置正確。

### 指令執行：

```bash
# 檢查建構工具
npm run --help

# 驗證 node 版本相容性
node -v

# 檢查環境變數
printenv | grep -E "NODE_|PATH|HOME"

# 驗證存取權限
ls -la .
```

### 驗證標準：

- Node.js 版本需相容
- package.json 需有建構指令
- 環境需有必要權限
- 必要環境變數需設置

### 常見修正：

- 更新 Node.js 版本
- 補齊 package.json scripts
- 修正檔案權限（chmod/icacls）
- 設定必要環境變數

## 🔥 4️⃣ 最小建構測試流程（原始）

此驗證點測試最小建構，確保基本功能可運作。

### 指令執行：

```bash
# 執行最小建構
npm run build -- --dry-run || npm run dev -- --dry-run

# 驗證進入點檔案存在
find src -name "main.*" -o -name "index.*"

# 驗證 HTML 進入點
grep -i "script.*src=" index.html
```

### 驗證標準：

- 建構過程無錯誤
- 進入點檔案存在且正確參照
- HTML 需正確參照 JS 進入點
- 測試環境可正常渲染

### 常見修正：

- 修正 HTML 進入點參照
- 修正 JS 匯入路徑
- 修正建構設定錯誤
- 修正路徑或參照錯誤

## 📊 強化綜合 QA 報告格式

```
╔═════════════════════════ 🔍 強化 QA 驗證報告 ═════════════════════╗
│                                                                               │
│ 專案： [專案名稱]               日期： [當前日期]                    │
│ 平台： [作業系統]               偵測階段： [目前階段]               │
│                                                                               │
│ ━━━━━━━━━━━━━━━━━━━━━━━━ 通用驗證結果 ━━━━━━━━━━━━━━━━━━━━━━━ │
│                                                                               │
│ 1️⃣ 記憶體庫驗證                                                           │
│    ✓ 核心檔案： [狀態]                                                     │
│    ✓ 內容一致性： [狀態]                                                    │
│    ✓ 最後修改： [狀態]                                                      │
│                                                                               │
│ 2️⃣ 任務追蹤驗證                                                           │
│    ✓ tasks.md 狀態： [狀態]                                                 │
│    ✓ 任務參照： [狀態]                                                      │
│    ✓ 狀態一致性： [狀態]                                                    │
│                                                                               │
│ 3️⃣ 參照驗證                                                               │
│    ✓ 交互參照： [狀態]                                                      │
│    ✓ 參照正確性： [狀態]                                                    │
│                                                                               │
│ ━━━━━━━━━━━━━━━━━━━━━━━ 階段專屬驗證 ━━━━━━━━━━━━━━━━━━━━━━━━━ │
│                                                                               │
│ [VAN/PLAN/CREATIVE/IMPLEMENT] 階段驗證                                       │
│    ✓ [階段專屬檢查 1]： [狀態]                                              │
│    ✓ [階段專屬檢查 2]： [狀態]                                              │
│    ✓ [階段專屬檢查 3]： [狀態]                                              │
│                                                                               │
│ [技術驗證區塊僅於 IMPLEMENT 階段顯示]                                        │
│                                                                               │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━ 整體狀態 ━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│                                                                               │
│ ✅ 驗證通過 - 目前階段專案品質已驗證                                         │
│                                                                               │
╚═══════════════════════════════════════════════════════════════════════════════╝
```

## 🚫 強化失敗報告格式

若驗證失敗，將產生詳細失敗報告：

```
╔═════════════════════════ ⚠️ QA 驗證失敗 ═════════════════════════════╗
│                                                                                 │
│ 專案： [專案名稱]               日期： [當前日期]                      │
│ 平台： [作業系統]               偵測階段： [目前階段]                 │
│                                                                                 │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━ 失敗檢查 ━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│                                                                                 │
│ ❌ 記憶體庫問題                                                           │
│    • [具體問題細節]                                                       │
│    • [具體問題細節]                                                       │
│                                                                                 │
│ ❌ 任務追蹤問題                                                           │
│    • [具體問題細節]                                                       │
│    • [具體問題細節]                                                       │
│                                                                                 │
│ ❌ 參照問題                                                               │
│    • [具體問題細節]                                                       │
│    • [具體問題細節]                                                       │
│                                                                                 │
│ ❌ [階段]專屬問題                                                         │
│    • [具體問題細節]                                                       │
│    • [具體問題細節]                                                       │
│                                                                                 │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━ 必要修正 ━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│                                                                                 │
│ 1. [具體修正指令與說明]                                                    │
│ 2. [具體修正指令與說明]                                                    │
│ 3. [具體修正指令與說明]                                                    │
│                                                                                 │
│ ⚠️ 驗證失敗 - 請先修正問題再繼續                                          │
│                                                                                 │
╚═════════════════════════════════════════════════════════════════════════════════╝
```

## 🔄 QA-ANYTIME 啟動協定

強化 QA 模式可於開發任意時機啟動：

```mermaid
graph TD
    Start["使用者輸入：QA"] --> DetectContext["偵測目前情境"]
    DetectContext --> RunQA["依情境執行 QA 檢查"]
    RunQA --> GenerateReport["產生對應 QA 報告"]
    GenerateReport --> UserResponse["回報結果給使用者"]

    UserResponse --> FixNeeded{"需修正？"}
    FixNeeded -->|"是"| SuggestFixes["顯示修正指引"]
    FixNeeded -->|"否"| ContinueWork["繼續目前階段作業"]

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style FixNeeded fill:#f6546a,stroke:#c30052,color:white
    style SuggestFixes fill:#ff5555,stroke:#dd3333,color:white
    style ContinueWork fill:#10b981,stroke:#059669,color:white
```

此強化 QA 模式為開發全程的「品質守門員」，確保文件持續維護且各階段需求皆滿足後方可進入下一階段。
