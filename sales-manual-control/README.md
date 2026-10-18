# sales-manual-control（招生人工控制）

Grist 的 Custom widget，放在 **Application** 表旁邊。選一位學生後有四個中文按鈕：

| 按鈕 | 作用 |
|---|---|
| 人工接手 | 暫停這筆報名的自動流程，顯示「可以修改」後才可改資料 |
| 檢查下一步 | 顯示下一步方案（不發訊息、不建付款連結） |
| 確認執行 | 執行方案，完成後接續自動流程 |
| 核對付款 | 向 Airwallex 查證付款（不發訊息、不建新連結） |

## 在 Grist 加入

1. Admin 文件 → 有 Application 表的頁面 → **Add New → Add widget to page → Custom**。
2. 資料來源 **Application**；**Select By** 連到報名表。
3. **Custom URL**：`<網站網址>/sales-manual-control/`（見上層 README 的「已部署位置」）
4. **Access**：Full document access。

## 它怎樣運作

widget 把「請求編號」寫進該報名列的 `Manual_Request_ID`；Grist 的 webhook（只監看這一欄、只有 Update）通知 n8n 的 `11 - Grist Manual Control and Recovery [v2]` 處理，結果寫回報名列，widget 顯示。

- n8n webhook 路徑：`/webhook/grist-sales-manual-control`（需要 Header 驗證，密鑰只在 Grist 與 n8n，不在這個 repo）。
- 表格若不叫 `Application`：在 widget 選項設定 `tableId`。

## 檔案

- `index.html`：widget 本體（單一檔案，無其他依賴；載入 Grist 官方 plugin API）。

## 來源與版本

- 原始檔：本機項目 `sales/widgets/manual-control.html`。
- 修改紀錄：見上層 [`CHANGELOG.md`](../CHANGELOG.md)。
