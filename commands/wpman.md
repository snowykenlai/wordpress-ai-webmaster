---
description: Open the WordPress AI webmaster menu. Supports direct selection with 0-5. / 開啟 WordPress AI 站長選單，支援 0-5 編號直接選擇。
argument-hint: "[0-5]"
---

Use the `wordpress-ai-webmaster` skill for this request, and follow its fixed menu, input parsing, response format and read-only limits exactly.

請使用 `wordpress-ai-webmaster` skill 處理這次站長選單請求，並完整遵守其中的固定選單、輸入解析、回應格式與唯讀限制。

User input: `/wpman $ARGUMENTS`
使用者輸入：`/wpman $ARGUMENTS`

- If `$ARGUMENTS` is empty, let the skill show the fixed menu.
- If `$ARGUMENTS` has content, pass the raw argument to the skill. A valid number selects that option; anything else re-prompts.
- Do not add, remove, or rewrite menu items.
- Do not connect to a site, call paid APIs, run system commands, use tools, or modify the user's site or project files.
- Do not pretend items 1-4 are implemented. Do not promise SEO rankings or GEO results.

- `$ARGUMENTS` 為空白時，交由 skill 顯示固定選單。
- `$ARGUMENTS` 有內容時，將原始參數原樣交給 skill 判斷；有效編號直接選項，無效輸入提示重選。
- 不自行增加、刪除或改寫選單項目。
- 不連接網站、不呼叫付費 API、不執行系統指令、不使用工具，也不修改使用者網站或既有專案檔案（站長自己的操作紀錄除外）。
- 不假裝第 1～4 項模組已實作，不承諾 SEO 排名或 GEO 成效。
