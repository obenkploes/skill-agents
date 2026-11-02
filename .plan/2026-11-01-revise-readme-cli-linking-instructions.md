# IMPLEMENTATION PLAN: REVISI README.MD (PANDUAN MENGHUBUNGKAN SKILL KE ANTIGRAVITY CLI DI LINUX & WINDOWS)

- **Tanggal Pembuatan**: 2026-11-01
- **Kategori**: documentation / cli-setup
- **Lokasi Berkas**: `.plan/2026-11-01-revise-readme-cli-linking-instructions.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Rendah (Dokumentasi Petunjuk Teknis Lintas OS)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Pengguna menginstruksikan revisi pada berkas `README.md` untuk menambahkan panduan lengkap dan terperinci mengenai cara menghubungkan (*link/mount*) seluruh modul skill di repositori ini ke Antigravity CLI (`agy`), baik di lingkungan **Windows** (PowerShell / CMD) maupun **Linux** (Bash / Zsh) serta macOS.

### Goals
1. **Menyempurnakan Bagian 7 di `README.md`**:
   - Menambahkan sub-bagian khusus: **Panduan Menghubungkan ke Antigravity CLI (`agy`)**.
   - **Lingkungan Windows**:
     - *Metode 1 (Rekomendasi)*: Menghubungkan folder via NTFS Junction (`mklink /J`) ke folder plugin Antigravity global (`%USERPROFILE%\.gemini\config\plugins\skills-agent`).
     - *Metode 2 (Konfigurasi JSON)*: Mendaftarkan path repositori di `%USERPROFILE%\.gemini\config\plugins.json` atau `skills.json`.
     - *Metode 3 (Environment Variable)*: Menyetel environment variable `SKILLS_AGENT_PATH` / `ANTIGRAVITY_CUSTOMIZATIONS_PATH`.
     - Perintah verifikasi ketersediaan skill di CLI (`agy`).
   - **Lingkungan Linux & macOS**:
     - *Metode 1 (Rekomendasi)*: Membuat Symbolic Link (`ln -s ~/skills-agent ~/.gemini/config/plugins/skills-agent`).
     - *Metode 2 (Konfigurasi JSON)*: Mendaftarkan path di `~/.gemini/config/plugins.json`.
     - *Metode 3 (Environment Variable)*: Menambahkan `export` di `~/.bashrc` atau `~/.zshrc`.
     - Perintah verifikasi dan pengujian di terminal Linux/macOS.
2. **Menyajikan Contoh Perintah Eksekusi Antigravity CLI (`agy`)**:
   - Cara menjalankan sesi interaktif TUI: `agy`
   - Cara menjalankan perintah langsung (*one-shot headless execution*):
     - `agy run --skill skills-agent/coffee-shop-ui "Buatkan Order Summary screen"`
     - `agy run "@viral apa saja tren medsos hari ini"`
     - `agy run "@fakta apakah benar isu kenaikan tarif X"`
     - `agy run "/matematika-sma buatkan materi pertemuan 1 kelas 10"`
   - Perintah pengecekan ketersediaan plugin & skill di dalam CLI (`/help`, `/skills`).

---

## 2. STRUKTUR PERUBAHAN DOKUMEN `README.MD`

Dokumen `README.md` Bagian 7 akan diperkaya dengan struktur navigasi yang jelas:

```text
README.md
└── 7. PANDUAN PENGHUBUNGAN KE ANTIGRAVITY CLI & IDE (WINDOWS, LINUX, & MACOS)
    ├── A. Arsitektur Discovery Antigravity
    ├── B. Panduan Menghubungkan di Windows (CLI & IDE)
    │   ├── 1. Metode NTFS Junction (Rekomendasi Utama)
    │   ├── 2. Metode Konfigurasi plugins.json (Tanpa Hak Akses Khusus)
    │   └── 3. Verifikasi & Pengecekan
    ├── C. Panduan Menghubungkan di Linux & macOS
    │   ├── 1. Metode Symbolic Link (ln -s)
    │   ├── 2. Metode Konfigurasi plugins.json (~/.gemini/config/)
    │   └── 3. Verifikasi & Pengecekan
    └── D. Contoh Perintah Pemanggilan Antigravity CLI (agy)
        ├── 1. Mode Interaktif (TUI Session)
        └── 2. Mode One-Shot Command Line (Headless Execution)
```

---

## 3. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Penyiapan Konten & Panduan CLI Windows**
  - [x] Menyusun langkah clone, pembuatan folder plugins, `mklink /J`, dan konfigurasi JSON untuk Windows.
- [x] **Fase 2: Penyiapan Konten & Panduan CLI Linux/macOS**
  - [x] Menyusun langkah clone, `mkdir -p ~/.gemini/config/plugins`, `ln -s`, dan `plugins.json` untuk Linux.
- [x] **Fase 3: Penyusunan Contoh Perintah `agy` Real-World**
  - [x] Menyertakan contoh pemanggilan untuk seluruh skill yang ada (`@viral`, `@fakta`, `/coffee-ui`, `/matematika-sma`, `/tailmind`, dll.).
- [x] **Fase 4: Penerapan Perubahan ke `README.md` & Verifikasi Markdown**
  - [x] Mengedit `README.md` dan memastikan format markdown bersih serta link/code-blocks valid.

---

## 4. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Path Windows menggunakan backslash `\` sedangkan format JSON membutuhkan slash `/` atau double-backslash `\\`.
- **Mitigasi**: Memberikan contoh sintaks eksplisit yang benar untuk PowerShell, CMD, dan format berkas `plugins.json` agar pengguna tidak mengalami syntax error saat mendaftarkan path.

---

> **COMPLETED**: Seluruh tahapan rencana revisi telah dieksekusi dengan lengkap. Panduan Antigravity CLI Windows dan Linux telah diperbarui pada `README.md`.

