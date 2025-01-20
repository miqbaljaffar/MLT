# Laporan Proyek Machine Learning - Mohammad Iqbal Jaffar

## Domain Proyek

Proyek ini bertujuan untuk menganalisis faktor-faktor yang mempengaruhi harga kendaraan baru (MSRP) dan membangun model prediksi harga kendaraan berdasarkan berbagai fitur. Permasalahan yang diangkat berkaitan dengan harga kendaraan yang sangat bervariasi tergantung pada faktor-faktor seperti merek, jenis kendaraan, dan spesifikasi teknis. Dengan menggunakan teknik machine learning, tujuan utama proyek ini adalah untuk membangun model prediktif yang dapat memprediksi harga kendaraan dengan akurasi tinggi.

### Mengapa Masalah Ini Harus Diselesaikan?

Masalah harga kendaraan harus diselesaikan untuk memberikan dasar yang kuat dalam penetapan harga oleh produsen serta memberikan pembeli panduan yang lebih cerdas dalam menentukan anggaran mereka. Di era yang semakin kompetitif ini, kemampuan untuk memahami faktor harga kendaraan dapat membantu dalam merancang strategi harga yang lebih efisien dan tepat sasaran.

### Riset Terkait

Penelitian dalam area ini telah dilakukan sebelumnya, dengan banyak studi yang menganalisis faktor harga kendaraan menggunakan berbagai fitur kendaraan. Beberapa studi yang relevan melibatkan penggunaan model regresi dan pohon keputusan untuk memprediksi harga kendaraan. Penelitian mengenai analisis harga kendaraan dapat ditemukan dalam artikel seperti yang dipublikasikan oleh [Sumber Riset](https://unars.ac.id/ojs/index.php/cermin_unars/article/view/529), yang memberikan dasar teori serta pendekatan metodologi yang dapat digunakan untuk memecahkan masalah ini.

---

## Business Understanding

### Problem Statements

1. **Faktor apa saja yang mempengaruhi harga kendaraan baru (MSRP)?**
   - Pemahaman tentang fitur-fitur teknis dan faktor-faktor eksternal yang memengaruhi harga kendaraan.
   
2. **Bagaimana hubungan antara jenis kendaraan dan harga?**
   - Menyaring perbedaan harga yang dipengaruhi oleh jenis kendaraan seperti SUV, sedan, atau convertible.

3. **Bagaimana distribusi harga kendaraan berpengaruh pada strategi harga?**
   - Memahami rentang harga kendaraan di pasar dan bagaimana hal ini mempengaruhi penentuan harga oleh produsen.

4. **Bagaimana kinerja prediksi model dibandingkan dengan data aktual?**
   - Menganalisis seberapa akurat model dapat memprediksi harga kendaraan dibandingkan dengan data aktual.

5. **Bagaimana tren residual memberikan wawasan tentang kelompok yang kurang terlayani?**
   - Mencari pola-pola yang menunjukkan bahwa model mungkin tidak dapat menangani beberapa kelompok kendaraan dengan baik, terutama harga tinggi.

### Goals

1. **Mengetahui faktor utama yang mempengaruhi harga kendaraan.**
2. **Mengetahui hubungan antara jenis kendaraan dan harga.**
3. **Mengetahui distribusi harga kendaraan untuk menentukan strategi harga yang tepat.**
4. **Membangun model prediksi harga kendaraan yang dapat diandalkan dan akurat.**
5. **Mengidentifikasi kelompok kendaraan yang kurang terlayani melalui analisis residual.**

### Solution Statement

Untuk mencapai tujuan di atas, proyek ini menggunakan berbagai teknik pemodelan dan analisis data:
1. **Regresi Linier** untuk memprediksi harga berdasarkan fitur-fitur kendaraan.
2. **Decision Tree** untuk mengevaluasi pentingnya setiap fitur dalam mempengaruhi harga kendaraan.
3. **Visualisasi Data** untuk membantu pemahaman distribusi harga dan hubungan antar fitur dengan lebih jelas.

---

## Data Understanding

Dataset yang digunakan adalah dataset kendaraan yang berisi informasi mengenai merek kendaraan, harga MSRP, tenaga mesin, torsi, dan beberapa fitur lainnya. Data ini diambil dari [sumber dataset](https://github.com/Pitsillides91/python_2025/blob/main/6.Python_Reg_ml_model/car_data.csv). Variabel-variabel dalam dataset ini antara lain:
- **MSRP**: Harga kendaraan baru, yang akan diprediksi.
- **Horsepower**: Tenaga mesin kendaraan yang mempengaruhi performa kendaraan dan harga.
- **Torque**: Torsi kendaraan yang menunjukkan performa mesin, berpengaruh pada harga.
- **Make**: Merek kendaraan, yang sering menjadi indikator harga.
- **Body Style**: Jenis bodi kendaraan, seperti sedan, SUV, convertible, dll.

Setelah memuat dan memahami data, kami melakukan eksplorasi lebih lanjut terhadap distribusi fitur dan hubungan antar fitur untuk mendapatkan wawasan yang lebih dalam melalui visualisasi dan analisis data eksploratori. Kami juga melakukan analisis untuk melihat apakah ada fitur yang tidak memberikan informasi berguna atau mengandung banyak nilai hilang.

### Lampiran:
- **Sample Dataset**: ![Sample Dataset](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt1.PNG)

---

## Data Preparation

Proses ini melibatkan pengolahan data untuk mempersiapkannya agar dapat digunakan dalam pemodelan:

1. **Menghapus kolom yang tidak relevan atau memiliki banyak nilai hilang**  
   Kolom yang tidak memberikan kontribusi terhadap model atau memiliki terlalu banyak nilai hilang dihapus untuk meningkatkan kualitas dataset. Sebagai contoh, kolom Invoice Price, Cylinders, dan Highway Fuel Economy dihapus karena memiliki terlalu banyak nilai hilang atau dianggap kurang relevan untuk analisis harga kendaraan.

2. **Mengisi nilai yang hilang**  
   Nilai yang hilang pada kolom numerik, seperti Horsepower dan Torque, diisi dengan rata-rata dari nilai kolom tersebut. Sebelum pengisian, data pada kolom Horsepower dan Torque mengandung string, sehingga pertama-tama bagian angka diekstraksi dan dikonversi menjadi tipe numerik. Setelah itu, nilai hilang diisi dengan rata-rata untuk memastikan kelengkapan data.

3. **Mengonversi kolom string yang berisi angka**  
   Kolom seperti MSRP yang berisi nilai dalam bentuk string dengan simbol mata uang dan tanda koma, diformat ulang dengan menghapus simbol tersebut dan mengonversinya menjadi tipe data numerik agar bisa digunakan dalam pemodelan.

4. **Melakukan encoding pada variabel kategori**  
   Fitur kategori seperti 'Make' dan 'Body Style' yang berupa string perlu diubah menjadi format numerik agar bisa digunakan dalam model machine learning. Teknik **one-hot encoding** digunakan untuk mengubah variabel kategori menjadi representasi numerik yang bisa diproses oleh algoritma machine learning.

Proses ini penting untuk memastikan bahwa data yang digunakan dalam pelatihan model sudah bersih, konsisten, dan siap untuk dianalisis lebih lanjut. Dengan mempersiapkan data dengan cara ini, model machine learning yang dibangun nantinya dapat bekerja dengan optimal.

### Lampiran:
- **Tabel Missing Value**: ![Missing Value Table](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt2.PNG)

---

## Modeling

Model yang digunakan dalam proyek ini terdiri dari dua pendekatan utama:
1. **Regresi Linier** untuk memprediksi harga kendaraan berdasarkan berbagai fitur teknis dan kategori.
2. **Decision Tree** untuk mengevaluasi pentingnya berbagai fitur dalam memprediksi harga kendaraan dan memahami interaksi yang lebih kompleks antar fitur.

Proses modeling meliputi pembagian data menjadi data latih dan data uji, pelatihan model, dan evaluasi performa model untuk mengidentifikasi model terbaik.

### Hyperparameter Tuning

Kami juga melakukan tuning hyperparameter pada model untuk meningkatkan akurasi prediksi. Dengan melakukan pencarian grid dan menggunakan teknik validasi silang, kami memilih parameter yang memberikan hasil terbaik pada data uji.

---

## Evaluation

Model dievaluasi menggunakan beberapa metrik:
- **R² (R-squared)**: Mengukur proporsi variabilitas harga kendaraan yang dapat dijelaskan oleh model.
- **RMSE (Root Mean Squared Error)**: Mengukur rata-rata kesalahan kuadrat, memberikan gambaran kesalahan prediksi model.
- **MAE (Mean Absolute Error)**: Mengukur rata-rata kesalahan absolut, memberikan gambaran yang lebih jelas tentang akurasi prediksi.

Dari evaluasi ini, kami mendapatkan hasil yang menunjukkan bahwa model regresi linier memiliki performa yang baik dengan R² mencapai **0.93** pada data uji. Meskipun demikian, RMSE dan MAE menunjukkan bahwa masih ada ruang untuk perbaikan.

### Lampiran:
- **Pairplot to Visualize Relationships**: ![Pairplot](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt3.png)
- **Correlation Matrix**: ![Correlation Matrix](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt4.png)

---

## Hasil dan Analisis

1. **Faktor Paling Mempengaruhi Harga Kendaraan**: Analisis menunjukkan bahwa **Horsepower** dan **Torque** adalah faktor utama yang mempengaruhi harga kendaraan. Kendaraan dengan tenaga mesin dan torsi yang lebih tinggi memiliki harga yang lebih tinggi.
   
2. **Hubungan Antara Jenis Kendaraan dan Harga**: Kendaraan dengan merek premium seperti **Bentley** atau jenis bodi mewah seperti **Convertible** memiliki harga yang lebih tinggi dibandingkan dengan kendaraan jenis lain.

3. **Distribusi Harga Kendaraan**: Harga kendaraan menunjukkan konsentrasi di rentang harga menengah hingga tinggi, yang memberikan gambaran bagi produsen untuk menyesuaikan strategi harga mereka.

4. **Kinerja Prediksi Model**: Model regresi linier memberikan hasil yang baik dengan R² **0.93**. Evaluasi model menunjukkan hasil yang memadai dengan tingkat akurasi **0.89** pada data latih dan **0.93** pada data uji. Beberapa metrik evaluasi lainnya adalah:
   - **R² pada data latih**: 0.89
   - **R² pada data uji**: 0.93
   - **RMSE pada data latih**: 17706.2
   - **RMSE pada data uji**: 15634.0
   - **MAE pada data latih**: 10816.5
   - **MAE pada data uji**: 10354.2

   Meskipun model menunjukkan kinerja yang baik secara keseluruhan, prediksi masih kurang akurat untuk kendaraan dengan harga sangat tinggi, yang menunjukkan ada potensi perbaikan lebih lanjut.

5. **Tren Residual**: Tren residual menunjukkan bahwa model kurang akurat pada kendaraan dengan harga sangat tinggi, yang memberikan wawasan tentang kelompok kendaraan yang kurang terlayani oleh model.

### Lampiran:
- **Train Data: Predicted vs Actual**: ![Predicted vs Actual](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt5.png)
- **Residuals for Train Data**: ![Residuals](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt6.png)

---

## Conclusion

Proyek ini berhasil mengidentifikasi faktor utama yang mempengaruhi harga kendaraan dan membangun model prediksi harga kendaraan dengan akurasi yang cukup baik. Walaupun model memiliki akurasi tinggi untuk sebagian besar harga kendaraan, terdapat ruang untuk meningkatkan prediksi terutama pada kendaraan dengan harga tinggi. Ke depannya, pengembangan model dengan fitur lebih banyak dan teknik lain seperti regresi berbasis pohon keputusan atau XGBoost dapat meningkatkan performa lebih jauh.

---
