---
description: Integration hub for Memory Bank optimizations
globs: "**/optimization*/**", "**/integration*/**"
alwaysApply: false
---

# 記憶體庫最佳化整合

> **重點摘要：** 本檔案作為所有記憶體庫最佳化的整合點，協調各最佳化元件無縫協作。

## 🔄 最佳化整合流程

```mermaid
graph TD
    Start["記憶體庫<br>初始化"] --> HRL["階層式<br>規則載入"]
    HRL --> ACM["自適應<br>複雜度模型"]
    ACM --> DCM["動態<br>情境管理"]
    DCM --> TMO["轉換<br>最佳化"]

    subgraph "層級專屬最佳化"
        L1["層級 1<br>最佳化"]
        L2["層級 2<br>最佳化"]
        L3["層級 3<br>最佳化"]
        L4["層級 4<br>最佳化"]
    end

    ACM --> L1 & L2 & L3 & L4

    L1 & L2 & L3 & L4 --> CPO["創意階段<br>最佳化"]

    CPO --> PDO["漸進式<br>文件化"]
    TMO --> PDO

    PDO --> MBO["記憶體庫<br>最佳化"]

    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style HRL fill:#ffa64d,stroke:#cc7a30,color:white
    style ACM fill:#4dbb5f,stroke:#36873f,color:white
    style DCM fill:#d94dbb,stroke:#a3378a,color:white
    style TMO fill:#4dbbbb,stroke:#368787,color:white
    style CPO fill:#e699d9,stroke:#d94dbb,color:white
    style PDO fill:#d971ff,stroke:#a33bc2,color:white
    style MBO fill:#ff71c2,stroke:#c23b8a,color:white
```

## 📋 最佳化元件註冊表

```javascript
// Optimization component registry pseudocode
const optimizationRegistry = {
  // Core optimizations
  hierarchicalRuleLoading: {
    file: "Core/hierarchical-rule-loading.md",
    dependencies: [],
    priority: 1,
  },
  adaptiveComplexityModel: {
    file: "main-optimized.md",
    dependencies: ["hierarchicalRuleLoading"],
    priority: 2,
  },
  modeTransitionOptimization: {
    file: "Core/mode-transition-optimization.md",
    dependencies: ["hierarchicalRuleLoading", "adaptiveComplexityModel"],
    priority: 3,
  },

  // Level-specific optimizations
  level1Optimization: {
    file: "Level1/optimized-workflow-level1.md",
    dependencies: ["adaptiveComplexityModel"],
    priority: 4,
  },

  // Feature-specific optimizations
  creativePhaseOptimization: {
    file: "Phases/CreativePhase/optimized-creative-template.md",
    dependencies: ["hierarchicalRuleLoading", "adaptiveComplexityModel"],
    priority: 5,
  },
};
```

## 🔄 最佳化初始化序列

```mermaid
sequenceDiagram
    participant MB as 記憶體庫
    participant Reg as 最佳化註冊表
    participant HRL as 階層式規則載入
    participant ACM as 自適應複雜度
    participant TMO as 轉換最佳化
    participant CPO as 創意階段最佳化

    MB->>Reg: 請求最佳化初始化
    Reg->>Reg: 依優先順序與相依性排序最佳化
    Reg->>HRL: 初始化（優先 1）
    HRL-->>Reg: 初始化完成
    Reg->>ACM: 初始化（優先 2）
    ACM->>HRL: 請求規則載入服務
    HRL-->>ACM: 提供規則載入
    ACM-->>Reg: 初始化完成
    Reg->>TMO: 初始化（優先 3）
    TMO->>HRL: 請求規則載入服務
    TMO->>ACM: 請求複雜度模型
    HRL-->>TMO: 提供規則載入
    ACM-->>TMO: 提供複雜度模型
    TMO-->>Reg: 初始化完成
    Reg->>CPO: 初始化（最終）
    CPO->>HRL: 請求規則載入服務
    CPO->>ACM: 請求複雜度模型
    CPO->>TMO: 請求轉換服務
    HRL-->>CPO: 提供規則載入
    ACM-->>CPO: 提供複雜度模型
    TMO-->>CPO: 提供轉換服務
    CPO-->>Reg: 初始化完成
    Reg-->>MB: 所有最佳化已初始化
```

## 🔍 最佳化設定

```javascript
// Optimization configuration pseudocode
const optimizationConfig = {
  // Token optimization settings
  tokenOptimization: {
    enableHierarchicalLoading: true,
    enableProgressiveDocumentation: true,
    enableLazyRuleLoading: true,
    enableContextPruning: true,
  },

  // Context preservation settings
  contextPreservation: {
    preserveDesignDecisions: true,
    preserveImplementationContext: true,
    preserveUserPreferences: true,
    contextCompressionLevel: "high", // none, low, medium, high
  },

  // Documentation optimization
  documentationOptimization: {
    level1DocumentationLevel: "minimal", // minimal, standard, comprehensive
    level2DocumentationLevel: "standard",
    level3DocumentationLevel: "comprehensive",
    level4DocumentationLevel: "comprehensive",
    enableProgressiveDisclosure: true,
    enableTemplateCaching: true,
  },
};
```

## 📊 最佳化監控

```mermaid
graph TD
    Monitor["最佳化<br>監控"] --> TokenUsage["位元組使用<br>追蹤"]
    Monitor --> ContextEfficiency["情境<br>效率"]
    Monitor --> RuleLoadingStats["規則載入<br>統計"]
    Monitor --> DocumentationSize["文件<br>大小"]

    TokenUsage --> Dashboard["最佳化<br>儀表板"]
    ContextEfficiency --> Dashboard
    RuleLoadingStats --> Dashboard
    DocumentationSize --> Dashboard

    Dashboard --> Feedback["最佳化<br>回饋迴路"]
    Feedback --> Config["最佳化<br>設定"]
    Config --> Monitor

    style Monitor fill:#4da6ff,stroke:#0066cc,color:white
    style Dashboard fill:#ffa64d,stroke:#cc7a30,color:white
    style Feedback fill:#4dbb5f,stroke:#36873f,color:white
    style Config fill:#d94dbb,stroke:#a3378a,color:white
```

## 📈 最佳化指標

```markdown
# Optimization Metrics

## Token Usage

- Core Rule Loading: [X] tokens
- Mode-Specific Rules: [Y] tokens
- Creative Phase Documentation: [Z] tokens
- Overall Token Reduction: [P]%

## Context Efficiency

- Context Utilization: [Q]%
- Context Waste: [R]%
- Effective Token Capacity: [S] tokens

## Rule Loading

- Rules Loaded: [T] / [U] (Total)
- Lazy-Loaded Rules: [V]
- Cached Rules: [W]

## Documentation

- Level 1 Documentation Size: [X] tokens
- Level 2 Documentation Size: [Y] tokens
- Level 3 Documentation Size: [Z] tokens
- Level 4 Documentation Size: [AA] tokens
```

## 🔄 整合使用範例

### 初始化所有最佳化

```javascript
// Pseudocode for initializing all optimizations
function initializeMemoryBankOptimizations() {
  // Load optimization registry
  const registry = loadOptimizationRegistry();

  // Sort by priority and dependencies
  const sortedOptimizations = sortOptimizations(registry);

  // Initialize each optimization in order
  for (const opt of sortedOptimizations) {
    initializeOptimization(opt);
  }

  // Configure optimization parameters
  configureOptimizations(loadOptimizationConfig());

  // Start monitoring
  initializeOptimizationMonitoring();

  return "Memory Bank optimizations initialized";
}
```

### 使用最佳化創意階段

```markdown
// Using the optimized creative phase with progressive documentation

// Initialize with minimal documentation
📌 CREATIVE PHASE START: Authentication System
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1️⃣ PROBLEM
Description: Design an authentication system for the application
Requirements: Secure, scalable, supports SSO, easy to maintain
Constraints: Must work with existing user database, <100ms response time

2️⃣ OPTIONS
Option A: JWT-based stateless auth
Option B: Session-based auth with Redis
Option C: OAuth2 implementation

// Progressively add detail as needed
3️⃣ ANALYSIS
| Criterion | JWT | Sessions | OAuth2 |
|-----------|-----|----------|--------|
| Security | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Scalability | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| Complexity | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |

// Focus on decision and implementation
4️⃣ DECISION
Selected: Option A: JWT-based auth with refresh tokens
Rationale: Best balance of performance and scalability

5️⃣ IMPLEMENTATION NOTES

- Use HS256 algorithm for token signing
- Implement short-lived access tokens (15min)
- Store token blacklist in Redis for revocation
```

## 🔄 模式轉換範例

```markdown
// Optimized mode transition from CREATIVE to IMPLEMENT

# MODE TRANSITION: CREATIVE → IMPLEMENT

## Context Summary

- Task: Authentication system implementation
- Complexity: Level 3
- Decision: JWT-based auth with refresh tokens

## Key Context

- Security requirements verified
- Algorithm selection: HS256
- Token lifecycle: 15min access / 7 days refresh

## Next Steps

1. Implement JWT generation module
2. Create token validation middleware
3. Build refresh token handling

// Transition happens with preserved context
// IMPLEMENT mode continues with this context available
```

## 🔄 階層式規則載入範例

```javascript
// Pseudocode example of hierarchical rule loading

// Initial load - only core rules
loadCoreRules();

// Determine complexity
const complexity = determineComplexity();

// Load mode-specific essential rules
loadModeEssentialRules("CREATIVE");

// Register lazy loaders for specialized rules
registerLazyLoader("architecture", () =>
  loadRule("creative-phase-architecture.md")
);
registerLazyLoader("algorithm", () => loadRule("creative-phase-algorithm.md"));
registerLazyLoader("uiux", () => loadRule("creative-phase-uiux.md"));

// Later, when architecture design is needed:
const architectureRule = loadSpecializedRule("architecture");
// Architecture rule is now loaded only when needed
```

這些整合式最佳化可無縫協作，為記憶體庫系統帶來顯著效率提升，同時維持完整功能。
