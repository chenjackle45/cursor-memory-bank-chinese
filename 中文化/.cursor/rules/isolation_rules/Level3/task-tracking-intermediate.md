---
description: Level 3 中階任務追蹤
globs: task-tracking-intermediate.md
alwaysApply: false
---

# LEVEL 3 中階任務追蹤

> **重點摘要：** 本文件提供 Level 3（中階功能）任務的結構化追蹤指引，包含視覺化追蹤元素與明確檢查點。

## 🔍 任務追蹤流程

```mermaid
graph TD
    Start["任務開始"] --> Init["📋 初始化<br>任務登錄"]
    Init --> Struct["🏗️ 建立任務<br>結構"]
    Struct --> Track["📊 進度<br>追蹤"]
    Track --> Update["🔄 定期<br>更新"]
    Update --> Complete["✅ 任務<br>完成"]

    Struct --> Components["組成要素："]
    Components --> Req["需求"]
    Components --> Steps["實作<br>步驟"]
    Components --> Creative["創意階段<br>標記"]
    Components --> Check["檢查點"]

    Track --> Status["追蹤狀態："]
    Status --> InProg["🔄 進行中"]
    Status --> Block["⛔ 阻塞"]
    Status --> Done["✅ 完成"]
    Status --> Skip["⏭️ 已略過"]

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style Init fill:#ffa64d,stroke:#cc7a30,color:white
    style Struct fill:#4dbb5f,stroke:#36873f,color:white
    style Track fill:#d94dbb,stroke:#a3378a,color:white
    style Update fill:#4dbbbb,stroke:#368787,color:white
    style Complete fill:#d971ff,stroke:#a33bc2,color:white
```

## 📋 任務登錄範本

```markdown
# [任務標題]

## 需求

- [ ] 需求 1
- [ ] 需求 2
- [ ] 需求 3

## 影響元件

- 元件 1
- 元件 2
- 元件 3

## 實作步驟

1. [ ] 步驟 1
2. [ ] 步驟 2
3. [ ] 步驟 3

## 創意階段需求

- [ ] 🎨 UI/UX 設計
- [ ] 🏗️ 架構設計
- [ ] ⚙️ 演算法設計

## 檢查點

- [ ] 需求已驗證
- [ ] 創意階段完成
- [ ] 實作已測試
- [ ] 文件已更新

## 目前狀態

- 階段：[目前階段]
- 狀態：[進行中/阻塞/完成]
- 阻礙事項：[如有]
```

## 🔄 進度追蹤視覺化

```mermaid
graph TD
    subgraph "任務進度"
    P1["✓ 需求<br>已定義"]
    P2["✓ 元件<br>已確認"]
    P3["→ 創意階段<br>進行中"]
    P4["□ 實作"]
    P5["□ 測試"]
    P6["□ 文件"]
    end

    style P1 fill:#4dbb5f,stroke:#36873f,color:white
    style P2 fill:#4dbb5f,stroke:#36873f,color:white
    style P3 fill:#ffa64d,stroke:#cc7a30,color:white
    style P4 fill:#d94dbb,stroke:#a3378a,color:white
    style P5 fill:#4dbbbb,stroke:#368787,color:white
    style P6 fill:#d971ff,stroke:#a33bc2,color:white
```

## ✅ 更新協議

```mermaid
sequenceDiagram
    participant Task as 任務登錄
    participant Status as 狀態更新
    participant Creative as 創意階段
    participant Implementation as 實作

    Task->>Status: 更新進度
    Status->>Creative: 標記創意階段
    Creative->>Implementation: 完成設計
    Implementation->>Status: 更新狀態
    Status->>Task: 標記完成
```

## 🎯 檢查點驗證

| 階段 | 驗證項目         | 狀態 |
| ---- | ---------------- | ---- |
| 需求 | 所有需求已記錄   | [ ]  |
| 元件 | 影響元件已列出   | [ ]  |
| 創意 | 設計決策已記錄   | [ ]  |
| 實作 | 程式碼變更已追蹤 | [ ]  |
| 測試 | 測試結果已記錄   | [ ]  |
| 文件 | 更新已完成       | [ ]  |

## 🔄 文件管理

```mermaid
graph TD
    Current["現有文件"] --> Active["啟用中：<br>- task-tracking-intermediate.md<br>- planning-comprehensive.md"]
    Current --> Required["下一步所需：<br>- creative-phase-enforcement.md<br>- implementation-phase-reference.md"]

    style Current fill:#4da6ff,stroke:#0066cc,color:white
    style Active fill:#4dbb5f,stroke:#36873f,color:white
    style Required fill:#ffa64d,stroke:#cc7a30,color:white
```
