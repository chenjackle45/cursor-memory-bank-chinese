---
description: VAN QA 規則呼叫的完整指南
globs: van-qa-utils/rule-calling-guide.md
alwaysApply: false
---

# VAN QA：完整規則呼叫指南

> **重點摘要：** 本參考指南說明如何於驗證流程中正確呼叫所有 VAN QA 規則。

## 🔍 規則呼叫基礎

請記住以下重點原則：

1. 請務必使用 `fetch_rules` 工具載入規則
2. 使用正確的規則路徑
3. 僅於需要時載入元件

## 📋 主要 QA 進入點

當使用者輸入 "VAN QA" 時，請載入主進入點：

```
fetch_rules with "isolation_rules/visual-maps/van-qa-main"
```

## 📋 驗證檢查

於驗證過程中依序載入下列元件：

```
1. fetch_rules with "isolation_rules/visual-maps/van-qa-checks/dependency-check"
2. fetch_rules with "isolation_rules/visual-maps/van-qa-checks/config-check"
3. fetch_rules with "isolation_rules/visual-maps/van-qa-checks/environment-check"
4. fetch_rules with "isolation_rules/visual-maps/van-qa-checks/build-test"
```

## 📋 工具元件

根據驗證結果需要時載入下列元件：

```
- 產生報告：fetch_rules with "isolation_rules/visual-maps/van-qa-utils/reports"
- 問題修正：fetch_rules with "isolation_rules/visual-maps/van-qa-utils/common-fixes"
- 模式切換：fetch_rules with "isolation_rules/visual-maps/van-qa-utils/mode-transitions"
```

## ⚠️ 關鍵提醒

請於下列特定時機呼叫這些規則：

- 每當輸入 "VAN QA" 時，務必載入主 QA 進入點
- 驗證開始前，務必先載入 dependency-check
- 驗證結束後，務必載入報告
- 驗證成功後，務必載入模式切換
- 驗證失敗後，務必載入常見修正

## 🔄 完整驗證流程順序

QA 驗證流程的完整順序如下：

1. 載入主進入點：`isolation_rules/visual-maps/van-qa-main`
2. 載入第一檢查：`isolation_rules/visual-maps/van-qa-checks/dependency-check`
3. 載入第二檢查：`isolation_rules/visual-maps/van-qa-checks/config-check`
4. 載入第三檢查：`isolation_rules/visual-maps/van-qa-checks/environment-check`
5. 載入第四檢查：`isolation_rules/visual-maps/van-qa-checks/build-test`
6. 通過時載入：`isolation_rules/visual-maps/van-qa-utils/reports`
7. 通過時載入：`isolation_rules/visual-maps/van-qa-utils/mode-transitions`
8. 失敗時載入：`isolation_rules/visual-maps/van-qa-utils/common-fixes`
