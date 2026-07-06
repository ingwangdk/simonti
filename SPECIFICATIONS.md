# Dokumen Spesifikasi Teknis: SIMONTI

## 1. Arsitektur & Teknologi Utama
*   **Backend:** PHP 8.4
*   **Database:** MySQL / MariaDB
*   **Frontend:** JavaScript (jQuery), DataTables, dan pustaka grafik (Chart.js/ApexCharts)
*   **Manajemen Paket:** SheetJS (untuk ekspor/impor Excel)

---

## 2. Aturan Emas Pengembangan (Golden Rules)
Dokumen ini wajib dijadikan acuan utama untuk setiap penambahan fitur baru agar aplikasi tetap konsisten:

### A. Standar Penginputan Waktu
*   **Format Jam:** Wajib menggunakan standar **24-hour clock** (format waktu Indonesia, HH:mm). 
*   **Validasi:** Dilarang keras menggunakan format AM/PM pada komponen *time picker* maupun validasi skrip.

### B. Visualisasi & Pelaporan
*   **Entitas Supplier:** Dalam grafik, dasbor, maupun ringkasan laporan keuangan, **wajib menampilkan nama supplier**, bukan kode supplier. Kode hanya digunakan sebagai *primary key* atau relasi di level database.

### C. Metodologi Analisis Keuangan
*   **Baseline Data:** Semua perbandingan tren, capaian realisasi, atau evaluasi anggaran **wajib menggunakan data bulan Maret (Triwulan I) sebagai nilai awal (baseline)**. Jangan gunakan data bulan Januari sebagai titik awal komparasi.

---

## 3. Ketentuan Keamanan & Audit
*   **RBAC (Role-Based Access Control):** Setiap modul harus mengecek hak akses pengguna (admin, pimpinan, operator).
*   **Log Audit:** Setiap transaksi penambahan, perubahan, atau penghapusan data krusial wajib mencatat data ke tabel log sistem secara otomatis untuk kepatuhan pemeriksaan (*audit compliance*).

---

## 4. Struktur Database Awal (Rencana Modul)
*   `users` - Data autentikasi dan peran (role).
*   `suppliers` - Master data supplier (id, nama_supplier, kode_supplier).
*   `anggaran_realisasi` - Data transaksi keuangan dengan acuan Triwulan I.
*   `system_logs` - Catatan riwayat aktivitas user (audit trail).
