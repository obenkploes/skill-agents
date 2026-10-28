# IMPLEMENTATION PLAN: MODUL SKILL MATEMATIKA SMP (MATERI AJAR LENGKAP KELAS 7, 8, & 9)

- **Tanggal Pembuatan**: 2026-10-28
- **Kategori**: materi-ajar
- **Lokasi Berkas**: `.plan/2026-10-28-skill-matematika-smp.md` (disimpan di root proyek yang sedang aktif dikerjakan)
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Diperlukan modul keahlian agen (*skill agent*) di direktori `materi-ajar/matematika-smp` yang mampu menyusun bahan ajar mandiri siswa (materi ajar murni, bukan materi tutor) untuk seluruh spektrum silabus Matematika SMP (Kelas 7, 8, dan 9; Semester Ganjil dan Genap; total 72 pertemuan). Bahan ajar yang dihasilkan wajib mengikuti standar baku [`rule/template-materi-ajar.md`](../../rule/template-materi-ajar.md).
- **Goals**:
  1. Menyusun direktori modul lengkap di `materi-ajar/matematika-smp/` yang memuat `skill.json` (metadata & CLI triggers), `SKILL.md` (Antigravity native progressive disclosure), dan `prompt.md` (instruksi spesialisasi kurikulum & silabus roadmap).
  2. Mengintegrasikan seluruh silabus berjenjang yang diberikan pengguna:
     - **Kelas 7**: Bilangan, Aritmetika Sosial, Aljabar & Himpunan, PLSV & PtLSV, Geometri Dasar, Segiempat & Segitiga, Perbandingan & Skala, Penyajian Data & Statistika Dasar.
     - **Kelas 8**: Koordinat Kartesius & Pola Bilangan, Relasi & Fungsi, Persamaan Garis Lurus (PGL), Sistem Persamaan Linear Dua Variabel (SPLDV), Teorema Pythagoras, Lingkaran, Bangun Ruang Sisi Datar (BRSD).
     - **Kelas 9**: Bilangan Berpangkat & Bentuk Akar, Persamaan & Fungsi Kuadrat, Kesebangunan & Kekongruenan, Transformasi Geometri, Bangun Ruang Sisi Lengkung (BRSL).
  3. Memastikan output materi ajar mematuhi format 9 bagian materi ajar siswa: Pengertian & Konsep Dasar, Bentuk Umum & Rumus LaTeX KaTeX, Sifat & Aturan Khusus, Contoh Soal Scaffolding Terperinci, Penerapan Kontekstual Santri/Harian, Pola Kunci / Jembatan Keledai, Latihan Soal Mandiri (LOTS/MOTS/HOTS), PR Pondok/Mandiri, dan Ringkasan Materi.
  4. Menghubungkan modul secara ketat ke invariant rules: [`rule/base_prompt.md`](../../rule/base_prompt.md), [`rule/project-workflow.md`](../../rule/project-workflow.md), dan [`rule/template-materi-ajar.md`](../../rule/template-materi-ajar.md).
- **Out of Scope**:
  - Pembuatan 72 berkas materi statis sekaligus (skill bertindak sebagai generator cerdas saat menerima permintaan pertemuan/topik tertentu).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Format Penulisan & Rendering**:
  - Markdown standar dengan KaTeX math renderer (`$...$` untuk inline dan `$$...$$` untuk display equations).
  - Anotasi path berkas eksplisit di baris teratas blok kode/dokumen.
- **Dependensi Aturan Invariant**:
  - `rule/base_prompt.md`: Prinsip *Zero Fluff*, *Root-Cause Driven*, batasan keamanan, format respons langsung.
  - `rule/project-workflow.md`: Protokol dua fase dan konvensi `.plan/`.
  - `rule/template-materi-ajar.md`: Standar struktur 9 bagian materi ajar mandiri siswa.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-28-skill-matematika-smp.md    # [Baru] Rencana implementasi modul
└── materi-ajar/
    └── matematika-smp/                       # [Direktori Sasaran]
        ├── skill.json                        # [Baru] Metadata, triggers (/matematika-smp, /math-smp), rules link
        ├── SKILL.md                          # [Baru] Dokumentasi kapabilitas Antigravity & YAML frontmatter
        └── prompt.md                         # [Baru] System prompt spesialis kurikulum matematika SMP & peta silabus
```

### Rincian Komponen Modul:
1. **`skill.json`**:
   - `name`: `matematika-smp`
   - `category`: `materi-ajar`
   - `triggers`: `commands` (`["/matematika-smp", "/math-smp", "/materi-smp"]`), `keywords` (`["matematika smp", "aljabar smp", "spldv", "pythagoras", "brsd", "brsl", "persamaan kuadrat smp"]`).
   - `rules`: Mengaitkan `../../rule/base_prompt.md`, `../../rule/project-workflow.md`, dan `../../rule/template-materi-ajar.md`.
2. **`SKILL.md`**:
   - Format Antigravity native dengan frontmatter deskriptif untuk aktivasi on-demand.
3. **`prompt.md`**:
   - **Peran**: *Author Kurikulum & Penulis Bahan Ajar Matematika SMP*.
   - **Roadmap Silabus 72 Pertemuan**: Terbagi rapi menurut Kelas (7, 8, 9) dan Semester (Ganjil, Genap).
   - **Protokol Penulisan 9 Bagian**: Mewajibkan implementasi terperinci tanpa memotong penjelasan, penulisan rumus LaTeX murni (tanpa teks datar), scaffolding contoh soal, dan studi kasus santri/harian.

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Antigravity Indexing (`skill.json` & `SKILL.md`)**
  - [x] Pembuatan `materi-ajar/matematika-smp/skill.json`.
  - [x] Pembuatan `materi-ajar/matematika-smp/SKILL.md` dengan frontmatter YAML dan overview kapabilitas.
- [x] **Fase 2: Perumusan System Prompt & Roadmap Silabus (`prompt.md`)**
  - [x] Penulisan persona, batasan domain (khusus materi ajar siswa, tanpa rubrik pengajar).
  - [x] Penyusunan matriks silabus lengkap 72 pertemuan (Kelas 7, 8, 9 Semester Ganjil & Genap).
  - [x] Standarisasi contoh output per pertemuan mengikuti format 9 bagian `template-materi-ajar.md`.
- [x] **Fase 3: Validasi Modul & Registrasi Katalog**
  - [x] Verifikasi ketiadaan instruksi guru/tutor sesuai instruksi pengguna.
  - [x] Penyelarasan matriks modul di `README.md` pada kategori `materi-ajar`.

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Siswa bingung membaca rumus jika persamaan matematika ditulis dalam bentuk teks biasa.
- **Mitigasi**: Menegakkan aturan ketat di dalam `prompt.md` bahwa setiap ekspresi aljabar, pecahan, pangkat, dan bentuk akar wajib menggunakan notasi LaTeX KaTeX (`$\frac{a}{b}$`, `$\sqrt{x}$`, `$x^2$`).
- **Potensi Risiko**: Permintaan pembuatan materi ambigu (misal pengguna hanya meminta "buatkan materi pertemuan 3" tanpa menyebut kelas/semester).
- **Mitigasi**: Prompt mewajibkan agen memetakan topik berdasarkan nomor pertemuan pada silabus yang aktif atau mengonfirmasi kelas/topik jika belum disebutkan.

---

> **COMPLETED**: Seluruh tahapan rencana implementasi telah dieksekusi dengan lengkap. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` telah aktif di `materi-ajar/matematika-smp/`.

