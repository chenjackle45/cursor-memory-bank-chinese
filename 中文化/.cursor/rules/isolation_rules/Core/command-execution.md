---
description: Command execution guidelines for isolation-focused Memory Bank
globs: command-execution.md
alwaysApply: false
---

# 指令執行系統

> **重點摘要：** 本系統提供高效指令執行指引，透過適當的指令串接平衡清晰度與位元組最佳化，並妥善記錄指令與結果。

## 🔍 指令效率工作流程

```mermaid
graph TD
    Start["指令<br>規劃"] --> Analyze["分析指令<br>需求"]
    Analyze --> Balance["平衡清晰度<br>與效率"]
    Balance --> Complexity{"指令<br>複雜度？"}

    Complexity -->|"簡單"| Single["執行<br>單一指令"]
    Complexity -->|"中等"| Chain["使用高效<br>指令串接"]
    Complexity -->|"複雜"| Group["分組為<br>邏輯步驟"]

    Single & Chain & Group --> Verify["驗證<br>結果"]
    Verify --> Document["記錄<br>指令與結果"]
    Document --> Next["下一個<br>指令"]
```

## 📋 指令串接指引

```mermaid
graph TD
    Command["指令<br>執行"] --> ChainApprop{"適合<br>串接？"}

    ChainApprop -->|"是"| ChainTypes["串接<br>類型"]
    ChainApprop -->|"否"| SingleCmd["使用單一<br>指令"]

    ChainTypes --> Sequential["順序操作<br>cmd1 && cmd2"]
    ChainTypes --> Conditional["條件操作<br>cmd1 || cmd2"]
    ChainTypes --> Piping["管線<br>cmd1 | cmd2"]
    ChainTypes --> Grouping["指令分組<br>(cmd1; cmd2)"]

    Sequential & Conditional & Piping & Grouping --> Doc["記錄<br>指令與結果"]
```

## 🚦 目錄驗證工作流程

```mermaid
graph TD
    Command["指令<br>執行"] --> DirCheck["檢查目前<br>目錄"]
    DirCheck --> ProjectRoot{"在專案<br>根目錄？"}

    ProjectRoot -->|"是"| Execute["執行<br>指令"]
    ProjectRoot -->|"否"| Locate["尋找<br>專案根目錄"]

    Locate --> Found{"找到專案<br>根目錄？"}
    Found -->|"是"| Navigate["切換至<br>專案根目錄"]
    Found -->|"否"| Error["錯誤：無法<br>找到專案根目錄"]

    Navigate --> Execute
    Execute --> Verify["驗證<br>結果"]
```

## 📋 目錄驗證檢查表

執行任何 npm 或建構指令前：

| 步驟                  | Windows (PowerShell)         | Unix/Linux/Mac                          | 目的                     |
| --------------------- | ---------------------------- | --------------------------------------- | ------------------------ |
| **檢查 package.json** | `Test-Path package.json`     | `ls package.json`                       | 確認目前目錄為專案根目錄 |
| **檢查父目錄**        | `Test-Path "*/package.json"` | `find . -maxdepth 2 -name package.json` | 尋找潛在專案目錄         |
| **切換至專案根目錄**  | `cd [project-dir]`           | `cd [project-dir]`                      | 執行指令前切換至正確目錄 |

## 📋 React 專案指令指引

針對 React 應用，請遵循以下嚴格指引：

| 指令              | 正確用法                                            | 錯誤用法                           | 備註                              |
| ----------------- | --------------------------------------------------- | ---------------------------------- | --------------------------------- |
| **npm start**     | `cd [project-root] && npm start`                    | `npm start`（於父目錄）            | 必須於含 package.json 目錄執行    |
| **npm run build** | `cd [project-root] && npm run build`                | `cd [parent-dir] && npm run build` | 必須於含 package.json 目錄執行    |
| **npm install**   | `cd [project-root] && npm install [pkg]`            | `npm install [pkg]`（錯誤目錄）    | 相依套件安裝於最近的 package.json |
| **npm create**    | `npm create vite@latest my-app -- --template react` | 手動設定 webpack                   | 請使用標準工具建立專案            |

## 🔄 指令串接模式

有效的指令串接模式包括：

| 模式     | 格式           | 範例                                   | 使用情境                     |
| -------- | -------------- | -------------------------------------- | ---------------------------- | ----------------- | --- | --------------- | ------------------ |
| **順序** | `cmd1 && cmd2` | `mkdir dir && cd dir`                  | 順序執行，前者成功才執行後者 |
| **條件** | `cmd1          |                                        | cmd2`                        | `test -f file.txt |     | touch file.txt` | 前者失敗才執行後者 |
| **管線** | `cmd1 \| cmd2` | `grep "pattern" file.txt \| wc -l`     | 前者輸出作為後者輸入         |
| **背景** | `cmd &`        | `npm start &`                          | 背景執行指令                 |
| **分組** | `(cmd1; cmd2)` | `(echo "Start"; npm test; echo "End")` | 一次執行一組指令             |

## 📋 指令記錄範本

```
## 指令執行：［用途］

### 指令
```

[實際指令或串接]

```

### 結果
```

[指令輸出]

```

### 效果
[簡述系統變動]

### 下一步
[後續動作]
```

## 🔍 平台專屬注意事項

```mermaid
graph TD
    Platform["平台<br>偵測"] --> Windows["Windows<br>指令"]
    Platform --> Unix["Unix/Linux/Mac<br>指令"]

    Windows --> WinAdapt["Windows 指令<br>調整"]
    Unix --> UnixAdapt["Unix 指令<br>調整"]

    WinAdapt --> WinChain["Windows 串接：<br>以 & 分隔"]
    UnixAdapt --> UnixChain["Unix 串接：<br>以 ; 分隔"]

    WinChain & UnixChain --> Execute["執行<br>平台專屬<br>指令"]
```

## 📋 指令效率範例

高效指令使用範例：

| 低效                                                  | 高效                                   | 說明                 |
| ----------------------------------------------------- | -------------------------------------- | -------------------- |
| `mkdir dir`<br>`cd dir`<br>`npm init -y`              | `mkdir dir && cd dir && npm init -y`   | 合併相關順序操作     |
| `ls`<br>`grep "\.js$"`                                | `ls \| grep "\.js$"`                   | 管線串接             |
| `test -f file.txt`<br>`if not exists, touch file.txt` | `test -f file.txt \|\| touch file.txt` | 僅在不存在時建立檔案 |
| `mkdir dir1`<br>`mkdir dir2`<br>`mkdir dir3`          | `mkdir dir1 dir2 dir3`                 | 使用內建多參數能力   |
| `npm install pkg1`<br>`npm install pkg2`              | `npm install pkg1 pkg2`                | 一次安裝多個套件     |

## 📋 React 專案初始化標準

請務必使用以下標準方式建立 React 專案：

| 方式                              | 指令                                                | 優點                 | 避免              |
| --------------------------------- | --------------------------------------------------- | -------------------- | ----------------- |
| **Create React App**              | `npx create-react-app my-app`                       | 預設 webpack & babel | 手動設定錯誤      |
| **Create React App w/TypeScript** | `npx create-react-app my-app --template typescript` | 型別安全 + 預設設定  | 模組系統不一致    |
| **Vite**                          | `npm create vite@latest my-app -- --template react` | 更快建構             | 複雜 webpack 設定 |
| **Next.js**                       | `npx create-next-app@latest my-app`                 | SSR 支援             | 模組系統衝突      |

## ⚠️ 錯誤處理工作流程

```mermaid
sequenceDiagram
    participant User
    participant AI
    participant System

    AI->>System: 執行指令
    System->>AI: 回傳結果

    alt 成功
        AI->>AI: 驗證預期結果
        AI->>User: 回報成功
    else 錯誤
        AI->>AI: 分析錯誤訊息
        AI->>AI: 辨識可能原因
        AI->>User: 說明錯誤與原因
        AI->>User: 建議修正方式
        User->>AI: 同意修正
        AI->>System: 執行修正後指令
    end
```

## 📋 指令結果驗證

執行指令後，請驗證：

```mermaid
graph TD
    Execute["執行<br>指令"] --> Check{"檢查<br>結果"}

    Check -->|"成功"| Verify["驗證預期<br>結果"]
    Check -->|"錯誤"| Analyze["分析<br>錯誤"]

    Verify -->|"預期"| Document["記錄<br>成功"]
    Verify -->|"非預期"| Investigate["調查<br>非預期結果"]

    Analyze --> Diagnose["診斷<br>錯誤原因"]
    Diagnose --> Correct["提出<br>修正"]

    Document & Investigate & Correct --> Next["流程<br>下一步"]
```

## 📝 指令執行檢查表

```
✓ 指令執行檢查表
- 指令用途明確？ [是/否]
- 清晰度與效率平衡？ [是/否]
- 平台專屬考量已處理？ [是/否]
- 指令與結果有記錄？ [是/否]
- 結果有依預期驗證？ [是/否]
- 錯誤有妥善處理？ [是/否/不適用]
- npm/建構指令：於專案根目錄執行？ [是/否/不適用]
- React 專案：使用標準工具？ [是/否/不適用]

→ 全部為是：指令執行完成
→ 有否：請補齊缺漏
```

## 🚨 指令執行警告

請避免以下常見指令問題：

```mermaid
graph TD
    Warning["指令<br>警告"] --> W1["過度<br>冗長"]
    Warning --> W2["缺乏<br>錯誤處理"]
    Warning --> W3["不必要<br>複雜"]
    Warning --> W4["毀損性操作<br>未確認"]
    Warning --> W5["錯誤目錄<br>執行"]

    W1 --> S1["使用旗標減少<br>不必要輸出"]
    W2 --> S2["指令串接納入<br>錯誤處理"]
    W3 --> S3["優先使用<br>內建能力"]
    W4 --> S4["毀損操作前<br>需確認"]
    W5 --> S5["npm/建構指令前<br>確認目錄"]
```
