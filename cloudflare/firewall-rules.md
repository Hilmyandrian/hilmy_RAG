# 🛡️ Cloudflare Firewall (WAF) Configuration

Berikut adalah detail konfigurasi aturan keamanan yang diterapkan di Dashboard Cloudflare untuk mengamankan n8n dan Webhook.

### 1. Rule: Block Unwanted HTTP Methods

- **Expression**: `(http.request.method ne "GET" and http.request.method ne "POST")`
- **Action**: `Block`
- **Tujuan**: Mencegah penyerang menggunakan metode seperti `DELETE`, `PUT`, atau `TRACE` yang tidak diperlukan oleh n8n/Webhook.

### 2. Rule: Allow Only Trusted Providers (Telegram & Vercel)

- **Expression**: `not (ip.geoip.asnum in {62041 14061})`
- **Action**: `Managed Challenge`
- **Tujuan**: Menampilkan tantangan Captcha jika akses datang dari luar jaringan Telegram (untuk Bot) atau Vercel (untuk WebApp), guna menghindari serangan DDoS atau Bot otomatis.

---

_Konfigurasi ini memastikan server lokal tetap privat dan hanya menerima lalu lintas yang telah terverifikasi._
