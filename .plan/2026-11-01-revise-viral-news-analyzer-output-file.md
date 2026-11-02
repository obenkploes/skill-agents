# IMPLEMENTATION PLAN: REVISI SKILL VIRAL NEWS ANALYZER (OTOMASI OUTPUT BERKAS .MD)

- **Tanggal Pembuatan**: 2026-11-01
- **Kategori**: intelligence / media-monitoring / revision
- **Lokasi Berkas**: `.plan/2026-11-01-revise-viral-news-analyzer-output-file.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Rendah - Sedang (Instruction & Output Protocol Revision)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Pengguna menginstruksikan revisi pada skill `@viral` (`viral-news-analyzer`) agar setiap kali skill ini dijalankan, agen tidak hanya menampilkan teks markdown di jendela percakapan, melainkan **wajib menghasilkan dan menyimpan laporan analisis lengkap ke dalam berkas fisik `.md`** di workspace proyek. Berkas ini berfungsi sebagai arsip laporan intelijen tren yang dapat disimpan, diedit, atau dibagikan secara mandiri.

### Goals
1. **Memperbarui Aturan Eksekusi pada `skills/viral-news-analyzer/SKILL.md`**:
   - Menambahkan instruksi eksplisit bahwa output laporan akhir wajib disimpan ke berkas Markdown (`.md`).
   - Menyertakan konvensi penamaan berkas dan direktori output terstandar: `reports/viral/YYYY-MM-DD-<slug-topik>.md` (atau direktori `viral-reports/`).
   - Agen wajib menyajikan tautan berkas klikable `file:///` di jendela chat setelah berkas berhasil disimpan.
2. **Memperbarui Panduan Operasional pada `skills/viral-news-analyzer/prompt.md`**:
   - Mengintegrasikan SOP pembuatan berkas Markdown:
     1. Penyusunan konten laporan lengkap (Tabel Executive Summary + Laporan Analisis Mendalam).
     2. Penulisan ke berkas dengan tool `write_file` pada path `reports/viral/YYYY-MM-DD-<nama-isu>.md`.
     3. Penyajian ringkasan eksekutif di chat disertai tautan berkas `file:///`.
3. **Memperbarui Metadata `skills/viral-news-analyzer/skill.json`**:
   - Memastikan deskripsi mencerminkan kapabilitas pembuatan berkas laporan `.md`.

### Out of Scope
- Tidak mengubah metodologi analisis inti (tetap mempertahankan verifikasi cek fakta, dekonstruksi polarisasi pro-kontra, dan penilaian tingkat risiko).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI

### Konvensi Berkas Output
- **Folder Penyimpanan**: `reports/viral/` (otomatis dibuat jika belum ada).
- **Format Penamaan Berkas**: `YYYY-MM-DD-<slug-topik-viral>.md`
  - Contoh: `reports/viral/2026-11-01-boikot-brand-x.md`
  - Contoh kompilasi harian: `reports/viral/2026-11-01-tren-harian-medsos.md`
- **Standar Format Isi Berkas**:
  - Frontmatter metadata laporan (*title, date, category, dominant_sentiment, risk_level, verification_status*).
  - Tabel Matriks Executive Summary.
  - Lembar Analisis Mendalam per Isu (Identitas, Kronologi, Polarisasi Sentimen, Cek Fakta, Implikasi Strategis).
  - Blok JSON data terstruktur siap ekspor.

---

## 3. RANCANGAN PERUBAHAN BERKAS

```text
skills/viral-news-analyzer/
├── skill.json     # [Update] Perbarui deskripsi kapabilitas ekspor berkas .md
├── SKILL.md       # [Update] Tambahkan aturan wajib output berkas .md dan struktur path
└── prompt.md      # [Update] Tambahkan langkah wajib penulisan berkas fisik .md dan template frontmatter
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Pembaruan `skills/viral-news-analyzer/SKILL.md`**
  - [x] Tambahkan klausul protokol wajib penyimpanan berkas `.md` di `reports/viral/YYYY-MM-DD-<slug-topik>.md`.
  - [x] Tambahkan format tautan klikable `file:///` pada chat respons.
- [x] **Fase 2: Pembaruan `skills/viral-news-analyzer/prompt.md`**
  - [x] Tambahkan bagian *"File Output Generation Protocol"* pada alur eksekusi Skenario A & B.
  - [x] Sertakan standar metadata frontmatter YAML di dalam berkas laporan `.md`.
- [x] **Fase 3: Pembaruan `skills/viral-news-analyzer/skill.json`**
  - [x] Perbarui ringkasan deskripsi metadata.
- [x] **Fase 4: Verifikasi & Uji Konsistensi**
  - [x] Pastikan instruksi selaras dengan aturan universal `rules/AGENTS.md`.

---

## 5. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Berkas lama tertimpa (*overwrite*) jika ada beberapa isu dianalisis pada hari yang sama.
- **Mitigasi**: Menggunakan slug topik yang unik pada nama berkas: `YYYY-MM-DD-<slug-topik>.md` (bukan sekadar `YYYY-MM-DD.md`).

---

> **COMPLETED**: Seluruh tahapan rencana revisi telah dieksekusi dengan lengkap. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` pada `skills/viral-news-analyzer/` telah diperbarui untuk mewajibkan output berkas `.md` di `reports/viral/`.

