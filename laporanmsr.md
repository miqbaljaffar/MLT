# Laporan Proyek Machine Learning - Nama Anda

## Project Overview

Proyek ini bertujuan untuk membangun sistem rekomendasi produk ponsel berdasarkan kemiripan fitur dan deskripsi produk. Sistem rekomendasi ini dapat membantu pengguna dalam menemukan produk ponsel yang sesuai dengan preferensi mereka, baik berdasarkan spesifikasi teknis maupun deskripsi produk. Proyek ini penting karena dapat meningkatkan pengalaman pengguna dalam berbelanja online, terutama di platform e-commerce seperti Flipkart, dengan memberikan rekomendasi yang relevan dan personal.

Referensi:
- [Recommender Systems: The Textbook](https://scholar.google.com/)
- [Building a Recommendation System with Python](https://scholar.google.com/)

---

## Business Understanding

### Problem Statements

1. **Bagaimana cara merekomendasikan produk ponsel yang paling relevan kepada pengguna berdasarkan preferensi mereka?**
   - Pengguna sering kesulitan menemukan produk ponsel yang sesuai dengan kebutuhan mereka, baik dari segi spesifikasi teknis maupun deskripsi produk.

2. **Bagaimana memastikan bahwa rekomendasi yang diberikan tidak hanya berdasarkan satu fitur (seperti harga), tetapi juga mempertimbangkan fitur lain seperti RAM, storage, dan kamera?**
   - Sistem rekomendasi yang hanya mengandalkan satu fitur (misalnya harga) mungkin tidak memberikan rekomendasi yang akurat dan relevan.

3. **Bagaimana mengatasi masalah data yang tidak lengkap atau tidak konsisten dalam dataset produk ponsel?**
   - Dataset sering kali mengandung missing values atau nilai yang tidak konsisten, yang dapat memengaruhi kualitas rekomendasi.

4. **Bagaimana memastikan bahwa sistem rekomendasi dapat memberikan rekomendasi yang beragam, bukan hanya produk dengan spesifikasi yang sangat mirip?**
   - Rekomendasi yang terlalu homogen mungkin tidak memberikan variasi yang cukup bagi pengguna.

5. **Bagaimana mengukur keefektifan sistem rekomendasi dalam memberikan rekomendasi yang sesuai dengan preferensi pengguna?**
   - Tanpa metrik evaluasi yang jelas, sulit untuk menentukan apakah sistem rekomendasi yang dibangun benar-benar membantu pengguna.

---

### Goals

1. **Membangun sistem rekomendasi yang dapat merekomendasikan produk ponsel berdasarkan kemiripan deskripsi dan spesifikasi teknis.**
   - Sistem ini akan mempertimbangkan berbagai fitur seperti harga, RAM, storage, kamera, dan deskripsi produk.

2. **Menggunakan teknik Cosine Similarity untuk mengukur kemiripan antar produk berdasarkan fitur teks (deskripsi) dan numerik (spesifikasi teknis).**
   - Dengan menggabungkan kedua jenis fitur, sistem rekomendasi dapat memberikan rekomendasi yang lebih komprehensif.

3. **Membersihkan dan mempersiapkan data dengan menghapus missing values dan menangani ketidakconsistenan data.**
   - Langkah ini akan memastikan bahwa data yang digunakan untuk membangun sistem rekomendasi berkualitas tinggi.

4. **Memastikan bahwa sistem rekomendasi dapat memberikan rekomendasi yang beragam dengan mempertimbangkan berbagai kombinasi fitur.**
   - Ini akan membantu pengguna menemukan produk yang mungkin tidak mereka pertimbangkan sebelumnya.

5. **Mengevaluasi sistem rekomendasi dengan metrik precision untuk memastikan rekomendasi yang diberikan relevan dengan preferensi pengguna.**
   - Precision akan digunakan untuk mengukur seberapa banyak rekomendasi yang diberikan benar-benar sesuai dengan produk yang dicari.

---

### Solution Approach

1. **Pendekatan Berbasis Konten (Content-Based Filtering)**:
   - Menggunakan fitur produk seperti deskripsi, harga, RAM, storage, dan kamera untuk merekomendasikan produk yang mirip.
   
2. **Cosine Similarity**:
   - Mengukur kemiripan antar produk berdasarkan fitur numerik dan teks.
   
3. **Data Cleaning dan Preparation**:
   - Menghapus missing values, menangani ketidakconsistenan data, dan melakukan normalisasi fitur.
   
4. **Kombinasi Fitur Teks dan Numerik**:
   - Menggabungkan kemiripan berdasarkan deskripsi produk dan spesifikasi teknis untuk memberikan rekomendasi yang lebih komprehensif dan beragam.
   
5. **Evaluasi dengan Metrik Precision**:
   - Menggunakan precision untuk mengukur keefektifan sistem rekomendasi dalam memberikan rekomendasi yang relevan.

---

## Data Understanding

Dataset yang digunakan dalam proyek ini adalah dataset ponsel dari Flipkart, yang berisi informasi tentang berbagai produk ponsel. Dataset ini terdiri dari 984 entri dan 12 kolom, dengan informasi seperti nama produk, harga, rating, RAM, storage, ukuran layar, kamera, dan deskripsi produk.

Variabel-variabel pada dataset adalah sebagai berikut:
- **Product Name**: Nama produk ponsel.
- **Actual Price**: Harga asli sebelum diskon.
- **Discount Price**: Harga setelah diskon.
- **Stars**: Rating dalam bentuk bintang.
- **Rating**: Jumlah total penilaian dari pengguna.
- **Reviews**: Jumlah ulasan yang diberikan.
- **RAM (GB)**: Kapasitas RAM dalam GB.
- **Storage (GB)**: Kapasitas penyimpanan dalam GB.
- **Display Size (inch)**: Ukuran layar dalam inci.
- **Camera**: Resolusi kamera dalam MP.
- **Description**: Deskripsi singkat tentang produk.
- **Link**: Tautan menuju halaman produk di Flipkart.

Sumber dataset: [Mobiles Dataset](https://www.kaggle.com/datasets)

---

### Exploratory Data Analysis (EDA)

1. **Distribusi Harga**: Sebagian besar ponsel memiliki harga setelah diskon di kisaran ₹20,000.
2. **Distribusi Rating**: Mayoritas produk memiliki rating di atas 4.0, dengan puncak pada rating 4.2.
3. **Distribusi RAM**: RAM 8GB merupakan konfigurasi paling umum, diikuti oleh 4GB dan 12GB.
4. **Korelasi Harga vs Rating**: Tidak terdapat korelasi yang jelas antara harga dan rating.
5. **Distribusi Harga Berdasarkan RAM**: Terdapat korelasi positif antara RAM dan harga, di mana semakin besar RAM, semakin tinggi harga produk.

---

## Data Preparation

1. **Handling Missing Values**: Menghapus baris yang memiliki missing values karena data yang hilang tidak dapat diisi dengan rata-rata atau median.
2. **Cleaning Text Data**: Menghapus simbol mata uang dan karakter non-numerik dari kolom harga dan rating.
3. **Feature Engineering**: Menggabungkan kolom 'Product Name' dan 'Description' menjadi satu kolom 'Product Description' untuk mempermudah analisis teks.
4. **TF-IDF Vectorization**: Mengubah teks deskripsi produk menjadi representasi numerik menggunakan TF-IDF.
5. **Normalisasi Fitur Numerik**: Melakukan normalisasi pada fitur numerik seperti harga, RAM, storage, dan kamera menggunakan MinMaxScaler.
6. **One-Hot Encoding**: Mengkodekan brand ponsel menjadi variabel biner menggunakan One-Hot Encoding.

---

## Modeling

1. **Cosine Similarity Berdasarkan Teks**: Menghitung kemiripan antar produk berdasarkan deskripsi produk menggunakan TF-IDF dan Cosine Similarity.
2. **Cosine Similarity Berdasarkan Fitur Numerik**: Menghitung kemiripan antar produk berdasarkan spesifikasi teknis seperti harga, RAM, storage, dan kamera.
3. **Kombinasi Similarity**: Menggabungkan kemiripan teks dan numerik dengan bobot 50%-50% untuk mendapatkan matriks kemiripan akhir.

---

## Evaluation

Metrik evaluasi yang digunakan adalah **precision**, yang mengukur seberapa banyak rekomendasi yang diberikan relevan dengan produk yang dicari. Precision dihitung dengan formula:

\[
\text{Precision} = \frac{\text{Jumlah rekomendasi yang relevan}}{\text{Jumlah rekomendasi yang diberikan}}
\]

Contoh evaluasi:
- Produk yang dicari: POCO C61
- Rekomendasi yang diberikan: 5 produk
- Rekomendasi yang relevan: 4 produk

\[
\text{Precision} = \frac{4}{5} = 0.8 = 80\%
\]

Dengan demikian, sistem rekomendasi ini memiliki precision sebesar 80%, yang menunjukkan bahwa 80% dari rekomendasi yang diberikan benar-benar relevan dengan produk yang dicari.

---

## Kesimpulan

Sistem rekomendasi yang dibangun dalam proyek ini berhasil memberikan rekomendasi produk ponsel yang relevan berdasarkan kemiripan deskripsi dan spesifikasi teknis. Dengan menggunakan kombinasi fitur teks dan numerik, serta metrik evaluasi precision, sistem ini dapat membantu pengguna dalam menemukan produk yang sesuai dengan preferensi mereka.

--- 

Dengan struktur ini, laporan Anda menjadi lebih lengkap, terstruktur, dan mudah dipahami. Semoga membantu! 😊
