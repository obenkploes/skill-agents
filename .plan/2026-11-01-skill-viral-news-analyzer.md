# IMPLEMENTATION PLAN: MODUL SKILL VIRAL NEWS ANALYZER

- **Tanggal Pembuatan**: 2026-11-01
- **Kategori**: intelligence / media-monitoring / analysis
- **Lokasi Berkas**: `.plan/2026-11-01-skill-viral-news-analyzer.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang (Intelligence Synthesis, Fact-Checking, & Sentiment Polarization Protocol)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Pengguna membutuhkan modul keahlian agen (*skill agent*) baru bernama `viral-news-analyzer` untuk memantau, memverifikasi, menganalisis sentimen, dan menyusun laporan terstruktur mengenai topik, isu, atau peristiwa yang sedang viral di media sosial (TikTok, Instagram, X/Twitter, Facebook, dll.). Modul ini harus mampu menyajikan data yang tidak hanya berupa kliping berita biasa, melainkan laporan intelijen tren yang informatif, terukur, dan siap digunakan untuk pengambilan keputusan atau analisis lanjutan.

### Goals
1. **Penyusunan Modul Skill Terstandar Antigravity** di `skills/viral-news-analyzer/`:
   - `skill.json`: Metadata, triggers (`@viral`, `/viral`, `/trend-analyzer`, `/isu-viral`, `/social-listening`), keywords, dependensi, dan rujukan rules.
   - `SKILL.md`: Entrypoint skill Antigravity dengan frontmatter YAML resmi, metodologi analisis, aturan invariant, dan panduan trigger.
   - `prompt.md`: System prompt spesialis media monitoring & intelligence analysis komprehensif (protokol targeted search, triangulasi media arus utama, taksonomi cek fakta, dekonstruksi polarisasi sentimen, dan matriks risiko).
2. **Implementasi Metodologi Analisis Terukur**:
   - **Alur Kerja Pencarian Cerdas & Triangulasi**: Menghubungkan agen dengan pencarian web terarah ke media arus utama dan database pemeriksa fakta resmi (TurnBackHoax, CekFakta, dll.).
   - **Parameter Analisis Komprehensif**:
     - *Kategori Isu*: Politik & Kebijakan, Hukum & Kriminal, Bisnis & Brand, Sosial & Humaniora, Gaya Hidup & Pop Culture.
     - *Siklus Tren (Virality Lifecycle)*: Emerging, Peak, Cooling Down.
     - *Tingkat Dampak (Risk Level)*: Tinggi/Kritis, Sedang, Rendah.
     - *Polarisasi Opini*: Pemetaan argumen kunci kubu pro vs kubu kontra beserta stakeholder terdampak.
     - *Status Verifikasi Cek Fakta*: Terverifikasi Fakta, Konteks Menyesatkan (*Misleading*), Manipulasi/Hoaks, atau Klaim Sepihak Belum Terbukti.
     - *Indikator Gerakan*: Organik Publik vs Terindikasi Buzzer/Bot.
3. **Format Output Standar 2 Lapis**:
   - *Lapis 1*: **Tabel Matriks Executive Summary** di bagian pembuka untuk pandangan cepat (*quick scan*).
   - *Lapis 2*: **Laporan Analisis Mendalam per Isu** (Identitas, Kronologi, Polarisasi Sentimen, Cek Fakta, Implikasi Strategis).
4. **Pembaruan Katalog Proyek**:
   - Memperbarui `README.md` pada struktur folder, daftar pemanggilan skill, dan tabel matriks peran.

### Out of Scope
- Tidak melakukan crawling atau scraping ilegal langsung ke database privat platform media sosial (menggunakan pendekatan pencarian web cerdas, liputan berita arus utama terindeks, data cek fakta, dan analisis data masukan pengguna).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI

### Alat & Protokol yang Digunakan
- **Web Search Engine Tool (`search_web`)**: Untuk menelusuri artikel berita terindeks, pernyataan resmi, dan data cek fakta.
- **Rujukan Aturan Invariant**:
  - `rules/AGENTS.md`: Prinsip *Zero Fluff*, *Root-Cause Driven*, dan format respons langsung.
- **Dukungan Format Data**:
  - Format tabel Markdown Github-Flavored Markdown (GFM).
  - Format blok data terstruktur (opsional JSON untuk diekspor ke Pandas/Excel).

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-11-01-skill-viral-news-analyzer.md  # [Baru] Dokumen rencana implementasi
├── skills/
│   └── viral-news-analyzer/                     # [Baru] Direktori modul skill
│       ├── skill.json                           # [Baru] Metadata skill & triggers CLI/chat
│       ├── SKILL.md                             # [Baru] Deskripsi skill, alur kerja, & format output
│       └── prompt.md                            # [Baru] System prompt spesialis media monitoring & sentiment
└── README.md                                    # [Update] Registrasi katalog dan panduan pemanggilan
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Direktori (`skills/viral-news-analyzer/skill.json`)**
  - [x] Pembuatan direktori `skills/viral-news-analyzer`.
  - [x] Pembuatan berkas `skill.json` memuat properti `name: "viral-news-analyzer"`, `category: "intelligence"`, triggers (`@viral`, `/viral`, dll.), keywords, dan aturan rujukan.
- [x] **Fase 2: Pembuatan Entrypoint Antigravity (`skills/viral-news-analyzer/SKILL.md`)**
  - [x] Frontmatter YAML resmi dengan peringatan `MANDATORY WORKFLOW`.
  - [x] Penjelasan kapan skill digunakan, metodologi triangulasi & akurasi, dan struktur format output.
- [x] **Fase 3: Penyusunan System Prompt Spesialis (`skills/viral-news-analyzer/prompt.md`)**
  - [x] Panduan persona *Senior Media Intelligence & Social Sentiment Analyst*.
  - [x] Standard Operating Procedure (SOP) pencarian berita viral (Skenario Trend Discovery vs Deep-Dive Issue).
  - [x] Taksonomi cek fakta baku dan pemetaan polarisasi opini publik.
  - [x] Template output lengkap (Tabel Executive Summary, Lembar Analisis Mendalam, dan Implikasi Strategis).
- [x] **Fase 4: Pembaruan Dokumentasi Repositori (`README.md`)**
  - [x] Memperbarui diagram pohon direktori di `README.md`.
  - [x] Menambahkan contoh pemanggilan `@viral` di panduan penggunaan.
  - [x] Menambahkan baris skill `viral-news-analyzer` pada tabel matriks peran.

---

## 5. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Berita viral di media sosial sering kali simpang siur, bias, atau berasal dari akun anonim yang menyebarkan disinformasi.
- **Mitigasi**: Menegakkan protokol wajib verifikasi silang (*cross-checking*) dengan media arus utama bereputasi dan portal cek fakta (Mafindo/TurnBackHoax). Setiap klaim yang belum terkonfirmasi wajib diberi label tegas: `[Klaim Sepihak Belum Terbukti]`.
- **Potensi Risiko**: Analisis sentimen menjadi terlalu subjektif jika hanya mengandalkan satu cuplikan komentar.
- **Mitigasi**: Mengharuskan pemetaan dua kutub narasi (*Kubu Pro vs Kubu Kontra*) dan membedah substansi argumen masing-masing kubu, bukan sekadar pelabelan umum positif/negatif.

---

> **COMPLETED**: Seluruh tahapan rencana implementasi telah dieksekusi dengan lengkap. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` telah aktif dan siap digunakan di `skills/viral-news-analyzer/`.

