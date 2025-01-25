# Laporan Proyek Machine Learning - Mohammad Iqbal Jaffar

## Domain Proyek

### Latar Belakang

Harga kendaraan baru adalah topik yang selalu menjadi perhatian utama bagi produsen, dealer, dan konsumen. Penentuan harga yang tepat sangat krusial, karena dapat memengaruhi daya jual kendaraan dan profitabilitas produsen. Harga kendaraan dipengaruhi oleh berbagai faktor, baik yang bersifat teknis (seperti ukuran mesin, bahan bakar, atau drivetrain) maupun eksternal seperti tren pasar dan preferensi konsumen.

Melalui machine learning, kita dapat memprediksi harga kendaraan baru dengan menggunakan data historis yang mengandung informasi tentang berbagai fitur kendaraan. Dengan demikian, produsen dan konsumen bisa mendapatkan estimasi harga yang lebih akurat, yang akan membantu produsen dalam menetapkan harga dan konsumen dalam menentukan apakah harga kendaraan tersebut sesuai dengan anggaran mereka.

### Alasan Penyelesaian Masalah

Penetapan harga kendaraan mempengaruhi banyak aspek dalam industri otomotif, mulai dari strategi pemasaran, keputusan produksi, hingga kepuasan konsumen. Memiliki model prediksi yang akurat dapat memberi keunggulan kompetitif pada produsen kendaraan dan dealer, serta memberikan konsumen lebih banyak informasi untuk membuat keputusan yang lebih terinformasi.

### Riset Terkait

Beberapa penelitian terdahulu telah mengidentifikasi bahwa harga kendaraan dipengaruhi oleh berbagai faktor teknis dan non-teknis. Sebagai contoh, sebuah studi oleh Simanjuntak (2020) menganalisis pengaruh harga dan merek terhadap keputusan pembelian mobil, dengan menggunakan regresi linier. Hasil penelitian menunjukkan bahwa harga dan merek memiliki pengaruh yang signifikan terhadap keputusan pembelian, dengan variabel harga berkontribusi sebesar 66,6%. Hasil tersebut menunjukkan bahwa faktor-faktor seperti harga dan merek kendaraan memainkan peran penting dalam menentukan keputusan pembelian.

Referensi terkait dapat ditemukan pada [ANALISIS FAKTOR PEMBELIAN MOBIL BERDASARKAN HARGA DAN MEREK](https://unars.ac.id/ojs/index.php/cermin_unars/article/view/529).

---

# Business Understanding

Proyek ini bertujuan untuk membangun sebuah model prediksi yang dapat memperkirakan harga kendaraan baru (MSRP), yang akan membantu produsen kendaraan dalam menetapkan harga yang optimal. Selain itu, model ini juga akan mempermudah konsumen dalam membandingkan harga kendaraan berdasarkan fitur-fitur yang relevan. Dengan adanya model ini, produsen dapat membuat keputusan yang lebih tepat mengenai harga jual, sementara konsumen dapat memperoleh informasi yang lebih transparan mengenai harga kendaraan yang mereka minati.

### Problem Statements

1. **Apa saja faktor yang mempengaruhi harga kendaraan baru (MSRP)?**
   - Beberapa faktor yang diharapkan dapat mempengaruhi harga kendaraan baru antara lain merek, jenis bodi, ukuran mesin, tenaga kuda (horsepower), torsi, dan fitur-fitur tambahan seperti sistem penggerak (drivetrain), jenis transmisi, dan lain sebagainya. Dalam hal ini, kita ingin mengetahui seberapa besar kontribusi masing-masing faktor terhadap harga kendaraan.

2. **Bagaimana hubungan antara jenis kendaraan dan harga?**
   - Jenis kendaraan, seperti sedan, SUV, minivan, atau truk, memiliki karakteristik yang berbeda yang dapat mempengaruhi harga jual kendaraan tersebut. Misalnya, SUV atau kendaraan mewah cenderung memiliki harga yang lebih tinggi daripada kendaraan kompak. Memahami hubungan ini dapat memberikan wawasan tentang bagaimana produsen dan konsumen memandang nilai suatu kendaraan berdasarkan jenisnya.

3. **Bagaimana model dapat memberikan prediksi yang akurat untuk harga kendaraan baru?**
   - Tujuan utama dari proyek ini adalah membangun model prediksi harga kendaraan berdasarkan data yang tersedia. Model ini harus mampu memprediksi harga kendaraan baru dengan akurat, menggunakan variabel-variabel seperti merek, jenis bodi, tenaga mesin, dan fitur lainnya sebagai input.

4. **Bagaimana performa model yang dihasilkan berdasarkan evaluasi metrik yang digunakan?**
   - Evaluasi model dilakukan menggunakan beberapa metrik, seperti R² (Coefficient of Determination), RMSE (Root Mean Squared Error), dan MAE (Mean Absolute Error), yang akan mengukur seberapa baik model dapat memprediksi harga kendaraan pada data yang belum dilihat sebelumnya. Hasil evaluasi ini akan menunjukkan apakah model sudah cukup akurat untuk digunakan dalam situasi dunia nyata.

5. **Bagaimana distribusi harga kendaraan berpengaruh pada strategi harga?**
   - Memahami distribusi harga kendaraan dapat membantu dalam merumuskan strategi harga yang efektif. Misalnya, mengetahui bahwa sebagian besar kendaraan berada pada rentang harga tertentu dapat membantu produsen dalam menentukan strategi pemasaran atau segmentasi harga yang lebih efisien. Selain itu, distribusi harga juga bisa memberi wawasan tentang segmentasi pasar, apakah pasar lebih banyak berfokus pada kendaraan ekonomis atau kendaraan mewah.

### Goals

1. **Menemukan faktor-faktor utama yang mempengaruhi harga kendaraan baru**: Tujuan pertama adalah mengidentifikasi dan memahami faktor-faktor yang paling signifikan dalam menentukan harga kendaraan. Faktor-faktor ini bisa mencakup merek, ukuran mesin, jenis bodi, dan fitur kendaraan lainnya.
   
2. **Memahami hubungan antara jenis kendaraan dan harga**: Analisis ini bertujuan untuk menjawab pertanyaan tentang bagaimana perbedaan jenis kendaraan (misalnya SUV vs. sedan) mempengaruhi harga jualnya. Hal ini akan membantu dalam memahami bagaimana preferensi pasar mempengaruhi harga kendaraan.

3. **Membangun model yang dapat memprediksi harga kendaraan dengan akurat**: Dengan membangun model prediksi, tujuan utamanya adalah untuk menghasilkan alat yang dapat memberikan estimasi harga yang tepat berdasarkan input dari berbagai fitur kendaraan. Model ini bisa digunakan oleh produsen kendaraan untuk menetapkan harga atau oleh konsumen untuk menilai nilai kendaraan.

4. **Mengevaluasi model menggunakan metrik R², RMSE, dan MAE**: Evaluasi model menggunakan metrik yang relevan adalah bagian penting untuk memastikan model yang dibangun dapat diandalkan. R² digunakan untuk mengukur seberapa baik model menjelaskan variabilitas data, RMSE memberikan gambaran seberapa jauh prediksi model dari nilai aktual, dan MAE mengukur rata-rata kesalahan absolut prediksi.

5. **Menganalisis distribusi harga kendaraan dan dampaknya pada strategi harga**: Analisis ini bertujuan untuk memberikan wawasan lebih dalam tentang bagaimana harga kendaraan tersebar di pasar dan bagaimana distribusi harga ini dapat memengaruhi strategi harga yang digunakan oleh produsen dan pengecer kendaraan. Misalnya, jika sebagian besar kendaraan berada dalam kisaran harga tertentu, produsen dapat fokus pada segmentasi harga tersebut untuk memaksimalkan keuntungan.

---

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

Dataset yang digunakan adalah dataset "Automobile" yang tersedia di [Dataset](https://github.com/Pitsillides91/python_2025/blob/main/6.Python_Reg_ml_model/car_data.csv). Dataset ini berisi informasi mengenai kendaraan seperti merek, ukuran mesin, tipe bodi, dan harga kendaraan. Data ini digunakan untuk memprediksi harga kendaraan baru (MSRP) berdasarkan berbagai fitur kendaraan.

### Variabel-variabel pada dataset ini:

- **Make**: Merek kendaraan (misalnya Ford, BMW).
- **Body Style**: Jenis bodi kendaraan (misalnya sedan, SUV, minivan).
- **Engine Size**: Ukuran mesin kendaraan (dalam liter).
- **Horsepower**: Daya kuda kendaraan.
- **MSRP**: Harga kendaraan baru (target variabel yang akan diprediksi).
- **Transmission**: Jenis transmisi (misalnya otomatis atau manual).
- **Fuel Economy**: Penghematan bahan bakar (miles per gallon).
- **Drivetrain**: Jenis penggerak (misalnya FWD, AWD).

### Load and Preview Dataset

Pada bagian ini, kita akan memuat dataset mobil dari file CSV ke dalam DataFrame menggunakan pustaka pandas.

Setelah memuat dataset, kita dapat melihat lima baris pertama untuk memahami struktur dan isi dataset.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt1.PNG)

Output dari kode ini menunjukkan struktur dataset, dengan kolom-kolom seperti **Make**, **Model**, **Year**, **MSRP**, **Body Style**, dan **Horsepower** untuk setiap mobil.

### Data Summary and Information

Pada bagian ini, kita akan menampilkan informasi dasar mengenai dataset, termasuk jenis kolom, jumlah nilai yang tidak kosong, dan tipe data pada setiap kolom. Informasi ini sangat penting untuk memahami karakteristik dataset dan untuk memutuskan langkah-langkah yang diperlukan untuk pembersihan data.

Dataset ini memiliki **1610 baris** dan **17 kolom**. Beberapa kolom seperti "Invoice Price", "Cylinders", "Horsepower", "Torque", dan "Highway Fuel Economy" memiliki nilai kosong (null). Sementara kolom lainnya memiliki nilai yang lengkap tanpa kekurangan data.

Mayoritas kolom adalah bertipe **object** (biasanya tipe data string), kecuali untuk kolom "index" dan "Year" yang bertipe **int64**.

### Descriptive Statistics

Pada bagian ini, kita akan mendapatkan statistik deskriptif dari kolom numerik dalam dataset. Statistik deskriptif ini memberikan gambaran umum mengenai sebaran data, seperti nilai rata-rata (mean), standar deviasi (std), nilai minimum (min), dan nilai maksimum (max) untuk kolom-kolom numerik.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt15.PNG)

Berikut adalah penjelasan beberapa statistik yang diperoleh:

- **Kolom "index"**:
  - Jumlah data (**count**) adalah **1610**, yang berarti tidak ada nilai yang hilang pada kolom ini.
  - Rata-rata (**mean**) nilai index adalah **2932.10**.
  - Standar deviasi (**std**) adalah **1857.61**, menunjukkan bahwa data dalam kolom ini memiliki variasi yang cukup besar.
  - Nilai minimum (**min**) adalah **0**, sementara nilai maksimum (**max**) adalah **6414**, yang menunjukkan rentang yang cukup luas.

- **Kolom "Year"**:
  - Jumlah data (**count**) adalah **1610**, yang berarti kolom ini juga tidak memiliki nilai yang hilang.
  - Rata-rata (**mean**) tahun adalah **2023.45**, dengan sebagian besar data berada pada tahun 2023 dan 2024.
  - Standar deviasi (**std**) yang kecil (**0.50**) menunjukkan bahwa data tahun relatif tidak bervariasi jauh.
  - Nilai minimum (**min**) dan maksimum (**max**) adalah **2023**, yang menunjukkan bahwa hampir semua data berasal dari tahun 2023 dan 2024.
    
---

### Exploratory Data Analysis (EDA)

**Tujuan EDA** adalah untuk memahami distribusi data dan hubungan antar fitur. Pada tahap ini, dilakukan analisis visual menggunakan berbagai grafik untuk menggali wawasan dari data.

---

#### 1. Analisis Data Eksplorasi (EDA): Cek Nilai Unik pada Setiap Kolom

Pada tahap ini, kita akan melakukan analisis untuk memeriksa nilai unik yang ada pada setiap kolom dalam dataset. Hal ini penting untuk memahami jenis data yang ada di setiap kolom, serta untuk menentukan apakah ada kolom dengan jumlah nilai yang terlalu banyak atau terlalu sedikit. Ini juga berguna untuk memahami variabilitas dan keunikan data dalam setiap kolom.

Jika jumlah nilai unik suatu kolom kurang dari atau sama dengan 12, kita akan menampilkan daftar nilai unik tersebut. Jika jumlah nilai uniknya lebih dari 12, hanya jumlah nilai unik yang akan ditampilkan.

**Langkah-langkah Implementasi:**

1. Melakukan pengecekan nilai unik pada setiap kolom dalam dataset mobil.
2. Jika jumlah nilai unik pada kolom lebih kecil atau sama dengan 12, menampilkan daftar nilai unik untuk kolom tersebut.
3. Jika jumlah nilai unik lebih dari 12, hanya menampilkan jumlah nilai unik pada kolom tersebut.

**Penjelasan Hasil Output:**

- **Kolom index** memiliki **1610** nilai unik, yang menunjukkan bahwa setiap baris dalam dataset memiliki nilai index yang berbeda.
- **Kolom Make** memiliki **7** nilai unik, yang menunjukkan ada 7 merek mobil yang berbeda dalam dataset: `['Aston Martin', 'Audi', 'BMW', 'Bentley', 'Ford', 'Mercedes-Benz', 'Nissan']`.
- **Kolom Model** memiliki **150** nilai unik, yang berarti ada 150 model mobil yang berbeda dalam dataset.
- **Kolom Year** hanya memiliki **2** nilai unik, yaitu 2023 dan 2024, menunjukkan bahwa dataset ini hanya mencakup mobil dari tahun tersebut.
- **Kolom Trim** memiliki **373** nilai unik, yang menunjukkan banyaknya varian trim yang tersedia dalam dataset.
- **Kolom MSRP**, **Invoice Price**, dan **Used/New Price** memiliki banyak nilai unik, masing-masing **1317**, **944**, dan **1317** nilai unik, yang menunjukkan harga mobil yang bervariasi.
- **Kolom Body Size** memiliki **3** nilai unik, yaitu `['Compact', 'Large', 'Midsize']`, yang menggambarkan ukuran tubuh mobil.
- **Kolom Body Style** memiliki **12** nilai unik, yang menggambarkan berbagai jenis tubuh mobil seperti 'SUV', 'Sedan', 'Pickup Truck', dan lainnya.
- **Kolom Cylinders** memiliki **10** nilai unik, yang menggambarkan jumlah dan tipe silinder pada mesin mobil.
- **Kolom Engine Aspiration** memiliki **6** nilai unik, menggambarkan jenis aspirasi mesin seperti 'Turbocharged' dan 'Electric Motor'.
- **Kolom Drivetrain** memiliki **4** nilai unik, menggambarkan jenis sistem penggerak roda pada mobil, seperti '4WD', 'AWD', 'FWD', dan 'RWD'.
- **Kolom Transmission** memiliki **2** nilai unik, yaitu 'automatic' dan 'manual', yang menggambarkan jenis transmisi mobil.
- **Kolom Horsepower** dan **Torque** memiliki **192** dan **176** nilai unik, yang menunjukkan banyaknya variasi dalam daya dan torsi mesin mobil.
- **Kolom Highway Fuel Economy** memiliki **63** nilai unik, yang menggambarkan variasi konsumsi bahan bakar mobil di jalan raya.

---

#### 2. **Histogram**
Histogram digunakan untuk memeriksa distribusi harga dan fitur lainnya.

![Distribusi Harga](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt4.png)
![Distribusi MSRP](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt31.png)

**Distribusi Harga (Used/New Price dan MSRP):**
- **Gambar:** Terdapat dua grafik yang menunjukkan distribusi harga kendaraan:
  - **Harga bekas/baru (Used/New Price)**
  - **MSRP (Manufacturer's Suggested Retail Price)**

**Statistik:**
- **Rata-rata (Mean):** 62,795.98
- **Median:** 55,900.00
- **Modus:** 114,843.75

**Interpretasi:**
Grafik menunjukkan pola distribusi harga kendaraan:
- Puncak grafik menggambarkan harga yang paling sering muncul (modus).
- Rata-rata dan median memberikan informasi tambahan tentang lokasi sebaran data.

---

##### 1. **Distribusi Horsepower**
- **Gambar:** Grafik distribusi tenaga kuda (Horsepower).
  
**Statistik:**
- **Rata-rata (Mean):** 345.37
- **Median:** 318.00
- **Modus:** 275.00

**Interpretasi:**
Grafik ini memperlihatkan jumlah tenaga kuda yang dimiliki kendaraan. Sebagian besar kendaraan memiliki horsepower sekitar nilai modus, sementara nilai rata-rata dan median memberikan informasi tambahan tentang penyebaran data.

---

##### 2. **Distribusi Torque**
- **Gambar:** Grafik distribusi torsi kendaraan (Torque).
  
**Statistik:**
- **Rata-rata (Mean):** 364.63
- **Median:** 339.00
- **Modus:** 260.00

**Interpretasi:**
Grafik menunjukkan pola distribusi nilai torsi kendaraan. Sebagian besar kendaraan memiliki torsi mendekati nilai modus, sedangkan rata-rata dan median memberikan gambaran tentang sebaran data di sekitar nilai tersebut.

---

#### 3. **Pairplot**
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

### 4. Cek Missing Value

Pada tahap ini, kita akan memeriksa apakah terdapat nilai yang anomali dalam dataset, seperti NaN, null, atau nilai hilang lainnya.

![out](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt5.png)

#### Hasil
- Kolom `index`, `Make`, `Model`, `Year`, `Trim`, `MSRP`, `Used/New Price`, `Body Size`, `Body Style`, `Engine Aspiration`, `Drivetrain`, dan `Transmission` tidak memiliki nilai yang hilang, karena jumlah nilai yang hilang pada kolom-kolom ini adalah **0**.
- Kolom `Invoice Price` memiliki **552 nilai yang hilang**.
- Kolom `Cylinders` memiliki **165 nilai yang hilang**.
- Kolom `Horsepower` memiliki **5 nilai yang hilang**.
- Kolom `Torque` memiliki **27 nilai yang hilang**.
- Kolom `Highway Fuel Economy` memiliki **424 nilai yang hilang**.


### 5. Cek Outlier

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

### Penanganan Missing Value

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

### 3. Pembersihan dan Konversi Tipe Data

#### Metode
Pada tahap ini, dilakukan pembersihan dan konversi data pada kolom `MSRP` dan `Used/New Price` yang awalnya berformat string. Kolom-kolom tersebut mengandung simbol mata uang ($) dan tanda koma (,) sebagai pemisah ribuan, yang perlu dihapus agar data dapat dikonversi menjadi tipe numerik. Langkah ini sangat penting untuk memungkinkan analisis statistik dan perhitungan matematika pada data harga kendaraan.

#### Langkah-langkah
Pertama, simbol mata uang `$` dan tanda koma `,` yang ada di kolom `MSRP` dan `Used/New Price` dihapus. Proses ini dilakukan dengan metode penggantian berbasis pola menggunakan ekspresi reguler. Setelah simbol dan tanda koma dihapus, data dalam kedua kolom tersebut dikonversi dari format string menjadi angka desimal (`float`). Langkah ini memastikan bahwa data dapat digunakan untuk berbagai analisis statistik dan matematis. Setelah itu, dilakukan pengecekan kembali pada informasi dataset.

![info](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt6.png)

#### Hasil
Setelah proses pembersihan dan konversi:
- Kolom `MSRP` dan `Used/New Price` berhasil diubah dari format string menjadi format angka desimal (`float64`).
- Tidak ada nilai hilang yang tercatat pada kedua kolom ini setelah konversi.
- Dataset sekarang memiliki total 1583 entri dengan 16 kolom. Semua kolom relevan telah berada dalam format yang sesuai untuk analisis lebih lanjut.

---

### Statistik Deskriptif Kolom Numerik

#### Pengecekan Statistik Deskriptif
Setelah pembersihan dan konversi tipe data, langkah selanjutnya adalah memeriksa statistik deskriptif dari kolom-kolom numerik pada dataset. Statistik deskriptif memberikan gambaran umum tentang distribusi data, seperti nilai minimum, maksimum, rata-rata, dan simpangan baku. Hal ini penting untuk memahami karakteristik dari setiap kolom numerik yang ada dalam dataset.

![desc](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt14.PNG)

#### Penjelasan Hasil Output
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

#### Kesimpulan
Dari statistik deskriptif ini, kita dapat melihat bahwa dataset ini mengandung variasi yang cukup besar, baik dari sisi harga maupun performa kendaraan. Dengan informasi ini, kita dapat mulai mengidentifikasi pola atau tren dalam data, atau mengelompokkan kendaraan berdasarkan kategori harga dan spesifikasi performa untuk analisis lebih lanjut.

---

### 4. Penanganan Outlier dengan Winsorizing

#### Metode
Pada bagian ini, kita menangani nilai-nilai yang termasuk outlier dalam kolom-kolom numerik yang relevan, yaitu `MSRP`, `Used/New Price`, `Horsepower_No`, dan `Torque_No`. Outlier akan diganti dengan batas bawah atau batas atas yang dihitung berdasarkan rentang interkuartil (IQR). Teknik ini dikenal dengan sebutan **Winsorizing**, di mana nilai yang lebih besar dari batas atas diganti dengan batas atas, dan nilai yang lebih kecil dari batas bawah diganti dengan batas bawah.

#### Langkah-langkah
1. Menghitung **Q1** (Kuartil pertama) dan **Q3** (Kuartil ketiga) untuk setiap kolom.
2. Menghitung **IQR** (Rentang Interkuartil), yaitu selisih antara Q3 dan Q1.
3. Menentukan **Lower Bound** (batas bawah) dan **Upper Bound** (batas atas) berdasarkan rumus:
   - Lower Bound = Q1 - 1.5 * IQR
   - Upper Bound = Q3 + 1.5 * IQR
4. Mengganti nilai-nilai yang berada di luar batas ini (outliers) dengan nilai batas yang sesuai menggunakan metode Winsorizing.
5. Setelah itu, memeriksa distribusi data menggunakan boxplot untuk melihat perubahan setelah menangani outliers.
6. Memeriksa statistik deskriptif untuk memastikan bahwa data telah dibersihkan dari outliers ekstrem.

#### Implementasi
- Kolom yang ingin diperiksa adalah: `MSRP`, `Used/New Price`, `Horsepower_No`, dan `Torque_No`.
- Untuk setiap kolom tersebut, perhitungan Q1, Q3, IQR, serta batas bawah dan atas dilakukan untuk mendeteksi dan menangani outlier menggunakan Winsorizing.

![MRS](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt7.png)
![USE](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt8.png)

#### Hasil
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

### 6. Normalisasi Fitur

### Metode
Pada tahap ini, normalisasi fitur numerik dilakukan menggunakan `StandardScaler` untuk memastikan bahwa setiap fitur memiliki **mean = 0** dan **standar deviasi = 1**. Normalisasi ini penting untuk memastikan model dapat mempelajari semua fitur dengan skala yang seragam, menghindari dominasi fitur dengan skala yang lebih besar, seperti harga dan tenaga kuda, dalam proses pelatihan model.

### Langkah-langkah
- Melakukan normalisasi pada fitur numerik seperti `Horsepower_No` dan `Torque_No` menggunakan `StandardScaler`.

### Hasil
Fitur numerik `Horsepower_No` dan `Torque_No` telah berhasil dinormalisasi, yang memungkinkan model untuk mempelajari semua fitur dengan skala yang konsisten. Setelah normalisasi, kedua fitur ini memiliki distribusi yang seragam, memfasilitasi proses pelatihan model yang lebih efektif.

---

### 7. Encoding Variabel Kategorikal

### Metode
Untuk mengonversi variabel kategorikal menjadi format numerik, digunakan metode **one-hot encoding**. Teknik ini mengubah setiap kategori dalam variabel menjadi kolom biner (dummy variables), yang mewakili setiap kategori unik dengan nilai 0 atau 1.

### Langkah-langkah
- Mengonversi variabel kategorikal, seperti `Make`, `Body Style`, dan lainnya, menjadi kolom dummy (one-hot encoding) menggunakan `pd.get_dummies()`.

![OHE](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt9.PNG)

### Hasil
Dataset yang dihasilkan memiliki kolom dummy untuk variabel kategorikal, seperti `Make_Aston Martin`, `Drivetrain_AWD`, dan `Transmission_automatic`. Kolom-kolom ini siap digunakan dalam modeling, memungkinkan algoritma machine learning untuk memproses informasi kategorikal dalam format numerik.

---

### 8. Cek Korelasi Setiap Fitur

### Metode
Matriks korelasi dihitung dan divisualisasikan untuk fitur numerik. Matriks korelasi ini menunjukkan sejauh mana hubungan antara fitur-fitur numerik dalam dataset, yang membantu untuk mengidentifikasi hubungan antar fitur sebelum modeling.

### Langkah-langkah
- Menghitung dan memvisualisasikan matriks korelasi untuk fitur numerik seperti `MSRP`, `Horsepower_No`, dan `Torque_No`.

![corr](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt10.png)

### Hasil
Matriks korelasi menunjukkan hubungan positif yang kuat antara `MSRP`, `Horsepower_No`, dan `Torque_No`. Ini menunjukkan bahwa fitur-fitur ini saling berhubungan dan relevan untuk model. Model machine learning dapat memanfaatkan hubungan ini untuk membuat prediksi yang lebih akurat mengenai harga mobil.

---

### Feature Importance menggunakan Decision Tree

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

### 9. Split Data

Pada bagian ini, dataset dibagi menjadi dua bagian, yaitu data latih (train) dan data uji (test). Pembagian ini bertujuan untuk melatih model dengan sebagian data dan mengevaluasi performa model menggunakan data yang tidak digunakan saat pelatihan. Pembagian yang umum digunakan adalah 80% data untuk pelatihan dan 20% data untuk pengujian.

**Alasan Menggunakan Pembagian 80/20:**
- **Pelatihan yang Optimal:** Dengan memberikan 80% data untuk pelatihan, model memiliki cukup banyak data untuk belajar dan mengoptimalkan parameter-parameter yang ada.
- **Evaluasi yang Adil:** Dengan menyisakan 20% data untuk pengujian, kita dapat mengevaluasi model dengan data yang tidak dilihat sebelumnya, sehingga hasil evaluasi lebih dapat dipercaya dan mencerminkan kemampuan model pada data yang belum dikenalnya.
- **Mencegah Overfitting:** Pembagian ini juga membantu menghindari overfitting, yaitu saat model terlalu menyesuaikan diri dengan data pelatihan dan tidak mampu menggeneralisasi dengan baik ke data baru.

**Langkah-langkah Pembagian Data:**
1. Gunakan fungsi `train_test_split` dari pustaka scikit-learn untuk membagi dataset.
2. Tentukan parameter `train_size=0.8`, yang berarti 80% data digunakan untuk pelatihan.
3. Tentukan `random_state=15` agar pembagian data konsisten dan dapat direplikasi di masa depan.

**Hasil Pembagian:**
- Data latih (`X_train` dan `y_train`): Fitur dan target yang digunakan untuk melatih model.
- Data uji (`X_test` dan `y_test`): Fitur dan target yang digunakan untuk menguji model.

Dengan pembagian ini, model dapat dilatih dengan data yang cukup banyak dan diuji dengan data yang tidak terlihat sebelumnya, memberikan evaluasi yang lebih objektif mengenai kemampuan model.

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

| **Model**               | **R² Train** | **R² Test** | **RMSE Train** | **RMSE Test** | **MAE Train** | **MAE Test** |
|-------------------------|--------------|-------------|----------------|---------------|---------------|--------------|
| **Regresi Linier**      | 0.883937     | 0.873134    | 8485.445020    | 8518.103444   | 6400.032599   | 6381.047981  |
| **K-Nearest Neighbors** | 0.934369     | 0.910862    | 6380.930219    | 7140.058920   | 4432.861769   | 4881.146372  |

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

## Kesimpulan dan Rekomendasi Model

Berdasarkan evaluasi, model **K-Nearest Neighbors (KNN)** adalah model terbaik untuk memprediksi harga kendaraan baru, dengan kinerja yang lebih baik dibandingkan dengan regresi linier. Oleh karena itu, disarankan untuk menggunakan **KNN** dalam proyek ini.

### Rekomendasi:

1. **Lakukan Hyperparameter Tuning pada KNN**: Uji berbagai nilai `n_neighbors` dan metric yang berbeda untuk melihat apakah ada peningkatan kinerja lebih lanjut.
2. **Eksplorasi Fitur Tambahan**: Cobalah menambahkan fitur lain yang mungkin relevan, seperti data ekonomi atau data pasar untuk meningkatkan akurasi model lebih lanjut.
3. **Gunakan Model Ensambel**: Pertimbangkan untuk menggunakan model ensambel seperti Random Forest atau Gradient Boosting untuk menggabungkan keunggulan beberapa model dan meningkatkan akurasi prediksi harga.

---

### Answering the Problem Statement:

1. **Faktor Apa yang Paling Mempengaruhi Harga Kendaraan Baru (MSRP)?**
   Berdasarkan analisis model dan hasil feature importance, faktor yang paling mempengaruhi harga kendaraan baru (MSRP) adalah **Torque_No** dan **Horsepower_No**, dengan kontribusi masing-masing sebesar 22.07% dan 21.42%. Selain itu, merek Ford juga memiliki pengaruh signifikan terhadap harga kendaraan.

2. **Bagaimana Hubungan Antara Jenis Kendaraan dan Harga (MSRP)?**
   - **Merek (Make):** Merek premium seperti Aston Martin, Bentley, Audi, BMW, dan Mercedes-Benz memiliki harga yang lebih tinggi. Sedangkan merek seperti Ford dan Nissan lebih terjangkau untuk pasar massal.
   - **Ukuran Bodi (Body Size):** Kendaraan besar (Large) memiliki harga tertinggi, sementara kendaraan kecil (Compact) lebih ekonomis.
   - **Gaya Bodi (Body Style):** Convertible dan coupe biasanya memiliki harga lebih tinggi, mencerminkan pasar kendaraan mewah dan sporty. Sebaliknya, minivan cenderung lebih murah.
   - **Jenis Penggerak (Drivetrain):** Kendaraan dengan penggerak AWD atau 4WD memiliki harga lebih tinggi, sementara FWD cenderung lebih murah.
   - **Jenis Transmisi (Transmission):** Transmisi otomatis umumnya lebih mahal daripada transmisi manual.

3. **Bagaimana Kinerja Prediksi Model Dibandingkan dengan Data Aktual?**
   Model KNN memberikan hasil yang sangat baik, dengan R² sebesar 0.93 pada data latih dan 0.91 pada data uji. Nilai RMSE dan MAE yang cukup tinggi menunjukkan adanya kesalahan prediksi pada beberapa kasus, namun secara keseluruhan model memberikan prediksi yang cukup akurat.

4. **Bagaimana Tren Residual Memberikan Wawasan Tentang Kelompok yang Kurang Terlayani?**
   - **Residual** menunjukkan distribusi yang acak dan tidak ada bias sistematis pada kelompok tertentu. Model relatif adil untuk sebagian besar data, namun outlier pada residual menunjukkan bahwa ada kasus yang mungkin kurang terlayani oleh model.
   - Penyebaran residual yang konsisten di sekitar garis nol (homoskedastisitas) mengindikasikan model tidak memiliki pola kesalahan yang jelas.

5. **Bagaimana Distribusi Harga Kendaraan Berpengaruh pada Strategi Harga?**
   - **Distribusi Harga:** Modus (114,843.75) menunjukkan harga kendaraan yang paling sering ditemukan. Strategi harga dapat difokuskan untuk segmen ini dengan penawaran yang kompetitif.
   - **Rentang Harga:** Rata-rata harga (mean: 62,795.98) dan median (55,900.00) menunjukkan adanya ketimpangan harga, dengan harga lebih tinggi untuk kendaraan premium dan harga lebih rendah untuk kendaraan massal.
     
### Goals and Problem Statement Review:

- **Faktor yang mempengaruhi harga kendaraan (MSRP)** sudah dijawab dengan mengidentifikasi faktor seperti torque, horsepower, dan merek. Hal ini menunjukkan bahwa faktor teknis kendaraan dan brand menjadi pendorong utama harga kendaraan.
- **Hubungan antara jenis kendaraan dan harga** telah dijelaskan dengan menganalisis hubungan merek, ukuran bodi, dan gaya bodi terhadap harga kendaraan. Jenis kendaraan memiliki pengaruh yang signifikan terhadap harga, dengan kendaraan besar dan merek premium cenderung lebih mahal.
- **Model prediksi yang akurat** telah dicapai dengan model KNN, yang memberikan hasil lebih baik dibandingkan Linear Regression berdasarkan metrik evaluasi. Model ini terbukti mampu memberikan prediksi harga yang cukup akurat, meskipun ada beberapa kasus yang perlu diperhatikan untuk meningkatkan prediksi lebih lanjut.
- **Evaluasi model** dengan menggunakan metrik R², RMSE, dan MAE telah dilakukan, dan model KNN menunjukkan performa yang lebih baik, dengan R² yang tinggi pada data latih dan uji. Metrik ini mengonfirmasi bahwa model mampu memprediksi harga kendaraan dengan cukup baik, meskipun ada kesalahan prediksi pada beberapa kasus.
- **Distribusi harga kendaraan** telah dianalisis untuk memberikan wawasan mengenai bagaimana harga kendaraan tersebar di pasar dan bagaimana ini dapat memengaruhi strategi harga yang digunakan oleh produsen. Hasil analisis distribusi menunjukkan bahwa kendaraan dengan harga tertentu cenderung lebih banyak ditemukan di pasar, yang dapat menjadi dasar untuk merancang strategi harga yang lebih efektif dan efisien.

Dengan demikian, **semua tujuan** dari analisis ini telah tercapai, dan pernyataan masalah telah terjawab dengan baik. Model prediksi harga kendaraan yang dibangun dapat menjadi alat yang berguna untuk membantu produsen dan konsumen dalam menentukan harga yang wajar dan kompetitif.

---

# Referensi
Simanjuntak, D. S. (2020). Analisis Faktor Pembelian Mobil Berdasarkan Harga dan Merek. *CERMIN: Jurnal Penelitian, 4*(1), 176–187. https://doi.org/10.36841/cermin_unars.v4i1.529
