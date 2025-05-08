---
description: Platform detection and command adaptation for isolation-focused Memory Bank
globs: platform-awareness.md
alwaysApply: false
---

# 平台感知系統

> **重點摘要：** 本系統會偵測作業系統、路徑格式與 shell 環境，並據此調整指令，確保跨平台相容性。

## 🔍 平台偵測流程

```mermaid
graph TD
    Start["開始平台<br>偵測"] --> DetectOS["偵測作業系統<br>環境"]
    DetectOS --> Windows["Windows<br>偵測"]
    DetectOS --> Mac["macOS<br>偵測"]
    DetectOS --> Linux["Linux<br>偵測"]

    Windows & Mac & Linux --> PathCheck["路徑分隔符<br>偵測"]
    PathCheck --> CmdAdapt["指令<br>調整"]
    CmdAdapt --> ShellCheck["Shell 類型<br>偵測"]
    ShellCheck --> Complete["平台偵測<br>完成"]
```

## 📋 平台偵測實作

為了可靠的平臺偵測：

```
## 平台偵測結果
作業系統: [Windows/macOS/Linux]
路徑分隔符: [\ 或 /]
Shell 環境: [PowerShell/Bash/Zsh/Cmd]
指令調整: [需要/不需要]

正在調整指令以符合 [偵測到的平台]...
```

## 🔍 路徑格式轉換

當需轉換路徑格式時：

```mermaid
sequenceDiagram
    participant Input as 路徑輸入
    participant Detector as 格式偵測器
    participant Converter as 格式轉換器
    participant Output as 已調整路徑

    Input->>Detector: 原始路徑
    Detector->>Detector: 偵測目前格式
    Detector->>Converter: 路徑 + 目前格式
    Converter->>Converter: 套用目標格式
    Converter->>Output: 平台專屬路徑
```

## 📝 平台驗證檢查表

```
✓ 平台驗證
- 作業系統是否正確辨識？ [是/否]
- 路徑分隔符格式已偵測？ [是/否]
- Shell 環境已辨識？ [是/否]
- 指令集已適當調整？ [是/否]
- 路徑格式處理已設定？ [是/否]

→ 全部為是：平台調整完成
→ 有否：請執行額外偵測步驟
```
