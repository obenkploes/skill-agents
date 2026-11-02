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
├── plugin.json                        # Manifest resmi Antigravity Global Plugin
├── .plan/                             # Arsip dokumen perencanaan implementasi fitur/proyek
│   └── 2026-10-27-contoh-fitur.md     # Contoh berkas rencana eksekusi (mandatory planning)
├── rules/                             # Global Discovery Rules resmi Antigravity
│   ├── AGENTS.md                      # Invariant rules (Base prompt + Mandatory Two-Phase Planning)
│   └── templates/                     # Berkas template resmi rujukan
│       ├── template-plan.md           # Format baku berkas perencanaan implementasi
│       └── template-materi-ajar.md    # Format baku modul ajar, praktikum, & tugas siswa
└── skills/                            # Discovery root resmi Antigravity untuk semua skill
    ├── task-management-ui/            # Dual-Engine UI Kit (Flutter & React / React Native)
    ├── coffee-shop-ui/                # Coffee Shop UI Kit Nam Design (Font Sora & Terracotta #C67C4E)
    ├── food-delivery-ui/              # Food Delivery & Chef Marketplace UI Kit (Brand Orange #FF7622)
    ├── sql-server/                    # Modul tutorial Microsoft SQL Server (Zero to Advanced)
    ├── mysql/                         # Modul tutorial MySQL 8.x (36 Materi Tematik Terurut)
    ├── matematika-smp/                # Modul silabus Matematika SMP Kelas 7, 8, 9 (72 Pertemuan)
    ├── matematika-sma/                # Modul silabus Matematika SMA Kelas 10, 11, 12 IPA & Pesantren (72 Pertemuan)
    ├── tailmind/                      # Modul skill TailAdmin / TailMind dashboard
    ├── zenith-ui/                     # Modul skill Zenith UI Multi-Engine (Native CSS, Tailwind, Bootstrap)
    ├── viral-news-analyzer/           # Modul analisis intelijen berita viral & sentimen medsos
    └── fact-verifier/                 # Modul uji kebenaran fakta & ekstraksi teks berita asli
```

### Rincian Fungsi Direktori Inti:
- **`plugin.json`**: Manifest resmi penanda bahwa repositori ini adalah paket Antigravity Global Plugin.
- **`rules/`**: Fondasi tak-tergantikan (*invariants*). Berkas `rules/AGENTS.md` otomatis diinjeksi ke setiap percakapan oleh Antigravity engine secara global. Folder `rules/templates/` memuat format baku perencanaan dan bahan ajar.
- **`.plan/`**: Tempat seluruh berkas perencanaan dieksekusi sebelum kode implementasi ditulis pada root proyek yang sedang aktif dikerjakan. Menggunakan format penamaan standar `.plan/YYYY-MM-DD-<nama-fitur>.md`.
- **`skills/<skill-name>/`**: Folder mandiri (*self-contained*) untuk masing-masing keahlian teknis atau peran agen yang langsung dideteksi oleh Antigravity.

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

## 7. PANDUAN PENGGUNAAN LINTAS KOMPUTER & LINUX / MACOS

Repositori ini telah dikemas sebagai **Antigravity Global Plugin (`plugin.json` + `rules/AGENTS.md` + `skills/`)**. Anda dapat menggunakannya di komputer lain atau di sistem operasi Linux/macOS tanpa perlu menyalin aturan (*rules*) ke setiap proyek baru.

---

### A. Penggunaan di Komputer Lain (Windows)

1. **Clone Repositori**:
   Simpan repositori pada direktori pilihan Anda (misalnya di drive `C:` atau `D:`):
   ```powershell
   git clone <URL_REPOSITORI_ANDA> "D:\Project\exercise\skills-agent"
   ```

2. **Tautkan ke Antigravity Global Plugins (Sekali Setup)**:
   Buka terminal PowerShell dan jalankan perintah pembuatan NTFS Junction:
   ```powershell
   # Buat folder plugins jika belum ada
   New-Item -ItemType Directory -Force "$env:USERPROFILE\.gemini\config\plugins"

   # Hubungkan repositori langsung ke direktori plugin Antigravity
   cmd /c mklink /J "$env:USERPROFILE\.gemini\config\plugins\skills-agent" "D:\Project\exercise\skills-agent"
   ```

3. **(Opsional) Daftarkan Environment Variable**:
   ```powershell
   [Environment]::SetEnvironmentVariable("SKILLS_AGENT_PATH", "D:\Project\exercise\skills-agent", "User")
   ```

---

### B. Penggunaan di Linux (Ubuntu / Debian / Fedora / Arch) & macOS

Di sistem operasi Linux dan macOS, Antigravity menyimpan konfigurasi global di `~/.gemini/config/`.

1. **Clone Repositori**:
   ```bash
   git clone <URL_REPOSITORI_ANDA> ~/skills-agent
   ```

2. **Tautkan Menggunakan Symbolic Link (`ln -s`)**:
   Buat symbolic link dari folder repositori ke folder plugins Antigravity:
   ```bash
   # Buat direktori plugins jika belum ada
   mkdir -p ~/.gemini/config/plugins

   # Buat symbolic link
   ln -s ~/skills-agent ~/.gemini/config/plugins/skills-agent
   ```

3. **Konfigurasi Auto-Open di Linux / macOS**:
   Pada Linux/macOS, perintah pembuka dokumen `.plan/` disesuaikan:
   - **Linux**: Menggunakan perintah `xdg-open .plan/<nama-file>.md` atau `code .plan/<nama-file>.md`.
   - **macOS**: Menggunakan perintah `open .plan/<nama-file>.md` atau `code .plan/<nama-file>.md`.

4. **(Opsional) Export Environment Variable**:
   Tambahkan ke berkas `~/.bashrc` atau `~/.zshrc`:
   ```bash
   export SKILLS_AGENT_PATH="$HOME/skills-agent"
   export ANTIGRAVITY_SKILLS_PATH="$HOME/skills-agent"
   ```
   Lalu muat ulang terminal:
   ```bash
   source ~/.bashrc   # atau source ~/.zshrc
   ```

---

### C. Metode Alternatif Tanpa Symlink/Junction (`plugins.json`)

Jika sistem operasi atau hak akses membatasi pembuatan link simbolik/junction, Anda dapat mendaftarkan path repositori menggunakan berkas konfigurasi resmi Antigravity di `~/.gemini/config/plugins.json`:

- **Windows** (`C:\Users\<User>\.gemini\config\plugins.json`):
  ```json
  {
    "entries": [
      { "path": "D:/Project/exercise/skills-agent" }
    ]
  }
  ```
- **Linux / macOS** (`~/.gemini/config/plugins.json`):
  ```json
  {
    "entries": [
      { "path": "~/skills-agent" }
    ]
  }
  ```

---

### D. Cara Pemanggilan Skill Sehari-Hari Lintas Proyek

Setelah ditautkan via salah satu metode di atas:
1. **Di Antigravity Chat / IDE (VS Code)**:
   Buka proyek coding Anda yang mana saja (misal: proyek baru Flutter, Laravel, atau React di direktori terpisah). Panggil trigger skill langsung di chat:
   - `/coffee-ui` atau `/food-ui` $\rightarrow$ Merancang antarmuka mobile.
   - `/sql-server` $\rightarrow$ Menyiapkan modul tutorial atau skrip SQL Server.
   - `/mysql` $\rightarrow$ Menyusun modul tutorial, skrip praktikum, & latihan MySQL 8.x per materi tematik.
   - `/tailmind` $\rightarrow$ Merancang dashboard admin Tailwind CSS.
   - `/zenith-ui` $\rightarrow$ Merancang antarmuka Zenith dashboard (Native CSS, Tailwind, Bootstrap).
   - `/matematika-smp` $\rightarrow$ Menyusun bahan ajar mandiri matematika SMP.
   - `/matematika-sma` $\rightarrow$ Menyusun bahan ajar mandiri matematika SMA (IPA & Pesantren).
   - `@viral` atau `/viral` $\rightarrow$ Menganalisis berita viral medsos, verifikasi fakta, & sentimen publik.
   - `@fakta` atau `/fakta` $\rightarrow$ Memverifikasi kebenaran fakta, uji silang multi-sumber, & ekstraksi teks berita asli.

2. **Perilaku Otomatis (Planning Enforced)**:
   Antigravity di proyek mana pun akan **otomatis membaca `rules/AGENTS.md`**, sehingga agen akan:
   - Membuat file `.plan/YYYY-MM-DD-<nama-fitur>.md` di proyek target Anda.
   - Membukanya secara otomatis di editor.
   - Berhenti untuk meminta konfirmasi (*"eksekusi"* / *"lanjutkan"*) sebelum menulis kode implementasi.

3. **Via Antigravity CLI (`agy`)**:
   Antigravity menyediakan antarmuka baris perintah (*Command Line Interface*) yang ringan dan cepat melalui binary `agy`. Seluruh skill yang terdaftar dapat langsung dipanggil di terminal:

   - **Mode Interaktif (TUI Terminal Session)**:
     ```bash
     # Jalankan sesi chat terminal di proyek mana saja
     agy
     ```
     Di dalam sesi interaktif, ketik pemicu skill secara langsung:
     - `@viral apa saja tren medsos hari ini`
     - `@fakta cek kebenaran video viral X`
     - `/matematika-sma buatkan materi eksponen kelas 10`
     - `/skills` untuk melihat daftar seluruh skill aktif yang terhubung.

   - **Mode Perintah Langsung (*One-Shot Headless Execution*)**:
     ```bash
     # Investigasi berita viral langsung dari terminal
     agy run "@viral analisis isu boikot brand X yang ramai di TikTok"

     # Uji kebenaran klaim fakta langsung dari terminal
     agy run "@fakta apakah benar berita kenaikan tarif listrik 20% di WhatsApp"

     # Generate modul materi ajar SMA
     agy run "/matematika-sma buatkan materi turunan fungsi kelas 11"

     # Desain antarmuka dengan menentukan modul skill secara eksplisit
     agy run --skill skills-agent/coffee-shop-ui "Buatkan Order Summary screen menggunakan Flutter"
     ```

---

## 8. MATRIKS PERAN & KATALOG MODUL

Tabel status dan pemetaan modul skill yang aktif dan tersedia di repositori:

| Kategori | Lokasi / Modul | Peran Representatif | Status | Cakupan Utama |
| :--- | :--- | :--- | :---: | :--- |
| **Global Rule** | `rules/AGENTS.md` | Core Supervisor & Process Controller | **Aktif** | Standar komunikasi direct, boundaries, & Mandatory Two-Phase Planning Protocol |
| **Template** | `rules/templates/template-plan.md` | Planning Architect | **Aktif** | Format baku dokumen perencanaan 5 bagian (.plan/) |
| **Template** | `rules/templates/template-materi-ajar.md` | Curriculum Author | **Aktif** | Standar modul materi ajar siswa 9 bagian, LaTeX KaTeX, Scaffolding |
| **Skill** | `skills/task-management-ui` | Mobile UI/UX Architect | **Aktif** | Dual-Engine (Flutter & React): Task Dashboard, Gradient Slider, Detail Sheet, Create Form |
| **Skill** | `skills/coffee-shop-ui` | Coffee Shop UI/UX Specialist | **Aktif** | Nam Design Styleguide (Sora, #C67C4E), 5 Layar Pemesanan Kopi, Dual-Engine (Flutter & React) |
| **Skill** | `skills/food-delivery-ui` | Food Delivery UI/UX Architect | **Aktif** | Dual-Engine (Flutter & React): 24+ Layar Customer App & Chef Marketplace (#FF7622) |
| **Skill** | `skills/tailmind` | TailAdmin System Specialist | **Aktif** | TailAdmin Dashboard, KPI Stat Cards, Gauge Chart, Sales Bar, Period Filter Area |
| **Skill** | `skills/sql-server` | Senior DBA & Technical Instructor | **Aktif** | Kurikulum 7 Level (Instalasi $\rightarrow$ Advanced), 7 Format Lab, T-SQL Blueprints, Disaster Recovery |
| **Skill** | `skills/mysql` | Senior DBA & Technical Instructor | **Aktif** | Silabus 36 Pembahasan Tematik Terurut (DDL, DML, Where, Joins, Window Functions, Indexing, PITR), 7 Bagian Lab |
| **Skill** | `skills/matematika-smp` | Mathematics Curriculum Author | **Aktif** | Silabus 72 Pertemuan (Kelas 7-9), 9 Bagian Materi Siswa, LaTeX KaTeX, Scaffolding |
| **Skill** | `skills/matematika-sma` | Mathematics Curriculum Author | **Aktif** | Silabus 72 Pertemuan (Kelas 10-12 IPA & Pesantren), 9 Bagian Materi Siswa, LaTeX KaTeX, Scaffolding |
| **Skill** | `skills/zenith-ui` | Multi-Engine UI Architect | **Aktif** | Zenith Modern Dashboard & Web UI (Native CSS, Tailwind CSS, Bootstrap 5) |
| **Skill** | `skills/viral-news-analyzer` | Media Intelligence Analyst | **Aktif** | Pemantauan isu viral medsos, verifikasi akurasi cek fakta, polarisasi pro-kontra, & arsip laporan .md (reports/viral/) |
| **Skill** | `skills/fact-verifier` | Fact-Checker & Investigative Verifier | **Aktif** | Uji silang multi-sumber resmi (minimal 2 media), ekstraksi kutipan asli (verbatim), & tautan URL artikel asli |

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
