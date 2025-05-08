---
description: ARCHIVE 模式視覺化流程圖（任務文件化）
globs: "**/archive*/**", "**/document*/**", "**/complete*/**"
alwaysApply: false
---

# ARCHIVE 模式：任務文件化流程圖

> **重點摘要：** 本視覺化地圖引導 ARCHIVE 模式流程，聚焦於建立完整的任務文件、歸檔相關檔案，並更新記憶體庫以供未來參考。

## 🧭 ARCHIVE 模式流程

```mermaid
graph TD
    Start["啟動 ARCHIVE 模式"] --> ReadTasks["讀取 tasks.md<br>reflection.md 及<br>progress.md"]

    %% 初步評估
    ReadTasks --> VerifyReflect{"回顧<br>完成？"}
    VerifyReflect -->|"否"| ReturnReflect["返回<br>REFLECT 模式"]
    VerifyReflect -->|"是"| AssessLevel{"判斷<br>複雜度等級"}

    %% 依等級歸檔
    AssessLevel -->|"等級 1"| L1Archive["等級 1 歸檔<br>Level1/archive-minimal.md"]
    AssessLevel -->|"等級 2"| L2Archive["等級 2 歸檔<br>Level2/archive-basic.md"]
    AssessLevel -->|"等級 3"| L3Archive["等級 3 歸檔<br>Level3/archive-standard.md"]
    AssessLevel -->|"等級 4"| L4Archive["等級 4 歸檔<br>Level4/archive-comprehensive.md"]

    %% 等級 1 歸檔（最小）
    L1Archive --> L1Summary["建立快速<br>摘要"]
    L1Summary --> L1Task["更新<br>tasks.md"]
    L1Task --> L1Complete["標記任務<br>完成"]

    %% 等級 2 歸檔（基本）
    L2Archive --> L2Summary["建立基本<br>歸檔文件"]
    L2Summary --> L2Doc["記錄<br>變更"]
    L2Doc --> L2Task["更新<br>tasks.md"]
    L2Task --> L2Progress["更新<br>progress.md"]
    L2Progress --> L2Complete["標記任務<br>完成"]

    %% 等級 3-4 歸檔（全面）
    L3Archive & L4Archive --> L34Summary["建立全面<br>歸檔文件"]
    L34Summary --> L34Doc["記錄<br>實作"]
    L34Doc --> L34Creative["歸檔創意<br>階段文件"]
    L34Creative --> L34Code["記錄程式碼<br>變更"]
    L34Code --> L34Test["記錄<br>測試"]
    L34Test --> L34Lessons["總結<br>經驗教訓"]
    L34Lessons --> L34Task["更新<br>tasks.md"]
    L34Task --> L34Progress["更新<br>progress.md"]
    L34Progress --> L34System["更新系統<br>文件"]
    L34System --> L34Complete["標記任務<br>完成"]

    %% 完成
    L1Complete & L2Complete & L34Complete --> CreateArchive["建立歸檔<br>文件於<br>docs/archive/"]
    CreateArchive --> UpdateActive["更新<br>activeContext.md"]
    UpdateActive --> Reset["重設以<br>進行下個任務"]
```

## 📋 歸檔文件結構

歸檔文件應遵循以下結構：

```mermaid
graph TD
    subgraph "歸檔文件結構"
        Header["# 任務歸檔：[任務名稱]"]
        Meta["## Metadata<br>任務資訊、日期、複雜度"]
        Summary["## 摘要<br>任務簡要說明"]
        Requirements["## 需求<br>任務需達成內容"]
        Implementation["## 實作<br>如何完成任務"]
        Testing["## 測試<br>驗證方式"]
        Lessons["## 經驗教訓<br>重點收穫"]
        Refs["## 參考資料<br>相關文件連結"]
    end

    Header --> Meta --> Summary --> Requirements --> Implementation --> Testing --> Lessons --> Refs
```

## 📊 必要檔案狀態驗證

開始歸檔前，請驗證檔案狀態：

```mermaid
graph TD
    Start["檔案狀態<br>驗證"] --> CheckTasks{"tasks.md 是否<br>標記回顧完成？"}

    CheckTasks -->|"否"| ErrorReflect["錯誤：<br>返回 REFLECT 模式"]
    CheckTasks -->|"是"| CheckReflection{"reflection.md<br>存在？"}

    CheckReflection -->|"否"| ErrorCreate["錯誤：<br>請先建立 reflection.md"]
    CheckReflection -->|"是"| CheckProgress{"progress.md<br>已更新？"}

    CheckProgress -->|"否"| ErrorProgress["錯誤：<br>請先更新 progress.md"]
    CheckProgress -->|"是"| ReadyArchive["可進行<br>歸檔"]
```

## 🔍 依複雜度歸檔類型

```mermaid
graph TD
    subgraph "等級 1：最小歸檔"
        L1A["基本錯誤<br>描述"]
        L1B["解決方案<br>摘要"]
        L1C["受影響<br>檔案"]
    end

    subgraph "等級 2：基本歸檔"
        L2A["增強內容<br>描述"]
        L2B["實作<br>摘要"]
        L2C["測試<br>結果"]
        L2D["經驗<br>教訓"]
    end

    subgraph "等級 3-4：全面歸檔"
        L3A["詳細<br>需求"]
        L3B["架構/<br>設計決策"]
        L3C["實作<br>細節"]
        L3D["測試<br>策略"]
        L3E["效能<br>考量"]
        L3F["未來<br>增強"]
        L3G["跨系統<br>參照"]
    end

    L1A --> L1B --> L1C

    L2A --> L2B --> L2C --> L2D

    L3A --> L3B --> L3C --> L3D --> L3E --> L3F --> L3G
```

## 📝 歸檔文件範本

### 等級 1（最小）歸檔

```
# 錯誤修復歸檔：[錯誤名稱]

## 日期
[修復日期]

## 摘要
[錯誤與解決方案簡述]

## 實作
[修正內容說明]

## 變更檔案
- [檔案 1]
- [檔案 2]
```

### 等級 2-4（全面）歸檔

```
# 任務歸檔：[任務名稱]

## Metadata
- **複雜度**：等級 [2/3/4]
- **類型**：[增強/功能/系統]
- **完成日期**：[日期]
- **相關任務**：[相關任務參照]

## 摘要
[任務完整摘要]

## 需求
- [需求 1]
- [需求 2]
- [需求 3]

## 實作
### 方法
[實作方法說明]

### 主要元件
- [元件 1]：[說明]
- [元件 2]：[說明]

### 變更檔案
- [檔案 1]：[變更說明]
- [檔案 2]：[變更說明]

## 測試
- [測試 1]：[結果]
- [測試 2]：[結果]

## 經驗教訓
- [經驗 1]
- [經驗 2]
- [經驗 3]

## 未來考量
- [未來增強 1]
- [未來增強 2]

## 參考資料
- [reflection 文件連結]
- [創意階段文件連結]
- [其他相關參照]
```

## 📋 歸檔位置與命名

歸檔文件應依下列結構組織：

```mermaid
graph TD
    subgraph "歸檔結構"
        Root["docs/archive/"]
        Tasks["tasks/"]
        Features["features/"]
        Systems["systems/"]

        Root --> Tasks
        Root --> Features
        Root --> Systems

        Tasks --> Bug["bug-fix-name-YYYYMMDD.md"]
        Tasks --> Enhancement["enhancement-name-YYYYMMDD.md"]
        Features --> Feature["feature-name-YYYYMMDD.md"]
        Systems --> System["system-name-YYYYMMDD.md"]
    end
```

## 📊 TASKS.MD 最終更新

歸檔完成時，請於 tasks.md 更新：

```
## 狀態
- [x] 初始化完成
- [x] 規劃完成
[等級 3-4:]
- [x] 創意階段完成
- [x] 實作完成
- [x] 回顧完成
- [x] 歸檔完成

## 歸檔
- **日期**：[完成日期]
- **歸檔文件**：[歸檔文件連結]
- **狀態**：COMPLETED
```

## 📋 歸檔驗證清單

```
✓ 歸檔驗證
- 已檢閱回顧文件？ [是/否]
- 歸檔文件已建立且內容完整？ [是/否]
- 歸檔文件已放置正確位置？ [是/否]
- tasks.md 已標記完成？ [是/否]
- progress.md 已更新歸檔參照？ [是/否]
- activeContext.md 已更新下個任務？ [是/否]
- 創意階段文件已歸檔（等級 3-4）？ [是/否/不適用]

→ 全部為是：歸檔完成，記憶體庫可進行下個任務
→ 任一為否：請補齊缺漏歸檔內容
```

## 🔄 任務完成通知

歸檔完成時，請通知使用者：

```
## 任務已歸檔

✅ 歸檔文件已建立於 docs/archive/
✅ 所有任務文件已保存
✅ 記憶體庫已更新參照
✅ 任務已標記為 COMPLETED

→ 記憶體庫已可進行下個任務
→ 開始新任務請使用 VAN 模式
```
