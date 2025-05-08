---
description: Level 2 簡易增強任務的基本工作流程
globs: "**/level2/**", "**/workflow/**"
alwaysApply: false
---

# LEVEL 2 任務工作流程

> **重點摘要：** 本文件說明 Level 2（簡易增強）任務的結構化且高效率工作流程，包含 6 個關鍵階段、里程碑檢查點與品質驗證。

## 🔍 LEVEL 2 工作流程總覽

```mermaid
graph LR
    Init["1. 初始化"] --> Doc["2. 文件<br>設定"]
    Doc --> Plan["3. 任務<br>規劃"]
    Plan --> Impl["4. 實作"]
    Impl --> Reflect["5. 反思"]
    Reflect --> Archive["6. 歸檔"]

    %% Document connections for each phase
    Init -.-> InitDocs["初始化"]
    Doc -.-> DocDocs["文件"]
    Plan -.-> PlanDocs["規劃"]
    Impl -.-> ImplDocs["實作"]
    Reflect -.-> ReflectDocs["反思"]
    Archive -.-> ArchiveDocs["歸檔"]
```

Level 2 任務屬於簡易增強，需結構化流程與適度規劃、文件。本流程兼顧流程與效率。

## 📋 工作流程階段

### 階段 1：初始化

```mermaid
graph TD
    Start["開始 Level 2 任務"] --> Platform{"偵測<br>平台"}
    Platform --> FileCheck["關鍵檔案<br>驗證"]
    FileCheck --> LoadStructure["載入記憶體庫<br>結構"]
    LoadStructure --> TaskCreation["在 tasks.md<br>建立任務"]
    TaskCreation --> SetupComplete["初始化<br>完成"]
```

**步驟：**

1. 平台偵測
2. 關鍵檔案驗證
3. 載入記憶體庫結構
4. 在 tasks.md 建立任務
5. 定義初始任務範圍

**里程碑檢查點：**

```
✓ 初始化檢查點
- 平台已偵測並設定？ [是/否]
- 關鍵檔案已驗證？ [是/否]
- 記憶體庫已載入？ [是/否]
- 任務已建立於 tasks.md？ [是/否]
- 初始範圍已定義？ [是/否]

→ 全部是：進入文件設定
→ 有否：補齊初始化步驟
```

### 階段 2：文件設定

```mermaid
graph TD
    Start["開始文件<br>設定"] --> LoadTemplate["載入基本<br>文件範本"]
    LoadTemplate --> UpdateProject["更新<br>projectbrief.md"]
    UpdateProject --> UpdateContext["更新<br>activeContext.md"]
    UpdateContext --> SetupComplete["文件設定<br>完成"]
```

**步驟：**

1. 載入基本文件範本
2. 更新 projectbrief.md，記錄增強細節
3. 更新 activeContext.md，標記目前重點
4. 建立最小文件結構

**里程碑檢查點：**

```
✓ 文件檢查點
- 文件範本已載入？ [是/否]
- projectbrief.md 已更新？ [是/否]
- activeContext.md 已更新？ [是/否]
- 文件結構已建立？ [是/否]

→ 全部是：進入任務規劃
→ 有否：補齊文件設定
```

### 階段 3：任務規劃

```mermaid
graph TD
    Start["開始任務<br>規劃"] --> Requirements["明確定義<br>需求"]
    Requirements --> SubTasks["拆解為<br>子任務"]
    SubTasks --> TasksUpdate["更新 tasks.md<br>子任務"]
    TasksUpdate --> TimeEstimate["建立時間<br>預估"]
    TimeEstimate --> PlanComplete["規劃<br>完成"]
```

**步驟：**

1. 明確定義需求
2. 拆解為子任務
3. 在 tasks.md 更新子任務
4. 建立時間預估
5. 記錄相依與限制

**里程碑檢查點：**

```
✓ 規劃檢查點
- 需求明確定義？ [是/否]
- 任務已拆解為子任務？ [是/否]
- tasks.md 已更新子任務？ [是/否]
- 時間預估已建立？ [是/否]
- 相依已記錄？ [是/否]

→ 全部是：進入實作
→ 有否：補齊規劃步驟
```

### 階段 4：實作

```mermaid
graph TD
    Start["開始<br>實作"] --> SubTask1["完成<br>子任務 1"]
    SubTask1 --> UpdateStatus1["更新 tasks.md<br>狀態"]
    UpdateStatus1 --> SubTask2["完成<br>子任務 2"]
    SubTask2 --> UpdateStatus2["更新 tasks.md<br>狀態"]
    UpdateStatus2 --> FinalSubTask["完成<br>最終子任務"]
    FinalSubTask --> Verification["執行<br>驗證"]
    Verification --> ImplComplete["實作<br>完成"]
```

**步驟：**

1. 實作第一個子任務
2. 在 tasks.md 更新狀態
3. 實作其餘子任務
4. 每個子任務後定期更新狀態
5. 驗證整體實作

**里程碑檢查點：**

```
✓ 實作檢查點
- 所有子任務已完成？ [是/否]
- 狀態更新有維護？ [是/否]
- 增強功能已完整實作？ [是/否]
- 已執行基本驗證？ [是/否]
- tasks.md 已完整更新？ [是/否]

→ 全部是：進入反思
→ 有否：補齊實作步驟
```

### 階段 5：反思

```mermaid
graph TD
    Start["開始<br>反思"] --> Template["載入反思<br>範本"]
    Template --> Review["檢視已完成<br>增強"]
    Review --> Document["記錄成功與<br>挑戰"]
    Document --> Insights["萃取關鍵<br>洞見"]
    Insights --> Actions["定義後續<br>行動"]
    Actions --> ReflectComplete["反思<br>完成"]
```

**步驟：**

1. 載入反思範本
2. 檢視已完成增強
3. 記錄成功與挑戰
4. 萃取關鍵洞見
5. 定義未來行動項目

**里程碑檢查點：**

```
✓ 反思檢查點
- 反思範本已載入？ [是/否]
- 增強已檢視？ [是/否]
- 成功與挑戰已記錄？ [是/否]
- 關鍵洞見已萃取？ [是/否]
- 行動項目已定義？ [是/否]

→ 全部是：進入歸檔
→ 有否：補齊反思步驟
```

### 階段 6：歸檔

```mermaid
graph TD
    Start["開始<br>歸檔"] --> Template["載入歸檔<br>範本"]
    Template --> Gather["彙整實作<br>細節"]
    Gather --> Create["建立歸檔<br>文件"]
    Create --> CrossRef["建立交叉<br>參照"]
    CrossRef --> Update["更新記憶體<br>庫檔案"]
    Update --> ArchiveComplete["歸檔<br>完成"]
```

**步驟：**

1. 載入歸檔範本
2. 彙整實作細節
3. 建立歸檔文件
4. 建立交叉參照
5. 更新記憶體庫檔案

**里程碑檢查點：**

```
✓ 歸檔檢查點
- 歸檔範本已載入？ [是/否]
- 實作細節已彙整？ [是/否]
- 歸檔文件已建立？ [是/否]
- 交叉參照已建立？ [是/否]
- 記憶體庫檔案已更新？ [是/否]

→ 全部是：任務完成
→ 有否：補齊歸檔步驟
```

## 📋 工作流程驗證清單

```
✓ 最終工作流程驗證
- 所有階段已完成？ [是/否]
- 所有里程碑檢查點通過？ [是/否]
- tasks.md 已完整更新？ [是/否]
- 反思文件已建立？ [是/否]
- 歸檔文件已建立？ [是/否]
- 記憶體庫已完整更新？ [是/否]

→ 全部是：Level 2 任務成功完成
→ 有否：補齊未完成項目
```

## 📋 最小模式工作流程

最小模式可用以下精簡流程：

```
1. 初始化：驗證環境、建立任務登錄
2. 文件：更新 projectbrief 與 activeContext
3. 規劃：定義需求、子任務、預估
4. 實作：完成子任務、更新狀態
5. 反思：記錄關鍵洞見與行動
6. 歸檔：記錄完成與交叉參照
```

## 🔄 等級轉換處理

```mermaid
graph TD
    L2["Level 2 任務"] --> Assess["持續<br>評估"]

    Assess --> Down["降級至<br>Level 1"]
    Assess --> Up["升級至<br>Level 3/4"]

    Down --> L1Trigger["觸發條件：<br>- 較預期簡單<br>- 可快速修復<br>- 單一元件"]

    Up --> L34Trigger["觸發條件：<br>- 較複雜<br>- 多元件<br>- 需設計"]

    L1Trigger --> L1Switch["切換至<br>Level 1 流程"]
    L34Trigger --> L34Switch["切換至<br>Level 3/4 流程"]
```

## 🔄 與記憶體庫整合

```mermaid
graph TD
    Workflow["Level 2<br>工作流程"] --> PB["更新<br>projectbrief.md"]
    Workflow --> AC["更新<br>activeContext.md"]
    Workflow --> TM["維護<br>tasks.md"]
    Workflow --> PM["更新<br>progress.md"]

    PB & AC & TM & PM --> MB["記憶體庫<br>整合"]
    MB --> NextTask["轉換至<br>下一任務"]
```

## 🚨 效率原則

請記住：

```
┌─────────────────────────────────────────────────────┐
│ Level 2 工作流程兼顧流程與效率。                     │
│ 遵循結構但避免不必要的負擔。                         │
└─────────────────────────────────────────────────────┘
```

這確保簡易增強能以適當的文件與流程完成。
