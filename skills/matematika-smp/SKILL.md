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
- **Wajib Mengikuti Format 9 Bagian Siswa (Terkalibrasi 80 Menit/Minggu)** di [template-materi-ajar.md](../../rules/templates/template-materi-ajar.md):
  1. *Pemanasan Prasyarat & Konsep Dasar* (2 soal pemanasan kilat 3 menit + pengantar ringkas & analogi konkret SMP).
  2. *Bentuk Umum & Rumus Baku* (KaTeX LaTeX murni `$...$` dan `$$...$$`, maksimal 1–2 rumus inti per pertemuan).
  3. *Sifat-Sifat & Aturan Penting* (maksimal 2–3 syarat/aturan yang langsung dipakai di latihan).
  4. *Contoh Soal & Pembahasan Bertingkat Mikro* (minimal 2 contoh: Dasar Angka Bulat → Variasi Ringan; menerapkan Prinsip *Contoh Kembar* 1-to-1 dengan latihan).
  5. *Penerapan Kontekstual* (1 studi kasus soal cerita ramah hitung sebagai model langsung bagi Soal Cerita di Bagian 6C).
  6. *Latihan Soal Kelas* (4 tangga halus sebelum cara cepat: `6A` Terbimbing 2 soal → `6B` Penguasaan Prosedur Inti 4–5 soal angka bulat bertahap → `6C` Soal Cerita Terpisah 1–2 soal → `6D` Tantangan Opsional 1 soal).
  7. *Pola Kunci, Jebakan Umum, & Cara Cepat* (penguatan pola & cara cek hasil setelah latihan + peringatan kesalahan umum).
  8. *Pekerjaan Rumah (PR Pondok / Mandiri)* (soal rutin, soal cerita, refleksi konsep, dan Kunci Jawaban Akhir Ringkas untuk cek mandiri).
  9. *Ringkasan Materi* (2–4 poin inti paling esensial).
- **Kalibrasi Tingkat Kesulitan SMP (80 Menit/Minggu)**: Utamakan bilangan bulat/rasional ramah hitung, hindari hasil akar irasional atau manipulasi pecahan aljabar rumit kecuali menjadi materi pokok pertemuan, dan gunakan instruksi soal yang ringkas.

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

