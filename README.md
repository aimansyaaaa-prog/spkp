<div align="center">

# 🌿 SPKP MBAS

### Sistem Pengurusan Kesihatan Persekitaran
**Majlis Bandaraya Alor Setar (MBAS)**

Aplikasi web untuk merekod, memproses dan meluluskan aktiviti kesihatan persekitaran — kawalan vektor (fogging & Aedes), kawalan lilati, tangkapan haiwan terbiar, gotong-royong, promosi kesihatan dan operasi COVID — lengkap dengan pengurusan aduan, laporan bulanan, penjanaan PDF rasmi dan aliran kerja kelulusan berperingkat.

![Laravel](https://img.shields.io/badge/Laravel-11-FF2D20?logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.2%2B-777BB4?logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.x-4479A1?logo=mysql&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?logo=tailwindcss&logoColor=white)
![Bahasa](https://img.shields.io/badge/Bahasa-Melayu-red)

</div>

---

## 📖 Pengenalan

**SPKP MBAS** ialah sistem dalaman Bahagian Kesihatan Persekitaran, Majlis Bandaraya Alor Setar bagi menggantikan borang & log manual dengan satu platform digital berpusat. Pegawai penyedia merekod aktiviti harian di lapangan (termasuk gambar, lokasi GPS dan tandatangan digital), ketua bahagian menyemak & mengesahkan rekod, dan laporan bulanan dijana secara automatik dalam format PDF rasmi.

Antara muka sepenuhnya dalam **Bahasa Melayu** dan direka bentuk **mesra mudah alih (PWA)** supaya boleh digunakan terus di lapangan.

---

## ✨ Ciri-Ciri Utama

### 📋 Log Aktiviti
- Rekod aktiviti mengikut jenis: **Fogging, Aedes, Lilati (lipas/lalat/tikus), Tangkapan Haiwan, Gotong-Royong, Promosi Kesihatan, COVID** dan lain-lain.
- Muat naik **berbilang gambar** (dengan susun semula & padam), tangkap **lokasi GPS + peta Leaflet**, dan **tandatangan digital**.
- Nombor fail rasmi dijana automatik mengikut format `MBAS/JKP/...`.
- **Templat aktiviti** untuk pra-isi borang aktiviti rutin berulang.
- **Duplicate**, **eksport CSV**, tindakan **pukal (bulk)** dan **tong sampah** (soft delete + pulih/padam kekal).

### 🔄 Aliran Kerja Kelulusan (Workflow)
- Aliran berperingkat: **Draf → Dihantar → Disemak (Penyelia) → Disahkan (Ketua Bahagian)**.
- **Baris gilir semakan** (approval queue) terpusat untuk Ketua & Admin.
- **Pengesahan pukal** dengan kod sebab & pemeriksaan rambang (spot-check).
- Tarik balik, kembalikan (dengan sebab) dan batal-sahkan.

### 📊 Laporan
- **Laporan bulanan** automatik (sasaran vs pencapaian, peratus prestasi).
- Penjanaan **PDF rasmi** (DomPDF) dengan tandatangan & tajuk laporan mengikut jenis aktiviti.
- **Templat laporan** boleh dikongsi, **ulasan** & aliran kelulusan laporan, eksport CSV.
- **Ringkasan bulanan** dan pratonton laporan.

### 📮 Pengurusan Aduan
- Rekod aduan orang awam dengan **kategori, zon, keutamaan dan SLA**.
- Penetapan pegawai bertanggungjawab & penjejakan status siasatan.

### 🛠️ Modul Pentadbir
- **Pengurusan pengguna** (cipta, edit, aktif/nyahaktif, set semula kata laluan).
- **Pengumuman** halaman utama.
- **Import CSV** pukal (serasi e-PBT) dengan pratonton sebelum commit.
- **Kesihatan sistem & sandaran (backup)** pangkalan data.
- **Tetapan tapak** + **mod suntingan langsung (live edit)**.
- **Log audit** penuh (siapa buat apa, bila, dari IP mana).

### 💬 Sokongan & Bantuan
- **Tiket sokongan** (pengguna hantar, admin balas & tutup).
- **AI Helpline** berkuasa **Claude (Anthropic)** untuk bantuan segera.
- Pusat bantuan & carian global (JSON).

### 🔔 Lain-Lain
- Papan pemuka (dashboard) dengan **carta interaktif**.
- **Notifikasi** dalam sistem + emel.
- Profil pengguna, avatar, pustaka tandatangan peribadi.
- Set semula kata laluan, had kadar (throttling) pada log masuk.
- **PWA** — halaman luar talian & service worker.

---

## 🧑‍💼 Peranan Pengguna

| Peranan | Kod | Keupayaan |
|---|---|---|
| **Pentadbir Sistem** | `admin` | Akses penuh — pengguna, tetapan, import, sandaran, audit, sokongan, pengumuman. |
| **Ketua Bahagian** | `ketua` | Semak & sahkan rekod, akses baris gilir semakan, log audit. |
| **Pegawai Penyedia** | `penyedia` | Cipta & hantar rekod aktiviti, jana laporan, urus aduan. |

---

## 🛠️ Teknologi

| Lapisan | Teknologi |
|---|---|
| **Backend** | PHP 8.2+, Laravel 11 |
| **Pangkalan Data** | MySQL 8.x |
| **Frontend** | Blade, Tailwind CSS, Alpine.js, Vite |
| **Peta** | Leaflet.js |
| **PDF** | barryvdh/laravel-dompdf |
| **Auth/API** | Laravel Sanctum |
| **AI** | Anthropic Claude (Helpline sokongan) |
| **Lain-lain** | Flatpickr (tarikh), PWA (service worker) |

---

## 📦 Keperluan Sistem

- PHP **8.2** atau lebih tinggi
- Composer 2.x
- MySQL 8.x (atau MariaDB)
- Node.js 20+ & npm (untuk membina aset frontend)
- Pelayan web (Apache/Nginx) atau `php artisan serve` — sesuai untuk **Laragon/XAMPP** di Windows

---

## 🚀 Pemasangan

```bash
# 1. Klon repositori
git clone <url-repo> SPKP-MBAS
cd SPKP-MBAS

# 2. Pasang kebergantungan PHP
composer install

# 3. Sediakan fail persekitaran
cp .env.example .env
php artisan key:generate

# 4. Konfigurasi pangkalan data di dalam .env
#    DB_DATABASE=spkp_mbas
#    DB_USERNAME=root
#    DB_PASSWORD=

# 5. Jalankan migrasi + data contoh (pilihan)
php artisan migrate --seed

# 6. Pautan storan (untuk gambar & tandatangan)
php artisan storage:link

# 7. Pasang & bina aset frontend
npm install
npm run build      # atau: npm run dev (untuk pembangunan dengan hot-reload)

# 8. Jalankan aplikasi
php artisan serve
```

Buka pelayar di `http://127.0.0.1:8000` (atau `http://spkp.test` jika menggunakan Laragon virtual host).

---

## 👤 Akaun Demo

Selepas `php artisan migrate --seed`, akaun berikut tersedia (kata laluan: **`password`**):

| Peranan | Emel | Kata Laluan |
|---|---|---|
| Pentadbir Sistem | `admin@mbas.gov.my` | `password` |
| Ketua Bahagian | `ketua@mbas.gov.my` | `password` |
| Pegawai Penyedia | `firdaus@mbas.gov.my` | `password` |

> ⚠️ **Tukar semua kata laluan default sebelum digunakan dalam persekitaran sebenar (production).**

---

## ⚙️ Konfigurasi Penting (`.env`)

```env
APP_NAME="SPKP MBAS"
APP_LOCALE=ms
APP_TIMEZONE=Asia/Kuala_Lumpur
APP_URL=http://spkp.test

DB_CONNECTION=mysql
DB_DATABASE=spkp_mbas

# AI Helpline (pilihan) — isi kunci untuk aktifkan bantuan AI
ANTHROPIC_API_KEY=
ANTHROPIC_MODEL=claude-haiku-4-5-20251001
```

> Ciri **AI Helpline** hanya berfungsi apabila `ANTHROPIC_API_KEY` diisi. Semua ciri lain berfungsi tanpanya.

---

## 📁 Struktur Ringkas

```
app/
├── Http/Controllers/       # Aktiviti, Workflow, Laporan, Aduan, Admin, Sokongan…
├── Models/                 # Activity, Complaint, Report, User, AuditLog…
└── Http/Middleware/        # EnsureUserRole (kawalan akses peranan)
database/
├── migrations/             # Skema pangkalan data
└── seeders/                # Akaun demo & data contoh
resources/views/            # Templat Blade (UI Bahasa Melayu)
routes/web.php              # Semua laluan aplikasi
```

---

## 🔒 Nota Keselamatan

- **Jangan** commit fail `.env` atau kunci `APP_KEY` / `ANTHROPIC_API_KEY` ke repositori awam.
- Tukar kata laluan akaun demo & jangan seed data contoh dalam production.
- Log masuk dilindungi had kadar (rate limiting); log audit merekod aktiviti sensitif.

---

## 📄 Lesen & Hak Cipta

© Majlis Bandaraya Alor Setar (MBAS). Sistem dalaman untuk kegunaan rasmi MBAS.
Kerangka Laravel adalah perisian sumber terbuka di bawah [lesen MIT](https://opensource.org/licenses/MIT).

---

<div align="center">
<sub>Dibina untuk Bahagian Kesihatan Persekitaran, Majlis Bandaraya Alor Setar.</sub>
</div>
