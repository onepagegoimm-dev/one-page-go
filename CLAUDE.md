# One Page Go - GitHub（公開展示）

## Project Overview
One Page Go 是一個接案平台，為客戶製作「單頁式網頁應用」。
此 repo 為公開展示用，包含主銷售頁、4 個 Demo、客戶接單流程。

## Repository Structure
```
one-page-go/                              ← GitHub Pages 公開展示
├── index.html                            # 主銷售頁
├── demos/
│   ├── ecommerce/index.html              # 電商 Demo（Bloom Bakery Sample）
│   ├── ecommerce-coffee/index.html       # 電商 Demo（Urban Drip Coffee Sample）
│   ├── ecommerce-tea/index.html          # 電商 Demo（Jade Leaf Tea Sample）
│   ├── booking/index.html                # 預約 Demo（Serenity Spa Sample）
│   ├── booking-barber/index.html         # 預約 Demo（Sharp Cuts Barber Sample）
│   ├── booking-pet/index.html            # 預約 Demo（Paws & Love Pet Salon Sample）
│   ├── groupbuy/index.html               # 團購 Demo（Fruitbox Collective Sample）
│   ├── groupbuy-kitchen/index.html       # 團購 Demo（Mama's Kitchen Sample）
│   ├── groupbuy-dock/index.html          # 團購 Demo（Fisherman's Dock Sample）
│   ├── ticketing/index.html              # 售票 Demo（Starlight Festival Sample）
│   ├── ticketing-yoga/index.html         # 售票 Demo（Morning Yoga Retreat Sample）
│   ├── ticketing-arcade/index.html       # 售票 Demo（Retro Arcade Night Sample）
│   └── payment/index.html                # 金流 Demo
├── onboarding/index.html                 # 客戶接單流程（需求→簽約→付款）
├── guide/index.html                      # 購買後設定指南（GitHub + Google Sheet）
├── sitemap.xml                           # SEO sitemap
├── robots.txt                            # SEO robots
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
- 字型：Playfair Display（標題）+ Noto Serif TC（內文）
- 動畫：fadeUp 進場、float logo、spin loading
- 手機優先設計，max-width: 480px 主容器
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
