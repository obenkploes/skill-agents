# IMPLEMENTATION PLAN: MODUL SKILL SANTRI ROBOTICS & IOT MENTOR

- **Tanggal Pembuatan**: 2026-11-07
- **Kategori**: robotics / embedded-systems / iot / curriculum
- **Lokasi Berkas**: `.plan/2026-11-07-skill-santri-robotics-iot-mentor.md`
- **Status**: Selesai Diimplementasikan
- **Estimasi Kompleksitas**: Sedang (Comprehensive Embedded Systems, Robotics & IoT Curriculum)

---

## 1. TUJUAN & RUANG LINGKUP

### Problem Statement
Pengguna membutuhkan modul keahlian agen (*skill agent*) baru bernama `santri-robotics-iot-mentor` yang bertindak sebagai Senior Software Engineer, Systems Analyst, Database Analyst, dan Ahli Otomatisasi untuk membimbing santri dari tingkat dasar hingga mahir dalam rekayasa sistem tertanam (*embedded systems*), robotika, dan Internet of Things (IoT) berbasis Arduino Uno, simulator virtual Wokwi, hingga ESP32 dan integrasi basis data.

### Prinsip Utama & Karakteristik Unik Skill:
1. **Bahasa Indonesia Teknis yang Lugas & Bebas Kiasan Non-Teknis**:
   - Dilarang keras menyisipkan kiasan, perumpamaan agama, fiqih, atau tata bahasa di luar konteks rekayasa perangkat lunak dan elektronika.
   - Menggunakan terminologi teknis baku (mikrokontroler, papan pengembangan, resistor pembatas arus, loop tak terbatas, status logika tegangan, PWM, penanganan interupsi, dll.).
2. **Pendekatan Bertahap (*Scaffolding*)**:
   - Dilarang langsung memberikan skrip penuh atau konfigurasi siap pakai sejak awal.
   - Menjelaskan baris demi baris, fungsi demi fungsi, dan blok per blok.
3. **Simulasi Virtual-First (Wokwi-First)**:
   - Seluruh modul praktikum dan proyek dirancang dapat disimulasikan secara penuh di peramban web menggunakan Wokwi (`wokwi.com`) dengan Arduino Uno/ESP32 sebelum masuk ke perangkat keras fisik.
4. **Format Standar Modul 5 Bagian**:
   - Bagian 1: Pengantar Konsep Rekayasa.
   - Bagian 2: Kamus Teknis: Fungsi dan Argumen (Format sintaksis C++, Tipe Data, Peran, Nilai Valid/Konstanta).
   - Bagian 3: Implementasi Kode Bersih (*Clean Code*, hemat memori, komentar kunci).
   - Bagian 4: Skema Perakitan Virtual di Wokwi (diagram koneksi pinout/ASCII, langkah perakitan, rumus elektronika/Hukum Ohm).
   - Bagian 5: Lembar Latihan & Penguatan Logika (Latihan 1: Manipulasi Argumen, Latihan 2: Penambahan Komponen/Fungsi, Latihan 3: Studi Kasus Otomasi Nyata).
5. **Roadmap 5 Tahap Proyek Aplikatif**:
   - **Tahap 1**: Fondasi Digital I/O & Rekayasa Waktu (`pinMode`, `digitalWrite`, `millis()`, non-blocking).
   - **Tahap 2**: Input Sensorik, Penggerak Mekanik, & **Proyek 1: Tong Sampah Otomatis (Smart Trash Bin)** (Ultrasonik HC-SR04, Servo SG90, indikator LED).
   - **Tahap 3**: Kendali Motor DC & **Proyek 2: Robot Line Follower Otonom** (`analogWrite` PWM, array IR sensor TCRT5000, motor driver H-Bridge L298N/L293D, algoritma koreksi jalur).
   - **Tahap 4**: Deteksi Multi-Sensor & **Proyek 3: Robot Pemadam Api Otonom** (Flame sensor multi-arah, navigasi berbasis prioritas, aktuator kipas/relay/transistor).
   - **Tahap 5**: Internet of Things (IoT), Telemetri, & Basis Data (**Proyek 4: Node Telemetri & Kontrol Web ESP32**) (ESP32 dual-core, WiFi Station, JSON serialization, MQTT Publish/Subscribe, REST API ke basis data PostgreSQL/Supabase).

---

## 2. RANCANGAN ARSITEKTUR & STRUKTUR BERKAS

### Struktur Berkas Terkait
```text
skills-agent/
├── .plan/
│   └── 2026-11-07-skill-santri-robotics-iot-mentor.md   # [Baru] Dokumen perencanaan implementasi modul
├── skills/
│   └── santri-robotics-iot-mentor/                     # [Baru] Direktori modul skill
│       ├── skill.json                                  # [Baru] Metadata skill & triggers CLI/chat
│       ├── SKILL.md                                    # [Baru] Ringkasan kapabilitas & roadmap kurikulum
│       └── prompt.md                                   # [Baru] System prompt instruktur rekayasa embedded & Wokwi
└── README.md                                           # [Update] Registrasi pada katalog modul proyek
```

---

## 3. TAHAPAN EKSEKUSI (CHECKLIST)

- [x] **Fase 1: Konfigurasi Metadata & Direktori (`skills/santri-robotics-iot-mentor/skill.json`)**
  - [x] Pembuatan direktori `skills/santri-robotics-iot-mentor`.
  - [x] Penyusunan `skill.json` memuat properti `name: "santri-robotics-iot-mentor"`, `category: "robotics/iot"`, triggers (`/robotics`, `/iot`, `/santri-robotics`, `/wokwi`, `/arduino-mentor`), keywords, dan aturan rujukan ke `rules/AGENTS.md`.
- [x] **Fase 2: Pembuatan Entrypoint Antigravity (`skills/santri-robotics-iot-mentor/SKILL.md`)**
  - [x] Frontmatter YAML resmi dengan peringatan `MANDATORY WORKFLOW`.
  - [x] Penjabaran prinsip pedagogi (Bahasa teknis lugas tanpa kiasan non-teknis, Scaffolding, Wokwi-First).
  - [x] Struktur standar modul 5 bagian dan ringkasan 5 tahap kurikulum hingga 4 proyek robotika & IoT.
- [x] **Fase 3: Penyusunan System Prompt Spesialis (`skills/santri-robotics-iot-mentor/prompt.md`)**
  - [x] Persona Senior Embedded Systems & IoT Architect.
  - [x] Kamus teknis fungsi C++ Arduino/ESP32 dengan pembedahan argumen dan tipe data.
  - [x] Blueprint skema Wokwi (diagram koneksi pinout), clean code C++, dan panduan logika 4 proyek inti.
- [x] **Fase 4: Pembaruan Dokumentasi Repositori (`README.md`)**
  - [x] Memperbarui diagram pohon direktori di `README.md`.
  - [x] Menambahkan contoh pemanggilan skill pada daftar penggunaan harian dan CLI (`/robotics`, `/iot`).
  - [x] Mendaftarkan baris skill `santri-robotics-iot-mentor` pada tabel matriks peran.

---

## 4. ANALISIS RISIKO & MITIGASI

- **Potensi Risiko**: Siswa bingung merangkai sirkuit virtual di Wokwi jika diagram pinout tidak jelas.
- **Mitigasi**: Di dalam `prompt.md` diwajibkan menyertakan tabel atau diagram koneksi pin-ke-pin yang eksplisit (misal: `VCC -> 5V`, `GND -> GND`, `TRIG -> D9`, `ECHO -> D10`), serta instruksi penambahan part di Wokwi (`diagram.json` atau panduan visual).
- **Potensi Risiko**: Kode Arduino menggunakan `delay()` berlebihan yang membekukan eksekusi waktu nyata (*CPU blocking*).
- **Mitigasi**: Modul menegakkan transisi ke teknik pewaktu non-blocking berbasis `millis()` sedini mungkin agar robot tetap responsif membaca sensor saat bermanuver.

---

> **STATUS**: Selesai Diimplementasikan (COMPLETED)
