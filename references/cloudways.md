# Cloudways 操作指南（參考資料）

> 從 `SKILL.md` 拆出。與主檔衝突時，以主檔為準。
> 讀取時機：使用者的主機是 Cloudways，要找某個功能在哪時。

## Cloudways 操作指南

Cloudways 的介面會改版，而且不同方案看到的畫面不完全一樣。

**所以這一章不給你死的位置，給你「找得到的方法」。**

已經查證過的位置我還是會寫，但那只是「我查證當天看到的位置」，不是保證。
**以使用者眼前的畫面為準。**

### 0. 三個萬用方法（比背路徑有用）

找不到東西時，照這個順序試：

1. **看左側選單** —— 主要功能都在那裡，往下捲到底也會有東西
2. **在頁面上搜尋** —— 按 Ctrl+F（Mac 是 Cmd+F），打關鍵字：
   Backup、SSL、Cache、Monitoring、Security、Access
3. **問我** —— 跟我說你要做什麼，我告訴你可能在哪；還是找不到，就一起看畫面

**這三個方法不會因為改版而失效。**

### 1. 先判斷你用哪個介面

| 你看到的 | 是哪個 |
|---|---|
| 左側有固定的側邊欄、首頁是磚塊式的產品入口 | **新介面** |
| 上方是橫向選單、沒有側邊欄 | **舊介面** |

新介面把伺服器與應用程式收在 **Cloudways Flexible** 底下。
另外還有 **Autonomous** 與 **Velocity** 兩條產品線，不同產品線的功能不完全一樣。

如果使用者看到的是舊介面，直接說「你這版是舊介面，位置跟新介面不同」，
不要硬套下面的路徑。

### 2. 找到你的網站

**查證過的位置（2026-11-16，Cloudways 官方文件 article 5121284）：**

- **Flexible → My Applications** → 你的應用程式
- **Flexible → My Servers** → 你的伺服器

找不到就用第 0 節那三個方法。

### 3. 看網站正不正常

三種看法，從外到內。

**從外面看（最快）**

直接開網站首頁。打得開、內容對不對，這一步不需要登入任何後台。

**從主機看資源**

查證過的位置：**Flexible → My Servers → 選你的 server → Monitoring**（來源：article 5121284，2026-11-16 查證）

Monitoring 裡面有這些頁面：

- **Summary**：CPU、記憶體、磁碟、頻寬
- **Details**：各項資源的歷史圖表
- **Traffic**：IP 請求、機器人流量、URL 請求、狀態碼、頻寬
- **PHP**：請求的頁面、執行中的程序、慢頁面
- **MySQL**：摘要、慢查詢
- **Running Crons**：自動執行中的排程
- **Disk Usage**：磁碟用量
- **Access Logs / Error Logs**：存取與錯誤記錄

**從應用程式看**

查證過的位置：**Flexible → My Applications → 選應用程式 → Monitoring**（來源：article 5121284，2026-11-16 查證）

**一個很容易卡住的地方：Cloudways 的 log 時間是 UTC。**

頁面會顯示與你當地時間的差。使用者問「網站什麼時候壞的」時，記得換算，
不然會對不上。

**打不開時，先看這三件事：**

1. 服務有沒有在跑（Monitoring）
2. 磁碟有沒有滿（滿了資料庫會停）
3. 最近有沒有動過什麼（裝外掛、改主題、改 DNS）

### 4. 清快取、備份、登入後台、SSH

**這幾項的位置依方案與版本而異，我沒有查到單一的固定路徑。
不要硬記我說的，用第 0 節的方法找。**

| 你要做的事 | 在頁面上搜這個字 | 大概在哪一類頁面 |
|---|---|---|
| 清快取 | Cache、Purge | 應用程式頁面 |
| 備份與還原 | Backup | 應用程式或 server 頁面 |
| 一鍵登入 WordPress 後台 | Site Manager、WP Admin | 新介面才有 |
| SSH / SFTP 帳密 | Application Access Details | 應用程式頁面 |
| 安全功能 | Security | server 頁面（新介面、Flexible 才有） |

**找到之後，做法不變：**

**清快取** —— Cloudways 的快取不只一層。這裡清了還有外掛快取、CDN 快取。
只清一層就看到舊內容，是很常見的情況，不要以為沒生效。

**備份與還原** —— 還原等於回到過去。**還原之後才寫的文章、訂單、會員註冊都會消失。**
這是不可逆的，所以還原前一定先做一份「現在的備份」。

**SSH** —— 公鑰放主機、私鑰給站長，不要搞反。
公鑰可以公開，私鑰絕對不行。

### 5. 安全功能

新介面整合了 Imunify360。Server 的 Security 頁面大致有這些分頁：

- **Overview**：防火牆與掃描的總覽
- **Incidents**：被擋下的事件，可以從這裡把 IP 加進白名單或黑名單
- **Domain Reputation**：網域信譽，被列黑名單時會收到提醒
- **Firewall**：IP 與國家的允許、封鎖規則
- **Shell Access**：SSH/SFTP 與 MySQL 遠端連線的 IP 白名單

惡意程式掃描（Malware Protection）是**每個應用程式各自加購的 add-on**，不是整台 server 都有。要到應用程式的 Application Security → Malware Protection 查看與啟用。

來源：
- Server Security 頁面：`support.cloudways.com/en/articles/9979437-a-brief-guide-to-server-security-management`，2026-11-16 查證。原文："Security Management is only available on Cloudways New Interface and limited to Cloudways Flexible Product only."
- Malware Protection：`support.cloudways.com/en/articles/9166541-how-to-use-malware-protection-to-protect-your-applications`，2026-11-16 查證。原文："Malware Protection is exclusively available on the New Interface of Cloudways Flexible for all types of applications hosted on Cloudways."
- 新介面總覽：`support.cloudways.com/en/articles/11847555-navigating-the-new-cloudways-interface-how-to-use-it-what-s-new`，2026-11-16 查證。原文：“Integrated with Imunify360, our new security suite provides a complete set of tools to protect your servers and applications in real-time.”；“explore the new Security tab under your server settings. You'll find advanced tools like firewall rules, incident logs…”（惡意掃描的位置以上面 9166541 為準）；“The advanced Security Management tools (powered by Imunify360) are only available on the New UI and currently limited to Cloudways Flexible products.”

**只有新介面、而且依官方原文只有 Cloudways Flexible 才有。** 用其他產品線看不到，不要假裝有。
注意：Cloudways Velocity 另有一篇 Security 說明（`16160629`），介面路徑與分頁不同。如果使用者用的是 Velocity，以那篇為準。

### 6. Cloudways MCP：讓 AI 直接接上你的主機帳號

Cloudways 有官方的 MCP server，可以讓 Cursor、Claude、VS Code 這類 AI 工具
直接接上你的 Cloudways 帳號，用講話的方式操作主機。

它有 300 種以上的工具，涵蓋大部分你在網頁介面能做的事。

**要不要用，由使用者決定。** 站長的立場：

- 它是一個選項，不是必要條件。
- 它用你的帳號權限做事，所以 Access Token 的權限要選對（優先用 Read-Only）。
- 它一樣會做不可逆的事（例如刪 server），操作分級與安全網照樣適用。
- 使用者不想接，就不要接。BrowserOS 或 SSH 一樣能做。

**怎麼接（給想接的人）：**

1. 進入 **API Integration**。官方文件對入口有兩種說法：
   **右上角的頭像選單**，或**左側選單最下面的方格圖示**。
   兩個都試，看到 API Integration 就點進去。
2. 在 **Access Token Details** 按 **Create Access Token**
3. 選權限與到期日。**第一次建議 Read-Only，到期日設短一點。**
4. 複製 token。**它只顯示一次。**
5. 在 AI 工具裡依 Cloudways 的 MCP 設定指南貼上 token
6. 確認連接：Cursor 是 `Settings → Tools & MCP`，綠點代表連上、紅點代表有問題。
   （來源：Cloudways 官方 MCP 設定指南 `support.cloudways.com/en/articles/14654372-how-to-use-cloudways-mcp-server-for-ai-based-server-management`，2026-11-16 查證。）

### 7. 舊版 API Key 已經不能用了

Cloudways 在 **2026-10-15** 停止舊版 API Key 的服務，現在只能用 Access Token。

**這是已經發生的事，不是即將發生。**

如果使用者說「我用 API Key 啊」，告訴他那條連線已經失效，要重新產生 Access Token。

來源：Cloudways 官方部落格 MCP 2.0 文（2026-11-16 查證）。

### 8. 這一章的使用原則

- **位置以使用者看到的畫面為準。** 我寫的是查證當天的樣子。
- 使用者說「我找不到」時，先問他看到什麼，不要硬報路徑。
- 不確定某個功能在不在，就說「我不確定這個版本有沒有」，比亂指好。
- **我給的具體位置都有查證日期。超過三個月就當「可能過時」，重新查或問使用者。**
- 動到備份還原、刪 server 這類事情，一律走操作分級與安全網。

