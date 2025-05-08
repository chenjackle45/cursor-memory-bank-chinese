---
description: Hierarchical rule loading system for optimized token usage
globs: "**/rule-loading*/**", "**/optimization*/**"
alwaysApply: false
---

# 階層式規則載入系統

> **重點摘要：** 本規則實作最佳化載入系統，僅根據情境、複雜度等級與當前階段載入必要規則，以最大化位元組效率。

## 🧠 階層式規則結構

```mermaid
graph TD
    Root["根規則"] --> Core["核心規則<br>（永遠載入）"]
    Root --> Common["通用規則<br>（模式無關）"]
    Root --> Mode["模式專屬<br>規則"]
    Root --> Level["複雜度等級<br>規則"]

    Core --> Platform["平台<br>偵測"]
    Core --> File["檔案<br>操作"]
    Core --> Transition["模式<br>轉換"]

    Mode --> VAN["VAN 模式<br>規則"]
    Mode --> PLAN["PLAN 模式<br>規則"]
    Mode --> CREATIVE["CREATIVE 模式<br>規則"]
    Mode --> IMPLEMENT["IMPLEMENT 模式<br>規則"]
    Mode --> REFLECT["REFLECT 模式<br>規則"]

    Level --> Level1["等級 1<br>規則"]
    Level --> Level2["等級 2<br>規則"]
    Level --> Level3["等級 3<br>規則"]
    Level --> Level4["等級 4<br>規則"]

    style Root fill:#4da6ff,stroke:#0066cc,color:white
    style Core fill:#ffa64d,stroke:#cc7a30,color:white
    style Common fill:#4dbb5f,stroke:#36873f,color:white
    style Mode fill:#d94dbb,stroke:#a3378a,color:white
    style Level fill:#4dbbbb,stroke:#368787,color:white
```

## 📊 規則載入協定

```mermaid
sequenceDiagram
    participant User
    participant LoadManager
    participant RuleCache
    participant FileSystem

    User->>LoadManager: 請求模式啟動
    LoadManager->>RuleCache: 檢查核心規則快取
    RuleCache-->>LoadManager: 若有則回傳快取規則

    LoadManager->>FileSystem: 載入必要模式規則
    FileSystem-->>LoadManager: 回傳必要規則

    LoadManager->>LoadManager: 註冊專屬規則延遲載入器
    LoadManager->>User: 回傳已初始化模式

    User->>LoadManager: 請求專屬功能
    LoadManager->>RuleCache: 檢查專屬規則快取
    RuleCache-->>LoadManager: 若有則回傳快取規則

    alt 規則未在快取
        LoadManager->>FileSystem: 載入專屬規則
        FileSystem-->>LoadManager: 回傳專屬規則
        LoadManager->>RuleCache: 快取專屬規則
    end

    LoadManager->>User: 執行專屬功能
```

## 🔄 規則載入實作

```javascript
// Pseudocode for hierarchical rule loading
class RuleLoadManager {
  constructor() {
    this.cache = {
      core: {},
      common: {},
      mode: {},
      level: {},
    };
    this.lazyLoaders = {};
  }

  // Initialize a mode with only essential rules
  initializeMode(modeName, complexityLevel) {
    // Always load core rules
    this.loadCoreRules();

    // Load common rules
    this.loadCommonRules();

    // Load essential mode-specific rules
    this.loadEssentialModeRules(modeName);

    // Load complexity level rules
    this.loadComplexityRules(complexityLevel);

    // Register lazy loaders for specialized functionality
    this.registerLazyLoaders(modeName, complexityLevel);

    return {
      modeName,
      complexityLevel,
      status: "initialized",
    };
  }

  // Load only when specialized functionality is needed
  loadSpecializedRule(ruleType) {
    if (this.lazyLoaders[ruleType]) {
      if (!this.cache.specialized[ruleType]) {
        const rule = this.lazyLoaders[ruleType]();
        this.cache.specialized[ruleType] = rule;
      }
      return this.cache.specialized[ruleType];
    }
    return null;
  }

  // Register specialized rule loaders based on mode and complexity
  registerLazyLoaders(modeName, complexityLevel) {
    // Clear existing lazy loaders
    this.lazyLoaders = {};

    // Register mode-specific lazy loaders
    if (modeName === "CREATIVE") {
      this.lazyLoaders["architecture"] = () =>
        this.loadRule("creative-phase-architecture.md");
      this.lazyLoaders["algorithm"] = () =>
        this.loadRule("creative-phase-algorithm.md");
      this.lazyLoaders["uiux"] = () => this.loadRule("creative-phase-uiux.md");
    } else if (modeName === "IMPLEMENT") {
      this.lazyLoaders["testing"] = () =>
        this.loadRule("implementation-testing.md");
      this.lazyLoaders["deployment"] = () =>
        this.loadRule("implementation-deployment.md");
    }

    // Register complexity-specific lazy loaders
    if (complexityLevel >= 3) {
      this.lazyLoaders["comprehensive-planning"] = () =>
        this.loadRule("planning-comprehensive.md");
      this.lazyLoaders["advanced-verification"] = () =>
        this.loadRule("verification-advanced.md");
    }
  }
}
```

## 📋 規則相依地圖

```mermaid
graph TD
    Main["main.md"] --> Core1["platform-awareness.md"]
    Main --> Core2["file-verification.md"]
    Main --> Core3["command-execution.md"]

    subgraph "VAN 模式"
        VanMap["van-mode-map.md"] --> Van1["van-complexity-determination.md"]
        VanMap --> Van2["van-file-verification.md"]
        VanMap --> Van3["van-platform-detection.md"]
    end

    subgraph "PLAN 模式"
        PlanMap["plan-mode-map.md"] --> Plan1["task-tracking-basic.md"]
        PlanMap --> Plan2["planning-comprehensive.md"]
    end

    subgraph "CREATIVE 模式"
        CreativeMap["creative-mode-map.md"] --> Creative1["creative-phase-enforcement.md"]
        CreativeMap --> Creative2["creative-phase-metrics.md"]
        Creative1 & Creative2 -.-> CreativeSpecialized["專屬創意規則"]
        CreativeSpecialized --> CArch["creative-phase-architecture.md"]
        CreativeSpecialized --> CAlgo["creative-phase-algorithm.md"]
        CreativeSpecialized --> CUIUX["creative-phase-uiux.md"]
    end

    subgraph "IMPLEMENT 模式"
        ImplementMap["implement-mode-map.md"] --> Impl1["implementation-guide.md"]
        ImplementMap --> Impl2["testing-strategy.md"]
    end
```

## 🔍 模式專屬規則載入

### VAN 模式必要規則

```markdown
- main.md（核心）
- platform-awareness.md（核心）
- file-verification.md（核心）
- van-mode-map.md（模式）
```

### PLAN 模式必要規則

```markdown
- main.md（核心）
- plan-mode-map.md（模式）
- task-tracking-[complexity].mdc（等級）
```

### CREATIVE 模式必要規則

```markdown
- main.md（核心）
- creative-mode-map.md（模式）
- creative-phase-enforcement.md（模式）
```

### CREATIVE 模式專屬規則（延遲載入）

```markdown
- creative-phase-architecture.md（專屬）
- creative-phase-algorithm.md（專屬）
- creative-phase-uiux.md（專屬）
```

### IMPLEMENT 模式必要規則

```markdown
- main.md（核心）
- command-execution.md（核心）
- implement-mode-map.md（模式）
```

## 🚀 實作效益

階層式載入系統帶來：

1. **初始載入減少**：僅載入必要規則（約減少 70% 位元組）
2. **核心規則快取**：模式間共用規則快取
3. **專屬規則延遲載入**：僅於需要時載入專屬規則
4. **依複雜度載入**：僅載入符合任務複雜度的規則

## 📈 位元組用量比較

| 方式           | 初始位元組        | 專屬位元組      | 總位元組          |
| -------------- | ----------------- | --------------- | ----------------- |
| 原系統         | ~70,000           | 已含於初始      | ~70,000           |
| 階層式系統     | ~15,000           | ~10,000（隨需） | ~25,000           |
| **位元組減少** | **~55,000 (78%)** | **N/A**         | **~45,000 (64%)** |

## 🔄 使用範例

### 範例：創意階段搭配架構規則

```javascript
// Initialize the CREATIVE mode with only essential rules
const mode = ruleManager.initializeMode("CREATIVE", 3);

// Core and essential mode rules are loaded
// Architecture rules are NOT loaded yet

// Later, when architecture design is needed:
const architectureRule = ruleManager.loadSpecializedRule("architecture");

// Now the architecture rule is loaded and cached
```

## 🧪 規則載入驗證

為確保規則載入系統最佳運作：

```markdown
## 規則載入驗證

- 核心規則：[已載入]
- 模式必要規則：[已載入]
- 複雜度等級規則：[已載入]
- 專屬規則：[未載入]

目前位元組用量：[X] 位元組
潛在可節省位元組：[Y] 位元組
```

此階層式方法可確保最佳位元組用量，同時維持完整功能。
