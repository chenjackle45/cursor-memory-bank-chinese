---
description: 創意階段架構設計
globs: creative-phase-architecture.md
alwaysApply: false
---

# 創意階段：架構設計

> **重點摘要：** 本文件為創意階段中的架構設計決策提供結構化指引，確保對各種選項進行全面評估，並清楚記錄架構選擇。

## 🏗️ 架構設計工作流程

```mermaid
graph TD
    Start["架構設計開始"] --> Req["1. 需求分析"]
    Req --> Comp["2. 元件識別"]
    Comp --> Options["3. 架構選項"]
    Options --> Eval["4. 選項評估"]
    Eval --> Decision["5. 決策與文件化"]
    Decision --> Valid["6. 驗證與確認"]

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style Req fill:#ffa64d,stroke:#cc7a30,color:white
    style Comp fill:#4dbb5f,stroke:#36873f,color:white
    style Options fill:#d94dbb,stroke:#a3378a,color:white
    style Eval fill:#4dbbbb,stroke:#368787,color:white
    style Decision fill:#d971ff,stroke:#a33bc2,color:white
    style Valid fill:#ff71c2,stroke:#c23b8a,color:white
```

## 📋 架構決策範本

```markdown
# 架構決策紀錄

## 背景

- 系統需求：
  - [需求 1]
  - [需求 2]
- 技術限制：
  - [限制 1]
  - [限制 2]

## 元件分析

- 核心元件：
  - [元件 1]： [用途/角色]
  - [元件 2]： [用途/角色]
- 互動關係：
  - [互動 1]
  - [互動 2]

## 架構選項

### 選項 1：[名稱]

- 說明：[簡要說明]
- 優點：
  - [優點 1]
  - [優點 2]
- 缺點：
  - [缺點 1]
  - [缺點 2]
- 技術適配度：[高/中/低]
- 複雜度：[高/中/低]
- 延展性：[高/中/低]

### 選項 2：[名稱]

[與選項 1 相同結構]

## 決策

- 選擇方案：[選項名稱]
- 理由：[說明]
- 實作考量：
  - [考量 1]
  - [考量 2]

## 驗證

- 滿足需求：
  - [✓] 需求 1
  - [✓] 需求 2
- 技術可行性：[評估]
- 風險評估：[說明]
```

## 🎯 架構評估指標

```mermaid
graph TD
    subgraph "評估指標"
    C1["延展性"]
    C2["可維護性"]
    C3["效能"]
    C4["安全性"]
    C5["成本"]
    C6["上市時程"]
    end

    style C1 fill:#4dbb5f,stroke:#36873f,color:white
    style C2 fill:#ffa64d,stroke:#cc7a30,color:white
    style C3 fill:#d94dbb,stroke:#a3378a,color:white
    style C4 fill:#4dbbbb,stroke:#368787,color:white
    style C5 fill:#d971ff,stroke:#a33bc2,color:white
    style C6 fill:#ff71c2,stroke:#c23b8a,color:white
```

## 📊 架構視覺化範本

### 元件圖範本

```mermaid
graph TD
    subgraph "系統架構"
    C1["元件 1"]
    C2["元件 2"]
    C3["元件 3"]

    C1 -->|"介面 1"| C2
    C2 -->|"介面 2"| C3
    end

    style C1 fill:#4dbb5f,stroke:#36873f,color:white
    style C2 fill:#ffa64d,stroke:#cc7a30,color:white
    style C3 fill:#d94dbb,stroke:#a3378a,color:white
```

### 資料流範本

```mermaid
sequenceDiagram
    participant C1 as 元件 1
    participant C2 as 元件 2
    participant C3 as 元件 3

    C1->>C2: 請求
    C2->>C3: 處理
    C3-->>C2: 回應
    C2-->>C1: 結果
```

## ✅ 驗證清單

```markdown
## 架構設計驗證

- [ ] 所有系統需求皆已覆蓋
- [ ] 元件職責明確
- [ ] 介面已明確定義
- [ ] 資料流已記錄
- [ ] 已考慮安全性
- [ ] 滿足延展性需求
- [ ] 滿足效能需求
- [ ] 維護方式已定義

## 實作準備度

- [ ] 所有元件已識別
- [ ] 相依關係已繪製
- [ ] 技術限制已記錄
- [ ] 風險評估已完成
- [ ] 資源需求已定義
- [ ] 時程預估已提供
```

## 🔄 架構審查流程

```mermaid
graph TD
    subgraph "審查流程"
    R1["技術審查"]
    R2["安全性審查"]
    R3["效能審查"]
    R4["最終核准"]
    end

    R1 --> R2 --> R3 --> R4

    style R1 fill:#4dbb5f,stroke:#36873f,color:white
    style R2 fill:#ffa64d,stroke:#cc7a30,color:white
    style R3 fill:#d94dbb,stroke:#a3378a,color:white
    style R4 fill:#4dbbbb,stroke:#368787,color:white
```

## 🔄 文件管理

```mermaid
graph TD
    Current["目前文件"] --> Active["作用中：<br>- creative-phase-architecture.md"]
    Current --> Related["相關：<br>- creative-phase-enforcement.md<br>- planning-comprehensive.md"]

    style Current fill:#4da6ff,stroke:#0066cc,color:white
    style Active fill:#4dbb5f,stroke:#36873f,color:white
    style Related fill:#ffa64d,stroke:#cc7a30,color:white
```
