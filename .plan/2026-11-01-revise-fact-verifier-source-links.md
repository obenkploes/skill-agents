# IMPLEMENTATION PLAN: REVISI SKILL FACT-VERIFIER (KEWAJIBAN TAUTAN SUMBER BERITA ASLI & REVISI README CLI)

- **Tanggal Pembuatan**: 2026-11-01
- **Kategori**: intelligence / fact-checking / verification / documentation
- **Lokasi Berkas**: `.plan/2026-11-01-revise-fact-verifier-source-links.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Rendah - Sedang (Enforcing Real URL Source Linking & CLI Guide)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
1. **Revisi Skill `/fakta` (`fact-verifier`)**: Pengguna menginstruksikan bahwa setiap hasil verifikasi fakta **WAJIB SELALU menyertakan tautan (link URL) sumber berita aslinya** yang valid dan dapat langsung diklik (*clickable direct link*). Hal ini krusial agar pengguna dapat membuka halaman berita asli di peramban secara mandiri untuk menguji keaslian redaksi, tanggal, dan kredibilitas medianya.
2. **Revisi `README.md`**: Menindaklanjuti permintaan pengguna sebelumnya untuk menambahkan panduan menghubungkan skill repositori ke Antigravity CLI (`agy`) di **Linux** dan **Windows**.

### Goals
1. **Pembaruan `skills/fact-verifier/SKILL.md` & `skills/fact-verifier/prompt.md`**:
   - Menambahkan aturan ketat (*Strict Invariant Rule*): **Wajib Menyertakan Tautan Sumber Asli Nyata (*Mandatory Clickable Real URLs*)**.
   - Setiap rujukan media dan kutipan wajib langsung menyertakan tautan URL aktif dari hasil `search_web` (bukan placeholder teks seperti `[URL Langsung]`).
   - Format tautan wajib mudah diklik dengan mencantumkan nama media, judul artikel, dan URL lengkap: `[Baca Artikel Asli di Kompas.com](https://...)` atau tautan markdown standar.
   - DILARANG mencantumkan kutipan atau klaim verifikasi tanpa menyertakan tautan langsung ke artikel berita resminya.
2. **Pembaruan `README.md` (Integrasi CLI Antigravity)**:
   - Menambahkan panduan setup Windows (NTFS Junction `mklink /J`, `plugins.json`).
   - Menambahkan panduan setup Linux & macOS (Symbolic Link `ln -s`, `plugins.json`).
   - Menambahkan contoh perintah pemanggilan CLI (`agy run "@fakta ..."` dan `@viral`, `/matematika-sma`, dll.).

---

## 2. RANCANGAN STRUKTUR FORMAT OUTPUT SKILL `/FAKTA` YANG DIREVISI

Setiap rujukan pada Bagian 2 (*Isi Berita & Kutipan Asli*) dan Bagian 4 (*Daftar Sumber*) wajib menyematkan tautan URL aktif secara langsung:

```markdown
### A. Rujukan Media 1: [Nama Media Otoritatif]
* **Judul Artikel:** "[Judul Berita Asli]"
* **Tautan Langsung Berita Asli:** 🔗 [Buka Artikel Asli di <NamaMedia>](<URL_AKTIF_HASIL_SEARCH>)
* **Tanggal & Penulis:** [Tanggal, Jam - Jurnalis/Editor]
* **Petikan Paragraf Berita Asli:**
  > "[Kutipan teks berita asli...]"
* **Kutipan Langsung Narasumber (*Direct Quote*):**
  > *"[Pernyataan langsung narasumber...] "*
```

---

## 3. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Revisi `skills/fact-verifier/SKILL.md`**
  - [x] Tambahkan aturan wajib tautan URL aktif (*Mandatory Clickable Real URLs*).
  - [x] Perbarui template format output agar tautan URL disematkan langsung di bawah judul rujukan berita.
- [x] **Fase 2: Revisi `skills/fact-verifier/prompt.md`**
  - [x] Tambahkan klausul bahwa URL yang dicantumkan harus URL nyata yang diperoleh dari tool `search_web` (anti-placeholder, anti-tautan fiktif).
  - [x] Pastikan SOP verifikasi mewajibkan penangkapan URL artikel berita utama dan rilis resmi.
- [x] **Fase 3: Pembaruan `skills/fact-verifier/skill.json`**
  - [x] Perbarui ringkasan deskripsi metadata agar mencakup transparansi tautan sumber asli.
- [x] **Fase 4: Pembaruan `README.md` (Panduan Antigravity CLI Windows & Linux)**
  - [x] Tambahkan panduan koneksi CLI untuk Windows (`mklink /J` & `plugins.json`).
  - [x] Tambahkan panduan koneksi CLI untuk Linux/macOS (`ln -s` & `plugins.json`).
  - [x] Sertakan contoh eksekusi `agy run "@fakta ..."` dan verifikasi ketersediaan skill.

---

## 4. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Model dapat menghasilkan URL fiktif jika tidak diperingatkan dengan tegas.
- **Mitigasi**: Di dalam `prompt.md` ditegaskan bahwa agen HANYA BOLEH menyalin URL yang benar-benar dikembalikan oleh hasil pencarian web `search_web`. Dilarang menebak atau mengarang URL.

---

> **COMPLETED**: Seluruh tahapan rencana revisi telah dieksekusi dengan lengkap. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` pada `skills/fact-verifier/` telah diperbarui untuk mewajibkan tautan URL berita asli aktif, serta panduan CLI pada `README.md` telah disempurnakan.

