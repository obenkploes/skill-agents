# IMPLEMENTATION PLAN: MODUL SKILL SUPABASE CURRICULUM ARCHITECT

- **Tanggal Pembuatan**: 2026-11-18
- **Kategori**: database / baas / curriculum-standards / supabase
- **Lokasi Berkas**: `.plan/2026-11-18-skill-supabase-curriculum-architect.md`
- **Status**: Selesai Diimplementasikan (COMPLETED)
- **Estimasi Kompleksitas**: Sedang (7-Module PostgreSQL & BaaS Curriculum + Multi-Platform Integration)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Pengguna membutuhkan modul keahlian agen (*skill agent*) baru bernama `supabase-curriculum-architect` yang bertindak sebagai **Database Analyst**, **System Analyst**, dan **Instruktur Teknis** spesialis ekosistem **Supabase (PostgreSQL)** untuk membimbing peserta didik (SMK dan Mahasiswa) dari dasar hingga mahir dalam merancang skema database, keamanan data berbasis RLS, otomasi backend (PL/pgSQL & Triggers), hingga integrasi multi-platform (REST API, React.js, Laravel, dan Go).

### Penyelarasan dengan Standar Repositori (`rules/templates/template-tutor.md` & `rules/AGENTS.md`)
1. **Aturan Emas Pembelajaran (*Strict Sequential Scaffolding*):**
   - Dilarang melompati materi: tidak ada satu pun perintah SQL, fungsi SDK, tipe data, atau klausa yang muncul sebelum konsep dasarnya dibedah di modul tersebut atau modul sebelumnya.
   - Evaluasi bertahap sebelum berpindah modul: tuntaskan satu modul dalam satu waktu, evaluasi kueri/tugas pengguna sebagai System Analyst, dan berikan umpan balik sebelum lanjut.
2. **Pola 8 Bagian Terpadu (`template-tutor.md`):**
   - **Bagian 1:** Pengingat Prasyarat Cepat (2 Menit) + Jembatan Konsep (*Why Before How* — Model Mental BaaS vs DB Tradisional) + Peta Alur Kerja `[INTI]`.
   - **Bagian 2:** Kamus Fungsi, Klausa SQL/SDK, & Argumen Dasar *(Wajib Terperinci)* `[INTI]`.
   - **Bagian 3:** Prasyarat Lingkungan (Supabase Web / CLI / VS Code) & Checkpoint 3 Tema Berkelanjutan `[INTI]`.
   - **Bagian 4:** Contoh Implementasi Bertingkat — Tema 1 *(Minimal 4 Contoh Mikro)*:
     - Contoh 1: Kasus Paling Dasar `[INTI]`
     - Contoh 2: Variasi Parameter + *State Tracing* `[INTI]`
     - Contoh 3: Kombinasi Menengah + *Step-by-Step Trace* `[INTI]`
     - Contoh 4: Implementasi Terapan & *Edge Case* / Security `[PENDALAMAN: Mahasiswa / SMK Lanjutan]`.
   - **Bagian 5:** Verifikasi Output & Panduan Debugging (*Common Pitfalls* — termasuk Direct Port 5432 vs Pooler 6543, RLS Superuser Bypass, `int8` vs `uuid`) `[INTI]`.
   - **Bagian 6:** Latihan Soal & Praktikum Berkelanjutan Multi-Tema *(4 Level)*:
     - Level 1: Pemahaman Fungsi & Tracing Output (Tema 1) `[INTI]`
     - Level 2: Modifikasi Terarah (Tema 1 — Pola Kembar) `[INTI]`
     - Level 3: Praktikum Berkelanjutan: Transfer Konsep & Milestone Modul (Tema 2) `[INTI LANJUT]`
     - Level 4: Praktikum Berkelanjutan: Analisis, *Edge Case*, & Integrasi Multi-Platform (Tema 2/3) `[PENDALAMAN]`.
   - **Bagian 7:** Cek Mandiri, Milestone Tema, & Panduan Verifikasi `[INTI]`.
   - **Bagian 8:** Ringkasan Fungsi & Refleksi Pemahaman `[INTI]`.
3. **Arsitektur 3 Tema Berkelanjutan (*Persistent Lab Tracks*):**
   - **Tema 1 (Jalur Contoh & Level 1–2):** *Sistem Inventaris Laboratorium Komputer (`perangkat_lab`, `teknisi`, `kategori_perangkat`)*
   - **Tema 2 (Jalur Transfer Berkelanjutan Level 3):** *Sistem Keanggotaan & Perpustakaan Digital (`anggota`, `kategori`, `peminjaman`)*
   - **Tema 3 (Jalur Pendalaman Level 4 Mahasiswa):** *Sistem Log Transaksi & Integrasi Multi-Platform (`transaksi_log`, proteksi RLS `auth.uid()`, REST API curl, React `@supabase/supabase-js` + Realtime, Laravel, Go)*.
4. **Instruksi Pembuka Sesi:**
   - Menyajikan Peta Jalan 7 Modul secara ringkas.
   - Menanyakan apakah pengguna ingin memulai dari Modul 1 atau melompat ke modul tertentu.

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI

- **Teknologi Utama:** Supabase Cloud / Supabase Local CLI, PostgreSQL 15+, PL/pgSQL, Supabase JavaScript SDK (`@supabase/supabase-js`), Supabase REST API (PostgREST), Supabase Realtime, PostgreSQL Client (VS Code extension / DBeaver / psql).
- **Infrastruktur Jaringan:** Supabase Direct Connection (Port 5432 / IPv6) vs Supavisor Connection Pooling (Port 6543 / Transaction & Session Mode / IPv4).
- **Integrasi Multi-Platform:**
  - REST API: `curl` dengan header `apikey` & `Authorization: Bearer`.
  - Frontend: React.js (Vite / Next.js) dengan `@supabase/supabase-js` + Realtime Channel.
  - Backend: Laravel (Eloquent ORM via `pgsql` driver SSL & Guzzle/Http client).
  - Backend: Go (`net/http` standard library).
- **Standar Keamanan:** Pembedahan pemisahan kredensial publik (`anon key`) vs rahasia admin (`service_role key`), perlindungan RLS (*Row Level Security*), serta praktik aman variabel lingkungan (`.env`).

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

```text
skills-agent/
├── .plan/
│   └── 2026-11-18-skill-supabase-curriculum-architect.md # [Update] Dokumen perencanaan implementasi skill
├── skills/
│   └── supabase-curriculum-architect/                   # [Baru] Direktori modul skill baru
│       ├── skill.json                                    # [Baru] Metadata skill, manifest triggers & keywords
│       ├── SKILL.md                                      # [Baru] Entrypoint Antigravity, roadmap 7 modul & aturan baku
│       └── prompt.md                                     # [Baru] System prompt instruktur, pedoman 8 bagian & blueprint kueri
└── README.md                                             # [Update] Registrasi pada katalog modul & trigger harian
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata (`skills/supabase-curriculum-architect/skill.json`)**
  - [x] Pembuatan direktori `skills/supabase-curriculum-architect`.
  - [x] Pembuatan `skill.json` memuat identitas, kategori `database/baas`, role System & Database Analyst, triggers (`/supabase`, `/supabase-tutor`, `/supabase-curriculum`, `/supabase-mentor`), keywords, dan rule binding ke `rules/AGENTS.md`.
- [x] **Fase 2: Entrypoint Antigravity (`skills/supabase-curriculum-architect/SKILL.md`)**
  - [x] Frontmatter YAML dengan peringatan *Mandatory Two-Phase Planning Protocol*.
  - [x] Peta jalan kurikulum 7 modul dari fundamental hingga integrasi multi-platform.
  - [x] Penjelasan 3 tema berkelanjutan dan integrasi standar 8 bagian `template-tutor.md`.
- [x] **Fase 3: System Prompt Komprehensif (`skills/supabase-curriculum-architect/prompt.md`)**
  - [x] Identitas & filosofi instruktur teknis interaktif.
  - [x] Aturan emas scaffolding berjenjang ketat (*no knowledge leap*, evaluasi bertahap).
  - [x] Format baku modul tutor 8 bagian lengkap dengan penanda `[INTI]` vs `[PENDALAMAN]` dan *State Tracing*.
  - [x] Rincian 7 modul kurikulum:
    - Modul 1: Konfigurasi Lingkungan (Web, CLI, VS Code Port 5432 vs 6543 Pooling IPv4).
    - Modul 2: Fondasi Database & Tabel Dasar (`int8`, `text`, `bool`, `timestamptz`, `id` identity).
    - Modul 3: Operasi Data Dasar (CRUD & bahaya kueri tanpa `WHERE`).
    - Modul 4: Relasi Antar Tabel & Integritas Data (FK, cascade, `JOIN`).
    - Modul 5: Keamanan Data & RLS (Policy `USING`/`WITH CHECK`, `auth.uid()`, superuser bypass).
    - Modul 6: Otomasi Logika Backend (PL/pgSQL Functions, Triggers, `NEW`/`OLD`).
    - Modul 7: Konsumsi API & Integrasi Multi-Platform (REST curl, React + Realtime, Laravel, Go).
  - [x] Blueprint skrip SQL PostgreSQL/Supabase, RLS policies, PL/pgSQL Triggers, dan boilerplate integrasi.
  - [x] Instruksi pembuka sesi interaktif.
- [x] **Fase 4: Pembaruan Dokumentasi Repositori (`README.md`)**
  - [x] Registrasi folder `supabase-curriculum-architect` pada pohon direktori.
  - [x] Penambahan trigger `/supabase` pada panduan pemanggilan harian dan CLI.
  - [x] Pendaftaran baris peran modul pada tabel Matriks Peran & Katalog Modul.

---

## 5. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Siswa gagal koneksi di VS Code karena ISP lokal tidak mendukung IPv6 direct connect ke port 5432 Supabase.
- **Mitigasi**: Di Modul 1 dijelaskan perbandingan Direct Connection (port 5432) dan Connection Pooler Supavisor (port 6543) dengan flag Session/Transaction mode yang mendukung jaringan IPv4.
- **Potensi Risiko**: Kunci rahasia `service_role` bocor di aplikasi frontend.
- **Mitigasi**: Modul 1, 5, dan 7 secara ketat menegakkan peringatan keamanan arsitektur: `anon key` hanya untuk client publik yang dilindungi RLS, sedangkan `service_role` dilarang keras dimasukkan ke frontend/React.
- **Potensi Risiko**: Siswa mengira RLS rusak karena saat dites di SQL Editor web / VS Code data tetap muncul.
- **Mitigasi**: Di Modul 5 ditegaskan bahwa user admin `postgres` memiliki hak *bypass RLS*. Pengujian RLS wajib dilakukan melalui peran `anon`/`authenticated` via API atau impersonation.

---

> **STATUS**: Selesai Diimplementasikan (COMPLETED)
