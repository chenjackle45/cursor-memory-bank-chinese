---
description: CREATIVE 模式視覺化流程圖（設計決策）
globs: "**/creative*/**", "**/design*/**", "**/decision*/**"
alwaysApply: false
---

# CREATIVE 模式：設計流程圖

> **重點摘要：** 本視覺化地圖引導 CREATIVE 模式流程，聚焦於針對需深入探索的元件進行結構化設計決策，於實作前完成設計。

## 🧭 CREATIVE 模式流程

```mermaid
graph TD
    Start["啟動 CREATIVE 模式"] --> ReadTasks["讀取 tasks.md<br>取得創意需求"]

    %% 初步評估
    ReadTasks --> VerifyPlan{"規劃完成<br>且創意階段<br>已標記？"}
    VerifyPlan -->|"否"| ReturnPlan["返回<br>PLAN 模式"]
    VerifyPlan -->|"是"| IdentifyPhases["識別需進行的<br>創意階段"]

    %% 創意階段選擇
    IdentifyPhases --> SelectPhase["選擇下一個<br>創意階段"]
    SelectPhase --> PhaseType{"創意<br>階段類型？"}

    %% 創意階段類型
    PhaseType -->|"UI/UX<br>設計"| UIPhase["UI/UX 創意階段<br>Core/creative-phase-uiux.md"]
    PhaseType -->|"架構<br>設計"| ArchPhase["ARCHITECTURE 創意階段<br>Core/creative-phase-architecture.md"]
    PhaseType -->|"資料模型<br>設計"| DataPhase["DATA MODEL 創意階段<br>Core/creative-phase-data.md"]
    PhaseType -->|"演算法<br>設計"| AlgoPhase["ALGORITHM 創意階段<br>Core/creative-phase-algorithm.md"]

    %% UI/UX 創意階段
    UIPhase --> UI_Problem["定義 UI/UX<br>問題"]
    UI_Problem --> UI_Research["研究 UI<br>模式"]
    UI_Research --> UI_Options["探索 UI<br>選項"]
    UI_Options --> UI_Evaluate["評估使用者<br>體驗"]
    UI_Evaluate --> UI_Decision["做出設計<br>決策"]
    UI_Decision --> UI_Document["記錄 UI<br>設計"]

    %% 架構創意階段
    ArchPhase --> Arch_Problem["定義架構<br>挑戰"]
    Arch_Problem --> Arch_Options["探索架構<br>選項"]
    Arch_Options --> Arch_Analyze["分析取捨"]
    Arch_Analyze --> Arch_Decision["做出架構<br>決策"]
    Arch_Decision --> Arch_Document["記錄<br>架構"]
    Arch_Document --> Arch_Diagram["建立架構<br>原理圖"]

    %% 資料模型創意階段
    DataPhase --> Data_Requirements["定義資料<br>需求"]
    Data_Requirements --> Data_Structure["設計資料<br>結構"]
    Data_Structure --> Data_Relations["定義<br>關聯"]
    Data_Relations --> Data_Validation["設計<br>驗證"]
    Data_Validation --> Data_Document["記錄<br>資料模型"]

    %% 演算法創意階段
    AlgoPhase --> Algo_Problem["定義演算法<br>問題"]
    Algo_Problem --> Algo_Options["探索演算法<br>方法"]
    Algo_Options --> Algo_Evaluate["評估時空<br>複雜度"]
    Algo_Evaluate --> Algo_Decision["做出演算法<br>決策"]
    Algo_Decision --> Algo_Document["記錄<br>演算法"]

    %% 文件與完成
    UI_Document & Arch_Diagram & Data_Document & Algo_Document --> CreateDoc["建立創意階段<br>文件"]
    CreateDoc --> UpdateTasks["更新 tasks.md<br>決策內容"]
    UpdateTasks --> MorePhases{"還有其他<br>創意階段？"}
    MorePhases -->|"是"| SelectPhase
    MorePhases -->|"否"| VerifyComplete["驗證所有<br>階段完成"]
    VerifyComplete --> NotifyComplete["通知創意<br>階段完成"]
```

## 📋 創意階段文件格式

每個創意階段應產出如下結構的文件：

```mermaid
graph TD
    subgraph "創意階段文件"
        Header["🎨 CREATIVE PHASE: [類型]"]
        Problem["問題說明<br>明確定義問題"]
        Options["選項分析<br>多種方法考量"]
        Pros["優缺點分析<br>各選項取捨"]
        Decision["決策<br>選擇方案與理由"]
        Impl["實作規劃<br>實作步驟"]
        Diagram["視覺化<br>解決方案原理圖"]
    end

    Header --> Problem --> Options --> Pros --> Decision --> Impl --> Diagram
```

## 🔍 創意類型與方法

```mermaid
graph TD
    subgraph "UI/UX 設計"
        UI1["使用流程<br>分析"]
        UI2["元件階層"]
        UI3["互動模式"]
        UI4["視覺設計<br>原則"]
    end

    subgraph "架構設計"
        A1["元件結構"]
        A2["資料流模式"]
        A3["介面設計"]
        A4["系統整合"]
    end

    subgraph "資料模型設計"
        D1["實體關聯"]
        D2["結構設計"]
        D3["驗證規則"]
        D4["查詢最佳化"]
    end

    subgraph "演算法設計"
        AL1["複雜度分析"]
        AL2["效率最佳化"]
        AL3["邊界情境處理"]
        AL4["延展性考量"]
    end
```

## 📊 必要檔案狀態驗證

開始創意階段前，請驗證檔案狀態：

```mermaid
graph TD
    Start["檔案狀態<br>驗證"] --> CheckTasks{"tasks.md<br>規劃完成？"}

    CheckTasks -->|"否"| ErrorPlan["錯誤：<br>返回 PLAN 模式"]
    CheckTasks -->|"是"| CheckCreative{"創意階段<br>已標記？"}

    CheckCreative -->|"否"| ErrorCreative["錯誤：<br>返回 PLAN 模式"]
    CheckCreative -->|"是"| ReadyCreative["可進行<br>創意階段"]
```

## 📋 選項分析範本

每個創意階段請分析多種選項：

```
## 選項分析

### 選項 1：[名稱]
**說明**：[簡要說明]
**優點**：
- [優點 1]
- [優點 2]
**缺點**：
- [缺點 1]
- [缺點 2]
**複雜度**：[低/中/高]
**實作時間**：[預估]

### 選項 2：[名稱]
**說明**：[簡要說明]
**優點**：
- [優點 1]
- [優點 2]
**缺點**：
- [缺點 1]
- [缺點 2]
**複雜度**：[低/中/高]
**實作時間**：[預估]

### 選項 3：[名稱]
**說明**：[簡要說明]
**優點**：
- [優點 1]
- [優點 2]
**缺點**：
- [缺點 1]
- [缺點 2]
**複雜度**：[低/中/高]
**實作時間**：[預估]
```

## 🎨 創意階段標記

創意階段請使用以下視覺標記：

```
🎨🎨🎨 進入創意階段：[類型] 🎨🎨🎨

[創意階段內容]

🎨 創意檢查點：[里程碑]

[補充內容]

🎨🎨🎨 離開創意階段 - 決策已定 🎨🎨🎨
```

## 📊 創意階段驗證清單

```
✓ 創意階段驗證
- 問題明確定義？ [是/否]
- 至少考慮三種選項？ [是/否]
- 每個選項皆有優缺點？ [是/否]
- 決策有明確理由？ [是/否]
- 包含實作規劃？ [是/否]
- 有視覺化/原理圖？ [是/否]
- tasks.md 已更新決策？ [是/否]

→ 全部為是：創意階段完成
→ 任一為否：請補齊缺漏內容
```

## 🔄 模式切換通知

所有創意階段完成時，請通知使用者：

```
## 創意階段完成

✅ 所有設計決策已完成
✅ 已建立創意階段文件
✅ tasks.md 已更新決策
✅ 實作規劃已更新

→ 下一推薦模式：IMPLEMENT 模式
```
