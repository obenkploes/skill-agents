# PANDUAN PENGEMBANGAN SKILL AGENT MODULAR

Panduan arsitektur dan standarisasi skill agent modular untuk integrasi VS Code dan Antigravity CLI. Desain ini memisahkan peran (*Prompt Engineering, Software Engineering, Tutor Kelas, Database Analyst, System Analyst*) ke dalam modul terisolasi dengan basis aturan global yang konsisten.

---

## DAFTAR ISI
1. [Struktur Folder Proyek](#1-struktur-folder-proyek)
2. [Arsitektur Tiga Lapis (Three-Layer Architecture)](#2-arsitektur-tiga-lapis-three-layer-architecture)
3. [Protokol Alur Kerja & Implementation Plan](#3-protokol-alur-kerja--implementation-plan)
4. [Spesifikasi & Anatomi Modul Skill](#4-spesifikasi--anatomi-modul-skill)
5. [Aturan Universal & Batasan Kritis (Base Rules)](#5-aturan-universal--batasan-kritis-base-rules)
6. [Panduan Pembuatan Skill Baru (Step-by-Step)](#6-panduan-pembuatan-skill-baru-step-by-step)
7. [Integrasi dengan Antigravity CLI & VS Code](#7-integrasi-dengan-antigravity-cli--vs-code)
8. [Matriks Peran & Katalog Modul](#8-matriks-peran--katalog-modul)
9. [Checklist Standar Kualitas (Quality Assurance)](#9-checklist-standar-kualitas-quality-assurance)

---

## 1. STRUKTUR FOLDER PROYEK

Struktur direktori dirancang dengan prinsip pemisahan tanggung jawab (*Separation of Concerns*). Seluruh aturan dasar disimpan terpusat, sementara modul peran dipecah berdasarkan domain spesifik:

```text
skills-agent/
├── README.md                          # Panduan utama arsitektur dan penggunaan sistem
├── .plan/                             # Arsip dokumen perencanaan implementasi fitur/proyek
│   └── 2026-10-27-contoh-fitur.md     # Contoh berkas rencana eksekusi (mandatory planning)
├── rule/                              # Invariant rules (aturan global wajib dipatuhi semua skill)
│   ├── base_prompt.md                 # Prinsip komunikasi, batas teknis, & format output universal
│   ├── project-workflow.md            # Protokol perencanaan dua-fase & gate persetujuan pengguna
│   ├── template-plan.md               # Format baku berkas perencanaan implementasi
│   └── template-materi-ajar.md        # Format baku modul ajar, praktikum, & tugas kontekstual santri
├── backend/                           # Modul skill domain backend engineering
│   └── laravel-api/
│       ├── skill.json                 # Metadata, parameter, & konfigurasi trigger CLI
│       └── prompt.md                  # System prompt spesifik modul backend Laravel
├── frontend/                          # Modul skill domain frontend engineering
│   ├── react-tailwind/
│   │   ├── skill.json                 # Metadata & konfigurasi trigger frontend
│   │   └── prompt.md                  # System prompt spesifik modul React & Tailwind CSS
│   ├── tailmind/                      # Modul skill TailAdmin / TailMind dashboard
│   │   ├── skill.json                 # Metadata, trigger CLI (/tailmind, /tailadmin)
│   │   └── prompt.md                  # System prompt spesialisasi TailAdmin UI & chart
│   └── mobile/                        # Modul frontend mobile
│       ├── task-management-ui/        # Dual-Engine UI Kit (Flutter & React / React Native)
│       │   ├── skill.json             # Metadata & triggers (/task-ui, /flutter-task-ui, /react-task-ui)
│       │   ├── SKILL.md               # Antigravity native progressive disclosure
│       │   └── prompt.md              # Universal tokens & Flutter/React widget blueprints
│       └── coffee-shop-ui/            # Coffee Shop UI Kit Nam Design (Font Sora & Terracotta #C67C4E)
│           ├── skill.json             # Metadata & triggers (/coffee-ui, /coffee-shop)
│           ├── SKILL.md               # Antigravity native progressive disclosure
│           └── prompt.md              # 5 Layar alur kopi (Onboarding, Home, Detail, Order, Delivery)
├── materi-ajar/                       # Modul bahan ajar mandiri siswa (LaTeX & scaffolding)
│   └── matematika-smp/                # Modul silabus Matematika SMP Kelas 7, 8, 9 (72 Pertemuan)
│       ├── skill.json                 # Metadata & trigger CLI (/matematika-smp, /math-smp)
│       ├── SKILL.md                   # Antigravity native progressive disclosure
│       └── prompt.md                  # Roadmap 72 pertemuan & format 9 bagian materi siswa
└── materi-tutor/                      # Modul materi pengajaran, praktikum, & bimbingan belajar
    ├── web-programming-lab/
    │   ├── skill.json                 # Metadata & konfigurasi modul tutor
    │   └── prompt.md                  # System prompt spesifik metode pedagogis dan scaffolding
    └── sql-server/                    # Modul tutorial Microsoft SQL Server (Zero to Advanced)
        ├── skill.json                 # Metadata & triggers (/sql-server, /mssql, /t-sql)
        ├── SKILL.md                   # Antigravity native progressive disclosure
        └── prompt.md                  # Kurikulum 7 level, format lab 7 bagian & T-SQL blueprints
```

### Rincian Fungsi Direktori Inti:
- **`rule/`**: Fondasi tak-tergantikan (*invariants*). Aturan dalam direktori ini otomatis diinjeksi atau dirujuk oleh setiap modul skill. Tidak boleh diabaikan atau ditimpa oleh konfigurasi lokal.
- **`.plan/`**: Tempat seluruh berkas perencanaan dieksekusi sebelum kode implementasi ditulis pada root proyek yang sedang aktif dikerjakan. Menggunakan format penamaan standar `.plan/YYYY-MM-DD-<nama-fitur>.md`.
- **`<domain-category>/<skill-name>/`**: Folder mandiri (*self-contained*) untuk masing-masing keahlian teknis atau peran agen.

---

## 2. ARSITEKTUR TIGA LAPIS (THREE-LAYER ARCHITECTURE)

Sistem ini mengadopsi model berlapis untuk memastikan konsistensi output dan fleksibilitas kemampuan agen:

```
┌────────────────────────────────────────────────────────┐
│  LAYER 1: UNIVERSAL BASE DIRECTIVES (rule/base_prompt) │
│  - Zero Fluff & Root-Cause Driven                      │
│  - Production-Ready Standards & Security Constraints   │
└──────────────────────────┬─────────────────────────────┘
                           │ diwariskan ke
┌──────────────────────────▼─────────────────────────────┐
│  LAYER 2: PROTOKOL WORKFLOW (rule/project-workflow)    │
│  - Pre-Execution Planning (Fase Perencanaan)           │
│  - Mandatory Approval Gate (Konfirmasi Eksplisit)      │
└──────────────────────────┬─────────────────────────────┘
                           │ membungkus
┌──────────────────────────▼─────────────────────────────┐
│  LAYER 3: DOMAIN-SPECIFIC SKILLS (backend, frontend, …)│
│  - skill.json (Metadata, triggers, konfigurasi)        │
│  - prompt.md (Instruksi spesialisasi domain/peran)     │
└────────────────────────────────────────────────────────┘
```

1. **Layer 1 (Universal Base Directives)**: Mengatur bagaimana agen berpikir, berkomunikasi, dan menangani batas keamanan tanpa peduli bahasa pemrograman atau framework yang sedang digunakan.
2. **Layer 2 (Workflow & Planning Governance)**: Menjamin agen tidak melakukan perubahan destruktif atau menulis kode secara impulsif tanpa perencanaan terstruktur.
3. **Layer 3 (Domain-Specific Context)**: Memberikan keahlian mendalam pada stack tertentu (misal: RESTful API design di Laravel, arsitektur state management di React, atau scaffolding pedagogis untuk asisten lab).

---

## 3. PROTOKOL ALUR KERJA & IMPLEMENTATION PLAN

Setiap pekerjaan teknis berskala baru atau penambahan fitur wajib mengikuti protokol dua fase sesuai ketentuan di [`rule/project-workflow.md`](rule/project-workflow.md):

### Fase 1: Perencanaan Wajib (Pre-Execution Planning)
Sebelum menulis, mengedit, atau mengeksekusi kode apa pun, agen wajib menyusun berkas rencana kerja di folder `.plan/` pada root proyek yang sedang aktif dikerjakan dengan format:
`.plan/YYYY-MM-DD-<nama-fitur-atau-proyek>.md`

Dokumen ini wajib mengacu pada [`rule/template-plan.md`](rule/template-plan.md) dan mencakup 5 komponen mutlak:
1. **Tujuan & Ruang Lingkup**: Masalah yang diselesaikan (*problem statement*), target konkret (*goals*), dan batasan di luar cakupan (*out of scope*).
2. **Kebutuhan Sistem & Dependensi**: Paket pihak ketiga yang dibutuhkan, variabel lingkungan (`.env`), dan perubahan skema database.
3. **Rancangan Teknis / Arsitektur**: Struktur berkas yang dibuat/diubah, kontrak endpoint/antarmuka (method, payload, response).
4. **Tahapan Eksekusi Bertahap (Checklist)**:
   - *Fase 1*: Fondasi & Konfigurasi Data (Migrasi, seeder, env).
   - *Fase 2*: Logika Bisnis & Core Engine (Service layer, validasi request).
   - *Fase 3*: Integrasi & Antarmuka (Controller, route, komponen UI).
   - *Fase 4*: Verifikasi & Pengujian Kinerja (Test cases, audit N+1 query).
5. **Analisis Risiko & Mitigasi**: Antisipasi potensi breaking changes, overhead performa, dan strategi penanganannya.

### Fase 2: Otomatis Buka Berkas & Gate Persetujuan (Auto-Open & Awaiting Approval)
Setelah berkas rencana tersimpan di `.plan/` proyek target, agen **WAJIB membuka berkas rencana tersebut secara otomatis** di editor kerja (atau menyajikan tautan aktif) dan **DILARANG KERAS** langsung mengeksekusi kode implementasi. Agen wajib berhenti dan memberikan opsi peninjauan/eksekusi terstandar:

> *"Dokumen rencana telah disimpan dan dibuka di `[.plan/<nama-file>.md](file:///<path-ke-file>)`. Harap tinjau rancangan tersebut. Anda dapat memberikan masukan/revisi, atau konfirmasi dengan **'Lanjutkan' / 'Eksekusi'** untuk memulai implementasi kode."*

Eksekusi kode implementasi hanya boleh dijalankan setelah pengguna memberikan konfirmasi eksplisit (*"Lanjutkan"*, *"Eksekusi"*, *"Setuju"*, *"Approved"*, atau arahan revisi).

---

## 4. SPESIFIKASI & ANATOMI MODUL SKILL

Setiap modul skill disimpan dalam direktorinya masing-masing dan wajib memiliki tepat 2 berkas utama:

### 1. `skill.json` (Konfigurasi & Metadata)
Berkas JSON ini berfungsi sebagai identitas dan konfigurasi pemicu (*trigger*) saat agen dijalankan via CLI maupun ekstensi IDE.

#### Struktur Schema `skill.json`:
```json
{
  "name": "nama-skill-kebab-case",
  "version": "1.0.0",
  "category": "backend | frontend | materi-tutor | database | system-analyst",
  "displayName": "Nama Representatif Skill",
  "description": "Deskripsi singkat kapabilitas dan cakupan modul.",
  "role": "Role teknis agen saat modul aktif",
  "triggers": {
    "commands": ["/laravel", "/api"],
    "keywords": ["laravel", "eloquent", "artisan", "api-resource"]
  },
  "rules": [
    "../../rule/base_prompt.md",
    "../../rule/project-workflow.md"
  ],
  "dependencies": {
    "php": "^8.2",
    "laravel/framework": "^11.0"
  },
  "author": "Nama / Tim Pengembang"
}
```

### 2. `prompt.md` (System Prompt Spesifik Modul)
Berkas Markdown yang memuat instruksi spesialisasi domain. Berkas ini harus memuat bagian:
- **Role & Persona Identity**: Menjelaskan keahlian spesifik agen (contoh: Senior Backend Engineer spesialis Clean Architecture).
- **Tech Stack Standards**: Standar konvensi kode (PSR-12 untuk PHP, ESLint/Prettier untuk JavaScript, camelCase vs snake_case).
- **Core Engineering Patterns**: Pola arsitektur yang diutamakan (misal: Service-Repository Pattern, Action Classes, Custom Hooks, Redux Toolkit).
- **Negative Constraints Modul**: Larangan spesifik domain (contoh: dilarang menulis raw query SQL tanpa parameter binding, dilarang menaruh logic bisnis di dalam React component view).
- **Template / Format Respons Khusus**: Format cuplikan kode lengkap beserta path berkas eksplisit di baris atas blok kode.

---

## 5. ATURAN UNIVERSAL & BATASAN KRITIS (BASE RULES)

Seluruh skill wajib beroperasi di bawah batasan yang ditentukan dalam [`rule/base_prompt.md`](rule/base_prompt.md):

| Prinsip | Ketentuan Utama |
| :--- | :--- |
| **Direct & Zero Fluff** | Mulai respons langsung pada solusi teknis di kalimat pertama. Dilarang menggunakan basa-basi ("Tentu!", "Halo!", "Berikut adalah kodenya...") dan penutup klise ("Semoga membantu!"). |
| **Root-Cause Driven** | Selalu selesaikan akar permasalahan, bukan sekadar menambal gejala (*symptom*). Bila terjadi ambiguitas, pilih asumsi teknis teraman dan jelaskan batasan secara singkat. |
| **Production-Ready** | Seluruh kode harus lengkap dan fungsional. Dilarang memotong logika dengan komentar pemalas seperti `// implement logic here` atau `// sesuaikan sendiri`. |
| **Security & Secrets** | **DILARANG** menuliskan API key, password, token, atau kredensial langsung di kode (*hardcoded*). Selalu gunakan placeholder file konfigurasi atau `.env`. |
| **Dependency Integrity** | **DILARANG** mengasumsikan library terpasang secara ajaib. Sertakan selalu perintah instalasi (misal: `composer require ...` atau `npm install ...`). |
| **Explicit Pathing** | Cantumkan path file lengkap di atas setiap blok kode (contoh: `// app/Http/Controllers/Api/ProductController.php`). |

---

## 6. PANDUAN PEMBUATAN SKILL BARU (STEP-BY-STEP)

Ikuti langkah-langkah berikut untuk menambahkan modul keahlian baru ke dalam repositori:

### Langkah 1: Tentukan Direktori Domain
Pilih kategori yang sesuai atau buat kategori baru jika belum tersedia:
- `backend/` untuk framework dan service sisi server (Laravel, Go Fiber, Express, NestJS).
- `frontend/` untuk UI dan client-side libraries (React, Vue, Tailwind CSS, Next.js).
- `materi-tutor/` untuk modul praktikum, kurikulum asistensi lab, dan tutorial belajar.
- `database/` untuk optimasi skema, query tuning, dan manajemen index.
- `system-analyst/` untuk perancangan SRS, sequence diagram, dan user stories.

Buat folder baru dengan format kebab-case, contoh:
```bash
mkdir -p backend/go-fiber
```

### Langkah 2: Buat Berkas `skill.json`
Definisikan metadata modul:
```json
{
  "name": "go-fiber-api",
  "version": "1.0.0",
  "category": "backend",
  "displayName": "Go Fiber REST API",
  "description": "Spesialis pengembangan performa tinggi RESTful microservices menggunakan Go dan Fiber framework.",
  "role": "Senior Go Systems Engineer",
  "triggers": {
    "commands": ["/gofiber", "/golang"],
    "keywords": ["golang", "fiber", "gorm", "sqlx"]
  },
  "rules": [
    "../../rule/base_prompt.md",
    "../../rule/project-workflow.md"
  ]
}
```

### Langkah 3: Susun Berkas `prompt.md`
Tuliskan system prompt modul dengan struktur standar:
```markdown
# GO FIBER API SPECIALIST SYSTEM PROMPT

## 1. IDENTITY & EXPERTISE
Anda bertindak sebagai Senior Go Engineer dengan spesialisasi arsitektur Clean Architecture menggunakan framework Fiber.

## 2. CODING CONVENTIONS
- Ikuti standar resmi Effective Go.
- Struktur folder: `cmd/api`, `internal/delivery/http`, `internal/usecase`, `internal/repository`.
- Tangani setiap error secara eksplisit (`if err != nil`). Dilarang mengabaikan error dengan `_`.

## 3. STRICT DOMAIN CONSTRAINTS
- Wajib menggunakan context timeout pada setiap interaksi database dan HTTP outbound.
- Dilarang menyimpan pointer ke struct yang memiliki mutable state tanpa sinkronisasi mutex.
```

### Langkah 4: Validasi & Uji Modul
1. Pastikan berkas `rule/base_prompt.md` dirujuk dengan benar.
2. Uji pemicuan prompt menggunakan pemicu perintah (`commands`) dan kata kunci (`keywords`).
3. Pastikan alur kerja pembuatan plan tetap terpanggil saat menerima instruksi fitur baru.

---

## 7. INTEGRASI DENGAN ANTIGRAVITY CLI & VS CODE

Arsitektur ini dirancang agar dapat diintegrasikan dengan mulus ke dalam lingkungan pengembang harian lintas proyek melalui variabel lingkungan (*Environment Variables*).

### A. Konfigurasi Environment Variables (Global)
Path repositori telah didaftarkan pada variabel lingkungan pengguna Windows:
- `SKILLS_AGENT_PATH` = `D:\Project\exercise\skills-agent`
- `ANTIGRAVITY_SKILLS_PATH` = `D:\Project\exercise\skills-agent`

### B. Penggunaan dengan Antigravity CLI (`agy`)
Antigravity CLI dapat memanggil modul skill dari direktori mana pun dengan memanfaatkan variabel lingkungan:

```bash
# PowerShell
agy run --skill "$env:SKILLS_AGENT_PATH\frontend\tailmind" "Buatkan dashboard e-commerce dengan stat card dan gauge target"

# Windows Command Prompt (CMD)
agy run --skill "%SKILLS_AGENT_PATH%\frontend\tailmind" "Buatkan dashboard e-commerce dengan stat card dan gauge target"
```

**Mekanisme Context Resolution:**
Ketika sebuah skill dijalankan, urutan perakitan konteks sistem adalah:
$$\text{Base Prompt (`rule/base_prompt.md`)} \longrightarrow \text{Workflow Protocol (`rule/project-workflow.md`)} \longrightarrow \text{Domain Prompt (`prompt.md`)} \longrightarrow \text{User Task}$$

### C. Integrasi dengan Antigravity di VS Code
Agar Antigravity di VS Code mengenali modul skill di **proyek mana pun**:
1. Buat berkas `.agents/skills.json` di root proyek target untuk menautkan repositori skill:
   ```json
   {
     "entries": [
       { "path": "D:/Project/exercise/skills-agent/frontend" }
     ]
   }
   ```
2. Atau jalankan perintah otomatis satu baris di terminal proyek target (PowerShell):
   ```powershell
   New-Item -ItemType Directory -Force .agents; Set-Content -Path .agents/skills.json -Value '{"entries":[{"path":"D:/Project/exercise/skills-agent/frontend"}]}'
   ```
3. Antigravity IDE / VS Code akan secara otomatis membaca berkas `SKILL.md` (progressive disclosure) dan memuat keahlian *TailAdmin / TailMind Specialist* saat relevan dengan percakapan aktif.
4. Anda juga dapat menyematkan instruksi secara langsung pada prompt percakapan VS Code:
   `@file:D:/Project/exercise/skills-agent/frontend/tailmind/prompt.md`

---

## 8. MATRIKS PERAN & KATALOG MODUL

Tabel status dan pemetaan modul skill yang direncanakan dan tersedia di repositori:

| Kategori | Nama Modul | Peran Representatif | Status | Cakupan Utama |
| :--- | :--- | :--- | :---: | :--- |
| **Rule** | `base_prompt.md` | Core Supervisor | **Aktif** | Standar komunikasi direct, batas keamanan, format markdown |
| **Rule** | `project-workflow.md` | Process Controller | **Aktif** | Mandatory pre-execution planning, approval gate |
| **Rule** | `template-materi-ajar.md` | Curriculum Author | **Aktif** | Standar modul materi ajar siswa, scaffolding contoh soal, latihan, & PR santri |
| **Backend** | `laravel-api` | Senior Laravel Architect | *Tersedia* | Laravel 11, API Resources, Eloquent optimization, Service layer |
| **Frontend** | `react-tailwind` | Senior Frontend Engineer | *Tersedia* | React 19, TypeScript, Tailwind CSS, State management, Accessibility |
| **Frontend** | `tailmind` | TailAdmin System Specialist | **Aktif** | TailAdmin Dashboard, KPI Stat Cards, Gauge Chart, Sales Bar, Period Filter Area |
| **Frontend/Mobile** | `task-management-ui` | Mobile UI/UX Architect | **Aktif** | Dual-Engine (Flutter & React): Task Dashboard, Gradient Slider, Detail Sheet, Create Form |
| **Frontend/Mobile** | `coffee-shop-ui` | Coffee Shop UI/UX Specialist | **Aktif** | Nam Design Styleguide (Sora, #C67C4E), 5 Layar Pemesanan Kopi, Dual-Engine (Flutter & React) |
| **Materi Ajar**| `matematika-smp` | Mathematics Curriculum Author | **Aktif** | Silabus 72 Pertemuan (Kelas 7-9), 9 Bagian Materi Siswa, LaTeX KaTeX, Scaffolding |
| **Materi Tutor**| `web-programming-lab` | Lab Instructor & Mentor | *Tersedia* | Pedagogical scaffolding, analogi logika, tugas mandiri terstruktur |
| **Materi Tutor**| `sql-server` | Senior DBA & Technical Instructor | **Aktif** | Kurikulum 7 Level (Instalasi $\rightarrow$ Advanced), 7 Format Lab, T-SQL Blueprints, Disaster Recovery |
| **Database** | `postgres-analyst` | Database Administrator | *Rencana* | Desain skema relasional, optimasi index (EXPLAIN ANALYZE), partisi tabel |
| **System** | `architecture-designer` | Enterprise System Analyst | *Rencana* | Sequence diagrams, arsitektur event-driven, perancangan kontrak API |

---

## 9. CHECKLIST STANDAR KUALITAS (QUALITY ASSURANCE)

Sebelum mempublikasikan atau menggunakan modul skill baru, verifikasi daftar periksa berikut:

- [ ] Folder modul diletakkan di bawah direktori kategori domain yang tepat.
- [ ] Berkas `skill.json` memiliki sintaks JSON valid dan mencantumkan dependensi rule universal.
- [ ] Berkas `prompt.md` tidak mengandung basa-basi pembuka/penutup dan langsung mendefinisikan standar teknis.
- [ ] Aturan pencegahan kebocoran kredensial (`.env`) tercantum secara jelas.
- [ ] Pemicu kata kunci dan perintah di `skill.json` unik dan tidak bentrok dengan modul lain.
- [ ] Modul mematuhi protokol perencanaan dua fase sebelum menulis kode implementasi.
- [ ] Contoh kode yang disediakan menyertakan anotasi path file di baris paling atas.

---

*Panduan ini dipelihara secara terpusat untuk memastikan konsistensi, keandalan, dan kesiapan produksi seluruh interaksi agen pintar.*
