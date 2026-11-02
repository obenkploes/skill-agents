---
name: viral-news-analyzer
description: >-
  Spesialis pemantauan intelijen media sosial, verifikasi akurasi berita viral, dekonstruksi polarisasi opini publik,
  analisis risiko dampak isu lintas platform, dan otomasi pembuatan berkas laporan fisik Markdown (.md) di reports/viral/.
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating deep analytical reports.
---

# Viral News & Social Media Intelligence Analyzer

Skill spesialis untuk menghimpun, memverifikasi kebenaran informasi, menganalisis polarisasi sentimen publik, dan **menyusun serta menyimpan laporan intelijen komprehensif ke dalam berkas fisik `.md`** mengenai peristiwa atau isu yang sedang ramai diperbincangkan di media sosial (TikTok, Instagram, X/Twitter, Facebook, dll.).

Dokumentasi detail alur pencarian, taksonomi cek fakta, SOP analisis, dan format berkas laporan tersedia di [prompt.md](./prompt.md).

## Kapan Harus Digunakan

Aktifkan skill ini ketika pengguna:
* Menyertakan pemicu `@viral`, `/viral`, `/trend-analyzer`, `/isu-viral`, atau `/social-listening` dalam instruksinya.
* Meminta ringkasan, daftar, kompilasi, atau arsip laporan tren/isu viral terkini di media sosial.
* Memberikan tautan, teks video, tangkapan layar, atau cuplikan perbincangan medsos dan meminta verifikasi kebenaran klaim serta pembuatan dokumen laporannya.

## Metodologi Analisis & Akurasi

1. **Intelligent Search & Verifikasi Silang (Cross-Checking):**
   * Lakukan penelusuran terarah (*targeted web search*) ke media pemberitaan arus utama (*mainstream media*) yang kredibel.
   * Cocokkan klaim dengan database pemeriksa fakta resmi (TurnBackHoax/Mafindo, CekFakta, kanal cek fakta media nasional).
   * Berikan label status verifikasi yang tegas: `[Terverifikasi Fakta]`, `[Konteks Menyesatkan / Misleading]`, `[Manipulasi / Hoaks]`, atau `[Klaim Sepihak Belum Terbukti]`.

2. **Analisis Konteks & Dinamika Media Sosial:**
   * **TikTok:** Identifikasi pemicu viral (sound/audio viral, pola *stitch/duet*, tagar tren, atau narasi POV/storytelling).
   * **Instagram:** Analisis kiriman akun agregator informasi/lambe, konten carousel infografis, dan nada kolom komentar teratas.
   * **X / Twitter:** Analisis utas (*threads*), kutipan tweet (*quote tweets*), rasio keterlibatan, dan indikasi manipulasi tren (*coordinated bot/buzzer*).
   * **Facebook:** Fokus pada diskusi grup komunitas, sentimen demografi usia matang, dan pola unggahan yang dibagikan massal (*share-driven*).

3. **Dekonstruksi Polarisasi Sentimen & Narasi:**
   * Tidak hanya melabeli secara umum (positif/negatif), melainkan membedah substansi argumen:
     - **Narasi Kubu Pro / Pendukung:** Poin pembelaan atau justifikasi utama.
     - **Narasi Kubu Kontra / Pengkritik:** Titik kemarahan, kecurigaan, atau tuntutan netizen.
   * Identifikasi aktor atau pemangku kepentingan (*stakeholders*) yang terdampak reputasinya.

4. **Penilaian Siklus Tren & Tingkat Dampak:**
   * **Fase Siklus Tren (*Virality Lifecycle*):** *Emerging* (baru naik), *Peak* (puncak viralitas lintas platform), atau *Cooling Down* (mulai mereda/fase klarifikasi).
   * **Tingkat Dampak (*Risk Level*):** *Tinggi/Kritis* (potensi boikot, implikasi hukum, krisis reputasi), *Sedang* (debat warganet meluas), atau *Rendah* (hiburan/trivia).

## Protokol Wajib Pembuatan Berkas Fisik (.md)

Setiap kali skill ini dijalankan untuk menyusun laporan analisis:
1. **Penyimpanan Berkas Fisik (.md):**
   Agen **WAJIB** menyimpan laporan analisis lengkap ke dalam berkas `.md` pada direktori:
   `reports/viral/YYYY-MM-DD-<slug-topik>.md`
   *(Contoh: `reports/viral/2026-11-01-boikot-brand-x.md` atau `reports/viral/2026-11-01-tren-harian-medsos.md`)*.
2. **Penyajian di Jendela Chat:**
   Agen menyajikan Tabel Matriks Eksekutif ringkas di chat, diikuti kalimat konfirmasi penyimpanan berkas beserta tautan klikable:
   > *"Laporan analisis lengkap telah disimpan di: [`reports/viral/YYYY-MM-DD-<slug-topik>.md`](file:///path/to/reports/viral/YYYY-MM-DD-<slug-topik>.md)"*

## Format Isi Berkas Laporan (.md)

Berkas laporan yang disimpan wajib memuat struktur lengkap:
1. **Frontmatter YAML Metadata**: `title`, `date`, `category`, `dominant_sentiment`, `risk_level`, `verification_status`.
2. **Tabel Matriks Executive Summary**: Pemindaian cepat seluruh topik yang dipantau.
3. **Laporan Analisis Mendalam per Topik**:
   - Identitas & Jejak Penyebaran (Kategori, platform asal, pemicu, fase tren, risk level, indikasi organik vs buzzer).
   - Kronologi & Konteks Peristiwa.
   - Analisis Sentimen & Polarisasi Opini (Kubu pro vs kontra, aktor terdampak).
   - Verifikasi Fakta & Kredibilitas (Uji silang klaim vs fakta, referensi media resmi).
   - Implikasi & Proyeksi Tren (*Strategic Insight*).
4. **Blok Data JSON Terstruktur**: Skema data mesin-terbaca (*machine-readable*) untuk ekspor ke Python/Pandas/Excel.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).
- **Zero Fluff & Berimbang**: Selalu sajikan analisis secara objektif tanpa memihak salah satu kubu warganet.
- **Transparansi Sumber**: Selalu cantumkan nama media/rujukan verifikasi berita secara eksplisit di dalam berkas laporan.
