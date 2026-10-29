# IMPLEMENTATION PLAN: PEMBERSIHAN STRUKTUR BERKAS & FOLDER REDUNDAN

- **Tanggal Pembuatan**: 2026-10-29
- **Kategori**: project-maintenance / architecture-refactoring
- **Lokasi Berkas**: `.plan/2026-10-29-cleanup-redundant-structure.md`
- **Status**: Selesai Diimplementasikan (Completed)
- **Estimasi Kompleksitas**: Rendah (Pembersihan direktori duplikat & pemindahan template)

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Setelah migrasi ke arsitektur Centralized Global Plugin Antigravity dengan root `skills/` dan `rules/AGENTS.md`, terdapat banyak folder kosong dan folder skill lama (`frontend/`, `materi-ajar/`, `materi-tutor/`, `backend/`, `rule/`) yang menduplikasi isi dari `skills/` dan `rules/`. Hal ini membingungkan pemeliharaan berkas (*dual maintenance*) dan membuang ruang penyimpanan.
- **Goals**:
  1. Menghapus seluruh folder kosong tanpa berkas (`backend/`, `materi-ajar/matematika-sma`, `materi-ajar/MySQL`, `materi-tutor/flutter`, `materi-tutor/laravel`).
  2. Menghapus folder lama hasil migrasi yang kini menjadi duplikat dari `skills/`:
     - `frontend/mobile/` (`coffee-shop-ui`, `food-delivery-ui`, `task-management-ui`)
     - `frontend/web/` (`tailmind`)
     - `frontend/` (dihapus menyeluruh)
     - `materi-ajar/matematika-smp/` (dihapus menyeluruh bersama foldernya)
     - `materi-tutor/sql-server/` (dihapus menyeluruh bersama foldernya)
  3. Memindahkan template dokumen rujukan (`template-plan.md`, `template-materi-ajar.md`) dari folder lama `rule/` ke `rules/templates/`.
  4. Menghapus folder lama `rule/` yang isinya telah digabungkan ke `rules/AGENTS.md`.
  5. Memperbarui `README.md` agar mencerminkan struktur ramping yang 100% konsisten.
- **Out of Scope**:
  - Modifikasi isi internal di dalam berkas `skills/*/SKILL.md` atau `prompt.md` (hanya membersihkan duplikat di luar `skills/`).

---

## 2. EVALUASI STRUKTUR: BERKAS & FOLDER YANG DIHAPUS VS DIPERTAHANKAN

### A. Folder & Berkas yang TIDAK DIBUTUHKAN (AKAN DIHAPUS)
| Path Target | Alasan Teknis Penghapusan |
| :--- | :--- |
| `backend/` | Direktori kosong tanpa modul aktif. |
| `frontend/` | Seluruh isinya (`coffee-shop-ui`, `food-delivery-ui`, `task-management-ui`, `tailmind`) telah dimigrasi 100% ke `skills/`. |
| `materi-ajar/` | Modul `matematika-smp` telah dimigrasi ke `skills/matematika-smp`, sedangkan subfolder lain (`matematika-sma`, `MySQL`) kosong. |
| `materi-tutor/` | Modul `sql-server` telah dimigrasi ke `skills/sql-server`, sedangkan `flutter` dan `laravel` kosong. |
| `rule/base_prompt.md` | Telah dikonsolidasikan secara permanen ke dalam `rules/AGENTS.md`. |
| `rule/project-workflow.md` | Telah dikonsolidasikan secara permanen ke dalam `rules/AGENTS.md`. |
| `rule/` | Dihapus setelah file templatenya dipindahkan ke `rules/templates/`. |

### B. Folder & Berkas yang DIPERTAHANKAN (SUMBER UTAMA)
| Path Utama | Peran Arsitektural |
| :--- | :--- |
| `plugin.json` | Manifest resmi Antigravity Global Plugin. |
| `rules/AGENTS.md` | Aturan tunggal universal (Otomatis Aktif Global di seluruh proyek). |
| `rules/templates/` | Tempat penyimpanan `template-plan.md` dan `template-materi-ajar.md`. |
| `skills/` | Tempat tunggal seluruh modul skill resmi: `coffee-shop-ui`, `food-delivery-ui`, `matematika-smp`, `sql-server`, `tailmind`, `task-management-ui`. |
| `.plan/` | Arsip dokumen perencanaan fitur dan pemeliharaan proyek. |
| `README.md` | Dokumentasi arsitektur dan katalog modul. |

---

## 3. RANCANGAN ARSITEKTUR PASCA PEMBERSIHAN

```text
skills-agent/
├── .plan/                                 # Arsip rencana implementasi fitur/proyek
├── plugin.json                            # Manifest plugin resmi Antigravity
├── README.md                              # Panduan arsitektur & katalog repositori
├── rules/
│   ├── AGENTS.md                          # Invariant rules (Base prompt + Mandatory Planning Protocol)
│   └── templates/                         # Template dokumen baku
│       ├── template-plan.md
│       └── template-materi-ajar.md
└── skills/                                # Discovery root resmi seluruh modul skill
    ├── coffee-shop-ui/
    ├── food-delivery-ui/
    ├── matematika-smp/
    ├── sql-server/
    ├── tailmind/
    └── task-management-ui/
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Penyelamatan & Pemindahan Template Dokumen**
  - [x] Membuat direktori `rules/templates/`.
  - [x] Memindahkan `rule/template-plan.md` dan `rule/template-materi-ajar.md` ke `rules/templates/`.
- [x] **Fase 2: Penghapusan Direktori Redundan & Duplikat**
  - [x] Menghapus direktori `backend/`.
  - [x] Menghapus direktori `frontend/`.
  - [x] Menghapus direktori `materi-ajar/`.
  - [x] Menghapus direktori `materi-tutor/`.
  - [x] Menghapus direktori lama `rule/`.
- [x] **Fase 3: Pembaruan Dokumentasi & Verifikasi Integritas**
  - [x] Memperbarui `README.md` mencerminkan struktur bersih pasca pembersihan.
  - [x] Memverifikasi integritas junction `~/.gemini/config/plugins/skills-agent` bahwa semua skill tetap utuh dan terbaca.
  - [x] Menandai checklist `.plan/2026-10-29-cleanup-redundant-structure.md` selesai (`[x]`).

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Kehilangan kode template ajar atau template plan jika folder `rule/` langsung dihapus tanpa memindahkan filenya.
- **Mitigasi**: Pindahkan berkas template ke `rules/templates/` terlebih dahulu pada Fase 1 sebelum menjalankan penghapusan folder `rule/` pada Fase 2.

---

> **STATUS IMPLEMENTASI**: Seluruh direktori kosong dan folder duplikat telah berhasil dihapus secara bersih. Seluruh template telah diselamatkan di `rules/templates/` dan repositori kini beroperasi dengan struktur ramping tanpa redundansi.

