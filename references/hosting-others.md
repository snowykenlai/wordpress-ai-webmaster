# 其他主機（參考資料）

> 從 `SKILL.md` 拆出。與主檔衝突時，以主檔為準。
> 讀取時機：使用者的主機不是 Cloudways 時。
## 其他主機

不是 Cloudways 的話，四層快取與伺服器層操作做不到，但 WordPress 層一樣能做。
**不要因為不是 Cloudways 就少幫人家。** 先把限制講清楚，再用手上有的做。

### 共用的原則

- 先問他用哪一家主機。不同主機的介面差很多。
- 不確定位置就說「我不確定你這家的介面」，請他描述或截圖。
- 主機層做不到的事（重啟服務、清邊緣快取、看資源圖表），直接說做不到。

### cPanel

| 要做什麼 | 去哪 |
|---|---|
| 備份 | cPanel → **Files → Backup**，或主機商自己的備份工具 |
| 檔案管理 | cPanel → **Files → File Manager** |
| 資料庫 | cPanel → **Databases → phpMyAdmin** |
| 錯誤記錄 | cPanel → **Metrics → Errors** |
| PHP 版本與設定 | cPanel → **Software → Select PHP Version** |

### SiteGround

| 要做什麼 | 去哪 |
|---|---|
| 快取 | Site Tools → **Speed → Caching** |
| 備份 | Site Tools → **Security → Backups** |
| 檔案 | Site Tools → **Site → File Manager** |
| 資料庫 | Site Tools → **Site → MySQL** |
| SSL | Site Tools → **Security → SSL Manager** |

### 共用空間的虛擬主機

通常沒有 SSH，也沒有資料庫直接存取，只剩 WordPress 後台能操作。

遇到這種情況：

- 先講清楚限制在哪，不要假裝做得到。
- 能做的先做（改內容、改設定、看外掛）。
- 需要檔案層或資料庫層時，明確說「這台主機能給的權限不夠」。

### 自架（VPS / 自己的機器）

如果使用者自己管機器，他能給的權限最多，但風險也最高。

- 照「憑證索取」章的規則處理。
- 備份、還原、重啟這類操作，仍然走安全網。

### 這一章的使用原則

**主機介面會改版。** 上面列的位置可能過時，使用者說「找不到」時，
先問他看到什麼，不要堅持自己的版本是對的。

