# IMPLEMENTATION PLAN: REVISI TEMPLATE MODUL TUTOR & PENYELARASAN SKILL

- **Tanggal Pembuatan**: 2026-11-12
- **Kategori**: rules / templates / curriculum-standards
- **Lokasi Berkas**: `.plan/2026-11-12-revisi-template-tutor.md`
- **Status**: Selesai Diimplementasikan (COMPLETED)
- **Estimasi Kompleksitas**: Sedang

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Berdasarkan hasil evaluasi terhadap `rules/templates/template-tutor.md` dan implementasinya pada skill tutor (`mysql`, `sql-server`, `santri-robotics-iot-mentor`), ditemukan beberapa celah yang berpotensi membingungkan siswa SMK/Mahasiswa serta belum adanya mekanisme praktikum berkelanjutan multi-tema:
1. Belum ada jembatan model mental (*conceptual bridge*) dan pengecekan prasyarat cepat sebelum kamus sintaks.
2. Belum ada panduan pelacakan kondisi data/variabel antara (*state tracing*) pada contoh bertingkat.
3. Jalur SMK dan Mahasiswa belum dipisahkan secara visual dengan label tegas (`[INTI]` vs `[PENDALAMAN]`).
4. Latihan praktikum masih bersifat satu tema terisolasi per modul (*one-off*), belum berkelanjutan lintas modul berbasis 2–3 tema tetap (*Persistent Lab Tracks*).
5. Skill `santri-robotics-iot-mentor` masih memakai format 5 bagian yang belum selaras dengan standar 8 bagian `template-tutor.md`.

### Target Perbaikan
1. Meningkatkan kejelasan pedagogis `rules/templates/template-tutor.md` agar membangun pemahaman kokoh tanpa membuat siswa bingung.
2. Menanamkan arsitektur **2–3 Tema Praktikum Berkelanjutan (*Persistent Lab Tracks*)** ke dalam Bagian 3 dan Bagian 6.
3. Menyelaraskan `skills/mysql`, `skills/sql-server`, dan `skills/santri-robotics-iot-mentor` terhadap standar terbaru.

---

## 2. STRUKTUR BERKAS YANG DIMODIFIKASI

```text
skills-agent/
├── .plan/
│   └── 2026-11-12-revisi-template-tutor.md
├── rules/templates/
│   └── template-tutor.md
└── skills/
    ├── mysql/
    │   ├── SKILL.md
    │   └── prompt.md
    ├── sql-server/
    │   ├── SKILL.md
    │   └── prompt.md
    └── santri-robotics-iot-mentor/
        ├── SKILL.md
        └── prompt.md
```

---

## 3. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Pembaruan Standar Utama (`rules/templates/template-tutor.md`)**
  - [x] Penambahan prinsip Model Mental & *State Tracing*, Penanda Jalur (`[INTI]` vs `[PENDALAMAN]`), dan *Persistent Lab Tracks* (2–3 Tema Berkelanjutan).
  - [x] Penyempurnaan Bagian 1 (Prasyarat Konsep + Jembatan Konsep + Tujuan & Peta Alur).
  - [x] Penyempurnaan Bagian 3 & 4 (Checkpoint Tema 1–3 + *State Tracing* pada Contoh 2–3 + tag jalur pada Contoh 4).
  - [x] Penyempurnaan Bagian 6 & 7 (Latihan Level 1–2 pada Tema 1, Level 3 transfer berkelanjutan pada Tema 2, Level 4 pendalaman pada Tema 2/3).
- [x] **Fase 2: Penyelarasan Skill Database (`mysql` & `sql-server`)**
  - [x] Definisi 3 Tema Berkelanjutan (Tema 1 Toko/Ritel, Tema 2 Akademik/Perpustakaan, Tema 3 Log Audit/Gudang).
  - [x] Pembaruan kerangka 8 bagian di `prompt.md` dan ringkasan di `SKILL.md`.
- [x] **Fase 3: Penyelarasan Skill Robotika (`santri-robotics-iot-mentor`)**
  - [x] Adaptasi ke format 8 bagian dengan tetap menjaga prinsip Wokwi-First, bahasa teknis lugas tanpa kiasan non-teknis, clean code hemat memori, dan rumus elektronika.
  - [x] Definisi 3 Tema Berkelanjutan Robotika & IoT.
- [x] **Fase 4: Verifikasi Konsistensi & Penyelesaian**
  - [x] Memastikan tidak ada referensi usang atau inkonsistensi antar berkas.
  - [x] Memperbarui status rencana menjadi selesai.

---

> **STATUS**: Selesai Diimplementasikan (COMPLETED).
