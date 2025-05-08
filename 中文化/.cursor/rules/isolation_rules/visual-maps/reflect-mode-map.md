---
description: REFLECT 模式視覺化流程圖（任務回顧）
globs: "**/reflect*/**", "**/review*/**", "**/retrospect*/**"
alwaysApply: false
---

# REFLECT 模式：任務回顧流程圖

> **重點摘要：** 本視覺化地圖引導 REFLECT 模式流程，聚焦於結構化回顧實作、記錄經驗教訓，並為未來參考準備洞見。

## 🧭 REFLECT 模式流程

```mermaid
graph TD
    Start["啟動 REFLECT 模式"] --> ReadTasks["讀取 tasks.md<br>與 progress.md"]

    %% 初步評估
    ReadTasks --> VerifyImplement{"實作<br>完成？"}
    VerifyImplement -->|"否"| ReturnImplement["返回<br>IMPLEMENT 模式"]
    VerifyImplement -->|"是"| AssessLevel{"判斷<br>複雜度等級"}

    %% 依等級回顧
    AssessLevel -->|"等級 1"| L1Reflect["等級 1 回顧<br>Level1/reflection-basic.md"]
    AssessLevel -->|"等級 2"| L2Reflect["等級 2 回顧<br>Level2/reflection-standard.md"]
    AssessLevel -->|"等級 3"| L3Reflect["等級 3 回顧<br>Level3/reflection-comprehensive.md"]
    AssessLevel -->|"等級 4"| L4Reflect["等級 4 回顧<br>Level4/reflection-advanced.md"]

    %% 等級 1 回顧（快速）
    L1Reflect --> L1Review["回顧<br>錯誤修復"]
    L1Review --> L1Document["記錄<br>解決方案"]
    L1Document --> L1Update["更新<br>tasks.md"]

    %% 等級 2 回顧（標準）
    L2Reflect --> L2Review["回顧<br>增強內容"]
    L2Review --> L2WWW["記錄<br>成功之處"]
    L2WWW --> L2Challenges["記錄<br>挑戰"]
    L2Challenges --> L2Lessons["記錄<br>經驗教訓"]
    L2Lessons --> L2Update["更新<br>tasks.md"]

    %% 等級 3-4 回顧（全面）
    L3Reflect & L4Reflect --> L34Review["回顧實作<br>與創意階段"]
    L34Review --> L34Plan["對照<br>原始規劃"]
    L34Plan --> L34WWW["記錄<br>成功之處"]
    L34WWW --> L34Challenges["記錄<br>挑戰"]
    L34Challenges --> L34Lessons["記錄<br>經驗教訓"]
    L34Lessons --> L34ImproveProcess["記錄流程<br>改進"]
    L34ImproveProcess --> L34Update["更新<br>tasks.md"]

    %% 完成與切換
    L1Update & L2Update & L34Update --> CreateReflection["建立<br>reflection.md"]
    CreateReflection --> UpdateSystem["更新系統<br>文件"]
    UpdateSystem --> Transition["下一模式：<br>ARCHIVE 模式"]
```

## 📋 回顧結構

回顧應遵循以下結構化格式：

```mermaid
graph TD
    subgraph "回顧文件結構"
        Header["# 任務回顧：[任務名稱]"]
        Summary["## 摘要<br>已完成任務簡要說明"]
        WWW["## 成功之處<br>實作過程中的亮點"]
        Challenges["## 挑戰<br>實作過程遇到的困難"]
        Lessons["## 經驗教訓<br>從經驗中獲得的關鍵洞見"]
        ProcessImp["## 流程改進<br>未來可改進之處"]
        TechImp["## 技術改進<br>類似任務更佳做法"]
        NextSteps["## 後續步驟<br>後續行動或未來工作"]
    end

    Header --> Summary --> WWW --> Challenges --> Lessons --> ProcessImp --> TechImp --> NextSteps
```

## 📊 必要檔案狀態驗證

開始回顧前，請驗證檔案狀態：

```mermaid
graph TD
    Start["檔案狀態<br>驗證"] --> CheckTasks{"tasks.md 是否<br>標記實作完成？"}

    CheckTasks -->|"否"| ErrorImplement["錯誤：<br>返回 IMPLEMENT 模式"]
    CheckTasks -->|"是"| CheckProgress{"progress.md<br>有實作細節？"}

    CheckProgress -->|"否"| ErrorProgress["錯誤：<br>請先更新 progress.md"]
    CheckProgress -->|"是"| ReadyReflect["可進行<br>回顧"]
```

## 🔍 實作回顧方法

```mermaid
graph TD
    subgraph "實作回顧"
        Original["回顧原始<br>需求"]
        Plan["對照<br>實作規劃"]
        Actual["評估實際<br>實作"]
        Creative["回顧創意<br>階段決策"]
        Changes["找出與規劃<br>偏差"]
        Results["評估<br>成果"]
    end

    Original --> Plan --> Actual
    Plan --> Creative --> Changes
    Actual --> Results
    Changes --> Results
```

## 📝 回顧文件範本

### 等級 1（基礎）回顧

```
# 錯誤修復回顧：[錯誤名稱]

## 摘要
[簡要描述錯誤與解決方案]

## 實作
[修正內容說明]

## 測試
[測試方式說明]

## 其他說明
[其他相關資訊]
```

### 等級 2-4（全面）回顧

```
# 任務回顧：[任務名稱]

## 摘要
[任務簡要與成果]

## 成功之處
- [成功點 1]
- [成功點 2]
- [成功點 3]

## 挑戰
- [挑戰 1]：[如何解決]
- [挑戰 2]：[如何解決]
- [挑戰 3]：[如何解決]

## 經驗教訓
- [經驗 1]
- [經驗 2]
- [經驗 3]

## 流程改進
- [流程改進 1]
- [流程改進 2]

## 技術改進
- [技術改進 1]
- [技術改進 2]

## 後續步驟
- [後續任務 1]
- [後續任務 2]
```

## 📊 回顧品質指標

```mermaid
graph TD
    subgraph "回顧品質指標"
        Specific["具體<br>不空泛"]
        Actionable["可行<br>有明確方向"]
        Honest["誠實<br>承認成敗"]
        Forward["前瞻<br>聚焦未來改進"]
        Evidence["有依據<br>具體實例"]
    end
```

## 📋 TASKS.MD 更新格式

回顧過程中，請於 tasks.md 更新：

```
## 狀態
- [x] 初始化完成
- [x] 規劃完成
[等級 3-4:]
- [x] 創意階段完成
- [x] 實作完成
- [x] 回顧完成
- [ ] 歸檔中

## 回顧重點
- **成功之處**：[主要亮點]
- **挑戰**：[主要挑戰]
- **經驗教訓**：[主要經驗]
- **後續步驟**：[後續行動]
```

## 📊 回顧驗證清單

```
✓ 回顧驗證
- 是否徹底回顧實作？ [是/否]
- 成功之處已填寫？ [是/否]
- 挑戰已填寫？ [是/否]
- 經驗教訓已填寫？ [是/否]
- 流程改進已識別？ [是/否]
- 技術改進已識別？ [是/否]
- 後續步驟已記錄？ [是/否]
- 已建立 reflection.md？ [是/否]
- tasks.md 已更新回顧狀態？ [是/否]

→ 全部為是：回顧完成，可進入 ARCHIVE 模式
→ 任一為否：請補齊缺漏回顧內容
```

## 🔄 模式切換通知

回顧完成時，請通知使用者：

```
## 回顧完成

✅ 實作已徹底回顧
✅ 已建立回顧文件
✅ 已記錄經驗教訓
✅ 已識別流程改進
✅ tasks.md 已更新回顧狀態

→ 下一推薦模式：ARCHIVE 模式
```
