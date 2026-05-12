# Data Warehouse Wisata Yogyakarta

## 1. Pendahuluan

### 1.1 Latar Belakang
Perkembangan sektor pariwisata di Indonesia, khususnya di Daerah Istimewa Yogyakarta, menghasilkan data yang sangat besar dan beragam. Data tersebut meliputi informasi tempat wisata, kategori wisata, rating pengunjung, jumlah ulasan, hingga koordinat lokasi wisata.

Namun, data mentah sering kali sulit digunakan secara langsung untuk kebutuhan analisis dan pengambilan keputusan. Oleh karena itu, dibutuhkan suatu sistem yang mampu mengelola, membersihkan, menyimpan, serta menampilkan data secara terstruktur dan informatif. Salah satu solusi yang dapat digunakan adalah penerapan konsep **Data Warehouse** dan **Business Intelligence (BI)**.

Project ini dibuat untuk memenuhi tugas mata kuliah **Data Warehouse** dengan memanfaatkan Google Colab sebagai media pengolahan, analisis, dan visualisasi data wisata di Yogyakarta.

---

# 2. Tujuan Project

Tujuan dari project ini adalah:

- Mengimplementasikan konsep **Data Warehouse** pada data wisata Yogyakarta.
- Melakukan proses **ETL (Extract, Transform, Load)** terhadap dataset wisata.
- Membersihkan data agar lebih konsisten dan siap dianalisis.
- Menampilkan visualisasi data yang informatif dan mudah dipahami.
- Membantu pengguna memahami insight dari data wisata melalui grafik dan analisis visual.
- Menggunakan Python dan Google Colab sebagai media analisis data.

---

# 3. Anggota Kelompok

| Nama | NIM |
|---|---|
| Darel Prasetya Fawwaz | 2409116064 |
| Christian Amsal Asimaro Lumban Tobing | 2409116053 |
| Muhammad Irdhan Nur Faudzan | 2409116077 |
| Zidan Daffa Ramadhan | 2409116056 |

---

# 4. Tools dan Teknologi yang Digunakan

| Teknologi | Fungsi |
|---|---|
| Python | Pengolahan dan analisis data |
| Google Colab | Platform analisis data |
| Pandas | Data cleaning dan manipulasi data |
| NumPy | Operasi numerik |
| Matplotlib | Visualisasi data |
| Seaborn | Pembuatan grafik statistik |
| MySQL | Penyimpanan data warehouse |
| GitHub | Repository project |

---

# 5. Metodologi Project

## 5.1 Data Collection
Tahap pertama adalah pengumpulan dataset wisata Yogyakarta yang berisi informasi seperti:

- Nama tempat wisata
- Jenis wisata
- Rating
- Jumlah ulasan
- Lokasi koordinat
- Informasi tambahan lainnya

Dataset kemudian digunakan sebagai sumber utama dalam proses analisis dan visualisasi.

---

## 5.2 Data Cleaning
Tahap data cleaning dilakukan menggunakan Python di Google Colab untuk memastikan data:

- Tidak memiliki nilai kosong (missing value)
- Tidak memiliki data duplikat
- Format data konsisten
- Tipe data sesuai
- Data siap digunakan untuk proses analisis

Tujuan dari data cleaning adalah meningkatkan kualitas data agar hasil visualisasi dan analisis menjadi lebih akurat.

---

## 5.3 ETL Process (Extract, Transform, Load)

### Extract
Data diambil dari dataset sumber yang telah tersedia.

### Transform
Data diubah dan disesuaikan ke dalam format yang lebih terstruktur, seperti:
- Normalisasi data
- Perbaikan format
- Pengelompokan kategori wisata
- Konversi tipe data

### Load
Data hasil transformasi dimasukkan ke dalam database warehouse untuk digunakan dalam proses analisis dan visualisasi.

---

# 6. Implementasi Data Warehouse

Data warehouse digunakan sebagai tempat penyimpanan data terintegrasi yang mendukung proses analisis data wisata.

Struktur warehouse memungkinkan:
- Pengolahan data lebih cepat
- Penyajian informasi lebih terstruktur
- Visualisasi data yang lebih mudah
- Analisis historis dan insight data

Data warehouse membantu proses Business Intelligence dalam menghasilkan informasi yang lebih bermanfaat dari data wisata yang tersedia.

---

# 7. Implementasi Analisis Data

Analisis data dilakukan menggunakan Python pada Google Colab. Seluruh proses mulai dari data cleaning, ETL, hingga visualisasi dilakukan secara terintegrasi dalam notebook.

## Tahapan Analisis

### 7.1 Data Cleaning
Membersihkan dan menyesuaikan data agar siap digunakan.

### 7.2 Data Exploration
Melakukan eksplorasi terhadap dataset untuk memahami pola dan karakteristik data.

### 7.3 Visualisasi Data
Membuat grafik dan chart untuk menampilkan informasi secara visual.

### 7.4 Insight Analysis
Menghasilkan insight berdasarkan hasil visualisasi dan analisis data.

---

# 8. Struktur Project

```bash
dataset/
notebook/
visualization/
README.md
```

Penjelasan struktur project:

| Folder/File | Fungsi |
|---|---|
| dataset/ | Berisi dataset wisata |
| notebook/ | File Google Colab / Jupyter Notebook |
| visualization/ | Hasil visualisasi grafik |
| README.md | Dokumentasi project |

---

# 9. Hasil Visualisasi dan Analisis Data

## 9.1 Visualisasi Distribusi Rating

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/c0ac30c8-2fc5-489c-9ac4-9f230fa14423" />

### Analisis
Berdasarkan visualisasi distribusi rating:
- Mayoritas tempat wisata memiliki rating tinggi.
- Nilai rata-rata rating berada di angka **4.44 dari 5.0**.
- Sebanyak **75% tempat wisata memiliki rating di atas 4.3**.
- Sangat sedikit destinasi wisata yang memiliki rating buruk di bawah 3.0.

### Insight
Hal ini menunjukkan bahwa tingkat kepuasan pengunjung terhadap wisata di Yogyakarta tergolong sangat baik.

---

## 9.2 Visualisasi Jenis Wisata

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/a0182bd0-293a-4418-9632-ba316e35a69f" />

### Analisis
Kategori wisata yang paling mendominasi adalah:
- Wisata Alam : 27 tempat
- Wisata Budaya dan Sejarah : 24 tempat
- Wisata Pantai : 23 tempat

### Insight
Data menunjukkan bahwa Yogyakarta memiliki potensi besar pada sektor:
- Ekowisata
- Wisata alam
- Wisata budaya dan sejarah

Keanekaragaman kategori wisata menjadi salah satu daya tarik utama daerah ini.

---

## 9.3 Top 10 Wisata Terpopuler

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/461b182e-6cdf-4efe-80f7-29c0d42c2862" />

### Analisis
Destinasi dengan jumlah ulasan tertinggi adalah:
1. Candi Borobudur — 81.922 ulasan
2. Candi Prambanan — 71.751 ulasan
3. Tebing Breksi — 51.431 ulasan

### Insight
- Wisata budaya dan sejarah masih menjadi daya tarik utama wisatawan.
- Tempat wisata buatan seperti Gembira Loka Zoo dan Taman Sari juga memiliki tingkat popularitas tinggi.
- Walaupun wisata alam mendominasi jumlah kategori, interaksi pengunjung terbesar tetap berada pada wisata budaya dan buatan.

---

## 9.4 Peta Persebaran Tempat Wisata

<img width="981" height="790" alt="image" src="https://github.com/user-attachments/assets/d796cd99-a54e-4dd8-8098-8a1c4c1af6ae" />

### Analisis
Berdasarkan koordinat:
- Latitude berada pada rentang -7.5 hingga -8.2
- Longitude berada pada rentang 109.9 hingga 110.7

Persebaran lokasi wisata menunjukkan:
- Wisata pantai banyak berada di wilayah selatan
- Wisata budaya dan wisata buatan dominan di pusat kota
- Wisata alam banyak tersebar di wilayah utara dan pinggiran

### Insight
Pola persebaran wisata menunjukkan hubungan erat antara kategori wisata dengan kondisi geografis wilayah Yogyakarta.

---

# 10. Kesimpulan

Berdasarkan hasil implementasi project Data Warehouse Wisata Yogyakarta dapat disimpulkan bahwa:

1. Konsep Data Warehouse berhasil diterapkan untuk mengelola data wisata secara terstruktur.
2. Proses ETL membantu menghasilkan data yang lebih bersih dan siap dianalisis.
3. Visualisasi data mampu membantu pengguna memahami informasi dengan lebih mudah.
4. Wisata budaya, sejarah, dan alam menjadi kategori dominan di Yogyakarta.
5. Rating wisata yang tinggi menunjukkan tingkat kepuasan pengunjung yang baik.
6. Persebaran lokasi wisata menunjukkan karakter geografis wisata Yogyakarta yang beragam.

---

# Repository Project

Project dikelola menggunakan GitHub untuk dokumentasi dan penyimpanan hasil analisis data.