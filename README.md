<div align="center">

<img src="public/img/mbas-logo.png" alt="Logo MBAS" width="140">

# SPKP MBAS

### Sistem Pengurusan Kesihatan Persekitaran

*Sistem digital untuk pengurusan aktiviti kesihatan persekitaran*
*Majlis Bandaraya Alor Setar (MBAS)*

<br>

![Laravel](https://img.shields.io/badge/Laravel-11-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.3-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind-CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Alpine.js](https://img.shields.io/badge/Alpine.js-3-8BC0D0?style=for-the-badge&logo=alpine.js&logoColor=black)
![Claude AI](https://img.shields.io/badge/AI-Claude-D97757?style=for-the-badge&logo=anthropic&logoColor=white)

![License](https://img.shields.io/badge/License-Proprietary-red?style=flat-square)
![Status](https://img.shields.io/badge/Status-Production-success?style=flat-square)
![Version](https://img.shields.io/badge/Version-1.0-blue?style=flat-square)
![PWA](https://img.shields.io/badge/PWA-Ready-purple?style=flat-square)

</div>

---

## 📖 Tentang Sistem

**SPKP MBAS** adalah sistem web full-stack yang dibangunkan untuk **Bahagian Kawalan Penyakit & Promosi Kesihatan**, Jabatan Kesihatan Persekitaran, MBAS. Sistem ini mendigitalkan aliran kerja bahagian yang sebelumnya berasaskan kertas — daripada pendaftaran aktiviti, kelulusan Ketua Bahagian, tandatangan digital, sehingga penjanaan laporan bulanan.

Dibangunkan sepanjang **Latihan Industri di Bahagian Teknologi Maklumat MBAS** (April – Julai 2026).

---

## ✨ Ciri Utama

<table>
<tr>
<td width="50%">

### 📋 Pengurusan Aktiviti
- Pendaftaran aktiviti lapangan
- Upload gambar dengan **GPS watermark automatik**
- Template aktiviti untuk kelajuan
- Kalendar & timeline view

### ✅ Workflow Kelulusan
- KB sahkan / pulangkan laporan
- **SLA countdown** untuk prioritize
- Bulk approve untuk laporan banyak
- Komen threaded pada setiap rekod

### ✍️ Tandatangan Digital
- Canvas untuk KB tandatangan
- Auto-embed ke laporan PDF
- Audit trail penuh

</td>
<td width="50%">

### 🤖 Bot Helpline AI
- Integrasi **Anthropic Claude API**
- Auto-detect modul aktif dari sidebar
- Small-talk handler (mesra pengguna)
- Typewriter effect untuk pengalaman semulajadi
- Fallback ke keyword search

### 📊 Laporan & Analitik
- Auto-generate laporan bulanan
- Chart trend aktiviti
- Export PDF & Excel
- Dashboard KPI

### 🔐 Sekuriti
- 3 peringkat role (Admin, KB, PPKP)
- Role-based access control
- Full audit trail
- Password hashing (bcrypt)

</td>
</tr>
</table>

---

## 🛠️ Tech Stack

<div align="center">

| Kategori | Teknologi |
|:---:|:---|
| **Backend** | Laravel 11, PHP 8.3, Eloquent ORM |
| **Frontend** | Blade, Alpine.js, TailwindCSS, Vanilla JS |
| **Database** | MySQL 8, utf8mb4 |
| **AI** | Anthropic Claude (Haiku 4.5) |
| **PWA** | Service Worker, Web Manifest |
| **PDF** | DomPDF |
| **Dev Environment** | Laragon Full |
| **Tools** | Composer, Git, HeidiSQL, VS Code |

</div>

---

## 🚀 Pemasangan Cepat

### Prasyarat

- **Laragon Full** ([Download](https://laragon.org/download/)) — bundled dengan PHP 8.3 + MySQL 8 + Composer
- **VS Code** (optional)
- **Git**

### Cara 1: One-Click Setup (Windows) ⭐

```powershell
git clone https://github.com/USERNAME/spkp-mbas.git
cd spkp-mbas
.\SETUP.bat
```

`SETUP.bat` akan automatik:
1. Detect PHP dari Laragon (prefer 8.4 > 8.3 > 8.2)
2. Install Composer dependencies
3. Create database `spkp_mbas`
4. Import SQL dump
5. Generate `APP_KEY`
6. Clear cache
7. Start server

### Cara 2: Manual Setup

```bash
# 1. Clone repo
git clone https://github.com/USERNAME/spkp-mbas.git
cd spkp-mbas

# 2. Install dependencies
composer install

# 3. Copy .env
cp .env.example .env
php artisan key:generate

# 4. Setup database (edit .env dulu)
mysql -u root -e "CREATE DATABASE spkp_mbas CHARACTER SET utf8mb4"
php artisan migrate --seed

# 5. Storage link
php artisan storage:link

# 6. Start server
php artisan serve
```

Buka browser di `http://127.0.0.1:8000`

---

## 🔑 Login Demo

Selepas jalankan `migrate --seed`, akaun berikut dijana:

<div align="center">

| Role | Email | Password |
|:---|:---|:---:|
| 👑 **Admin** | `admin@mbas.gov.my` | `password` |
| 🛡️ **Ketua Bahagian** | `ketua@mbas.gov.my` | `password` |
| 📋 **PPKP** | `firdaus@mbas.gov.my` | `password` |
| 📋 **PPKP** | `ramli@mbas.gov.my` | `password` |
| 📋 **PPKP** | `zubaidah@mbas.gov.my` | `password` |

</div>

> ⚠️ **PENTING:** Tukar password semua akaun sebaik selesai first login.

---

## 📁 Struktur Projek

```
spkp-mbas/
├── app/
│   ├── Console/Commands/       # Artisan commands (transfer:prepare, dll.)
│   ├── Http/Controllers/       # 20+ controllers
│   ├── Models/                 # Eloquent models
│   └── Services/
│       └── ChatbotService.php  # Anthropic Claude integration
├── database/
│   ├── migrations/             # 20+ migrations
│   └── seeders/                # DatabaseSeeder + demo data
├── resources/
│   └── views/
│       ├── layouts/            # Master + partials (sidebar, bot)
│       ├── activities/         # Modul Aktiviti
│       ├── semakan/            # Workflow Semakan KB
│       └── laporan/            # Laporan bulanan
├── routes/web.php              # 100+ routes
├── public/                     # Assets + service worker + manifest
├── SETUP.bat                   # One-click Windows installer
├── SETUP.ps1                   # PowerShell alternative
├── BACA_DULU.txt               # Arahan untuk penerima
└── TUTORIAL_*.txt              # 5 dokumen tutorial (BM)
```

---

## 📚 Dokumentasi

Sistem ini disertakan dengan dokumentasi menyeluruh dalam **Bahasa Melayu**:

| Fail | Kandungan |
|:---|:---|
| [`BACA_DULU.txt`](BACA_DULU.txt) | Arahan 5 langkah untuk penerima baru |
| [`TUTORIAL_DOWNLOAD.txt`](TUTORIAL_DOWNLOAD.txt) | Cara muat turun Laragon, VS Code, dll. |
| [`TUTORIAL_INSTALL.txt`](TUTORIAL_INSTALL.txt) | Panduan pemasangan step-by-step + 15 FAQ |
| [`TUTORIAL_IMPORT_DATABASE.txt`](TUTORIAL_IMPORT_DATABASE.txt) | Import database via phpMyAdmin/HeidiSQL |
| [`MANUAL_PENGGUNA_SPKP.md`](MANUAL_PENGGUNA_SPKP.md) | Manual penggunaan sistem harian |
| [`PANDUAN_TRANSFER.md`](PANDUAN_TRANSFER.md) | Panduan pemindahan sistem ke laptop lain |

---

## 🎨 Screenshot

<div align="center">

<em>Login Page · Dashboard · Bot Helpline · Kalendar Aktiviti · Laporan Bulanan</em>

<br>

*(Screenshot akan ditambah selepas deployment)*

</div>

---

## 🤖 Bot Helpline

Bot Helpline SPKP menggunakan **Anthropic Claude API** dengan konfigurasi khas:

- ✅ **Auto-detect modul aktif** — imbas `sidebar.blade.php` + `Route::getRoutes()`
- ✅ **Cache dinamik** — refresh automatik bila sidebar diubah (guna `filemtime`)
- ✅ **Small-talk handler** — balas mesra untuk sapaan (hi, terima kasih, dll.)
- ✅ **Typewriter effect** — respon muncul aksara demi aksara
- ✅ **Fallback keyword search** — kalau API tidak tersedia
- ✅ **Escalate ke admin** — untuk soalan complex

Untuk aktifkan, tambah dalam `.env`:
```env
ANTHROPIC_API_KEY=sk-ant-xxxxx
ANTHROPIC_MODEL=claude-haiku-4-5-20251001
```

---

## 🎯 Roadmap

- [x] Modul Aktiviti + GPS Watermark
- [x] Workflow Semakan KB
- [x] Tandatangan Digital
- [x] Laporan Bulanan + PDF Export
- [x] Bot Helpline dengan Claude AI
- [x] PWA (installable mobile app)
- [x] Handover tools (SETUP.bat)
- [ ] Push notifications
- [ ] Bulk import CSV
- [ ] Multi-language support (BM + EN)
- [ ] Mobile app (Flutter/React Native)

---

## 👨‍💻 Kredit

Sistem ini dibangunkan sepanjang **Latihan Industri** di:

**Bahagian Teknologi Maklumat**
Majlis Bandaraya Alor Setar (MBAS)
Kedah, Malaysia

Dengan sokongan daripada:
- **Bahagian Kawalan Penyakit & Promosi Kesihatan** (pengguna akhir & requirement)
- **Unit IT MBAS** (infrastruktur & bimbingan)

---

## 📞 Kontak

Untuk pertanyaan sistem atau sokongan teknikal:

📧 **devops1@mbas.gov.my**
🌐 **[www.mbas.gov.my](https://www.mbas.gov.my)**

---

## 📜 Lesen

Sistem ini adalah **hak milik Majlis Bandaraya Alor Setar (MBAS)**. Kod sumber disediakan untuk tujuan penyelenggaraan dan penambahbaikan dalaman sahaja.

Tidak dibenarkan menggunakan, menyalin, atau mengedar semula tanpa kebenaran bertulis daripada MBAS.

---

<div align="center">

**Dibina dengan ❤️ untuk komuniti MBAS**

<sub>© 2026 Majlis Bandaraya Alor Setar. Hak Cipta Terpelihara.</sub>

</div>
