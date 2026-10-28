---
name: food-delivery-ui
description: >-
  Spesialis arsitektur dan perancangan antarmuka aplikasi pesan-antar makanan dan pasar koki (Food Delivery & Chef Marketplace Mobile App)
  dengan arsitektur Dual-Engine dinamis (Flutter Dart & React Native / React Tailwind).
  Menyediakan implementasi visual 1:1 untuk 2 ekosistem lengkap (Customer App 14+ layar & Chef Partner App 10 layar):
  Onboarding, Auth & OTP, Lokasi, Home & Resto, Search & Filter, Detail Makanan & Size/Ingredients, Promo Modal, Cart,
  Payment & Add Card, Order Success, Delivery Tracking, Chef Dashboard & Revenue Chart, Menu Management, serta Profil & Withdrawal.
---

# Food Delivery & Chef Marketplace Mobile UI Kit Specialist (Dual-Engine)

Modul keahlian antarmuka mobile dinamis yang mendukung pembuatan komponen dan layar aplikasi pesan-antar makanan dan manajemen koki (*Food Delivery & Chef Marketplace*) modern baik di lingkungan **Flutter (Dart)** maupun **React / React Native (TypeScript & Tailwind)**.

Panduan lengkap, design tokens resmi (Brand Orange `#FF7622`, Midnight Dark `#121223`), serta blueprint komponen siap pakai tersedia di [prompt.md](./prompt.md).

## Aturan Utama (Invariant Rules)
- Patuhi aturan komunikasi direct di [base_prompt.md](../../../rule/base_prompt.md).
- Patuhi protokol perencanaan sebelum eksekusi kode implementasi di [project-workflow.md](../../../rule/project-workflow.md).
- **Production-Ready UI**: Dilarang memotong kode komponen visual dengan komentar malas (`// implement widget here`). Seluruh kode widget dan styling harus lengkap, responsif, dan siap dikompilasi.

---

## 2 Ekosistem Terpadu yang Didukung (24+ Layar)

### A. Customer Food Delivery App (14+ Screens)
1. **Splash & Onboarding (3 Slides)**:
   - Splash screen minimalis dengan cloche logo *"Food"*.
   - Slide 1: *"All your favorites"* (Ilustrasi pesan makanan dari rumah, dots oranye, tombol Next, Skip).
   - Slide 2: *"Order from chosen chef"* (Ilustrasi koki memasak hidangan istimewa).
   - Slide 3: *"Free delivery offers"* (Ilustrasi kurir bersepeda motor, tombol *Get Started*).
2. **Autentikasi & Verifikasi**:
   - **Log In Screen**: Header dark wave aesthetic, input Email & Password dengan toggle intip kata sandi, checkbox Remember me, Forgot Password, tombol oranye *Log In*, dan social login (Facebook, Twitter, Apple).
   - **Sign Up Screen**: Input Nama, Email, Password, dan Re-type Password.
   - **Verification Screen**: 4-box OTP input code (`[2] [0] [1] [5]`), counter *"Resend in 50sec"*, tombol *Verify*, dan custom numeric keypad (1-9, 0, backspace).
   - **Forgot Password**: Input Email pemulihan dan tombol *Send Code*.
3. **Location Permission Screen**:
   - Visual map circular badge dengan pin lokasi oranye di tengah.
   - Headline: *"DFOOD will access your location only while using the app"*.
   - Tombol utama: *"Access Location"*.
4. **Home / Discovery Screen**:
   - Header dinamis: Pilihan lokasi (*"DELIVER TO: Halal Lab office"*) dan icon cart dengan badge notifikasi angka.
   - Greeting personal: *"Hey Halal, Good Afternoon!"*.
   - Search bar terintegrasi dengan icon pencarian.
   - Category selector ganda: Tampilan horizontal pills (*All*, *Hot Dog*, *Burger*, *Pizza*) atau Grid card visual (*Pizza Starting $70*, *Burger Starting $50*).
   - Kartu restoran buka (*Open Restaurants*): Hero image makanan, nama restoran (*Rose Garden Restaurant*), kategori tags (*Burger - Chicken - Rice - Wings*), rating bintang (4.7), free delivery badge, dan estimasi waktu (20 min).
5. **Search & Filter Modal**:
   - Input pencarian aktif dengan tombol hapus (clear).
   - Bagian *Recent Keywords* (Burger, Sandwich, Pizza) dalam bentuk pills.
   - Bagian *Suggested Restaurants* (Pansi Restaurant, American Spicy Burger Shop) dengan avatar thumbnail.
   - Bagian *Popular Fast Food* (European Pizza, Buffalo Pizza).
   - Filter Bottom Sheet: Pilihan Offers (Delivery, Pick Up, Offer, Online payment), Deliver Time (10-15 min, 20 min, 30 min), Pricing ($, $$, $$$), Star Rating (1-5 stars), dan tombol *Filter*.
6. **Restaurant View Screen**:
   - Cover foto dapur/koki restoran (*Spicy Restaurant*).
   - Rating 4.7, Free delivery badge, estimasi 20 min.
   - Tab navigasi kategori hidangan (*Burger*, *Sandwich*, *Pizza*).
   - Daftar produk resto (*Burger (10)*) lengkap dengan harga dan tombol tambah `+`.
7. **Food Details Screen**:
   - Hero image hidangan melengkung (*Pizza Calzone European*) dengan floating favorite heart icon.
   - Chip nama restoran (*Uttora Coffee House*).
   - Rating 4.7, Free delivery, waktu 20 min.
   - Size selector pills: `10"`, `14"` (aktif oranye), `16"`.
   - Ingredients badges dengan icon (Garam, Ayam, Bawang, Bawang Putih, Paprika).
   - Sticky bottom action bar: Harga ($32), quantity stepper (`- 2 +`), dan tombol pesan.
8. **Promo Voucher Popup Modal**:
   - Modal kartu oranye cerah: *"Hurry Offers! #1243CD2 Use the coupon get 25% discount"*.
   - Tombol aksi *"GOT IT"* dan tombol close `X`.
9. **Cart & Checkout Screen**:
   - Daftar item makanan dengan opsi hapus merah dan quantity stepper.
   - Kartu Delivery Address (*2118 Thornridge Cir. Syracuse*) dengan tombol *Edit*.
   - Rincian biaya (*Total $96, Breakdown >*).
   - Tombol aksi utama: *"PLACE ORDER"*.
10. **Payment & Add Card Flow**:
    - Pilihan metode: Cash, Visa, Mastercard (aktif dengan badge centang), Paypal.
    - Card preview: Kartu Mastercard visual oranye/merah gradient.
    - Form *Add Card*: Card Holder Name, Card Number terformat (`2134 L--- ----`), Expire Date (`mm/yyyy`), CVC (`***`), dan tombol *Add & Make Payment*.
11. **Order Success Screen**:
    - Ilustrasi dompet terbuka penuh uang, kartu kredit, koin, dan konfeti perayaan.
    - Headline: *"Congratulations!"* - *"You successfully made a payment, enjoy our service!"*.
    - Tombol aksi: *"TRACK ORDER"*.
12. **Delivery Tracking Screen**:
    - Tampilan peta rute real-time dari restoran ke alamat pelanggan dengan polyline oranye.
    - Floating bottom sheet: Profil restoran (*Uttora Coffee House*), daftar item (*2x Burger, 4x Sandwich*), dan estimasi waktu sampai.

---

### B. Chef / Merchant Partner App (10 Screens)
1. **Chef Dashboard Screen**:
   - Header profil koki dengan dropdown lokasi dapur.
   - Stat Cards KPI ganda: *20 RUNNING ORDERS* dan *05 ORDER REQUEST*.
   - Grafik garis pendapatan *Total Revenue ($2,241)* dengan toggle filter harian/mingguan.
   - Ulasan ringkas (*Rating 4.9 dari 20 Ulasan*).
   - Galeri *Popular Items This Week*.
   - Bottom Navigation Bar 5-menu dengan floating plus button oranye di tengah.
2. **Running Orders Bottom Sheet**:
   - Daftar pesanan aktif (*20 Running Orders*): Foto hidangan, nama menu (*Chicken Thai Biriyani*, *Chicken Bhuna*), ID order, harga, serta tombol aksi *Done* (oranye) dan *Cancel* (outline).
3. **Menu Management (My Food List)**:
   - Filter tab kategori masakan (*All*, *Breakfast*, *Lunch*, *Dinner*).
   - Daftar kartu hidangan chef dengan rating, harga, dan tombol opsi `...`.
4. **Food Details (Chef Perspective)**:
   - Foto hero masakan, chip tag (*Breakfast*, *Delivery*), harga, ulasan rating (4.9 dari 10 reviews), daftar bahan (Ingredients), deskripsi hidangan, dan tombol *Edit*.
5. **Add New Food Item Screen**:
   - Form pembuatan menu baru: Item Name, area upload Foto/Video hidangan, Price ($), checkbox pemenuhan (*Pick up* vs *Delivery*).
   - Multi-select chips untuk bahan (*Ingredients: Basic, Fruit*).
   - Input Details/Deskripsi dan tombol simpan oranye *"SAVE CHANGES"*.
6. **Notifikasi & Chat Pelanggan**:
   - Tab switch ganda: *Notifications* vs *Messages (3)*.
   - Notifikasi pesanan baru (contoh: *"Tanbir Ahmed placed a new order 20 min ago"*).
   - Daftar thread percakapan dengan avatar pelanggan, pesan terakhir, waktu, dan badge unread counter.
7. **Customer Reviews Screen**:
   - Daftar ulasan pelanggan (*Great Food and Service*, *Awesome and Nice*) lengkap dengan avatar, tanggal, dan 5 bintang rating.
8. **Chef Profile & Earnings / Withdrawal**:
   - Header oranye cerah *My Profile*: *Available Balance $500.00* dan tombol aksi *Withdraw*.
   - Menu daftar: *Personal Info*, *Settings*, *Withdrawal History*, *Number of Orders (29K)*, *User Reviews*, *Log Out*.
9. **Withdrawal Success Modal**:
   - Dialog perayaan dengan checkmark oranye dan konfeti bintang.
   - Headline: *"Withdraw Successful"*.
   - Tombol konfirmasi: *"OK"*.

