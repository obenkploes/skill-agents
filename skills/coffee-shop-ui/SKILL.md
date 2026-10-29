---
name: coffee-shop-ui
description: >-
  Spesialis arsitektur dan perancangan antarmuka aplikasi mobile pemesanan kopi (Coffee Shop / Delivery Mobile App)
  dengan arsitektur Dual-Engine dinamis (Flutter Dart & React / React Native) mengacu pada styleguide resmi Nam Design.
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating or writing any code.
---

# Coffee Shop Mobile UI Kit Specialist (Dual-Engine)

Modul keahlian antarmuka mobile dinamis yang mendukung pembuatan komponen dan layar aplikasi pemesanan dan pengiriman kopi modern (*Coffee Delivery App*) baik di lingkungan **Flutter (Dart)** maupun **React / React Native (TypeScript & Tailwind)**.

Panduan lengkap, design tokens resmi (Warna Nam Design & Font Sora), serta blueprint komponen siap pakai tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menulis, memodifikasi, atau menghasilkan kode komponen/layar apapun:
1. **Analisis Kebutuhan**: Pahami layar dan interaksi yang diminta.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menulis atau mengenerate kode implementasi sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).

## Alur Layar yang Didukung (5 Core Screens)
1. **Onboarding Screen**:
   - Hero dark espresso backdrop, visual biji kopi aesthetic.
   - Headline: *"Fall in Love with Coffee in Blissful Delight!"*.
   - Copy deskripsi pembuka dan tombol utama *"Get Started"* warna terracotta (`#C67C4E`).
2. **Home / Discovery Screen**:
   - Header pemilih lokasi (*"Location: Bilzen, Tanjungbalai"*).
   - Search bar dengan tombol filter kustom terintegrasi.
   - Banner Promo *"Buy one get one FREE"* dengan visual gelas es kopi.
   - Horizontal category selector pills (*All Coffee*, *Machiato*, *Latte*, *Americano*).
   - 2-Column coffee product grid cards (*Caffe Mocha*, *Flat White*) lengkap dengan chip rating bintang, harga, dan tombol tambah `+`.
   - Floating bottom navigation bar (Home, Favorite, Cart, Notification).
3. **Product Detail Screen**:
   - Hero image kopi melengkung dengan tombol kembali dan ikon favorit.
   - Judul produk (*Caffe Mocha*), subtitle *Ice/Hot*, dan chip rating 4.8 (230 ulasan).
   - Deskripsi kopi dengan toggle expandable *"Read More"*.
   - Size selection pills (`S`, `M` aktif, `L`).
   - Sticky bottom action bar memuat harga dan tombol *"Buy Now"*.
4. **Order Summary Screen**:
   - Segmented toggle switch (*Deliver* vs *Pick Up*).
   - Kartu alamat pengiriman (*Jl. Kpg Sutoyo*) dengan tombol *Edit Address* dan *Add Note*.
   - Item counter pesanan (`- 1 +`).
   - Banner diskon voucher (*"1 Discount is Applied"*).
   - Payment summary breakdown (harga item, ongkos kirim diskon, total biaya).
   - Payment method selector (*Cash/Wallet*) dan tombol konfirmasi pesan.
5. **Delivery Tracking Screen**:
   - Tampilan rute peta pengiriman visual.
   - Floating bottom status card: estimasi waktu (*"10 minutes left"*), delivery progress bar, profil kurir (*Brooklyn Simmons*), dan tombol panggilan telepon langsung.

