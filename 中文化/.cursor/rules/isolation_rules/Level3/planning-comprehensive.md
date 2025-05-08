---
description: Level 3 全面規劃
globs: planning-comprehensive.md
alwaysApply: false
---

# LEVEL 3 全面規劃

> **重點摘要：** 本文件提供 Level 3（中階功能）任務的結構化規劃指引，強調全面規劃、創意階段與明確實作策略。

## 🏗️ 規劃流程

```mermaid
graph TD
    Start["規劃開始"] --> Req["📋 需求<br>分析"]
    Req --> Comp["🔍 元件<br>分析"]
    Comp --> Design["🎨 設計<br>決策"]
    Design --> Impl["⚙️ 實作<br>策略"]
    Impl --> Test["🧪 測試<br>策略"]
    Test --> Doc["📚 文件<br>計畫"]

    Design --> Creative["創意階段："]
    Creative --> UI["UI/UX 設計"]
    Creative --> Arch["架構"]
    Creative --> Algo["演算法"]

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style Req fill:#ffa64d,stroke:#cc7a30,color:white
    style Comp fill:#4dbb5f,stroke:#36873f,color:white
    style Design fill:#d94dbb,stroke:#a3378a,color:white
    style Impl fill:#4dbbbb,stroke:#368787,color:white
    style Test fill:#d971ff,stroke:#a33bc2,color:white
    style Doc fill:#ff71c2,stroke:#c23b8a,color:white
```

## 🔄 等級轉換處理

```mermaid
graph TD
    L3["Level 3 任務"] --> Assess["持續<br>評估"]

    Assess --> Down["降級至<br>Level 1/2"]
    Assess --> Up["升級至<br>Level 4"]

    Down --> L12Trigger["觸發條件：<br>- 較預期簡單<br>- 範圍有限<br>- 元件少"]

    Up --> L4Trigger["觸發條件：<br>- 系統層級影響<br>- 架構變更<br>- 高複雜度"]

    L12Trigger --> L12Switch["切換至<br>Level 1/2 流程"]
    L4Trigger --> L4Switch["切換至<br>Level 4 流程"]
```

## 📋 規劃範本

```markdown
# 功能規劃文件

## 需求分析

- 核心需求：
  - [ ] 需求 1
  - [ ] 需求 2
- 技術限制：
  - [ ] 限制 1
  - [ ] 限制 2

## 元件分析

- 影響元件：
  - 元件 1
    - 需變更內容：
    - 相依性：
  - 元件 2
    - 需變更內容：
    - 相依性：

## 設計決策

- 架構：
  - [ ] 決策 1
  - [ ] 決策 2
- UI/UX：
  - [ ] 設計 1
  - [ ] 設計 2
- 演算法：
  - [ ] 演算法 1
  - [ ] 演算法 2

## 實作策略

1. 階段 1：
   - [ ] 任務 1
   - [ ] 任務 2
2. 階段 2：
   - [ ] 任務 3
   - [ ] 任務 4

## 測試策略

- 單元測試：
  - [ ] 測試 1
  - [ ] 測試 2
- 整合測試：
  - [ ] 測試 3
  - [ ] 測試 4

## 文件計畫

- [ ] API 文件
- [ ] 使用者指南更新
- [ ] 架構文件
```

## 🎨 創意階段識別

```mermaid
graph TD
    subgraph "創意階段需求"
    UI["🎨 UI/UX 設計<br>需求：是/否"]
    Arch["🏗️ 架構設計<br>需求：是/否"]
    Algo["⚙️ 演算法設計<br>需求：是/否"]
    end

    UI --> UITrig["觸發條件：<br>- 新 UI 元件<br>- UX 流程變更"]
    Arch --> ArchTrig["觸發條件：<br>- 系統結構變更<br>- 新整合"]
    Algo --> AlgoTrig["觸發條件：<br>- 效能關鍵<br>- 複雜邏輯"]

    style UI fill:#4dbb5f,stroke:#36873f,color:white
    style Arch fill:#ffa64d,stroke:#cc7a30,color:white
    style Algo fill:#d94dbb,stroke:#a3378a,color:white
```

## ✅ 驗證檢查清單

```mermaid
graph TD
    subgraph "規劃驗證"
    R["需求<br>完成"]
    C["元件<br>已確認"]
    D["設計決策<br>已定"]
    I["實作計畫<br>就緒"]
    T["測試策略<br>已定"]
    Doc["文件計畫<br>就緒"]
    end

    R --> C --> D --> I --> T --> Doc

    style R fill:#4dbb5f,stroke:#36873f,color:white
    style C fill:#ffa64d,stroke:#cc7a30,color:white
    style D fill:#d94dbb,stroke:#a3378a,color:white
    style I fill:#4dbbbb,stroke:#368787,color:white
    style T fill:#d971ff,stroke:#a33bc2,color:white
    style Doc fill:#ff71c2,stroke:#c23b8a,color:white
```

## 🔄 實作階段

```mermaid
graph LR
    Setup["🛠️ 設定"] --> Core["⚙️ 核心<br>實作"]
    Core --> UI["🎨 UI<br>實作"]
    UI --> Test["🧪 測試"]
    Test --> Doc["📚 文件"]

    style Setup fill:#4da6ff,stroke:#0066cc,color:white
    style Core fill:#4dbb5f,stroke:#36873f,color:white
    style UI fill:#ffa64d,stroke:#cc7a30,color:white
    style Test fill:#d94dbb,stroke:#a3378a,color:white
    style Doc fill:#4dbbbb,stroke:#368787,color:white
```

## 🔄 與記憶體庫整合

```mermaid
graph TD
    L3["Level 3<br>任務"] --> PB["全面<br>projectbrief.md"]
    L3 --> AC["詳細<br>activeContext.md"]
    L3 --> TM["結構化<br>tasks.md"]
    L3 --> PM["詳細<br>progress.md"]

    PB & AC & TM & PM --> MB["記憶體庫<br>整合"]
    MB --> NextPhase["進入<br>實作階段"]
```

## 🚨 規劃效率原則

請記住：

```
┌─────────────────────────────────────────────────────┐
│ Level 3 規劃需全面設計，但避免過度設計。              │
│ 專注於可維護、文件完善的功能交付。                   │
└─────────────────────────────────────────────────────┘
```
