# 🏛️ Dokumentasi Arsitektur: Integrasi Cloudflare

## 1. Ringkasan Proyek

Pada tahap **Project Progress 6**, sistem telah melakukan migrasi dari penggunaan **Ngrok** ke **Cloudflare Tunnel**. Langkah ini diambil untuk meningkatkan aspek keamanan, stabilitas akses, dan profesionalisme infrastruktur aplikasi (n8n & WebApp).

## 2. Diagram Alur Jaringan (Traffic Flow)

Berikut adalah visualisasi bagaimana data mengalir dari internet ke server lokal:

1. **Client/Webhook Request**: Request datang dari Telegram atau User ke URL `https://n8n.dexquins.com`.
2. **Cloudflare WAF**: Cloudflare melakukan inspeksi paket data berdasarkan _Firewall Rules_ yang telah ditetapkan.
3. **Encrypted Tunnel**: Request yang valid diteruskan melalui _outgoing connection_ dari server lokal ke Edge Cloudflare (tanpa perlu membuka port di router).
4. **Local Service**: Request diterima oleh `cloudflared` di mesin lokal dan diteruskan ke `localhost:5678`.

## 3. Perbandingan Infrastruktur

| Komponen       | Sebelum (Ngrok)                                             | Sesudah (Cloudflare)               |
| :------------- | :---------------------------------------------------------- | :--------------------------------- |
| **Endpoint**   | `https://mercurially-pneumatologic-louetta.ngrok-free.dev/` | `https://n8n.dexquins.com`         |
| **Keamanan**   | Publik (Siapa saja bisa akses)                              | Terproteksi WAF & Bot Management   |
| **Stabilitas** | URL berubah saat restart (Gratis)                           | URL Permanen & Statis              |
| **Enkripsi**   | TLS standar                                                 | End-to-End Encryption (Cloudflare) |

## 4. Keamanan Jaringan (Layer 7 Security)

Kami menerapkan kebijakan keamanan melalui **Cloudflare WAF (Web Application Firewall)**:

- **Method Filtering**: Hanya mengizinkan `GET` dan `POST`. Metode lain diblokir untuk meminimalisir celah keamanan.
- **Source Validation**: Menggunakan verifikasi ASN untuk memastikan request berasal dari sumber terpercaya seperti Telegram (ASN 62041) dan Vercel.

## 5. Konfigurasi Endpoint Baru

| Service           | URL Baru (Cloudflare)          | Port Lokal |
| :---------------- | :----------------------------- | :--------- |
| **n8n Dashboard** | `https://n8n.dexquins.com`     | `5678`     |
| **Webhook API**   | `https://webhook.dexquins.com` | `5678`     |

---

_Dokumentasi ini dibuat untuk memenuhi tugas Project Progress 6 - Integrasi Cloudflare._
