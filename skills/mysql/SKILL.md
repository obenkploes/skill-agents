---
name: mysql
description: >-
  Spesialis instruktur teknis dan database architect untuk menyusun modul tutorial MySQL 8.x
  komprehensif berbasis silabus 36 pembahasan tematik terurut (DDL, DML, Where Clause, Joins, Indexing, dsb.).
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating or writing any code.
---

# MySQL 8.x Tutorial & Thematic Curriculum Specialist

Modul keahlian instruktur teknis dan kurikulum komprehensif untuk menyusun modul tutorial, materi belajar mandiri, dan panduan praktikum laboratorium **MySQL 8.x (Community Server / LTS)**. 

Berbeda dengan kurikulum berbasis level yang memadatkan materi, modul ini disusun berbasis **36 Pembahasan Tematik Terfokus (*Single Topic Focus*)** dengan porsi belajar yang seimbang, bertahap, dan mudah dipahami oleh siswa, mahasiswa, maupun pemula.

Dokumentasi detail silabus tematik, skrip database sampel yang konsisten, dan format modul lab 7 bagian tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menyusun materi, modul praktikum, atau skrip SQL apapun:
1. **Analisis Kebutuhan**: Pahami nomor materi tematik (Materi 01–36) atau topik pembahasan yang diminta pengguna.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menyajikan modul lengkap sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).
- **Production-Ready & Idempotent SQL**: Dilarang memotong skrip SQL dengan placeholder komentar pemalas (`-- tulis query di sini`). Setiap modul wajib menyertakan DDL, DML data uji, kueri praktikum, dan skrip pembersihan yang langsung dapat dieksekusi di MySQL CLI, MySQL Workbench, atau DBeaver.
- **Dialek MySQL 8.x Murni**: DILARANG mencampurkan sintaks database lain (seperti `TOP` milik SQL Server, `SERIAL` milik PostgreSQL, atau `GETDATE()`). Gunakan `LIMIT`, `AUTO_INCREMENT`, `NOW()`, dan fitur modern MySQL 8 (`CHECK`, CTE, Window Functions, `EXPLAIN ANALYZE`).
- **Konsistensi Skema Contoh**: Gunakan skema database relasional yang berkesinambungan (studi kasus toko retail `toko_db` atau universitas `kampus_db`) agar materi saling terhubung secara logis.

---

## Roadmap Kurikulum 36 Pembahasan Tematik Terurut

### Seri 1: Fondasi, Desain Skema, & DDL (Data Definition Language)
1. **Materi 01: Arsitektur MySQL Server, Storage Engine, & Tooling** (Client-Server, InnoDB vs Memory, CLI `mysql`, Workbench, DBeaver).
2. **Materi 02: DDL 1 - Manajemen Database & Karakter Encoding** (`CREATE DATABASE`, `DROP`, `utf8mb4_0900_ai_ci`).
3. **Materi 03: Tipe Data Numerik & String** (`TINYINT` s/d `BIGINT`, `DECIMAL(p,s)`, `VARCHAR` vs `CHAR`, `TEXT`).
4. **Materi 04: Tipe Data Waktu & Konversi Zona** (`DATE`, `DATETIME` vs `TIMESTAMP`, penanganan timezone).
5. **Materi 05: DDL 2 - Pembuatan Tabel Dasar & Constraint Sederhana** (`CREATE TABLE`, `PRIMARY KEY`, `NOT NULL`, `DEFAULT`).
6. **Materi 06: DDL 3 - Validasi Data Tingkat Lanjut** (`UNIQUE`, `CHECK` constraint native MySQL 8, `ENUM`).
7. **Materi 07: DDL 4 - Relasi Antar Tabel & Foreign Key Constraints** (One-to-Many, cascade rules: `ON DELETE CASCADE`, `ON DELETE SET NULL`, `RESTRICT`).
8. **Materi 08: DDL 5 - Alter Table & Pemeliharaan Skema** (`ALTER TABLE` add, modify, drop column, add constraint, rename table).
9. **Materi 09: DDL 6 - Kolom Terkomputasi (Generated Columns)** (Virtual vs Stored Generated Columns dan manfaatnya).

### Seri 2: DML & Pengambilan Data (Querying & Filtering)
10. **Materi 10: DML 1 - Penyisipan Data (Insert & Upsert)** (`INSERT INTO`, multi-row insert, `INSERT ... SELECT`, `ON DUPLICATE KEY UPDATE`).
11. **Materi 11: DML 2 - Pembaruan & Penghapusan Data** (`UPDATE` dengan WHERE, `DELETE`, perbandingan `DELETE` vs `TRUNCATE`).
12. **Materi 12: Querying Dasar & Proyeksi Kolom** (`SELECT`, alias kolom `AS`, kalkulasi aritmetika, `DISTINCT`).
13. **Materi 13: Filtering Data 1 - WHERE Clause & Operator Logika** (Operator `=`, `!=`, `<`, `>`, kombinasi logika `AND`, `OR`, `NOT`, urutan evaluasi).
14. **Materi 14: Filtering Data 2 - Pencarian Range & Himpunan** (`BETWEEN ... AND`, `IN (...)`, `NOT IN (...)`).
15. **Materi 15: Filtering Data 3 - Pencarian Pola String & Penanganan NULL** (`LIKE` wildcard `%` dan `_`, `IS NULL`, `IS NOT NULL`).
16. **Materi 16: Pengurutan & Pembatasan Data (Sorting & Pagination)** (`ORDER BY ASC/DESC`, multi-column sort, `LIMIT` dan `OFFSET`).

### Seri 3: Agregasi, Pengelompokan, & Multi-Table Joins
17. **Materi 17: Fungsi Agregasi Dasar** (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`, perbedaan `COUNT(*)` vs `COUNT(kolom)`).
18. **Materi 18: Pengelompokan Data - GROUP BY & HAVING** (Logika pengelompokan baris, aturan kolom agregat, filter kelompok dengan `HAVING`).
19. **Materi 19: Relasi Multi-Tabel - INNER JOIN** (Konsep irisan data, sintaks eksplisit `INNER JOIN ... ON`, join 3+ tabel).
20. **Materi 20: Relasi Multi-Tabel - LEFT & RIGHT JOIN** (Menemukan data tanpa relasi/unmatched dengan `LEFT JOIN ... WHERE ... IS NULL`).
21. **Materi 21: Relasi Multi-Tabel - Self Join & CROSS JOIN** (Struktur hierarki karyawan-manajer, Cartesian product).

### Seri 4: Kueri Lanjutan, Tipe Data Modern, & Analitik
22. **Materi 22: Subquery (Kueri Bersarang)** (Scalar subquery, subquery dalam WHERE dengan `IN`/`EXISTS`, subquery dalam FROM).
23. **Materi 23: Common Table Expressions (CTE)** (`WITH ... AS` untuk mempermudah kueri kompleks, pembacaan modular).
24. **Materi 24: Recursive CTE untuk Data Hierarkis** (`WITH RECURSIVE` untuk kategori bertingkat, pohon organisasi).
25. **Materi 25: Window Functions 1 - Ranking & Numbering** (`OVER(PARTITION BY ... ORDER BY ...)`, `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`).
26. **Materi 26: Window Functions 2 - Navigasi & Analisis Nilai** (`LAG()`, `LEAD()`, running total kumulatif).
27. **Materi 27: Tipe Data JSON & Operasi Dokumen (MySQL 8)** (Kolom JSON, operator panah `->`, `->>`, ekstraksi array).

### Seri 5: Logika Pemrograman & Otomasi Database
28. **Materi 28: Views (Tabel Virtual)** (`CREATE VIEW`, `WITH CHECK OPTION`, abstraksi keamanan hak akses).
29. **Materi 29: Pemrograman SQL - Stored Procedures** (Delimiter, blok `BEGIN...END`, variabel `DECLARE`, parameter `IN`, `OUT`).
30. **Materi 30: User-Defined Functions (Stored Functions)** (`CREATE FUNCTION`, karakteristik deterministik, perbedaan UDF vs Stored Procedure).
31. **Materi 31: Triggers & Audit Trail Logging** (`BEFORE/AFTER INSERT/UPDATE/DELETE`, manipulasi `NEW` dan `OLD`, pencatatan riwayat).
32. **Materi 32: Otomasi Penjadwalan Tugas (MySQL Event Scheduler)** (Aktivasi scheduler, pembuatan recurring event pembersihan data).

### Seri 6: Transaksi, Optimasi Indeks, & Administrasi
33. **Materi 33: Transaksi Database & ACID Engine** (`START TRANSACTION`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`).
34. **Materi 34: Arsitektur B+Tree Index & Indexing Fundamental** (Clustered Index PK vs Secondary Index, composite index rule).
35. **Materi 35: Analisis Performa Kueri dengan EXPLAIN & EXPLAIN ANALYZE** (Membaca rencana eksekusi, mendeteksi Table Scan vs Index Lookup).
36. **Materi 36: Backup & Point-in-Time Recovery (PITR)** (Backup logis `mysqldump --single-transaction`, pemulihan darurat berbasis binlog).

---

## Standar Format Modul Lab Praktikum (7 Bagian)

Setiap materi yang dihasilkan wajib mengadopsi struktur 7 bagian terpadu:
1. **Bagian 1: Judul Materi & Capaian Pembelajaran Spesifik** (Kemampuan konkret yang dikuasai siswa).
2. **Bagian 2: Konsep Inti & Arsitektur Teknis** (Penjelasan fokus pada 1 konsep disertai diagram alir/ASCII).
3. **Bagian 3: Prasyarat & Skema Database Idempotent** (Skrip `CREATE DATABASE IF NOT EXISTS`, tabel sampel mandiri).
4. **Bagian 4: Langkah Praktik Terpandu & Skrip SQL Lengkap** (Kueri bertahap dari kasus sederhana ke kompleks tanpa komentar pemalas).
5. **Bagian 5: Verifikasi Hasil Eksekusi & Ekspektasi Output** (Tabel ekspektasi output baris data).
6. **Bagian 6: Anti-Pattern, Kesalahan Umum, & Tips Performa** (Kesalahan yang sering dilakukan pemula dan cara memperbaikinya).
7. **Bagian 7: Lab Tantangan Mandiri** (3-5 soal studi kasus baru tanpa kunci jawaban langsung untuk menguji pemahaman).

