# IMPLEMENTATION PLAN: MODUL SKILL FRONTEND TAILMIND (TAILADMIN DASHBOARD SPECIALIST)

- **Tanggal Pembuatan**: 2026-10-27
- **Kategori**: frontend
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Dibutuhkan modul keahlian agen frontend (`frontend/tailmind`) untuk menghasilkan, merekayasa, dan memelihara antarmuka admin dashboard berbasis Tailwind CSS sesuai spesifikasi visual pada tangkapan layar antarmuka *TailAdmin*. Modul ini harus mampu menghasilkan komponen React/TypeScript siap produksi dengan standar layout, palet warna, tipografi, visualisasi chart, dan interaktivitas yang identik.
- **Goals**:
  1. Menyediakan modul skill modular di `frontend/tailmind/` yang terdiri dari `skill.json` (metadata & CLI triggers) dan `prompt.md` (spesifikasi arsitektural Tailwind & dashboard design system).
  2. Memetakan seluruh hierarki UI dari screenshot TailAdmin: Top Navbar (search shortcut `⌘K`, dark mode toggle, notification, user profile), Sidebar Navigation (accordion, nested sub-items, badge status `NEW`), dan Main Dashboard Grid (KPI Metric Cards, Monthly Target semi-gauge chart, Monthly Sales bar chart, serta Statistics area chart dengan filter periode).
  3. Menerapkan konvensi Clean Component Architecture (React 19, Tailwind CSS v3/v4, TypeScript, Lucide Icons, dan ApexCharts/Recharts) dengan dukungan penuh Dark Mode (`dark:` classes).
- **Out of Scope**:
  - Implementasi backend endpoint riil / database persistence (fokus pada frontend skill directives, mock state, dan UI components).
  - Pemasangan package npm secara global di workspace saat ini (hanya mencatat dependensi yang direkomendasikan).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Package / Library Terkait (Frontend Stack)**:
  - `react` (^19.0.0) & `react-dom`: Library inti UI.
  - `tailwindcss` (^3.4.0 atau ^4.0.0): Utility-first CSS framework.
  - `lucide-react` atau `@heroicons/react`: Ikonografi terstandar untuk dashboard (Search, Bell, Moon/Sun, Chevron, Cube, Users, Calendar, MoreVertical).
  - `apexcharts` & `react-apexcharts` (atau `recharts`): Rendering grafik bar, radial semi-gauge target, dan spline area chart.
  - `clsx` & `tailwind-merge`: Utility penggabungan conditional class (`cn()`).
- **Environment Variables (.env)**:
  - Tidak memerlukan environment variables rahasia (menggunakan mock data dan token UI).
- **Database Changes**:
  - Tidak ada perubahan skema database (modul berbasis frontend skill).

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-27-frontend-tailmind-skill.md  # [Baru] Dokumen perencanaan modul
└── frontend/
    └── tailmind/                              # [Baru] Direktori modul skill
        ├── skill.json                         # [Baru] Metadata, trigger CLI, dan registrasi rule
        └── prompt.md                          # [Baru] System prompt spesifik desain sistem TailAdmin
```

### Rincian Blueprint Desain Berdasarkan Tangkapan Layar:
1. **Design Tokens & Theme System**:
   - Primary Accent: `#3C50E0` / `#465FFF` (Electric Blue).
   - Canvas Background: `#F4F7FF` / `bg-slate-50` (Light) & `#1A222C` / `bg-gray-900` (Dark).
   - Card Surface: `#FFFFFF` (Light) & `#24303F` (Dark) dengan rounded border `rounded-2xl border border-gray-100 dark:border-gray-800`.
   - Badges: `text-xs px-2.5 py-0.5 rounded-full font-medium` (`bg-emerald-50 text-emerald-600` untuk kenaikan/NEW, `bg-rose-50 text-rose-600` untuk penurunan).
2. **Komposisi Komponen Dashboard**:
   - `Header`: Hamburger toggle, input pencarian dengan keyboard badge `⌘K`, Dark/Light mode switcher, ikon notifikasi dengan badge indikator merah, dan profile avatar info (`Musharof`).
   - `Sidebar`: Menu terkelompok (`MENU`), expandable accordion item (`Dashboard` aktif dengan sub-item: `Ecommerce`, `Analytics`, `Marketing`, dll.), serta status badge `NEW` hijau pada item tertentu (`AI`, `Sales`, `Finance`, `AI Assistant`).
   - `KPICards`:
     - *Customers*: Nilai `3,782`, badge `↑ 11.01%`, icon user group.
     - *Orders*: Nilai `5,359`, badge `↓ 9.05%`, icon package cube.
   - `MonthlyTargetCard`: Gauge chart setengah lingkaran target `75.55%`, milestone target ringkasan nominal (`Target $20K`, `Revenue $20K`, `Today $20K`), dan deskripsi perbandingan laba harian.
   - `MonthlySalesCard`: Bar chart 12 bulan (Jan–Dec) dengan rounded top corners.
   - `StatisticsCard`: Area chart multi-gradien dengan tombol filter periode (`Monthly`, `Quarterly`, `Annually`) dan pemilih rentang tanggal (`Oct 21 to Oct 27`).

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Fondasi Direktori & Konfigurasi Metadata (`skill.json`)**
  - [x] Pembuatan direktori `frontend/tailmind`.
  - [x] Penyusunan `skill.json` memuat schema terstandar: `name`, `version`, `category: "frontend"`, `role`, daftar `triggers` (`/tailadmin`, `/tailmind`, `/dashboard`), rujukan ke `rule/base_prompt.md` dan `rule/project-workflow.md`.
- [x] **Fase 2: Perumusan System Prompt Modul (`prompt.md`)**
  - [x] Pendefinisian persona *Senior Frontend Architect & TailAdmin Design System Specialist*.
  - [x] Spesifikasi design tokens: palet warna, tipografi, elevation/shadow, dan dark mode strategy.
  - [x] Blueprint modular komponen: Navbar, Collapsible Sidebar, Stat Card, Target Radial Gauge, Sales Bar Chart, Period Filter Area Chart.
  - [x] Penegakan konvensi kode: TypeScript interfaces yang ketat, zero hardcoded styles, responsif multi-device (`sm`, `md`, `lg`, `xl`, `2xl`).
- [x] **Fase 3: Validasi Modul & Kepatuhan Universal Rules**
  - [x] Verifikasi kepatuhan terhadap prinsip *Zero Fluff*, *Production-Ready*, dan *Negative Constraints*.
  - [x] Penyesuaian registrasi katalog modul di `README.md` (mengubah status `tailmind` menjadi aktif/tersedia).

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Ambiguitas penamaan modul antara nama folder yang diminta (`tailmind`) dan teks logo pada tangkapan layar (`TailAdmin`).
- **Mitigasi**: Menggunakan nama folder `tailmind` sesuai instruksi eksplisit pengguna, serta menyematkan alias trigger (`tailadmin`, `tailmind`) di dalam `skill.json` agar modul dapat dipicu secara fleksibel.
- **Potensi Risiko**: Kompleksitas rendering chart (SVG vs Chart.js vs ApexCharts) yang dapat memicu dependensi berat.
- **Mitigasi**: Menuliskan instruksi prompt yang agnostik dan fleksibel dengan panduan kode ApexCharts/Recharts murni Tailwind tanpa dependensi styling CSS eksternal yang rumit.

---

> **COMPLETED**: Seluruh tahapan rencana implementasi telah dieksekusi dengan lengkap. Berkas konfigurasi `skill.json` dan panduan `prompt.md` telah aktif di `frontend/tailmind/`.

