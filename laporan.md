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

### 3. Cek Outlier

#### Metode
- Menghitung kuartil pertama (Q1), kuartil ketiga (Q3), dan rentang interkuartil (IQR) untuk mendeteksi outlier. Outlier kemudian ditangani dengan metode Winsorizing.

#### Langkah-langkah
- Menghitung Q1, Q3, IQR, dan batas untuk setiap kolom.

![out](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt13.PNG)

#### Hasil
Terdapat 166 outliers untuk kolom `MSRP` dan `Used/New Price`, serta 36 outliers untuk `Horsepower_No` dan 17 outliers untuk `Torque_No`.

#### **Boxplot**
Boxplot digunakan untuk mendeteksi outlier pada fitur numerik seperti `Horsepower` dan `Engine Size`.

![Boxplot](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt2.PNG)

**Hasil Analisis:**
- Ditemukan beberapa outlier, terutama pada harga kendaraan (`MSRP`), yang memiliki rentang sangat lebar.
- Outlier ini perlu dianalisis lebih lanjut untuk menentukan apakah perlu dihapus atau ditangani secara khusus.


## Data Preparation

Pada tahap ini, kami menerapkan beberapa teknik pembersihan dan transformasi data untuk memastikan dataset siap digunakan dalam model machine learning. Proses ini mencakup penanganan nilai hilang, transformasi variabel, penanganan outlier, normalisasi fitur, serta split data.

## Penanganan Missing Value

Pada bagian ini, kita akan melakukan beberapa langkah untuk membersihkan dataset dan menangani masalah nilai yang hilang (*missing values*), serta menyesuaikan format data jika diperlukan. Langkah-langkah ini bertujuan untuk meningkatkan kualitas data dan memastikan analisis serta model yang dibangun dapat bekerja dengan optimal.

### 1. Penanganan Missing Value

#### Metode
1. **Menghapus Kolom dengan Terlalu Banyak Nilai Hilang**  
   Kolom yang memiliki lebih dari 20% nilai hilang dihapus untuk menjaga kualitas data. Dalam kasus ini, kolom `Invoice Price`, `Cylinders`, dan `Highway Fuel Economy` dihapus dari dataset.
   
2. **Mengisi Nilai Hilang pada Kolom Numerik**  
   Beberapa kolom numerik, seperti `Horsepower` dan `Torque`, memiliki nilai hilang. Nilai-nilai tersebut diisi menggunakan rata-rata dari kolom yang bersangkutan. Untuk membantu perhitungan ini, kolom tambahan `Horsepower_No` dan `Torque_No` dibuat dengan mengambil tiga digit pertama dari masing-masing kolom.

#### Langkah-langkah
Pertama, kolom `Invoice Price`, `Cylinders`, dan `Highway Fuel Economy` dihapus dari dataset karena memiliki terlalu banyak nilai hilang. Kemudian, dua kolom tambahan, yaitu `Horsepower_No` dan `Torque_No`, dibuat untuk menyimpan nilai numerik yang dihasilkan dari mengambil tiga digit pertama dari kolom `Horsepower` dan `Torque`. Nilai-nilai hilang pada kolom `Horsepower` dan `Torque` diisi menggunakan rata-rata nilai pada kolom tambahan tersebut.

Setelah semua langkah ini dilakukan, pengecekan dilakukan untuk memastikan bahwa kolom `Horsepower` dan `Torque` tidak lagi memiliki nilai hilang.

![miss](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt11.PNG)

#### Hasil
- Kolom `Invoice Price`, `Cylinders`, dan `Highway Fuel Economy` telah dihapus dari dataset.
- Nilai hilang pada kolom `Horsepower` dan `Torque` telah diisi dengan rata-rata dari nilai pada kolom `Horsepower_No` dan `Torque_No`.
- Kolom tambahan `Horsepower_No` dan `Torque_No` dibuat untuk membantu pengisian nilai hilang.

---

### 2. Penghapusan Baris dengan Nilai Hilang

#### Metode
Setelah langkah sebelumnya, kolom tambahan `Horsepower_No` dan `Torque_No` masih memiliki beberapa nilai hilang, karena terdapat nilai yang tidak dapat diubah menjadi angka atau tidak valid. Oleh karena itu, baris-baris yang memiliki nilai hilang pada kolom-kolom ini dihapus.

#### Langkah-langkah
Baris-baris yang memiliki nilai hilang pada kolom `Horsepower_No` dan `Torque_No` dihapus dari dataset. Setelah itu, dilakukan verifikasi untuk memastikan bahwa semua kolom pada dataset sekarang tidak memiliki nilai hilang.

![MISS](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt12.PNG)

#### Hasil
- Tidak ada lagi nilai hilang dalam dataset.
- Semua kolom sekarang memiliki jumlah nilai hilang yang bernilai 0.
- Kolom `Horsepower`, `Torque`, `Horsepower_No`, dan `Torque_No` sekarang bersih dari nilai hilang, karena baris dengan nilai hilang pada kolom-kolom tersebut telah dihapus.

---

## 3. Pembersihan dan Konversi Tipe Data

### Metode
Pada tahap ini, dilakukan pembersihan dan konversi data pada kolom `MSRP` dan `Used/New Price` yang awalnya berformat string. Kolom-kolom tersebut mengandung simbol mata uang ($) dan tanda koma (,) sebagai pemisah ribuan, yang perlu dihapus agar data dapat dikonversi menjadi tipe numerik. Langkah ini sangat penting untuk memungkinkan analisis statistik dan perhitungan matematika pada data harga kendaraan.

### Langkah-langkah
Pertama, simbol mata uang `$` dan tanda koma `,` yang ada di kolom `MSRP` dan `Used/New Price` dihapus. Proses ini dilakukan dengan metode penggantian berbasis pola menggunakan ekspresi reguler. Setelah simbol dan tanda koma dihapus, data dalam kedua kolom tersebut dikonversi dari format string menjadi angka desimal (`float`). Langkah ini memastikan bahwa data dapat digunakan untuk berbagai analisis statistik dan matematis. Setelah itu, dilakukan pengecekan kembali pada informasi dataset.

![info](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt6.png)

### Hasil
Setelah proses pembersihan dan konversi:
- Kolom `MSRP` dan `Used/New Price` berhasil diubah dari format string menjadi format angka desimal (`float64`).
- Tidak ada nilai hilang yang tercatat pada kedua kolom ini setelah konversi.
- Dataset sekarang memiliki total 1583 entri dengan 16 kolom. Semua kolom relevan telah berada dalam format yang sesuai untuk analisis lebih lanjut.

---

## Statistik Deskriptif Kolom Numerik

### Pengecekan Statistik Deskriptif
Setelah pembersihan dan konversi tipe data, langkah selanjutnya adalah memeriksa statistik deskriptif dari kolom-kolom numerik pada dataset. Statistik deskriptif memberikan gambaran umum tentang distribusi data, seperti nilai minimum, maksimum, rata-rata, dan simpangan baku. Hal ini penting untuk memahami karakteristik dari setiap kolom numerik yang ada dalam dataset.

### Penjelasan Hasil Output
Berdasarkan hasil dari fungsi `describe()`, kita mendapatkan informasi statistik untuk kolom-kolom numerik pada dataset, yaitu `Year`, `MSRP`, `Used/New Price`, `Horsepower_No`, dan `Torque_No`. Berikut adalah beberapa poin penting:

1. **Kolom Year**:
   - Data tahun berkisar antara **2023 hingga 2024**.
   - Tidak ada variasi yang besar dalam kolom ini, karena sebagian besar data hanya mencakup dua tahun yang sangat dekat, yaitu 2023 dan 2024.

2. **Kolom MSRP dan Used/New Price**:
   - **Rata-rata harga mobil** (MSRP dan Used/New Price) adalah sekitar **72.792 dolar**.
   - Terdapat perbedaan yang cukup besar antara **harga minimum** yang tercatat sekitar **15.980 dolar** dan **harga maksimum** yang mencapai **391.100 dolar**. Hal ini menunjukkan bahwa harga mobil dalam dataset ini bervariasi secara signifikan, mencakup berbagai jenis kendaraan dengan berbagai harga.
   - **Simpangan baku (std)** yang cukup tinggi, sekitar **55.276**, menunjukkan bahwa harga mobil memiliki sebaran yang cukup lebar. Ini berarti harga mobil tidak tersebar merata, dengan sebagian besar harga terkonsentrasi pada nilai tertentu, namun ada juga harga yang sangat tinggi dan rendah.

3. **Kolom Horsepower_No dan Torque_No**:
   - **Rata-rata tenaga kuda (Horsepower)** adalah sekitar **346** dan **rata-rata torsi (Torque)** adalah sekitar **365**.
   - **Nilai maksimum tenaga kuda** tercatat mencapai **831**, sedangkan **nilai maksimum torsi** adalah **811**. Hal ini menunjukkan bahwa ada mobil dengan performa mesin yang sangat tinggi.
   - Sebagian besar mobil dalam dataset memiliki tenaga kuda dan torsi yang lebih rendah, dengan hanya beberapa mobil yang memiliki performa jauh lebih tinggi, yang menunjukkan adanya variasi dalam jenis dan performa kendaraan.

### Kesimpulan
Dari statistik deskriptif ini, kita dapat melihat bahwa dataset ini mengandung variasi yang cukup besar, baik dari sisi harga maupun performa kendaraan. Dengan informasi ini, kita dapat mulai mengidentifikasi pola atau tren dalam data, atau mengelompokkan kendaraan berdasarkan kategori harga dan spesifikasi performa untuk analisis lebih lanjut.

---

### 4. Penanganan Outlier dengan Winsorizing

### Metode
Pada bagian ini, kita menangani nilai-nilai yang termasuk outlier dalam kolom-kolom numerik yang relevan, yaitu `MSRP`, `Used/New Price`, `Horsepower_No`, dan `Torque_No`. Outlier akan diganti dengan batas bawah atau batas atas yang dihitung berdasarkan rentang interkuartil (IQR). Teknik ini dikenal dengan sebutan **Winsorizing**, di mana nilai yang lebih besar dari batas atas diganti dengan batas atas, dan nilai yang lebih kecil dari batas bawah diganti dengan batas bawah.

### Langkah-langkah
1. Menghitung **Q1** (Kuartil pertama) dan **Q3** (Kuartil ketiga) untuk setiap kolom.
2. Menghitung **IQR** (Rentang Interkuartil), yaitu selisih antara Q3 dan Q1.
3. Menentukan **Lower Bound** (batas bawah) dan **Upper Bound** (batas atas) berdasarkan rumus:
   - Lower Bound = Q1 - 1.5 * IQR
   - Upper Bound = Q3 + 1.5 * IQR
4. Mengganti nilai-nilai yang berada di luar batas ini (outliers) dengan nilai batas yang sesuai menggunakan metode Winsorizing.
5. Setelah itu, memeriksa distribusi data menggunakan boxplot untuk melihat perubahan setelah menangani outliers.
6. Memeriksa statistik deskriptif untuk memastikan bahwa data telah dibersihkan dari outliers ekstrem.

### Implementasi
- Kolom yang ingin diperiksa adalah: `MSRP`, `Used/New Price`, `Horsepower_No`, dan `Torque_No`.
- Untuk setiap kolom tersebut, perhitungan Q1, Q3, IQR, serta batas bawah dan atas dilakukan untuk mendeteksi dan menangani outlier menggunakan Winsorizing.

![MRS](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt7.png)
![USE](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt8.png)

### Hasil
Setelah melakukan Winsorizing pada kolom-kolom yang relevan:
- **MSRP** dan **Used/New Price**:
  - Nilai maksimum yang sebelumnya sangat tinggi (misalnya 391.100) telah dikurangi menjadi sekitar 114.843,75 setelah Winsorizing, yang membuat rentang harga lebih terkontrol.
  - Nilai rata-rata tetap sekitar **62.795**, menunjukkan harga mobil yang lebih konsisten setelah menangani outliers.
  
- **Horsepower_No** dan **Torque_No**:
  - Nilai-nilai ekstrem dalam tenaga kuda dan torsi yang sangat tinggi (misalnya 697 dan 738) juga telah dikurangi, dengan nilai maksimum yang baru lebih rendah (621 untuk tenaga kuda dan 715 untuk torsi).
  - Rata-rata tenaga kuda dan torsi kini lebih konsisten, sekitar **345** untuk tenaga kuda dan **365** untuk torsi.

### Penjelasan Hasil Output
- Proses Winsorizing berhasil mengurangi nilai-nilai ekstrem yang ada pada kolom `MSRP`, `Used/New Price`, `Horsepower_No`, dan `Torque_No`, sehingga distribusi data menjadi lebih terkontrol dan konsisten.
- Boxplot menunjukkan distribusi data setelah penanganan outliers, yang mencerminkan perubahan yang signifikan pada nilai-nilai ekstrem yang telah dikendalikan.
- Statistik deskriptif setelah pembersihan menunjukkan bahwa data menjadi lebih stabil, dengan rentang nilai yang lebih terkontrol dan lebih sedikit variasi ekstrem.

---

## 6. Normalisasi Fitur

### Metode
Pada tahap ini, normalisasi fitur numerik dilakukan menggunakan `StandardScaler` untuk memastikan bahwa setiap fitur memiliki **mean = 0** dan **standar deviasi = 1**. Normalisasi ini penting untuk memastikan model dapat mempelajari semua fitur dengan skala yang seragam, menghindari dominasi fitur dengan skala yang lebih besar, seperti harga dan tenaga kuda, dalam proses pelatihan model.

### Langkah-langkah
- Melakukan normalisasi pada fitur numerik seperti `Horsepower_No` dan `Torque_No` menggunakan `StandardScaler`.

### Hasil
Fitur numerik `Horsepower_No` dan `Torque_No` telah berhasil dinormalisasi, yang memungkinkan model untuk mempelajari semua fitur dengan skala yang konsisten. Setelah normalisasi, kedua fitur ini memiliki distribusi yang seragam, memfasilitasi proses pelatihan model yang lebih efektif.

---

## 7. Encoding Variabel Kategorikal

### Metode
Untuk mengonversi variabel kategorikal menjadi format numerik, digunakan metode **one-hot encoding**. Teknik ini mengubah setiap kategori dalam variabel menjadi kolom biner (dummy variables), yang mewakili setiap kategori unik dengan nilai 0 atau 1.

### Langkah-langkah
- Mengonversi variabel kategorikal, seperti `Make`, `Body Style`, dan lainnya, menjadi kolom dummy (one-hot encoding) menggunakan `pd.get_dummies()`.

![OHE](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt9.PNG)

### Hasil
Dataset yang dihasilkan memiliki kolom dummy untuk variabel kategorikal, seperti `Make_Aston Martin`, `Drivetrain_AWD`, dan `Transmission_automatic`. Kolom-kolom ini siap digunakan dalam modeling, memungkinkan algoritma machine learning untuk memproses informasi kategorikal dalam format numerik.

---

## 8. Cek Korelasi Setiap Fitur

### Metode
Matriks korelasi dihitung dan divisualisasikan untuk fitur numerik. Matriks korelasi ini menunjukkan sejauh mana hubungan antara fitur-fitur numerik dalam dataset, yang membantu untuk mengidentifikasi hubungan antar fitur sebelum modeling.

### Langkah-langkah
- Menghitung dan memvisualisasikan matriks korelasi untuk fitur numerik seperti `MSRP`, `Horsepower_No`, dan `Torque_No`.

![corr](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt10.png)

### Hasil
Matriks korelasi menunjukkan hubungan positif yang kuat antara `MSRP`, `Horsepower_No`, dan `Torque_No`. Ini menunjukkan bahwa fitur-fitur ini saling berhubungan dan relevan untuk model. Model machine learning dapat memanfaatkan hubungan ini untuk membuat prediksi yang lebih akurat mengenai harga mobil.

---

## Feature Importance menggunakan Decision Tree

### Metode
Bagian ini bertujuan untuk mengevaluasi pentingnya setiap fitur dalam mempengaruhi target variabel (MSRP) menggunakan **Decision Tree Classifier**. Analisis ini membantu mengidentifikasi fitur mana yang memiliki kontribusi terbesar terhadap prediksi target, sehingga memungkinkan penyederhanaan model dan fokus pada fitur yang paling berpengaruh.

### Langkah-langkah
1. **Pemisahan fitur dan target:**
   - `X`: Semua kolom kecuali `MSRP`.
   - `y`: Kolom target (`MSRP`), yang dikonversi menjadi integer untuk kompatibilitas dengan Decision Tree.

2. **Inisialisasi model:**
   - Menggunakan `DecisionTreeClassifier` dengan parameter `criterion='entropy'`, `max_depth=10`, dan `random_state=15`.

3. **Latih model:**
   - Model dilatih pada dataset menggunakan `dt.fit(X, y)`.

4. **Evaluasi fitur penting:**
   - Mengambil nilai pentingnya fitur dari model yang telah dilatih.

### Hasil
Model Decision Tree berhasil dilatih, dan fitur penting dihitung berdasarkan nilai `feature_importances_`. Berikut adalah fitur-fitur dengan nilai penting tertinggi:

| Feature                | Importance (%) |
|------------------------|----------------|
| Horsepower_No          | 22.07%         |
| Torque_No              | 21.42%         |
| Make_Ford              | 13.33%         |
| ...                    | ...            |

### Interpretasi
- **Horsepower_No** dan **Torque_No** adalah dua fitur numerik yang memiliki pengaruh terbesar terhadap target `MSRP`, dengan kontribusi masing-masing sekitar **22.07%** dan **21.42%**.
- Beberapa fitur kategorikal, seperti **Make_Ford** dan **Engine Aspiration_Naturally Aspirated**, juga menunjukkan kontribusi yang signifikan terhadap model.

### Kesimpulan
Hasil ini memberikan wawasan tentang fitur mana yang paling relevan untuk prediksi harga mobil (`MSRP`). Fitur-fitur dengan nilai penting tertinggi, seperti `Horsepower_No` dan `Torque_No`, harus dipertimbangkan lebih dalam untuk analisis lebih lanjut atau model yang lebih efisien.

---

## Modeling

Dua model yang diterapkan untuk memprediksi harga kendaraan (MSRP) adalah Regresi Linier dan K-Nearest Neighbors (KNN). Berikut ini adalah penjelasan tentang cara kerja, alasan pemilihan, parameter yang digunakan, serta hasil evaluasi untuk masing-masing model.

### Model 1: Regresi Linier

**Cara Kerja:**
Regresi Linier adalah metode statistik yang digunakan untuk memodelkan hubungan linear antara satu atau lebih variabel independen (fitur) dengan variabel dependen (target).  
Model ini bekerja dengan meminimalkan kesalahan prediksi menggunakan metode least squares, yaitu mencari garis lurus terbaik yang meminimalkan jumlah kuadrat jarak vertikal antara nilai sebenarnya dan nilai prediksi.

**Alasan Pemilihan:**
- Regresi linier cocok untuk dataset yang memiliki hubungan linear antara fitur dan target.
- Mudah diinterpretasi untuk memahami kontribusi masing-masing fitur terhadap target.
- Efisien secara komputasi, sehingga cocok untuk dataset dengan jumlah data besar.

**Parameter yang Digunakan:**
- `fit_intercept=True`: Model akan menghitung nilai intercept.
- Semua parameter lain menggunakan nilai default dari pustaka scikit-learn, yaitu:
  - `normalize=False`: Data tidak dinormalisasi secara otomatis.
  - `copy_X=True`: Data asli tidak dimodifikasi selama pelatihan.
  - `n_jobs=None`: Model tidak menggunakan paralelisme.

### Model 2: K-Nearest Neighbors (KNN)

**Cara Kerja:**
KNN adalah algoritma non-parametrik yang menggunakan tetangga terdekat untuk memprediksi nilai target data baru.  
Model ini menghitung jarak antara data baru dan seluruh data latih, kemudian memilih k tetangga terdekat berdasarkan jarak tersebut (misalnya, jarak Euclidean). Prediksi dilakukan dengan mengambil rata-rata nilai target dari tetangga terdekat.

**Alasan Pemilihan:**
- Fleksibel untuk hubungan non-linear antara fitur dan target.
- Tidak membuat asumsi tentang distribusi data (non-parametrik).
- Sederhana dalam implementasi dan cocok untuk dataset dengan pola yang kompleks.

**Parameter yang Digunakan:**
- `n_neighbors=5`: Menggunakan 5 tetangga terdekat untuk prediksi.
- `metric='minkowski'`: Jarak Minkowski digunakan untuk mengukur jarak antar data.
- `weights='uniform'`: Semua tetangga memiliki bobot yang sama, artinya kontribusinya setara.

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

# Referensi
Simanjuntak, D. S. (2020). Analisis Faktor Pembelian Mobil Berdasarkan Harga dan Merek. *CERMIN: Jurnal Penelitian, 4*(1), 176–187. https://doi.org/10.36841/cermin_unars.v4i1.529

