## WORKFLOW PROTOCOL: PRE-EXECUTION PLANNING

Setiap pembuatan proyek baru, penambahan fitur skala besar, atau perubahan arsitektur wajib mematuhi protokol dua fase berikut:

### 1. FASE PERENCANAAN (MANDATORY PLANNING)
- DILARANG menulis atau mengeksekusi kode implementasi sebelum dokumen perencanaan dibuat dan disetujui pengguna.
- Dokumen rencana pelaksanaan **WAJIB disimpan di dalam direktori `.plan/` pada root folder proyek yang sedang aktif dikerjakan** (`<workspace-root>/.plan/`). Jika folder `.plan/` belum tersedia di proyek target, agent wajib membuat direktori tersebut terlebih dahulu.
- Konvensi penamaan berkas:
  `.plan/YYYY-MM-DD-<nama-fitur-atau-proyek>.md`
- Dokumen perencanaan di dalam folder `.plan/` wajib memuat:
  1. **Tujuan & Ruang Lingkup**: Masalah yang diselesaikan dan batasan teknis.
  2. **Daftar Kebutuhan**: Package/dependensi baru, skema database, atau konfigurasi environment.
  3. **Rancangan Teknis / Arsitektur**: Struktur berkas baru/diubah, rancangan endpoint/interface, atau skema relasi data.
  4. **Tahapan Eksekusi Bertahap (Checklist)**: Langkah pengerjaan berurutan dari fundamental (skema/model) hingga antarmuka/pengujian.
  5. **Analisis Risiko & Mitigasi**: Kemungkinan konflik dependensi, performa (overhead), atau celah keamanan.

### 2. OTOMATIS BUKA BERKAS & GATE PERSETUJUAN (AUTO-OPEN & AWAITING APPROVAL)
- **Otomatis Buka Berkas**: Segera setelah berkas rencana dibuat di folder `.plan/`, agent **WAJIB membuka berkas tersebut secara otomatis** di editor (misalnya menjalankan perintah pembuka editor seperti `code .plan/<nama-file>.md` atau menyajikan tautan aktif `file:///`) agar pengguna dapat langsung membaca draf perencanaannya di jendela kerja.
- **Berhenti & Meminta Keputusan Pengguna**: Agent wajib berhenti dan meminta konfirmasi eksplisit dari pengguna: apakah pengguna ingin melakukan peninjauan/revisi atau langsung menyetujui eksekusi.
- **Format Baku Penutup Prompt Perencanaan**:
  > Dokumen rencana telah disimpan dan dibuka di `[.plan/<nama-file>.md](file:///<path-ke-file>)`. Harap tinjau rancangan tersebut. Anda dapat memberikan masukan/revisi, atau konfirmasi dengan **"Lanjutkan" / "Eksekusi"** untuk memulai implementasi kode.
- **Kondisi Eksekusi**: Agent HANYA boleh mengeksekusi kode implementasi setelah menerima instruksi persetujuan eksplisit (seperti *"Lanjutkan"*, *"Eksekusi"*, *"Approved"*, atau arahan revisi dari pengguna).
