# IMPLEMENTATION PLAN: MODUL SKILL MATEMATIKA SMA (MATERI AJAR LENGKAP JURUSAN IPA & PESANTREN)

- **Tanggal Pembuatan**: 2026-10-31
- **Kategori**: materi-ajar
- **Lokasi Berkas**: `.plan/2026-10-31-skill-matematika-sma.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang - Tinggi (Comprehensive 72-Meeting Curriculum & Pedagogical Scaffolding)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Dibutuhkan modul keahlian agen (*skill agent*) baru di direktori `skills/matematika-sma/` yang bertindak sebagai kurikulum author dan spesialis penyusun bahan ajar mandiri matematika jenjang Sekolah Menengah Atas / Madrasah Aliyah (SMA/MA Jurusan IPA) dengan penyesuaian untuk Pesantren. Modul ini harus mampu mengenerate bahan belajar mandiri siswa (bukan panduan pengajar/tutor) dengan struktur baku 9 bagian, notasi LaTeX KaTeX murni, serta mengintegrasikan nilai-nilai logika, keteraturan alam semesta ciptaan Allah SWT, dan studi kasus kontekstual santri/keseharian.

### Goals
1. **Penyusunan Modul Skill Terstandar Antigravity** di `skills/matematika-sma/`:
   - `skill.json`: Metadata, triggers (`/matematika-sma`, `/math-sma`, `/materi-sma`, `/matematika-pesantren`), dependencies, dan rules links.
   - `SKILL.md`: Entrypoint skill dengan frontmatter YAML resmi, invariant rules, dan ringkasan 72 pertemuan kurikulum 3 tahun.
   - `prompt.md`: System prompt spesialisasi kurikulum lengkap dengan roadmap 72 pertemuan, konvensi formula KaTeX LaTeX, panduan scaffolding pedagogis, serta aturan penulisan modul mandiri siswa.
2. **Penyelarasan Silabus Komprehensif (72 Pertemuan Efektif)**:
   - **Kelas 10 (Ganjil & Genap - 24 Pertemuan)**: Eksponen, Bentuk Akar, Logaritma, Persamaan & Pertidaksamaan Nilai Mutlak, SPLDV, SPLTV, Fungsi & Grafiknya, Fungsi Kuadrat, Komposisi & Invers, Trigonometri Segitiga Siku-siku, Sudut Istimewa & 4 Kuadran, Aturan Sinus & Cosinus, Grafik Trigonometri, dan Pengenalan Geometri Ruang.
   - **Kelas 11 (Ganjil & Genap - 24 Pertemuan)**: Induksi Matematika, Program Linear & Uji Titik Pojok, Aljabar Matriks (Ordo, Transpos, Operasi, Determinan & Invers 2x2 dan 3x3 Sarrus, Aplikasi SPL), Transformasi Geometri (Translasi, Refleksi, Rotasi, Dilatasi), Barisan & Deret (Aritmetika, Geometri, Tak Hingga, Bunga Majemuk/Peluruhan), Limit Fungsi Aljabar & Bentuk Tak Tentu, serta Turunan / Diferensial (Aturan Dasar, Hasil Kali, Hasil Bagi, Aturan Rantai, Gradien Garis Singgung, Titik Stasioner, Kecepatan Sesaat).
   - **Kelas 12 (Ganjil & Genap - 24 Pertemuan)**: Geometri Ruang / Dimensi Tiga (Kedudukan, Jarak Titik/Garis/Bidang, Sudut), Statistika Deskriptif (Tabel Distribusi Frekuensi Sturges, Histogram, Poligon, Ogive, Ukuran Pemusatan: Mean/Median/Modus data tunggal & kelompok, Ukuran Letak: Kuartil/Desil/Persentil, Ukuran Penyebaran: Jangkauan, Simpangan Rata-rata, Varians, Standar Deviasi), Kaidah Pencacahan (Aturan Penjumlahan & Perkalian), Permutasi & Faktorial, Kombinasi, Peluang Kejadian Sederhana & Majemuk, Integral Tak Tentu & Tentu, Aplikasi Luas Daerah & Volume Benda Putar, serta Pemantapan UN/UTBK.
3. **Penerapan Format Baku 9 Bagian Materi Ajar Siswa**:
   Mengacu ketat pada `rules/templates/template-materi-ajar.md`:
   1. *Pengertian & Konsep Dasar* (komunikatif, analogi intuitif).
   2. *Bentuk Umum & Rumus Baku* (KaTeX LaTeX murni $...$ dan $$...$$).
   3. *Sifat-Sifat, Karakteristik, & Aturan Khusus* (tabel perbandingan, syarat keberlakuan).
   4. *Contoh Soal & Pembahasan Terperinci* (scaffolding bertingkat: Diketahui, Ditanyakan, Langkah, Kesimpulan $\checkmark$).
   5. *Penerapan Kontekstual* (Studi kasus nyata & lingkungan pondok pesantren: hafalan Qur'an, jadwal piket/ibadah, konsumsi, infak).
   6. *Pola Kunci & Cara Cepat Mengingat* (jembatan keledai, pola visual, catatan waspada kesalahan umum).
   7. *Latihan Soal Mandiri* (Tingkat Dasar, Variasi/Campuran, Tantangan/HOTS).
   8. *Pekerjaan Rumah (PR Pondok / Mandiri)* (soal latihan, soal cerita, dan pertanyaan pemahaman konsep).
   9. *Ringkasan Materi* (3-4 poin esensial).
4. **Pembaruan Katalog Proyek**:
   - Memperbarui tabel matriks katalog modul di `README.md` untuk mendaftarkan skill `matematika-sma`.

### Out of Scope
- Tidak membuat 72 file markdown statis individual secara terpisah saat instalasi (modul ini bertindak sebagai generator cerdas dinamis on-demand saat menerima trigger pertanyaan atau nomor pertemuan tertentu).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI

### Standar Penulisan & Rendering
- **Markdown & KaTeX Math Renderer**:
  - Rumus inline: `$U_n = a + (n-1)b$`
  - Rumus display blok: `$$S_n = \frac{n}{2}(2a + (n-1)b)$$`
  - Matriks & sistem persamaan: `\begin{pmatrix} ... \end{pmatrix}` dan `\begin{cases} ... \end{cases}`
  - Pecahan, akar, limit, integral: `\frac{a}{b}`, `\sqrt{x}`, `\lim_{x \to a}`, `\int f(x)\,dx`
- **Negative Constraints**:
  - DILARANG menuliskan rumus dalam format teks datar tanpa format (misal: `nn+12` atau `ax2+bx+c=0`).
  - DILARANG menyertakan rubrik penilaian guru, lembar penskoran instruktur, atau instruksi fasilitator (murni materi ajar siswa).

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-31-skill-matematika-sma.md      # [Baru] Dokumen perencanaan modul
├── skills/
│   └── matematika-sma/                         # [Baru] Direktori modul skill Matematika SMA
│       ├── skill.json                          # [Baru] Metadata skill & triggers CLI/chat
│       ├── SKILL.md                            # [Baru] Deskripsi skill, invariant rules, & ringkasan silabus
│       └── prompt.md                           # [Baru] Comprehensive System Prompt, 72-Meeting Syllabus, & KaTeX Guidelines
└── README.md                                   # [Update] Registrasi pada tabel katalog modul skill
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Direktori (`skills/matematika-sma/skill.json`)**
  - [x] Pembuatan folder `skills/matematika-sma`.
  - [x] Pembuatan file `skill.json` memuat properti `name: "matematika-sma"`, `category: "materi-ajar"`, `role`, daftar triggers (`/matematika-sma`, `/math-sma`, `/materi-sma`, `/matematika-pesantren`), kata kunci, dan referensi aturan `rules/AGENTS.md` serta `rules/templates/template-materi-ajar.md`.
- [x] **Fase 2: Pembuatan Entrypoint Antigravity (`skills/matematika-sma/SKILL.md`)**
  - [x] Penulisan frontmatter YAML terstandar dengan `MANDATORY WORKFLOW`.
  - [x] Deskripsi peran, kapabilitas kurikulum, batasan kritis, dan ringkasan silabus Kelas 10, 11, 12.
- [x] **Fase 3: Penyusunan System Prompt Komprehensif (`skills/matematika-sma/prompt.md`)**
  - [x] Identitas & Batasan Kritis (Negative Constraints, zero teacher rubric).
  - [x] Roadmap Silabus 72 Pertemuan Lengkap (Tabel detail Kelas 10-12 Ganjil & Genap).
  - [x] Panduan Format 9 Bagian Siswa dengan integrasi nilai pesantren (hikmah keteraturan & pemecahan masalah harian).
  - [x] Standar Notasi Rumus KaTeX (Eksponen, Logaritma, Matriks, Trigonometri, Limit, Turunan, Integral, Geometri Dimensi 3, Statistika, Peluang).
- [x] **Fase 4: Pembaruan Dokumentasi Proyek (`README.md`)**
  - [x] Update tabel matriks peran pada `README.md` menambahkan `skills/matematika-sma`.

---

## 5. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Terdapat notasi matematika yang ambigu jika disalin mentah dari dokumen sumber (seperti `nn+12`, `51-1=4`, `x-2x+2x-2`).
- **Mitigasi**: Di dalam `prompt.md` ditegaskan secara ketat bahwa agen WAJIB mengonversi seluruh ekspresi matematika ke notasi KaTeX yang sempurna (misalnya `\frac{n(n+1)}{2}`, `5^1 - 1 = 4`, `\frac{(x-2)(x+2)}{x-2}`).
- **Potensi Risiko**: Integrasi nilai pesantren terkesan dipaksakan atau mengurangi kedalaman matematika.
- **Mitigasi**: Nilai pesantren difokuskan pada pengantar makna (hikmah keteraturan alam semesta ciptaan Allah SWT) dan studi kasus soal cerita nyata santri (hafalan Al-Qur'an, zakat/infak, jadwal piket/marbot, konsumsi asrama, waktu sholat/ibadah), sementara konsep matematika tetap diajarkan dengan rigoritas ilmiah standar SMA Jurusan IPA.

---

> **COMPLETED**: Seluruh tahapan rencana implementasi telah dieksekusi dengan lengkap. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` telah aktif dan siap digunakan di `skills/matematika-sma/`.

