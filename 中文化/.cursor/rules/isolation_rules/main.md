---
description: main rule
globs: main.md
alwaysApply: false
---

# 🔍 隔離導向記憶體庫系統

🚨 關鍵規則：必須建立記憶體庫 🚨
記憶體庫必須在任何模式下的任何操作前建立
未驗證記憶體庫存在時，任何流程皆不得繼續

> **重點摘要：** 本系統設計用於 Cursor 自訂模式，每個模式僅載入所需規則。系統利用 Mermaid 視覺圖與選擇性文件載入，最佳化情境使用。

## 🧭 模式專屬視覺地圖

```mermaid
graph TD
    subgraph Modes["Cursor 自訂模式"]
        VAN["VAN 模式<br>初始化"] --> PLAN["PLAN 模式<br>任務規劃"]
        PLAN --> Creative["CREATIVE 模式<br>設計決策"]
        Creative --> Implement["IMPLEMENT 模式<br>程式碼實作"]
        Implement --> Reflect["REFLECT 模式<br>任務回顧"]
        Reflect --> Archive["ARCHIVE 模式<br>文件化"]
    end

    VAN -.->|"載入"| VANRules["• main.md<br>• platform-awareness.md<br>• file-verification.md<br>• workflow-init.md"]
    PLAN -.->|"載入"| PLANRules["• main.md<br>• task-tracking.md<br>• planning-process.md"]
    Creative -.->|"載入"| CreativeRules["• main.md<br>• creative-phase.md<br>• design-patterns.md"]
    Implement -.->|"載入"| ImplementRules["• main.md<br>• command-execution.md<br>• implementation-guide.md"]
    Reflect -.->|"載入"| ReflectRules["• main.md<br>• reflection-format.md"]
    Archive -.->|"載入"| ArchiveRules["• main.md<br>• archiving-guide.md"]
```

## 📋 記憶體庫驗證－所有模式皆強制

```mermaid
graph TD
    Start["模式啟動"] --> CheckMemBank{"記憶體庫<br>存在？"}

    CheckMemBank -->|"否"| CreateMemBank["建立記憶體庫<br>[關鍵步驟]"]
    CheckMemBank -->|"是"| VerifyMemBank["驗證記憶體庫<br>結構"]

    CreateMemBank --> VerifyCreation{"建立<br>成功？"}
    VerifyCreation -->|"否"| AbortAll["⛔ 終止所有操作<br>請先修復記憶體庫"]
    VerifyCreation -->|"是"| VerifyMemBank

    VerifyMemBank --> StructureCheck{"結構<br>有效？"}
    StructureCheck -->|"否"| FixStructure["修復記憶體庫<br>結構"]
    StructureCheck -->|"是"| ContinueMode["繼續執行<br>模式操作"]

    FixStructure --> VerifyFix{"修復<br>成功？"}
    VerifyFix -->|"否"| AbortAll
    VerifyFix -->|"是"| ContinueMode

    style CheckMemBank fill:#ff0000,stroke:#990000,color:white,stroke-width:3px
    style CreateMemBank fill:#ff0000,stroke:#990000,color:white,stroke-width:3px
    style VerifyCreation fill:#ff0000,stroke:#990000,color:white,stroke-width:3px
    style AbortAll fill:#ff0000,stroke:#990000,color:white,stroke-width:3px
    style StructureCheck fill:#ff0000,stroke:#990000,color:white,stroke-width:3px
    style FixStructure fill:#ff5555,stroke:#dd3333,color:white
    style VerifyFix fill:#ff5555,stroke:#dd3333,color:white
```

## 📚 視覺流程圖

每個模式皆有專屬視覺流程圖：

- @VAN 模式地圖
- @PLAN 模式地圖
- @CREATIVE 模式地圖
- @IMPLEMENT 模式地圖
- @REFLECT 模式地圖
- @ARCHIVE 模式地圖

## 🔄 檔案狀態驗證

在此隔離導向架構下，記憶體庫檔案於各模式間維持連續性：

```mermaid
graph TD
    subgraph "記憶體庫檔案"
        tasks["tasks.md<br>真實來源"]
        active["activeContext.md<br>目前焦點"]
        creative["creative-*.md<br>設計決策"]
        progress["progress.md<br>實作狀態"]
    end

    VAN["VAN 模式"] -->|"建立/更新"| tasks
    VAN -->|"建立/更新"| active

    PLAN["PLAN 模式"] -->|"讀取"| tasks
    PLAN -->|"讀取"| active
    PLAN -->|"更新"| tasks

    Creative["CREATIVE 模式"] -->|"讀取"| tasks
    Creative -->|"建立"| creative
    Creative -->|"更新"| tasks

    Implement["IMPLEMENT 模式"] -->|"讀取"| tasks
    Implement -->|"讀取"| creative
    Implement -->|"更新"| tasks
    Implement -->|"更新"| progress

    Reflect["REFLECT 模式"] -->|"讀取"| tasks
    Reflect -->|"讀取"| progress
    Reflect -->|"更新"| tasks

    Archive["ARCHIVE 模式"] -->|"讀取"| tasks
    Archive -->|"讀取"| progress
    Archive -->|"封存"| creative
```

## 📋 模式轉換協定

```mermaid
sequenceDiagram
    participant User
    participant CurrentMode
    participant NextMode

    CurrentMode->>CurrentMode: 完成階段需求
    CurrentMode->>User: "階段完成。下一模式: [mode name]"
    User->>CurrentMode: 結束當前模式
    User->>NextMode: 啟動下一模式
    NextMode->>NextMode: 驗證所需檔案狀態

    alt 檔案狀態有效
        NextMode->>User: "已從前一模式繼續..."
    else 檔案狀態無效
        NextMode->>User: "所需檔案狀態不符"
        NextMode->>User: "請返回 [previous mode] 完成需求"
    end
```

## 💻 平台專屬指令

| 動作         | Windows            | Mac/Linux            |
| ------------ | ------------------ | -------------------- |
| 建立檔案     | `echo. > file.ext` | `touch file.ext`     |
| 建立目錄     | `mkdir directory`  | `mkdir -p directory` |
| 切換目錄     | `cd directory`     | `cd directory`       |
| 列出檔案     | `dir`              | `ls`                 |
| 顯示檔案內容 | `type file.ext`    | `cat file.ext`       |

## ⚠️ 指令效率指引

為獲得最佳效能，請於適當時機使用高效指令串接：

```
# 高效指令串接範例：
mkdir -p project/{src,tests,docs} && cd project
grep "TODO" $(find . -name "*.js")
npm install && npm start
```

詳細指引請參閱 [command-execution.md](mdc:.cursor/rules/isolation_rules/Core/command-execution.md)。
