# Personal AI Advisor - RAG System Integration
**Laporan Project Progress 4 & 5**

* **Nama:** Hilmy Andrian Saputra
* **NIM:** 24523014

---

## 🚀 Progress 4: Implementasi Vector Database Pipeline
### A. Deskripsi Progress
Fokus utama pada tahap ini adalah membangun pipeline otomatisasi pengolahan data dokumen (**Ingestion**). Sistem mengubah dokumen mentah (PDF) menjadi data vektor yang siap digunakan oleh AI.

**Pencapaian Utama:**
* Integrasi **Google Drive** sebagai sumber data dinamis.
* Implementasi **Text Splitting** menggunakan *Recursive Character Text Splitter*.
* Generate Embedding menggunakan model **OpenAI**.
* Penyimpanan vektor ke **Pinecone Vector Store**.

### B. Arsitektur Workflow (Ingestion)
1.  **Manual Trigger:** Inisiasi jalannya workflow.
2.  **Google Drive Node:** Mencari & mengunduh file PDF secara otomatis.
3.  **Data Loader:** Konversi biner ke teks.
4.  **Embeddings OpenAI:** Mengubah teks menjadi vektor numerik.
5.  **Pinecone Store (Insert):** Menyimpan vektor ke indeks `ragproject`.

---

## 🤖 Progress 5: Integrasi Sistem RAG (Telegram, WebApp, & AI Agent)
### A. Deskripsi Progress
Tahap ini merupakan integrasi *End-to-End* antara antarmuka pengguna dengan logika backend AI menggunakan sistem **Multi-Channel**.

**Pencapaian Utama:**
* **Web App kustom:** "Personal AI Advisor" dengan tampilan Dark Mode.
* **AI Agent:** Dilengkapi kemampuan *Tools Retrieval* (Pinecone) dan *Memory* (Postgres).
* **Routing Logic:** Pemisahan respon otomatis antara WebApp dan Telegram.
* **Debugging:** Penanganan isu data *undefined* menggunakan referensi `.first().json.channel`.

### B. Logika Kerja Sistem (RAG & Routing)
1.  **Multi-Trigger:** Menerima input dari **Webhook** (WebApp) dan **Telegram Trigger**.
2.  **Standardisasi Data:** Menggunakan node *Edit Fields* untuk variabel `userMessage`.
3.  **AI Agent (Brain):** Melakukan pencarian konteks ke Pinecone (Retrieve) sebelum memberikan jawaban.
4.  **Router (If Node):**
    * `channel == webhook` ➡️ Mengirim respon ke WebApp.
    * `channel != webhook` ➡️ Mengirim respon ke bot Telegram.

---

## 📊 Bukti Eksekusi
* **Ingestion Success:** Jalur kiri (Drive ke Pinecone) terverifikasi hijau/sukses di n8n.
* **RAG Verification:** AI berhasil menjawab pertanyaan spesifik berdasarkan dokumen PDF yang diunggah (bukan Pengetahuan Umum).
* **Frontend-Backend Sync:** Koneksi antara WebApp, Telegram, dan n8n berjalan lancar tanpa error.

---
*Dokumentasi ini disusun sebagai bagian dari pemenuhan tugas Project AI.*