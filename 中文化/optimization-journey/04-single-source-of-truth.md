# 🔄 最佳化第 4 輪：單一真實來源實作

## 🚨 發現的主要問題

1. 雖已引入 tasks.md，系統仍要求多檔案同步任務狀態
2. 需同時更新 .cursorrules 與 activeContext.md，易產生同步錯誤
3. 複雜指令驗證與巢狀 if-statement 造成終端機當機
4. 文件參考不一致導致任務追蹤混亂

## ✅ 主要改進

1. **真正單一真實來源**

   - 指定 tasks.md 為唯一任務狀態追蹤檔案
   - 移除所有 .cursorrules 任務狀態更新指令
   - 所有檔案僅參考，不重複任務資訊
   - 增加 tasks.md 存在性驗證

2. **指令執行安全**

   - 簡化文件驗證流程避免終端機當機
   - 移除 Windows 批次指令巢狀 if-statement
   - 增加更安全的常用指令版本
   - 信任 AI 既有檔案操作知識

3. **文件角色明確化**

   - .cursorrules：僅記錄專案模式與情報
   - activeContext.md：實作細節與當前重點
   - progress.md：總進度與任務參考
   - tasks.md：所有任務狀態追蹤

4. **技術修正**
   - 修正 main.mdc 的 MDC 參考連結
   - 修正單一來源驗證清單
   - 強化平台專屬文件
   - 簡化即時更新格式
