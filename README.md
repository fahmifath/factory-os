<div align="center">

# 🏭 FactoryOS ERP

**Sistem Enterprise Resource Planning untuk Perusahaan Manufaktur**

[![Laravel](https://img.shields.io/badge/Laravel-11.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![Vue.js](https://img.shields.io/badge/Vue.js-3.x-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)](https://vuejs.org)
[![Inertia](https://img.shields.io/badge/Inertia.js-1.x-9553E9?style=for-the-badge&logo=inertia&logoColor=white)](https://inertiajs.com)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)
[![Redis](https://img.shields.io/badge/Redis-7.x-DC382D?style=for-the-badge&logo=redis&logoColor=white)](https://redis.io)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

<br/>

> FactoryOS adalah sistem Mini ERP berbasis web yang dirancang khusus untuk kebutuhan perusahaan manufaktur skala menengah. Mengelola seluruh operasional bisnis dari satu platform — mulai dari produksi, gudang, keuangan, hingga penggajian karyawan.

<br/>

[📖 Dokumentasi](#-dokumentasi) · [🚀 Instalasi](#-instalasi) · [✨ Fitur](#-fitur-utama) · [🗂️ Modul](#️-modul) · [👥 Role](#-role--akses)

</div>

---

## 📋 Daftar Isi

- [Tentang Proyek](#-tentang-proyek)
- [Fitur Utama](#-fitur-utama)
- [Tech Stack](#-tech-stack)
- [Modul](#️-modul)
- [Role & Akses](#-role--akses)
- [Alur Sistem](#-alur-sistem)
- [Database](#-database)
- [Instalasi](#-instalasi)
- [Konfigurasi](#-konfigurasi)
- [Penggunaan](#-penggunaan)
- [Screenshot](#-screenshot)
- [Kontribusi](#-kontribusi)
- [Lisensi](#-lisensi)

---

## 🏭 Tentang Proyek

FactoryOS hadir sebagai solusi terpadu untuk perusahaan manufaktur yang ingin mendigitalisasi proses bisnisnya. Sistem ini mengintegrasikan 6 modul utama yang saling terhubung secara real-time, menggantikan penggunaan spreadsheet yang tersebar dan proses manual yang rawan kesalahan.

### Permasalahan yang Diselesaikan

| ❌ Sebelum FactoryOS | ✅ Sesudah FactoryOS |
|---|---|
| Stok bahan baku dicatat manual di Excel | Stok terupdate otomatis setiap transaksi |
| Laporan keuangan dibuat akhir bulan | Laporan real-time kapan saja |
| Slip gaji dihitung manual | Payroll otomatis berdasarkan absensi |
| Tidak ada approval workflow | Multi-step approval dengan notifikasi |
| Data tersebar di berbagai file | Satu platform terintegrasi |
| Tidak ada audit trail | Setiap aksi tercatat di activity log |

---

## ✨ Fitur Utama

- 🔐 **Role-Based Access Control** — 6 role dengan permission granular per modul
- 📦 **Multi-Gudang** — Kelola beberapa gudang sekaligus dengan transfer stok antar lokasi
- 🏗️ **Bill of Materials (BOM)** — Definisi resep produk dengan validasi stok otomatis
- 💰 **Double-Entry Accounting** — Sistem akuntansi dengan jurnal otomatis setiap transaksi
- 👷 **Payroll Otomatis** — Kalkulasi gaji berdasarkan data absensi real-time
- 📊 **Dashboard Analytics** — Visualisasi data bisnis secara real-time
- 🔔 **Notifikasi Real-time** — Alert stok kritis, approval pending, invoice jatuh tempo
- 📄 **Export PDF & Excel** — Semua laporan bisa diunduh dalam format PDF dan Excel
- 📧 **Scheduled Report** — Laporan bulanan dikirim otomatis via email ke manajemen
- 🕵️ **Activity Log** — Setiap aksi user tercatat lengkap untuk keperluan audit
- 🔑 **2FA Authentication** — Two-factor authentication untuk role sensitif (Finance, Admin)
- 📱 **Responsive UI** — Antarmuka yang nyaman diakses dari desktop maupun mobile

---

## 🛠️ Tech Stack

### Backend
| Package | Versi | Fungsi |
|---|---|---|
| [Laravel](https://laravel.com) | 11.x | Core Framework |
| [Spatie Permission](https://spatie.be/docs/laravel-permission) | 6.x | RBAC & Permission |
| [Spatie Activity Log](https://spatie.be/docs/laravel-activitylog) | 4.x | Audit Trail |
| [Laravel Sanctum](https://laravel.com/docs/sanctum) | 4.x | API Authentication |
| [Laravel Reverb](https://reverb.laravel.com) | 1.x | WebSocket Real-time |
| [Maatwebsite Excel](https://laravel-excel.com) | 3.x | Export Excel |
| [DomPDF](https://github.com/barryvdh/laravel-dompdf) | 2.x | Generate PDF |
| [Laravel Queue](https://laravel.com/docs/queues) | — | Background Jobs |

### Frontend
| Package | Versi | Fungsi |
|---|---|---|
| [Vue.js](https://vuejs.org) | 3.x | Frontend Framework |
| [Inertia.js](https://inertiajs.com) | 1.x | SPA tanpa API terpisah |
| [Tailwind CSS](https://tailwindcss.com) | 3.x | Styling |
| [ApexCharts](https://apexcharts.com) | 3.x | Grafik & Visualisasi |

### Infrastructure
| Teknologi | Fungsi |
|---|---|
| MySQL 8.0 | Database utama |
| Redis 7.x | Cache, Queue, Session |
| Vite | Asset Bundler |

---

## 🗂️ Modul

### 🔐 1. Auth & Access Control

Mengelola autentikasi dan otorisasi seluruh pengguna sistem.

- Registrasi & login dengan email/password
- Two-factor authentication (2FA) via OTP
- Session management & remember me
- Permission-based access per modul (`inventory.view`, `payroll.approve`, dll.)
- Activity log setiap aksi user (login, create, update, delete, approve)
- Reset password via email

---

### 📦 2. Inventory & Gudang

Pengelolaan stok bahan baku dan barang jadi secara komprehensif.

**Master Data**
- Manajemen gudang (Gudang Bahan Baku, Gudang Barang Jadi, Transit)
- Data bahan baku dengan satuan unit, kategori, dan harga terakhir
- Setting minimum stok untuk trigger alert otomatis

**Purchase Order (PO)**
- Buat PO ke supplier dengan approval flow: `Draft → Approved → Sent → Received`
- Item PO dengan tracking qty dipesan vs qty diterima
- Goods Receipt dengan upload dokumen surat jalan
- Otomatis update stok dan buat jurnal akuntansi saat GR dibuat

**Stock Management**
- Log pergerakan stok setiap transaksi (masuk, keluar, transfer, adjustment)
- Transfer stok antar gudang
- Rekap stok harian/mingguan
- Alert otomatis saat stok di bawah minimum

---

### 🏗️ 3. Production Management

Pengelolaan proses produksi dari perencanaan hingga barang jadi.

**Bill of Materials (BOM)**
- Definisi resep produk: Produk A = Bahan X (2kg) + Bahan Y (500ml)
- Versioning BOM (v1.0, v1.1, v2.0)
- Setting persentase waste per bahan baku
- Kalkulasi kebutuhan bahan otomatis berdasarkan target produksi

**Work Order (WO)**
- Buat WO berdasarkan BOM dengan validasi ketersediaan stok
- Status tracking: `Planned → In Progress → Quality Check → Done`
- Input progress produksi harian oleh operator
- Catat downtime mesin beserta alasannya
- Saat WO selesai: stok bahan baku berkurang otomatis, stok barang jadi bertambah
- Hitung Harga Pokok Produksi (HPP) otomatis

---

### 💰 4. Finance & Akuntansi

Sistem keuangan dengan double-entry bookkeeping.

**Chart of Accounts (COA)**
- Struktur akun hierarki: Aset, Liabilitas, Ekuitas, Pendapatan, Beban
- Kode akun terstruktur (1xxx Aset, 2xxx Liabilitas, dll.)
- Header account dan detail account

**Jurnal & Transaksi**
- Double-entry bookkeeping: setiap transaksi membuat jurnal otomatis
- Jurnal manual untuk transaksi khusus
- Validasi: total debit harus selalu sama dengan total kredit

**Invoice & Pembayaran**
- Invoice penjualan (Sales) dan pembelian (Purchase)
- Tracking status pembayaran: `Unpaid → Partial → Paid → Overdue`
- Partial payment support
- Alert invoice jatuh tempo H-1 dan H-0

**Laporan Keuangan**
- Laporan Laba Rugi (Profit & Loss)
- Neraca Keuangan (Balance Sheet)
- Laporan Arus Kas (Cash Flow)
- Semua laporan bisa difilter per periode dan diekspor ke PDF/Excel

---

### 👷 5. HR & Payroll

Pengelolaan sumber daya manusia dan penggajian.

**Data Karyawan**
- Profil karyawan lengkap (NIK, jabatan, departemen, BPJS, NPWP)
- Manajemen kontrak: PKWT, PKWTT, Magang dengan notifikasi kontrak akan berakhir
- Upload dokumen karyawan (KTP, Ijazah, Kontrak kerja)
- Riwayat jabatan dan riwayat gaji

**Absensi**
- Input absensi harian (Hadir, Izin, Sakit, Alpha, Cuti)
- Pencatatan jam masuk dan jam keluar
- Hitung lembur otomatis berdasarkan jam kerja
- Import absensi massal via CSV/Excel
- Rekap kehadiran bulanan per karyawan dan per departemen

**Cuti & Izin**
- Pengajuan cuti dengan approval flow: `Pending → Approved/Rejected`
- Saldo cuti tahunan otomatis terpotong saat cuti diapprove
- Jenis cuti: Tahunan, Sakit, Melahirkan, Darurat
- Riwayat pengajuan cuti

**Payroll**
- Generate payroll bulanan berdasarkan data absensi
- Komponen gaji: Gaji Pokok, Tunjangan Jabatan, Tunjangan Makan, Lembur
- Komponen potongan: Absen, BPJS Ketenagakerjaan, BPJS Kesehatan, PPh 21
- Rumus: `Take Home Pay = Gaji Pokok + Tunjangan + Lembur - Potongan`
- Approval flow payroll: `Draft → Submitted → Approved → Paid`
- Slip gaji PDF per karyawan
- Export Excel untuk transfer bank massal

---

### 📊 6. Dashboard & Laporan

Pusat informasi dan analitik bisnis.

**Executive Dashboard**
- Revenue vs Cost bulan berjalan (grafik perbandingan)
- Jumlah produksi harian 30 hari terakhir
- Top 5 produk terlaris bulan ini
- Stok kritis yang perlu segera direorder
- Outstanding invoice (tagihan belum dibayar)
- Ringkasan payroll bulan berjalan

**Laporan per Modul**
- Laporan Stok & Pergerakan Barang
- Laporan Efisiensi Produksi (target vs aktual, reject rate)
- Laporan Laba Rugi, Neraca, Arus Kas
- Laporan Payroll per Departemen
- Laporan Rekap Absensi

**Notifikasi & Scheduled Jobs**
- Real-time notification via Laravel Reverb (WebSocket)
- Scheduled report: setiap tanggal 1 kirim ringkasan bulan lalu ke email manajemen
- Alert stok kritis, invoice jatuh tempo, kontrak karyawan akan berakhir

---

## 👥 Role & Akses

FactoryOS memiliki **6 role** dengan hak akses yang berbeda pada setiap modul.

### 🔴 Super Admin

**Deskripsi:** Pengguna dengan akses penuh ke seluruh sistem. Biasanya diisi oleh IT Manager atau pemilik sistem.

**Tanggung Jawab:**
- Setup awal sistem (master data: departemen, jabatan, gudang, COA)
- Membuat dan mengelola akun user serta assign role
- Memantau activity log seluruh pengguna
- Mengakses semua modul dan semua laporan
- Melakukan konfigurasi sistem (pengaturan email, notifikasi, dll.)

**Akses Khusus:**
- Satu-satunya role yang bisa membuat/menghapus user
- Bisa override approval yang sudah disubmit
- Akses ke seluruh activity log

---

### 🟡 Finance

**Deskripsi:** Staf atau manager keuangan yang mengelola seluruh aspek finansial perusahaan.

**Tanggung Jawab:**
- Approve Purchase Order yang diajukan Warehouse
- Membuat dan mengelola invoice penjualan & pembelian
- Input pembayaran dari customer dan ke supplier
- Membuat jurnal manual jika diperlukan
- Approve payroll yang disubmit HRD
- Melihat dan mengekspor laporan keuangan (P&L, Neraca, Cash Flow)

**Akses Khusus:**
- Satu-satunya role (selain Super Admin) yang bisa approve PO
- Akses ke seluruh modul Finance & Akuntansi
- Menerima notifikasi invoice jatuh tempo dan PO menunggu approval

---

### 🟠 Warehouse (Kepala Gudang)

**Deskripsi:** Penanggung jawab operasional gudang dan pengelolaan stok bahan baku.

**Tanggung Jawab:**
- Memantau stok bahan baku di semua gudang
- Membuat Purchase Order saat stok mendekati minimum
- Membuat Goods Receipt saat barang dari supplier datang
- Melakukan transfer stok antar gudang
- Melakukan stock adjustment jika ada selisih
- Menerima notifikasi stok kritis secara real-time

**Akses Khusus:**
- Bisa membuat PO tapi tidak bisa approve (harus Finance)
- Akses penuh ke modul Inventory & Gudang
- Menerima notifikasi otomatis saat stok di bawah minimum

---

### 🟢 Production Manager

**Deskripsi:** Manager yang merencanakan dan mengawasi seluruh proses produksi.

**Tanggung Jawab:**
- Membuat dan mengelola Bill of Materials (BOM)
- Membuat Work Order berdasarkan target produksi
- Memantau progress Work Order secara real-time
- Submit WO ke tahap Quality Check
- Approve atau reject hasil QC
- Melihat laporan efisiensi dan produktivitas produksi
- Menerima notifikasi saat stok bahan baku tidak mencukupi untuk WO

**Akses Khusus:**
- Satu-satunya role yang bisa membuat dan mengelola BOM
- Bisa approve/reject hasil Quality Check
- Akses ke laporan produksi dan efisiensi mesin

---

### 🔵 HRD

**Deskripsi:** Staf atau manager HR yang mengelola data karyawan dan proses penggajian.

**Tanggung Jawab:**
- Input dan mengelola data karyawan (onboarding, mutasi, resign)
- Mengelola kontrak karyawan dan memantau tanggal berakhir
- Input atau verifikasi data absensi harian
- Approve atau reject pengajuan cuti karyawan
- Generate payroll bulanan
- Submit payroll ke Finance untuk approval
- Mencetak slip gaji dan membuat file transfer bank

**Akses Khusus:**
- Akses penuh ke data seluruh karyawan
- Bisa generate dan submit payroll (tapi tidak bisa approve sendiri)
- Menerima notifikasi kontrak karyawan yang akan berakhir dalam 30 hari
- Akses ke laporan rekap absensi dan payroll

---

### ⚪ Operator

**Deskripsi:** Karyawan level produksi yang melakukan input data harian di lantai produksi.

**Tanggung Jawab:**
- Input progress produksi harian pada Work Order yang ditugaskan
- Catat downtime mesin (durasi dan alasan)
- Lihat Work Order yang sedang berjalan
- Lihat data absensi dan slip gaji milik sendiri

**Akses Khusus:**
- Akses paling terbatas — hanya bisa melihat dan input data milik sendiri
- Tidak bisa membuat, mengedit, atau menghapus data master
- Hanya bisa melihat Work Order yang di-assign kepadanya

---

## 🔄 Alur Sistem

### Alur Pembelian Bahan Baku
```
Warehouse (stok kritis)
    → Buat PO [Draft]
    → Finance Approve [Approved]
    → Kirim ke Supplier [Sent]
    → Barang datang → Goods Receipt
    → Stok otomatis bertambah
    → Jurnal hutang terbuat otomatis
    → Finance input pembayaran
    → Hutang lunas ✅
```

### Alur Produksi
```
Production Manager
    → Buat Work Order (pilih BOM)
    → Sistem validasi stok bahan baku
    → WO In Progress → Operator input progress harian
    → WO selesai → Submit ke QC
    → QC Approved → Stok bahan baku berkurang, stok barang jadi bertambah ✅
```

### Alur Penggajian
```
[Sepanjang bulan] Absensi karyawan dicatat
    → [Akhir bulan] HRD generate payroll
    → Sistem kalkulasi otomatis (gaji + tunjangan + lembur - potongan)
    → HRD submit ke Finance
    → Finance approve → Status: Approved
    → Slip gaji PDF & file Excel transfer bank siap diunduh ✅
```

---

## 🗄️ Database

Sistem menggunakan **30 tabel** yang terbagi dalam 6 modul:

```
┌─────────────────────────────────────────────────────────┐
│  AUTH          │ users, roles, permissions,              │
│                │ role_user, activity_logs                │
├─────────────────────────────────────────────────────────┤
│  HR & PAYROLL  │ departments, positions, employees,      │
│                │ contracts, attendances, leave_requests,  │
│                │ payrolls, payroll_items                  │
├─────────────────────────────────────────────────────────┤
│  INVENTORY     │ warehouses, raw_materials,              │
│                │ stock_movements, suppliers,              │
│                │ purchase_orders, po_items,               │
│                │ goods_receipts                           │
├─────────────────────────────────────────────────────────┤
│  PRODUCTION    │ products, bill_of_materials,            │
│                │ bom_items, work_orders, wo_logs          │
├─────────────────────────────────────────────────────────┤
│  FINANCE       │ accounts, journal_entries,              │
│                │ journal_lines, invoices, payments        │
└─────────────────────────────────────────────────────────┘
```

> Lihat ERD lengkap di [`docs/erd.html`](docs/erd.html)

---

## 🚀 Instalasi

### Prasyarat

Pastikan environment kamu sudah memenuhi requirement berikut:

- PHP >= 8.2
- Composer >= 2.x
- Node.js >= 20.x & NPM >= 10.x
- MySQL >= 8.0
- Redis >= 7.x

### Langkah Instalasi

**1. Clone repository**
```bash
git clone https://github.com/username/factoryos.git
cd factoryos
```

**2. Install dependencies**
```bash
composer install
npm install
```

**3. Setup environment**
```bash
cp .env.example .env
php artisan key:generate
```

**4. Konfigurasi database di `.env`**
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=factoryos
DB_USERNAME=root
DB_PASSWORD=your_password

REDIS_HOST=127.0.0.1
REDIS_PORT=6379
```

**5. Jalankan migration & seeder**
```bash
php artisan migrate
php artisan db:seed
```

**6. Build assets**
```bash
npm run build
# atau untuk development:
npm run dev
```

**7. Jalankan server**
```bash
php artisan serve
```

**8. Jalankan queue worker (terminal terpisah)**
```bash
php artisan queue:work
```

**9. Jalankan WebSocket server (terminal terpisah)**
```bash
php artisan reverb:start
```

Akses aplikasi di: `http://localhost:8000`

---

## ⚙️ Konfigurasi

### Default Login Setelah Seeder

| Role | Email | Password |
|---|---|---|
| Super Admin | `admin@factoryos.com` | `password` |
| Finance | `finance@factoryos.com` | `password` |
| Warehouse | `warehouse@factoryos.com` | `password` |
| Production Manager | `production@factoryos.com` | `password` |
| HRD | `hrd@factoryos.com` | `password` |
| Operator | `operator@factoryos.com` | `password` |

> ⚠️ **Ganti semua password default sebelum deploy ke production!**

 
## 🤝 Kontribusi

Kontribusi sangat diterima! Silakan ikuti langkah berikut:

1. Fork repository ini
2. Buat branch fitur baru: `git checkout -b feature/nama-fitur`
3. Commit perubahan: `git commit -m 'feat: tambah fitur X'`
4. Push ke branch: `git push origin feature/nama-fitur`
5. Buat Pull Request

### Konvensi Commit
```
feat:     Fitur baru
fix:      Perbaikan bug
docs:     Perubahan dokumentasi
style:    Formatting, missing semi-colons, dll.
refactor: Refactoring kode
test:     Menambah atau memperbaiki test
chore:    Pembaruan build process, dll.
```

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

