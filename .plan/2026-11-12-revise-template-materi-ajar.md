# IMPLEMENTATION PLAN: REVISI TEMPLATE MATERI AJAR & SINKRONISASI SKILL SMP/SMA (SIKLUS 80 MENIT/MINGGU)

- **Tanggal Pembuatan**: 2026-11-12
- **Kategori**: curriculum-architecture / template-maintenance
- **Lokasi Berkas**: `.plan/2026-11-12-revise-template-materi-ajar.md`
- **Status**: Selesai Diimplementasikan (Completed)
- **Estimasi Kompleksitas**: Sedang (Pedagogical Re-scaffolding & Cross-File Alignment)

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**:
  Hasil evaluasi terhadap `rules/templates/template-materi-ajar.md` serta implementasinya pada `skills/matematika-smp/` dan `skills/matematika-sma/` menunjukkan tiga kendala utama saat digunakan untuk pembelajaran **80 menit per pertemuan (1 kali seminggu)**:
  1. **Bias abstraksi SMA & tidak adanya batas beban 80 menit**, sehingga modul sering terlalu padat untuk selesai di kelas.
  2. **Loncatan kesulitan (*scaffolding gap*) terlalu curam**: contoh soal langsung melompat ke manipulasi pecahan/akar/transpos (hanya 2 contoh), sedangkan `Latihan Soal` hanya menyediakan 2 soal dasar sebelum memaksa soal campuran pecahan/akar dan HOTS pembuktian.
  3. **Urutan kurang tepat & fitur cek mandiri hilang**: `Pola Kunci & Cara Cepat` ditempatkan sebelum siswa berlatih prosedur dasar, belum ada pemanasan prasyarat jeda 1 minggu, soal cerita belum dipisah secara tegas di latihan kelas, dan belum tersedia kunci jawaban akhir ringkas untuk PR mandiri.
  4. **Kesalahan teknis minor**: path rusak `../../rule/template-materi-ajar.md` pada `skills/matematika-smp/SKILL.md` dan `prompt.md`, instruksi Review Pertemuan 11 SMP yang terlalu berat, serta duplikasi baris penutup di `rules/templates/template-plan.md`.
- **Goals**:
  1. Merevisi `rules/templates/template-materi-ajar.md` dengan arsitektur **9 Bagian Terkalibrasi 80 Menit/Minggu** yang membedakan jalur **SMP vs SMA**, menambahkan pemanasan prasyarat, aturan *Contoh Kembar (1-to-1 Pairing)*, tangga latihan 4 tahap halus (`6A` Terbimbing → `6B` Drilling Prosedur Inti 4–5 soal → `6C` Soal Cerita Terpisah → `6D` Tantangan Opsional 1 soal), memindahkan `Pola Kunci & Cek Kesalahan Umum` setelah latihan (`Bagian 7`), dan menambahkan `Kunci Jawaban Akhir Ringkas` di `Bagian 8`.
  2. Menyelaraskan instruksi 9 bagian, tautan path template, dan aturan beban 80 menit pada `skills/matematika-smp/` (`SKILL.md`, `prompt.md`) dan `skills/matematika-sma/` (`SKILL.md`, `prompt.md`).
  3. Merapikan duplikasi baris akhir pada `rules/templates/template-plan.md` dan memperbarui ringkasan pada `README.md`.
- **Out of Scope**:
  - Tidak mengubah modul materi ajar yang sudah terbit di workspace `be_good_teacher`.
  - Tidak memodifikasi berkas non-Markdown (`skill.json`) di luar lingkup persetujuan eksplisit dokumen `.md` (dicatat sebagai rekomendasi tindak lanjut jika diperlukan).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Package / Library Baru**: Tidak ada.
- **Environment Variables (.env)**: Tidak ada.
- **Keterkaitan File Lintas Modul**:
  - `rules/templates/template-materi-ajar.md` menjadi sumber rujukan utama bagi `skills/matematika-smp` dan `skills/matematika-sma`.
  - Seluruh perubahan di `D:\Project\exercise\skills-agent\` tersinkronisasi otomatis ke `~/.gemini/config/plugins/skills-agent` melalui NTFS Directory Junction.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
D:/Project/exercise/skills-agent/
├── .plan/
│   └── 2026-11-12-revise-template-materi-ajar.md   # [Baru] Rencana & checklist revisi
├── rules/
│   └── templates/
│       ├── template-materi-ajar.md                 # [Ubah] Redesign 9 bagian (siklus 80 mnt, SMP vs SMA, 4-tier drill)
│       └── template-plan.md                        # [Ubah] Hapus duplikasi baris penutup
├── skills/
│   ├── matematika-smp/
│   │   ├── SKILL.md                                # [Ubah] Perbaiki path ke rules/templates & struktur 9 bagian baru
│   │   └── prompt.md                               # [Ubah] Perbaiki path, selaraskan 9 bagian, kalibrasi beban 80 mnt
│   └── matematika-sma/
│       ├── SKILL.md                                # [Ubah] Selaraskan rincian 9 bagian baru
│       └── prompt.md                               # [Ubah] Selaraskan 9 bagian & kalibrasi scaffolding halus 80 mnt
└── README.md                                       # [Ubah] Sinkronkan deskripsi matriks template-materi-ajar.md
```

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Revisi Template Inti (`rules/templates/`)**
  - [x] Merancang ulang `rules/templates/template-materi-ajar.md` untuk siklus 80 menit/minggu (diferensiasi SMP vs SMA, blok prasyarat di Bagian 1, contoh bertingkat mikro 1-to-1 di Bagian 4–5, latihan 4 tingkat halus di Bagian 6, pola kunci pasca-latihan di Bagian 7, PR + kunci jawaban akhir ringkas di Bagian 8, ringkasan di Bagian 9).
  - [x] Menghapus duplikasi baris `> **AWAITING APPROVAL**` pada `rules/templates/template-plan.md`.
- [x] **Fase 2: Sinkronisasi Skill Matematika SMP**
  - [x] Memperbaiki tautan template di `skills/matematika-smp/SKILL.md` dan `prompt.md`.
  - [x] Memperbarui batasan kritis, kalibrasi Pertemuan 11–12 Kelas 9, dan rincian 9 bagian di `skills/matematika-smp/prompt.md`.
- [x] **Fase 3: Sinkronisasi Skill Matematika SMA**
  - [x] Menyelaraskan daftar 9 bagian di `skills/matematika-sma/SKILL.md` dan `skills/matematika-sma/prompt.md` agar sejalan dengan scaffolding halus 80 menit tanpa menghilangkan kekhasan SMA IPA & Pesantren.
- [x] **Fase 4: Dokumentasi & Verifikasi Integritas**
  - [x] Memperbarui catatan ringkas `README.md`.
  - [x] Memverifikasi konsistensi penomoran 9 bagian, tautan relative path, serta sinkronisasi live ke `~/.gemini/config/plugins/skills-agent`.

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Ketidaksinkronan antara `template-materi-ajar.md` dan `prompt.md` pada `matematika-smp` atau `matematika-sma` (misalnya instruksi lama memaksa soal HOTS/pecahan sebelum drilling dasar).
- **Mitigasi**: Memperbarui template dan kedua skill (`SKILL.md` + `prompt.md`) dalam satu siklus terkoordinasi serta memverifikasi ulang seluruh penomoran bagian 1–9 di setiap berkas.

---

> **COMPLETED**: Seluruh tahapan revisi berkas Markdown telah selesai diimplementasikan dan tersinkronisasi otomatis ke plugin global `~/.gemini/config/plugins/skills-agent`. (Catatan: `skills/matematika-smp/skill.json` masih mencatat array `"rules"` lama `../../rule/...` di luar cakupan auto-approval `.md` apabila ingin turut diperbarui secara terpisah.)
