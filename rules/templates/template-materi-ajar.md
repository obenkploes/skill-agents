# STANDAR FORMAT MATERI AJAR (MODUL BELAJAR SISWA)

Aturan baku penyusunan modul **Materi Ajar** yang dibaca, dipelajari, dan dikerjakan langsung oleh peserta didik / santri. Modul ini diformat sebagai bahan belajar yang komunikatif, terstruktur, tuntas tanpa memuat instruksi pengajar atau rubrik penilaian tutor, dan **dikalibrasi untuk pembelajaran tatap muka 80 menit (1 pertemuan per minggu)** serta belajar mandiri selama jeda pekan.

> **PRINSIP KALIBRASI WAJIB BAGI PENYUSUN MODUL:**
> 1. **Anggaran Waktu 80 Menit/Minggu:** Batasi cakupan pada **1 konsep inti** (atau maksimal 2 sub-konsep kecil yang menyambung langsung). Jaga agar penjelasan Bagian 1–3 padat dan dapat dipahami dalam ≤ 15 menit, sehingga porsi terbesar jam kelas terpakai untuk contoh terbimbing dan latihan soal bertahap.
> 2. **Diferensiasi Jenjang (SMP vs SMA):**
>    - **Jalur SMP (Kelas 7–9):** Gunakan bahasa ringan, analogi konkret kehidupan harian, dan **angka bulat atau pecahan sederhana ramah hitung**. Hindari hasil berupa bentuk akar irasional atau manipulasi pecahan aljabar bertingkat, kecuali memang topik pokok pertemuan tersebut.
>    - **Jalur SMA (Kelas 10–12):** Boleh memuat abstraksi simbolik dan pembuktian bertahap bila sesuai silabus, namun **tetap wajib** memulai Contoh 1 dan Latihan 6A–6B dari bilangan ramah hitung sebelum naik ke variasi aljabar.
> 3. **Prinsip *Contoh Kembar (1-to-1 Pairing)*:** Setiap variasi bentuk soal di `Bagian 6 (Latihan Soal Kelas)` **wajib** memiliki padanan contoh penyelesaian langkah demi langkah di `Bagian 4` atau `Bagian 5`. Dilarang menyelipkan pola manipulasi baru yang belum dicontohkan.
> 4. **Latihan Bertingkat Halus (*Smooth Scaffolding*):** Bangun pemahaman lewat repetisi bertahap (terbimbing → penguasaan prosedur 4–5 soal → soal cerita terpisah → 1 soal tantangan opsional), **bukan** loncat langsung dari 2 soal dasar ke soal pecahan/akar atau HOTS.
> 5. **Format Bersih & Portabel:** Gunakan LaTeX KaTeX murni (`$...$` inline, `$$...$$` display block) dan penomoran standar agar rapi saat dibuka di Google Docs maupun penampil Markdown.
> 6. **Konteks & Kosakata Sesuai Nilai Islam:** Gunakan latar yang baik dan halal (`kantin`, `toko`, `pasar`, `zakat`, `infak`, `bola bernomor`); **hindari** istilah atau konteks yang bertentangan dengan Islam seperti `koperasi`, transaksi berbunga/riba (`bunga bank`, `bunga tunggal/majemuk`), `dadu`, `kartu remi`, `undian`, atau `musik`.
> 7. **Instruksi Terpusat (Anti-Repetisi):** Jika instruksi soal pada suatu sub-bagian seragam, tuliskan kalimat instruksi **cukup satu kali** di judul atau kalimat pengantar sub-bagian (contoh: `#### A. Tentukan nilai $x$ dan $y$ dari sistem persamaan berikut:`). **DILARANG MENGULANG** kalimat instruksi yang sama di setiap butir nomor soal (`1. Tentukan nilai x dan y...`, `2. Tentukan nilai x dan y...`). Setiap butir nomor soal langsung menyajikan bentuk matematisnya secara bersih (`1. $$...$$`, `2. $$...$$`).
> 8. **Bebas Label Meta Internal Authoring:** DILARANG mencantumkan teks panduan internal authoring seperti `*(Pola Kembar Contoh 1)*`, `*(Pola Kembar Contoh 2)*`, atau label deskriptif kategori soal (`1. Koefisien bulat positif sederhana:`, `2. Memuat suku koefisien negatif:`) pada lembar latihan siswa. Prinsip *Contoh Kembar* dan scaffolding bertahap adalah panduan perancangan bagi penyusun modul, bukan teks untuk dicetak pada soal siswa.
> 9. **Kelugasan Konsep & Zero Forced Analogy:** Awali penjelasan konsep secara lugas, komunikatif, dan langsung ke inti materi matematis. Jangan memaksakan analogi filosofis, ayat, atau dalil keagamaan jika tidak relevan secara ilmiah atau terkesan dibuat-buat. Gunakan analogi fenomena alam atau keseharian konkret yang proporsional dan masuk akal. Bila konsep sudah jelas, langsung masuk ke materi inti.
> 10. **Format Penyelesaian Menurun Baris per Baris (Anti-Teks Menumpuk):** Seluruh proses perhitungan, pemetaan variabel, dan penjabaran aljabar pada contoh soal dan pembahasan **WAJIB ditulis menurun ke bawah baris per baris** (menggunakan lingkungan KaTeX `\begin{aligned} ... \end{aligned}` atau blok baris terpisah dengan spasi vertikal yang lega). **DILARANG KERAS** menyusun rantai persamaan aljabar menyamping/horizontal yang panjang dengan deretan tanda implikasi ($\implies$) atau sama dengan ($=$) beruntun (contoh yang dilarang: `$2(x' + 1) - 3(y' - 4) + 6 = 0 \implies 2x' + 2 - 3y' + 12 + 6 = 0 \implies 2x' - 3y' + 20 = 0$`). Penulisan horizontal membuat teks menumpuk, sesak dibaca di layar maupun cetak, serta menyulitkan siswa melacak alur logika perubahan per baris.
> 11. **Fokus Repetisi & Penguatan Konsep Dasar (Beban Belajar Terkalibrasi):** Mengingat keterbatasan jam tatap muka siswa dan padatnya agenda kegiatan harian mereka (terutama kegiatan asrama/santri/madrasah), contoh dan soal latihan **wajib difokuskan pada penguatan dan repetisi konsep dasar yang esensial** sampai siswa benar-benar paham fondasinya sebelum masuk ke variasi lanjutan. Hindari manipulasi aljabar berbelit, angka ekstrem, atau bentuk kuadrat/akar rumit di awal. Utamakan pola pengulangan terfokus (misal: satu objek/titik yang sama diuji ke beberapa variasi aturan dasar) agar konsep dasar terekam kuat dan intuitif.

---

# [JUDUL BAB / MATA PELAJARAN]
## Pertemuan [X]: [Nama Topik / Subtopik Pembahasan]

---

### 1. Pemanasan Prasyarat & Konsep Dasar
*Mulai dengan 2 soal kilat untuk menyegarkan ingatan materi pekan lalu (karena jeda belajar 1 minggu), lalu sajikan pengantar konsep utama secara ringkas dan komunikatif.*

#### A. Pemanasan Cepat (3 Menit)
Kerjakan soal pengingat berikut sebelum masuk ke materi baru:
1. [Soal kilat prasyarat 1, misal: hitung operasi bilangan bulat / substitusi nilai sederhana]
2. [Soal kilat prasyarat 2 yang langsung menjadi modal langkah awal materi hari ini]

*(Cek singkat: No. 1 = `[jawaban]`, No. 2 = `[jawaban]`)*

#### B. Pengertian Konsep Dasar
[Tuliskan pengertian konsep utama dalam 1–2 paragraf yang ringkas, komunikatif, dan lugas tanpa analogi filosofis/keagamaan yang dipaksakan.]

**Analogi Konkret & Proporsional (Bila Diperlukan):**
- **[Sesuai Jenjang SMP/SMA]:** [Gunakan analogi konkret dan logis yang akrab bagi siswa. Contoh SMP: neraca timbangan untuk persamaan linear, denah rumah untuk skala. Contoh SMA: koordinat ruang untuk posisi fisik, aliran pengisian tandon air untuk laju perubahan. Jika konsep sudah jelas tanpa analogi, langsung masuk ke materi inti.]

---

### 2. Bentuk Umum & Rumus Baku
*Tuliskan maksimal 1–2 formula inti yang benar-benar digunakan pada pertemuan ini menggunakan notasi KaTeX yang rapi (`$...$` untuk inline dan `$$...$$` untuk display blok). Pastikan seluruh simbol diberi keterangan jelas.*

Bentuk umum [nama konsep] dituliskan sebagai:

$$[Tuliskan\ rumus\ utama\ di\ sini,\ contoh:\ ax^2 + bx + c = 0 \quad \text{atau} \quad U_n = a + (n-1)b]$$

**Keterangan:**
- [Simbol 1] = [arti simbol dan satuan/syaratnya]
- [Simbol 2] = [arti simbol dan satuan/syaratnya]
- [Simbol 3] = [arti simbol dan syarat nilai, misal $a \neq 0$ atau $n \in \mathbb{N}$]

---

### 3. Sifat-Sifat & Aturan Penting
*Paparkan maksimal 2–3 syarat atau aturan main paling penting yang langsung terpakai di latihan hari ini agar siswa tidak kewalahan.*

Beberapa aturan penting yang wajib diperhatikan:
1. **[Aturan / Syarat 1]:** [Penjelasan ringkas dan contoh angka kecil yang jelas.]
2. **[Aturan / Syarat 2]:** [Penjelasan ringkas tanpa jargon berlebihan.]

*(Gunakan tabel ringkas berikut hanya jika pertemuan memang membandingkan 2–3 kasus berbeda):*

| Kasus / Kondisi | Ciri yang Terlihat | Langkah / Rumus yang Dipakai |
| :--- | :--- | :--- |
| **Kondisi A** | [Ciri A] | $$[Rumus\ /\ Aturan\ A]$$ |
| **Kondisi B** | [Ciri B] | $$[Rumus\ /\ Aturan\ B]$$ |

---

### 4. Contoh Soal & Pembahasan Bertingkat Mikro
*Sajikan minimal **2 contoh** (SMP) atau **2–3 contoh** (SMA) yang naik tingkat secara halus dan berpasangan langsung (Contoh Kembar) dengan tipe soal pada Bagian 6. Fokuskan contoh pada penguatan dan repetisi konsep dasar secara teratur. Setiap contoh wajib memuat: **Diketahui**, **Ditanyakan**, **Langkah Penyelesaian** yang ditulis **MENURUN KE BAWAH** baris per baris (menggunakan lingkungan KaTeX `\begin{aligned} ... \end{aligned}` atau blok baris menurun), dan **Kesimpulan** ($\checkmark\ \text{Benar}$). DILARANG menyusun langkah aljabar menyamping secara horizontal.*

#### Contoh 1 (Tingkat Dasar — Bilangan Bulat Sederhana)
**Soal:**
[Tuliskan soal inti yang paling bersih, memakai bilangan bulat positif dan hasil yang rapi.]

**Penyelesaian:**
- **Diketahui:**
  - [Komponen 1] = $\dots$
  - [Komponen 2] = $\dots$
- **Ditanyakan:** [Nilai/bentuk yang dicari]
- **Langkah Penyelesaian (Menurun):**
  $$
  \begin{aligned}
  [\text{Baris 1: Tuliskan Rumus / Model}] &= \dots \\
  [\text{Baris 2: Substitusi Nilai Diketahui}] &= \dots \\
  [\text{Baris 3: Operasi Hitung Sederhana}] &= \dots \\
  [\text{Baris 4: Hasil Akhir Bersih}] &= \dots
  \end{aligned}
  $$
- **Kesimpulan:** Jadi, nilai yang dicari adalah $\dots$ ($\checkmark\ \text{Benar}$)

#### Contoh 2 (Variasi Ringan — Persiapan Latihan Mandiri)
**Soal:**
[Tuliskan variasi 1 langkah lebih maju dari Contoh 1—misal melibatkan tanda negatif atau koefisien $> 1$—yang polanya akan langsung diujikan di Latihan 6B. Fokuskan pada penguatan konsep dasar, hindari loncatan ke pecahan/akar rumit jika bukan topik intinya.]

**Penyelesaian:**
- **Diketahui:** $\dots$
- **Ditanyakan:** $\dots$
- **Langkah Penyelesaian (Menurun):**
  $$
  \begin{aligned}
  [\text{Baris 1: Perlakuan tanda / aturan khusus}] &= \dots \\
  [\text{Baris 2: Penjabaran bertahap ke bawah}] &= \dots \\
  [\text{Baris 3: Hasil akhir bersih}] &= \dots
  \end{aligned}
  $$
- **Kesimpulan:** Jadi, hasilnya adalah $\dots$ ($\checkmark\ \text{Benar}$)

*(Tambahkan **Contoh 3** khusus untuk Jalur SMA atau pertemuan pendalaman apabila diperlukan satu pola aljabar tambahan atau langkah pembuktian terpandu.)*

---

### 5. Penerapan Kontekstual (Studi Kasus Nyata / Santri)
*Sajikan 1 studi kasus soal cerita nyata dalam keseharian siswa atau lingkungan pesantren (hafalan Qur'an, jadwal piket/konsumsi santri, infak, jual-beli kantin/toko, pengukuran jarak/luas) dengan **angka yang ramah hitung**. Contoh ini berfungsi sebagai model langsung bagi Soal Cerita di Bagian 6C.*

#### Contoh Kasus:
> [Sajikan narasi cerita masalah sehari-hari yang ringkas dan jelas pertanyaannya.]

**Langkah Pemecahan:**
1. **Membuat Model Matematika:**
   - Misalkan [variabel] = [arti besaran]
   - Persamaan / model: $$[Tuliskan\ model\ matematika]$$
2. **Perhitungan:**
   [Uraikan langkah hitung sistematis baris demi baris.]
3. **Jawaban Kontekstual:**
   Jadi, [tuliskan kalimat jawaban yang menjawab konteks cerita secara konkret].

---

### 6. Latihan Soal Kelas (Bertingkat & Terstruktur)
*Paket soal latihan untuk dikerjakan siswa di kelas (~35–40 menit). Disusun sebelum bagian Pola Kunci agar siswa membangun pemahaman dari praktik, bukan sekadar menghafal jalan pintas. Seluruh instruksi diletakkan terpusat pada judul/pengantar sub-bagian (tanpa diulang di setiap nomor soal), dan bebas dari label meta authoring seperti `*(Pola Kembar)*` atau label kategori scaffolding.*

#### A. Latihan Terbimbing (Ikuti Langkah Contoh)
*Pola soal identik dengan Contoh 1–2 sebagai pijakan awal agar siswa langsung mengalami keberhasilan pertama. Tuliskan instruksi umum di awal, tanpa tag meta authoring `*(Pola Kembar)*` di butir nomor soal.*

Kerjakan soal berikut dengan mengikuti urutan langkah pada contoh yang telah dipelajari:
1. [Soal bernomor langsung tanpa tag *(Pola Kembar)*; boleh disertai petunjuk langkah awal jika perlu]
2. [Soal bernomor langsung tanpa tag *(Pola Kembar)* dengan angka baru yang tetap bulat dan mudah dihitung]

#### B. Penguasaan Prosedur Inti (Latihan Bertahap)
*Latihan inti berulang (4–5 soal) dengan angka bulat/rasional bersih yang naik perlahan antar-nomor untuk membentuk pemahaman yang utuh.*

[Tuliskan satu kalimat instruksi umum dan seragam di sini, misal: *"Tentukan himpunan penyelesaian dari persamaan berikut secara sistematis:"* atau *"Selesaikan operasi aljabar berikut:"*. DILARANG mengulang instruksi ini di setiap nomor soal]:
1. [Soal langsung menyajikan rumus/persamaan; DILARANG memberi label kategori seperti "1. Koefisien positif:"]
2. [Soal variasi kedua langsung menyajikan persamaan]
3. [Soal variasi ketiga langsung menyajikan persamaan]
4. [Soal variasi keempat langsung menyajikan persamaan]
5. [*(Opsional soal ke-5)* Soal variasi kelima langsung menyajikan persamaan]

#### C. Soal Cerita Kontekstual
*Dipisahkan khusus agar siswa fokus melatih kemampuan mengubah kalimat cerita menjadi model matematika sesuai Bagian 5.*

1. [Soal cerita 1: latar keseharian siswa/pesantren, sepola dengan Bagian 5, angka ramah hitung]
2. [*(Opsional)* Soal cerita 2: variasi konteks ringan dengan kompleksitas perhitungan setara]

#### D. Soal Tantangan *(Opsional / Pengayaan)*
*Dikerjakan hanya jika Bagian A–C sudah selesai dan masih tersedia waktu di kelas.*

1. [Satu soal penalaran terstruktur atau variasi sedikit lebih dalam—tetap bertumpu pada rumus pertemuan ini, bukan materi lompat jauh]

---

### 7. Pola Kunci, Jebakan Umum, & Cara Cepat
*Disajikan setelah siswa mencoba Latihan Soal Kelas untuk menguatkan pola berpikir dan cara mengecek ketepatan jawaban.*

- **Pola Kunci yang Terbentuk:**
  - *"[Tuliskan intisari pola yang baru dipraktikkan di Bagian 6 agar melekat sebagai logika, bukan hafalan buta]"*
  - **Cara Cek Cepat Hasil:** [Jelaskan 1 langkah verifikasi sederhana, misal: substitusikan kembali akar yang didapat ke persamaan awal untuk memastikan hasilnya nol.]
- **Waspada Jebakan Umum:**
  - ⚠️ *[Sebutkan kesalahan tanda/operasi paling sering terjadi pada topik ini, contoh: hati-hati mengalikan bilangan negatif saat memindah atau membuka kurung.]*
  - ⚠️ *[Sebutkan syarat batas/langkah krusial yang sering terlupa, contoh: pastikan urutan langkah atau syarat penyebut $\neq 0$.]*

---

### 8. Pekerjaan Rumah (PR Pondok / Mandiri)
*Tugas ringan terukur untuk menjaga ingatan selama jeda 6 hari sebelum pertemuan pekan depan.*

**Petunjuk:**
- Kerjakan di buku tugas dengan menuliskan apa yang diketahui, rumus/model, dan langkah perhitungannya.
- Setelah selesai, cocokkan hasil akhirmu dengan **Kunci Jawaban Akhir** di bawah untuk memastikan prosesmu sudah tepat.

1. [Soal penguatan prosedur rutin 1 (setara 6B no. 1–2)]
2. [Soal penguatan prosedur rutin 2 (setara 6B no. 3–4)]
3. [Soal cerita aplikatif sederhana seputar aktivitas harian/santri (setara 6C)]
4. **Pertanyaan Pemahaman Konsep:**
   *Jelaskan dengan kata-katamu sendiri: mengapa [aturan/syarat inti pada topik ini] harus diperhatikan saat menyelesaikan soal? Sertakan satu contoh kecil.*

**Kunci Jawaban Akhir Ringkas (Cek Mandiri):**
- **Latihan 6A:** `1.` $\dots$ | `2.` $\dots$
- **Latihan 6B:** `1.` $\dots$ | `2.` $\dots$ | `3.` $\dots$ | `4.` $\dots$ | `5.` $\dots$
- **Latihan 6C:** `1.` $\dots$
- **PR No. 1–3:** `1.` $\dots$ | `2.` $\dots$ | `3.` $\dots$

---

### 9. Ringkasan Materi
*Rangkuman padat 2–4 poin paling penting yang wajib diingat siswa setelah menutup modul.*

- **Poin 1:** [Rumus/bentuk umum paling utama]
- **Poin 2:** [Syarat atau aturan kunci yang menentukan]
- **Poin 3:** [Urutan langkah inti pengerjaan + cara memeriksa hasil]
