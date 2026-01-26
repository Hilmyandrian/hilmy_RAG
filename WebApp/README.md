# 🤖 WebApp: RAG Chatbot Interface - Official Documentation

Repository ini berisi antarmuka pengguna (Frontend) untuk sistem AI Chatbot berbasis **Retrieval-Augmented Generation (RAG)**. Proyek ini mengintegrasikan desain web modern dengan workflow otomatisasi n8n untuk memberikan jawaban yang akurat berdasarkan basis data dokumen.

---

## 📑 Daftar Isi
1. [Gambaran Umum](#-gambaran-umum)
2. [Fitur Utama](#-fitur-utama)
3. [Tech Stack](#-tech-stack)
4. [Struktur File](#-struktur-file)
5. [Panduan Instalasi & Konfigurasi](#-panduan-instalasi--konfigurasi)
6. [Cara Menjalankan (Penting)](#-cara-menjalankan-penting)
7. [Alur Kerja Sistem (Workflow)](#-alur-kerja-sistem-workflow)

---

## 🌟 Gambaran Umum
Berbeda dengan chatbot biasa, sistem ini menggunakan teknik **RAG**. Saat user bertanya, sistem tidak langsung menjawab, melainkan mencari referensi dari dokumen yang relevan terlebih dahulu di dalam vector database, lalu memberikan jawaban yang lebih akurat dan terkonteks melalui LLM (OpenAI).

## 🚀 Fitur Utama
- **Real-time Interaction**: Chat langsung dibalas tanpa refresh halaman.
- **Modern UI**: Dark mode interface yang bersih dan responsif.
- **Context-Aware**: Jawaban AI didasarkan pada dokumen yang di-upload ke n8n.
- **Natural Language**: Gaya bahasa disesuaikan menjadi santai (Gue/Lu) layaknya teman kuliah.

## 🛠️ Tech Stack
- **Frontend**: HTML5, CSS3, JavaScript (Vanilla - Fetch API).
- **Orchestrator**: [n8n.io](https://n8n.io/).
- **AI Model**: OpenAI GPT-4o / GPT-3.5.
- **Tunneling**: Ngrok (Localhost to Public).

## 📂 Struktur File
* `index.html`: File tunggal yang berisi struktur HTML, styling CSS, dan logika JavaScript.
* `progress3.json`: Backup workflow n8n yang bisa di-import langsung.
* `README.md`: Dokumentasi lengkap proyek (file ini).

---

## ⚙️ Panduan Instalasi & Konfigurasi

### 1. Persiapan Endpoint
Pastikan **n8n** dan **Ngrok** sudah berjalan. Buka `index.html` dan perbarui variabel `webhookUrl` dengan URL Ngrok kamu yang sedang aktif:
```javascript
const webhookUrl = '[https://mercurially-pneumatologic-louetta.ngrok-free.dev/webhook-test/webapp](https://mercurially-pneumatologic-louetta.ngrok-free.dev/webhook-test/webapp)';
