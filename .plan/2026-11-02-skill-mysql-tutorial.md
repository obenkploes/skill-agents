# IMPLEMENTATION PLAN: REVISI MODUL SKILL MYSQL TUTORIAL (SILABUS TEMATIK PER PEMBAHASAN / FOCUSED TOPIC MODULES)

- **Tanggal Pembuatan**: 2026-11-02
- **Kategori**: database / tutorial / curriculum
- **Lokasi Berkas**: `.plan/2026-11-02-skill-mysql-tutorial.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang - Tinggi (Granular 36 Thematic Topic Modules & Pedagogical Balance)

---

## 1. TUJUAN & RUANG LINGKUP

### Masukan & Evaluasi Pengguna (User Feedback)
Pengguna memberikan koreksi penting terhadap rancangan silabus:
> *"Revisi plan : buat kelompok materi tidak per level tetapi per pembahasan misal : materi 1 DDL, materi 2 DML, materi 3 Where clause, sehingga setiap kelompok pembahasan mendapat porsi pembelajaran yang sama untuk menguatkan pemahaman siswa / mahasiswa. Jika dibuat level maka materi terlalu padat."*

### Pendekatan Solusi (Pedagogical Re-engineering)
Membagi silabus ke dalam **unit pembahasan tematik tunggal (*Single Topic Focus*)**. Setiap modul tutorial dirancang dengan beban belajar yang seimbang, mandiri (*self-contained*), dan memiliki alur bertahap tanpa memadatkan terlalu banyak konsep dalam satu waktu.

Total materi dipetakan menjadi **36 Modul Pembahasan Tematik Terurut**, yang terbagi ke dalam 8 Seri Kurikulum:

---

## 2. ROADMAP SILABUS 36 MODUL PEMBAHASAN TEMATIK TERURUT

### Seri 1: Fondasi, Desain Skema, & DDL (Data Definition Language)
- **Materi 01: Arsitektur MySQL Server, Pluggable Storage Engine, & Tooling** (Client-Server, InnoDB vs Memory, CLI `mysql`, Workbench, DBeaver).
- **Materi 02: DDL 1 - Manajemen Database & Karakter Encoding** (`CREATE DATABASE`, `DROP`, `utf8mb4_0900_ai_ci`).
- **Materi 03: Tipe Data Numerik & String** (`TINYINT` s/d `BIGINT`, `DECIMAL(p,s)`, `VARCHAR` vs `CHAR`, `TEXT`).
- **Materi 04: Tipe Data Waktu & Konversi Zona** (`DATE`, `DATETIME` vs `TIMESTAMP`, penanganan timezone).
- **Materi 05: DDL 2 - Pembuatan Tabel Dasar & Constraint Sederhana** (`CREATE TABLE`, `PRIMARY KEY`, `NOT NULL`, `DEFAULT`).
- **Materi 06: DDL 3 - Validasi Data Tingkat Lanjut** (`UNIQUE`, `CHECK` constraint native MySQL 8, `ENUM`).
- **Materi 07: DDL 4 - Relasi Antar Tabel & Foreign Key Constraints** (One-to-Many, cascade rules: `ON DELETE CASCADE`, `ON DELETE SET NULL`, `RESTRICT`).
- **Materi 08: DDL 5 - Alter Table & Pemeliharaan Skema** (`ALTER TABLE` add, modify, drop column, add constraint, rename table).
- **Materi 09: DDL 6 - Kolom Terkomputasi (Generated Columns)** (Virtual vs Stored Generated Columns dan manfaatnya).

### Seri 2: DML & Pengambilan Data (Querying & Filtering)
- **Materi 10: DML 1 - Penyisipan Data (Insert & Upsert)** (`INSERT INTO`, multi-row insert, `INSERT ... SELECT`, `ON DUPLICATE KEY UPDATE`).
- **Materi 11: DML 2 - Pembaruan & Penghapusan Data** (`UPDATE` dengan WHERE, `DELETE`, perbandingan `DELETE` vs `TRUNCATE`).
- **Materi 12: Querying Dasar & Proyeksi Kolom** (`SELECT`, alias kolom `AS`, kalkulasi aritmetika, `DISTINCT`).
- **Materi 13: Filtering Data 1 - WHERE Clause & Operator Logika** (Operator `=`, `!=`, `<`, `>`, kombinasi logika `AND`, `OR`, `NOT`, urutan evaluasi).
- **Materi 14: Filtering Data 2 - Pencarian Range & Himpunan** (`BETWEEN ... AND`, `IN (...)`, `NOT IN (...)`).
- **Materi 15: Filtering Data 3 - Pencarian Pola String & Penanganan NULL** (`LIKE` wildcard `%` dan `_`, `IS NULL`, `IS NOT NULL`).
- **Materi 16: Pengurutan & Pembatasan Data (Sorting & Pagination)** (`ORDER BY ASC/DESC`, multi-column sort, `LIMIT` dan `OFFSET`).

### Seri 3: Agregasi, Pengelompokan, & Multi-Table Joins
- **Materi 17: Fungsi Agregasi Dasar** (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`, perbedaan `COUNT(*)` vs `COUNT(kolom)`).
- **Materi 18: Pengelompokan Data - GROUP BY & HAVING** (Logika pengelompokan baris, aturan kolom agregat, filter kelompok dengan `HAVING`).
- **Materi 19: Relasi Multi-Tabel - INNER JOIN** (Konsep irisan data, sintaks eksplisit `INNER JOIN ... ON`, join 3+ tabel).
- **Materi 20: Relasi Multi-Tabel - LEFT & RIGHT JOIN** (Menemukan data tanpa relasi/unmatched dengan `LEFT JOIN ... WHERE ... IS NULL`).
- **Materi 21: Relasi Multi-Tabel - Self Join & CROSS JOIN** (Struktur hierarki karyawan-manajer, Cartesian product).

### Seri 4: Kueri Lanjutan, Tipe Data Modern, & Analitik
- **Materi 22: Subquery (Kueri Bersarang)** (Scalar subquery, subquery dalam WHERE dengan `IN`/`EXISTS`, subquery dalam FROM).
- **Materi 23: Common Table Expressions (CTE)** (`WITH ... AS` untuk mempermudah kueri kompleks, pembacaan modular).
- **Materi 24: Recursive CTE untuk Data Hierarkis** (`WITH RECURSIVE` untuk kategori bertingkat, pohon organisasi).
- **Materi 25: Window Functions 1 - Ranking & Numbering** (`OVER(PARTITION BY ... ORDER BY ...)`, `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`).
- **Materi 26: Window Functions 2 - Navigasi & Analisis Nilai** (`LAG()`, `LEAD()`, running total kumulatif).
- **Materi 27: Tipe Data JSON & Operasi Dokumen (MySQL 8)** (Kolom JSON, operator panah `->`, `->>`, ekstraksi array).

### Seri 5: Logika Pemrograman & Otomasi Database
- **Materi 28: Views (Tabel Virtual)** (`CREATE VIEW`, `WITH CHECK OPTION`, abstraksi keamanan hak akses).
- **Materi 29: Pemrograman SQL - Stored Procedures** (Delimiter, blok `BEGIN...END`, variabel `DECLARE`, parameter `IN`, `OUT`).
- **Materi 30: User-Defined Functions (Stored Functions)** (`CREATE FUNCTION`, karakteristik deterministik, perbedaan UDF vs Stored Procedure).
- **Materi 31: Triggers & Audit Trail Logging** (`BEFORE/AFTER INSERT/UPDATE/DELETE`, manipulasi `NEW` dan `OLD`, pencatatan riwayat).
- **Materi 32: Otomasi Penjadwalan Tugas (MySQL Event Scheduler)** (Aktivasi scheduler, pembuatan recurring event pembersihan data).

### Seri 6: Transaksi, Optimasi Indeks, & Administrasi
- **Materi 33: Transaksi Database & ACID Engine** (`START TRANSACTION`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`).
- **Materi 34: Arsitektur B+Tree Index & Indexing Fundamental** (Clustered Index PK vs Secondary Index, composite index rule).
- **Materi 35: Analisis Performa Kueri dengan EXPLAIN & EXPLAIN ANALYZE** (Membaca rencana eksekusi, mendeteksi Table Scan vs Index Lookup).
- **Materi 36: Backup & Point-in-Time Recovery (PITR)** (Backup logis `mysqldump --single-transaction`, pemulihan darurat berbasis binlog).

---

## 3. STANDAR FORMAT MODUL LAB PRAKTIKUM (7 BAGIAN TERPADU)

Setiap materi yang dihasilkan wajib mengadopsi format 7 bagian terstruktur:
1. **Bagian 1: Judul Materi & Capaian Pembelajaran Spesifik** (Apa kemampuan nyata mahasiswa setelah selesai).
2. **Bagian 2: Konsep Inti & Arsitektur Teknis** (Penjelasan konsep tunggal yang mendalam + diagram alir/ASCII).
3. **Bagian 3: Prasyarat & Skema Database Idempotent** (Skrip `CREATE DATABASE IF NOT EXISTS`, tabel sampel mandiri).
4. **Bagian 4: Langkah Praktik Terpandu & Skrip SQL Lengkap** (Kueri bertahap dari kasus sederhana ke kompleks tanpa komentar pemalas).
5. **Bagian 5: Verifikasi Hasil Eksekusi & Ekspektasi Output** (Tabel ekspektasi output baris data).
6. **Bagian 6: Anti-Pattern, Kesalahan Umum, & Tips Performa** (Kesalahan yang sering dilakukan pemula dan cara menghindarinya).
7. **Bagian 7: Lab Tantangan Mandiri** (3-5 soal studi kasus baru tanpa kunci jawaban langsung untuk menguji pemahaman).

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Direktori (`skills/mysql/skill.json`)**
  - [x] Pembuatan direktori `skills/mysql`.
  - [x] Penyusunan `skill.json` memuat properti `name: "mysql"`, `category: "database/tutorial"`, triggers (`/mysql`, `/mysql-tutorial`, dll.), keywords, dan aturan rujukan.
- [x] **Fase 2: Pembuatan Entrypoint Antigravity (`skills/mysql/SKILL.md`)**
  - [x] Frontmatter YAML resmi dengan peringatan `MANDATORY WORKFLOW`.
  - [x] Matriks lengkap 36 Modul Pembahasan Tematik Terurut.
  - [x] Panduan pemanggilan per materi (misal: `/mysql materi 13 where clause`).
- [x] **Fase 3: Penyusunan System Prompt Spesialis (`skills/mysql/prompt.md`)**
  - [x] Panduan persona *Senior Database Administrator & MySQL Technical Instructor*.
  - [x] Detail silabus 36 materi tematik dengan fokus materi tunggal per modul.
  - [x] Template baku modul praktikum 7 bagian.
  - [x] Aturan ketat skrip SQL idempotent dan dialek murni MySQL 8.x.
- [x] **Fase 4: Pembaruan Dokumentasi Repositori (`README.md`)**
  - [x] Memperbarui diagram pohon direktori di `README.md`.
  - [x] Menambahkan contoh pemanggilan `/mysql` pada daftar pemanggilan harian dan CLI.
  - [x] Mendaftarkan baris skill `mysql` pada tabel matriks peran.

---

## 5. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Siswa bingung jika database sampel berubah-ubah di setiap materi.
- **Mitigasi**: Di dalam `prompt.md` ditetapkan skema basis data studi kasus yang konsisten (misal: Toko Retail/Ecommerce `toko_db` atau Universitas `kampus_db`), sehingga materi dari DDL, DML, hingga Joins dan Indeks saling berkesinambungan secara logis.

---

> **COMPLETED**: Seluruh tahapan rencana implementasi telah dieksekusi dengan lengkap. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` telah aktif dan siap digunakan di `skills/mysql/`.
