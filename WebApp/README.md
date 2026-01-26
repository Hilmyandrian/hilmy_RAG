# 🤖 WebApp: RAG Chatbot Interface

Halaman ini merupakan **Frontend Interface** dari sistem Chatbot berbasis **Retrieval-Augmented Generation (RAG)**. Web ini dirancang untuk memberikan pengalaman interaksi yang *seamless* antara pengguna dengan sistem AI yang dikelola melalui **n8n**.

## 📑 Daftar Isi
- [Gambaran Umum](#-gambaran-umum)
- [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
- [Struktur Folder](#-struktur-folder)
- [Konfigurasi & Instalasi](#-konfigurasi--instalasi)
- [Cara Kerja Sistem](#-cara-kerja-sistem)

## 🌟 Gambaran Umum
Proyek ini mengimplementasikan teknik RAG untuk memastikan AI tidak hanya menjawab berdasarkan data umum, tetapi juga merujuk pada dokumen spesifik yang telah di-upload ke dalam database vector di n8n. Antarmuka web dibuat responsif agar nyaman digunakan di perangkat apa pun.

## 🛠️ Teknologi yang Digunakan
- **Frontend**: HTML5, CSS3 (Custom UI), JavaScript (Fetch API).
- **Backend Orchestrator**: [n8n](https://n8n.io/) sebagai pengelola workflow.
- **AI Brain**: OpenAI GPT Models.
- **Tunneling**: Ngrok (untuk menghubungkan localhost n8n ke publik).

## 📂 Struktur Folder
Di dalam direktori ini terdapat file-file utama:
* `index.html`: Berisi struktur UI chat, styling CSS (dark mode), dan logika JavaScript untuk mengirim/menerima pesan dari API.
* `progress3.json`: File export workflow n8n yang digunakan pada tahap pengembangan ketiga.
* `README.md`: Dokumentasi teknis folder WebApp.

## ⚙️ Konfigurasi & Instalasi

### 1. Update Endpoint API
Buka file `index.html` dan cari bagian script JavaScript. Pastikan variabel `webhookUrl` mengarah ke URL Ngrok yang sedang aktif:
```javascript
const webhookUrl = '[https://mercurially-pneumatologic-louetta.ngrok-free.dev/webhook-test/webapp](https://mercurially-pneumatologic-louetta.ngrok-free.dev/webhook-test/webapp)';

### 2. Cara Menjalankan (PENTING)
Untuk menghindari masalah kebijakan keamanan browser (CORS) dan memastikan fitur chat berjalan lancar, **jangan langsung klik dua kali pada file `index.html`**. 

Gunakan ekstensi **Live Server** di VS Code atau web server lokal lainnya:
1. Buka folder `WebApp` di Visual Studio Code.
2. Klik kanan pada file `index.html`.
3. Pilih **"Open with Live Server"**.
4. Web akan terbuka di `http://127.0.0.1:5500`, dan chat bisa digunakan secara normal.
