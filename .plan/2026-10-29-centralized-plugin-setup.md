# IMPLEMENTATION PLAN: SETUP CENTRALIZED GLOBAL PLUGIN DENGAN MANDATORY PLANNING ENFORCEMENT

- **Tanggal Pembuatan**: 2026-10-29
- **Kategori**: system-architecture / tooling
- **Lokasi Berkas**: `.plan/2026-10-29-centralized-plugin-setup.md`
- **Status**: Selesai Diimplementasikan (Completed)
- **Estimasi Kompleksitas**: Sedang

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Pengguna ingin seluruh skill yang telah dibangun dapat digunakan di proyek/workspace manapun di Antigravity tanpa harus menduplikasi rule atau file planning secara manual ke setiap proyek target, dan memastikan Antigravity selalu mematuhi protokol planning dua-fase sebelum menulis kode.
- **Goals**:
  1. Mentransformasikan repositori `D:\Project\exercise\skills-agent` menjadi **Antigravity Global Plugin** resmi bernama `skills-agent`.
  2. Membuat `plugin.json` di root repositori sebagai manifest plugin resmi Antigravity.
  3. Mengonsolidasikan seluruh invariant rule (`rule/base_prompt.md`, `rule/project-workflow.md`) ke dalam `rules/AGENTS.md` resmi plugin, sehingga Antigravity secara otomatis menginjeksi aturan ini ke SEMUA sesi/proyek di komputer pengguna.
  4. Menata seluruh modul skill ke dalam direktori standar `skills/<skill_name>/` (`task-management-ui`, `coffee-shop-ui`, `food-delivery-ui`, `sql-server`, `matematika-smp`, `tailmind`).
  5. Memperbarui `SKILL.md` pada setiap skill agar memuat klausul *Mandatory Planning Protocol* langsung di dalam instruksinya (pertahanan berlapis).
  6. Menghubungkan direktori repositori ke path plugin global Antigravity (`~/.gemini/config/plugins/skills-agent`) via NTFS Directory Junction agar terjadi sinkronisasi instan (*live sync*) tanpa copy-paste.

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Platform**: Windows, PowerShell.
- **Antigravity Global Plugin Path**: `C:\Users\Dokter Komputer\.gemini\config\plugins\skills-agent`.
- **Mekanisme Tautan**: NTFS Directory Junction (`New-Item -ItemType Junction` atau `cmd /c mklink /J`).

---

## 3. RANCANGAN STRUKTUR BERKAS PLUGIN

```text
skills-agent/ (D:\Project\exercise\skills-agent)
├── plugin.json                                 # [Baru] Manifest plugin resmi Antigravity
├── rules/
│   └── AGENTS.md                               # [Baru] Universal Global Invariant Rules (Otomatis Aktif Global)
├── skills/                                     # [Baru/Terstruktur] Discovery root resmi Antigravity
│   ├── task-management-ui/
│   │   ├── SKILL.md                            # [Update] Memuat mandatory planning gate
│   │   ├── prompt.md
│   │   └── skill.json
│   ├── coffee-shop-ui/
│   │   ├── SKILL.md                            # [Update] Memuat mandatory planning gate
│   │   ├── prompt.md
│   │   └── skill.json
│   ├── food-delivery-ui/
│   │   ├── SKILL.md                            # [Update] Memuat mandatory planning gate
│   │   ├── prompt.md
│   │   └── skill.json
│   ├── sql-server/
│   │   ├── SKILL.md                            # [Update] Memuat mandatory planning gate
│   │   ├── prompt.md
│   │   └── skill.json
│   ├── matematika-smp/
│   │   ├── SKILL.md
│   │   ├── prompt.md
│   │   └── skill.json
│   └── tailmind/
│       ├── SKILL.md
│       ├── prompt.md
│       └── skill.json
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Pembuatan Manifest & Global Invariant Rules**
  - [x] Pembuatan `plugin.json` di root `skills-agent`.
  - [x] Pembuatan `rules/AGENTS.md` (menggabungkan base prompt dan aturan planning dua-fase).
- [x] **Fase 2: Penataan Struktur Modul Skill (`skills/`)**
  - [x] Migrasi modul dari `frontend/mobile/`, `materi-tutor/`, `materi-ajar/`, `frontend/web/tailmind` ke `skills/`.
  - [x] Pembaruan instruksi pada setiap `SKILL.md` agar memuat gate planning wajib di frontmatter dan konten.
- [x] **Fase 3: Pembuatan Directory Junction ke Global Antigravity Config**
  - [x] Membuat NTFS Junction dari `~/.gemini/config/plugins/skills-agent` menuju `D:\Project\exercise\skills-agent`.
  - [x] Verifikasi keberadaan dan keterbacaan junction.
- [x] **Fase 4: Dokumentasi & Verifikasi**
  - [x] Pembaruan `README.md` repositori.
  - [x] Verifikasi discovery plugin dan rule.

---

> **STATUS IMPLEMENTASI**: Seluruh penataan plugin dan pembuatan Directory Junction global telah berhasil diselesaikan. Repositori `skills-agent` kini resmi terdaftar sebagai global plugin aktif pada instalasi Antigravity.
