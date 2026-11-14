# STANDAR FORMAT MODUL TUTOR & PRAKTIKUM (SMK & MAHASISWA)

Aturan baku penyusunan **Modul Tutor, Praktikum Laboratorium, dan Tutorial Teknis** (pemrograman, basis data, kerangka kerja web/mobile, jaringan, maupun sistem tertanam) bagi peserta didik jenjang **SMK** maupun **Mahasiswa**. Modul wajib membangun pemahaman dari model mental dan fungsi terkecil hingga praktikum lintas modul yang berkelanjutan, sehingga peserta benar-benar paham *mengapa*, *bagaimana proses di tengah jalan*, dan *di konteks apa* setiap baris kode/perintah bekerja tanpa mengalami kebingungan.

> **PRINSIP PEDAGOGI & KALIBRASI WAJIB:**
> 1. **Model Mental Sebelum Sintaks (*Why Before How*):** Sebelum membedah parameter di Bagian 2, jelaskan secara ringkas di Bagian 1 masalah apa yang diselesaikan fitur ini dan bagaimana mekanismenya bekerja (*mental model*), disertai 2 pertanyaan pengingat prasyarat dari modul sebelumnya.
> 2. **Bedah Fungsi Dasar Sebelum Praktik (*Syntax & API First*):** Jangan pernah langsung menyajikan skrip proyek atau kueri multi-klausa sebelum **Bagian 2 (Kamus Fungsi, Perintah, & Argumen Dasar)** membedah setiap fungsi, method, perintah CLI, klausa, parameter (wajib/opsional), tipe data, dan nilai kembaliannya.
> 3. **Penanda Jalur yang Bersih (`Inti` vs `Pendalaman`):**
>    - **Materi Inti (SMK & Mahasiswa)** (Bagian 1–3, Contoh 1–3, Latihan Level 1–2, serta Level 3 dasar): Wajib dikuasai seluruh peserta. Gunakan bahasa teknis lugas, contoh konkret, dan fokus pada ketepatan alur.
>    - **Materi Pendalaman (Mahasiswa / SMK Lanjutan)** (Contoh 4, Latihan Level 4, dan catatan optimasi): Dipisahkan secara rapi menggunakan keterangan teks biasa atau *callout* (mis. `(Pendalaman)` atau `> **Jalur Pendalaman:** ...`) agar siswa SMK tidak kewalahan, sementara Mahasiswa tetap mendapat tantangan *edge case* dan desain arsitektur. **Jangan** membungkus tag seperti `` `[INTI: ...]` `` dengan *backtick* kode di dalam heading karena merusak tampilan tipografi modul.
> 4. **Kenaikan Mikro (*1 Hal Baru per Contoh*) & *State Tracing*:** Setiap contoh di **Bagian 4** hanya menambahkan satu lapisan kerumitan dibanding contoh sebelumnya (`Dasar Mikro → Variasi Parameter → Kombinasi Ringan → Implementasi Terapan & Edge Case`). Pada **Contoh 2 dan Contoh 3**, wajib sertakan **Pelacakan Kondisi Antara (*State Tracing*)** yang memperlihatkan isi variabel/baris data sebelum hasil akhir terbentuk.
> 5. **Format Baku Latihan Soal (Tabel Acuan Data + Instruksi Terarah):**
>    - **Penyajian Tabel Acuan Praktik:** Pada awal Bagian 6, **wajib** menyajikan tabel-tabel data acuan visual (berisi nama tabel, kolom, dan baris data konkret 4–5 baris per tabel, atau kamus spesifikasi rancangan untuk modul DDL) sebelum daftar pertanyaan.
>    - **Pola Kalimat Soal Langsung & Aplikatif:** Susun daftar bernomor 1 s.d. 8–10 butir soal dengan instruksi langsung pada tindakan teknis (*action-oriented*), diawali kalimat baku: *"Tulis perintah [SQL/kode] untuk [tindakan] [tabel] dengan [kondisi/nilai]..."*.
>    - **Kenaikan Tingkat Kesulitan Alami:** Tingkat kesulitan soal meningkat secara alami dari butir-butir awal (operasi dasar/tunggal) menuju butir-butir akhir (kombinasi kondisi, agregasi, atau relasi) tanpa menyematkan label subjudul pemecah (`Level 1`, `Level 2`) agar tampilan soal ringkas dan fokus.
> 6. **Praktikum Berkelanjutan Multi-Tema (2–3 *Persistent Lab Tracks*):** Latihan tidak boleh selalu ganti-ganti domain acak setiap pertemuan. Setiap seri kurikulum wajib menetapkan **2 atau 3 Tema Tetap yang Berkelanjutan** lintas modul:
>    - **Tema 1 (Jalur Contoh & Penguasaan Dasar):** Dipakai konsisten pada **Bagian 4 (Contoh 1–4)** dan latihan inti agar fokus peserta tidak terpecah oleh domain baru saat mempelajari sintaks baru.
>    - **Tema 2 (Jalur Transfer Berkelanjutan):** Domain berbeda yang skema/kodenya juga bertumbuh dari modul ke modul (*cumulative milestone*), dipakai pada butir latihan transfer untuk menguji apakah peserta mampu mentransfer konsep ke konteks lain.
>    - **Tema 3 *(Opsional untuk Analisis Lanjut)*:** Dipakai untuk skenario data besar, audit/logging, atau optimasi.
> 7. **Konteks & Kosakata Sesuai Nilai Islam:** Gunakan skenario tema yang baik, halal, dan mendidik (manajemen kantin/toko ritel, akademik/pesantren, perpustakaan, logistik gudang, telemetri sensor); hindari istilah atau skenario yang bertentangan dengan nilai Islam (seperti `koperasi`, transaksi berbunga/riba, `dadu`, `kartu remi`, `undian`, atau `musik`).
> 8. **Prinsip *Zero Untaught Syntax* & Kalibrasi Pendekatan Modul:** Pada modul ke-$N$, materi dan contoh inti **dilarang keras** menggunakan sintaks/klausa/fitur yang baru diajarkan pada modul berikutnya ($> N$). Sesuaikan format 8 bagian dengan kesiapan materi:
>    - **Pendekatan Fondasi (Modul Pengantar / Instalasi / Tooling):** Jika peserta didik belum mempelajari sintaks pemrograman/DDL/DML, Bagian 3 berupa checklist prasyarat & profil skenario Tema 1–3 (*tanpa skrip DDL/DML berat*), Bagian 4 berisi 4 tahap terpandu (keputusan arsitektur $\rightarrow$ langkah GUI/CLI $\rightarrow$ verifikasi 1 perintah dasar yang dibedah per kata $\rightarrow$ studi kasus perencanaan produksi), dan Bagian 6 menguji penalaran arsitektural & verifikasi dasar.
>    - **Pendekatan Praktikum Sintaks (Modul Lanjutan):** Menggunakan format penuh skrip idempotent + *seeder* + 4 contoh kode bertingkat + *State Tracing* dengan tetap mematuhi batas sintaks per level.
> 9. **Gaya Bahasa Buku Ajar yang Membimbing & Profesional (*Guiding Mentor Tone & Zero Meta-Leakage*):**
>    - Tulislah modul dengan **bahasa tutor yang membimbing, jelas, suportif, dan menghargai peserta didik** (gunakan sapaan langsung yang membangun pemahaman seperti *"Pada tahap ini, kita akan mempelajari..."*, *"Perhatikan peran tiap bagian..."*, *"Tipe Data Dasar yang Umum Digunakan"*, *"Kendala Umum & Cara Mengatasinya"*).
>    - **DILARANG** memberi label yang merendahkan atau menempelkan stigma tingkat kemampuan pembaca pada judul, subjudul, maupun penjelasan (misalnya: *"untuk pemula"*, *"sering dipakai pemula"*, *"ramah pemula"*, *"panduan pemula"*, *"khusus anak SMK"*, atau *"orang awam"*).
>    - **DILARANG** membocorkan catatan instruksi template atau istilah internal penyusunan ke dalam isi modul (seperti `*(Wajib Terperinci)*`, `*(Minimal 4 Contoh Terpandu)*`, `*(Pola Kembar Contoh)*`, `` `[INTI: ...]` ``, `"Mode A/Mode B"`, `"Zero Untaught Syntax"`, atau catatan defensif tentang fitur apa saja yang belum diajarkan).
> 10. **Kunci Jawaban Terpisah & Target Visual Output (*Separated Answer Key & Visual Output Target*):**
>    - Kunci jawaban kode/kueri SQL lengkap dan rancangan solusi **DILARANG** ditulis langsung di dalam modul praktikum siswa agar tidak mengurangi tantangan belajar aktif.
>    - Kunci jawaban seluruh modul dikumpulkan dan disatukan dalam satu dokumen terpisah (misalnya: `KUNCI_JAWABAN_LATIHAN_SOAL_*.md` sebagai buku pegangan instruktur/guru).
>    - Di dalam modul praktikum siswa, Bagian 7 difokuskan murni sebagai **Panduan Evaluasi & Checklist Mandiri**.
>    - **Standar Visual Output Kueri (`SELECT`):** Jika soal latihan menguji perintah pembacaan data (`SELECT`, `WHERE`, pengurutan, agregasi, atau `JOIN`), Bagian 7 **WAJIB menyajikan contoh hasil akhir tampilan tabel yang diinginkan (*Expected Output Table Grid*)** dalam format teks/ASCII tabel MySQL (`+---+---+`) lengkap dengan jumlah baris yang dihasilkan. Dengan demikian, siswa dapat mencocokkan hasil kueri di terminal/editor mereka secara visual tanpa melihat kunci sintaks SQL-nya.

---

# MODUL PRAKTIKUM: [NAMA TOPIK / TEKNOLOGI]
- **Subjek / Mata Kuliah:** [Nama Mata Pelajaran SMK / Mata Kuliah]
- **Target Level:** [SMK / Mahasiswa / Terpadu Bertingkat]
- **Fokus Materi:** [Satu subtopik atau alur konsep utama yang tuntas dipelajari]
- **Tema Berkelanjutan Aktif:** Tema 1 (`[Nama Tema 1]`), Tema 2 (`[Nama Tema 2]`), *[Opsional: Tema 3 (`[Nama Tema 3]`)]*

---

### 1. Prasyarat, Jembatan Konsep, & Peta Alur

#### A. Pengingat Prasyarat Cepat (2 Menit)
*Sebelum melangkah ke materi baru, segarkan kembali konsep prasyarat berikut:*
- **Konsep yang Harus Sudah Dipahami:** [Sebutkan 1–2 konsep kunci dari modul sebelumnya, misal: `PRIMARY KEY` dan relasi `FOREIGN KEY`.]
- **Cek Kilat Prasyarat (Jawab Singkat Sebelum Lanjut):**
  1. [Pertanyaan singkat 1 tentang konsep sebelumnya] *(Jawab singkat: `...`)*
  2. [Pertanyaan singkat 2 yang menjadi modal langsung untuk modul ini] *(Jawab singkat: `...`)*

#### B. Jembatan Konsep: Mengapa Fitur Ini Diperlukan?
[Jelaskan untuk pembaca dalam 1–2 paragraf lugas: masalah nyata apa yang terjadi tanpa konsep ini dan bagaimana mekanismenya bekerja di balik layar (*mental model*). Gunakan analogi atau perbandingan teknis konkret.]

#### C. Tujuan Pembelajaran & Peta Alur Kerja
Setelah menyelesaikan modul ini, peserta didik mampu:
1. Menjelaskan fungsi, argumen wajib/opsional, dan hasil keluaran dari perintah/API dasar `[sebutkan fungsi/perintah inti]`.
2. Melacak perubahan data/variabel pada alur eksekusi `[konsep utama]` serta menerapkannya pada **Tema 1** dan **Tema 2** tanpa kesalahan sintaks.
3. Menganalisis pesan kesalahan umum, kasus batas (*edge cases*), dan memverifikasi kesesuaian hasil eksekusi.

**Peta Alur Kerja (*Data / Execution Flow*):**
```text
[Input / Data Awal]
        │
        ▼  (Langkah 1: Fungsi / Perintah 1)
[Kondisi Antara / Intermediate State]
        │
        ▼  (Langkah 2: Fungsi / Perintah 2)
[Validasi / Kondisi Batas] ──(Tidak valid)──► [Pesan Error / Penanganan Aman]
        │ (Valid)
        ▼
[Output / Hasil Akhir]
```

---

### 2. Kamus Fungsi, Perintah, & Argumen Dasar
*Pada bagian ini, Anda akan mempelajari **format umum penulisan**, rincian fungsi/klausa beserta argumennya, dan contoh mini sebelum menerapkannya pada studi kasus.*

#### A. `[Nama Fungsi / Perintah 1]`
- **Kegunaan Utama:** [Penjelasan singkat 1–2 kalimat dengan bahasa lugas tentang apa yang dilakukan fungsi/perintah ini.]
- **Format Umum / Sintaks Baku:**
  *(Selalu awali dengan kerangka pola umum lengkap sebelum contoh nyata; tandai bagian opsional dengan `[...]`)*
  ```[lang]
  PERINTAH_UTAMA [OPSI_OPSIONAL] nama_objek (
      bagian_wajib_1 tipe_atau_format [aturan_opsional],
      bagian_wajib_2 tipe_atau_format [aturan_opsional]
  );
  ```
- **Rincian Parameter / Argumen / Klausa:**

  | Nama Parameter / Klausa | Status | Tipe Data / Format | Penjelasan & Contoh Nilai Valid |
  | :--- | :---: | :--- | :--- |
  | `argumen_1` | **Wajib** | `[string / array / int / nama_kolom]` | [Peran parameter pertama, misal: data sumber yang diproses] |
  | `argumen_2` | **Wajib** | `[callback / kondisi / nilai]` | [Peran parameter kedua, misal: kriteria seleksi/perbandingan] |
  | `argumen_opsional` | *Opsional* | `[bool / int]` | [Peran & nilai bawaan (*default*), misal: bawaan `false`] |

- **Nilai Kembalian (*Return Value*) / Efek Eksekusi:**
  [Jelaskan tipe dan bentuk hasil saat berhasil, serta perilakunya jika input kosong/tidak ditemukan—misal mengembalikan array kosong `[]`, `null`, atau 0 baris.]
- **Contoh Mikro (1–5 Baris Mandiri) & Penjelasan Singkat:**
  ```[lang]
  // Contoh terkecil yang langsung menunjukkan kerja fungsi/perintah ini sesuai Format Umum di atas
  ```
  - *Penjelasan baris:* [Jelaskan bagian inti contoh mikro dan hubungannya dengan Format Umum.]
  - *Hasil eksekusi:* `[tuliskan hasil persisnya]`

#### B. `[Nama Fungsi / Perintah 2]`
*(Ulangi pola struktur yang sama untuk fungsi/perintah/klausa dasar ke-2, ke-3, dan seterusnya hingga tidak ada sintaks asing di Bagian 4.)*

---

### 3. Persiapan Lingkungan & Skema Praktikum
*(Catatan penulis: Untuk modul fondasi/instalasi, cantumkan spesifikasi sistem, checklist persiapan GUI, dan profil skenario kebutuhan Tema 1–3 tanpa skrip DDL/DML yang belum diajarkan. Untuk modul praktikum sintaks, sediakan skrip inisialisasi idempotent sesuai batas sintaks levelnya.)*

- **Kebutuhan Lingkungan:** `[Bahasa / DBMS / Framework + versi minimal, misal PHP 8.2 / MySQL 8.x / Python 3.11 / Wokwi Arduino Uno]`
- **Peta Status Tema Berkelanjutan (Progresi Lintas Modul):**

  | Tema | Domain Sistem | Status dari Modul Sebelumnya | Target Penambahan di Modul Ini |
  | :--- | :--- | :--- | :--- |
  | **Tema 1 (Inti)** | `[Misal: toko_db]` | `[Komponen/tabel yang sudah ada]` | `[Fitur/komponen baru di Bagian 4 & Level 1–2]` |
  | **Tema 2 (Transfer)** | `[Misal: akademik_db]` | `[Komponen/tabel yang sudah ada]` | `[Milestone baru di Level 3]` |
  | **Tema 3 *(Opsional)*** | `[Misal: logistik_db]` | `[Komponen/tabel yang sudah ada]` | `[Milestone analitik/optimasi di Level 4]` |

- **Inisialisasi Tema 1 — Jalur Contoh & Latihan Dasar (*Siap Salin & Jalankan*):**
  ```[lang]
  // Skrip idempotent Tema 1 lengkap (skema + 5–10 data uji)
  ```
- **Inisialisasi Tema 2 *(dan Tema 3 bila dipakai)* — Jalur Praktikum Berkelanjutan:**
  ```[lang]
  // Skrip idempotent Tema 2 (checkpoint modul sebelumnya + data uji siap pakai untuk Level 3–4)
  ```

---

### 4. Contoh Praktik Bertingkat — Studi Kasus `[Tema 1]`
*Seluruh contoh di bagian ini berfokus pada studi kasus `[Tema 1]` dengan peningkatan satu konsep baru pada setiap tahapnya.*

> **Alur Wajib Setiap Contoh Praktik:**
> 1. **Format Umum / Pola Perintah:** Awali dengan pola kerangka sintaks umum (atau rujuk pola di Bagian 2 bila variasi).
> 2. **Rancangan Data (Kamus Data / Diagram Skema):** Untuk setiap contoh pembuatan atau perubahan struktur data (`CREATE TABLE`, `ALTER TABLE`, relasi tabel/`JOIN`), **wajib** sajikan tabel **Kamus Data** dan/atau **Diagram Skema** terlebih dahulu sebelum kode ditulis.
> 3. **Kode Implementasi:** Tulis kode lengkap siap salin-jalankan.
> 4. **Penjelasan Tiap Baris:** Bedah **baris demi baris** dari awal hingga akhir (bukan sekadar ringkasan global), diikuti **State Tracing / Hasil Keluaran**.

#### Contoh 1 — Kasus Paling Dasar
*Penggunaan dasar satu fungsi atau langkah paling sederhana.*
- **Format Umum yang Dipakai:**
  ```[lang]
  // Kerangka sintaks umum singkat untuk pola Contoh 1
  ```
- **Rancangan Data (*Kamus Data / Diagram Skema*):**
  *(Untuk DDL/Tabel, wajib tampilkan Kamus Data kolom, tipe, & aturan serta diagram skema sebelum kode)*

  | Nama Kolom / Elemen | Tipe Data & Panjang | Aturan / Keterangan |
  | :--- | :--- | :--- |
  | `[kolom_1]` | `[tipe]` | `[PRIMARY KEY / NOT NULL / deskripsi]` |

- **Kode Implementasi:**
  ```[lang]
  // scripts/contoh_01_dasar...
  ```
- **Penjelasan Tiap Baris:**
  - **Baris 1 (`...`):** [Jelaskan fungsi baris ke-1]
  - **Baris 2 (`...`):** [Jelaskan fungsi baris ke-2]
  - *(Lanjutkan hingga seluruh baris kode penting dijelaskan satu per satu)*
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 1]
  ```

#### Contoh 2 — Variasi Argumen / Kondisi Tunggal
*Mengembangkan Contoh 1 dengan mengubah atau menambah satu parameter/opsi.*
```[lang]
// scripts/contoh_02_variasi...
```
- **Perbedaan dengan Contoh 1:** [Jelaskan bagian mana yang berubah dan mengapa hasilnya berubah.]
- **Pelacakan Kondisi Antara (*State Tracing*):**
  ```text
  [Tunjukkan kondisi data/variabel sebelum filter/proses → baris/nilai mana yang gugur atau berubah → kondisi akhir]
  ```
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 2]
  ```

#### Contoh 3 — Kombinasi Menengah
*Menghubungkan dua fungsi atau perintah dari Bagian 2 menjadi satu alur proses berurutan.*
```[lang]
// scripts/contoh_03_kombinasi...
```
- **Pelacakan Alur Data (*Step-by-Step Trace*):**
  ```text
  Input Awal ──► [Output Tahap 1] ──► [Transformasi Tahap 2] ──► Hasil Akhir
  ```
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 3]
  ```

#### Contoh 4 — Penerapan Lanjutan & Penanganan Kasus Batas (Pendalaman)
> **Catatan Pendalaman:** Bagian ini mengajak Anda memahami penanganan kasus batas (*edge case*), validasi keandalan, atau pertimbangan efisiensi sistem.

```[lang]
// scripts/contoh_04_produksi_edge_case...
```
- **Mengapa Langkah Ini Penting:** [Jelaskan kasus batas apa yang ditangani dan dampaknya pada keandalan/performa sistem.]
- **Hasil Keluaran:**
  ```text
  [Output nyata dari Contoh 4]
  ```

---

### 5. Verifikasi Output & Panduan Troubleshooting

#### A. Ringkasan Ekspektasi Output Contoh 1–4
| Contoh | Jalur | Fokus Fitur yang Diuji | Indikator Berhasil / Output Kunci |
| :--- | :---: | :--- | :--- |
| **Contoh 1** | Inti | Penggunaan dasar `[Fungsi 1]` | [Output ringkas / jumlah baris] |
| **Contoh 2** | Inti | Variasi parameter `[argumen/klausa]` | [Output ringkas / perubahan hasil] |
| **Contoh 3** | Inti | Kombinasi `[Fungsi 1]` + `[Fungsi 2]` | [Output gabungan yang tepat] |
| **Contoh 4** | Pendalaman | Penanganan kasus batas / validasi | [Respons aman saat input kosong/salah] |

#### B. Kesalahan Umum & Cara Memperbaikinya
| Kesalahan / Gejala Error | Penyebab Umum pada Fungsi/Argumen | Solusi Tepat |
| :--- | :--- | :--- |
| `[Error 1 / Output Null]` | [Salah tipe argumen atau urutan parameter tertukar] | [Perbaikan konkret yang harus dilakukan] |
| `[Error 2 / Hasil Keliru]` | [Lupa kondisi batas, filter terbalik, atau mengabaikan nilai opsional] | [Cara mengecek dan memperbaiki logika] |
| `[Error 3 / Lambat / Crash]` | [Tidak menangani data kosong atau melakukan operasi berulang tidak perlu] | [Terapkan validasi awal / *guard clause*] |

---

### 6. Latihan Soal

*Perhatikan tabel-tabel data acuan berikut sebelum mengerjakan latihan soal:*

#### Tabel: [nama_tabel_1, misal: karyawan]

| id | nama | jabatan | gaji |
| :---: | :--- | :--- | :---: |
| 1 | Budi | Manager | 100000 |
| 2 | Siti | Staff | 50000 |
| 3 | Andi | Staff | 60000 |
| 4 | Rina | Supervisor | 80000 |
| 5 | Joko | Manager | 120000 |

#### Tabel: [nama_tabel_2, misal: produk]

| id_produk | nama_produk | harga | stok |
| :---: | :--- | :---: | :---: |
| 1 | Laptop | 1500000 | 5 |
| 2 | Smartphone | 500000 | 10 |
| 3 | Tablet | 800000 | 2 |
| 4 | Monitor | 1200000 | 8 |
| 5 | Keyboard | 300000 | 15 |

*(Sajikan tabel-tabel acuan lainnya yang relevan dengan topik modul, seperti tabel `order`, `pelanggan`, atau spesifikasi kamus kolom untuk modul DDL).*

---

#### Daftar Tugas Praktik
1. Tulis perintah [SQL/kode] untuk menambahkan data [nama_tabel] baru dengan [daftar nilai kolom].
2. Tulis perintah [SQL/kode] untuk memperbarui [kolom] pada [nama_tabel] dengan [kondisi] menjadi [nilai baru].
3. Tulis perintah [SQL/kode] untuk menghapus data pada [nama_tabel] dengan [kondisi].
4. Tulis perintah [SQL/kode] untuk menampilkan [kolom spesifik/semua data] dari [nama_tabel] yang memiliki [kondisi].
5. Tulis perintah [SQL/kode] untuk [menghitung/mengagregasi] [kolom] dari [nama_tabel] dan menampilkan hasilnya.
6. Tulis perintah [SQL/kode] untuk memperbarui [kolom] pada [nama_tabel] dengan [kondisi].
7. Tulis perintah [SQL/kode] untuk menghapus data dari [nama_tabel] dengan kombinasi kondisi [kondisi_1] dan [kondisi_2].
8. Tulis perintah [SQL/kode] untuk memilih [kolom_1] dan [kolom_2] dari [nama_tabel], urutkan berdasarkan [kolom_urut] secara [ascending/descending].
9. Tulis perintah [SQL/kode] untuk memperbarui beberapa kolom sekaligus pada [nama_tabel] dengan [kondisi].
10. Tulis perintah [SQL/kode] untuk menampilkan [kolom relasi/gabungan/kelompok] berdasarkan [kondisi pengelompokan/relasi].

---

### 7. Panduan Evaluasi & Checklist Mandiri
*Gunakan petunjuk ringkas berikut untuk mencocokkan hasil eksekusi kueri latihan soal Anda secara mandiri:*

#### A. Indikator Keberhasilan Tugas & Target Tampilan Output
*(Jika soal menguji perintah `SELECT`, tampilkan contoh hasil akhir tampilan tabel yang diinginkan dalam format grid ASCII MySQL agar siswa dapat mencocokkan hasil visualnya tanpa melihat kunci kuerinya):*

- **Target Output Soal 1:**
  ```text
  +---------+----------+
  | kolom_1 | kolom_2  |
  +---------+----------+
  | nilai_1 | nilai_2  |
  +---------+----------+
  [N] rows in set
  ```
*(Untuk soal manipulasi DML/DDL, tampilkan indikator baris terdampak `Query OK` atau cetakan struktur kolom `DESCRIBE`).*

#### B. Checklist Kesiapan Teknis
- [ ] Seluruh butir perintah SQL di atas berhasil dijalankan tanpa pesan error.
- [ ] Hasil tampilan tabel atau perubahan data di editor cocok persis dengan target visual yang diharapkan.

> **Catatan Buku Pegangan Pengajar:**
> Kunci jawaban kueri SQL lengkap dan pembahasan detail untuk seluruh butir latihan soal dihimpun secara terpisah pada dokumen pegangan instruktur (`KUNCI_JAWABAN_*.md`) agar modul praktikum tetap dapat digunakan sebagai sarana latihan mandiri yang menantang bagi peserta didik.

---

### 8. Ringkasan Fungsi & Refleksi Pemahaman

| Fungsi / Perintah | Kegunaan Inti | Parameter Kritis | Nilai Kembalian / Efek |
| :--- | :--- | :--- | :--- |
| `[Fungsi 1]` | [Ringkasan fungsi 1] | `[Param wajib]` | `[Tipe/hasil kembali]` |
| `[Fungsi 2]` | [Ringkasan fungsi 2] | `[Param wajib]` | `[Tipe/hasil kembali]` |

**Pertanyaan Refleksi:**
1. *Jelaskan dengan bahasamu sendiri: kapan kita menggunakan `[Fungsi 1]` dibanding `[Fungsi 2]`, dan apa akibatnya jika argumen `[X]` diisi tipe data yang salah?*
2. *Dari penerapan pada Tema 1 dan Tema 2, apa pola perubahan yang tetap sama meskipun nama tabel/variabelnya berbeda?*
