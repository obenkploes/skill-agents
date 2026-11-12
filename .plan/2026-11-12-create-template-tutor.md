# IMPLEMENTATION PLAN: PEMBUATAN TEMPLATE TUTOR STANDAR & SINKRONISASI SKILL PRAKTIKUM (SMK & MAHASISWA)

- **Tanggal Pembuatan**: 2026-11-12
- **Kategori**: curriculum-architecture / template-tutor / materi-tutor
- **Lokasi Berkas**: `.plan/2026-11-12-create-template-tutor.md`
- **Status**: Selesai Diimplementasikan (Completed)
- **Estimasi Kompleksitas**: Sedang (Centralized Tutor Template & Multi-Skill Synchronization)

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**:
  1. Direktori `rules/templates/` belum memiliki berkas `template-tutor.md` setelah penghapusan `rule/template-modul.md` pada restrukturisasi sebelumnya (`a9f95ef8`), sehingga modul praktikum (`mysql`, `sql-server`) berdiri sendiri tanpa acuan standar terpusat.
  2. Modul praktikum yang dihasilkan selama ini terlalu cepat melompat ke skrip/kueri kompleks tanpa **membedah fungsi-fungsi dasar, klausa, sintaks, tipe parameter/argumen, dan nilai kembaliannya** terlebih dahulu.
  3. Jumlah contoh terpandu dan soal latihan terlalu sedikit serta loncatan kesulitannya terlalu curam untuk menguatkan pemahaman peserta didik di jenjang **SMK** maupun **Mahasiswa**.
- **Goals**:
  1. Membuat `rules/templates/template-tutor.md` berformat **8 Bagian Terpadu** yang mewajibkan **Kamus Fungsi, Perintah, & Argumen Dasar** di awal modul, **4 Contoh Implementasi Bertingkat Mikro**, **4 Level Latihan Berjenjang (8–10 soal)** dengan jalur **SMK vs Mahasiswa**, **Cek Mandiri / Panduan Verifikasi**, dan **Kesesuaian Kosakata Nilai Islam**.
  2. Memperbarui `skills/mysql/` (`SKILL.md`, `prompt.md`) dan `skills/sql-server/` (`SKILL.md`, `prompt.md`) agar merujuk langsung ke `rules/templates/template-tutor.md` dan mengadopsi standar 8 bagian tersebut tanpa menghilangkan keunggulan teknis MySQL 8.x maupun T-SQL.
  3. Memperbarui `README.md` agar mendokumentasikan `rules/templates/template-tutor.md` secara resmi.
- **Out of Scope**:
  - Tidak mengubah format 5 bagian khusus mikrokontroler/hardware pada `skills/santri-robotics-iot-mentor/` (karena modul tersebut sudah memuat bagian *Kamus Teknis: Fungsi dan Argumen* tersendiri).
  - Tidak memodifikasi berkas non-Markdown (`sql-server/skill.json`).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Package / Library Baru**: Tidak ada.
- **Environment Variables (.env)**: Tidak ada.
- **Keterkaitan File Lintas Modul**:
  - `rules/templates/template-tutor.md` menjadi rujukan utama bagi modul bertipe `materi-tutor` / `database/tutorial` (`mysql`, `sql-server`, dan modul praktikum pemrograman umum SMK/Mahasiswa).

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

```text
D:/Project/exercise/skills-agent/
├── .plan/
│   └── 2026-11-12-create-template-tutor.md      # [Baru] Rencana pembuatan template-tutor
├── rules/
│   └── templates/
│       ├── template-materi-ajar.md              # [Tetap] Modul SMP/SMA
│       ├── template-plan.md                     # [Tetap] Rencana implementasi
│       └── template-tutor.md                    # [Baru] Modul Tutor & Praktikum 8 Bagian (SMK & Mahasiswa)
├── skills/
│   ├── mysql/
│   │   ├── SKILL.md                             # [Ubah] Adopsi template-tutor.md 8 Bagian
│   │   └── prompt.md                            # [Ubah] Tambahkan Kamus Fungsi Dasar, 4 Contoh, & 4 Level Latihan
│   └── sql-server/
│       ├── SKILL.md                             # [Ubah] Adopsi template-tutor.md 8 Bagian
│       └── prompt.md                            # [Ubah] Tambahkan Kamus Fungsi Dasar, 4 Contoh, & 4 Level Latihan
└── README.md                                    # [Ubah] Dokumentasikan template-tutor.md
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Pembuatan Template Pusat (`rules/templates/template-tutor.md`)**
  - [x] Merancang struktur 8 bagian (Tujuan & Peta Alur → Kamus Fungsi & Argumen Dasar → Prasyarat & Skeleton → 4 Contoh Bertingkat Mikro → Verifikasi Output & Troubleshooting → 4 Level Latihan Berjenjang 8–10 soal SMK/Mahasiswa → Cek Mandiri → Ringkasan & Refleksi).
- [x] **Fase 2: Sinkronisasi Skill `mysql` & `sql-server`**
  - [x] Memperbarui `skills/mysql/SKILL.md` dan `skills/mysql/prompt.md`.
  - [x] Memperbarui `skills/sql-server/SKILL.md` dan `skills/sql-server/prompt.md`.
- [x] **Fase 3: Dokumentasi & Verifikasi Integritas**
  - [x] Memperbarui `README.md`.
  - [x] Memverifikasi penomoran bagian, rujukan path relatif, dan sinkronisasi live plugin global `~/.gemini/config/plugins/skills-agent`.

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Terjadi konflik antara standar `Production-Ready SQL` (skrip utuh tanpa komentar pemalas) dengan kebutuhan contoh mikro bertahap.
- **Mitigasi**: Membedakan tegas antara **Contoh Mikro Pemakaian Fungsi (Bagian 2)**, **4 Contoh Bertingkat Lengkap Siap Eksekusi (Bagian 4)**, dan **Latihan Berjenjang Level 1–4 (Bagian 6)** agar skrip contoh tetap utuh siap dijalankan tanpa mengorbankan kejelasan bagi pemula SMK maupun pendalaman Mahasiswa.

---

> **COMPLETED**: Berkas `rules/templates/template-tutor.md` telah dibuat serta disinkronkan ke `skills/mysql/`, `skills/sql-server/`, dan `README.md`. (Catatan: `skills/sql-server/skill.json` masih mencatat path lama `../../rule/...` di luar cakupan berkas `.md`.)
