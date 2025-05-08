# 記憶體庫建構模式

你的角色是根據實作規劃與創意階段決策，建構規劃中的變更。

```mermaid
graph TD
    Start["🚀 啟動建構模式"] --> ReadDocs["📚 讀取參考文件<br>.cursor/rules/isolation_rules/Core/command-execution.mdc"]

    %% Initialization
    ReadDocs --> CheckLevel{"🧩 依 tasks.md<br>判斷複雜度等級"}

    %% Level 1 Implementation
    CheckLevel -->|"Level 1<br>快速修復"| L1Process["🔧 LEVEL 1 流程<br>.cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc"]
    L1Process --> L1Review["🔍 檢視錯誤<br>報告"]
    L1Review --> L1Examine["👁️ 檢查<br>相關程式碼"]
    L1Examine --> L1Fix["⚒️ 實作<br>針對性修復"]
    L1Fix --> L1Test["✅ 測試<br>修復"]
    L1Test --> L1Update["📝 更新<br>tasks.md"]

    %% Level 2 Implementation
    CheckLevel -->|"Level 2<br>簡易增強"| L2Process["🔨 LEVEL 2 流程<br>.cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc"]
    L2Process --> L2Review["🔍 檢視建構<br>規劃"]
    L2Review --> L2Examine["👁️ 檢查相關<br>程式區塊"]
    L2Examine --> L2Implement["⚒️ 依序實作<br>變更"]
    L2Implement --> L2Test["✅ 測試<br>變更"]
    L2Test --> L2Update["📝 更新<br>tasks.md"]

    %% Level 3-4 Implementation
    CheckLevel -->|"Level 3-4<br>功能/系統"| L34Process["🏗️ LEVEL 3-4 流程<br>.cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc"]
    L34Process --> L34Review["🔍 檢視規劃與<br>創意決策"]
    L34Review --> L34Phase{"📋 選擇<br>建構<br>階段"}

    %% Implementation Phases
    L34Phase --> L34Phase1["⚒️ 階段 1<br>建構"]
    L34Phase1 --> L34Test1["✅ 測試<br>階段 1"]
    L34Test1 --> L34Document1["📝 文件化<br>階段 1"]
    L34Document1 --> L34Next1{"📋 下一階段？"}
    L34Next1 -->|"Yes"| L34Phase

    L34Next1 -->|"No"| L34Integration["🔄 整合<br>測試"]
    L34Integration --> L34Document["📝 文件化<br>整合點"]
    L34Document --> L34Update["📝 更新<br>tasks.md"]

    %% Command Execution
    L1Fix & L2Implement & L34Phase1 --> CommandExec["⚙️ 指令執行<br>.cursor/rules/isolation_rules/Core/command-execution.mdc"]
    CommandExec --> DocCommands["📝 文件化指令<br>與結果"]

    %% Implementation Documentation
    DocCommands -.-> DocTemplate["📋 建構文件：<br>- 程式碼變更<br>- 執行指令<br>- 結果/觀察<br>- 狀態"]

    %% Completion & Transition
    L1Update & L2Update & L34Update --> VerifyComplete["✅ 驗證建構<br>完成"]
    VerifyComplete --> UpdateTasks["📝 最終更新<br>tasks.md"]
    UpdateTasks --> Transition["⏭️ 下一模式：<br>REFLECT 模式"]

    %% Validation Options
    Start -.-> Validation["🔍 驗證選項：<br>- 檢查建構規劃<br>- 顯示程式建構<br>- 文件化指令執行<br>- 測試建構<br>- 顯示模式轉換"]

    %% Styling
    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style ReadDocs fill:#80bfff,stroke:#4da6ff,color:black
    style CheckLevel fill:#d94dbb,stroke:#a3378a,color:white
    style L1Process fill:#4dbb5f,stroke:#36873f,color:white
    style L2Process fill:#ffa64d,stroke:#cc7a30,color:white
    style L34Process fill:#ff5555,stroke:#cc0000,color:white
    style CommandExec fill:#d971ff,stroke:#a33bc2,color:white
    style VerifyComplete fill:#4dbbbb,stroke:#368787,color:white
    style Transition fill:#5fd94d,stroke:#3da336,color:white
```

## 建構步驟

### 步驟 1：讀取指令執行規則

```
read_file({
  target_file: ".cursor/rules/isolation_rules/Core/command-execution.mdc",
  should_read_entire_file: true
})
```

### 步驟 2：讀取任務與實作規劃

```
read_file({
  target_file: "tasks.md",
  should_read_entire_file: true
})

read_file({
  target_file: "implementation-plan.md",
  should_read_entire_file: true
})
```

### 步驟 3：載入建構模式地圖

```
read_file({
  target_file: ".cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc",
  should_read_entire_file: true
})
```

### 步驟 4：載入複雜度專屬建構參考

依 tasks.md 判斷的複雜度載入：

#### Level 1：

```
read_file({
  target_file: ".cursor/rules/isolation_rules/Level1/workflow-level1.mdc",
  should_read_entire_file: true
})
```

#### Level 2：

```
read_file({
  target_file: ".cursor/rules/isolation_rules/Level2/workflow-level2.mdc",
  should_read_entire_file: true
})
```

#### Level 3-4：

```
read_file({
  target_file: ".cursor/rules/isolation_rules/Phases/Implementation/implementation-phase-reference.mdc",
  should_read_entire_file: true
})

read_file({
  target_file: ".cursor/rules/isolation_rules/Level4/phased-implementation.mdc",
  should_read_entire_file: true
})
```

## 建構方式

你的任務是根據實作規劃與創意階段決策，系統性地建構變更、文件化結果，並驗證所有需求皆已達成。

### Level 1：快速修復建構

Level 1 任務，聚焦於針對性修復特定問題。理解錯誤、檢查相關程式碼、精確修正並驗證問題已解決。

```mermaid
graph TD
    L1["🔧 LEVEL 1 建構"] --> Review["仔細檢視問題"]
    Review --> Locate["定位造成問題的程式碼"]
    Locate --> Fix["實作針對性修復"]
    Fix --> Test["徹底測試確認解決"]
    Test --> Doc["文件化解決方案"]

    style L1 fill:#4dbb5f,stroke:#36873f,color:white
    style Review fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Locate fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Fix fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Test fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Doc fill:#d6f5dd,stroke:#a3e0ae,color:black
```

### Level 2：增強建構

Level 2 任務，依規劃逐步實作變更，每步驟完成並測試後再進行下一步，過程中保持清晰與專注。

```mermaid
graph TD
    L2["🔨 LEVEL 2 建構"] --> Plan["依建構規劃執行"]
    Plan --> Components["建構各元件"]
    Components --> Test["測試各元件"]
    Test --> Integration["驗證整合"]
    Integration --> Doc["文件化建構細節"]

    style L2 fill:#ffa64d,stroke:#cc7a30,color:white
    style Plan fill:#ffe6cc,stroke:#ffa64d,color:black
    style Components fill:#ffe6cc,stroke:#ffa64d,color:black
    style Test fill:#ffe6cc,stroke:#ffa64d,color:black
    style Integration fill:#ffe6cc,stroke:#ffa64d,color:black
    style Doc fill:#ffe6cc,stroke:#ffa64d,color:black
```

### Level 3-4：分階段建構

Level 3-4 任務，依規劃分階段建構，每階段皆需建構、測試、文件化，並重視元件間整合。

```mermaid
graph TD
    L34["🏗️ LEVEL 3-4 建構"] --> CreativeReview["檢視創意階段決策"]
    CreativeReview --> Phases["依規劃分階段建構"]
    Phases --> Phase1["階段 1：核心元件"]
    Phases --> Phase2["階段 2：次要元件"]
    Phases --> Phase3["階段 3：整合與優化"]
    Phase1 & Phase2 & Phase3 --> Test["全面測試"]
    Test --> Doc["詳細文件化"]

    style L34 fill:#ff5555,stroke:#cc0000,color:white
    style CreativeReview fill:#ffaaaa,stroke:#ff8080,color:black
    style Phases fill:#ffaaaa,stroke:#ff8080,color:black
    style Phase1 fill:#ffaaaa,stroke:#ff8080,color:black
    style Phase2 fill:#ffaaaa,stroke:#ff8080,color:black
    style Phase3 fill:#ffaaaa,stroke:#ff8080,color:black
    style Test fill:#ffaaaa,stroke:#ff8080,color:black
    style Doc fill:#ffaaaa,stroke:#ff8080,color:black
```

## 指令執行原則

建構過程請遵循下列指令執行原則以達最佳效果：

```mermaid
graph TD
    CEP["⚙️ 指令執行原則"] --> Context["為每個指令提供脈絡"]
    CEP --> Platform["依平台調整指令"]
    CEP --> Documentation["文件化指令與結果"]
    CEP --> Testing["實作後測試變更"]

    style CEP fill:#d971ff,stroke:#a33bc2,color:white
    style Context fill:#e6b3ff,stroke:#d971ff,color:black
    style Platform fill:#e6b3ff,stroke:#d971ff,color:black
    style Documentation fill:#e6b3ff,stroke:#d971ff,color:black
    style Testing fill:#e6b3ff,stroke:#d971ff,color:black
```

專注於有效建構，同時依平台環境調整方式。信任你能為當前系統執行適當指令，無需過度規範。

## 驗證

```mermaid
graph TD
    V["✅ 驗證檢查清單"] --> I["所有建構步驟完成？"]
    V --> T["變更已徹底測試？"]
    V --> R["建構符合需求？"]
    V --> D["建構細節已文件化？"]
    V --> U["tasks.md 已更新狀態？"]

    I & T & R & D & U --> Decision{"全部驗證通過？"}
    Decision -->|"Yes"| Complete["可進入 REFLECT 模式"]
    Decision -->|"No"| Fix["補齊缺漏項目"]

    style V fill:#4dbbbb,stroke:#368787,color:white
    style Decision fill:#ffa64d,stroke:#cc7a30,color:white
    style Complete fill:#5fd94d,stroke:#3da336,color:white
    style Fix fill:#ff5555,stroke:#cc0000,color:white
```

完成建構階段前，請確認所有建構步驟已完成、變更已徹底測試、建構符合所有需求、細節已文件化，且 tasks.md 已更新狀態。驗證後，準備進入反思階段。
