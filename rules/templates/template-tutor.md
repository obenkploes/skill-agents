# STANDAR FORMAT MODUL TUTOR & PRAKTIKUM (SMK & MAHASISWA)

Aturan baku penyusunan **Modul Tutor, Praktikum Laboratorium, dan Tutorial Teknis** (pemrograman, basis data, kerangka kerja web/mobile, jaringan, maupun rekayasa sistem) bagi peserta didik jenjang **SMK** maupun **Mahasiswa**. Modul wajib membangun pemahaman dari fondasi fungsi terkecil hingga penerapan terpadu, sehingga peserta benar-benar paham *mengapa* dan *bagaimana* setiap baris kode/perintah bekerja.

> **PRINSIP PEDAGOGI & KALIBRASI WAJIB:**
> 1. **Bedah Fungsi Dasar Sebelum Praktik (*Syntax & API First*):** Jangan pernah langsung menyajikan skrip proyek atau kueri multi-klausa sebelum **Bagian 2 (Kamus Fungsi, Perintah, & Argumen Dasar)** membedah setiap fungsi, method, perintah CLI, klausa, parameter (wajib/opsional), tipe data, dan nilai kembaliannya.
> 2. **Diferensiasi Jenjang (SMK vs Mahasiswa):**
>    - **Jalur SMK:** Gunakan bahasa teknis lugas dan konkret, perbanyak contoh mikro 1 fitur/1 perintah serta latihan modifikasi terbimbing (`Level 1–2`), fokus pada keterbacaan alur (*code tracing*), kepastian eksekusi, dan penanganan error umum.
>    - **Jalur Mahasiswa:** Tetap **wajib** melewati bedah fungsi dasar dan contoh mikro di awal agar fondasi akurat, lalu dorong pendalaman pada kombinasi fitur, kasus batas (*edge cases*), efisiensi/kompleksitas, serta desain arsitektur di `Contoh 4` dan `Latihan Level 3–4`.
> 3. **Kenaikan Mikro (*1 Hal Baru per Contoh*) & *Contoh Kembar*:** Setiap contoh di **Bagian 4** hanya menambahkan satu lapisan kerumitan dibanding contoh sebelumnya (`Dasar Mikro → Variasi Parameter → Kombinasi Ringan → Implementasi Terapan & Edge Case`). Setiap pola pada soal latihan `Level 1–3` **wajib** memiliki contoh sepola pada Bagian 2 atau Bagian 4.
> 4. **Kode Contoh Utuh & Siap Jalan:** Dilarang memotong contoh implementasi (Bagian 4) dengan komentar pemalas seperti `// lanjutkan sendiri` atau `-- tulis query di sini`. Khusus modul berstatus **Soal Ujian/Asesmen**, hilangkan kode solusi dari soal latihan namun tetap pertahankan rincian fungsi dasar pada Bagian 2.
> 5. **Konteks & Kosakata Sesuai Nilai Islam:** Gunakan skenario domain yang halal dan mendidik (inventaris perpustakaan/toko, data akademik/pesantren, kantin/perdagangan murni, logistik gudang, telemetri sensor); hindari istilah atau skenario yang bertentangan dengan nilai Islam (seperti `koperasi`, transaksi berbunga/riba, `dadu`, `kartu remi`, `undian`, atau `musik`).

---

# MODUL PRAKTIKUM: [NAMA TOPIK / TEKNOLOGI]
- **Subjek / Mata Kuliah:** [Nama Mata Pelajaran SMK / Mata Kuliah]
- **Target Level:** [SMK / Mahasiswa / Umum Bertahap]
- **Fokus Materi:** [Satu subtopik atau alur konsep utama yang tuntas dipelajari]

---

### 1. Tujuan Pembelajaran & Peta Konsep
*Paparkan target kemampuan terukur serta diagram alur sederhana agar peserta melihat gambaran besar sistem sebelum menulis kode.*

**Tujuan Pembelajaran:**
Setelah menyelesaikan modul ini, peserta didik mampu:
1. Menjelaskan fungsi, argumen wajib/opsional, dan hasil keluaran dari perintah/API dasar `[sebutkan fungsi/perintah inti]`.
2. Menerapkan `[konsep utama]` pada skenario sederhana hingga kombinasi menengah tanpa kesalahan sintaks.
3. Menganalisis pesan kesalahan umum, kasus batas (*edge cases*), dan memverifikasi kesesuaian hasil eksekusi.

**Peta Alur Kerja (*Data / Execution Flow*):**
```text
[Input / Data Awal]
        │
        ▼  (Fungsi / Perintah 1: ...)
[Proses / Transformasi Inti]
        │
        ▼  (Fungsi / Perintah 2: ...)
[Validasi / Kondisi Batas] ──(Tidak valid)──► [Pesan Error / Penanganan Aman]
        │ (Valid)
        ▼
[Output / Hasil Akhir]
```

---

### 2. Kamus Fungsi, Perintah, & Argumen Dasar *(Wajib Terperinci)*
*Bedah **setiap** fungsi bawaan, method, klausa, keyword, atau perintah yang akan dipakai pada Bagian 4 dan Bagian 6 sebelum masuk ke implementasi penuh.*

#### A. `[Nama Fungsi / Perintah 1]`
- **Kegunaan Utama:** [Penjelasan singkat 1–2 kalimat dengan bahasa lugas tentang apa yang dilakukan fungsi/perintah ini.]
- **Sintaks Baku:**
  ```[lang]
  nama_fungsi(argumen_1, argumen_2, [argumen_opsional])
  ```
- **Rincian Parameter / Argumen / Klausa:**

  | Nama Parameter / Klausa | Status | Tipe Data / Format | Penjelasan & Contoh Nilai Valid |
  | :--- | :---: | :--- | :--- |
  | `argumen_1` | **Wajib** | `[string / array / int / nama_kolom]` | [Peran parameter pertama, misal: data sumber yang diproses] |
  | `argumen_2` | **Wajib** | `[callback / kondisi / nilai]` | [Peran parameter kedua, misal: kriteria seleksi/perbandingan] |
  | `argumen_opsional` | *Opsional* | `[bool / int]` | [Peran & nilai bawaan (*default*), misal: bawaan `false`] |

- **Nilai Kembalian (*Return Value*) / Efek Eksekusi:**
  [Jelaskan tipe dan bentuk hasil saat berhasil, serta perilakunya jika input kosong/tidak ditemukan—misal mengembalikan array kosong `[]`, `null`, atau 0 baris.]
- **Contoh Mikro (1–3 Baris Mandiri):**
  ```[lang]
  // Contoh terkecil yang langsung menunjukkan kerja fungsi ini secara terisolasi
  ```
  *Hasil eksekusi:* `[tuliskan hasil persisnya]`

#### B. `[Nama Fungsi / Perintah 2]`
*(Ulangi pola struktur yang sama untuk fungsi/perintah/klausa dasar ke-2, ke-3, dan seterusnya hingga tidak ada sintaks asing di Bagian 4.)*

---

### 3. Prasyarat, Lingkungan Kerja, & Dataset / Skeleton Awal
*Siapkan lingkungan kerja dan data awal yang bersih serta dapat dijalankan ulang (*idempotent*) agar peserta bisa langsung berlatih.*

- **Kebutuhan Lingkungan:** `[Bahasa / DBMS / Framework + versi minimal, misal PHP 8.2 / MySQL 8.x / Python 3.11]`
- **Struktur Berkas Kerja (bila multi-file):**
  ```text
  proyek-praktikum/
  ├── [file_konfigurasi_atau_skema]
  └── [file_utama_praktik]
  ```
- **Inisialisasi Awal / Data Uji (*Siap Salin & Jalankan*):**
  ```[lang]
  // Skrip setup data awal / dummy record lengkap (5–10 data) atau kerangka awal siap jalan
  ```

---

### 4. Contoh Implementasi Bertingkat *(Minimal 4 Contoh Terpandu)*
*Sajikan minimal **4 contoh bertahap halus** (*1 hal baru per contoh*) dengan kode lengkap bebas komentar pemalas, diikuti penjelasan baris demi baris dan hasil keluarannya.*

#### Contoh 1 — Kasus Paling Dasar (*Minimal Working Example*)
*Hanya menggunakan 1 fungsi/perintah inti pada skenario paling bersih tanpa kondisi rumit.*
```[lang]
// Kode lengkap, singkat, dan langsung berjalan
```
- **Penjelasan Baris Kunci:** [Uraikan apa yang terjadi pada setiap baris penting.]
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 1]
  ```

#### Contoh 2 — Variasi Argumen / Kondisi Tunggal
*Tetap memakai fungsi yang sama seperti Contoh 1, hanya mengganti atau menambah 1 argumen/opsi/filter.*
```[lang]
// Kode lengkap yang menunjukkan dampak perubahan 1 parameter/klausa
```
- **Perbedaan dengan Contoh 1:** [Jelaskan bagian mana yang berubah dan mengapa hasilnya berubah.]
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 2]
  ```

#### Contoh 3 — Kombinasi Menengah (Menggabungkan 2 Fungsi Dasar)
*Menghubungkan 2 fungsi/perintah dari Bagian 2 menjadi satu alur proses berurutan.*
```[lang]
// Kode lengkap kombinasi dua konsep yang terstruktur rapi
```
- **Penjelasan Alur Data:** [Jelaskan output fungsi pertama masuk sebagai input fungsi kedua.]
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 3]
  ```

#### Contoh 4 — Implementasi Terapan Utuh & Penanganan *Edge Case*
*Penerapan siap produksi dengan penanganan data kosong/tidak valid atau optimasi struktur (bekal penting untuk SMK tingkat lanjut dan Mahasiswa).*
```[lang]
// Kode lengkap termasuk guard clause / validasi input / error handling / optimasi
```
- **Mengapa Langkah Ini Penting:** [Jelaskan kasus batas apa yang ditangani dan dampaknya pada keandalan/performa sistem.]
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 4]
  ```

---

### 5. Verifikasi Output & Panduan Debugging (*Common Pitfalls*)

#### A. Ringkasan Ekspektasi Output Contoh 1–4
| Contoh | Fokus Fitur yang Diuji | Indikator Berhasil / Output Kunci |
| :--- | :--- | :--- |
| **Contoh 1** | Penggunaan dasar `[Fungsi 1]` | [Output ringkas / jumlah baris] |
| **Contoh 2** | Variasi parameter `[argumen/klausa]` | [Output ringkas / perubahan hasil] |
| **Contoh 3** | Kombinasi `[Fungsi 1]` + `[Fungsi 2]` | [Output gabungan yang tepat] |
| **Contoh 4** | Penanganan kasus batas / validasi | [Respons aman saat input kosong/salah] |

#### B. Kesalahan Umum & Cara Memperbaikinya
| Kesalahan / Gejala Error | Penyebab Umum pada Fungsi/Argumen | Solusi Tepat |
| :--- | :--- | :--- |
| `[Error 1 / Output Null]` | [Salah tipe argumen atau urutan parameter tertukar] | [Perbaikan konkret yang harus dilakukan] |
| `[Error 2 / Hasil Keliru]` | [Lupa kondisi batas, filter terbalik, atau mengabaikan nilai opsional] | [Cara mengecek dan memperbaiki logika] |
| `[Error 3 / Lambat / Crash]` | [Tidak menangani data kosong atau melakukan operasi berulang tidak perlu] | [Terapkan validasi awal / *guard clause*] |

---

### 6. Latihan Soal & Praktikum Berjenjang *(Minimal 4 Level)*
*Seluruh soal di bawah ini disusun berurutan dari pemahaman sintaks dasar hingga pemecahan kasus nyata agar pemahaman terbangun utuh.*

#### Level 1 — Pemahaman Fungsi & Prediksi Output *(Wajib SMK & Mahasiswa)*
*Menguji penguasaan fungsi dasar di Bagian 2 tanpa menulis sistem besar terlebih dahulu.*
1. **[Prediksi Output]:** Perhatikan potongan kode/kueri berikut:
   ```[lang]
   [Potongan pendek 2–4 baris menggunakan Fungsi 1]
   ```
   Tanpa menjalankannya dulu, tuliskan hasil keluaran persisnya dan jelaskan peran argumen ke-2 pada kode tersebut.
2. **[Identifikasi Argumen]:** Mengapa pemanggilan `[contoh pemanggilan salah atau kurang parameter]` menghasilkan error/hasil salah? Parameter apa yang harus ditambahkan atau diubah?
3. **[Perbaikan Sintaks Kecil]:** Temukan 1 kesalahan argumen/klausa pada cuplikan 3 baris berikut lalu perbaiki:
   ```[lang]
   [Potongan kode dengan 1 bug spesifik yang sering dialami pemula]
   ```

#### Level 2 — Latihan Terbimbing / Modifikasi Terarah *(Wajib SMK & Mahasiswa)*
*Pola kembar dari Contoh 1–2; peserta berlatih memodifikasi argumen dan melengkapi alur terarah.*
4. **[Modifikasi Parameter]:** Salin pola **Contoh 1**, lalu ubah kriteria/argumen `[X]` agar menghasilkan `[target output A]`. *(Petunjuk: cukup ubah bagian parameter `[Y]`.)*
5. **[Variasi Kondisi Tunggal]:** Dengan pola **Contoh 2**, tambahkan kondisi baru `[syarat B]` pada dataset yang sama dan catat perbedaannya.
6. **[Melengkapi Blok Kode]:** Diberikan kerangka fungsi/kueri berikut yang bagian pemanggilannya masih kosong pada satu baris utama; lengkapi baris yang ditandai agar keluaran sesuai `[spesifikasi hasil]`:
   ```[lang]
   [Kerangka kode pendek dengan 1 baris terarah untuk dilengkapi peserta]
   ```

#### Level 3 — Implementasi Mandiri Terpadu *(Wajib SMK Lanjutan & Mahasiswa)*
*Menggabungkan beberapa fungsi dasar dari nol berdasarkan spesifikasi input–proses–output yang jelas.*
7. **[Kombinasi 2 Fungsi]:** Dengan dataset pada Bagian 3, tulislah solusi mandiri untuk menampilkan `[spesifikasi data/hasil 1]` menggunakan gabungan `[Fungsi 1]` dan `[Fungsi 2]`.
8. **[Kasus Terapan Bisnis/Teknis]:** Buatlah fungsi/prosedur/kueri untuk skenario `[kasus terapan nyata]`, dengan ketentuan input `[A]` menghasilkan output terformat `[B]`.

#### Level 4 — Studi Kasus Analisis & Pengayaan *(Khusus Mahasiswa / Pendalaman SMK)*
*Melatih penalaran arsitektural, penanganan kasus batas (*edge cases*), dan efisiensi solusi.*
9. **[Kasus Batas & Keandalan]:** Rancang solusi untuk `[skenario kasus nyata yang memuat data kosong, duplikat, atau input di luar batas]`. Pastikan program/kueri tetap mengembalikan status terstruktur tanpa *crash* dan beri penjelasan alasan pilihan arsitekturmu.
10. **[*Opsional Pengayaan / Analisis Performa*]:** Bandingkan dua pendekatan solusi (pendekatan A vs pendekatan B) untuk kasus di atas dari sisi keterbacaan kode, efisiensi memori/waktu eksekusi, atau *scalability* bila data membesar hingga 100.000 entri.

---

### 7. Cek Mandiri & Panduan Verifikasi Latihan
*Sesuaikan bagian ini dengan jenis modul:*
- **Untuk Modul Belajar Mandiri:** Cantumkan **hanya ringkasan indikator hasil/nilai akhir** (tanpa menuliskan skrip jawaban utuh untuk Level 3–4) bagi **Level 1 dan Level 2** agar peserta dapat mengecek pemahamannya sendiri sebelum berlanjut:
  - **Cek Level 1:** `No. 1` = `[nilai/output akhir]` | `No. 2` = `[nama argumen/penyebab]` | `No. 3` = `[bagian sintaks yang diperbaiki]`
  - **Cek Level 2:** `No. 4` = `[jumlah data / output akhir]` | `No. 5` = `[jumlah data / output akhir]` | `No. 6` = `[indikator sukses]`
- **Untuk Modul Soal Ujian / Evaluasi:** Ubah bagian ini menjadi **Daftar Periksa Pengujian (*Verification Checklist*)** yang berisi skenario input uji dan kriteria hasil yang harus dipenuhi, tanpa menyertakan potongan skrip solusi.

---

### 8. Ringkasan Fungsi & Refleksi Pemahaman

| Fungsi / Perintah | Kegunaan Inti | Parameter Kritis | Nilai Kembalian / Efek |
| :--- | :--- | :--- | :--- |
| `[Fungsi 1]` | [Ringkasan fungsi 1] | `[Param wajib]` | `[Tipe/hasil kembali]` |
| `[Fungsi 2]` | [Ringkasan fungsi 2] | `[Param wajib]` | `[Tipe/hasil kembali]` |

**Pertanyaan Refleksi:**
1. *Jelaskan dengan bahasamu sendiri: kapan kita menggunakan `[Fungsi 1]` dibanding `[Fungsi 2]`, dan apa akibatnya jika argumen `[X]` diisi tipe data yang salah?*
