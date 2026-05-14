# Sistem Deteksi Anomali Tender Pengadaan Barang/Jasa

Proyek ini bertujuan untuk mengidentifikasi pola tidak wajar atau potensi anomali pada data pengadaan barang dan jasa pemerintah (OpenTender) menggunakan pendekatan **Machine Learning** dan **Network Analysis**.

## Tim Proyek
- **Dzaki Pranaja** (Lead Developer / Data Scientist)
- **Idzar** & **Afzaal** (Collaborators)

## Teknologi yang Digunakan
- **Bahasa Pemrograman:** Python 3.12
- **Analisis Data:** Pandas, NumPy
- **Machine Learning:** Scikit-Learn (Isolation Forest)
- **Visualisasi:** Matplotlib, Pyvis (Interactive Network)
- **Network Theory:** NetworkX

## Dataset Menggunakan dataset open public dari Indonesia Corruption Watch

## Struktur File Notebook
Proyek ini terbagi menjadi dua bagian utama:

### 1. `main.ipynb` (Prapemrosesan & Pemodelan)
Berfokus pada pembersihan data dan penerapan algoritma deteksi anomali.
* **Data Cleaning:** Menghapus noise pada kolom metode pengadaan dan menangani *missing values*.
* **Feature Engineering:** Membuat metrik baru untuk mendeteksi kecurangan:
    * `ratio`: Rasio nilai kontrak terhadap HPS (HPS/Pagu).
    * `discount_percentage`: Besaran potongan harga yang diberikan vendor.
    * `vendor_win_count`: Total kemenangan vendor secara historis.
    * `vendor_instansi_frequency`: Intensitas vendor menang pada instansi yang sama.
* **Anomaly Detection:** Menggunakan **Isolation Forest** dengan kontaminasi 2% untuk melabeli transaksi yang mencurigakan.

### 2. `idzar.ipynb` (Exploratory Data Analysis & Visualisasi Graf)
Berfokus pada analisis hubungan antar entitas melalui teori jaringan.
* **Network Metrics:** Menghitung *Degree Centrality* (pusat transaksi) dan *Clustering Coefficient* (indikasi koalisi/sindikasi).
* **Interactive Visualization:** Membangun graf interaktif menggunakan algoritma fisika `forceAtlas2Based`.
* **Output:** Menghasilkan file `super_anomaly_network.html` untuk inspeksi visual hubungan Vendor-Pembeli.

## Alur Kerja (Workflow)
1.  **Ingestion:** Memuat dataset mentah `opentender_clean_2022_2024.csv`.
2.  **Transformation:** Ekstraksi fitur numerik dan standarisasi data menggunakan `StandardScaler`.
3.  **Detection:** Menjalankan model Isolation Forest untuk mendeteksi pencilan data.
4.  **Networking:** Memetakan relasi antar vendor dan instansi untuk melihat dominasi pasar.
5.  **Reporting:** Menyimpan hasil akhir ke dalam `featured_procurement_dataset.csv`.

## Cara Menjalankan
1. Pastikan dataset tersedia di folder `datasets/`.
2. Instal pustaka yang dibutuhkan:
