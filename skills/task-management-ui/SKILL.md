---
name: task-management-ui
description: >-
  Spesialis arsitektur dan perancangan antarmuka aplikasi mobile manajemen tugas (Task Management Mobile App)
  dengan arsitektur Dual-Engine dinamis yang mendukung Flutter (Dart) dan React / React Native (Tailwind CSS / NativeWind).
  MANDATORY WORKFLOW: You MUST create a .plan/YYYY-MM-DD-<name>.md file, auto-open it via Start-Process, and await user approval BEFORE generating or writing any code.
---

# Dual-Engine Task Management Mobile UI Kit Specialist

Modul keahlian antarmuka mobile dinamis yang mendukung pembuatan komponen dan layar aplikasi task management modern baik di lingkungan **Flutter (Dart)** maupun **React / React Native (TypeScript & Tailwind)**.

Panduan arsitektur, design tokens universal, serta blueprint komponen lengkap tersedia di [prompt.md](./prompt.md).

## MANDATORY PRE-EXECUTION PLANNING PROTOCOL (DO NOT SKIP)
Sebelum menulis, memodifikasi, atau menghasilkan kode komponen/layar apapun:
1. **Analisis Kebutuhan**: Pahami layar dan interaksi yang diminta.
2. **Buat Berkas Rencana**: Tulis dokumen perencanaan di `.plan/YYYY-MM-DD-<nama-fitur>.md` pada proyek aktif.
3. **Buka Otomatis Rencana**: Jalankan perintah terminal `Start-Process -FilePath ".plan\<nama-file>.md"`.
4. **BERHENTI & Tunggu Persetujuan**: Sajikan tautan berkas `file:///` dan minta konfirmasi ("eksekusi" / "lanjutkan") dari pengguna.
DILARANG KERAS langsung menulis atau mengenerate kode implementasi sebelum konfirmasi diberikan.

## Aturan Utama (Invariant Rules)
- Patuhi aturan universal di [rules/AGENTS.md](../../rules/AGENTS.md).

## Fitur & Layar yang Didukung
1. **Home / Task Dashboard Screen**:
   - Header sapaan personal dengan avatar profil, search button, dan notifikasi unread badge.
   - Horizontal Category Slider dengan kartu gradien ganda (*Web Design* & *Web Development*), progress tracker, dan tumpukan avatar pengguna (*Avatar Stack*).
   - My Tasks Section: Segmented control kapsul (`[Active]` vs `[Completed]`) dan daftar kartu tugas (`TaskCard`) dengan tag chips dan priority chip.
   - Docked Bottom Navigation Bar dengan elevated central Floating Action Button (FAB `+`).
2. **Task Detail Modal / Bottom Sheet**:
   - Header judul tugas dengan tombol aksi edit.
   - Segmented tab switch: `Details` vs `Comments (2)`.
   - Matriks informasi 2x2: Priority box, Due Date box, Status box, dan Description box.
   - Accordion expandable *"Additional Details"*.
   - Aksi footer: Tombol hijau *"Mark As Done"* dan tombol *"Close"*.
3. **Create New Task Modal / Drawer Form**:
   - Form fields: Judul tugas, deskripsi tugas, interaktif date picker dengan ikon kalender, dropdown prioritas, dropdown status, tag bar dengan tombol `+`, dan switch toggle *"Recurring Task"*.
   - Aksi footer: Tombol *"Cancel"* dan tombol *"Create Task"* (solid primary blue).

