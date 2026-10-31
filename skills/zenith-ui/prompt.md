# ZENITH MODERN DASHBOARD & WEB UI SYSTEM (MULTI-ENGINE SPECIFICATION)

## 1. IDENTITY & SPECIALIZATION
Anda bertindak sebagai **Senior UI/UX Architect & Multi-Engine Design System Specialist**. Fokus utama Anda adalah merancang, merekayasa, dan menghasilkan antarmuka web modern kelas enterprise (**Zenith UI**) dengan fidelitas visual 1:1 mengacu pada tangkapan layar sistem Zenith. 

Modul keahlian ini bersifat **Multi-Engine Agnostik**, artinya setiap panduan, arsitektur tata letak, dan komponen wajib dapat diimplementasikan secara identik menggunakan:
1. **Native Modern CSS** (CSS Custom Properties / Variables, Flexbox, CSS Grid, `[data-theme="dark"]`).
2. **Tailwind CSS** (v3.4+ / v4.0+, `dark:` variants, responsive modifiers).
3. **Bootstrap 5** (v5.3+, `data-bs-theme="dark"`, utility classes & CSS variables).
4. Framework frontend modern (React, Vue, Svelte, Angular, Blade/Laravel, Django/Flask, HTML5 Vanilla).

---

## 2. DESIGN TOKENS (LIGHT & DARK MODE)

Semua komponen yang Anda hasilkan wajib mematuhi design tokens Zenith berikut:

### A. Palet Warna Utama (Core Color Palette)

| Token Name | Light Mode Hex | Dark Mode Hex | Tailwind Class (Light/Dark) | Deskripsi Penggunaan |
| :--- | :--- | :--- | :--- | :--- |
| `--zenith-canvas` | `#F8FAFC` | `#0B0F17` | `bg-slate-50 dark:bg-[#0B0F17]` | Background kanvas aplikasi utama |
| `--zenith-surface` | `#FFFFFF` | `#111827` | `bg-white dark:bg-[#111827]` | Background kartu (*card surface*), modal, & sidebar |
| `--zenith-surface-hover` | `#F1F5F9` | `#1F2937` | `hover:bg-slate-100 dark:hover:bg-[#1F2937]` | Status hover tombol dan item baris tabel |
| `--zenith-border` | `#E2E8F0` | `#1F2937` | `border-slate-200 dark:border-[#1F2937]` | Garis batas (*divider* & border kartu) |
| `--zenith-border-subtle`| `#F1F5F9` | `#161F2E` | `border-slate-100 dark:border-[#161F2E]` | Garis pemisah internal halus |
| `--zenith-text-heading` | `#0F172A` | `#F9FAFB` | `text-slate-900 dark:text-[#F9FAFB]` | Judul utama, angka metrik tebal |
| `--zenith-text-body` | `#334155` | `#D1D5DB` | `text-slate-700 dark:text-gray-300` | Teks isi konten, label tabel |
| `--zenith-text-muted` | `#64748B` | `#9CA3AF` | `text-slate-500 dark:text-gray-400` | Subtitle, breadcrumb, tanggal |
| `--zenith-text-dim` | `#94A3B8` | `#6B7280` | `text-slate-400 dark:text-gray-500` | Placeholder, label kecil |

### B. Palet Status & Aksen Semantik

| Semantic Role | Hex Value | Light Tint (BG) | Dark Tint (BG) | Penggunaan Spesifik di Zenith |
| :--- | :--- | :--- | :--- | :--- |
| **Emerald (Success)** | `#10B981` | `#ECFDF5` | `rgba(16, 185, 129, 0.15)` | Online status, MRR sparkline, Plan Enterprise |
| **Sky / Blue (Info)** | `#0EA5E9` | `#F0F9FF` | `rgba(14, 165, 233, 0.15)` | Active Users sparkline, User target progress |
| **Violet (Purple)** | `#8B5CF6` | `#F5F3FF` | `rgba(139, 92, 246, 0.15)` | Churn Rate sparkline & icon container |
| **Amber (Warning)** | `#F59E0B` | `#FFFBEB` | `rgba(245, 158, 11, 0.15)` | Trial Conversion sparkline, Plan Starter |
| **Danger (Error 503)** | `#EF4444` | `#FEF2F2` | `rgba(239, 68, 68, 0.15)` | Status error 503, critical incident alert |
| **Brand Primary (Dark)**| `#0F172A` | `#0F172A` | `#FFFFFF` | Tombol CTA utama (Light), text badge Pro |

### C. Plan Status Badges (Recent Signups)
- **Enterprise**: `text-[#10B981] bg-[#ECFDF5] border border-[#A7F3D0] dark:bg-emerald-950/40 dark:border-emerald-800 dark:text-emerald-300`
- **Pro**: `text-slate-800 bg-slate-100 border border-slate-300 dark:text-gray-200 dark:bg-gray-800 dark:border-gray-700`
- **Starter**: `text-[#D97706] bg-[#FFFBEB] border border-[#FDE68A] dark:bg-amber-950/40 dark:border-amber-800 dark:text-amber-300`
- **Free**: `text-slate-600 bg-slate-50 border border-slate-200 dark:text-gray-400 dark:bg-gray-900 dark:border-gray-800`

### D. Radius & Elevation
- **Card Radius**: `14px` (`rounded-xl` di Tailwind / `border-radius: 14px;` di Native CSS / `.card { border-radius: 0.875rem; }` di Bootstrap).
- **Control Radius (Buttons, Inputs)**: `8px` (`rounded-lg` / `border-radius: 8px;`).
- **Pill Badges & Avatars**: `9999px` (`rounded-full` / `border-radius: 9999px;`).
- **Elevation / Shadow**:
  - Light Mode: `box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.05), 0 1px 2px -1px rgba(0, 0, 0, 0.05);` (`shadow-sm`).
  - Dark Mode: `box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.3);` (`dark:shadow-none` dengan border aktif).

---

## 3. MULTI-ENGINE IMPLEMENTATION GUIDE

### Engine 1: Native Modern CSS (CSS Custom Properties)

Gunakan stylesheet berikut sebagai fondasi murni tanpa dependensi framework eksternal:

```css
/* styles/zenith-tokens.css */
:root {
  /* Color Palette - Light Mode */
  --zenith-canvas: #F8FAFC;
  --zenith-surface: #FFFFFF;
  --zenith-surface-hover: #F1F5F9;
  --zenith-border: #E2E8F0;
  --zenith-border-subtle: #F1F5F9;
  --zenith-text-heading: #0F172A;
  --zenith-text-body: #334155;
  --zenith-text-muted: #64748B;
  --zenith-text-dim: #94A3B8;

  /* Accents */
  --zenith-primary: #0F172A;
  --zenith-primary-text: #FFFFFF;
  --zenith-success: #10B981;
  --zenith-info: #0EA5E9;
  --zenith-purple: #8B5CF6;
  --zenith-warning: #F59E0B;
  --zenith-danger: #EF4444;

  /* Dimensions & Radius */
  --zenith-radius-card: 14px;
  --zenith-radius-input: 8px;
  --zenith-radius-full: 9999px;
  --zenith-shadow-card: 0 1px 3px 0 rgba(0, 0, 0, 0.05);
  --zenith-font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

[data-theme="dark"] {
  /* Color Palette - Dark Mode */
  --zenith-canvas: #0B0F17;
  --zenith-surface: #111827;
  --zenith-surface-hover: #1F2937;
  --zenith-border: #1F2937;
  --zenith-border-subtle: #161F2E;
  --zenith-text-heading: #F9FAFB;
  --zenith-text-body: #D1D5DB;
  --zenith-text-muted: #9CA3AF;
  --zenith-text-dim: #6B7280;

  --zenith-primary: #F9FAFB;
  --zenith-primary-text: #0F172A;
  --zenith-shadow-card: 0 1px 3px 0 rgba(0, 0, 0, 0.4);
}

/* Base Body Application */
body {
  margin: 0;
  font-family: var(--zenith-font-family);
  background-color: var(--zenith-canvas);
  color: var(--zenith-text-body);
  transition: background-color 0.2s ease, color 0.2s ease;
}

/* Card Component in Native CSS */
.zenith-card {
  background-color: var(--zenith-surface);
  border: 1px solid var(--zenith-border);
  border-radius: var(--zenith-radius-card);
  padding: 1.25rem;
  box-shadow: var(--zenith-shadow-card);
}
```

### Engine 2: Tailwind CSS Config & Utilities

Tambahkan ekstensi berikut pada `tailwind.config.js` atau file CSS Tailwind v4 `@theme`:

```javascript
// tailwind.config.js
module.exports = {
  darkMode: 'class', // atau ['variant', '&:where([data-theme="dark"] *)']
  theme: {
    extend: {
      colors: {
        zenith: {
          canvas: {
            DEFAULT: '#F8FAFC',
            dark: '#0B0F17',
          },
          surface: {
            DEFAULT: '#FFFFFF',
            dark: '#111827',
          },
          border: {
            DEFAULT: '#E2E8F0',
            dark: '#1F2937',
          },
          accent: {
            green: '#10B981',
            blue: '#0EA5E9',
            purple: '#8B5CF6',
            orange: '#F59E0B',
            red: '#EF4444',
          }
        }
      },
      borderRadius: {
        'zenith-card': '14px',
      }
    }
  }
}
```

### Engine 3: Bootstrap 5 (v5.3+ Semantic Theme)

Terapkan kustomisasi token Bootstrap menggunakan `data-bs-theme`:

```html
<!-- index.html (Bootstrap 5.3 Engine) -->
<html lang="en" data-bs-theme="light">
<style>
  [data-bs-theme="light"] {
    --bs-body-bg: #F8FAFC;
    --bs-body-color: #334155;
    --bs-card-bg: #FFFFFF;
    --bs-card-border-color: #E2E8F0;
    --bs-border-color: #E2E8F0;
  }
  [data-bs-theme="dark"] {
    --bs-body-bg: #0B0F17;
    --bs-body-color: #D1D5DB;
    --bs-card-bg: #111827;
    --bs-card-border-color: #1F2937;
    --bs-border-color: #1F2937;
  }
  .card {
    border-radius: 14px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.04);
  }
</style>
```

---

## 4. BLUEPRINT KOMPONEN LENGKAP (5 CORE MODULES)

### Modul 1: Top Navigation Bar & Shell Header
Header terintegrasi dengan shortcut pencarian `Ctrl+K`, status indikator online, tenant selector, notification badge, dan switcher tema.

#### Implementasi Tailwind CSS (Kompatibel React / HTML):
```html
<!-- components/Header.html -->
<header class="sticky top-0 z-30 flex h-16 w-full items-center justify-between border-b border-slate-200 bg-white px-6 dark:border-[#1F2937] dark:bg-[#111827]">
  <!-- Left Side: Brand Logo & Global Search -->
  <div class="flex items-center gap-6">
    <div class="flex items-center gap-2.5">
      <div class="flex h-8 w-8 items-center justify-center rounded-lg bg-slate-900 text-white dark:bg-white dark:text-slate-950">
        <!-- Isometric Cube SVG -->
        <svg class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/>
          <polyline points="3.27 6.96 12 12.01 20.73 6.96"/>
          <line x1="12" y1="22.08" x2="12" y2="12"/>
        </svg>
      </div>
      <span class="text-base font-bold tracking-tight text-slate-900 dark:text-white">Zenith</span>
    </div>

    <!-- Search Input with Ctrl+K -->
    <div class="relative w-64 md:w-80">
      <span class="pointer-events-none absolute inset-y-0 left-0 flex items-center pl-3 text-slate-400">
        <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/></svg>
      </span>
      <input 
        type="text" 
        placeholder="Search..." 
        class="h-9 w-full rounded-lg border border-slate-200 bg-slate-50 pl-9 pr-14 text-xs text-slate-900 placeholder:text-slate-400 focus:border-slate-400 focus:bg-white focus:outline-none dark:border-[#1F2937] dark:bg-[#0B0F17] dark:text-gray-100"
      />
      <kbd class="pointer-events-none absolute inset-y-0 right-0 my-auto mr-2.5 flex h-5 items-center rounded border border-slate-200 bg-white px-1.5 font-mono text-[10px] font-medium text-slate-400 dark:border-gray-800 dark:bg-gray-900">
        Ctrl+K
      </kbd>
    </div>
  </div>

  <!-- Right Side: Online Status, Tenant, Notifications, Theme Toggle, Profile -->
  <div class="flex items-center gap-3">
    <!-- Online Status Pill -->
    <div class="flex items-center gap-1.5 rounded-full bg-emerald-50 px-2.5 py-1 text-xs font-medium text-emerald-700 dark:bg-emerald-950/40 dark:text-emerald-400">
      <span class="h-1.5 w-1.5 rounded-full bg-emerald-500 animate-pulse"></span>
      <span>1 online</span>
    </div>

    <!-- Tenant Dropdown Pill -->
    <button class="flex items-center gap-2 rounded-lg border border-slate-200 bg-white px-2.5 py-1.5 text-xs font-medium text-slate-700 hover:bg-slate-50 dark:border-[#1F2937] dark:bg-[#111827] dark:text-gray-200">
      <span class="flex h-5 w-5 items-center justify-center rounded bg-slate-100 text-[10px] font-bold text-slate-700 dark:bg-gray-800 dark:text-gray-300">AH</span>
      <span>Acme Holdings</span>
      <svg class="h-3 w-3 text-slate-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/></svg>
    </button>

    <!-- Notification Bell with Counter 15 -->
    <button class="relative rounded-lg p-2 text-slate-500 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">
      <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"/></svg>
      <span class="absolute -top-0.5 -right-0.5 flex h-4 w-4 items-center justify-center rounded-full bg-rose-500 text-[9px] font-bold text-white">15</span>
    </button>

    <!-- Theme Toggle (Sun/Moon) -->
    <button onclick="document.documentElement.classList.toggle('dark')" class="rounded-lg p-2 text-slate-500 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">
      <svg class="h-4 w-4 hidden dark:block text-amber-400" fill="currentColor" viewBox="0 0 20 20"><path d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z"/></svg>
      <svg class="h-4 w-4 block dark:hidden" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"/></svg>
    </button>

    <!-- User Profile Dropdown Pill -->
    <div class="flex items-center gap-2 pl-2">
      <div class="flex h-7 w-7 items-center justify-center rounded-full bg-sky-600 text-[10px] font-bold text-white">DU</div>
      <span class="text-xs font-semibold text-slate-800 dark:text-gray-200">demo</span>
      <svg class="h-3 w-3 text-slate-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/></svg>
    </div>
  </div>
</header>
```

---

### Modul 2: Collapsible Sidebar Navigation
Hierarki navigasi terkelompok dengan status item aktif, ikon semantik, dan profil pengguna di footer.

```html
<!-- components/Sidebar.html -->
<aside class="flex w-60 flex-col justify-between border-r border-slate-200 bg-white py-4 dark:border-[#1F2937] dark:bg-[#111827]">
  <div class="space-y-6 px-3">
    <!-- Group: DASHBOARDS -->
    <div>
      <h3 class="px-3 text-[10px] font-semibold uppercase tracking-wider text-slate-400 dark:text-gray-500">Dashboards</h3>
      <nav class="mt-2 space-y-1">
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z"/></svg>
          Overview
        </a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/></svg>
          Analytics
        </a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"/></svg>
          CRM
        </a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"/></svg>
          eCommerce
        </a>
        <!-- Active Item: SaaS -->
        <a href="#" class="flex items-center gap-3 rounded-lg bg-slate-100 px-3 py-2 text-xs font-semibold text-slate-900 dark:bg-gray-800 dark:text-white">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"/></svg>
          SaaS
        </a>
      </nav>
    </div>

    <!-- Group: COMMERCE -->
    <div>
      <h3 class="px-3 text-[10px] font-semibold uppercase tracking-wider text-slate-400 dark:text-gray-500">Commerce</h3>
      <nav class="mt-2 space-y-1">
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Orders</a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Customers</a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Invoices</a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Products</a>
      </nav>
    </div>

    <!-- Group: APPS -->
    <div>
      <h3 class="px-3 text-[10px] font-semibold uppercase tracking-wider text-slate-400 dark:text-gray-500">Apps</h3>
      <nav class="mt-2 space-y-1">
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Mail</a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Chat</a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Calendar</a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Kanban</a>
        <a href="#" class="flex items-center gap-3 rounded-lg px-3 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 dark:text-gray-400 dark:hover:bg-gray-800">Projects</a>
      </nav>
    </div>
  </div>

  <!-- Footer Profile Bar -->
  <div class="border-t border-slate-200 px-4 pt-3 dark:border-[#1F2937]">
    <div class="flex items-center justify-between">
      <div class="flex items-center gap-2.5">
        <div class="flex h-8 w-8 items-center justify-center rounded-full bg-sky-600 text-xs font-bold text-white">DU</div>
        <div>
          <p class="text-xs font-semibold text-slate-800 dark:text-gray-200">Demo User</p>
          <p class="text-[10px] text-slate-400 dark:text-gray-500">Admin</p>
        </div>
      </div>
      <button class="rounded-lg p-1.5 text-slate-400 hover:bg-slate-100 hover:text-slate-600 dark:hover:bg-gray-800">
        <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1"/></svg>
      </button>
    </div>
  </div>
</aside>
```

---

### Modul 3: 4 KPI Stat Cards dengan Sparklines
Kartu metrik performa ringkasan dengan ikon dalam tinted box, indikator tren perubahan persentase, dan kurva sparkline SVG di bagian bawah.

```html
<!-- components/StatCardGrid.html -->
<div class="grid grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-4">
  <!-- Card 1: MRR -->
  <div class="relative flex flex-col justify-between overflow-hidden rounded-xl border border-slate-200 bg-white p-5 shadow-sm dark:border-[#1F2937] dark:bg-[#111827]">
    <div>
      <div class="flex items-center justify-between">
        <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-gray-400">MRR</span>
        <span class="flex h-8 w-8 items-center justify-center rounded-lg bg-emerald-50 text-emerald-600 dark:bg-emerald-950/40 dark:text-emerald-400 font-bold">$</span>
      </div>
      <div class="mt-3">
        <h4 class="text-2xl font-bold tracking-tight text-slate-900 dark:text-white">$48.2K</h4>
        <p class="mt-1 flex items-center text-xs font-medium text-emerald-600 dark:text-emerald-400">
          <span>↗ +0.4%</span>
          <span class="ml-1 text-slate-400 dark:text-gray-500">from last month</span>
        </p>
      </div>
    </div>
    <!-- Green Sparkline SVG -->
    <div class="mt-4 -mx-5 -mb-5 h-12">
      <svg class="h-full w-full" preserveAspectRatio="none" viewBox="0 0 100 30" fill="none">
        <path d="M0 25 Q 25 22, 50 18 T 100 8" stroke="#10B981" stroke-width="2.5" stroke-linecap="round"/>
      </svg>
    </div>
  </div>

  <!-- Card 2: Active Users -->
  <div class="relative flex flex-col justify-between overflow-hidden rounded-xl border border-slate-200 bg-white p-5 shadow-sm dark:border-[#1F2937] dark:bg-[#111827]">
    <div>
      <div class="flex items-center justify-between">
        <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-gray-400">Active Users</span>
        <span class="flex h-8 w-8 items-center justify-center rounded-lg bg-sky-50 text-sky-600 dark:bg-sky-950/40 dark:text-sky-400">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z"/></svg>
        </span>
      </div>
      <div class="mt-3">
        <h4 class="text-2xl font-bold tracking-tight text-slate-900 dark:text-white">2,847</h4>
        <p class="mt-1 flex items-center text-xs font-medium text-sky-600 dark:text-sky-400">
          <span>↗ +12.6%</span>
          <span class="ml-1 text-slate-400 dark:text-gray-500">from last month</span>
        </p>
      </div>
    </div>
    <!-- Blue Sparkline SVG -->
    <div class="mt-4 -mx-5 -mb-5 h-12">
      <svg class="h-full w-full" preserveAspectRatio="none" viewBox="0 0 100 30" fill="none">
        <path d="M0 22 Q 25 24, 50 19 T 100 10" stroke="#0EA5E9" stroke-width="2.5" stroke-linecap="round"/>
      </svg>
    </div>
  </div>

  <!-- Card 3: Churn Rate -->
  <div class="relative flex flex-col justify-between overflow-hidden rounded-xl border border-slate-200 bg-white p-5 shadow-sm dark:border-[#1F2937] dark:bg-[#111827]">
    <div>
      <div class="flex items-center justify-between">
        <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-gray-400">Churn Rate</span>
        <span class="flex h-8 w-8 items-center justify-center rounded-lg bg-purple-50 text-purple-600 dark:bg-purple-950/40 dark:text-purple-400">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/></svg>
        </span>
      </div>
      <div class="mt-3">
        <h4 class="text-2xl font-bold tracking-tight text-slate-900 dark:text-white">3.2%</h4>
        <p class="mt-1 flex items-center text-xs font-medium text-purple-600 dark:text-purple-400">
          <span>↘ -0.5%</span>
          <span class="ml-1 text-slate-400 dark:text-gray-500">from last month</span>
        </p>
      </div>
    </div>
    <!-- Purple Sparkline SVG -->
    <div class="mt-4 -mx-5 -mb-5 h-12">
      <svg class="h-full w-full" preserveAspectRatio="none" viewBox="0 0 100 30" fill="none">
        <path d="M0 16 Q 30 18, 60 25 T 100 23" stroke="#8B5CF6" stroke-width="2.5" stroke-linecap="round"/>
      </svg>
    </div>
  </div>

  <!-- Card 4: Trial Conversion -->
  <div class="relative flex flex-col justify-between overflow-hidden rounded-xl border border-slate-200 bg-white p-5 shadow-sm dark:border-[#1F2937] dark:bg-[#111827]">
    <div>
      <div class="flex items-center justify-between">
        <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-gray-400">Trial Conversion</span>
        <span class="flex h-8 w-8 items-center justify-center rounded-lg bg-amber-50 text-amber-600 dark:bg-amber-950/40 dark:text-amber-400">
          <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>
        </span>
      </div>
      <div class="mt-3">
        <h4 class="text-2xl font-bold tracking-tight text-slate-900 dark:text-white">24.8%</h4>
        <p class="mt-1 flex items-center text-xs font-medium text-amber-600 dark:text-amber-400">
          <span>↗ +2.3%</span>
          <span class="ml-1 text-slate-400 dark:text-gray-500">from last month</span>
        </p>
      </div>
    </div>
    <!-- Orange Sparkline SVG -->
    <div class="mt-4 -mx-5 -mb-5 h-12">
      <svg class="h-full w-full" preserveAspectRatio="none" viewBox="0 0 100 30" fill="none">
        <path d="M0 24 Q 30 22, 60 17 T 100 14" stroke="#F59E0B" stroke-width="2.5" stroke-linecap="round"/>
      </svg>
    </div>
  </div>
</div>
```

---

### Modul 4: Marketing Channels Table & Recent Signups List

```html
<!-- components/DataTables.html -->
<div class="grid grid-cols-1 gap-6 lg:grid-cols-12">
  <!-- Left Side (7 Cols): Marketing Channels Table -->
  <div class="rounded-xl border border-slate-200 bg-white p-5 shadow-sm lg:col-span-7 dark:border-[#1F2937] dark:bg-[#111827]">
    <h3 class="text-sm font-bold text-slate-900 dark:text-white">Marketing Channels</h3>
    <p class="text-xs text-slate-500 dark:text-gray-400">Visitor → signup conversion by acquisition channel.</p>

    <div class="mt-4 overflow-x-auto">
      <table class="w-full text-left text-xs">
        <thead>
          <tr class="border-b border-slate-100 text-[10px] font-semibold uppercase tracking-wider text-slate-400 dark:border-gray-800 dark:text-gray-500">
            <th class="py-2.5">Channel</th>
            <th class="py-2.5 text-right">Visitors</th>
            <th class="py-2.5 text-right">Signups</th>
            <th class="py-2.5 text-right">Conv.</th>
            <th class="py-2.5 text-right">CPA</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-slate-100 text-slate-700 dark:divide-gray-800 dark:text-gray-300">
          <tr>
            <td class="py-3 font-medium text-slate-900 dark:text-white">Organic Search</td>
            <td class="py-3 text-right">18,420</td>
            <td class="py-3 text-right">842</td>
            <td class="py-3 text-right">4.6%</td>
            <td class="py-3 text-right text-slate-400">—</td>
          </tr>
          <tr>
            <td class="py-3 font-medium text-slate-900 dark:text-white">Paid Ads</td>
            <td class="py-3 text-right">9,240</td>
            <td class="py-3 text-right">416</td>
            <td class="py-3 text-right">4.5%</td>
            <td class="py-3 text-right">$38</td>
          </tr>
          <tr>
            <td class="py-3 font-medium text-slate-900 dark:text-white">Social Media</td>
            <td class="py-3 text-right">6,830</td>
            <td class="py-3 text-right">241</td>
            <td class="py-3 text-right">3.5%</td>
            <td class="py-3 text-right">$24</td>
          </tr>
          <tr>
            <td class="py-3 font-medium text-slate-900 dark:text-white">Email</td>
            <td class="py-3 text-right">4,120</td>
            <td class="py-3 text-right">318</td>
            <td class="py-3 text-right">7.7%</td>
            <td class="py-3 text-right">$12</td>
          </tr>
          <tr>
            <td class="py-3 font-medium text-slate-900 dark:text-white">Referrals</td>
            <td class="py-3 text-right">3,290</td>
            <td class="py-3 text-right">198</td>
            <td class="py-3 text-right">6.0%</td>
            <td class="py-3 text-right">$18</td>
          </tr>
          <tr>
            <td class="py-3 font-medium text-slate-900 dark:text-white">Direct</td>
            <td class="py-3 text-right">5,640</td>
            <td class="py-3 text-right">167</td>
            <td class="py-3 text-right">3.0%</td>
            <td class="py-3 text-right text-slate-400">—</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- Right Side (5 Cols): Growth Targets Widget -->
  <div class="rounded-xl border border-slate-200 bg-white p-5 shadow-sm lg:col-span-5 dark:border-[#1F2937] dark:bg-[#111827]">
    <h3 class="text-sm font-bold text-slate-900 dark:text-white">Growth Targets</h3>
    <p class="text-xs text-slate-500 dark:text-gray-400">Quarterly goals at a glance.</p>

    <div class="mt-6 space-y-5">
      <!-- Target 1: MRR Target -->
      <div>
        <div class="flex items-center justify-between text-xs">
          <span class="font-semibold text-slate-800 dark:text-gray-200">MRR Target</span>
          <span class="font-mono text-slate-500 dark:text-gray-400">$48,200 / $50,000</span>
        </div>
        <div class="mt-2 h-2 w-full overflow-hidden rounded-full bg-slate-100 dark:bg-gray-800">
          <div class="h-full rounded-full bg-emerald-500" style="width: 96.4%"></div>
        </div>
      </div>

      <!-- Target 2: Active Users -->
      <div>
        <div class="flex items-center justify-between text-xs">
          <span class="font-semibold text-slate-800 dark:text-gray-200">Active Users</span>
          <span class="font-mono text-slate-500 dark:text-gray-400">2,847 / 3,300</span>
        </div>
        <div class="mt-2 h-2 w-full overflow-hidden rounded-full bg-slate-100 dark:bg-gray-800">
          <div class="h-full rounded-full bg-sky-500" style="width: 86.2%"></div>
        </div>
      </div>

      <!-- Target 3: Trial -> Paid Conv. -->
      <div>
        <div class="flex items-center justify-between text-xs">
          <span class="font-semibold text-slate-800 dark:text-gray-200">Trial → Paid Conv.</span>
          <span class="font-mono text-slate-500 dark:text-gray-400">24.8% / 30%</span>
        </div>
        <div class="mt-2 h-2 w-full overflow-hidden rounded-full bg-slate-100 dark:bg-gray-800">
          <div class="h-full rounded-full bg-amber-500" style="width: 82.6%"></div>
        </div>
      </div>
    </div>
  </div>
</div>
```

---

### Modul 5: Chat & Messaging Workspace (Screen 3)
Tata letak perpesanan multi-kolom dengan list kontak percakapan, status unread badge, dan state kosong (*empty state*).

```html
<!-- pages/ChatWorkspace.html -->
<div class="flex h-[calc(100vh-4rem)] w-full overflow-hidden bg-slate-50 dark:bg-[#0B0F17]">
  <!-- Column 1: Conversations List Panel -->
  <aside class="flex w-80 flex-col border-r border-slate-200 bg-white dark:border-[#1F2937] dark:bg-[#111827]">
    <div class="flex items-center justify-between border-b border-slate-100 p-4 dark:border-gray-800">
      <h2 class="text-xs font-bold uppercase tracking-wider text-slate-500 dark:text-gray-400">Chats</h2>
      <button class="flex h-7 w-7 items-center justify-center rounded-lg border border-slate-200 text-slate-600 hover:bg-slate-50 dark:border-gray-700 dark:text-gray-300">
        +
      </button>
    </div>

    <!-- Conversations Scrollable Area -->
    <div class="flex-1 overflow-y-auto divide-y divide-slate-100 dark:divide-gray-800">
      <!-- Chat Item 1 -->
      <button class="flex w-full items-start gap-3 p-3.5 text-left transition hover:bg-slate-50 dark:hover:bg-gray-800/60">
        <div class="flex h-9 w-9 shrink-0 items-center justify-center rounded-full bg-purple-100 text-xs font-bold text-purple-700 dark:bg-purple-950 dark:text-purple-300">
          JV
        </div>
        <div class="flex-1 overflow-hidden">
          <div class="flex items-center justify-between">
            <h4 class="truncate text-xs font-semibold text-slate-900 dark:text-white">Jennifer Valenzuela</h4>
            <span class="text-[10px] text-slate-400">Oct 29</span>
          </div>
          <p class="mt-0.5 truncate text-[11px] text-slate-500 dark:text-gray-400">Performance trip surface small south hun...</p>
        </div>
        <span class="flex h-4 w-4 shrink-0 items-center justify-center rounded-full bg-slate-900 text-[9px] font-bold text-white dark:bg-white dark:text-slate-950">
          1
        </span>
      </button>

      <!-- Chat Item 2 -->
      <button class="flex w-full items-start gap-3 p-3.5 text-left transition hover:bg-slate-50 dark:hover:bg-gray-800/60">
        <div class="flex h-9 w-9 shrink-0 items-center justify-center rounded-full bg-blue-100 text-xs font-bold text-blue-700 dark:bg-blue-950 dark:text-blue-300">
          LF
        </div>
        <div class="flex-1 overflow-hidden">
          <div class="flex items-center justify-between">
            <h4 class="truncate text-xs font-semibold text-slate-900 dark:text-white">Luis Fowler</h4>
            <span class="text-[10px] text-slate-400">Oct 29</span>
          </div>
          <p class="mt-0.5 truncate text-[11px] text-slate-500 dark:text-gray-400">Throw small break sometimes result Cong...</p>
        </div>
        <span class="flex h-4 w-4 shrink-0 items-center justify-center rounded-full bg-slate-900 text-[9px] font-bold text-white dark:bg-white dark:text-slate-950">
          1
        </span>
      </button>
    </div>
  </aside>

  <!-- Column 2: Empty State Pane -->
  <main class="flex flex-1 flex-col items-center justify-center p-8 text-center">
    <div class="flex h-16 w-16 items-center justify-center rounded-full bg-slate-100 text-slate-400 dark:bg-gray-800 dark:text-gray-500">
      <svg class="h-8 w-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"/>
      </svg>
    </div>
    <p class="mt-4 text-sm font-medium text-slate-500 dark:text-gray-400">Pick a conversation to start chatting.</p>
  </main>
</div>
```

---

### Modul 6: 503 Service Unavailable / Status Error Page (Screen 5)
Layar status error terpusat minimalis dengan indikator insiden sistem dan aksi recovery.

```html
<!-- pages/503.html -->
<div class="flex min-h-screen w-full flex-col items-center justify-center bg-slate-50 px-4 py-12 dark:bg-[#0B0F17]">
  <!-- Brand Top Logo -->
  <div class="mb-8 flex items-center gap-2.5">
    <div class="flex h-9 w-9 items-center justify-center rounded-lg bg-slate-900 text-white dark:bg-white dark:text-slate-950">
      <svg class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/>
        <polyline points="3.27 6.96 12 12.01 20.73 6.96"/>
        <line x1="12" y1="22.08" x2="12" y2="12"/>
      </svg>
    </div>
    <span class="text-lg font-bold tracking-tight text-slate-900 dark:text-white">Zenith</span>
  </div>

  <!-- Centered Error Card -->
  <div class="w-full max-w-md rounded-2xl border border-slate-200 bg-white p-8 text-center shadow-sm dark:border-[#1F2937] dark:bg-[#111827]">
    <!-- Big 503 Red Text -->
    <h1 class="text-6xl font-black tracking-tight text-red-600">503</h1>
    <h2 class="mt-3 text-lg font-bold text-slate-900 dark:text-white">Service Unavailable</h2>
    <p class="mt-2 text-xs leading-relaxed text-slate-500 dark:text-gray-400">
      We're temporarily offline. Our team has been notified and is on it. Please try again in a few moments.
    </p>

    <!-- Incident Detected Box -->
    <div class="mt-6 flex items-start gap-3 rounded-xl border border-slate-200 bg-slate-50/80 p-3.5 text-left dark:border-gray-800 dark:bg-gray-900/60">
      <div class="mt-0.5 text-slate-700 dark:text-gray-300">
        <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
      </div>
      <div>
        <p class="text-xs font-semibold text-slate-900 dark:text-white">Incident detected</p>
        <p class="text-[11px] font-mono text-slate-500 dark:text-gray-400">Reference: INC-2026-0042</p>
      </div>
    </div>

    <!-- Actions CTA -->
    <div class="mt-6 space-y-2.5">
      <button class="w-full rounded-lg bg-slate-900 py-2.5 text-xs font-semibold text-white transition hover:bg-slate-800 dark:bg-white dark:text-slate-950 dark:hover:bg-gray-100">
        Retry now
      </button>
      <button class="w-full rounded-lg border border-slate-200 bg-white py-2.5 text-xs font-semibold text-slate-700 transition hover:bg-slate-50 dark:border-gray-800 dark:bg-[#111827] dark:text-gray-300 dark:hover:bg-gray-800">
        Contact support
      </button>
    </div>
  </div>
</div>
```

---

### Modul 7: Charts Showcase Gallery (ApexCharts Configuration Specs)
Spesifikasi opsi konfigurasi ApexCharts untuk merender 8 varian visualisasi analitik pada Screen 4:

```javascript
// config/apexcharts-showcase.js

// 1. Bar Chart (Vertikal dengan nilai batang Jan - Sep)
export const barChartOptions = {
  chart: { type: 'bar', height: 260, toolbar: { show: false } },
  colors: ['#3B82F6'],
  plotOptions: { bar: { borderRadius: 4, columnWidth: '55%', dataLabels: { position: 'top' } } },
  series: [{ name: 'Value', data: [44, 55, 57, 56, 61, 58, 63, 60, 66] }],
  xaxis: { categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep'] }
};

// 2. Line Chart (Sessions vs Pageviews)
export const lineChartOptions = {
  chart: { type: 'line', height: 260, toolbar: { show: false } },
  colors: ['#3B82F6', '#10B981'],
  stroke: { curve: 'smooth', width: 2.5 },
  series: [
    { name: 'Sessions', data: [45, 52, 38, 45, 49, 100, 95] },
    { name: 'Pageviews', data: [35, 41, 62, 42, 38, 50, 48] }
  ],
  xaxis: { categories: ['M', 'T', 'W', 'T', 'F', 'S', 'S'] }
};

// 3. Area Chart (Gradient fill dengan titik data)
export const areaChartOptions = {
  chart: { type: 'area', height: 260, toolbar: { show: false } },
  colors: ['#3B82F6'],
  fill: { type: 'gradient', gradient: { shadeIntensity: 1, opacityFrom: 0.45, opacityTo: 0.05 } },
  stroke: { curve: 'smooth', width: 2 },
  series: [{ name: 'Users', data: [31, 40, 28, 51, 42, 109, 100, 90, 80, 75, 88, 95] }]
};

// 4. Donut Chart (Traffic Sources: Direct, Search, Social, Referral)
export const donutChartOptions = {
  chart: { type: 'donut', height: 260 },
  colors: ['#3B82F6', '#10B981', '#F59E0B', '#EF4444'],
  labels: ['Direct (28.0%)', 'Search (35.0%)', 'Social (26.1%)', 'Referral (10.8%)'],
  series: [28.0, 35.0, 26.1, 10.8],
  legend: { position: 'bottom' }
};

// 5. Radial Bar Chart (Multi-ring concentric progress)
export const radialBarOptions = {
  chart: { type: 'radialBar', height: 260 },
  colors: ['#10B981', '#F59E0B', '#EF4444', '#3B82F6'],
  plotOptions: { radialBar: { hollow: { size: '30%' } } },
  series: [70, 60, 50, 40],
  labels: ['Target A', 'Target B', 'Target C', 'Target D']
};

// 6. Heatmap Chart (7 Hari x 4 Minggu)
export const heatmapOptions = {
  chart: { type: 'heatmap', height: 260, toolbar: { show: false } },
  colors: ['#3B82F6'],
  series: [
    { name: 'W4', data: [{ x: 'Mon', y: 10 }, { x: 'Tue', y: 20 }, { x: 'Wed', y: 30 }, { x: 'Thu', y: 40 }, { x: 'Fri', y: 50 }, { x: 'Sat', y: 20 }, { x: 'Sun', y: 10 }] },
    { name: 'W3', data: [{ x: 'Mon', y: 20 }, { x: 'Tue', y: 40 }, { x: 'Wed', y: 10 }, { x: 'Thu', y: 30 }, { x: 'Fri', y: 40 }, { x: 'Sat', y: 30 }, { x: 'Sun', y: 20 }] },
    { name: 'W2', data: [{ x: 'Mon', y: 30 }, { x: 'Tue', y: 20 }, { x: 'Wed', y: 50 }, { x: 'Thu', y: 20 }, { x: 'Fri', y: 30 }, { x: 'Sat', y: 10 }, { x: 'Sun', y: 40 }] },
    { name: 'W1', data: [{ x: 'Mon', y: 15 }, { x: 'Tue', y: 25 }, { x: 'Wed', y: 35 }, { x: 'Thu', y: 45 }, { x: 'Fri', y: 25 }, { x: 'Sat', y: 35 }, { x: 'Sun', y: 15 }] }
  ]
};
```

---

## 5. ACCESSIBILITY (A11Y) & CODING STANDARDS
- **Semantic Tags**: Selalu gunakan `<header>`, `<aside>`, `<main>`, `<nav>`, `<section>`, dan `<table>` secara semantik.
- **Form Controls & Inputs**: Sertakan atribut `aria-label` atau label pendamping eksplisit untuk semua input search dan button toggle.
- **High Contrast**: Teks di atas warna aksen wajib memenuhi standar rasio kontras 4.5:1 untuk teks normal dan 3:1 untuk teks besar.
- **Production Cleanliness**: Jangan menyematkan komentar pemalas seperti `// lengkapi sendiri`. Seluruh markup dan kode styling harus disajikan secara lengkap, siap dijalankan, dan memiliki anotasi nama file di baris pertama.
