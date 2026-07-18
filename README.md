# BA.SEW Landing Page

**Landing thương mại cho thiết bị cảnh báo khẩn cấp BA.SEW**  
*(BE SMART EMERGENCY WARNING)* — one-page conversion: giới thiệu → trải nghiệm tracking → giỏ hàng → checkout VietQR/COD.

<p align="center">
  <img alt="React" src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" />
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img alt="Tailwind" src="https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" />
  <img alt="Webpack" src="https://img.shields.io/badge/Webpack-8DD6F9?style=for-the-badge&logo=webpack&logoColor=black" />
  <img alt="Zod" src="https://img.shields.io/badge/Zod-3E67B1?style=for-the-badge&logo=zod&logoColor=white" />
</p>

> Một mắt xích trong hệ sinh thái **BA.SEW**:  
> **Firmware ESP32** → **Cloud relay** → **[Tracking map](https://github.com/ThanhVu220809/Tracking_page)** → **Landing bán hàng (repo này)**

---

## Sản phẩm đang bán gì?

BA.SEW là thiết bị SOS + GPS cho người thân (người lớn tuổi, trẻ em, đi một mình):

- Bấm nút → SMS + gọi cascade + chia sẻ vị trí
- Theo dõi qua web, **không cần cài app**
- Giá niêm yết landing: **400.000đ / thiết bị** · ship toàn quốc

Landing này không chỉ “đẹp” — nó đóng **funnel bán hàng end-to-end**.

---

## Tính năng

### Conversion UI
| Section | Việc |
|---|---|
| **Hero** | Headline + bullet SOS/GPS/web + CTA |
| **Overview** | BA.SEW là gì · đối tượng · 3 bước hoạt động |
| **Experience** | Video demo + deep-link sang Tracking map |
| **Conversion** | Pricing / CTA đặt hàng |
| **Checkout** | Giỏ hàng · form · VietQR / MoMo / Bank / COD |

### Thương mại
- **Cart context** — chọn màu, SL, tổng tiền realtime
- **Order modal + checkout drawer** — UX kiểu Apple (blur, rounded, micro-interaction)
- **VietQR động** — BIN ngân hàng + STK + nội dung `BASEW…` từ env
- **Validate VN phone** (regex nhà mạng) + email
- **Submit order → Google Apps Script** (Sheets backend), follow redirect 302

### Lead & analytics
- Lead form → Google Sheet webhook (fallback local endpoint)
- Demo mode (`VITE_LEAD_FORM_DEMO_MODE`) để demo không spam sheet
- Optional **GA4 + Meta Pixel** (bật bằng flag)

### DX / chất lượng
- **i18n vi/en** sẵn framework
- Dark/light theme hook
- `useInView` scroll reveal
- Error boundary toàn app
- `check-image-dims` script — chặn ảnh quá lớn làm chậm LCP
- Deploy tự động **GitHub Actions → Pages**

---

## Kiến trúc funnel

```text
Visitor
  │
  ├─ Hero / Overview  ─── hiểu sản phẩm
  ├─ Experience       ─── xem demo + mở Tracking_page
  ├─ Add to cart      ─── CartProvider
  └─ Checkout
        ├─ COD
        ├─ VietQR / Bank / MoMo  → PaymentQRModal
        └─ POST Google Apps Script → Sheet đơn hàng
```

Liên kết hệ sinh thái:

```text
Landing_page  ──link──►  Tracking_page (bản đồ)
                 ▲
                 │ API
esp32_sim_neo10 ──POST──► Cloudflare Worker / selfhost-relay
```

---

## Tech stack

| | |
|---|---|
| UI | React 18 · TypeScript · Tailwind · lucide-react |
| Form | react-hook-form · Zod · `@hookform/resolvers` |
| Build | Webpack 5 (dev server `:8082`) · PostCSS · sharp |
| Deploy | GitHub Actions `deploy.yml` → GitHub Pages |

---

## Chạy local

```bash
npm ci
cp .env.example .env
npm run dev
# → http://localhost:8082
```

```bash
npm run type-check
npm run check-images
npm run build
```

### Biến môi trường quan trọng

```env
VITE_TRACKING_WEB_URL=https://thanhvu220809.github.io/Tracking_page/
VITE_DEMO_VIDEO_EMBED_URL=videos/basew-demo.mp4
VITE_LEAD_FORM_DEMO_MODE=false
VITE_GOOGLE_SHEET_WEBHOOK_URL=
VITE_ENABLE_ANALYTICS=false
VITE_GA_MEASUREMENT_ID=
VITE_META_PIXEL_ID=

# Thanh toán
VITE_PAYMENT_BANK_BIN=970422
VITE_PAYMENT_ACCOUNT_NO=
VITE_PAYMENT_ACCOUNT_NAME=
VITE_PAYMENT_BANK_NAME=MB Bank
VITE_PAYMENT_COMPANY_PREFIX=BASEW
```

---

## Cấu trúc

```text
src/
├── components/          # Navbar, Footer, Cart, Order, PaymentQR
│   └── sections/        # Hero · Overview · Experience · Conversion · Checkout
├── hooks/               # theme · cart · inView · address · scrolled
├── i18n/                # vi / en
├── services/
│   ├── forms/           # lead + order (validate + submit)
│   └── analytics/       # GA / Pixel
├── config/env.ts        # single source for env
└── pages/Index.tsx      # composition root
```

---

## Repo liên quan

| Repo | Vai trò |
|---|---|
| [`esp32_sim_neo10`](https://github.com/ThanhVu220809/esp32_sim_neo10) | Firmware SOS · GPS · 4G · FreeRTOS |
| [`Tracking_page`](https://github.com/ThanhVu220809/Tracking_page) | Web map theo dõi thiết bị |
| [`owin-quote-tool`](https://github.com/ThanhVu220809/owin-quote-tool) | Tool báo giá cửa nhôm (project khác) |

---

<p align="center">
  <strong>BA.SEW</strong> — Be Smart Emergency Warning · Landing built to convert
</p>
