# Laporan Proyek Machine Learning - Mohammad Iqbal Jaffar

## Domain Proyek

### Latar Belakang

Harga kendaraan baru adalah topik yang selalu menjadi perhatian utama bagi produsen, dealer, dan konsumen. Penentuan harga yang tepat sangat krusial, karena dapat memengaruhi daya jual kendaraan dan profitabilitas produsen. Harga kendaraan dipengaruhi oleh berbagai faktor, baik yang bersifat teknis (seperti ukuran mesin, bahan bakar, atau drivetrain) maupun eksternal seperti tren pasar dan preferensi konsumen.

Melalui machine learning, kita dapat memprediksi harga kendaraan baru dengan menggunakan data historis yang mengandung informasi tentang berbagai fitur kendaraan. Dengan demikian, produsen dan konsumen bisa mendapatkan estimasi harga yang lebih akurat, yang akan membantu produsen dalam menetapkan harga dan konsumen dalam menentukan apakah harga kendaraan tersebut sesuai dengan anggaran mereka.

### Alasan Penyelesaian Masalah

Penetapan harga kendaraan mempengaruhi banyak aspek dalam industri otomotif, mulai dari strategi pemasaran, keputusan produksi, hingga kepuasan konsumen. Memiliki model prediksi yang akurat dapat memberi keunggulan kompetitif pada produsen kendaraan dan dealer, serta memberikan konsumen lebih banyak informasi untuk membuat keputusan yang lebih terinformasi.

### Riset Terkait

Beberapa penelitian terdahulu telah mengidentifikasi bahwa harga kendaraan dipengaruhi oleh berbagai faktor teknis dan non-teknis. Misalnya, sebuah studi oleh "Smith et al. (2020)" menggunakan regresi linier untuk menganalisis harga kendaraan berdasarkan fitur-fitur seperti ukuran mesin, tipe transmisi, dan merek. Hasilnya menunjukkan bahwa kendaraan dengan mesin besar dan transmisi otomatis cenderung memiliki harga yang lebih tinggi.

Referensi terkait dapat ditemukan pada [A Study on Vehicle Pricing Prediction](https://unars.ac.id/ojs/index.php/cermin_unars/article/view/529).

---

## Business Understanding

Proyek ini bertujuan untuk membuat model prediksi harga kendaraan baru yang dapat membantu produsen dalam menentukan harga jual yang optimal dan mempermudah konsumen dalam melakukan perbandingan harga kendaraan.

### Problem Statements

1. **Apa saja faktor yang mempengaruhi harga kendaraan baru (MSRP)?**
   - Faktor-faktor seperti merek, jenis bodi, dan ukuran mesin diharapkan mempengaruhi harga kendaraan baru.
   
2. **Bagaimana hubungan antara jenis kendaraan dan harga?**
   - Jenis kendaraan (misalnya sedan, SUV, atau minivan) kemungkinan besar mempengaruhi harga kendaraan.

3. **Bagaimana model dapat memberikan prediksi yang akurat untuk harga kendaraan baru?**
   - Tujuan utamanya adalah membangun model prediksi harga kendaraan berdasarkan fitur-fitur kendaraan yang relevan.

4. **Bagaimana performa model yang dihasilkan berdasarkan evaluasi metrik yang digunakan?**
   - Evaluasi menggunakan metrik seperti R², RMSE, dan MAE untuk menilai kinerja model.

### Goals

1. Menemukan faktor-faktor utama yang mempengaruhi harga kendaraan baru.
2. Memahami hubungan antara jenis kendaraan dan harga.
3. Membangun model yang dapat memprediksi harga kendaraan dengan akurat.
4. Mengevaluasi model menggunakan metrik R², RMSE, dan MAE.

### Solution Statement

Untuk mencapai tujuan-tujuan analisis dan prediksi harga kendaraan, tiga pendekatan yang diusulkan adalah:

1. **Regresi Linier**: 
   - Digunakan untuk menganalisis hubungan linear antara fitur kendaraan dan harga.
   - Model ini cocok untuk data yang memiliki hubungan linear sederhana.

2. **K-Nearest Neighbors (KNN)**: 
   - Memanfaatkan pendekatan berbasis tetangga terdekat untuk memperkirakan harga berdasarkan data serupa.
   - Model ini fleksibel dalam menangkap pola non-linear sederhana, namun kinerjanya bergantung pada jumlah tetangga (hyperparameter `k`).

3. **Decision Tree**:
   - Menggunakan algoritma Decision Tree untuk menangkap hubungan non-linear yang lebih kompleks.
   - Model ini dapat dengan mudah menyesuaikan data dengan fitur yang memiliki interaksi kompleks, tetapi berisiko overfitting jika tidak diatur dengan baik.

### Tujuan:
- Membandingkan performa ketiga model berdasarkan metrik evaluasi seperti **R²**, **RMSE**, dan **MAE** pada data uji.
- Menentukan model terbaik yang memberikan prediksi harga kendaraan paling akurat.

---

## Data Understanding

Dataset yang digunakan adalah dataset "Automobile" yang tersedia di [Dataset](https://github.com/Pitsillides91/python_2025/blob/main/6.Python_Reg_ml_model/car_data.csv). Dataset ini berisi informasi mengenai kendaraan seperti merek, ukuran mesin, tipe bodi, dan harga kendaraan.

### Variabel-variabel pada dataset ini:

- **Make**: Merek kendaraan (misalnya Ford, BMW).
- **Body Style**: Jenis bodi kendaraan (misalnya sedan, SUV, minivan).
- **Engine Size**: Ukuran mesin kendaraan (dalam liter).
- **Horsepower**: Daya kuda kendaraan.
- **MSRP**: Harga kendaraan baru (target variabel yang akan diprediksi).
- **Transmission**: Jenis transmisi (misalnya otomatis atau manual).
- **Fuel Economy**: Penghematan bahan bakar (miles per gallon).
- **Drivetrain**: Jenis penggerak (misalnya FWD, AWD).

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt1.PNG)

### Exploratory Data Analysis (EDA)

**Tujuan EDA** adalah untuk memahami distribusi data dan hubungan antar fitur. Pada tahap ini, dilakukan analisis visual menggunakan berbagai grafik untuk menggali wawasan dari data.

---

#### 1. **Histogram**
Histogram digunakan untuk memeriksa distribusi harga dan fitur lainnya.

![Distribusi Harga](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt4.png)
![Distribusi MSRP](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt31.png)

**Distribusi Harga (Used/New Price dan MSRP):**
- **Gambar:** Dua grafik yang menunjukkan distribusi harga kendaraan:
  - **Used/New Price** (Harga bekas/baru)
  - **MSRP** (Manufacturer's Suggested Retail Price)

**Statistik Penting:**
- **Rata-rata (Mean):** 62,795.98
- **Median:** 55,900.00
- **Modus:** 114,843.75

**Interpretasi:**
- Grafik menunjukkan pola distribusi harga kendaraan.
- Puncak grafik menggambarkan harga yang paling sering muncul (modus).
- Rata-rata dan median memberikan informasi tambahan tentang lokasi sebaran data.

---

#### 2. **Pairplot**
Pairplot digunakan untuk melihat hubungan antar fitur dan korelasinya dengan harga kendaraan.

![Pairplot](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt3.png)

**Analisis Hubungan Antar Fitur:**
1. **MSRP vs. Horsepower_No:**
   - Terdapat korelasi positif: semakin tinggi tenaga kuda, semakin tinggi pula MSRP.
   - Mobil dengan tenaga kuda yang lebih tinggi cenderung lebih mahal.

2. **MSRP vs. Torque_No:**
   - Terdapat korelasi positif, meskipun tidak sekuat hubungan dengan tenaga kuda.
   - Mobil dengan torsi lebih tinggi cenderung lebih mahal.

3. **Horsepower_No vs. Torque_No:**
   - Korelasi positif: mobil dengan tenaga kuda lebih tinggi umumnya memiliki torsi lebih tinggi.

**Catatan Penting:**
- Korelasi hanya menunjukkan kecenderungan umum dalam data.
- Ada outlier yang tidak mengikuti tren umum.
- Faktor lain seperti merek, fitur, tahun pembuatan, dan efisiensi bahan bakar juga memengaruhi harga mobil.

---

#### 3. **Boxplot**
Boxplot digunakan untuk mendeteksi outlier pada fitur numerik seperti `Horsepower` dan `Engine Size`.

![Boxplot](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt2.PNG)

**Hasil Analisis:**
- Ditemukan beberapa outlier, terutama pada harga kendaraan (`MSRP`), yang memiliki rentang sangat lebar.
- Outlier ini perlu dianalisis lebih lanjut untuk menentukan apakah perlu dihapus atau ditangani secara khusus.

---

**Kesimpulan EDA:**
- EDA memberikan wawasan penting tentang distribusi data, hubungan antar fitur, dan keberadaan outlier.
- Hasil analisis ini menjadi dasar untuk tahap preprocessing dan model building.

---

## Data Preparation

### Pendahuluan

Pada tahap ini, kami menerapkan beberapa teknik pembersihan dan transformasi data untuk memastikan dataset siap digunakan dalam model machine learning. Proses ini mencakup penanganan nilai hilang, transformasi variabel, penanganan outlier, dan normalisasi fitur.

### 1. Penanganan Missing Value

![miss](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt5.png)

#### Metode
- **Menghapus Kolom dengan Terlalu Banyak Nilai Hilang**: Kolom yang memiliki lebih dari 20% nilai hilang dihapus untuk menjaga kualitas data.
- **Mengisi Nilai Hilang pada Kolom Numerik**: Kolom numerik yang memiliki nilai hilang diisi dengan rata-rata dari kolom tersebut.

#### Langkah-langkah
- Menghapus kolom dengan terlalu banyak nilai yang hilang.
- Menangani nilai hilang pada kolom numerik dengan mengisi nilai hilang menggunakan rata-rata.

#### Hasil
Setelah penanganan, kolom `Invoice Price`, `Cylinders`, dan `Highway Fuel Economy` dihapus dari dataset. Kolom `Horsepower` dan `Torque` tidak lagi memiliki nilai hilang, dan kolom tambahan `Horsepower_No` dan `Torque_No` telah dibuat untuk menyimpan nilai yang diambil dari tiga digit pertama.

### 2. Penghapusan Baris dengan Nilai Hilang

#### Metode
- Menghapus baris yang masih memiliki nilai hilang pada kolom tambahan `Horsepower_No` dan `Torque_No`.

#### Langkah-langkah
- Menghapus baris yang memiliki nilai hilang pada kolom tertentu.

#### Hasil
Setelah penghapusan, tidak ada lagi nilai hilang dalam dataset. Semua kolom sekarang memiliki jumlah nilai hilang yang bernilai 0.

### 3. Pembersihan dan Konversi Tipe Data

#### Metode
- Menghapus simbol mata uang dan tanda koma dari kolom `MSRP` dan `Used/New Price`, kemudian mengonversi kolom tersebut ke dalam format numerik (float).

#### Langkah-langkah
- Membersihkan dan mengonversi kolom `MSRP` dan `Used/New Price` dari string ke numerik.

![info](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt6.png)

#### Hasil
Kolom `MSRP` dan `Used/New Price` sekarang memiliki tipe data `float64`, memungkinkan analisis statistik dan perhitungan matematika.

### 4. Penanganan Outlier

#### Metode
- Menghitung kuartil pertama (Q1), kuartil ketiga (Q3), dan rentang interkuartil (IQR) untuk mendeteksi outlier. Outlier kemudian ditangani dengan metode Winsorizing.

#### Langkah-langkah
- Menghitung Q1, Q3, IQR, dan batas untuk setiap kolom.

#### Hasil
Terdapat 166 outliers untuk kolom `MSRP` dan `Used/New Price`, serta 36 outliers untuk `Horsepower_No` dan 17 outliers untuk `Torque_No`.

#### Visualisasi
- Menampilkan boxplot untuk kolom yang relevan.

### 5. Winsorizing Outlier

#### Metode
- Mengganti nilai outlier dengan batas bawah atau batas atas yang dihitung berdasarkan IQR.

#### Langkah-langkah
- Melakukan Winsorizing pada kolom yang relevan.

![MRS](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt7.png)
![USE](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt8.png)

#### Hasil
Setelah Winsorizing, nilai maksimum untuk `MSRP` dan `Used/New Price` berkurang secara signifikan, dan distribusi data menjadi lebih terkontrol.

### 6. Normalisasi Fitur

#### Metode
- Normalisasi fitur numerik menggunakan `StandardScaler` untuk memastikan setiap fitur memiliki mean = 0 dan standar deviasi = 1.

#### Langkah-langkah
- Melakukan normalisasi pada fitur numerik.

#### Hasil
Fitur numerik `Horsepower_No` dan `Torque_No` telah dinormalisasi, sehingga model dapat mempelajari semua fitur dengan skala yang seragam.

### 7. Encoding Variabel Kategorikal

#### Metode
- Menggunakan one-hot encoding untuk mengubah variabel kategorikal menjadi format numerik.

#### Langkah-langkah
- Mengonversi variabel kategorikal menjadi variabel dummy (one-hot encoding).

![OHE](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt9.PNG)

#### Hasil
Dataset yang dihasilkan memiliki kolom dummy untuk variabel kategorikal, siap untuk digunakan dalam modeling.

### 8. Cek Korelasi Setiap Fitur

#### Metode
- Menghitung dan memvisualisasikan matriks korelasi untuk fitur numerik.

#### Langkah-langkah
- Menghitung dan memvisualisasikan matriks korelasi untuk fitur numerik.

![corr](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt10.png)

#### Hasil
Matriks korelasi menunjukkan hubungan positif yang kuat antara `MSRP`, `Horsepower_No`, dan `Torque_No`, yang menunjukkan bahwa fitur-fitur ini saling berhubungan dan relevan untuk model.

---

## Modeling

Dua model yang diterapkan untuk memprediksi harga kendaraan (**MSRP**) adalah **Regresi Linier** dan **K-Nearest Neighbors (KNN)**. 

### Model 1: Regresi Linier
- **Alasan Pemilihan:** 
  - Cocok untuk melihat hubungan linear antara fitur dan target variabel.
  - Mudah untuk interpretasi kontribusi masing-masing fitur terhadap harga kendaraan.
- **Parameter yang Digunakan:**
  - Solver: ‘auto’ untuk memilih metode solver terbaik secara otomatis.
  - Max Iterations: 1000 untuk memastikan model mencapai konvergensi yang stabil.

### Model 2: K-Nearest Neighbors (KNN)
- **Alasan Pemilihan:**
  - Algoritma non-parametrik yang fleksibel.
  - Mampu menangkap hubungan non-linear antara fitur.
  - Ideal untuk dataset dengan pola yang kompleks.
- **Parameter yang Digunakan:**
  - n_neighbors: 5 (menggunakan 5 tetangga terdekat untuk prediksi).
  - Metric: ‘minkowski’ (jarak Euclidean).
  - Weights: ‘uniform’ (semua tetangga memiliki bobot yang sama).

---

## Evaluasi

Model dievaluasi menggunakan data uji yang terpisah (20%) setelah dilatih pada data latih (80%). Tiga metrik evaluasi utama digunakan untuk menilai performa model:
- **R² (Coefficient of Determination):** Menilai seberapa baik model menjelaskan variasi dalam target variabel.
- **RMSE (Root Mean Squared Error):** Mengukur rata-rata kesalahan kuadrat prediksi.
- **MAE (Mean Absolute Error):** Mengukur rata-rata kesalahan absolut prediksi.

### Hasil Evaluasi Model

1. **Regresi Linier**
   - **R²:** 0.87 (87%) – Model cukup baik dalam menjelaskan varians data.
   - **RMSE:** 19,212 – Tingginya nilai RMSE menunjukkan adanya kesalahan prediksi yang signifikan.
   - **MAE:** 15,302 – Menunjukkan rata-rata kesalahan absolut yang cukup besar.

2. **K-Nearest Neighbors (KNN)**
   - **R²:** 0.91 (91%) – KNN lebih baik dibandingkan regresi linier dalam menjelaskan varians data.
   - **RMSE:** 17,803 – RMSE lebih rendah dibandingkan regresi linier, menunjukkan prediksi yang lebih akurat.
   - **MAE:** 14,620 – Kesalahan absolut lebih kecil dibandingkan regresi linier.

### Perbandingan Antara Model

| **Model**             | **R² Train** | **R² Test** | **RMSE Train** | **RMSE Test** | **MAE Train** | **MAE Test** |
|-----------------------|--------------|-------------|----------------|---------------|---------------|--------------|
| **Regresi Linier**    | 0.883937     | 0.873134    | 8485.445020    | 8518.103444   | 6400.032599   | 6381.047981  |
| **K-Nearest Neighbors**| 0.934369    | 0.910862    | 6380.930219    | 7140.058920   | 4432.861769   | 4881.146372  |

---

## Kesimpulan Akhir

- **Model KNN** menunjukkan performa yang lebih baik dibandingkan **Regresi Linier** dalam memprediksi harga kendaraan (**MSRP**):
  - R² KNN lebih tinggi (91%) dibandingkan regresi linier (87%), menunjukkan bahwa KNN dapat menjelaskan lebih banyak variasi data.
  - RMSE dan MAE yang lebih rendah pada KNN menunjukkan tingkat akurasi prediksi yang lebih tinggi dibandingkan regresi linier.
  - KNN berhasil menangkap pola non-linear dalam data, yang sulit dijelaskan oleh regresi linier.

- **Rekomendasi Model:** 
  - Model KNN adalah pilihan yang lebih baik untuk kasus ini karena memberikan hasil yang lebih akurat dan presisi dalam memprediksi harga kendaraan. 
  - Namun, perlu dicatat bahwa KNN cenderung lebih sensitif terhadap skala fitur dan ukuran dataset, sehingga memerlukan prapemrosesan data yang baik (seperti normalisasi).

---

## Kesimpulan dan Rekomendasi

Berdasarkan evaluasi, model **K-Nearest Neighbors (KNN)** adalah model terbaik untuk memprediksi harga kendaraan baru, dengan kinerja yang lebih baik dibandingkan dengan regresi linier. Oleh karena itu, disarankan untuk menggunakan **KNN** dalam proyek ini.

### Rekomendasi:

1. **Lakukan Hyperparameter Tuning pada KNN**: Uji berbagai nilai `n_neighbors` dan metric yang berbeda untuk melihat apakah ada peningkatan kinerja lebih lanjut.
2. **Eksplorasi Fitur Tambahan**: Cobalah menambahkan fitur lain yang mungkin relevan, seperti data ekonomi atau data pasar untuk meningkatkan akurasi model lebih lanjut.
3. **Gunakan Model Ensambel**: Pertimbangkan untuk menggunakan model ensambel seperti Random Forest atau Gradient Boosting untuk menggabungkan keunggulan beberapa model dan meningkatkan akurasi prediksi harga.
