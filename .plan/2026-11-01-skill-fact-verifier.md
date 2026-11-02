# IMPLEMENTATION PLAN: MODUL SKILL FACT VERIFIER & NEWS AGGREGATOR

- **Tanggal Pembuatan**: 2026-11-01
- **Kategori**: intelligence / fact-checking / verification
- **Lokasi Berkas**: `.plan/2026-11-01-skill-fact-verifier.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang (Multi-Source Verification & Verbatim Media Extraction Protocol)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Pengguna membutuhkan modul keahlian agen (*skill agent*) baru bernama `fact-verifier` yang secara ketat bertugas mengumpulkan fakta, menguji klaim atau isu viral dari media sosial, menyilangkannya dengan saluran berita resmi terpercaya (*multi-sourcing*, minimal 2 sumber independen), dan menyajikan laporan verifikasi yang **tidak hanya memuat rangkuman/parafrase AI**, melainkan menyajikan **petikan teks berita asli dan kutipan langsung narasumber (*primary verbatim quotes*)**. Hal ini penting agar pengguna dapat melakukan telaah dan analisis mandiri secara objektif tanpa bias ringkasan.

### Goals
1. **Penyusunan Modul Skill Terstandar Antigravity** di `skills/fact-verifier/`:
   - `skill.json`: Metadata, triggers (`@fakta`, `/fakta`, `/cekfakta`, `/fact-check`, `/verifikasi`), kata kunci, dan rujukan aturan universal.
   - `SKILL.md`: Entrypoint Antigravity dengan frontmatter YAML resmi, metodologi validasi multi-sourcing, daftar putih sumber terpercaya (*whitelisted media*), dan format output standar.
   - `prompt.md`: System prompt spesialis pemeriksa fakta investigatif (SOP penelusuran web, protokol ekstraksi petikan berita asli tanpa parafrase, taksonomi manipulasi standar IFCN, analisis kesenjangan konteks / *gap analysis*, dan penilaian derajat keyakinan bukti).
2. **Penerapan Metodologi Verifikasi Ketat**:
   - **Aturan Multi-Sourcing (Minimal 2 Sumber Resmi)**: Tidak pernah menyimpulkan fakta hanya dari satu artikel atau satu pernyataan sepihak.
   - **Daftar Putih Sumber Otoritatif (Whitelisted Tier)**:
     - Media Nasional Terakreditasi Dewan Pers: Antara News, Kompas, Tempo, Tirto, Detik, CNN Indonesia, BBC News Indonesia.
     - Kantor Berita Internasional: Reuters, AP News, AFP, Bloomberg.
     - Portal Pemeriksa Fakta Bersertifikasi IFCN: TurnBackHoax.id (Mafindo), CekFakta.com, Kompas Cek Fakta, Tempo CekFakta, Liputan6 Cek Fakta.
     - Kanal Resmi Pemerintah/Instansi: Rilis pers Humas Polri, BMKG, Kemenkes, BPS, kementerian/lembaga terkait.
   - **Tabel Komparasi Berdampingan**: Membandingkan klaim warganet vs fakta resmi lapangan (Narasi, Konteks Waktu/Tempat, Aktor).
   - **Penyajian Teks Asli (*Verbatim Excerpts*)**: Menyertakan 2–3 paragraf teks berita asli dan kutipan langsung pejabat/narasumber (*direct quotes*) lengkap dengan tanggal, jam, dan nama media.
   - **Analisis Kesenjangan Konteks (*Context Gap Analysis*)**: Menunjukkan secara spesifik bagian video/kalimat mana yang dipotong (*cropped/truncated*) atau dipelintir oleh pembuat konten viral.
3. **Pembaruan Katalog Proyek**:
   - Memperbarui diagram pohon direktori di `README.md`.
   - Menambahkan contoh trigger `@fakta` pada daftar penggunaan harian.
   - Mendaftarkan baris `fact-verifier` pada tabel matriks peran katalog.

### Out of Scope
- Tidak menggunakan blog anonim, akun agregator gosip medsos, atau situs tanpa redaksi pers yang jelas sebagai rujukan fakta penentu.

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI

### Alat & Protokol yang Digunakan
- **Web Search Engine Tool (`search_web`)**: Menelusuri artikel berita dari media terakreditasi dan portal cek fakta.
- **Rujukan Aturan Invariant**:
  - `rules/AGENTS.md`: Prinsip *Zero Fluff*, *Root-Cause Driven*, batasan keamanan, dan respons langsung.
- **Standar Taksonomi IFCN (International Fact-Checking Network)**:
  - *False Context* (Konteks Menyesatkan)
  - *Manipulated Content* (Rekayasa Gambar/Suara/AI)
  - *Fabricated Content* (Pabrikasi/Hoaks Total)
  - *Misleading Content* (Pelintiran Fakta)

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-11-01-skill-fact-verifier.md       # [Baru] Dokumen perencanaan implementasi modul
├── skills/
│   └── fact-verifier/                          # [Baru] Direktori modul skill Fact Verifier
│       ├── skill.json                          # [Baru] Metadata skill & triggers CLI/chat
│       ├── SKILL.md                            # [Baru] Dokumentasi kapabilitas & standar sumber terpercaya
│       └── prompt.md                           # [Baru] System prompt spesialis pemeriksa fakta & ekstraksi teks asli
└── README.md                                   # [Update] Registrasi pada katalog modul proyek
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Direktori (`skills/fact-verifier/skill.json`)**
  - [x] Pembuatan direktori `skills/fact-verifier`.
  - [x] Pembuatan berkas `skill.json` memuat properti `name: "fact-verifier"`, `category: "intelligence"`, triggers (`@fakta`, `/fakta`, `/cekfakta`, `/fact-check`, `/verifikasi`), kata kunci, dan rujukan ke `rules/AGENTS.md`.
- [x] **Fase 2: Pembuatan Entrypoint Antigravity (`skills/fact-verifier/SKILL.md`)**
  - [x] Frontmatter YAML resmi dengan peringatan `MANDATORY WORKFLOW`.
  - [x] Deskripsi peran, kapan harus digunakan, protokol multi-sourcing, whitelist sumber, dan format output terstruktur.
- [x] **Fase 3: Penyusunan System Prompt Spesialis (`skills/fact-verifier/prompt.md`)**
  - [x] Persona *Senior Fact-Checker & Investigative Intelligence Verifier*.
  - [x] Protokol penelusuran fakta terarah dan uji silang (*triangulasi data*).
  - [x] Aturan ketat penyajian teks berita asli dan kutipan langsung narasumber (*verbatim quotes*).
  - [x] Format output lengkap 4 bagian (Deskripsi & Tabel Komparasi, Isi Berita Asli Sumber Terpercaya, Analisis Kesenjangan Konteks, dan Daftar Tautan Resmi).
- [x] **Fase 4: Pembaruan Dokumentasi Repositori (`README.md`)**
  - [x] Update struktur pohon folder direktori `skills/`.
  - [x] Update daftar pemanggilan skill di chat (`@fakta` / `/fakta`).
  - [x] Update tabel matriks katalog modul skill.

---

## 5. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Parafrase atau ringkasan AI dapat secara tidak sengaja mengubah makna hukum/pernyataan narasumber (misal: kata "diduga" atau "indikasi" terhapus).
- **Mitigasi**: Di dalam `prompt.md` diwajibkan menyertakan blok *blockquote* kutipan teks berita asli kata-per-kata dari media arus utama, sehingga pengguna dapat mengonfirmasi redaksi aslinya secara langsung.
- **Potensi Risiko**: Informasi masih sangat baru sehingga media arus utama belum menerbitkan artikel klarifikasi.
- **Mitigasi**: Memberikan label status tegas `[Klaim Sepihak Belum Terkonfirmasi]` disertai tingkat keyakinan bukti `[Rendah]`, serta menjelaskan batas fakta yang saat ini sudah diketahui vs apa yang masih spekulasi.

---

> **COMPLETED**: Seluruh tahapan rencana implementasi telah dieksekusi dengan lengkap. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` telah aktif dan siap digunakan di `skills/fact-verifier/`.

