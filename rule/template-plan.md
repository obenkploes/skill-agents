# IMPLEMENTATION PLAN: [NAMA FITUR / PROYEK]

- **Tanggal Pembuatan**: YYYY-MM-DD
- **Kategori**: [backend / frontend / materi-tutor / database / system-analyst]
- **Lokasi Berkas**: `.plan/YYYY-MM-DD-<nama-fitur-atau-proyek>.md` (wajib disimpan di root proyek yang sedang aktif dikerjakan)
- **Status**: Menunggu Persetujuan
- **Estimasi Kompleksitas**: [Rendah / Sedang / Tinggi]

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Penjelasan ringkas mengenai kendala atau kebutuhan bisnis/sistem yang mendasari pembuatan modul ini.
- **Goals**: Target konkret yang harus tercapai setelah implementasi selesai.
- **Out of Scope**: Batasan fitur atau aspek teknis yang tidak ditangani pada siklus pengerjaan saat ini.

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Package / Library Baru**:
  - `nama-paket` (versi): Alasan teknis penambahan dependensi.
- **Environment Variables (.env)**:
  - `KEY_NAME`: Deskripsi peruntukan variabel tanpa mencantumkan nilai rahasia.
- **Database Changes**:
  - Tabel baru / modifikasi skema: `nama_tabel`.
  - Catatan indeks, relasi foreign key, atau constraint khusus.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
path/ke/proyek/
├── subfolder/
│   ├── FileBaru.ext          # [Baru] Deskripsi peran dan fungsionalitas berkas
│   └── FileLama.ext          # [Ubah] Titik modifikasi logika atau penambahan routing
```

### Rancangan Kontrak / Interface (Khusus API / Service)
- **Method & URI**: `POST /api/v1/resource`
- **Request Payload**:
  ```json
  {
    "field_name": "tipe_data"
  }
  ```
- **Response Format**:
  ```json
  {
    "status": "success",
    "data": {}
  }
  ```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [ ] **Fase 1: Fondasi & Konfigurasi Data**
  - [ ] Pembuatan berkas migrasi database dan seeder data dummy
  - [ ] Penambahan konfigurasi environment atau registrasi dependensi package
- [ ] **Fase 2: Logika Bisnis & Core Engine**
  - [ ] Implementasi class service atau domain logic layer
  - [ ] Pembuatan skema validasi request (Form Request / Payload Validation)
- [ ] **Fase 3: Integrasi & Antarmuka**
  - [ ] Pembuatan controller handler, API route, atau komponen UI antarmuka
  - [ ] Integrasi state management dan error handler terpusat
- [ ] **Fase 4: Verifikasi & Audit Kinerja**
  - [ ] Pengujian fungsionalitas setiap alur checklist
  - [ ] Evaluasi performa query (pencegahan masalah N+1 query, pemanfaatan indeks)

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Potensi konflik dependensi, performa database overhead, atau breaking changes pada sistem yang sudah ada.
- **Mitigasi**: Langkah pencegahan terukur yang disiapkan sebelum atau selama eksekusi kode.

---

> **AWAITING APPROVAL**: Dokumen perencanaan ini berada dalam status menunggu peninjauan dan persetujuan dari pengguna. Berkas otomatis dibuka untuk ditinjau. Berikan masukan/revisi atau konfirmasi dengan instruksi "Lanjutkan" / "Eksekusi" sebelum pengerjaan kode dimulai.

> **AWAITING APPROVAL**: Dokumen perencanaan ini berada dalam status menunggu peninjauan dan persetujuan dari pengguna. Berkas otomatis dibuka untuk ditinjau. Berikan masukan/revisi atau konfirmasi dengan instruksi "Lanjutkan" / "Eksekusi" sebelum pengerjaan kode dimulai.