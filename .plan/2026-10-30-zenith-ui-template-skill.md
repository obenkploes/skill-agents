# IMPLEMENTATION PLAN: MODUL SKILL ZENITH UI TEMPLATE & DESIGN SYSTEM

- **Tanggal Pembuatan**: 2026-10-30
- **Kategori**: frontend / ui-system
- **Status**: Menunggu Persetujuan Pengguna (Approval Gate)
- **Estimasi Kompleksitas**: Sedang - Tinggi (Multi-Engine UI Specification)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Pengguna membutuhkan modul skill template antarmuka pengguna (UI) baru yang dibuat berdasarkan 5 tangkapan layar (screenshot) sistem dashboard dan aplikasi modern bernama **Zenith**. Modul skill ini dirancang sebagai acuan arsitektur antarmuka komprehensif yang agnostik terhadap teknologi styling, sehingga agen AI dapat mereferensikannya untuk menghasilkan kode UI yang konsisten dan pixel-perfect menggunakan:
1. **Native Modern CSS** (CSS Variables / Custom Properties, Flexbox, Grid, `[data-theme]` / `color-scheme`).
2. **Tailwind CSS** (v3/v4 utility classes, `dark:` modifiers, arbitrary values, responsive grid).
3. **Bootstrap 5** (v5.3+ CSS variables, `data-bs-theme="dark"`, layout grid, card, badges, tables).
4. Framework UI apapun (React, Vue, Svelte, Blade/Laravel, Django/Flask, HTML5 Vanilla).

### Analisis 5 Tangkapan Layar (Screenshot Deconstruction)
1. **Screenshot 1: SaaS Analytics Dashboard (Light Mode)**
   - **Header / Top Bar**: Logo isometric 3D cube + label "Zenith", search box interaktif dengan shortcut keyboard `Ctrl+K`, status indikator online (green pill `● 1 online`), dropdown tenant/organisasi (`AH Acme Holdings ⌵`), tombol notifikasi dengan counter badge (`15`), switcher tema (sun icon), profil pengguna (`DU demo ⌵`).
   - **Sidebar Navigasi**: Hierarki menu terkelompok (`DASHBOARDS`: Overview, Analytics, CRM, eCommerce, SaaS [aktif dengan background pill halus]; `COMMERCE`: Orders, Customers, Invoices, Products; `APPS`: Mail, Chat, Calendar, Kanban, Projects, Team, Activity; Footer profil `Demo User Admin` + tombol collapse/logout).
   - **Header Konten & Breadcrumb**: `Dashboards > SaaS`, Title `SaaS`, subtitle `MRR, growth, and subscriber health for your subscription business.`.
   - **4 Kartu KPI Metrik (Stat Cards)**:
     - MRR: `$48.2K`, tren `+0.4% from last month` (hijau), ikon `$` dalam container rounded hijau muda, sparkline hijau di bagian bawah.
     - Active Users: `2,847`, tren `+12.6% from last month` (biru), ikon user group dalam container rounded cyan muda, sparkline biru.
     - Churn Rate: `3.2%`, tren `-0.5% from last month` (ungu), ikon user dalam container rounded ungu muda, sparkline ungu.
     - Trial Conversion: `24.8%`, tren `+2.3% from last month` (oranye), ikon badge dalam container rounded oranye muda, sparkline oranye.
   - **Bagian Grafik Utama (Grid 2 Kolom)**:
     - Kiri (65%): `Revenue Growth` (MRR & ARR over the last 12 months) — dual line/spline chart dengan legend titik warna teal & hijau.
     - Kanan (35%): `Subscription Plans` (Active subscribers by plan) — Donut chart dengan total `2,847` di tengah dan legend 4 kategori (`Free`, `Starter`, `Pro`, `Enterprise`).
   - **Bagian Bawah (Grid 2 Kolom)**:
     - Kiri: 
       - Tabel `Marketing Channels` (Channel, Visitors, Signups, Conv %, CPA).
       - Tabel `Recent Signups` (Avatar inisial bulat, nama, email, plan pill badges, tanggal pendaftaran).
     - Kanan:
       - Bar chart `User Growth` (Pertumbuhan 6 bulan terakhir dengan rounded bars).
       - Widget `Growth Targets` (Target kuartal: MRR Target, Active Users, Trial → Paid Conv lengkap dengan perbandingan angka dan progress bar berwarna).

2. **Screenshot 2: SaaS Analytics Dashboard (Dark Mode)**
   - Desain yang sama persis dalam palet **Dark Mode** modern kelas enterprise:
     - Background canvas: `#0B0F17` / `#0D1117`.
     - Card surface: `#111827` / `#161B22` dengan border halus `#1F2937`.
     - Teks kontras tinggi `#F9FAFB` (headings) dan muted `#9CA3AF`.
     - Aksen warna grafik dan badge tetap vibrant dan eye-friendly.

3. **Screenshot 3: Messaging / Chat Workspace Layout**
   - Layout split multi-kolom: Sidebar utama + Kolom percakapan (`CHATS` dengan tombol `+` New Chat) + Kolom utama pesan.
   - List item chat: Avatar/inisial, nama kontak (`Jennifer Valenzuela`, `Luis Fowler`, `Lisa Rivera`), timestamp (`Oct 29`), cuplikan pesan teks, badge unread pesan bulat hitam dengan counter (`1`).
   - Empty state pane: Ikon speech bubble minimalis dan instruksi `Pick a conversation to start chatting.`.

4. **Screenshot 4: Charts Showcase (Gallery of ApexCharts Variants)**
   - Menu `SHOWCASE > Charts` aktif.
   - Grid galeri 2 kolom memuat ragam visualisasi data analitik:
     1. Bar Chart (Vertikal dengan nilai batang).
     2. Line Chart (Multi-line comparison: Sessions vs Pageviews).
     3. Area Chart (Gradient fill di bawah kurva dengan titik penanda data).
     4. Donut Chart (Distribusi persentase multi-segmen: Direct, Search, Social, Referral).
     5. Radial / Concentric Ring Chart (Progress lingkaran bertingkat).
     6. Heatmap Grid Chart (Matriks hari Senin–Minggu vs Minggu W1–W4 dengan intensitas warna).
     7. Scatter Plot (Sebaran titik koordinat X-Y).
     8. Mixed Chart (Kombinasi Line + Bar chart).

5. **Screenshot 5: 503 Service Unavailable / Error & Status Screen**
   - Layar status error minimalis berpusat di tengah layar (*centered card*).
   - Branding Zenith di bagian atas.
   - Angka kode status besar warna merah menyala `503`.
   - Judul `Service Unavailable` dan pesan penjelas ramah pengguna.
   - Box alert insiden sistem: Ikon denyut/warning, label `Incident detected`, kode referensi tiket `INC-2026-0042`.
   - Tombol aksi: CTA Utama `Retry now` (solid dark) dan CTA Sekunder `Contact support` (outline/ghost).

### Goals
1. Membuat direktori modul skill terstandar di `skills/zenith-ui/` yang berisi:
   - `skill.json`: Metadata, triggers (`/zenith-ui`, `/zenith-dashboard`, `/saas-ui`, `/ui-template`), category `frontend/ui-system`, dependencies, dan aturan.
   - `SKILL.md`: Ringkasan modul, blueprint kapabilitas, aturan invariant, dan mandatory planning protocol.
   - `prompt.md`: Dokumentasi acuan sistem desain lengkap (Design Tokens, Multi-Engine Styling Guide: Native CSS, Tailwind CSS, Bootstrap 5, serta kode blueprint komponen siap pakai untuk setiap layar).
2. Memperbarui `plugin.json` dan `README.md` workspace untuk mendaftarkan skill baru `zenith-ui`.

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI

### Styling & UI Stack Agnostic
Modul ini menyajikan panduan implementasi untuk 3 paradigma styling utama:
- **Native CSS**:
  - CSS Custom Properties (`:root` dan `[data-theme="dark"]`).
  - CSS Flexbox & CSS Grid Layout (Auto-fit, Minmax).
  - Modern Reset & Media Queries (`prefers-color-scheme`).
- **Tailwind CSS**:
  - Tailwind v3.4+ / v4.0+.
  - Utility classes: layout (`flex`, `grid`, `col-span-*`), typography, elevation, dark mode (`dark:*`).
- **Bootstrap 5**:
  - Bootstrap v5.3+ memanfaatkan variabel CSS bawaan, `data-bs-theme="light|dark"`, utilities, card, tables, progress, badges.
- **Ikonografi & Visualisasi**:
  - Ikon: Lucide Icons, Heroicons, FontAwesome, Bootstrap Icons, atau SVG inline.
  - Grafik: ApexCharts, Chart.js, Recharts, atau representasi SVG semantik.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-30-zenith-ui-template-skill.md  # [Baru] Dokumen perencanaan implementasi
├── skills/
│   └── zenith-ui/                              # [Baru] Direktori modul skill Zenith UI
│       ├── skill.json                          # [Baru] Metadata skill & triggers
│       ├── SKILL.md                            # [Baru] Ringkasan skill & instruksi cepat
│       └── prompt.md                           # [Baru] Comprehensive System Prompt & Multi-Engine UI Blueprint
├── plugin.json                                 # [Update] Registrasi versi modul skill
└── README.md                                   # [Update] Dokumentasi katalog modul skill
```

### Rincian Token Desain (Zenith Design Tokens)
- **Palet Warna Inti (Theme Palette)**:
  - **Brand / Accent**: `#0F172A` (Slate Dark / Primary Light) & `#3B82F6` / `#2563EB` (Interactive Blue)
  - **Success / Trend Up / Online**: `#10B981` (Emerald Green)
  - **Info / Active Users**: `#06B6D4` / `#0EA5E9` (Sky Cyan)
  - **Warning / Trial / Conversion**: `#F59E0B` (Amber Orange)
  - **Purple / Churn**: `#8B5CF6` (Violet Purple)
  - **Danger / Error 503**: `#EF4444` / `#DC2626` (Red)
- **Background & Canvas**:
  - Light Canvas: `#F8FAFC` (Slate-50) | Card Surface: `#FFFFFF` | Border: `#E2E8F0` (Slate-200)
  - Dark Canvas: `#0B0F17` (Deep Obsidian) | Card Surface: `#111827` (Gray-900) | Border: `#1F2937` (Gray-800)
- **Typography & Elevation**:
  - Font Family: `Inter`, `Plus Jakarta Sans`, atau `system-ui, -apple-system, sans-serif`
  - Radius: `rounded-xl` (12px) untuk kartu/modal, `rounded-lg` (8px) untuk tombol/input/icon-box, `rounded-full` untuk badge pill dan avatar.
  - Shadow: `shadow-sm` untuk kartu standar, `shadow-md` untuk dropdown/flyout.

### 5 Komponen / Layar Blueprint yang Didokumentasikan
1. **Master Layout Shell**: Top Navbar dengan search `Ctrl+K`, quick status, organization switcher, notification bell, dark/light toggle, profile menu, serta Collapsible Sidebar terkelompok.
2. **SaaS Analytics Dashboard**: 4 KPI Cards dengan sparkline dinamis, Revenue Growth Dual-line Chart, Subscription Plans Donut Chart, Marketing Channels Table, Recent Signups List Table, User Growth Bar Chart, dan Growth Targets Progress Widget.
3. **Chat & Messaging Screen**: Multi-column chat list, conversation snippet, badge unread, dan empty conversation state.
4. **Charts Showcase Gallery**: Galeri 8 varian visualisasi analitik (Bar, Line, Area, Donut, Radial, Heatmap, Scatter, Mixed).
5. **System / Status 503 Service Unavailable**: Layar error terpusat dengan incident card box dan action CTA.

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [ ] **Fase 1: Konfigurasi Metadata & Direktori (`skills/zenith-ui/skill.json`)**
  - [ ] Pembuatan folder `skills/zenith-ui`.
  - [ ] Pembuatan file `skill.json` memuat properti `name: "zenith-ui"`, `displayName: "Zenith UI Template & Design System Specialist"`, kategori `frontend/ui-system`, triggers `/zenith-ui`, `/zenith`, `/dashboard-template`, `/saas-ui`, dependensi, dan aturan.
- [ ] **Fase 2: Pembuatan Entrypoint `SKILL.md`**
  - [ ] Penulisan frontmatter YAML terstandar dengan `MANDATORY WORKFLOW`.
  - [ ] Deskripsi peran, kemampuan utama, invariant rules, dan daftar layar/komponen yang didukung.
- [ ] **Fase 3: Penyusunan Comprehensive Design System & Code Blueprint (`prompt.md`)**
  - [ ] Bagian 1: Identitas & Filosofi Desain Zenith UI.
  - [ ] Bagian 2: Design Tokens (Color, Typography, Spacing, Radius, Shadow) lengkap untuk Light & Dark Mode.
  - [ ] Bagian 3: Panduan Multi-Engine Styling:
    - *Engine A: Native CSS* (CSS variables, semantic HTML5 structure, responsive grid, zero-dependency).
    - *Engine B: Tailwind CSS* (utility classes, dark: variants, arbitrary values, responsive modifiers).
    - *Engine C: Bootstrap 5* (data-bs-theme, card, badges, tables, progress, custom styling).
  - [ ] Bagian 4: Blueprint Komponen Lengkap untuk 5 Layar (Master Shell, SaaS Dashboard, Chat UI, Charts Showcase, 503 Status Screen).
- [ ] **Fase 4: Integrasi Proyek & Dokumentasi (`README.md` & `plugin.json`)**
  - [ ] Update `README.md` untuk mencantumkan skill `zenith-ui` pada tabel daftar skill frontend.
  - [ ] Verifikasi konsistensi struktur dan linting.

---

## 5. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Variasi sintaks dan kapabilitas antara Native CSS, Tailwind CSS, dan Bootstrap 5 dapat menyebabkan inkonsistensi visual bila tidak distandarkan.
- **Mitigasi**: Menggunakan *Design Tokens Terpadu* sebagai landasan (single source of truth untuk warna, radius, dan tipografi). Memberikan contoh konversi ekuivalen yang jelas antara variabel Native CSS (`--zenith-primary`), kelas Tailwind (`bg-[#...]` / `bg-emerald-500`), dan Bootstrap (`--bs-primary` / class `bg-primary`).
- **Potensi Risiko**: Kompleksitas grafik visual pada chart showcase (ApexCharts).
- **Mitigasi**: Menyertakan konfigurasi ApexCharts standar (JSON option/series) yang dapat langsung dipasang baik di lingkungan JavaScript murni, React, Vue, maupun HTML static CDN.

---

> **STATUS SAAT INI**: Dokumen rencana implementasi ini telah selesai disusun. Menunggu persetujuan pengguna sebelum memulai Fase 1.

