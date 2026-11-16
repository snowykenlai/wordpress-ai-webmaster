# WordPress 基礎知識（參考資料）

> 從 `SKILL.md` 拆出。與主檔衝突時，以主檔為準。
> 讀取時機：要解釋 WordPress 概念、或判斷某個東西是什麼時。

## WordPress 基礎知識

這一章是給「不熟 WordPress 的模型」看的。你的 agent 可能本來就懂，也可能不懂。
不確定時，照這一章判斷，不要憑印象回答。

### 1. 一個 WordPress 網站由五個部分組成

| 部分 | 位置 | 壞掉會怎樣 |
|---|---|---|
| **核心** | `wp-admin/`、`wp-includes/`、根目錄的 `wp-*.php` | 不要手改。壞了就重新安裝核心，覆蓋時保留 `wp-config.php` 與 `wp-content/` |
| **主題** | `wp-content/themes/` | 外觀與版面。主題壞掉會白畫面，但資料都還在 |
| **外掛** | `wp-content/plugins/` | 功能。一次停用全部外掛可以快速判斷是不是外掛造成 |
| **上傳檔案** | `wp-content/uploads/` | 所有圖片與附件。這個目錄刪掉無法從資料庫還原 |
| **資料庫** | MySQL | 文章、頁面、設定、使用者、選單全在這裡 |

**判斷原則：畫面相關的往主題找，功能相關的往外掛找，資料不見了往資料庫找。**

### 2. 資料庫只有幾張表重要

| 表 | 放什麼 |
|---|---|
| `{prefix}_posts` | 文章、頁面、選單項目、附件記錄 |
| `{prefix}_postmeta` | 每篇文章的附加設定 |
| `{prefix}_options` | 全站設定。`siteurl`、`home`、`active_plugins`、`template` 都在這裡 |
| `{prefix}_users` / `{prefix}_usermeta` | 帳號與權限 |
| `{prefix}_terms` / `{prefix}_term_taxonomy` / `{prefix}_term_relationships` | 分類與標籤 |

**前綴不一定是 `wp_`。** 動手前先用 `wp db prefix` 或查 `wp-config.php` 的 `$table_prefix` 確認，不要寫死。

**`active_plugins` 這一筆是外掛的開關。** 停用外掛改的就是它在 `_options` 裡的序列化資料，這正是不能用正則硬改的原因。

### 3. wp-config.php 裡只有幾個常數要記

| 常數 | 作用 |
|---|---|
| `DB_NAME` / `DB_USER` / `DB_PASSWORD` / `DB_HOST` | 資料庫連線。改錯整站白畫面 |
| `$table_prefix` | 資料表前綴。改錯等於找不到資料 |
| `WP_DEBUG` / `WP_DEBUG_LOG` / `WP_DEBUG_DISPLAY` | 除錯。暫時開啟可以在 `wp-content/debug.log` 看到錯誤 |
| `WP_MEMORY_LIMIT` | 前端可用記憶體 |
| `WP_MAX_MEMORY_LIMIT` | 後台與圖片處理可用記憶體 |

**`wp-config.php` 是封閉規則。** 只有 G2 清單列舉的單一 `define()` 常數可以改，其餘一律走 G3。

### 4. 快取有四層，要全清才算數

| 層 | 誰做的 | 怎麼清 |
|---|---|---|
| **外掛磁碟快取** | 主機或快取外掛提供的頁面快取 | 對應外掛或主機後台的「清除全部快取」 |
| **物件快取** | Redis 或 Memcached | `wp cache flush`，或主機後台重啟該服務 |
| **邊緣快取** | CDN 或主機內建的邊緣層 | CDN 後台的 purge，或主機後台清邊緣快取 |
| **資源最佳化快取** | 壓縮／合併 CSS、JS 的外掛 | 該外掛的「重新產生」 |

**只清一層不算驗收。** 改完前台還是舊的，百分之八十是某一層沒清。

### 5. 排錯的固定順序

不要跳步。每一步確認完再往下。

1. **網站活著嗎**：首頁打得開嗎、後台打得開嗎
2. **壞在哪裡**：全部頁面都壞，還是只有某一頁
3. **什麼時候開始壞的**：最近有沒有人裝外掛、改主題、改程式碼、換主機
4. **切到預設主題測試**：換成官方預設主題，外觀恢復就是主題問題
5. **停用全部外掛再逐一開**：把 `wp-content/plugins` 改名可以一次停用全部；正常了就是外掛問題
6. **看錯誤記錄**：`wp-content/debug.log`、主機的 error log、PHP error log

**不要一開始就改程式碼。** 八成的問題靠前五步就找出來了。

### 6. 常見錯誤訊息對照

| 訊息 | 意思 | 先看哪裡 |
|---|---|---|
| `Allowed memory size exhausted` | 記憶體用盡 | `WP_MEMORY_LIMIT` / `WP_MAX_MEMORY_LIMIT`，或找吃記憶體的外掛 |
| `Maximum execution time exceeded` | 執行逾時 | 通常是無窮迴圈或有問題的外掛 |
| `Error establishing a database connection` | 連不上資料庫 | `wp-config.php` 的 DB 常數、資料庫服務是否活著 |
| 整頁白畫面 | PHP 致命錯誤 | 開 `WP_DEBUG`，看 `debug.log` |
| HTTP 500 | 伺服器端錯誤 | PHP 錯誤或 `.htaccess` 寫壞 |
| HTTP 403 | 被拒絕 | 檔案權限，或安全外掛擋住 |
| `Briefly unavailable for scheduled maintenance` | 更新中途失敗 | 刪掉根目錄的 `.maintenance` 檔 |
| 中文變方塊 | 字型沒有中文字 | 補 `Noto Sans TC` 這類後備字型 |

### 7. 不可以手改的地方

| 位置 | 為什麼 |
|---|---|
| `wp-admin/`、`wp-includes/` | 核心檔案，升級會覆蓋，改了等於白改 |
| 資料庫的表結構 | 直接改 schema 會讓核心與外掛失效 |
| `wp-config.php` 的 DB 常數 | 改錯整站連不上資料庫 |
| `wp-content/uploads/` 的內容 | 刪掉無法從資料庫還原 |

**要加功能，寫 MU-Plugin（`wp-content/mu-plugins/`），不要改 `functions.php`。**
主題一更新，`functions.php` 的修改就消失了，MU-Plugin 不會。

### 8. 這一章跟其他章的關係

- 本章的知識用來**判斷**，不用來繞過規則。
- 知道怎麼做，不等於可以直接做。要不要做、怎麼做，仍依「操作分級」與「安全網」。
- 本章沒寫到的，不要憑印象補。說「這個我不確定」，比猜錯好。

