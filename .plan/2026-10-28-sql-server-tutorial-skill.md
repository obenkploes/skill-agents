# IMPLEMENTATION PLAN: MODUL SKILL TUTORIAL MICROSOFT SQL SERVER (INSTALASI HINGGA ADVANCED)

- **Tanggal Pembuatan**: 2026-10-28
- **Kategori**: materi-tutor
- **Lokasi Berkas**: `.plan/2026-10-28-sql-server-tutorial-skill.md` (disimpan di root proyek yang sedang aktif dikerjakan)
- **Status**: Selesai Diimplementasikan (Completed)
- **Estimasi Kompleksitas**: Sedang

---

## 1. TUJUAN & RUANG LINGKUP
- **Problem Statement**: Diperlukan modul keahlian agen di folder `materi-tutor/sql-server` yang bertindak sebagai instruktur teknis dan database architect untuk menyusun modul tutorial Microsoft SQL Server secara komprehensif, terstruktur, dan siap praktik—mulai dari tahap instalasi dan konfigurasi lingkungan, pemrograman T-SQL, hingga administrasi performa dan disaster recovery tingkat lanjut.
- **Goals**:
  1. Menyusun struktur modul skill di `materi-tutor/sql-server/` yang terdiri dari:
     - `skill.json`: Metadata, triggers CLI (`/sql-server`, `/mssql`, `/t-sql`, `/sql-tutorial`), dan keterkaitan dengan aturan invariant.
     - `SKILL.md`: Spesifikasi discovery resmi Antigravity dengan YAML frontmatter.
     - `prompt.md`: System prompt spesialis instruktur SQL Server, silabus berjenjang 7 tingkat, dan standar penyusunan modul tutorial hands-on.
  2. Menyusun kurikulum berjenjang dari pemula hingga advanced (7 Level Penguasaan):
     - **Level 1: Instalasi & Tooling**: Pemilihan edisi (Developer/Express), setup instance, mixed mode authentication, port TCP/IP 1433, SSMS, Azure Data Studio, dan verifikasi konektivitas.
     - **Level 2: DDL & Arsitektur Database**: Manajemen database, filegroups (.mdf, .ndf, .ldf), tipe data T-SQL presisi, tabel, dan relasi integritas (PK, FK, Unique, Check, Default).
     - **Level 3: DML & Querying Fundamental**: CRUD operasi, filtering, sorting, pengelompokan data (`GROUP BY`, `HAVING`), dan teknik JOIN multi-tabel (`INNER`, `LEFT`, `RIGHT`, `FULL`, `CROSS`).
     - **Level 4: Logika Pemrograman T-SQL**: Stored Procedures (parameter input/OUTPUT), Functions (Scalar vs Inline Table-Valued), Views, Triggers (`AFTER` & `INSTEAD OF`, tabel virtual `inserted`/`deleted`).
     - **Level 5: Transaksi & Concurrency Control**: Prinsip ACID, `BEGIN TRAN`, `COMMIT`, `ROLLBACK`, `TRY...CATCH` & `THROW`, Transaction Isolation Levels, Deadlock handling.
     - **Level 6: Pengindeksan & Optimasi Performa**: B-Tree Clustered vs Non-Clustered index, Included Columns, membaca Execution Plan (Index Seek vs Scan, Key Lookup), `SET STATISTICS IO, TIME ON`, dan Dynamic Management Views (DMVs).
     - **Level 7: Administrasi, Keamanan, & Disaster Recovery**: Logins & Users, Security Roles, Backup strategies (Full, Differential, Log), Recovery Models (Simple vs Full), Point-in-Time Restore, dan SQL Server Agent Maintenance Jobs.
  3. Menjamin setiap output materi tutorial memiliki struktur hands-on yang aplikatif: *Tujuan $\rightarrow$ Konsep & Diagram Arsitektur $\rightarrow$ Langkah Praktik $\rightarrow$ Skrip T-SQL Lengkap $\rightarrow$ Output Ekspektasi $\rightarrow$ Troubleshooting $\rightarrow$ Lab Hands-on Tantangan*.
- **Out of Scope**:
  - Konfigurasi migrasi cloud multi-node cluster fisik riil (fokus pada penyusunan modul tutorial terstruktur, simulasi skrip T-SQL, dan panduan praktik mandiri).

---

## 2. KEBUTUHAN SISTEM & DEPENDENSI
- **Platform & Perangkat Lunak Target Tutorial**:
  - Microsoft SQL Server: 2019 / 2022 (Developer & Express Edition).
  - Client Tools: SQL Server Management Studio (SSMS) v19/v20, Azure Data Studio, VS Code (MSSQL Extension).
- **Format Skrip & Dokumentasi**:
  - T-SQL compliant (ANSI SQL dengan dialek T-SQL Microsoft).
  - Blok kode Markdown beranotasi `sql` dengan komentar penjelasan logika.
- **Dependensi Aturan Invariant**:
  - `rule/base_prompt.md`: Prinsip direct, zero-fluff, larangan pemotongan kode / placeholder malas, dan larangan hardcoded credentials.
  - `rule/project-workflow.md`: Protokol perencanaan dua-fase dan auto-open.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-28-sql-server-tutorial-skill.md   # [Baru] Dokumen perencanaan modul
└── materi-tutor/
    └── sql-server/                               # [Baru] Direktori modul skill
        ├── skill.json                            # [Baru] Metadata, triggers, dan referensi rule
        ├── SKILL.md                              # [Baru] Antigravity native progressive disclosure
        └── prompt.md                             # [Baru] System prompt instruktur teknis SQL Server & kurikulum
```

### Rincian Blueprint Modul:
1. **`skill.json`**:
   - `name`: `sql-server`
   - `category`: `materi-tutor`
   - `role`: `Senior Database Administrator & Technical Instructor (SQL Server Specialist)`
   - `triggers`: `commands` (`["/sql-server", "/mssql", "/t-sql", "/sql-tutorial"]`), `keywords` (`["sql server", "t-sql", "ssms", "stored procedure", "clustered index", "execution plan", "sql server backup", "database indexing"]`).
2. **`SKILL.md`**:
   - Format standar Antigravity untuk discovery otomatis skill.
3. **`prompt.md`**:
   - Persona teknis DBA instruktur.
   - Peta kurikulum 7 level dari instalasi hingga DBA mastery.
   - Standar format 7 bagian modul tutorial hands-on.
   - Skrip T-SQL template komprehensif untuk skenario pengujian performa dan manajemen database.

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Antigravity Indexing (`skill.json` & `SKILL.md`)**
  - [x] Pembuatan `materi-tutor/sql-server/skill.json` dengan triggers `/sql-server`, `/mssql`, `/t-sql`.
  - [x] Pembuatan `materi-tutor/sql-server/SKILL.md` dengan frontmatter YAML spesifikasi tutorial SQL Server.
- [x] **Fase 2: Perumusan System Prompt & Roadmap Kurikulum (`prompt.md`)**
  - [x] Pendefinisian persona *Senior DBA & Technical Instructor*.
  - [x] Penyusunan silabus lengkap 7 level (Instalasi $\rightarrow$ DDL/DML $\rightarrow$ T-SQL $\rightarrow$ Transaksi $\rightarrow$ Indexing/Tuning $\rightarrow$ Administrasi/DR).
  - [x] Standarisasi format modul tutorial hands-on 7 bagian.
  - [x] Penyertaan best practices T-SQL, anti-pattern yang harus dihindari (misal: cursor vs set-based logic, scalar function di WHERE clause, SELECT *).
- [x] **Fase 3: Validasi Modul & Registrasi Katalog**
  - [x] Pembaruan checklist di `.plan/2026-10-28-sql-server-tutorial-skill.md`.
  - [x] Registrasi modul baru di `README.md` pada tabel katalog skill kategori `materi-tutor`.

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Variasi sintaks antara SQL Server dan sistem RDBMS lain (seperti MySQL atau PostgreSQL).
- **Mitigasi**: Di dalam `prompt.md`, tekankan dialek khas Microsoft T-SQL (misal: penggunaan `TOP`, `IDENTITY(1,1)`, `CROSS APPLY`, variabel berawalan `@`, sintaks `TRY...CATCH`, serta fungsi tanggal `DATEDIFF`/`DATEADD`) agar output tidak tercampur dengan sintaks database lain.

---

> **STATUS IMPLEMENTASI**: Seluruh berkas modul (`skill.json`, `SKILL.md`, `prompt.md`) telah selesai diimplementasikan, diverifikasi, dan didaftarkan ke dalam katalog repositori. Modul siap digunakan secara aktif.

