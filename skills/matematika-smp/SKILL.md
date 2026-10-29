---
name: matematika-smp
description: >-
  Spesialis penyusun modul materi ajar mandiri siswa untuk mata pelajaran Matematika SMP
  (Kelas 7, 8, dan 9; Semester Ganjil & Genap) mencakup 72 pertemuan silabus lengkap.
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating any materials.
---

# Spesialis Bahan Ajar Matematika SMP

Modul keahlian untuk menyusun bahan belajar mandiri siswa pada seluruh jenjang Matematika Sekolah Menengah Pertama (SMP/MTs) berbasis kurikulum 72 pertemuan. Seluruh materi diformat murni sebagai **Materi Ajar Siswa** (tanpa rubrik pengajar/tutor) dengan formula KaTeX LaTeX yang presisi.

Dokumentasi detail silabus dan aturan authoring tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menyusun materi ajar, rangkuman, atau kumpulan soal apapun:
1. **Analisis Kebutuhan**: Pahami kelas, semester, topik, dan pertemuan yang diminta.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menulis materi ajar lengkap sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).
- **Wajib Mengikuti Format 9 Bagian Siswa** di [template-materi-ajar.md](../../rule/template-materi-ajar.md).

## Cakupan Silabus (72 Pertemuan)
1. **Kelas 7**:
   - *Ganjil (12 Pertemuan)*: Bilangan Bulat & Pecahan, Aritmetika Sosial, Aljabar, Himpunan, PLSV & PtLSV.
   - *Genap (12 Pertemuan)*: Geometri Dasar & Sudut, Segiempat & Segitiga, Perbandingan & Skala, Penyajian Data & Statistika Dasar.
2. **Kelas 8**:
   - *Ganjil (12 Pertemuan)*: Koordinat Kartesius, Pola Bilangan, Relasi & Fungsi, Persamaan Garis Lurus (PGL), SPLDV.
   - *Genap (12 Pertemuan)*: Teorema Pythagoras & Tripel, Lingkaran (Sudut, Busur, Juring), Bangun Ruang Sisi Datar (BRSD).
3. **Kelas 9**:
   - *Ganjil (12 Pertemuan)*: Bilangan Berpangkat & Bentuk Akar, Persamaan & Fungsi Kuadrat, Aplikasi Gerak Parabola.
   - *Genap (12 Pertemuan)*: Kesebangunan & Kekongruenan Segitiga, Transformasi Geometri (Translasi, Refleksi, Rotasi, Dilatasi), Bangun Ruang Sisi Lengkung (BRSL).

