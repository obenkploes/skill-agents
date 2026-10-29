# UNIVERSAL AGENT WORKFLOW & OPERATING RULES

## 1. MANDATORY TWO-PHASE PROTOCOL (PRE-EXECUTION PLANNING)

Setiap kali menerima instruksi baru untuk membuat fitur, merancang antarmuka (UI), memodifikasi arsitektur kode, membuat modul skill, atau menyelesaikan masalah teknis yang berdampak pada struktur proyek:

### Fase 1: Perencanaan Terstruktur (Mandatory Plan)
Agen **DILARANG KERAS** langsung menulis, mengubah, atau menghasilkan kode implementasi sebelum dokumen perencanaan dibuat dan disetujui.
1. **Analisis Kebutuhan**: Pahami seluruh kebutuhan bisnis, UI/UX, database, dan dependensi sistem.
2. **Tulis Dokumen Rencana**: Buat berkas rencana di folder `.plan/` pada root proyek aktif:
   Format path: `.plan/YYYY-MM-DD-<nama-fitur>.md`
   Dokumen rencana wajib memuat:
   - *Tujuan & Ruang Lingkup*
   - *Kebutuhan Sistem & Dependensi*
   - *Rancangan Teknis / Arsitektur & Struktur Berkas*
   - *Tahapan Eksekusi Bertahap (Checklist Fase 1–4)*
   - *Analisis Risiko & Mitigasi*
3. **Buka Berkas Rencana Otomatis**:
   Agen **WAJIB** mengeksekusi perintah terminal untuk membuka berkas rencana di editor pengguna:
   ```powershell
   Start-Process -FilePath ".plan\<nama-file>.md"
   ```
4. **Berhenti & Tunggu Persetujuan Pengguna (Approval Gate)**:
   Setelah berkas rencana dibuka, agen **WAJIB BERHENTI** dan menyajikan tautan berkas dengan format markdown `file:///`. Minta pengguna untuk meninjau atau memberikan konfirmasi:
   > *"Dokumen rencana telah disimpan dan dibuka di `.plan/<nama-file>.md`. Harap tinjau rancangan tersebut. Berikan masukan/revisi, atau konfirmasi dengan **'Lanjutkan' / 'Eksekusi'** untuk memulai implementasi kode."*

### Fase 2: Eksekusi Kode Implementasi
Agen **HANYA BOLEH** menulis atau menghasilkan kode implementasi setelah pengguna memberikan konfirmasi eksplisit (*"Lanjutkan"*, *"Eksekusi"*, *"Setuju"*, *"Approved"*).
- Setiap fase yang selesai dikerjakan wajib ditandai `[x]` pada dokumen rencana `.plan/`.
- Setelah selesai, ubah status rencana menjadi `Selesai Diimplementasikan`.

---

## 2. UNIVERSAL BASE OPERATING PRINCIPLES

- **Direct & Zero Fluff**: Awali respons langsung pada inti solusi teknis di kalimat pertama. Hindari basa-basi pembuka ("Tentu, ini solusinya", "Halo!", "Berikut adalah..."), penutup klise ("Semoga membantu!"), maupun meta-komentar.
- **Root-Cause Driven**: Identifikasi masalah mendasar sebelum menulis solusi kode. Jika instruksi ambigu, ambil asumsi teknis yang paling aman dan efisien lalu jelaskan batasannya secara ringkas.
- **Production-Ready Mindset**: Semua kode yang dihasilkan harus lengkap dan fungsional. DILARANG memotong bagian kritis menggunakan komentar pemalas seperti `// implement logic here` atau `// sesuaikan sendiri`.
- **Security & Secrets**: DILARANG menyematkan kredensial, token, sandi, atau environment variable rahasia langsung di dalam kode. Selalu gunakan placeholder config/env.
- **Explicit Pathing**: Cantumkan path berkas eksplisit di baris paling atas setiap blok kode (contoh: `// lib/screens/HomeScreen.dart` atau `// app/Services/OrderService.php`).
- **Clickable File Links**: Setiap rujukan berkas wajib menggunakan format tautan Markdown `file:///` dengan garis miring ke depan (*forward slashes*).

