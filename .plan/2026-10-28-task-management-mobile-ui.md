# IMPLEMENTATION PLAN: MODUL SKILL DUAL-ENGINE MOBILE TASK MANAGEMENT UI (FLUTTER & REACT)

- **Tanggal Pembuatan**: 2026-10-28 (Revisi 3: Arsitektur Dinamis Multi-Framework Flutter & React)
- **Kategori**: frontend/mobile
- **Target Platform**: Dual-Engine (Flutter Dart & React Native / React Tailwind)
- **Lokasi Berkas**: `.plan/2026-10-28-task-management-mobile-ui.md` (disimpan di root proyek yang sedang aktif dikerjakan)
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang

---

## 1. REKOMENDASI ARSITEKTUR DINAMIS (FLUTTER VS REACT)

Menjawab kebutuhan pengguna agar modul dapat menghasilkan UI dinamis menggunakan **Flutter** maupun **React**, terdapat dua pendekatan arsitektur:

### A. Pendekatan Dual-Engine dalam Satu Skill (Rekomendasi Utama)
- **Struktur**: Tetap menggunakan folder tunggal `frontend/mobile/task-management-ui`.
- **Mekanisme**:
  1. **Universal Design Tokens (Single Source of Truth)**: Mendefinisikan token desain visual (palet warna `#2563EB`, gradien ganda, radius `20px`, elevasi bayangan) sebagai fondasi bersama.
  2. **Dynamic Framework Switcher**:
     - Jika proyek/instruksi mengarah ke **Flutter**: Mengeluarkan kode Flutter widget murni (`Material 3`, `ThemeData`, `home_screen.dart`, dll.).
     - Jika proyek/instruksi mengarah ke **React / React Native**: Mengeluarkan kode React Native / Tailwind CSS (`NativeWind`, `HomeScreen.tsx`, dll.).
     - **Context Auto-Detection**: Agen memeriksa keberadaan berkas `pubspec.yaml` (memicu Flutter) atau `package.json` (memicu React) di workspace target.
- **Kelebihan**: Sangat efisien, konsistensi visual 100% identik di kedua platform, satu konfigurasi trigger untuk pemeliharaan jangka panjang.

### B. Pendekatan Dua Modul Terpisah (Alternatif)
- `frontend/mobile/task-ui-flutter` dan `frontend/mobile/task-ui-react`.
- **Kelemahan**: Terjadi duplikasi definisi desain token dan mempersulit pengguna saat ingin berpindah framework pada project yang sama.

> **Rekomendasi**: Mengadopsi **Pendekatan Dual-Engine** di dalam folder `frontend/mobile/task-management-ui`.

---

## 2. TUJUAN & RUANG LINGKUP MODUL
- **Problem Statement**: Pengembang membutuhkan fleksibilitas saat membangun aplikasi mobile task management: terkadang menggunakan **Flutter** untuk performa native lintas platform, atau **React Native / React Tailwind Mobile** untuk integrasi web/mobile cepat. Modul ini dirancang untuk dapat mengeluarkan komponen UI pada kedua platform dengan fidelitas visual yang identik mengacu pada tangkapan layar desain (*Task Management Mobile App UI Kit*).
- **Goals**:
  1. Menyusun direktori modul skill di `frontend/mobile/task-management-ui/` yang memuat:
     - `skill.json`: Metadata, triggers multi-framework (`/task-ui`, `/flutter-task-ui`, `/react-task-ui`).
     - `SKILL.md`: Spesifikasi discovery resmi Antigravity.
     - `prompt.md`: System prompt dual-engine (Universal Design Tokens + Blueprint Flutter + Blueprint React).
  2. Implementasi Blueprint Komponen pada Kedua Framework:
     - **Layar 1 (Home Dashboard)**:
       - *Flutter*: `home_screen.dart` (`AppBar`, `CircleAvatar`, Horizontal Category `ListView`, Segmented Pill, `TaskCard`, Docked `BottomAppBar` + `FloatingActionButton`).
       - *React*: `HomeScreen.tsx` (TopBar, horizontal scroll container, segmented active/completed buttons, `TaskCard`, floating bottom bar + central FAB button).
     - **Layar 2 (Task Detail Modal / Bottom Sheet)**:
       - *Flutter*: `task_detail_bottom_sheet.dart` (`showModalBottomSheet`, tab switch `Details` vs `Comments`, info grid 2x2, `ExpansionTile`, tombol *"Mark As Done"*).
       - *React*: `TaskDetailModal.tsx` (Bottom sheet modal, tab switch, info grid, expandable accordion, tombol *"Mark As Done"*).
     - **Layar 3 (Create New Task Form)**:
       - *Flutter*: `create_task_bottom_sheet.dart` (Form fields, `showDatePicker`, dropdown prioritas/status, tag input, switch toggle recurring, tombol Cancel & Create Task).
       - *React*: `CreateTaskModal.tsx` (Form inputs, date picker, custom select dropdowns, tag chips input, toggle switch, tombol Cancel & Create Task).
  3. Konvensi Kualitas: Clean Architecture, TypeScript interfaces (React), Null-safety & `const` constructors (Flutter), serta anotasi path berkas eksplisit di baris teratas.

---

## 3. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-10-28-task-management-mobile-ui.md   # [Revisi 3] Rencana modul Dual-Engine
└── frontend/
    └── mobile/
        └── task-management-ui/                   # [Direktori Modul Skill]
            ├── skill.json                        # [Baru] Metadata, multi-framework triggers, rules link
            ├── SKILL.md                          # [Baru] Spesifikasi Antigravity progressive disclosure
            └── prompt.md                         # [Baru] System prompt Dual-Engine (Universal Tokens + Flutter & React Blueprints)
```

### Rincian Blueprint Arsitektur Modul:
1. **Universal Design Tokens (Shared Truth)**:
   - Primary Color: `#2563EB` (Electric Blue).
   - Card Gradients:
     - *Web Design*: `#2563EB` $\rightarrow$ `#4338CA`.
     - *Web Development*: `#4F46E5` $\rightarrow$ `#7C3AED`.
   - Canvas Background: `#F8FAFC` (Light) & `#0F172A` (Dark).
   - Card Surface: `#FFFFFF` dengan corner radius `20px` dan bayangan halus `shadow-sm`.
   - Priority Chips: `High` (Amber `#FEF3C7` / `#D97706`), `Medium` (Blue `#DBEAFE` / `#2563EB`).
   - Action Success: `Mark As Done` (Emerald `#10B981`).
2. **Flutter Engine Spec**:
   - `lib/theme/app_colors.dart` & `app_theme.dart`
   - `lib/models/task_model.dart`
   - `lib/views/home_screen.dart`
   - `lib/widgets/task_card.dart`
   - `lib/widgets/task_detail_bottom_sheet.dart`
   - `lib/widgets/create_task_bottom_sheet.dart`
3. **React / React Native Engine Spec**:
   - `src/types/task.ts`
   - `src/components/HomeScreen.tsx`
   - `src/components/TaskCard.tsx`
   - `src/components/TaskDetailModal.tsx`
   - `src/components/CreateTaskModal.tsx`

---

## 4. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Antigravity Indexing (`skill.json` & `SKILL.md`)**
  - [x] Pembuatan `frontend/mobile/task-management-ui/skill.json` dengan dukungan multi-framework dan triggers `/task-ui`, `/flutter-task-ui`, `/react-task-ui`.
  - [x] Pembuatan `frontend/mobile/task-management-ui/SKILL.md` dengan frontmatter YAML spesifikasi Dual-Engine.
- [x] **Fase 2: Perumusan System Prompt Dual-Engine (`prompt.md`)**
  - [x] Pendefinisian persona *Senior Mobile UI/UX Architect (Flutter & React Native Specialist)*.
  - [x] Bagian Universal Design Tokens (Warna, Gradien, Tipografi, Radius).
  - [x] Framework Switcher Logic (Deteksi otomatis via konteks proyek atau kata kunci instruksi pengguna).
  - [x] Blueprint Widget Flutter lengkap tanpa *placeholder*.
  - [x] Blueprint Komponen React / React Native lengkap tanpa *placeholder*.
- [x] **Fase 3: Validasi Modul & Registrasi Katalog**
  - [x] Pembaruan checklist di `.plan/2026-10-28-task-management-mobile-ui.md`.
  - [x] Pendaftaran modul baru di `README.md` pada tabel katalog skill kategori `frontend/mobile` (Dual-Engine: Flutter & React).

---

## 5. ANALISIS RISIKO & MITIGASI
- **Potensi Risiko**: Ambiguitas framework jika pengguna hanya meminta *"Buatkan halaman dashboard task"* tanpa menyebutkan Flutter atau React.
- **Mitigasi**: Di dalam `prompt.md`, agen diprogram untuk memeriksa berkas proyek (`pubspec.yaml` vs `package.json`). Jika berada di luar workspace proyek, agen akan memberikan opsi cepat atau mendahulukan Flutter sebagai default dengan catatan bahwa varian React juga tersedia.

---

> **COMPLETED**: Seluruh tahapan rencana implementasi modul Dual-Engine Task Management Mobile UI Kit telah selesai dieksekusi. Berkas `skill.json`, `SKILL.md`, dan `prompt.md` aktif di `frontend/mobile/task-management-ui/`.
