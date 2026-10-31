---
name: matematika-sma
description: >-
  Spesialis penyusun modul materi ajar mandiri siswa untuk mata pelajaran Matematika SMA/MA (Jurusan IPA & Pesantren)
  mencakup 72 pertemuan silabus lengkap (Kelas 10, 11, dan 12; Semester Ganjil & Genap).
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating any materials.
---

# Spesialis Bahan Ajar Matematika SMA (IPA & Pesantren)

Modul keahlian untuk menyusun bahan belajar mandiri siswa pada seluruh jenjang Matematika Sekolah Menengah Atas / Madrasah Aliyah (SMA/MA Jurusan IPA) dengan penyesuaian untuk Pesantren berbasis kurikulum 72 pertemuan (3 tahun, 6 semester, 12 pertemuan efektif per semester).

Seluruh materi diformat murni sebagai **Materi Ajar Siswa** (tanpa rubrik pengajar/tutor) dengan formula KaTeX LaTeX yang presisi, scaffolding bertahap, serta penanaman hikmah keteraturan alam semesta ciptaan Allah SWT dan studi kasus kontekstual kehidupan santri.

Dokumentasi detail silabus, standar notasi rumus KaTeX, dan aturan authoring tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menyusun materi ajar, modul rangkuman, lembar kerja siswa (LKS), atau kumpulan soal evaluasi apapun:
1. **Analisis Kebutuhan**: Pahami kelas (10, 11, 12), semester (Ganjil/Genap), topik pembahasan, dan nomor pertemuan yang diminta.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menulis materi ajar lengkap sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).
- **Wajib Mengikuti Format 9 Bagian Siswa** di [template-materi-ajar.md](../../rules/templates/template-materi-ajar.md):
  1. *Pengertian & Konsep Dasar* (komunikatif, analogi intuitif).
  2. *Bentuk Umum & Rumus Baku* (KaTeX LaTeX murni `$ ... $` dan `$$ ... $$`).
  3. *Sifat-Sifat, Karakteristik, & Aturan Khusus* (tabel komparasi & syarat keberlakuan rumus).
  4. *Contoh Soal & Pembahasan Terperinci* (scaffolding bertingkat: Diketahui, Ditanyakan, Langkah, Kesimpulan $\checkmark$).
  5. *Penerapan Kontekstual* (Studi kasus nyata & lingkungan pesantren: hafalan Al-Qur'an, infak, jadwal piket/ibadah, konsumsi asrama).
  6. *Pola Kunci & Cara Cepat Mengingat* (jembatan keledai visual & catatan waspada kesalahan umum).
  7. *Latihan Soal Mandiri* (Tingkat Dasar, Variasi/Campuran, Tantangan/HOTS).
  8. *Pekerjaan Rumah (PR Pondok / Mandiri)* (soal perhitungan, soal cerita, dan pertanyaan pemahaman konsep).
  9. *Ringkasan Materi* (3-4 poin esensial).
- **Strict LaTeX KaTeX**: Dilarang menggunakan teks datar tanpa format untuk rumus matematika (seperti `nn+12`, `51-1=4`, `x-2x+2x-2`). Semua variabel, persamaan, pecahan, akar, eksponen, limit, turunan, integral, dan matriks WAJIB diformat menggunakan sintaks KaTeX murni.
- **Zero Teacher Rubric**: Dilarang menyertakan rubrik penilaian instruktur, lembar penskoran guru, atau catatan fasilitator.

## Cakupan Silabus (72 Pertemuan / 6 Semester)

### 1. KELAS 10
- **Semester Ganjil (Fondasi Aljabar dan Logika - 12 Pertemuan)**:
  - Pertemuan 1-2: Eksponen & Bentuk Akar (Sifat-sifat eksponen, fungsi eksponensial, persamaan & pertidaksamaan eksponensial).
  - Pertemuan 3-4: Logaritma (Konsep dasar, hubungan eksponen-logaritma, sifat-sifat logaritma, persamaan logaritma sederhana).
  - Pertemuan 5: Evaluasi 1 (Ulangan Harian: Eksponen, Bentuk Akar, dan Logaritma).
  - Pertemuan 6-7: Nilai Mutlak (Persamaan & pertidaksamaan linear satu variabel yang memuat nilai mutlak sebagai jarak).
  - Pertemuan 8-9: Sistem Persamaan Linear (SPLDV metode eliminasi/substitusi, SPLTV dan pemodelan soal cerita).
  - Pertemuan 10: Latihan & Aplikasi (Gabungan nilai mutlak & SPL dalam konteks masalah nyata).
  - Pertemuan 11: Evaluasi 2 (Ulangan Harian: Nilai Mutlak dan SPL).
  - Pertemuan 12: Review & Persiapan UAS Ganjil.
- **Semester Genap (Fungsi, Geometri, dan Trigonometri Dasar - 12 Pertemuan)**:
  - Pertemuan 1-2: Fungsi & Fungsi Kuadrat (Relasi, fungsi, domain, kodomain, range, grafik parabola, sumbu simetri, titik puncak).
  - Pertemuan 3: Komposisi & Invers Fungsi (Operasi aljabar fungsi, fungsi komposisi $f \circ g$, konsep dan penentuan fungsi invers $f^{-1}$).
  - Pertemuan 4: Evaluasi 1 (Ulangan Harian: Fungsi, Komposisi, dan Invers).
  - Pertemuan 5-6: Trigonometri Dasar (Perbandingan sin, cos, tan, csc, sec, cot segitiga siku-siku, sudut istimewa, 4 kuadran).
  - Pertemuan 7: Aturan Sinus & Cosinus (Aturan sinus, aturan cosinus, luas segitiga sembarang).
  - Pertemuan 8: Grafik Fungsi Trigonometri (Grafik sinus, cosinus, dan tangen sederhana).
  - Pertemuan 9: Latihan & Aplikasi Trigonometri (Masalah pengukuran jarak, tinggi menara, arah kiblat).
  - Pertemuan 10: Evaluasi 2 (Ulangan Harian: Trigonometri).
  - Pertemuan 11: Geometri Dasar (Konsep titik, garis, dan bidang dalam ruang).
  - Pertemuan 12: Review & Persiapan UAS Genap.

### 2. KELAS 11
- **Semester Ganjil (Matematika Lanjutan dan Kalkulus Awal - 12 Pertemuan)**:
  - Pertemuan 1: Induksi Matematika (Prinsip efek domino, pembuktian deret aljabar dan sifat keterbagian).
  - Pertemuan 2-3: Program Linear (Model matematika, daerah himpunan penyelesaian, nilai optimum dengan uji titik pojok).
  - Pertemuan 4: Evaluasi 1 (Ulangan Harian: Induksi Matematika & Program Linear).
  - Pertemuan 5-7: Matriks (Ordo, kesamaan, transpos, operasi aljabar, perkalian matriks, determinan & invers $2 \times 2$ dan $3 \times 3$ aturan Sarrus, aplikasi SPL).
  - Pertemuan 8: Evaluasi 2 (Ulangan Harian: Matriks).
  - Pertemuan 9-10: Transformasi Geometri (Translasi, refleksi, rotasi, dilatasi, dan matriks transformasi).
  - Pertemuan 11: Evaluasi 3 (Ulangan Harian: Transformasi Geometri).
  - Pertemuan 12: Review & Persiapan UAS Ganjil.
- **Semester Genap (Barisan, Deret, dan Kalkulus Diferensial - 12 Pertemuan)**:
  - Pertemuan 1-3: Barisan dan Deret (Aritmetika $U_n$ & $S_n$, geometri, deret geometri tak hingga konvergen/divergen, aplikasi pertumbuhan/peluruhan/bunga).
  - Pertemuan 4: Evaluasi 1 (Ulangan Harian: Barisan dan Deret).
  - Pertemuan 5-6: Limit Fungsi (Konsep intuitif limit, limit aljabar bentuk tak tentu $\frac{0}{0}$ pemfaktoran & rasionalisasi akar, limit trigonometri).
  - Pertemuan 7-8: Turunan Fungsi / Diferensial (Konsep laju perubahan, aturan dasar konstanta/pangkat/koefisien, aturan hasil kali, bagi, dan rantai).
  - Pertemuan 9-10: Aplikasi Turunan (Gradien garis singgung, fungsi naik/turun, titik stasioner maksimum/minimum, laju kecepatan sesaat).
  - Pertemuan 11: Evaluasi 2 (Ulangan Harian: Limit dan Turunan).
  - Pertemuan 12: Review & Persiapan UAS Genap.

### 3. KELAS 12
- **Semester Ganjil (Geometri Ruang dan Statistika Deskriptif - 12 Pertemuan)**:
  - Pertemuan 1-3: Geometri Ruang / Dimensi Tiga (Kedudukan titik/garis/bidang pada kubus/balok/limas, jarak titik-titik, titik-garis, titik-bidang, dan sudut).
  - Pertemuan 4: Evaluasi 1 (Ulangan Harian: Geometri Ruang).
  - Pertemuan 5: Statistika Deskriptif (Penyajian data: aturan Sturges, tabel distribusi frekuensi, histogram, poligon, ogive naik/turun).
  - Pertemuan 6: Statistika Deskriptif (Ukuran Pemusatan: Mean $\bar{x}$, Median $Me$, Modus $Mo$ data tunggal dan berkelompok).
  - Pertemuan 7: Statistika Deskriptif (Ukuran Letak: Kuartil $Q_1, Q_2, Q_3$, Desil $D_k$, Persentil $P_k$ data tunggal dan berkelompok).
  - Pertemuan 8: Statistika Deskriptif (Ukuran Penyebaran: Jangkauan $R$, Simpangan Rata-rata $SR$, Varians $S^2$, Simpangan Baku $S$).
  - Pertemuan 9: Latihan & Aplikasi Statistika (Studi kasus analisis data riil dan evaluasi prestasi santri).
  - Pertemuan 10: Evaluasi 2 (Ulangan Harian: Statistika Deskriptif).
  - Pertemuan 11: Pemantapan Materi Kelas 10 & 11 (Review komprehensif aljabar, trigonometri, dan kalkulus).
  - Pertemuan 12: Review & Persiapan UAS Ganjil.
- **Semester Genap (Peluang, Kalkulus Integral, dan Pemantapan Ujian - 12 Pertemuan)**:
  - Pertemuan 1-2: Kaidah Pencacahan (Aturan penjumlahan, aturan perkalian, notasi faktorial $n!$, permutasi $P(n,r)$, kombinasi $C(n,r)$).
  - Pertemuan 3: Peluang Kejadian (Ruang sampel, titik sampel, frekuensi harapan, peluang kejadian majemuk saling lepas & saling bebas).
  - Pertemuan 4: Evaluasi 1 (Ulangan Harian: Kaidah Pencacahan dan Peluang).
  - Pertemuan 5-7: Kalkulus Integral (Integral tak tentu sebagai antiturunan, rumus dasar aljabar, integral tentu, aplikasi luas daerah di bawah kurva, volume benda putar).
  - Pertemuan 8: Evaluasi 2 (Ulangan Harian: Integral).
  - Pertemuan 9-11: Pemantapan & Latihan Soal Ujian / UTBK (Aljabar & Trigonometri, Kalkulus & Geometri, Statistika & Peluang).
  - Pertemuan 12: Try Out & Pembahasan Strategi Ujian.

