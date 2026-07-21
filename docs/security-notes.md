# 資安須知(Security Notes)

前端資安重點:**所有插入 `innerHTML` 的資料值都要用 `esc()` 轉義**(防儲存型 XSS),
token 存 `localStorage` 須設時效。

完整資安基準與標準函式(`esc()` / `sanitizeCell()`)收錄於後端範本庫的內部文件。

> 改前端 → git push 才生效;後端是另一套(Apps Script 重新部署)。
