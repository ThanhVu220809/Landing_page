# BA.SEW — Landing Page

### Thiết bị cảnh báo khẩn cấp thông minh · landing bán hàng end-to-end

<p align="center">
  <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind" />
  <img src="https://img.shields.io/badge/Webpack_5-8DD6F9?style=for-the-badge&logo=webpack&logoColor=black" alt="Webpack" />
  <img src="https://img.shields.io/badge/Zod-3E67B1?style=for-the-badge" alt="Zod" />
</p>

<p align="center">
  <strong>BE SMART EMERGENCY WARNING</strong><br/>
  <sub>One-page conversion · giỏ hàng · VietQR · lead · analytics</sub>
</p>

---

## ✨ Một dòng

Landing thương mại cho **BA.SEW** — thiết bị SOS + GPS: giới thiệu sản phẩm, demo trải nghiệm bản đồ, bỏ vào giỏ, checkout COD / chuyển khoản — không cần app, ship toàn quốc.

---

## 🎯 Sản phẩm trên landing

<table>
<tr>
<td width="33%" align="center">

### 🆘 SOS một nút
SMS + gọi điện cascade  
chia sẻ vị trí ngay

</td>
<td width="33%" align="center">

### 📍 GPS realtime
Theo dõi trên web map  
**không cài app**

</td>
<td width="33%" align="center">

### 👨‍👩‍👧‍👦 Cho người thân
Người lớn tuổi · trẻ em  
đi một mình / gia đình

</td>
</tr>
</table>

**Giá niêm yết:** 400.000đ / thiết bị · **miễn phí vận chuyển** toàn quốc

---

## 🛒 Funnel bán hàng

```text
  HERO          OVERVIEW        EXPERIENCE       GIỎ HÀNG        CHECKOUT
 ──────►       ──────►         ──────►         ──────►         ──────►
  Hook + CTA    Là gì / ai      Video + map      Màu · SL · $     VietQR / COD
                dùng được       deep-link        realtime         → đơn vào Sheet
```

| Bước | Người dùng thấy | Hệ thống làm |
|------|-----------------|--------------|
| **Hero** | Headline, bullet, giá, CTA | First impression |
| **Overview** | 3 đối tượng + 3 bước hoạt động | Education |
| **Experience** | Video demo + link bản đồ live | Trust / try |
| **Đặt hàng** | Chọn màu, số lượng | Cart state |
| **Checkout** | Form + QR thanh toán | Validate · submit order |
| **Lead** | Form quan tâm nhanh | Webhook Google Sheet |

---

## 💳 Thanh toán & đơn hàng

| Phương thức | Chi tiết |
|-------------|----------|
| **VietQR** | QR động theo BIN · STK · nội dung `BASEW…` |
| **Chuyển khoản** | Bank config qua env |
| **MoMo** | QR / SĐT (optional) |
| **COD** | Thanh toán khi nhận |

- Validate **SĐT Việt Nam** (đầu số nhà mạng) + email  
- Order → **Google Apps Script / Sheet** (backend không server riêng)  
- Demo mode tắt spam sheet khi trình diễn  

---

## 🎨 UX / UI

| | |
|--|--|
| Phong cách | Apple-like: blur, rounded 2xl, micro-scale |
| Theme | Light / dark ready |
| Ngôn ngữ | **i18n vi · en** |
| Motion | Scroll reveal khi section vào viewport |
| Cart | Dropdown túi xách + drawer checkout |
| Safety | Error boundary toàn app · help modal |

---

## 🏗️ Công nghệ

```text
┌──────────────────────────────────────────────┐
│  React 18  ·  TypeScript  ·  Tailwind CSS    │
│  react-hook-form  ·  Zod  ·  lucide-react    │
└────────────────────┬─────────────────────────┘
                     │
        Lead / Order webhook · GA4 · Meta Pixel
                     │
┌────────────────────▼─────────────────────────┐
│  Google Sheets (Apps Script)                 │
│  Optional analytics IDs                      │
│  Deep-link → Tracking Map                    │
└──────────────────────────────────────────────┘
                     │
┌────────────────────▼─────────────────────────┐
│  Webpack 5 production build                  │
│  GitHub Actions → GitHub Pages               │
└──────────────────────────────────────────────┘
```

### Stack

| Tầng | Công nghệ |
|------|-----------|
| UI | React 18 · TypeScript · Tailwind · lucide |
| Form | react-hook-form · Zod resolvers |
| Build | Webpack 5 · PostCSS · image budget check |
| Commerce | Cart context · VietQR · multi payment |
| Growth | GA4 · Meta Pixel (flag) · lead capture |
| Deploy | GitHub Actions → Pages |

---

## 🌐 Hệ sinh thái BA.SEW

Landing không đứng một mình — nối với phần cứng & map:

| | Vai trò |
|--|---------|
| **[Firmware ESP32](https://github.com/ThanhVu220809/esp32_sim_neo10)** | SOS · GPS · 4G · FreeRTOS |
| **[Tracking Map](https://github.com/ThanhVu220809/Tracking_page)** | Bản đồ live người thân mở trên web |
| **Landing (repo này)** | Bán hàng · education · checkout |

```text
  Thiết bị ──POST──► Cloud ──API──► Bản đồ web
                                      ▲
  Landing ──── “Trải nghiệm ngay” ────┘
  Landing ──── đơn hàng ──► Google Sheet
```

---

## 🚀 Deploy

| | |
|--|--|
| Platform | GitHub Pages |
| Pipeline | push `main` → install → build → deploy |
| Config | Bank / Sheet / analytics qua env secrets |

---

<p align="center">
  <sub><strong>BA.SEW</strong> — Be Smart Emergency Warning · built to convert</sub>
</p>
