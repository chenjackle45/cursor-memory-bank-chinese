---
description: PLAN 模式視覺化流程圖（程式碼建構）
globs: plan-mode-map.md
alwaysApply: false
---

# PLAN 模式：任務規劃流程圖

> **重點摘要：** 本視覺化地圖引導 PLAN 模式流程，聚焦於根據初始化階段判斷的複雜度等級，建立詳細的實作規劃，並於實作前強制進行技術驗證。

## 🧭 PLAN 模式流程

```mermaid
graph TD
    Start["啟動規劃"] --> ReadTasks["讀取 tasks.md<br>Core/task-tracking.md"]

    %% 複雜度判斷
    ReadTasks --> CheckLevel{"判斷<br>複雜度等級"}
    CheckLevel -->|"等級 2"| Level2["等級 2 規劃<br>Level2/enhancement-planning.md"]
    CheckLevel -->|"等級 3"| Level3["等級 3 規劃<br>Level3/feature-planning.md"]
    CheckLevel -->|"等級 4"| Level4["等級 4 規劃<br>Level4/system-planning.md"]

    %% 等級 2 規劃
    Level2 --> L2Review["檢視程式碼<br>結構"]
    L2Review --> L2Document["記錄<br>規劃變更"]
    L2Document --> L2Challenges["識別<br>挑戰"]
    L2Challenges --> L2Checklist["建立任務<br>清單"]
    L2Checklist --> L2Update["更新 tasks.md<br>規劃內容"]
    L2Update --> L2Tech["技術<br>驗證"]
    L2Tech --> L2Verify["驗證規劃<br>完整性"]

    %% 等級 3 規劃
    Level3 --> L3Review["檢視程式碼庫<br>結構"]
    L3Review --> L3Requirements["記錄詳細<br>需求"]
    L3Requirements --> L3Components["識別受影響<br>元件"]
    L3Components --> L3Plan["建立全面<br>實作規劃"]
    L3Plan --> L3Challenges["記錄挑戰<br>與解法"]
    L3Challenges --> L3Update["更新 tasks.md<br>規劃內容"]
    L3Update --> L3Tech["技術<br>驗證"]
    L3Tech --> L3Flag["標記需創意<br>階段元件"]
    L3Flag --> L3Verify["驗證規劃<br>完整性"]

    %% 等級 4 規劃
    Level4 --> L4Analysis["程式碼庫結構<br>分析"]
    L4Analysis --> L4Requirements["記錄全面<br>需求"]
    L4Requirements --> L4Diagrams["建立架構<br>圖"]
    L4Diagrams --> L4Subsystems["識別受影響<br>子系統"]
    L4Subsystems --> L4Dependencies["記錄相依套件<br>與整合點"]
    L4Dependencies --> L4Plan["建立分階段<br>實作規劃"]
    L4Plan --> L4Update["更新 tasks.md<br>規劃內容"]
    L4Update --> L4Tech["技術<br>驗證"]
    L4Tech --> L4Flag["標記需創意<br>階段元件"]
    L4Flag --> L4Verify["驗證規劃<br>完整性"]

    %% 技術驗證閘道 - 新增
    L2Tech & L3Tech & L4Tech --> TechGate["⛔ 技術<br>驗證閘道"]
    TechGate --> TechSelection["記錄技術<br>棧選擇"]
    TechSelection --> TechHelloWorld["建立 Hello World<br>概念驗證"]
    TechHelloWorld --> TechDependencies["驗證必要<br>相依套件"]
    TechDependencies --> TechConfig["驗證建構<br>設定"]
    TechConfig --> TechBuild["完成測試<br>建構"]
    TechBuild --> TechVerify["⛔ 技術<br>檢查點"]

    %% 驗證與完成
    L2Verify & L3Verify & L4Verify & TechVerify --> CheckCreative{"是否需<br>創意階段？"}

    %% 模式切換
    CheckCreative -->|"是"| RecCreative["下一模式：<br>CREATIVE 模式"]
    CheckCreative -->|"否"| RecImplement["下一模式：<br>IMPLEMENT 模式"]

    %% 技術閘道樣式
    style TechGate fill:#ff5555,stroke:#dd3333,color:white,stroke-width:3px
    style TechVerify fill:#ff5555,stroke:#dd3333,color:white,stroke-width:3px
    style TechSelection fill:#4da6ff,stroke:#0066cc,color:white
    style TechHelloWorld fill:#4da6ff,stroke:#0066cc,color:white
    style TechDependencies fill:#4da6ff,stroke:#0066cc,color:white
    style TechConfig fill:#4da6ff,stroke:#0066cc,color:white
    style TechBuild fill:#4da6ff,stroke:#0066cc,color:white
```

## 📋 等級專屬規劃方式

```mermaid
graph TD
    subgraph "等級 2：增強"
        L2A["基本需求<br>分析"]
        L2B["簡單元件<br>識別"]
        L2C["線性實作<br>規劃"]
        L2D["基本清單<br>建立"]
    end

    subgraph "等級 3：功能"
        L3A["詳細需求<br>分析"]
        L3B["元件對應<br>與相依"]
        L3C["多階段<br>實作規劃"]
        L3D["全面清單"]
        L3E["創意階段<br>識別"]
    end

    subgraph "等級 4：系統"
        L4A["架構需求<br>分析"]
        L4B["系統元件<br>對應"]
        L4C["子系統<br>整合規劃"]
        L4D["分階段實作<br>策略"]
        L4E["風險評估<br>與緩解"]
        L4F["多個創意<br>階段需求"]
    end

    L2A --> L2B --> L2C --> L2D
    L3A --> L3B --> L3C --> L3D --> L3E
    L4A --> L4B --> L4C --> L4D --> L4E --> L4F
```

## 🔧 技術驗證流程

```mermaid
graph TD
    Start["技術驗證開始"] --> Select["技術棧選擇"]
    Select --> Document["記錄選定<br>技術"]
    Document --> POC["建立最小化<br>概念驗證"]
    POC --> Build["驗證建構<br>流程可行"]
    Build --> Dependencies["驗證所有<br>相依套件"]
    Dependencies --> Config["確認設定檔<br>正確"]
    Config --> Test["完成測試<br>建構/執行"]
    Test --> Success{"所有檢查<br>通過？"}

    Success -->|"是"| Ready["可進入<br>實作"]
    Success -->|"否"| Fix["修正技術<br>問題"]
    Fix --> Document

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style POC fill:#4da6ff,stroke:#0066cc,color:white
    style Success fill:#ff5555,stroke:#dd3333,color:white
    style Fix fill:#ff5555,stroke:#dd3333,color:white
    style Ready fill:#10b981,stroke:#059669,color:white
```

## 📊 必要檔案狀態驗證

開始規劃前，請驗證檔案狀態：

```mermaid
graph TD
    Start["檔案狀態<br>驗證"] --> CheckTasks{"tasks.md<br>已初始化？"}

    CheckTasks -->|"否"| ErrorTasks["錯誤：<br>返回 VAN 模式"]
    CheckTasks -->|"是"| CheckActive{"activeContext.md<br>存在？"}

    CheckActive -->|"否"| ErrorActive["錯誤：<br>返回 VAN 模式"]
    CheckActive -->|"是"| ReadyPlan["可進行<br>規劃"]
```

## 📝 TASKS.MD 更新格式

規劃過程中，請於 tasks.md 依下列結構更新：

```
# 任務：[任務名稱]

## 描述
[詳細描述]

## 複雜度
等級：[2/3/4]
類型：[增強/功能/複雜系統]

## 技術棧
- 框架：[選定框架]
- 建構工具：[選定建構工具]
- 語言：[選定語言]
- 儲存：[選定儲存機制]

## 技術驗證檢查點
- [ ] 專案初始化指令已驗證
- [ ] 必要相依套件已識別並安裝
- [ ] 建構設定已驗證
- [ ] Hello world 驗證已完成
- [ ] 測試建構成功

## 狀態
- [x] 初始化完成
- [x] 規劃完成
- [ ] 技術驗證完成
- [ ] [實作步驟]

## 實作規劃
1. [步驟 1]
   - [子任務 1.1]
   - [子任務 1.2]
2. [步驟 2]
   - [子任務 2.1]
   - [子任務 2.2]

## 創意階段需求
- [ ] [元件 1] 設計
- [ ] [元件 2] 架構
- [ ] [元件 3] 資料模型

## 相依套件
- [相依套件 1]
- [相依套件 2]

## 挑戰與緩解
- [挑戰 1]：[緩解策略]
- [挑戰 2]：[緩解策略]
```

## 📋 創意階段識別

等級 3-4 任務需識別需創意階段的元件：

```mermaid
graph TD
    Start["創意階段<br>識別"] --> CheckComp{"元件<br>分析"}

    CheckComp --> UI["UI/UX<br>元件"]
    CheckComp --> Data["資料模型<br>元件"]
    CheckComp --> Arch["架構<br>元件"]
    CheckComp --> Algo["演算法<br>元件"]

    UI & Data & Arch & Algo --> Decision{"需設計決策？"}

    Decision -->|"是"| Flag["標記需<br>創意階段"]
    Decision -->|"否"| Skip["標準<br>實作"]

    Flag --> Document["記錄於<br>tasks.md"]
```

## 📊 技術驗證清單

```
✓ 技術驗證清單
- 技術棧明確定義？ [是/否]
- 專案初始化指令已記錄？ [是/否]
- 必要相依套件已識別？ [是/否]
- 已建立最小概念驗證？ [是/否]
- Hello world 建構/執行成功？ [是/否]
- 設定檔已驗證？ [是/否]
- 測試建構成功？ [是/否]

→ 全部為是：技術驗證完成，可進入下一階段
→ 任一為否：請先解決技術問題
```

## 📊 規劃驗證清單

```
✓ 規劃驗證清單
- 需求已明確記錄？ [是/否]
- 技術棧已驗證？ [是/否]
- 受影響元件已識別？ [是/否]
- 實作步驟已詳列？ [是/否]
- 相依套件已記錄？ [是/否]
- 挑戰與緩解已處理？ [是/否]
- 創意階段已識別（等級 3-4）？ [是/否/不適用]
- tasks.md 已更新規劃？ [是/否]

→ 全部為是：規劃完成，可進入下一模式
→ 任一為否：請補齊缺漏規劃內容
```

## 🔄 模式切換通知

規劃完成時，請通知使用者：

```
## 規劃完成

✅ 已建立實作規劃
✅ 技術棧已驗證
✅ tasks.md 已更新規劃
✅ 挑戰與緩解已記錄
[✅ 創意階段已識別（等級 3-4）]

→ 下一推薦模式：[CREATIVE/IMPLEMENT] 模式
```
