# IMPLEMENTATION PLAN: MODUL SKILL MOBILE COFFEE SHOP UI KIT (DUAL-ENGINE)

- **Tanggal Pembuatan**: 2026-10-28
- **Kategori**: frontend/mobile
- **Target Platform**: Dual-Engine (Flutter Dart & React Native / Tailwind)
- **Lokasi Berkas**: `.plan/2026-10-28-coffee-shop-mobile-ui.md` (disimpan di root proyek yang sedang aktif dikerjakan)
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Diperlukan modul keahlian agen frontend mobile di folder `frontend/mobile/coffee-shop-ui` untuk menghasilkan antarmuka aplikasi mobile pemesanan kopi (*Coffee Shop / Delivery Mobile App*) dengan fidelitas visual 1:1 mengacu pada 3 tangkapan layar desain yang dikirimkan pengguna:
  1. **Tangkapan Layar Antarmuka Layar (Screen Flows)**: Onboarding Screen, Home/Catalog Screen, Product Detail Screen, Order Summary Screen, dan Delivery Tracking Screen.
  2. **Styleguide Tipografi**: Font resmi **Sora** (Google Fonts).
  3. **Styleguide Palet Warna (Color Guide)**:
     - `01`: `#C67C4E` (Caramel / Terracotta Brown - Primary Accent)
     - `02`: `#EDD6C8` (Cream / Latte Foam - Secondary Light Tint)
     - `03`: `#313131` (Dark Espresso / Charcoal - Text & Dark Canvas)
     - `04`: `#E3E3E3` (Soft Gray - Borders & Inactive Lines)
     - `05`: `#F9F2ED` (Warm Milk - Background Canvas)
- **Goals**:
  1. Membuat direktori modul skill di `frontend/mobile/coffee-shop-ui/` yang memuat:
     - `skill.json`: Metadata, triggers CLI (`/coffee-ui`, `/coffee-shop`, `/coffee-app`), dan invariant rules.
     - `SKILL.md`: Spesifikasi discovery resmi Antigravity dengan YAML frontmatter.
     - `prompt.md`: System prompt Dual-Engine (Universal Design Tokens Sora & Color Guide + Blueprint Widget Flutter + Blueprint Komponen React Native).
  2. Menyediakan blueprint komponen siap pakai untuk 5 alur layar utama:
     - **Screen 1: Onboarding Screen**: Dark espresso backdrop, coffee beans splash visuals, headline *"Fall in Love with Coffee in Blissful Delight!"*, copy deskripsi, dan tombol CTA *"Get Started"* (`#C67C4E`).
     - **Screen 2: Home / Discovery Screen**: Dropdown pemilih lokasi (*"Location: Bilzen, Tanjungbalai"*), bar pencarian dengan tombol filter kustom, Banner Promo *"Buy one get one FREE"*, horizontal category pills (*All Coffee*, *Machiato*, *Latte*, *Americano*), 2-column coffee grid cards dengan rating bintang, harga, dan tombol tambah `+`, serta floating bottom navigation bar (Home, Favorite, Cart, Notification).
     - **Screen 3: Product Detail Screen**: Hero image kopi dengan rounded corners, nama produk (*"Caffe Mocha"*), hot/ice badge, rating chip 4.8 (230), deskripsi dengan toggle *"Read More"*, size selection pills (`S`, `M` selected, `L`), dan bottom bar sticky dengan harga dan tombol *"Buy Now"*.
     - **Screen 4: Order Summary Screen**: Segmented control toggle (*"Deliver"* vs *"Pick Up"*), kartu alamat pengiriman dengan tombol *Edit Address* dan *Add Note*, ringkasan pesanan dengan counter jumlah (`- 1 +`), banner diskon (*"1 Discount is Applied"*), payment summary breakdown, dan payment method selector (*Cash/Wallet*).
     - **Screen 5: Delivery Tracking Screen**: Peta rute pengiriman, floating bottom card status pengiriman (*"10 minutes left"*, progress delivery bar, profil kurir *"Brooklyn Simmons"*, dan tombol panggil telepon).
  3. Mengadopsi arsitektur Dual-Engine dinamis (bisa menghasilkan kode Flutter Material 3 atau React Native / Tailwind CSS sesuai preferensi pengguna).
- **Out of Scope**:
  - Konfigurasi payment gateway nyata atau GPS backend mapping riil (fokus murni pada layout visual, styling tokens, dan interaktivitas UI state).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Tipografi Resmi**:
  - Google Fonts: **Sora** (`google_fonts: ^6.1.0` di Flutter, `@import url('https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700;800&display=swap')` di React).
- **Palet Warna Resmi (Styleguide)**:
  - Primary `#C67C4E` (`Color(0xFFC67C4E)`)
  - Secondary Tint `#EDD6C8` (`Color(0xFFEDD6C8)`)
  - Dark Charcoal `#313131` (`Color(0xFF313131)`)
  - Light Border `#E3E3E3` (`Color(0xFFE3E3E3)`)
  - Warm Milk Background `#F9F2ED` (`Color(0xFFF9F2ED)`)
- **Dependensi Invariant Rules**:
  - `rule/base_prompt.md`: Prinsip komunikasi direct, zero-fluff, dan anotasi path berkas eksplisit.
  - `rule/project-workflow.md`: Protokol perencanaan dua-fase dan auto-open.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-28-coffee-shop-mobile-ui.md       # [Baru] Dokumen perencanaan modul
└── frontend/
    └── mobile/
        └── coffee-shop-ui/                       # [Baru] Direktori modul skill
            ├── skill.json                        # [Baru] Metadata, triggers (/coffee-ui, /coffee-shop), rules link
            ├── SKILL.md                          # [Baru] Antigravity progressive disclosure
            └── prompt.md                         # [Baru] System prompt Dual-Engine (Tokens Sora & Blueprints)
```

### Rincian Blueprint Kode yang Disediakan Modul:
1. **Universal Design Tokens**:
   - `AppColors`: Definisi 5 warna styleguide dan turunannya.
   - `AppTypography`: Konfigurasi font family **Sora** (Regular 400, SemiBold 600, Bold 700, ExtraBold 800).
   - `AppRadius`: Corner radius `16px` untuk card, `24px` untuk bottom sheet, `rounded-full` untuk pills dan circular buttons.
2. **Flutter Engine Spec (Dart)**:
   - `lib/theme/coffee_theme.dart`: ThemeData dengan GoogleFonts.sora dan ColorScheme kustom.
   - `lib/models/coffee_model.dart`: Model item kopi, kategori, dan pesanan.
   - `lib/views/onboarding_screen.dart`: Layar pembuka aesthetic.
   - `lib/views/home_screen.dart`: Layar katalog utama kopi dengan search, promo banner, dan grid.
   - `lib/views/detail_screen.dart`: Layar detail kopi dengan size selector dan CTA buy now.
   - `lib/views/order_screen.dart`: Layar checkout dengan delivery address dan payment summary.
   - `lib/views/delivery_screen.dart`: Layar tracking kurir dan status ETA.
3. **React / React Native Engine Spec (TypeScript & Tailwind)**:
   - `src/theme/colors.ts`: Token warna styleguide.
   - `src/components/OnboardingScreen.tsx`
   - `src/components/HomeScreen.tsx`
   - `src/components/DetailScreen.tsx`
   - `src/components/OrderScreen.tsx`
   - `src/components/DeliveryScreen.tsx`

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Antigravity Indexing (`skill.json` & `SKILL.md`)**
  - [x] Pembuatan `frontend/mobile/coffee-shop-ui/skill.json` dengan triggers `/coffee-ui`, `/coffee-shop`, `/coffee-app`.
  - [x] Pembuatan `frontend/mobile/coffee-shop-ui/SKILL.md` dengan frontmatter YAML spesifikasi Coffee Shop Mobile UI Kit.
- [x] **Fase 2: Perumusan System Prompt Dual-Engine (`prompt.md`)**
  - [x] Pendefinisian persona *Senior Mobile UI/UX Architect (Coffee Shop Design System Specialist)*.
  - [x] Spesifikasi token resmi: Palet 5 warna Nam Design dan font **Sora**.
  - [x] Blueprint widget Flutter lengkap tanpa *placeholder* (Onboarding, Home, Detail, Order, Delivery).
  - [x] Blueprint komponen React / React Native lengkap tanpa *placeholder*.
  - [x] Konvensi penulisan: Null safety, `const` constructor, path file eksplisit (`// lib/...` dan `// src/...`).
- [x] **Fase 3: Validasi Modul & Registrasi Katalog**
  - [x] Pembaruan checklist di `.plan/2026-10-28-coffee-shop-mobile-ui.md`.
  - [x] Registrasi modul baru di `README.md` pada kategori `frontend/mobile`.

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Font Sora belum terpasang secara lokal di mesin pengembang.
- **Mitigasi**: Di Flutter, gunakan paket resmi `google_fonts: ^6.1.0` yang otomatis mengunduh atau menyematkan font Sora. Di React/Web, sertakan tag CDN Google Fonts atau Tailwind font-family fallback (`['Sora', 'sans-serif']`).

---

> **COMPLETED**: Seluruh tahapan rencana implementasi modul Dual-Engine Coffee Shop Mobile UI Kit telah selesai dieksekusi. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` aktif di `frontend/mobile/coffee-shop-ui/`.

