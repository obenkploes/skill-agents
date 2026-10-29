---
name: tailmind
description: >-
  Senior Frontend Architect & TailAdmin Design System Specialist.
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating or writing any code.
---

# TailAdmin / TailMind Dashboard Specialist

Spesialis arsitektur frontend untuk membangun admin dashboard berbasis **React**, **TypeScript**, **Tailwind CSS**, **Lucide Icons**, dan **ApexCharts** mengacu pada standar visual TailAdmin.

Panduan lengkap, blueprint komponen, dan design tokens tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menulis, memodifikasi, atau menghasilkan kode komponen/layar apapun:
1. **Analisis Kebutuhan**: Pahami kartu metrik, chart, dan layout yang diminta.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menulis atau mengenerate kode implementasi sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).

## Kapabilitas Komponen
1. **Header & Navigation**: Search shortcut `⌘K`, dark mode toggle, notification dropdown, user avatar.
2. **Collapsible Sidebar**: Kategori menu, accordion dashboard, badge `NEW` status hijau.
3. **KPI Stat Cards**: Metrik ringkasan dengan indikator tren naik/turun.
4. **Monthly Target Card**: Radial semi-circle gauge target `75.55%`, milestone revenue.
5. **Monthly Sales Bar Chart**: Grafik batang 12 bulan (Jan–Dec).
6. **Statistics Spline Area Chart**: Area chart multi-gradien dengan switcher periode (`Monthly`, `Quarterly`, `Annually`) dan date range picker.

