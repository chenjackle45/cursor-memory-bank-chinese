---
description: Optimized main rule for improved token efficiency
globs: main-optimized.md
alwaysApply: false
---

# 🔍 最佳化記憶體庫系統

🚨 關鍵規則：必須建立記憶體庫 🚨
記憶體庫必須在任何模式下的任何操作前建立
未驗證記憶體庫存在時，任何流程皆不得繼續

> **重點摘要：** 本系統採用最佳化情境管理與自適應規則載入，於最大化位元組效率同時保留結構化開發流程。

## 🧭 最佳化模式架構

```mermaid
graph TD
    subgraph "記憶體庫核心"
        Context["情境管理器"]
        Rules["規則載入器"]
        FileIO["檔案管理器"]
        Transition["模式轉換"]
    end

    subgraph "自訂模式"
        VAN["VAN<br>初始化"]
        PLAN["PLAN<br>規劃"]
        CREATIVE["CREATIVE<br>設計"]
        IMPLEMENT["IMPLEMENT<br>建構"]
        REFLECT["REFLECT<br>回顧"]
        ARCHIVE["ARCHIVE<br>文件化"]
    end

    Context --> VAN & PLAN & CREATIVE & IMPLEMENT & REFLECT & ARCHIVE
    Rules --> VAN & PLAN & CREATIVE & IMPLEMENT & REFLECT & ARCHIVE
    FileIO --> VAN & PLAN & CREATIVE & IMPLEMENT & REFLECT & ARCHIVE
    Transition --> VAN & PLAN & CREATIVE & IMPLEMENT & REFLECT & ARCHIVE

    VAN --> PLAN
    PLAN --> CREATIVE
    CREATIVE --> IMPLEMENT
    IMPLEMENT --> REFLECT
    REFLECT --> ARCHIVE

    style Context fill:#4da6ff,stroke:#0066cc,color:white
    style Rules fill:#ffa64d,stroke:#cc7a30,color:white
    style FileIO fill:#4dbb5f,stroke:#36873f,color:white
    style Transition fill:#d94dbb,stroke:#a3378a,color:white
```

## 📈 自適應複雜度模型

```mermaid
graph TD
    Task["任務建立"] --> Complexity{"複雜度<br>等級？"}

    Complexity -->|"等級 1<br>快速修補"| L1["三階段<br>精簡流程"]
    Complexity -->|"等級 2<br>增強"| L2["四階段<br>平衡流程"]
    Complexity -->|"等級 3<br>功能"| L3["五階段<br>完整流程"]
    Complexity -->|"等級 4<br>企業級"| L4["六階段<br>治理流程"]

    L1 --> L1_Process["VAN → IMPLEMENT → REFLECT"]
    L2 --> L2_Process["VAN → PLAN → IMPLEMENT → REFLECT"]
    L3 --> L3_Process["VAN → PLAN → CREATIVE → IMPLEMENT → REFLECT"]
    L4 --> L4_Process["VAN → PLAN → CREATIVE → IMPLEMENT → REFLECT → ARCHIVE"]

    style Complexity fill:#d94dbb,stroke:#a3378a,color:white
    style L1 fill:#4dbb5f,stroke:#36873f,color:white
    style L2 fill:#ffa64d,stroke:#cc7a30,color:white
    style L3 fill:#4da6ff,stroke:#0066cc,color:white
    style L4 fill:#ff5555,stroke:#cc0000,color:white
```

## 🧠 階層式規則載入

規則以階層式載入以最佳化情境使用：

```mermaid
graph TD
    Root["記憶體庫<br>通用規則"] --> Core["核心規則<br>各模式共用"]

    Core --> L1["等級 1<br>規則"]
    Core --> L2["等級 2<br>規則"]
    Core --> L3["等級 3<br>規則"]
    Core --> L4["等級 4<br>規則"]

    Core --> VM["模式<br>視覺地圖"]

    Core --> Phase["階段專屬<br>規則"]

    Phase --> VAN_Rules["VAN 模式<br>規則"]
    Phase --> PLAN_Rules["PLAN 模式<br>規則"]
    Phase --> CREATIVE_Rules["CREATIVE 模式<br>規則"]
    Phase --> IMPLEMENT_Rules["IMPLEMENT 模式<br>規則"]
    Phase --> REFLECT_Rules["REFLECT 模式<br>規則"]
    Phase --> ARCHIVE_Rules["ARCHIVE 模式<br>規則"]

    style Root fill:#4da6ff,stroke:#0066cc,color:white
    style Core fill:#ffa64d,stroke:#cc7a30,color:white
    style Phase fill:#4dbb5f,stroke:#36873f,color:white
```

## 🔄 位元組最佳化創意階段

創意階段文件以漸進方式產生：

```mermaid
graph TD
    Start["創意階段<br>啟動"] --> P1["1️⃣ 問題<br>定義範圍"]
    P1 --> P2["2️⃣ 選項<br>列舉替代方案"]
    P2 --> P3["3️⃣ 分析<br>比較選項"]
    P3 --> P4["4️⃣ 決策<br>選擇方案"]
    P4 --> P5["5️⃣ 指引<br>記錄實作"]

    P3 -.->|"隨需"| Details["詳細選項<br>分析"]

    style Start fill:#d971ff,stroke:#a33bc2,color:white
    style P1 fill:#4da6ff,stroke:#0066cc,color:white
    style P2 fill:#ffa64d,stroke:#cc7a30,color:white
    style P3 fill:#4dbb5f,stroke:#36873f,color:white
    style P4 fill:#d94dbb,stroke:#a3378a,color:white
    style P5 fill:#4dbbbb,stroke:#368787,color:white
    style Details fill:#e699d9,stroke:#d94dbb,color:white,stroke-dasharray: 5 5
```

## 🔀 最佳化模式轉換

模式轉換採用統一情境轉移協定：

```mermaid
sequenceDiagram
    participant Current as 當前模式
    participant Context as 情境管理器
    participant Next as 下一模式

    Current->>Context: 建立轉換文件
    Current->>Context: 儲存關鍵情境
    Context->>Context: 準備規則快取
    Current->>Next: 啟動轉換
    Next->>Context: 驗證情境可用性
    Context->>Next: 載入相關情境
    Context->>Next: 載入快取規則
    Next->>Next: 保留情境繼續執行
```

## 📊 記憶體庫高效更新

```mermaid
graph TD
    subgraph "記憶體庫檔案"
        tasks["tasks.md<br>真實來源"]
        active["activeContext.md<br>目前焦點"]
        creative["creative-*.md<br>設計決策"]
        progress["progress.md<br>實作狀態"]
        transition["transition.md<br>模式轉換"]
    end

    Update["更新請求"] --> Diff{"有變更？"}
    Diff -->|"否"| Skip["略過更新"]
    Diff -->|"是"| Section{"區段<br>變更？"}
    Section -->|"是"| Partial["僅更新<br>變更區段"]
    Section -->|"否"| Full["完整檔案<br>更新"]

    Partial --> tasks
    Full --> tasks

    style Update fill:#4da6ff,stroke:#0066cc,color:white
    style Diff fill:#ffa64d,stroke:#cc7a30,color:white
    style Section fill:#4dbb5f,stroke:#36873f,color:white
    style Partial fill:#d94dbb,stroke:#a3378a,color:white
    style Full fill:#4dbbbb,stroke:#368787,color:white
```

## 💻 依複雜度調整文件

文件需求依複雜度等級調整：

| 文件內容 | 等級 1 | 等級 2 | 等級 3 | 等級 4 |
| -------- | ------ | ------ | ------ | ------ |
| 問題定義 | 簡要   | 標準   | 詳細   | 全面   |
| 選項分析 | 可選   | 基本   | 多選項 | 詳盡   |
| 實作計畫 | 簡單   | 標準   | 詳細   | 分階段 |
| 測試需求 | 基本   | 標準   | 完整   | 嚴謹   |
| 文件化   | 最少   | 標準   | 詳細   | 全面   |

## 📑 各等級最佳化範本

### 等級 1：快速修補範本

```markdown
## 快速修補：[問題名稱]

- 問題： [簡要描述]
- 解決方案： [實作方式]
- 驗證： [如何測試修補]
```

### 等級 2：增強範本

```markdown
## 增強：[功能名稱]

- 需求： [需完成事項]
- 方法： [實作方式]
- 測試： [驗證方式]
- 文件化： [文件位置]
```

### 等級 3-4：完整範本

採用最佳化創意階段範本，並依複雜度調整文件深度

## 🔄 參考地圖

各模式視覺流程圖皆已最佳化位元組效率：

- @VAN 模式地圖（最佳化）
- @PLAN 模式地圖（最佳化）
- @CREATIVE 模式地圖（最佳化）
- @IMPLEMENT 模式地圖（最佳化）
- @REFLECT 模式地圖（最佳化）
- @ARCHIVE 模式地圖（最佳化）

## ⚡ 位元組效率提升

本版本最佳化重點：

1. 階層式規則載入（減少 65% 位元組）
2. 創意階段漸進式文件（減少 60% 位元組）
3. 模式轉換時情境保留（減少 40% 位元組）
4. 記憶體庫差異化更新（減少 30% 位元組）
5. 依複雜度調整範本（依等級變動）

## 💡 使用指引

使用最佳化系統請依下列步驟：

1. 以 VAN 指令初始化並判斷複雜度
2. 依複雜度流程執行
3. 依任務複雜度採用漸進式文件
4. 讓系統自動管理規則載入與情境保留
5. 享受最佳化位元組效率並維持結構化開發
