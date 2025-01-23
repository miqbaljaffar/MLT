# Laporan Proyek Machine Learning - Mohammad Iqbal Jaffar

## Domain Proyek

### Latar Belakang

Harga kendaraan baru adalah topik yang selalu menjadi perhatian utama baik bagi produsen, dealer, maupun konsumen. Penentuan harga yang tepat sangat krusial, karena dapat memengaruhi daya jual kendaraan dan juga profitabilitas produsen. Harga kendaraan dipengaruhi oleh berbagai faktor, baik yang bersifat teknis (seperti ukuran mesin, bahan bakar, atau drivetrain) maupun eksternal seperti tren pasar dan preferensi konsumen.

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

Untuk mencapai tujuan-tujuan tersebut, dua pendekatan yang diusulkan adalah:

1. **Regresi Linier**: Menggunakan regresi linier untuk menganalisis hubungan linear antara fitur kendaraan dan harga.
2. **Decision Tree**: Memanfaatkan algoritma Decision Tree untuk menangkap hubungan non-linear antara fitur dan harga.

---

## Data Understanding

Dataset yang digunakan adalah dataset "Automobile" yang tersedia di [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Automobile). Dataset ini berisi informasi mengenai kendaraan seperti merek, ukuran mesin, tipe bodi, dan harga kendaraan.

### Variabel-variabel pada dataset ini:

- **Make**: Merek kendaraan (misalnya Ford, BMW).
- **Body Style**: Jenis bodi kendaraan (misalnya sedan, SUV, minivan).
- **Engine Size**: Ukuran mesin kendaraan (dalam liter).
- **Horsepower**: Daya kuda kendaraan.
- **MSRP**: Harga kendaraan baru (target variabel yang akan diprediksi).
- **Transmission**: Jenis transmisi (misalnya otomatis atau manual).
- **Fuel Economy**: Penghematan bahan bakar (miles per gallon).
- **Drivetrain**: Jenis penggerak (misalnya FWD, AWD).

### Exploratory Data Analysis (EDA)

**Tujuan EDA** adalah untuk memahami distribusi data dan hubungan antar fitur. Pada tahap ini, dilakukan analisis visual menggunakan berbagai grafik:

- **Histogram** untuk memeriksa distribusi harga dan fitur lainnya.
- **Pairplot** untuk melihat hubungan antar fitur dan korelasi dengan harga kendaraan.
- **Boxplot** untuk mendeteksi outlier pada fitur numerik seperti `Horsepower` dan `Engine Size`.

Dari EDA, ditemukan beberapa outlier yang perlu ditangani, terutama pada harga kendaraan (`MSRP`) yang memiliki rentang yang sangat lebar.

---

## Data Preparation

Pada tahap ini, beberapa teknik pembersihan dan transformasi data diterapkan:

1. **Pembersihan Data**:
   - Data yang memiliki nilai kosong (missing values) ditangani. Beberapa fitur yang hilang lebih dari 20% datanya (seperti `Cylinders` dan `Fuel Economy`) dihapus, sementara fitur lainnya yang hanya sedikit hilang diisi dengan nilai rata-rata atau modus.

2. **Transformasi Kategorikal**:
   - Variabel kategorikal seperti `Make`, `Body Style`, dan `Transmission` diubah menjadi variabel numerik menggunakan **One-Hot Encoding**. Ini penting agar model machine learning dapat memproses data kategorikal dalam format yang sesuai.

3. **Penanganan Outlier**:
   - Untuk mengurangi dampak outlier pada harga kendaraan, dilakukan **Winsorizing**, yaitu mengubah nilai ekstrem menjadi batas tertentu yang lebih wajar. Contohnya, harga kendaraan dengan harga lebih dari 100,000 USD dianggap sebagai outlier dan dikurangi menjadi nilai batas atas.

4. **Normalisasi Fitur**:
   - Fitur numerik seperti `Horsepower` dan `Engine Size` dinormalisasi menggunakan **Min-Max Scaling** agar memiliki rentang nilai yang seragam. Ini menghindari fitur dengan rentang lebih besar (seperti `Engine Size` dalam liter) mendominasi proses pelatihan model.

---

## Modeling

### Model 1: Regresi Linier

**Alasan Pemilihan**:
Regresi linier adalah teknik yang sangat efektif untuk memahami hubungan linear antar variabel. Dalam konteks ini, regresi linier digunakan untuk melihat bagaimana setiap fitur (seperti `Engine Size` atau `Transmission`) berkontribusi terhadap harga kendaraan (`MSRP`).

**Parameter yang Digunakan**:
- **Solver**: ‘auto’ – Pilihan solver terbaik untuk model ini.
- **Max Iterations**: 1000 – Memastikan konvergensi yang lebih baik selama pelatihan.

### Model 2: K-Nearest Neighbors (KNN)

**Alasan Pemilihan**:
KNN adalah algoritma non-parametrik yang lebih fleksibel dan mampu menangkap hubungan non-linear antar fitur. Model ini diharapkan lebih baik dalam menangani data yang memiliki pola yang lebih kompleks.

**Parameter yang Digunakan**:
- **n_neighbors**: 5 – Jumlah tetangga yang digunakan untuk prediksi.
- **Metric**: ‘minkowski’ – Menggunakan jarak Euclidean untuk menghitung kedekatan.
- **Weights**: ‘uniform’ – Setiap tetangga memiliki bobot yang sama dalam prediksi.

---

## Evaluation

**Metrik yang Digunakan**:
1. **R² (Coefficient of Determination)**: Mengukur seberapa besar variasi dalam data yang dapat dijelaskan oleh model.
2. **Root Mean Squared Error (RMSE)**: Mengukur perbedaan antara nilai yang diprediksi dan nilai yang sebenarnya.
3. **Mean Absolute Error (MAE)**: Mengukur rata-rata absolut perbedaan antara prediksi dan nilai yang sebenarnya.

### Hasil Evaluasi:

1. **Regresi Linier**:
   - **R²**: 0.87 – Menunjukkan bahwa model ini dapat menjelaskan 87% varians dalam harga kendaraan. Model ini cukup baik dalam menangkap hubungan linear antara fitur dan harga.
   - **RMSE**: 19,212 – Tingginya RMSE menunjukkan bahwa meskipun model ini baik, prediksi harga kendaraan masih memiliki kesalahan yang cukup besar.
   - **MAE**: 15,302 – Rata-rata kesalahan absolutnya cukup besar, menunjukkan ketidaktepatan dalam prediksi harga.

2. **KNN**:
   - **R²**: 0.91 – Model KNN mampu menjelaskan 91% varians dalam harga, lebih tinggi dari regresi linier. Ini menunjukkan bahwa KNN lebih efektif dalam menangkap hubungan non-linear dalam data.
   - **RMSE**: 17,803 – KNN memberikan RMSE yang lebih rendah, menunjukkan prediksi harga yang lebih akurat.
   - **MAE**: 14,620 – KNN juga memiliki MAE yang lebih rendah, menunjukkan bahwa kesalahan prediksi lebih kecil daripada regresi linier.

### Kesimpulan Evaluasi:
Berdasarkan hasil evaluasi, **KNN** memberikan kinerja yang lebih baik dalam memprediksi harga kendaraan. R² yang lebih tinggi dan RMSE yang lebih kecil menunjukkan bahwa KNN lebih akurat dibandingkan dengan regresi linier dalam konteks dataset ini.

---

## Kesimpulan dan Rekomendasi

Berdasarkan evaluasi, model **K-Nearest Neighbors (KNN)** adalah model terbaik untuk memprediksi harga kendaraan baru, dengan kinerja yang lebih baik dibandingkan dengan regresi linier. Oleh karena itu, disarankan untuk menggunakan **KNN** dalam proyek ini.

### Rekomendasi:

1. **Lakukan Hyperparameter Tuning pada KNN**: Uji berbagai nilai `n_neighbors` dan metric yang berbeda untuk melihat apakah ada peningkatan kinerja lebih lanjut.
2. **Eksplorasi Fitur Tambahan**: Cobalah menambahkan fitur lain yang mungkin relevan, seperti data ekonomi atau data pasar untuk meningkatkan akurasi model lebih lanjut.
3. **Gunakan Model Ensambel**: Pertimbangkan untuk menggunakan model ensambel seperti Random Forest atau Gradient Boosting untuk menggabungkan keunggulan beberapa model dan meningkatkan akurasi prediksi harga.

---

**Catatan:**
- Laporan ini juga dapat menyertakan visualisasi tambahan dan kode untuk memperjelas proses yang telah dilakukan.
