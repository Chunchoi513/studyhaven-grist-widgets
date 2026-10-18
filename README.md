# StudyHaven Grist widgets（整個資料夾就是要部署的網站）

StudyHaven 在 Grist 使用的自訂 widget（Custom widget）集中放在這個 repo，由靜態網站主機（Netlify／Cloudflare Pages／GitHub Pages 皆可）提供網址。**這裡沒有任何密鑰、API key 或客戶資料**；widget 只在使用者自己的瀏覽器內讀寫 Grist。

## Widget 一覽

| Widget | 資料夾 | 用途 | Grist 的 Custom URL | 狀態 |
|---|---|---|---|---|
| 招生人工控制（四個按鈕） | [`sales-manual-control/`](sales-manual-control/) | 在 Application 表選一位學生，按「人工接手／檢查下一步／確認執行／核對付款」 | `<網站網址>/sales-manual-control/`（目前：`https://chunchoi513.github.io/studyhaven-grist-widgets/sales-manual-control/`） | 測試中（Sandbox） |

> `<網站網址>` 是這個資料夾部署後得到的網址；實際網址記錄在下面「已部署位置」。

## 已部署位置

- 主機：GitHub Pages（repo：`https://github.com/Chunchoi513/studyhaven-grist-widgets`，公開，分支 `main`，根目錄）
- 網站：`https://chunchoi513.github.io/studyhaven-grist-widgets/`
- `sales-manual-control` 的 Custom URL：`https://chunchoi513.github.io/studyhaven-grist-widgets/sales-manual-control/`

## 結構與命名規則

```
studyhaven-grist-widgets/
├─ README.md                    ← 本頁：所有 widget 的目錄
├─ CHANGELOG.md                 ← 每次改動的紀錄（日期、哪個 widget、改了甚麼）
└─ <項目>-<功能>/               ← 一個 widget 一個資料夾，例如 sales-manual-control
   ├─ index.html                ← Grist 載入的網頁（固定叫 index.html）
   └─ README.md                 ← 這個 widget 的用途、權限、連到哪個流程
```

- 資料夾名：`<項目>-<功能>`，全小寫、用連字號，例如 `sales-manual-control`、之後可加 `post-sales-…`。
- 每個 widget 的網址就是 `<網站網址>/<資料夾名>/`。**改資料夾名會令 Grist 裡的網址失效**，請勿隨意改名。
- 每次修改都要在 `CHANGELOG.md` 加一行。

## 原始檔在哪裡（以本機為準）

本 repo 是**發佈用副本**。原始檔、設計、測試與設定說明都在本機項目 `Projects/StudyHaven/tutoring-automation/sales/`：

- 原始 widget：`sales/widgets/manual-control.html`（與 `sales/widgets/dist/index.html`、本 repo 的 `sales-manual-control/index.html` 內容相同）
- 設定步驟：`sales/widgets/dist/README.md`、`sales/docs/manual-control-setup.md`（M3／M4）
- 職員操作：`sales/docs/manual-handover-staff.md`

## 安全規則

- 不放密鑰、Token、webhook 值、真實學生資料。
- 要改 widget：先改本機原始檔、通過測試，再覆蓋本 repo 的對應檔案並更新 `CHANGELOG.md`。
