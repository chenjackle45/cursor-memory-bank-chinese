---
description: VAN 模式平台偵測的視覺流程圖
globs: van-platform-detection.md
alwaysApply: false
---

# VAN 模式：平台偵測

> **重點摘要：** 偵測作業系統、判斷路徑分隔符，並記錄所需的指令調整。

## 🌐 平台偵測流程

```mermaid
graph TD
    PD["平台偵測"] --> CheckOS["偵測作業系統"]
    CheckOS --> Win["Windows"]
    CheckOS --> Mac["macOS"]
    CheckOS --> Lin["Linux"]

    Win & Mac & Lin --> Adapt["依平台調整指令"]

    Win --> WinPath["路徑：反斜線 (\\)"]
    Mac --> MacPath["路徑：斜線 (/)"]
    Lin --> LinPath["路徑：斜線 (/)"]

    Win --> WinCmd["指令調整：<br>dir、icacls 等"]
    Mac --> MacCmd["指令調整：<br>ls、chmod 等"]
    Lin --> LinCmd["指令調整：<br>ls、chmod 等"]

    WinPath & MacPath & LinPath --> PathCP["路徑分隔符<br>檢查點"]
    WinCmd & MacCmd & LinCmd --> CmdCP["指令<br>檢查點"]

    PathCP & CmdCP --> PlatformComplete["平台偵測<br>完成"]

    style PD fill:#4da6ff,stroke:#0066cc,color:white
    style PlatformComplete fill:#10b981,stroke:#059669,color:white
```

## 📋 檢查點驗證範本（範例）

```
✓ 區段檢查點：平台偵測
- 作業系統已偵測？ [YES/NO]
- 路徑分隔符已確認？ [YES/NO]
- 指令調整已記錄？ [YES/NO]

→ 全部 YES：平台偵測完成。
→ 任一 NO：請先修正再繼續。
```

**下一步：** 載入並處理 `van-file-verification.md`。
