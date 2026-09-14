# One Page Go - GitHub（公開展示）

## Project Overview
One Page Go 是一個接案平台，為客戶製作「單頁式網頁應用」。
此 repo 為公開展示用，包含主銷售頁、4 個 Demo、客戶接單流程。

## Repository Structure
```
one-page-go/                              ← GitHub Pages 公開展示
├── index.html                            # 主銷售頁（中文）
├── en/
│   ├── index.html                        # 主銷售頁英文鏡射（T-041）
│   └── solutions/order-system/index.html # 方案頁英文版
├── solutions/order-system/index.html     # 方案：線上訂單系統
├── blog/
│   ├── index.html                        # 部落格索引
│   ├── one-page-website-cost/            # 文章 ×3，各一個 index.html
│   ├── small-business-website-guide/
│   ├── free-website-builder-comparison/
│   └── template.html                     # 新文章範本（不上 sitemap）
├── demos/
│   ├── ecommerce/index.html              # 電商 Demo（Bloom Bakery Sample）＋ admin.html
│   ├── ecommerce-coffee/index.html       # 電商 Demo（Urban Drip Coffee Sample）
│   ├── ecommerce-tea/index.html          # 電商 Demo（Jade Leaf Tea Sample）
│   ├── booking/index.html                # 預約 Demo（Serenity Spa Sample）
│   ├── booking-barber/index.html         # 預約 Demo（Sharp Cuts Barber Sample）
│   ├── booking-pet/index.html            # 預約 Demo（Paws & Love Pet Salon Sample）
│   ├── booking-yoga-flow/index.html      # 預約 Demo（Flow State Yoga Sample）＋ admin.html
│   ├── booking-yoga-terra/index.html     # 預約 Demo（Terra Yoga Sample）＋ admin.html
│   ├── groupbuy/index.html               # 團購 Demo（Fruitbox Collective Sample）
│   ├── groupbuy-kitchen/index.html       # 團購 Demo（Mama's Kitchen Sample）
│   ├── groupbuy-dock/index.html          # 團購 Demo（Fisherman's Dock Sample）
│   ├── ticketing/index.html              # 售票 Demo（Starlight Festival Sample）
│   ├── ticketing-yoga/index.html         # 售票 Demo（Morning Yoga Retreat Sample）
│   ├── ticketing-arcade/index.html       # 售票 Demo（Retro Arcade Night Sample）
│   └── payment/index.html                # 金流 Demo（綠界測試環境）
│   ※ 全部 demo 的資料層走 demo worker＋demo D1（demo-api.one-page-go.com），展示模式、每日重置
├── onboarding/index.html                 # 客戶接單流程（需求→簽約→付款）
├── guide/index.html                      # 購買後設定指南（寄信／資料庫／後台管理）
├── revision/index.html                   # 專案調整需求
├── assets/                               # 首頁作品展示區與 hero 用圖
├── sitemap.xml                           # SEO sitemap（26 筆：中文 9、英文 2、示範站 15）
├── robots.txt                            # SEO robots
├── llms.txt                              # 給 AI 爬蟲的站台摘要
├── favicon.ico                           # Favicon 系列
├── CLAUDE.md
└── README.md
```

## 對應私有 Repo
完整原始碼、模板、文檔、客戶資料在 GitLab 私有 repo：`../gitlab/`（同層 `one_page_go/gitlab/`）

## Code Conventions

### Frontend (index.html)
- 所有 CSS 寫在 `<style>` 內，所有 JS 寫在 `<script>` 內，不外連檔案
- CSS 變數定義在 `:root`，色票統一管理
- 首頁（index.html）採深藍×金設計基準（正本：`../docs/standards/design.md`）：navy／gold 色票變數、字型 Manrope（英數）+ Noto Sans TC（內文）、寬版容器 `min(1120px,92%)`、`.reveal` 進場動畫
- demos 與其他子頁暫沿用原慣例（Playfair Display + Noto Serif TC、480px 主容器、fadeUp 進場）；子頁改版依任務 T-008～T-013 分批進行，demos 不改版
- API 呼叫統一用 `fetch(API_URL)`，GET 用 query string，POST 用 JSON body

## Template Types
1. **ecommerce** - 微型電商一頁店
2. **booking** - 預約 + 付款追蹤
3. **groupbuy** - 團購管理系統
4. **ticketing** - 活動售票頁

## Development Rules
- Demo 展示不得使用真實客戶資訊，一律用虛構品牌名
- `demos/` 內的 HTML 是展示版（已填入虛構品牌），非模板原始碼
- 修改模板後需從 GitLab 複製展示版到此 repo

## 中英同步（T-041 立規）

英文頁是中文頁的**鏡射**，不是獨立文案：同一份 HTML／CSS／JS，只換文字、`lang`、meta 與結構化資料。2026-06 建立的英文頁因獨立維護，到 2026-09 已與中文首頁脫節 3 次改版，此後照以下規則：

- 有英文鏡射頁的中文頁：`index.html` ⇄ `en/index.html`、`solutions/order-system/` ⇄ `en/solutions/order-system/`（T-042、T-043 完成後再加 blog、onboarding、guide、revision）。
- **改中文頁的任何內容（文案、區塊、JS 行為、meta），同一個 commit 必須同步改 `en/` 對應頁**；沒同步就不能提交。
- 同一個 commit 一併更新 `sitemap.xml` 中該中英兩筆的 `lastmod`（值＝推送日）。新增頁面要加進 sitemap；`lastmod` 只在內容真的變更時才動，不填假日期。
- 每一對中英頁互指 hreflang 三筆（`zh-Hant-TW`、`en`、`x-default` 指中文版），`canonical` 各指自己。
- 語系切換元件 `.lang-switch`（地球圖示膠囊鈕，規格見 `../docs/standards/design.md`）連到**同一頁的另一語系**，不是首頁；手機版留在 header 上，不藏進漢堡選單。
- 英文頁 `body` 字型改為 `"Manrope","Noto Sans TC"`（英文優先），其餘樣式與中文頁相同。
- 示範站不翻譯；英文頁連到示範站處標示「Demo in Chinese」或「(in Chinese)」，並加 `hreflang="zh-Hant-TW"`。
- 英文頁的路徑一律用根相對路徑（`/assets/…`、`/demos/…`），因為 `en/` 在子目錄。
