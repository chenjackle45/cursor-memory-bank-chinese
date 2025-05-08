---
description: BUILD 模式視覺化流程圖（程式碼執行）
globs: implementation-mode-map.md
alwaysApply: false
---

# BUILD 模式：程式碼執行流程圖

> **重點摘要：** 本視覺化地圖引導 BUILD 模式流程，聚焦於根據規劃與創意階段高效執行程式碼，並正確執行指令與追蹤進度。

## 🧭 BUILD 模式流程

```mermaid
graph TD
    Start["啟動 BUILD 模式"] --> ReadDocs["讀取參考文件<br>Core/command-execution.md"]

    %% 初始化
    ReadDocs --> CheckLevel{"從 tasks.md<br>判斷複雜度等級"}

    %% 等級 1 實作
    CheckLevel -->|"等級 1<br>快速錯誤修復"| L1Process["等級 1 流程<br>Level1/quick-bug-workflow.md"]
    L1Process --> L1Review["檢查錯誤<br>報告"]
    L1Review --> L1Examine["檢查<br>相關程式碼"]
    L1Examine --> L1Fix["執行<br>目標修復"]
    L1Fix --> L1Test["測試<br>修復"]
    L1Test --> L1Update["更新<br>tasks.md"]

    %% 等級 2 實作
    CheckLevel -->|"等級 2<br>簡單增強"| L2Process["等級 2 流程<br>Level2/enhancement-workflow.md"]
    L2Process --> L2Review["檢查建構<br>規劃"]
    L2Review --> L2Examine["檢查相關<br>程式碼區塊"]
    L2Examine --> L2Implement["依序實作<br>變更"]
    L2Implement --> L2Test["測試<br>變更"]
    L2Test --> L2Update["更新<br>tasks.md"]

    %% 等級 3-4 實作
    CheckLevel -->|"等級 3-4<br>功能/系統"| L34Process["等級 3-4 流程<br>Level3/feature-workflow.md<br>Level4/system-workflow.md"]
    L34Process --> L34Review["檢查規劃與<br>創意決策"]
    L34Review --> L34Phase{"創意階段<br>文件完成？"}

    L34Phase -->|"否"| L34Error["錯誤：<br>返回 CREATIVE 模式"]
    L34Phase -->|"是"| L34DirSetup["建立目錄<br>結構"]
    L34DirSetup --> L34VerifyDirs["驗證目錄<br>建立成功"]
    L34VerifyDirs --> L34Implementation["建構<br>階段"]

    %% 實作階段
    L34Implementation --> L34Phase1["階段 1<br>建構"]
    L34Phase1 --> L34VerifyFiles["驗證檔案<br>建立成功"]
    L34VerifyFiles --> L34Test1["測試<br>階段 1"]
    L34Test1 --> L34Document1["記錄<br>階段 1"]
    L34Document1 --> L34Next1{"下一階段？"}
    L34Next1 -->|"是"| L34Implementation

    L34Next1 -->|"否"| L34Integration["整合<br>測試"]
    L34Integration --> L34Document["記錄<br>整合點"]
    L34Document --> L34Update["更新<br>tasks.md"]

    %% 指令執行
    L1Fix & L2Implement & L34Phase1 --> CommandExec["指令執行<br>Core/command-execution.md"]
    CommandExec --> DocCommands["記錄指令<br>與結果"]

    %% 完成與切換
    L1Update & L2Update & L34Update --> VerifyComplete["驗證建構<br>完成"]
    VerifyComplete --> UpdateProgress["更新 progress.md<br>狀態"]
    UpdateProgress --> Transition["下一模式：<br>REFLECT 模式"]
```

## 📋 必要檔案狀態驗證

開始實作前，請驗證檔案狀態：

```mermaid
graph TD
    Start["檔案狀態<br>驗證"] --> CheckTasks{"tasks.md 是否<br>規劃完成？"}

    CheckTasks -->|"否"| ErrorPlan["錯誤：<br>返回 PLAN 模式"]
    CheckTasks -->|"是"| CheckLevel{"任務<br>複雜度？"}

    CheckLevel -->|"等級 1"| L1Ready["可進行<br>實作"]

    CheckLevel -->|"等級 2"| L2Ready["可進行<br>實作"]

    CheckLevel -->|"等級 3-4"| CheckCreative{"需創意階段？"}

    CheckCreative -->|"否"| L34Ready["可進行<br>實作"]
    CheckCreative -->|"是"| VerifyCreative{"創意階段<br>已完成？"}

    VerifyCreative -->|"否"| ErrorCreative["錯誤：<br>返回 CREATIVE 模式"]
    VerifyCreative -->|"是"| L34Ready
```

## 🔄 檔案系統驗證流程

```mermaid
graph TD
    Start["開始檔案<br>驗證"] --> CheckDir["檢查目錄<br>結構"]
    CheckDir --> DirResult{"目錄<br>存在？"}

    DirResult -->|"否"| ErrorDir["❌ 錯誤：<br>缺少目錄"]
    DirResult -->|"是"| CheckFiles["檢查每個<br>建立檔案"]

    ErrorDir --> FixDir["修正目錄<br>結構"]
    FixDir --> CheckDir

    CheckFiles --> FileResult{"所有檔案<br>存在？"}
    FileResult -->|"否"| ErrorFile["❌ 錯誤：<br>缺少/路徑錯誤檔案"]
    FileResult -->|"是"| Complete["✅ 驗證<br>完成"]

    ErrorFile --> FixFile["修正檔案路徑<br>或重建檔案"]
    FixFile --> CheckFiles
```

## 📋 目錄驗證步驟

建立任何檔案前：

```
✓ 目錄驗證程序
1. 所有目錄必須先於檔案建立前建立
2. 使用絕對路徑：/full/path/to/directory
3. 建立後驗證每個目錄：
   ls -la /full/path/to/directory     # Linux/Mac
   dir "C:\full\path\to\directory"    # Windows
4. 於 progress.md 記錄目錄結構
5. 僅於所有目錄驗證存在後才可建立檔案
```

## 📋 檔案建立驗證

建立檔案後：

```
✓ 檔案驗證程序
1. 所有檔案操作皆用絕對路徑：/full/path/to/file.ext
2. 驗證每個檔案建立成功：
   ls -la /full/path/to/file.ext     # Linux/Mac
   dir "C:\full\path\to\file.ext"    # Windows
3. 若驗證失敗：
   a. 檢查路徑解析問題
   b. 驗證目錄存在
   c. 嘗試用正確路徑重建
   d. 修正後再次驗證檔案存在
4. 於 progress.md 記錄所有檔案路徑
```

## 🔄 指令執行流程

```mermaid
graph TD
    Start["指令<br>執行"] --> Analyze["分析指令<br>需求"]
    Analyze --> Complexity{"指令<br>複雜度？"}

    Complexity -->|"簡單"| Simple["執行<br>單一指令"]
    Complexity -->|"中等"| Chain["有效<br>指令串接"]
    Complexity -->|"複雜"| Break["拆解為<br>邏輯步驟"]

    Simple & Chain & Break --> Verify["驗證<br>結果"]
    Verify --> Document["記錄<br>指令與結果"]
    Document --> Next["下一個<br>指令"]
```

## 📋 等級專屬建構方式

```mermaid
graph TD
    subgraph "等級 1：快速錯誤修復"
        L1A["目標程式碼<br>檢查"]
        L1B["最小<br>變更範圍"]
        L1C["直接<br>修復"]
        L1D["驗證<br>修復"]
    end

    subgraph "等級 2：增強"
        L2A["依序<br>建構"]
        L2B["變更範圍<br>受控"]
        L2C["標準<br>測試"]
        L2D["元件<br>文件"]
    end

    subgraph "等級 3-4：功能/系統"
        L3A["先建立<br>目錄結構"]
        L3B["檔案前先驗證目錄"]
        L3C["分階段<br>建構"]
        L3D["建立後驗證檔案"]
        L3E["整合<br>測試"]
        L3F["詳細<br>文件"]
    end

    L1A --> L1B --> L1C --> L1D
    L2A --> L2B --> L2C --> L2D
    L3A --> L3B --> L3C --> L3D --> L3E --> L3F
```

## 📝 BUILD 文件格式

建構過程請記錄：

```
## Build: [元件/功能]

### 方法
[建構方法簡述]

### 目錄結構
- [/absolute/path/to/dir1/]: [用途]
- [/absolute/path/to/dir2/]: [用途]

### 程式碼變更
- [/absolute/path/to/file1.ext]: [變更說明]
- [/absolute/path/to/file2.ext]: [變更說明]

### 驗證步驟
- [✓] 目錄結構已建立並驗證
- [✓] 所有檔案已建立於正確位置
- [✓] 檔案內容已驗證

### 執行指令
```

[指令 1]
[結果]

```

```

[指令 2]
[結果]

```

### 測試
- [測試 1]：[結果]
- [測試 2]：[結果]

### 狀態
- [x] 建構完成
- [x] 已執行測試
- [x] 檔案驗證完成
- [ ] 文件已更新
```

## 📊 TASKS.MD 更新格式

建構過程中，請於 tasks.md 記錄進度：

```
## 狀態
- [x] 初始化完成
- [x] 規劃完成
[等級 3-4:]
- [x] 創意階段完成
- [x] 目錄結構已建立並驗證
- [x] [已建構元件 1]
- [x] [已建構元件 2]
- [ ] [剩餘元件]

## 建構進度
- [元件 1]：完成
  - 檔案：[/absolute/path/to/files]
  - [實作細節]
- [元件 2]：完成
  - 檔案：[/absolute/path/to/files]
  - [實作細節]
- [元件 3]：進行中
  - [目前狀態]
```

## 📋 PROGRESS.MD 更新格式

請於 progress.md 記錄：

```
# 建構進度

## 目錄結構
- [/absolute/path/to/dir1/]: 已建立並驗證
- [/absolute/path/to/dir2/]: 已建立並驗證

## [日期]：[元件/功能] 已建構
- **建立檔案**：
  - [/absolute/path/to/file1.ext]：已驗證
  - [/absolute/path/to/file2.ext]：已驗證
- **主要變更**：
  - [變更 1]
  - [變更 2]
- **測試**：[測試結果]
- **下一步**：[後續工作]
```

## 📊 BUILD 驗證清單

```
✓ BUILD 驗證
- 目錄結構正確建立？ [是/否]
- 所有檔案皆於正確位置？ [是/否]
- 所有檔案路徑皆為絕對路徑？ [是/否]
- 所有規劃變更皆已實作？ [是/否]
- 所有變更皆已測試？ [是/否]
- 程式碼符合專案標準？ [是/否]
- 邊界情境皆有處理？ [是/否]
- 建構文件皆用絕對路徑？ [是/否]
- tasks.md 已更新進度？ [是/否]
- progress.md 已更新細節？ [是/否]

→ 全部為是：建構完成，可進入 REFLECT 模式
→ 任一為否：請補齊缺漏建構內容
```

## 🔄 模式切換通知

建構完成時，請通知使用者：

```
## 建構完成

✅ 目錄結構已驗證
✅ 所有檔案皆於正確位置
✅ 所有規劃變更皆已實作
✅ 測試皆已成功執行
✅ tasks.md 已更新狀態
✅ progress.md 已更新細節

→ 下一推薦模式：REFLECT 模式
```
