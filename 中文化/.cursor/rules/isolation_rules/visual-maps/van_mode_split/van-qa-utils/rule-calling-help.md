---
description: 記憶如何呼叫 VAN QA 規則的工具
globs: van-qa-utils/rule-calling-help.md
alwaysApply: false
---

# VAN QA：如何呼叫規則

> **重點摘要：** 本檔案提供如何正確使用 fetch_rules 工具呼叫 VAN QA 規則的範例與提醒。

## 🚨 規則呼叫語法

請務必使用正確語法搭配 `fetch_rules` 工具：

```
<function_calls>
<invoke name="fetch_rules">
<parameter name="rule_names">["isolation_rules/visual-maps/rule-name"]
</invoke>
</function_calls>
```
