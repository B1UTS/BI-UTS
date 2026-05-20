# Data Warehouse Wisata Yogyakarta

Lini GCOLAB: https://colab.research.google.com/drive/194rD3l1ufcvxk3svofQKVkOFFCamPt5a?usp=sharing

## 1. Pendahuluan

### 1.1 Latar Belakang

Perkembangan sektor pariwisata di Indonesia, khususnya di Daerah Istimewa Yogyakarta, menghasilkan data yang sangat besar dan beragam. Data tersebut meliputi informasi tempat wisata, kategori wisata, rating pengunjung, jumlah ulasan, harga tiket masuk, hingga koordinat lokasi wisata.

Data mentah tersebut sulit digunakan secara langsung untuk kebutuhan analisis karena masih memiliki berbagai permasalahan seperti data kosong, format yang tidak konsisten, data duplikat, serta struktur data yang belum terorganisir dengan baik.

Untuk mengatasi permasalahan tersebut, diperlukan implementasi konsep Business Intelligence (BI) dan Data Warehouse agar data dapat diolah, dibersihkan, disimpan, dan divisualisasikan secara lebih terstruktur sehingga mampu membantu proses analisis dan pengambilan keputusan.

Project ini dibuat sebagai implementasi proses ETL (Extract, Transform, Load), Data Warehouse, serta visualisasi Business Intelligence menggunakan Python dan Google Colab pada data wisata Yogyakarta.

---

# 2. Tujuan Project

Tujuan dari project ini adalah:

* Mengimplementasikan konsep Data Warehouse pada data wisata Yogyakarta
* Melakukan proses ETL (Extract, Transform, Load) menggunakan Google Colab
* Membersihkan dan menormalisasi dataset wisata
* Membuat struktur Star Schema untuk kebutuhan analytics
* Menghasilkan dataset yang siap digunakan untuk Business Intelligence
* Menampilkan visualisasi data wisata secara informatif
* Membantu proses analisis data wisata menggunakan Python

---

# 3. Anggota Kelompok

| Nama                                  | NIM        |
| ------------------------------------- | ---------- |
| Darel Prasetya Fawwaz                 | 2409116064 |
| Christian Amsal Asimaro Lumban Tobing | 2409116053 |
| Muhammad Irdhan Nur Faudzan           | 2409116077 |
| Zidan Daffa Ramadhan                  | 2409116056 |

---

# 4. Tools dan Teknologi yang Digunakan

| Teknologi    | Fungsi                            |
| ------------ | --------------------------------- |
| Python       | Pengolahan dan analisis data      |
| Google Colab | Platform analisis data            |
| Pandas       | Data cleaning dan manipulasi data |
| NumPy        | Operasi numerik                   |
| Matplotlib   | Visualisasi data                  |
| Seaborn      | Pembuatan grafik statistik        |
| MySQL        | Penyimpanan data warehouse        |
| GitHub       | Repository project                |

---

# 5. Dataset yang Digunakan

Project ini menggunakan beberapa dataset wisata Yogyakarta, yaitu:

| Dataset         | Keterangan                        |
| --------------- | --------------------------------- |
| tour.csv        | Dataset utama tempat wisata       |
| tour_rating.csv | Dataset rating pengguna           |
| user.csv        | Dataset data pengguna             |
| raw_data.csv    | Dataset tambahan analytics wisata |

---

# 6. Struktur Dataset

## 6.1 Dataset Wisata

Dataset wisata berisi informasi:

* Nama tempat wisata
* Deskripsi wisata
* Kategori wisata
* Harga tiket
* Rating wisata
* Koordinat lokasi
* Kota wisata

---

## 6.2 Dataset Rating

Dataset rating digunakan untuk menyimpan interaksi pengguna terhadap tempat wisata.

Berisi:

* User ID
* Place ID
* Rating pengguna

---

## 6.3 Dataset User

Berisi:

* ID pengguna
* Lokasi pengguna
* Umur pengguna

---

## 6.4 Dataset Tambahan

Dataset tambahan digunakan untuk kebutuhan Business Intelligence dan analytics.

Berisi:

* vote_average
* vote_count
* harga weekday
* harga weekend
* latitude
* longitude
* type wisata

---

# 7. Metodologi Project

## 7.1 Data Collection

Tahap pertama adalah pengumpulan dataset wisata Yogyakarta yang berasal dari beberapa sumber dataset.

Dataset kemudian digunakan sebagai sumber utama dalam proses ETL dan pembangunan Data Warehouse.

---

## 7.2 Data Cleaning

Tahap data cleaning dilakukan menggunakan Python pada Google Colab untuk memastikan data siap digunakan pada proses analytics dan Business Intelligence.

### Handling Missing Value

Nilai kosong pada dataset dibersihkan menggunakan metode:

* median untuk data numerik
* mode untuk data kategori

```python
tour['Price'] = tour['Price'].fillna(
    tour['Price'].median()
)
```

---

### Penghapusan Duplicate

Data duplikat dihapus agar tidak menyebabkan kesalahan analytics.

```python
tour = tour.drop_duplicates()
```

---

### Normalisasi Data

Normalisasi dilakukan untuk menyamakan skala data numerik agar dapat digunakan pada proses analytics dan metode SAW.

Formula normalisasi:

x' = (x - xmin) / (xmax - xmin)

---

### Transformasi Data

Transformasi data dilakukan dengan:

* konversi tipe data
* normalisasi kategori wisata
* transformasi atribut numerik
* merge dataset
* feature engineering

---

## 7.3 ETL Process (Extract, Transform, Load)

### A. Extract

Tahap extract dilakukan dengan membaca seluruh dataset menggunakan Python pada Google Colab.

```python
tour = pd.read_csv('/content/tour.csv')
rating = pd.read_csv('/content/tour_rating.csv')
user = pd.read_csv('/content/user.csv')
raw = pd.read_csv('/content/raw_data.csv')
```

---

### B. Transform

Tahap transform dilakukan untuk membersihkan dan menyesuaikan data agar siap digunakan untuk analytics.

Proses transformasi meliputi:

* Data cleaning
* Handling missing value
* Penghapusan duplicate
* Normalisasi kategori
* Konversi tipe data
* Normalisasi atribut numerik
* Merge dataset
* Feature engineering

Contoh proses merge dataset:

```python
merged = pd.merge(
    tour,
    raw,
    left_on='Place_Name',
    right_on='nama',
    how='left'
)
```

Contoh feature engineering:

```python
merged['popularity_score'] = (
    merged['vote_average'] *
    merged['vote_count']
)
```

---

### C. Load

Tahap load dilakukan dengan mengekspor dataset hasil ETL menjadi CSV untuk kemudian diimport ke database warehouse MySQL.

Output hasil ETL:

* fact_tourism.csv
* dim_tour.csv
* dim_category.csv
* dim_user.csv
* dim_location.csv

Contoh export CSV:

```python
fact_tourism.to_csv(
    'fact_tourism.csv',
    index=False
)
```

---

# 8. Star Schema

Struktur Data Warehouse pada project ini menggunakan pendekatan Star Schema.

Star Schema dipilih karena:

* lebih sederhana
* mudah dipahami
* optimal untuk query analytics
* cocok untuk dashboard Business Intelligence
* mendukung proses agregasi data

Struktur Star Schema terdiri dari:

* 1 Fact Table
* beberapa Dimension Table

<img width="1536" height="1024" alt="star schema" src="https://github.com/user-attachments/assets/019722ff-b2a6-4fea-b248-671c03ff275e" />


---

## 8.1 Fact Table

Fact table digunakan untuk menyimpan data metrik utama yang digunakan pada proses analytics dan Business Intelligence.

### FACT_TOURISM

| Attribute        |
| ---------------- |
| place_id         |
| category_id      |
| rating           |
| vote_average     |
| vote_count       |
| popularity_score |
| htm_weekday      |
| htm_weekend      |

Fact table berisi data numerik yang digunakan untuk:

* analytics
* aggregation
* dashboard visualization
* popularity analysis
* recommendation insight

---

## 8.2 Dimension Table

Dimension table digunakan untuk menyimpan data deskriptif yang mendukung proses analytics.

### DIM_TOUR

Berisi informasi detail wisata.

### DIM_CATEGORY

Berisi kategori wisata.

### DIM_USER

Berisi data pengguna.

### DIM_LOCATION

Berisi data lokasi wisata.

### DIM_TIME

Berisi data waktu analytics.

---

# 9. Implementasi Data Warehouse

Data warehouse digunakan sebagai tempat penyimpanan data terintegrasi yang mendukung proses analisis data wisata.

Struktur warehouse memungkinkan:

* Pengolahan data lebih cepat
* Penyajian informasi lebih terstruktur
* Visualisasi data yang lebih mudah
* Analisis historis dan insight data

Data warehouse membantu proses Business Intelligence dalam menghasilkan informasi yang lebih bermanfaat dari data wisata yang tersedia.

---

# 10. Implementasi Analisis Data

Analisis data dilakukan menggunakan Python pada Google Colab. Seluruh proses mulai dari data cleaning, ETL, hingga visualisasi dilakukan secara terintegrasi dalam notebook.

## Tahapan Analisis

### 10.1 Data Cleaning

Membersihkan dan menyesuaikan data agar siap digunakan.

### 10.2 Data Exploration

Melakukan eksplorasi terhadap dataset untuk memahami pola dan karakteristik data.

### 10.3 Visualisasi Data

Membuat grafik dan chart untuk menampilkan informasi secara visual.

### 10.4 Insight Analysis

Menghasilkan insight berdasarkan hasil visualisasi dan analisis data.

---

# 11. Struktur Project

```bash
dataset/
notebook/
visualization/
README.md
```

Penjelasan struktur project:

| Folder/File    | Fungsi                               |
| -------------- | ------------------------------------ |
| dataset/       | Berisi dataset wisata                |
| notebook/      | File Google Colab / Jupyter Notebook |
| visualization/ | Hasil visualisasi grafik             |
| README.md      | Dokumentasi project                  |

---

# 12. Hasil Visualisasi dan Analisis Data

## 12.1 Visualisasi Distribusi Rating

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/c0ac30c8-2fc5-489c-9ac4-9f230fa14423" />

### Analisis

Berdasarkan visualisasi distribusi rating:

* Mayoritas tempat wisata memiliki rating tinggi.
* Nilai rata-rata rating berada di angka 4.44 dari 5.0.
* Sebanyak 75% tempat wisata memiliki rating di atas 4.3.
* Sangat sedikit destinasi wisata yang memiliki rating buruk di bawah 3.0.

### Insight

Hal ini menunjukkan bahwa tingkat kepuasan pengunjung terhadap wisata di Yogyakarta tergolong sangat baik.

---

## 12.2 Visualisasi Jenis Wisata

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/a0182bd0-293a-4418-9632-ba316e35a69f" />

### Analisis

Kategori wisata yang paling mendominasi adalah:

* Wisata Alam : 27 tempat
* Wisata Budaya dan Sejarah : 24 tempat
* Wisata Pantai : 23 tempat

### Insight

Data menunjukkan bahwa Yogyakarta memiliki potensi besar pada sektor:

* Ekowisata
* Wisata alam
* Wisata budaya dan sejarah

Keanekaragaman kategori wisata menjadi salah satu daya tarik utama daerah ini.

---

## 12.3 Top 10 Wisata Terpopuler

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/461b182e-6cdf-4efe-80f7-29c0d42c2862" />

### Analisis

Destinasi dengan jumlah ulasan tertinggi adalah:

1. Candi Borobudur — 81.922 ulasan
2. Candi Prambanan — 71.751 ulasan
3. Tebing Breksi — 51.431 ulasan

### Insight

* Wisata budaya dan sejarah masih menjadi daya tarik utama wisatawan.
* Tempat wisata buatan seperti Gembira Loka Zoo dan Taman Sari juga memiliki tingkat popularitas tinggi.
* Walaupun wisata alam mendominasi jumlah kategori, interaksi pengunjung terbesar tetap berada pada wisata budaya dan buatan.

---

## 12.4 Peta Persebaran Tempat Wisata

<img width="981" height="790" alt="image" src="https://github.com/user-attachments/assets/d796cd99-a54e-4dd8-8098-8a1c4c1af6ae" />

### Analisis

Berdasarkan koordinat:

* Latitude berada pada rentang -7.5 hingga -8.2
* Longitude berada pada rentang 109.9 hingga 110.7

Persebaran lokasi wisata menunjukkan:

* Wisata pantai banyak berada di wilayah selatan
* Wisata budaya dan wisata buatan dominan di pusat kota
* Wisata alam banyak tersebar di wilayah utara dan pinggiran

### Insight

Pola persebaran wisata menunjukkan hubungan erat antara kategori wisata dengan kondisi geografis wilayah Yogyakarta.

---

# 13. Kesimpulan

Berdasarkan hasil implementasi project Data Warehouse Wisata Yogyakarta dapat disimpulkan bahwa:

1. Konsep Data Warehouse berhasil diterapkan untuk mengelola data wisata secara terstruktur.
2. Proses ETL membantu menghasilkan data yang lebih bersih dan siap dianalisis.
3. Visualisasi data mampu membantu pengguna memahami informasi dengan lebih mudah.
4. Wisata budaya, sejarah, dan alam menjadi kategori dominan di Yogyakarta.
5. Rating wisata yang tinggi menunjukkan tingkat kepuasan pengunjung yang baik.
6. Persebaran lokasi wisata menunjukkan karakter geografis wisata Yogyakarta yang beragam.
7. Implementasi Star Schema membantu proses query analytics menjadi lebih cepat dan terstruktur.
8. Business Intelligence membantu menghasilkan insight wisata yang lebih informatif dan mendukung pengambilan keputusan.

---

# 14. Repository Project

Project dikelola menggunakan GitHub untuk dokumentasi, penyimpanan dataset, notebook ETL, visualisasi data, serta implementasi Data Warehouse dan Business Intelligence.
