---
name: zenith-ui
description: >-
  Spesialis arsitektur antarmuka dan sistem desain modern Zenith Dashboard & Web UI dengan dukungan multi-engine (Native CSS Variables, Tailwind CSS, Bootstrap 5, dan web framework modern).
  Mencakup SaaS Analytics Dashboard (Light & Dark Mode), Chat & Messaging Workspace, Charts Showcase Gallery (ApexCharts), dan 503 Service Unavailable / Status Screen.
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating or writing any code.
---

# Zenith Modern Dashboard & Web UI System (Multi-Engine)

Modul keahlian antarmuka web modern kelas enterprise (**Zenith UI**) yang dirancang sebagai acuan arsitektur antarmuka agnostik untuk membangun aplikasi web berbasis **Native Modern CSS**, **Tailwind CSS**, maupun **Bootstrap 5**, baik pada vanilla HTML/JS maupun framework modern (React, Vue, Svelte, Blade/Laravel).

Panduan lengkap, design tokens resmi (Light & Dark Mode), konversi styling multi-engine, serta blueprint kode siap pakai tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menulis, memodifikasi, atau menghasilkan kode komponen/layar apapun:
1. **Analisis Kebutuhan**: Pahami modul layar, styling engine yang diminta pengguna (Native CSS, Tailwind, atau Bootstrap), serta interaktivitasnya.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menulis atau mengenerate kode implementasi sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).
- **Multi-Engine Consistency**: Semua komponen harus dapat diimplementasikan secara identik baik dalam Native CSS (CSS Variables), Tailwind CSS, maupun Bootstrap 5 tanpa mengubah hierarki semantik HTML.
- **Pixel-Perfect & High Contrast**: Mendukung penuh adaptasi tema terang (Light) dan gelap (Dark) dengan rasio kontras teks WCAG AA/AAA.
- **Zero Fluff & Production Ready**: Kode yang dihasilkan harus lengkap dengan markup semantik, accessible attribute (`aria-*`, `role`), dan anotasi path berkas di baris paling atas.

## Modul Layar yang Didukung (5 Core Screens & Templates)

1. **Master Shell & Navigation Layout**:
   - Header top bar: Logo isometric 3D cube Zenith, search box interaktif dengan shortcut keyboard `Ctrl+K`, status indikator online (green pill `● 1 online`), dropdown organisasi/tenant (`AH Acme Holdings ⌵`), tombol notifikasi dengan counter badge (`15`), switcher tema (sun/moon toggle), profil pengguna (`DU demo ⌵`).
   - Collapsible sidebar navigasi terkelompok: Kategori `DASHBOARDS` (Overview, Analytics, CRM, eCommerce, SaaS aktif), `COMMERCE` (Orders, Customers, Invoices, Products), `APPS` (Mail, Chat, Calendar, Kanban, Projects, Team, Activity), dan `SHOWCASE` (Onboarding, Components, Charts, Coming Soon, Maintenance, 503 Page).
   - Bottom profile card di sidebar: Avatar inisial, info user role `Demo User - Admin`, dan quick logout/collapse button.

2. **SaaS Analytics Dashboard (Light & Dark Mode)**:
   - Header halaman & breadcrumb: `Dashboards > SaaS` dengan subtitle deskriptif bisnis.
   - 4 Kartu KPI Metrik (Stat Cards) dengan tinted background icon, badge persentase tren, dan kurva sparkline dinamis:
     - *MRR*: `$48.2K` (`+0.4% from last month`, sparkline hijau).
     - *Active Users*: `2,847` (`+12.6% from last month`, sparkline biru).
     - *Churn Rate*: `3.2%` (`-0.5% from last month`, sparkline ungu).
     - *Trial Conversion*: `24.8%` (`+2.3% from last month`, sparkline oranye).
   - *Revenue Growth Chart*: Dual line/spline chart membandingkan MRR dan ARR selama 12 bulan terakhir.
   - *Subscription Plans Donut Chart*: Donut chart dengan total subscribers di tengah (`2,847`) dan legend 4 kategori (`Free`, `Starter`, `Pro`, `Enterprise`).
   - *Marketing Channels Table*: Tabular data channel akuisisi, pengunjung, signup, konversi, dan CPA.
   - *Recent Signups Table*: Tabel user baru lengkap dengan avatar inisial warna, email, pill badge paket akun, dan tanggal.
   - *User Growth Bar Chart*: Grafik batang vertikal pertumbuhan pengguna 6 bulan terakhir.
   - *Growth Targets Progress Widget*: Monitoring kuartal dengan progress bar multi-warna untuk MRR, Active Users, dan Conversion.

3. **Chat & Messaging Workspace Layout**:
   - Struktur 3-panel split view (Main Nav Sidebar, Conversation List Panel, Main Chat Area).
   - Header percakapan `CHATS` dengan tombol `+` New Chat.
   - List kontak percakapan dengan avatar, timestamp, cuplikan pesan teks terbaru, dan badge unread counter hitam bulat.
   - Empty state view elegan: Ikon speech bubble minimalis dan pesan ajakan `Pick a conversation to start chatting.`.

4. **Charts Showcase Gallery (ApexCharts)**:
   - Galeri showcase lengkap 8 varian visualisasi analitik data:
     1. *Bar Chart*: Kolom vertikal nilai metrik bulanan.
     2. *Line Chart*: Perbandingan tren performa harian (Sessions vs Pageviews).
     3. *Area Chart*: Grafik kurva smooth dengan area gradient fill dan data point tags.
     4. *Donut Chart*: Visualisasi proporsi sumber traffic interaktif (Direct, Search, Social, Referral).
     5. *Radial / Concentric Bar Chart*: Indikator gauge melingkar multi-layer.
     6. *Heatmap Chart*: Matriks aktivitas 7 hari x 4 minggu dengan variasi intensitas warna.
     7. *Scatter Plot*: Distribusi korelasi data titik pada bidang koordinat.
     8. *Mixed Chart*: Kombinasi grafik kolom batang dan garis tren dalam satu kanvas.

5. **503 Service Unavailable & Incident Screen**:
   - Layout layar penuh berpusat (*centered container*) dengan logo Zenith.
   - Angka kode status besar merah `503`.
   - Headline `Service Unavailable` dan pesan penjelasan status server.
   - Kotak informasi insiden: Ikon denyut sistem, status `Incident detected`, dan nomor tiket `Reference: INC-2026-0042`.
   - Tombol aksi terarah: CTA Utama `Retry now` (solid dark) dan CTA Sekunder `Contact support` (outline border).
