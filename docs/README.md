# MBGlab — Platform Pengawasan UMKM Katering Terintegrasi AI & IoT

> **Prototipe interaktif untuk Digdaya x Hackathon**  
> Tim: Luminaries · Institut Teknologi Sumatera

---

## 🔗 Lihat Prototipe Langsung (Tanpa Install Apapun)

### 👉 https://georgehaansraj.github.io/MBGlab/

> Klik link di atas untuk membuka demo langsung di browser.  
> Tidak perlu download, tidak perlu install — cukup buka linknya.

---

## Tentang MBGlab

MBGlab adalah platform pengawasan B2G (Business-to-Government) terintegrasi AI dan IoT nirkabel untuk memastikan keamanan pangan dapur UMKM katering dalam program **Makan Bergizi Gratis (MBG)**. Solusi ini dirancang untuk menggantikan pencatatan manual yang rawan manipulasi dengan validasi proaktif berbasis teknologi.

**Tiga pilar utama:**

| Pilar                   | Teknologi                | Fungsi                                                              |
| ----------------------- | ------------------------ | ------------------------------------------------------------------- |
| 🌡️ IoT Smart Storage    | ESP32 + BLE Coin Sensor  | Monitor suhu & kelembapan gudang/kulkas real-time, tanpa kabel      |
| 🤖 AI Vision Auditor    | YOLO + Smartphone Vendor | Deteksi APD (masker/hairnet) & validasi porsi gizi via "Sidak Acak" |
| 📊 Dashboard Pemerintah | FastAPI + Web Analytics  | Heatmap kepatuhan nasional, penerbitan e-SLHS otomatis, e-Faktur    |

---

## Panduan Menjelajahi Prototipe

Buka link di atas, lalu navigasi menggunakan menu di bagian atas halaman:

### 1. Dashboard Nasional

Tampilan ringkasan kepatuhan seluruh vendor secara nasional, termasuk:

- Heatmap kepatuhan per provinsi
- KPI real-time: jumlah vendor aktif, anomali suhu, dan audit AI harian
- Feed peringatan otomatis yang diperbarui setiap beberapa detik

### 2. IoT Monitor

Simulasi data sensor BLE dari kulkas dan gudang bahan baku:

- Pembacaan suhu dan kelembapan yang berubah setiap 2 detik
- Sparkline chart per sensor
- MQTT log stream yang mensimulasikan transmisi data ke server cloud

### 3. Random Audit _(Fitur Utama — Bisa Dicoba Langsung)_

Fitur demonstrasi AI Vision:

**Cara mencoba:**

1. Upload sembarang foto (area dapur, makanan, atau orang yang sedang memasak)
2. Klik **"Analisis dengan AI"**
3. Lihat hasil deteksi APD, kebersihan, dan estimasi gizi

> **Tanpa API key:** Sistem menampilkan hasil simulasi yang sudah disiapkan.  
> **Dengan API key Anthropic:** AI Claude sungguhan akan menganalisis foto yang diupload secara langsung.

### 4. Rapor Vendor

Contoh tampilan aplikasi mobile vendor, mencakup:

- Skor kepatuhan harian dan rekap audit bulanan
- Validasi gizi per standar BGN
- Status e-SLHS dan simulasi penandatanganan e-Faktur pencairan dana

---

## Struktur Repository

```
📁 docs
├── index.html   # Seluruh prototipe dalam satu file HTML
└── README.md               # Dokumen ini
```

Seluruh prototipe dibuat dalam satu file HTML mandiri (tanpa framework eksternal, tanpa backend), sehingga bisa dijalankan langsung di browser manapun.

---

## Cara Menjalankan Secara Lokal (Opsional)

Jika ingin membuka prototipe secara offline:

1. Download file `index.html` dari repository ini
2. Buka file tersebut langsung di browser (Chrome, Firefox, atau Edge)

Tidak ada langkah instalasi tambahan yang diperlukan.

---

## Cara Mengaktifkan Live Demo (Untuk Pengelola Repo)

Agar link prototipe di atas bisa diakses publik, aktifkan **GitHub Pages**:

1. Buka repository ini di GitHub
2. Klik **Settings** → pilih **Pages** di menu kiri
3. Di bagian _Source_, pilih branch `main` dan folder `/ (root)`
4. Klik **Save**
5. Tunggu 1–2 menit, lalu akses di: `https://[USERNAME].github.io/[NAMA-REPO]/mbglab-prototype.html`

Setelah aktif, perbarui link di bagian atas README ini.

---

## Tumpukan Teknologi (Rancangan Sistem Penuh)

Prototipe ini mensimulasikan arsitektur sistem yang direncanakan sebagai berikut:

```
[BLE Coin Sensor] ──BLE──► [ESP32 Gateway] ──MQTT/TLS──► [FastAPI Backend]
[Smartphone Vendor] ──Wi-Fi──► [MQTT/HTTP] ──────────────► [YOLO AI Server]
                                                            ▼
                                                    [Database Telemetri]
                                                    [Penyimpanan Video/Foto]
                                                    [Sistem e-Invoice]
                                                            ▼
                                               [Dashboard Web BGN/Dinkes]
                                               [Aplikasi Mobile Vendor]
```

**Stack yang direncanakan:**

- **IoT:** ESP32 (C++), protokol MQTT dengan enkripsi TLS/SSL
- **AI/ML:** Python, YOLOv8 (deteksi objek & instance segmentation)
- **Backend:** FastAPI atau Django, PostgreSQL
- **Frontend:** Web dashboard (React) + Aplikasi mobile vendor
- **Keamanan:** E-signature Privy ID / BSrE untuk validasi dokumen

---

_Dibuat untuk keperluan seleksi Hackathon [nama hackathon] · [bulan tahun]_
