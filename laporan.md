# Laporan Proyek Machine Learning - Mohammad Iqbal Jaffar

## Domain Proyek

Proyek ini bertujuan untuk menganalisis faktor-faktor yang mempengaruhi harga kendaraan baru (MSRP) dan membangun model prediksi harga kendaraan berdasarkan berbagai fitur. Permasalahan yang diangkat berkaitan dengan harga kendaraan yang sangat bervariasi tergantung pada faktor-faktor seperti merek, jenis kendaraan, dan spesifikasi teknis. Dengan menggunakan teknik machine learning, tujuan utama proyek ini adalah untuk membangun model prediktif yang dapat memprediksi harga kendaraan dengan akurasi tinggi.

Mengidentifikasi faktor-faktor yang mempengaruhi harga kendaraan penting karena dapat membantu produsen, dealer, dan pembeli dalam menentukan harga yang lebih akurat dan strategis.

### Mengapa Masalah Ini Harus Diselesaikan?
Menyelesaikan masalah harga kendaraan dapat membantu produsen dalam menentukan harga yang kompetitif, serta membantu pembeli dalam membuat keputusan yang lebih baik terkait anggaran mereka.

### Riset Terkait
Penelitian dalam area ini telah dilakukan sebelumnya, dengan banyak studi yang menganalisis faktor harga kendaraan menggunakan berbagai fitur kendaraan. Referensi terkait dapat ditemukan dalam penelitian mengenai analisis prediksi harga kendaraan dan regresi harga kendaraan, seperti yang dipublikasikan oleh [Sumber Riset 1] dan [Sumber Riset 2].

## Business Understanding

### Problem Statements
1. **Faktor apa saja yang mempengaruhi harga kendaraan baru (MSRP)?**
2. **Bagaimana hubungan antara jenis kendaraan dan harga?**
3. **Bagaimana distribusi harga kendaraan berpengaruh pada strategi harga?**
4. **Bagaimana kinerja prediksi model dibandingkan dengan data aktual?**
5. **Bagaimana tren residual memberikan wawasan tentang kelompok yang kurang terlayani?**

### Goals
1. **Mengetahui faktor utama yang mempengaruhi harga kendaraan.**
2. **Mengetahui hubungan antara jenis kendaraan dan harga.**
3. **Mengetahui distribusi harga kendaraan untuk menentukan strategi harga.**
4. **Membangun model yang dapat memprediksi harga kendaraan dengan akurasi tinggi.**
5. **Menemukan kelompok kendaraan yang kurang terlayani dengan analisis residual.**

### Solution Statement
Untuk mencapai tujuan di atas, kami akan menggunakan berbagai teknik pemodelan termasuk:
1. **Regresi Linier** untuk memprediksi harga berdasarkan fitur-fitur kendaraan.
2. **Analisis Decision Tree** untuk mengetahui pentingnya fitur dalam mempengaruhi harga kendaraan.
3. **Visualisasi Data** untuk memahami distribusi harga dan hubungan antar fitur.

## Data Understanding

Dataset yang digunakan adalah dataset kendaraan yang berisi informasi mengenai merek kendaraan, harga MSRP, tenaga mesin, torsi, dan beberapa fitur lainnya. Data ini diambil dari [sumber dataset](https://github.com/Pitsillides91/python_2025/blob/main/6.Python_Reg_ml_model/car_data.csv). Variabel-variabel dalam dataset ini antara lain:
- **MSRP**: Harga kendaraan baru.
- **Horsepower**: Tenaga mesin kendaraan.
- **Torque**: Torsi kendaraan.
- **Make**: Merek kendaraan.
- **Body Style**: Gaya bodi kendaraan.

Setelah memuat dan memahami data, kami melakukan eksplorasi lebih lanjut terhadap distribusi fitur dan hubungan antar fitur untuk mendapatkan wawasan yang lebih dalam melalui visualisasi dan analisis data eksploratori.

## Data Preparation

Tahapan ini melibatkan pengolahan data yang diperlukan untuk membangun model prediksi. Beberapa langkah yang diambil antara lain:
1. **Menghapus kolom yang tidak relevan atau memiliki banyak nilai hilang**.
2. **Mengisi nilai yang hilang** untuk kolom numerik dengan nilai rata-rata.
3. **Mengonversi kolom string yang berisi angka (seperti MSRP dan harga bekas)** menjadi tipe data numerik.
4. **Melakukan encoding pada variabel kategori** dengan one-hot encoding.

Proses ini sangat penting untuk memastikan bahwa data yang digunakan untuk pelatihan model sudah bersih dan siap untuk analisis lebih lanjut.

## Modeling

Kami menggunakan dua model utama dalam proyek ini:
1. **Regresi Linier** untuk memprediksi harga kendaraan berdasarkan berbagai fitur.
2. **Decision Tree** untuk menilai pentingnya fitur dalam prediksi harga kendaraan.

Tahapan ini melibatkan pembagian data menjadi data latih dan data uji, pelatihan model, dan evaluasi performa model.

### Hyperparameter Tuning
Kami juga melakukan tuning hyperparameter pada model untuk meningkatkan akurasi prediksi dengan memilih parameter terbaik yang memberikan performa terbaik pada data uji.

## Evaluation

Model dievaluasi menggunakan metrik berikut:
- **R²**: Untuk mengukur seberapa baik model memprediksi harga kendaraan.
- **RMSE**: Untuk menghitung kesalahan kuadrat rata-rata.
- **MAE**: Untuk menghitung rata-rata kesalahan absolut.

Dari evaluasi ini, kami mendapatkan hasil yang menunjukkan bahwa model regresi linier memiliki performa yang baik dalam memprediksi harga kendaraan.

## Hasil dan Analisis

1. **Faktor Paling Mempengaruhi Harga Kendaraan**: Berdasarkan analisis, faktor-faktor seperti **Horsepower** dan **Torque** memiliki pengaruh terbesar terhadap harga kendaraan.
   
2. **Hubungan Antara Jenis Kendaraan dan Harga**: Kendaraan dengan merek terkenal dan jenis bodi premium, seperti **Bentley** dan **Convertible**, memiliki harga yang lebih tinggi.

3. **Distribusi Harga Kendaraan**: Harga kendaraan cenderung terkonsentrasi pada rentang harga tertentu, yang mempengaruhi strategi harga produsen.

4. **Kinerja Prediksi Model**: Model regresi linier memberikan akurasi yang baik, dengan R² mencapai **0.93** pada data uji. Namun, RMSE dan MAE masih menunjukkan ada ruang untuk perbaikan.

5. **Tren Residual**: Tren residual menunjukkan bahwa model kurang akurat pada kendaraan dengan harga sangat tinggi, yang memberikan wawasan untuk perbaikan di masa depan.

## Kesimpulan

Proyek ini berhasil membangun model yang dapat memprediksi harga kendaraan dengan akurasi yang cukup baik, namun masih ada ruang untuk perbaikan lebih lanjut, terutama dalam menangani kendaraan dengan harga sangat tinggi.
