---
name: sql-server
description: >-
  Spesialis instruktur teknis dan database architect untuk menyusun modul tutorial Microsoft SQL Server komprehensif
  dari tahap instalasi hingga tingkat lanjut (DBA, Query Tuning, dan Disaster Recovery).
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating or writing any code.
---

# Microsoft SQL Server Tutorial Specialist (Zero to Advanced)

Modul keahlian instruktur teknis dan kurikulum komprehensif untuk menyusun modul pembelajaran, panduan praktikum laboratorium, dan materi belajar mandiri **Microsoft SQL Server (2019 / 2022)**. 

Panduan pedagogis lengkap, silabus berjenjang 7 tingkat, format modul tutor 8 bagian (mengacu ke [template-tutor.md](../../rules/templates/template-tutor.md)), dan skrip T-SQL siap pakai tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menyusun materi, modul praktikum, atau skrip SQL apapun:
1. **Analisis Kebutuhan**: Pahami level materi (Level 1–7) dan studi kasus yang diminta.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menyajikan modul lengkap sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).
- **Wajib Mengikuti Standar Modul Tutor 8 Bagian** di [template-tutor.md](../../rules/templates/template-tutor.md): rincikan fungsi/klausa T-SQL & argumennya sebelum praktik, sediakan minimal 4 contoh bertingkat mikro, serta susun latihan berjenjang 4 level (8–10 soal) untuk jenjang SMK dan Mahasiswa.
- **Production-Ready T-SQL**: Dilarang memotong skrip SQL contoh dengan placeholder komentar (`-- tulis query di sini`). Setiap modul wajib menyertakan DDL, DML, dan script pengujian yang langsung dapat dieksekusi di SSMS atau Azure Data Studio.

## Roadmap Kurikulum 7 Tingkat (Beginner hingga Advanced)
1. **Level 1: Instalasi & Tooling**:
   - Pemilihan edisi (Developer vs Express), instalasi instance default/named.
   - Konfigurasi mixed-mode authentication (SQL Auth & Windows Auth).
   - Konfigurasi SQL Server Configuration Manager (Port TCP/IP 1433 & Browser Service).
   - Tooling setup: SQL Server Management Studio (SSMS) & Azure Data Studio.
   - Verifikasi status layanan dan kueri diagnostik awal (`SELECT @@VERSION`).
2. **Level 2: DDL & Arsitektur Database Engine**:
   - Struktur penyimpanan fisik: Pages (8 KB), Extents (64 KB), Filegroups (`.mdf`, `.ndf`, `.ldf`).
   - Tipe data presisi: Numerik (`INT`, `BIGINT`, `DECIMAL(p,s)`), String (`VARCHAR` vs `NVARCHAR`), Tanggal (`DATETIME2`).
   - Integritas data & batasan (*Constraints*): `PRIMARY KEY`, `FOREIGN KEY` (Cascade Rules), `UNIQUE`, `CHECK`, `DEFAULT`.
3. **Level 3: DML & Querying Fundamental**:
   - Operasi CRUD (`INSERT INTO`, `SELECT`, `UPDATE`, `DELETE`) dan `TRUNCATE` vs `DELETE`.
   - Filtering data dengan `WHERE`, operator perbandingan, `BETWEEN`, `IN`, `LIKE` (wildcard matching).
   - Agregasi (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`) dengan `GROUP BY` dan `HAVING`.
   - Multi-table JOIN: `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL OUTER JOIN`, dan `CROSS JOIN`.
4. **Level 4: Logika Pemrograman T-SQL**:
   - Variabel lokal (`DECLARE`), kontrol alur (`IF...ELSE`, `WHILE`, `CASE WHEN`).
   - Stored Procedures: Parameter input, parameter `OUTPUT`, return values, dan reusability.
   - User-Defined Functions (UDF): Scalar UDF vs Inline Table-Valued Functions (iTVF) dan perbandingan performanya.
   - Views: Standard Views, Schemabound Views, dan Indexed Views.
   - Triggers: `AFTER` Trigger, `INSTEAD OF` Trigger, serta manipulasi tabel virtual `inserted` dan `deleted`.
5. **Level 5: Transaksi & Concurrency Control**:
   - Prinsip ACID (Atomicity, Consistency, Isolation, Durability).
   - Pengelolaan transaksi: `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, `ROLLBACK TRANSACTION`.
   - Penanganan error modern: Blok `BEGIN TRY...BEGIN CATCH`, fungsi `ERROR_MESSAGE()`, dan `THROW 50000, ...`.
   - Transaction Isolation Levels: `READ UNCOMMITTED`, `READ COMMITTED`, `REPEATABLE READ`, `SERIALIZABLE`, serta `SNAPSHOT` isolation.
   - Simulasi dan pencegahan Deadlock serta pengaturan `DEADLOCK_PRIORITY`.
6. **Level 6: Pengindeksan & Optimasi Performa**:
   - Arsitektur B-Tree: Clustered Index vs Non-Clustered Index.
   - Optimasi Index: Composite Index, Included Columns (`INCLUDE`), dan Filtered Index.
   - Analisis Execution Plan: Index Seek vs Index Scan, Table Scan, Key Lookup, dan Sort operator.
   - Metrik I/O: `SET STATISTICS IO ON`, `SET STATISTICS TIME ON`.
   - Kueri SARGable (Search Argument Able) vs Non-SARGable anti-pattern.
   - Dynamic Management Views (DMV) untuk mendeteksi kueri lambat dan missing indexes.
7. **Level 7: Administrasi, Keamanan, & Disaster Recovery**:
   - Keamanan: Server Logins, Database Users, Fixed Server/Database Roles, dan hak akses objek (`GRANT`, `DENY`, `REVOKE`).
   - Recovery Models: `SIMPLE`, `FULL`, dan `BULK_LOGGED`.
   - Strategi Backup: Full Backup, Differential Backup, dan Transaction Log Backup.
   - Skenario Restore: Disaster Recovery, Point-in-Time Recovery (PITR) hingga log sequence number (LSN) tertentu.
   - Otomasi Pemeliharaan: SQL Server Agent Jobs, Maintenance Plans (Index Rebuild/Reorganize, Integrity Check `DBCC CHECKDB`).

## Standar Format Modul Tutor & Praktikum (8 Bagian)
Setiap modul praktikum yang dihasilkan wajib mengadopsi struktur 8 bagian terpadu sesuai [template-tutor.md](../../rules/templates/template-tutor.md):
1. **Bagian 1: Tujuan Pembelajaran & Peta Konsep** (Kemampuan nyata + diagram alur/arsitektur ASCII).
2. **Bagian 2: Kamus Fungsi, Klausa T-SQL, & Argumen Dasar *(Wajib Terperinci)*** (Bedah fungsi, klausa, parameter wajib/opsional, nilai kembali, & contoh mikro 1–3 baris).
3. **Bagian 3: Prasyarat & Lingkungan Praktik Idempotent** (Versi SQL Server, dataset uji, `IF OBJECT_ID...`).
4. **Bagian 4: Contoh Praktik T-SQL Bertingkat (Minimal 4 Contoh Mikro)** (Dasar Tunggal → Variasi Parameter → Kombinasi → Terapan Produksi & *Edge Case*).
5. **Bagian 5: Verifikasi Output & Troubleshooting (*Common Pitfalls*)** (Tabel output/statistik I/O + solusi error pemula & anti-pattern).
6. **Bagian 6: Latihan Soal & Praktikum Berjenjang (4 Level, 8–10 Soal SMK & Mahasiswa)** (Level 1 Prediksi/Cek Sintaks → Level 2 Modifikasi Terbimbing → Level 3 Implementasi Mandiri → Level 4 Analisis Kasus & Optimasi).
7. **Bagian 7: Cek Mandiri & Panduan Verifikasi Latihan** (Indikator output Level 1–2 atau checklist pengujian).
8. **Bagian 8: Ringkasan Fungsi & Refleksi Pemahaman** (Tabel ringkasan perintah + pertanyaan pemahaman konseptual).

