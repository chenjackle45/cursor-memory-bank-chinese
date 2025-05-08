---
description: creative phase enforcement
globs: creative-phase-enforcement.md
alwaysApply: false
---

# 創意階段強制執行

> **重點摘要：** 本文件針對 Level 3-4 任務，嚴格強制執行創意階段需求，確保所有設計決策在進入實作前皆已妥善記錄與驗證。

## 🔍 強制執行流程

```mermaid
graph TD
    Start["任務開始"] --> Check{"Level 3-4<br>任務？"}
    Check -->|Yes| Analyze["分析設計<br>決策點"]
    Check -->|No| Optional["創意階段<br>可選"]

    Analyze --> Decision{"需要設計<br>決策？"}
    Decision -->|Yes| Gate["🚨 實作<br>阻擋"]
    Decision -->|No| Allow["允許<br>實作"]

    Gate --> Creative["進入創意<br>階段"]
    Creative --> Verify{"所有決策<br>已記錄？"}
    Verify -->|No| Return["返回<br>創意階段"]
    Verify -->|Yes| Proceed["允許<br>實作"]

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style Check fill:#ffa64d,stroke:#cc7a30,color:white
    style Analyze fill:#4dbb5f,stroke:#36873f,color:white
    style Gate fill:#d94dbb,stroke:#a3378a,color:white
    style Creative fill:#4dbbbb,stroke:#368787,color:white
    style Verify fill:#d971ff,stroke:#a33bc2,color:white
```

## 🚨 強制執行關卡

```mermaid
graph TD
    subgraph "創意階段關卡"
    G1["進入關卡<br>驗證需求"]
    G2["過程關卡<br>驗證進度"]
    G3["結束關卡<br>驗證完成"]
    end

    G1 --> G2 --> G3

    style G1 fill:#4dbb5f,stroke:#36873f,color:white
    style G2 fill:#ffa64d,stroke:#cc7a30,color:white
    style G3 fill:#d94dbb,stroke:#a3378a,color:white
```

## 📋 強制執行檢查表

```markdown
## 進入關卡驗證

- [ ] 任務複雜度為 Level 3-4
- [ ] 已識別設計決策
- [ ] 已記錄創意階段需求
- [ ] 已通知必要參與者

## 過程關卡驗證

- [ ] 所有選項皆有考慮
- [ ] 優缺點已記錄
- [ ] 技術限制已識別
- [ ] 實作影響已評估

## 結束關卡驗證

- [ ] 所有決策已記錄
- [ ] 選擇理由已說明
- [ ] 已規劃實作方案
- [ ] 已對照需求驗證
```

## 🚨 實作阻擋通知

當創意階段尚未完成但已要求實作時：

```
🚨 實作阻擋
創意階段必須完成後才能進入實作。

必須完成的創意階段：
- [ ] [創意階段 1]
- [ ] [創意階段 2]
- [ ] [創意階段 3]

⛔ 這是嚴格阻擋
所有創意階段未完成前，實作不得進行。
輸入 "PHASE.REVIEW" 以開始創意階段審查。
```

## ✅ 驗證流程

```mermaid
graph TD
    subgraph "驗證步驟"
    V1["1. 需求<br>檢查"]
    V2["2. 文件<br>審查"]
    V3["3. 決策<br>驗證"]
    V4["4. 實作<br>就緒"]
    end

    V1 --> V2 --> V3 --> V4

    style V1 fill:#4dbb5f,stroke:#36873f,color:white
    style V2 fill:#ffa64d,stroke:#cc7a30,color:white
    style V3 fill:#d94dbb,stroke:#a3378a,color:white
    style V4 fill:#4dbbbb,stroke:#368787,color:white
```

## 🔄 創意階段標記

請使用下列標記明確標示創意階段界線：

```markdown
🎨🎨🎨 進入創意階段: [類型] 🎨🎨🎨
聚焦： [特定元件/功能]
目標： [本創意階段明確目標]
需求： [需求清單]

[創意階段內容]

🎨 創意檢查點: [里程碑]

- 進度: [狀態]
- 決策: [清單]
- 下一步: [計畫]

🎨🎨🎨 離開創意階段 🎨🎨🎨
摘要: [簡述]
關鍵決策: [清單]
下一步: [實作計畫]
```

## 🔄 文件管理

```mermaid
graph TD
    Current["目前文件"] --> Active["作用中：<br>- creative-phase-enforcement.md"]
    Current --> Related["相關：<br>- creative-phase-architecture.md<br>- task-tracking-intermediate.md"]

    style Current fill:#4da6ff,stroke:#0066cc,color:white
    style Active fill:#4dbb5f,stroke:#36873f,color:white
    style Related fill:#ffa64d,stroke:#cc7a30,color:white
```
