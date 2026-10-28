# IMPLEMENTATION PLAN: MODUL SKILL MOBILE UI FOOD DELIVERY & CHEF MARKETPLACE (DUAL-ENGINE)

- **Tanggal Pembuatan**: 2026-10-28
- **Kategori**: frontend/mobile
- **Lokasi Berkas**: `.plan/2026-10-28-food-delivery-mobile-ui.md` (disimpan di root repositori aktif)
- **Status**: Selesai Diimplementasikan (Completed)
- **Estimasi Kompleksitas**: Tinggi (Mencakup 2 domain aplikasi terintegrasi: Customer App & Chef/Partner App dengan 24+ layar)

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Pengguna membutuhkan modul keahlian frontend mobile pada folder `frontend/mobile/food-delivery-ui` untuk memodelkan secara visual 1:1 seluruh antarmuka aplikasi pesan-antar makanan modern (*Food Delivery & Chef Marketplace Platform*) berdasarkan 5 gambar tangkapan layar yang dikirimkan.
- **Goals**:
  1. Menyusun modul skill baru di `frontend/mobile/food-delivery-ui/` dengan berkas:
     - `skill.json`: Metadata, triggers CLI (`/food-ui`, `/food-delivery`, `/chef-app`, `/restaurant-ui`), dependensi, dan tautan invariant rules.
     - `SKILL.md`: Spesifikasi discovery resmi Antigravity dengan YAML frontmatter.
     - `prompt.md`: System prompt spesialis UI/UX mobile, design tokens (warna oranye energetic `#FF7622`, dark charcoal `#121223`, font modern), serta blueprint komponen siap pakai untuk Flutter (Dart) dan React Native / React Tailwind.
  2. Menyediakan cakupan 2 ekosistem aplikasi terpadu:
     - **A. Customer Food Delivery App (14+ Screens)**:
       - *Splash & Onboarding (3 slides)*: "All your favorites", "Order from chosen chef", "Free delivery offers" dengan ilustrasi vektor, pagination dots, dan tombol Next/Get Started.
       - *Autentikasi & Verifikasi*: Layar Log In (dark header wave pattern, social login Facebook/Twitter/Apple), Sign Up, 4-digit OTP Verification dengan custom numeric keypad, dan Forgot Password.
       - *Location Access*: Dialog izin akses lokasi dengan visual circular map dan pin oranye.
       - *Home / Discovery*: Header lokasi pengantaran (*Deliver to: Halal Lab office*) dengan cart badge counter, Search bar, Category selector dinamis (Pills vs Cards), Open Restaurants card (Rating, Free delivery, estimasi 20 min).
       - *Search & Filter*: Recent keywords, suggested restaurants, popular fast food, serta Filter Bottom Sheet (Offers, Delivery time, Pricing $, Rating).
       - *Restaurant & Food Details*: Cover banner, category tabs, detail hidangan dengan curved hero image, favorite heart icon, size selector (10", 14", 16"), ingredients icon badges, price & quantity stepper (`- 2 +`).
       - *Promo Voucher Popup*: Pop-up modal promo diskon (*"Hurry Offers! #1243CD2 Get 25% discount"*).
       - *Cart & Checkout*: Daftar pesanan dengan tombol delete & stepper, Delivery address card (*Edit*), pricing breakdown, dan tombol *Place Order*.
       - *Payment Flow*: Pilihan metode bayar (Cash, Visa, Mastercard, Paypal), Card preview gradient card, dan form Add Card (Card holder, Number, Expiry, CVC).
       - *Order Success*: Layar perayaan (*Congratulations!*) dengan ilustrasi dompet & konfeti serta tombol *Track Order*.
       - *Delivery Tracking*: Peta rute real-time, polyline rute oranye, indikator posisi kurir, dan bottom card info restoran & detail pesanan.
     - **B. Chef / Merchant Partner App (10 Screens)**:
       - *Chef Dashboard*: Stat cards KPI (Running Orders, Order Request), grafik garis *Total Revenue* dengan toggle filter periode harian, rating ulasan (4.9), dan popular items.
       - *Running Orders List*: Bottom sheet / kartu pesanan masuk lengkap dengan tombol aksi *Done* dan *Cancel*.
       - *Menu Management (My Food List)*: Tab filter kategori (*All*, *Breakfast*, *Lunch*, *Dinner*), daftar menu hidangan chef, dan form *Add New Food Item* (upload foto/video, harga, opsi Pick up / Delivery, multi-select ingredients badges).
       - *Food Details (Chef View)*: Tampilan detail menu dari perspektif koki dengan tombol edit.
       - *Notifikasi & Pesan Pelanggan*: Tab toggle ganda antara *Notifications* dan *Messages (3)* dengan avatar pelanggan dan thread chat interaktif.
       - *Ulasan Pelanggan (Reviews)*: Kartu review pelanggan dengan rating bintang dan komentar testimonial.
       - *Profil Koki & Penarikan Saldo (Withdrawal)*: Kartu header oranye *Available Balance ($500.00)* dengan tombol *Withdraw*, menu navigasi akun, dan dialog modal sukses penarikan (*Withdraw Successful*).
- **Out of Scope**:
  - Integrasi backend gateway pembayaran riil (Stripe/Midtrans) dan Google Maps API live key (fokus pada arsitektur komponen visual, token desain, state management mock, dan struktur layout UI).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Platform Frontend Target**:
  - **Flutter**: Dart SDK `>=3.19.0`, dependensi `google_fonts: ^6.1.0`, `flutter_svg: ^2.0.9`.
  - **React Native / React Web**: React `>=18.0.0`, Tailwind CSS `>=3.4.0`, `lucide-react` / `lucide-react-native`.
- **Design Tokens Resmi**:
  - `primary`: `#FF7622` (Vibrant Foodie Orange)
  - `primaryLight`: `#FFE8DB` (Soft Orange Tint)
  - `secondaryDark`: `#121223` / `#181C2E` (Midnight Charcoal Header)
  - `background`: `#FFFFFF` & `#F6F6F6` (Neutral Canvas)
  - `cardBackground`: `#FFFFFF` dengan shadow lembut (`0 8px 24px rgba(0,0,0,0.06)`)
  - `accentYellow`: `#FFA100` (Star rating & badges)
  - `textPrimary`: `#181C2E`
  - `textSecondary`: `#646982` / `#A0A5BA`
  - `success`: `#059669` / `#22C55E`
  - `danger`: `#E53935`
- **Aturan Invariant**:
  - `rule/base_prompt.md`: Komunikasi direct, zero fluff, kode produksi lengkap tanpa placeholder pemalas.
  - `rule/project-workflow.md`: Protokol perencanaan dua fase dan auto-open berkas rencana.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-28-food-delivery-mobile-ui.md   # [Baru] Dokumen perencanaan modul
└── frontend/
    └── mobile/
        └── food-delivery-ui/                   # [Baru] Direktori modul skill mobile
            ├── skill.json                      # [Baru] Metadata, triggers, dan referensi rule
            ├── SKILL.md                        # [Baru] Antigravity native progressive disclosure
            └── prompt.md                       # [Baru] Design tokens & blueprint Flutter & React
```

### Rincian Blueprint Modul:
1. **`skill.json`**:
   - `name`: `food-delivery-ui`
   - `category`: `frontend/mobile`
   - `displayName`: `Food Delivery & Chef Marketplace Mobile UI Kit (Dual-Engine)`
   - `triggers`: `commands` (`["/food-ui", "/food-delivery", "/chef-app", "/restaurant-ui"]`), `keywords` (`["food delivery ui", "chef app mobile", "restaurant mobile ui", "foodie flutter", "food order app", "halal lab food ui", "food delivery cart", "chef dashboard mobile"]`).
2. **`SKILL.md`**:
   - Dokumentasi ringkas cakupan Customer App dan Chef Partner App.
   - Design tokens palet warna `#FF7622` dan dark navy `#121223`.
3. **`prompt.md`**:
   - Token desain universal (Color, Typography, Border Radius, Shadow).
   - Blueprint komponen Flutter (Dart) siap pakai: Custom bottom navbar dengan circular action button, Food item card dengan stepper, Chef metric card, dan OTP input grid.
   - Blueprint komponen React / React Native (TypeScript + Tailwind CSS): Dashboard layout, Order item card, Payment selector, dan Modal pop-up promo.

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Antigravity Indexing (`skill.json` & `SKILL.md`)**
  - [x] Pembuatan `frontend/mobile/food-delivery-ui/skill.json` dengan triggers `/food-ui`, `/food-delivery`, `/chef-app`.
  - [x] Pembuatan `frontend/mobile/food-delivery-ui/SKILL.md` dengan frontmatter YAML spesifikasi Customer App & Chef App.
- [x] **Fase 2: Perumusan System Prompt & Blueprints Dual-Engine (`prompt.md`)**
  - [x] Pendefinisian persona *Senior Mobile UI/UX Architect (Food Delivery Specialist)*.
  - [x] Spesifikasi design tokens lengkap (Hex colors, font pairings, sizing).
  - [x] Implementasi blueprint widget Flutter (Dart): Customer Home, Food Detail dengan Size & Ingredients, Chef Dashboard dengan Chart & Bottom Sheet.
  - [x] Implementasi blueprint komponen React / React Native (TSX + Tailwind): Cart Screen, Payment Selector, Add Card Form, dan Promo Modal.
- [x] **Fase 3: Validasi Modul & Registrasi Katalog**
  - [x] Pembaruan checklist di `.plan/2026-10-28-food-delivery-mobile-ui.md`.
  - [x] Registrasi modul baru di `README.md` pada tabel katalog skill kategori `frontend/mobile`.

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Banyaknya variasi layar (24+ layar) dapat membuat prompt terlalu padat jika tidak distrukturkan dengan modular.
- **Mitigasi**: Pisahkan peran visual ke dalam 2 domain tegas: **Customer App Architecture** dan **Chef/Merchant App Architecture**, serta sediakan komponen atomik (*shared tokens, buttons, inputs, cards*) yang dapat dipakai ulang di kedua sisi platform.

---

> **STATUS IMPLEMENTASI**: Seluruh berkas modul (`skill.json`, `SKILL.md`, `prompt.md`) telah selesai diimplementasikan, diverifikasi, dan didaftarkan ke dalam katalog repositori. Modul siap digunakan secara aktif.

