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
- **Wajib Mengikuti Standar Modul Tutor 8 Bagian** di [template-tutor.md](../../rules/templates/template-tutor.md): sertakan prasyarat & jembatan konsep, rincikan konsep/perintah atau klausa T-SQL & argumennya sebelum praktik, sediakan 4 tahap/contoh bertingkat mikro disertai *state tracing* dan penanda jalur yang bersih (`Inti` vs `Pendalaman`), serta susun latihan berkelanjutan 4 level berbasis **3 Tema Tetap** (`TokoRitelDB`, `AkademikDB`, `LogistikAuditDB`) untuk jenjang SMK dan Mahasiswa.
- **Prinsip *Zero Untaught Syntax* & *Zero Meta-Prompt Leakage*:**
  - **Level 1 (Modul Fondasi, Instalasi, & Tooling):** Peserta belum belajar DDL/DML/T-SQL prosedural. Dilarang memaksakan `CREATE TABLE`, `INSERT`, `JOIN`, `TRY...CATCH`, atau DMV kompleks. Gunakan *mental model*, panduan terpandu GUI/Configuration Manager/SSMS, studi kasus skenario 3 tema, dan maksimal kueri verifikasi 1 baris (`SELECT @@VERSION;`, `SELECT @@SERVERNAME;`) yang dibedah token demi token.
  - **Level 2–7 (Modul Praktikum Sintaks & Arsitektur Lanjutan):** Wajib menyertakan skrip T-SQL utuh, idempotent (`IF OBJECT_ID...`, `CREATE OR ALTER...`), dan bebas placeholder komentar (`-- tulis query di sini`), dengan tetap mematuhi batas sintaks levelnya (DDL baru di Level 2, DML & `JOIN` di Level 3, SP/UDF/Trigger di Level 4, `TRY...CATCH` & Transaksi di Level 5, Index/DMV di Level 6, Security/Backup di Level 7).
  - **Gaya Bahasa Buku Ajar Bersih:** Tulis seluruh modul dari sudut pandang tutor kepada siswa/mahasiswa. Jangan membocorkan instruksi prompt (seperti `*(Wajib Terperinci)*`, `"Bedah setiap..."`, `"Mode A/B"`, `"Pola Kembar Contoh"`, atau catatan defensif fitur yang belum diajarkan), dan jangan membungkus penanda jalur dengan *backtick* di dalam heading (`##`).

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
1. **Bagian 1: Prasyarat, Jembatan Konsep, & Peta Alur** `[INTI]` (2 soal kilat prasyarat + *Why Before How* + diagram alur/arsitektur ASCII).
2. **Bagian 2: Kamus Fungsi, Klausa T-SQL, & Argumen Dasar *(Wajib Terperinci)*** `[INTI]` (Bedah fungsi, klausa, parameter wajib/opsional, nilai kembali, & contoh mikro 1–3 baris).
3. **Bagian 3: Prasyarat Lingkungan & Checkpoint 3 Tema Berkelanjutan** `[INTI]` (Versi SQL Server, tabel progresi & skrip idempotent `TokoRitelDB`, `AkademikDB`, `LogistikAuditDB`).
4. **Bagian 4: Contoh Praktik T-SQL Bertingkat — Tema 1 (Minimal 4 Contoh Mikro)** (Dasar Tunggal `[INTI]` → Variasi Parameter + *State Tracing* `[INTI]` → Kombinasi + *Step Trace* `[INTI]` → Terapan Produksi & *Edge Case* `[PENDALAMAN]`).
5. **Bagian 5: Verifikasi Output & Troubleshooting (*Common Pitfalls*)** `[INTI]` (Tabel output/statistik I/O + solusi error pemula & anti-pattern).
6. **Bagian 6: Latihan Soal** (Tabel acuan data visual konkret / spesifikasi arsitektur di awal + daftar tugas 1 s.d. 8–10 tanpa label pemecah, dengan instruksi langsung aksi teknis "Tulis perintah T-SQL untuk...", serta kenaikan kesulitan alami).
7. **Bagian 7: Panduan Evaluasi & Checklist Mandiri** (Target visual ASCII grid output kueri `SELECT` + indikator baris terdampak DML/DDL + checklist kesiapan teknis tanpa membocorkan kunci jawaban; kunci jawaban kueri lengkap dihimpun terpisah di `KUNCI_JAWABAN_LATIHAN_SOAL_SQL_SERVER.md`).
8. **Bagian 8: Ringkasan Fungsi & Refleksi Pemahaman** (Tabel ringkasan perintah + pertanyaan pemahaman konseptual & transfer lintas tema).

