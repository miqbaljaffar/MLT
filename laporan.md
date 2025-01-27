# Laporan Proyek Machine Learning - Mohammad Iqbal Jaffar

## Domain Proyek

### Latar Belakang

Harga kendaraan baru merupakan topik yang selalu menjadi perhatian utama bagi produsen, dealer, dan konsumen. Penentuan harga yang tepat sangat krusial, karena dapat memengaruhi daya jual kendaraan dan profitabilitas produsen. Harga kendaraan dipengaruhi oleh berbagai faktor, baik yang bersifat teknis (seperti ukuran mesin, bahan bakar, atau drivetrain) maupun eksternal seperti tren pasar dan preferensi konsumen.

Melalui machine learning, harga kendaraan baru dapat diprediksi dengan menggunakan data historis yang mengandung informasi tentang berbagai fitur kendaraan. Dengan demikian, produsen dan konsumen dapat memperoleh estimasi harga yang lebih akurat, yang akan membantu produsen dalam menetapkan harga dan konsumen dalam menentukan apakah harga kendaraan tersebut sesuai dengan anggaran yang tersedia.

### Alasan Penyelesaian Masalah

Penetapan harga kendaraan mempengaruhi banyak aspek dalam industri otomotif, mulai dari strategi pemasaran, keputusan produksi, hingga kepuasan konsumen. Memiliki model prediksi yang akurat dapat memberi keunggulan kompetitif pada produsen kendaraan dan dealer, serta memberikan konsumen lebih banyak informasi untuk membuat keputusan yang lebih terinformasi.

### Riset Terkait

Beberapa penelitian terdahulu telah mengidentifikasi bahwa harga kendaraan dipengaruhi oleh berbagai faktor teknis dan non-teknis. Sebagai contoh, sebuah studi oleh Simanjuntak (2020) menganalisis pengaruh harga dan merek terhadap keputusan pembelian mobil, dengan menggunakan regresi linier. Hasil penelitian menunjukkan bahwa harga dan merek memiliki pengaruh yang signifikan terhadap keputusan pembelian, dengan variabel harga berkontribusi sebesar 66,6%. Hasil tersebut menunjukkan bahwa faktor-faktor seperti harga dan merek kendaraan memainkan peran penting dalam menentukan keputusan pembelian.

Referensi terkait dapat ditemukan pada [ANALISIS FAKTOR PEMBELIAN MOBIL BERDASARKAN HARGA DAN MEREK](https://unars.ac.id/ojs/index.php/cermin_unars/article/view/529).

---

# Business Understanding

Proyek ini bertujuan untuk membangun sebuah model prediksi yang dapat memperkirakan harga kendaraan baru (MSRP), yang akan membantu produsen kendaraan dalam menetapkan harga yang optimal. Selain itu, model ini juga akan mempermudah konsumen dalam membandingkan harga kendaraan berdasarkan fitur-fitur yang relevan. Dengan adanya model ini, produsen dapat membuat keputusan yang lebih tepat mengenai harga jual, sementara konsumen dapat memperoleh informasi yang lebih transparan mengenai harga kendaraan yang diminati.

### Problem Statements

1. **Apa saja faktor yang mempengaruhi harga kendaraan baru (MSRP)?**
   - Beberapa faktor yang diharapkan dapat mempengaruhi harga kendaraan baru antara lain merek, jenis bodi, ukuran mesin, tenaga kuda (horsepower), torsi, dan fitur-fitur tambahan seperti sistem penggerak (drivetrain), jenis transmisi, dan lain sebagainya. Dalam hal ini, tujuan utama adalah untuk mengetahui seberapa besar kontribusi masing-masing faktor terhadap harga kendaraan.

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

### Variabel dalam Dataset Kendaraan

Berikut adalah penjelasan untuk setiap variabel dalam dataset kendaraan yang meliputi berbagai fitur kendaraan yang digunakan untuk analisis harga dan kinerja.

#### 1. Index
- **Deskripsi**: Ini adalah nomor urut yang digunakan untuk mengidentifikasi setiap baris data dalam dataset. Meskipun **Index** tidak memberikan informasi langsung tentang kendaraan, ia berfungsi sebagai identifikasi unik bagi setiap entri.
- **Contoh**: 0, 1, 2, 3, 4 (dan seterusnya).

#### 2. Make
- **Deskripsi**: Merujuk pada **merek** atau **brand** kendaraan, yang menunjukkan produsen atau pembuat kendaraan tersebut. Variabel ini penting untuk mengidentifikasi asal-usul kendaraan dan terkait dengan reputasi, kualitas, dan harga kendaraan.
- **Contoh**: Aston Martin, Audi, BMW, Toyota.

#### 3. Model
- **Deskripsi**: Merupakan **model** spesifik dari kendaraan yang diproduksi oleh produsen tersebut. Model biasanya merujuk pada varian yang memiliki desain dan fitur tertentu.
- **Contoh**: DBX707, A3, X5.

#### 4. Year
- **Deskripsi**: Merupakan tahun pembuatan kendaraan. Tahun kendaraan sangat penting karena mempengaruhi **harga**, **fitur**, dan **kinerja** kendaraan, dengan kendaraan yang lebih baru biasanya memiliki harga lebih tinggi dan fitur teknologi terbaru.
- **Contoh**: 2024, 2023, 2022.

#### 5. Trim
- **Deskripsi**: Trim mengacu pada **varian** atau **tingkatan** dari model kendaraan, yang sering kali mencakup berbagai fitur tambahan, seperti sistem hiburan, pilihan bahan interior, dan paket teknologi.
- **Contoh**: Base, Premium, Premium Plus.

#### 6. MSRP (Manufacturer’s Suggested Retail Price)
- **Deskripsi**: **Harga yang disarankan oleh pabrikan** untuk kendaraan baru. Ini adalah harga yang disarankan untuk kendaraan sebelum diskon atau tawar-menawar. Harga ini mencerminkan **harga pasar standar** untuk kendaraan baru.
- **Contoh**: $242,000, $35,800, $41,400.

#### 7. Invoice Price
- **Deskripsi**: Merupakan harga **pembelian grosir** atau harga yang dibayar oleh dealer kepada produsen untuk kendaraan tersebut. Ini sering kali lebih rendah daripada MSRP dan memberi gambaran tentang biaya dasar untuk dealer.
- **Contoh**: $33,653, $35,533.

#### 8. Used/New Price
- **Deskripsi**: Merupakan harga kendaraan **bekas** atau **baru** yang tertera pada pasar. Ini bisa berbeda tergantung pada status kendaraan (baru atau bekas) dan kondisi pasar saat itu.
- **Contoh**: $242,000 (baru), $35,800 (baru).

#### 9. Body Size
- **Deskripsi**: **Ukuran bodi** kendaraan, yang menentukan seberapa besar atau kecil kendaraan tersebut. Ini bisa mempengaruhi kenyamanan, ruang penumpang, dan efisiensi bahan bakar.
- **Contoh**: Large, Compact, Mid-Size.

#### 10. Body Style
- **Deskripsi**: Menunjukkan **jenis bodi** kendaraan, seperti sedan, SUV, hatchback, atau coupe. Gaya bodi mempengaruhi bentuk kendaraan, penggunaan ruang, dan tujuan kendaraan (misalnya, SUV lebih cocok untuk perjalanan jauh atau keluarga besar).
- **Contoh**: SUV, Sedan, Coupe.

#### 11. Cylinders
- **Deskripsi**: Menunjukkan jumlah **silinder** dalam mesin kendaraan. Ini berpengaruh pada **daya mesin** dan **efisiensi bahan bakar**. Semakin banyak silinder, semakin kuat biasanya mesin tersebut, tetapi itu juga bisa berarti konsumsi bahan bakar yang lebih tinggi.
- **Contoh**: V8, I4 (4-silinder), I6 (6-silinder).

#### 12. Engine Aspiration
- **Deskripsi**: Menunjukkan jenis sistem **pengisian udara mesin**. Ada dua jenis utama: **Naturally Aspirated** (tanpa turbocharger atau supercharger) dan **Turbocharged** (menggunakan turbocharger untuk meningkatkan daya).
- **Contoh**: Turbocharged, Naturally Aspirated, Supercharged.

#### 13. Drivetrain
- **Deskripsi**: Menunjukkan sistem **penggerak** kendaraan, yaitu bagaimana tenaga dari mesin disalurkan ke roda. Pilihan drivetrain dapat mempengaruhi traksi, pengendalian, dan efisiensi bahan bakar.
- **Contoh**: AWD (All-Wheel Drive), FWD (Front-Wheel Drive), RWD (Rear-Wheel Drive).

#### 14. Transmission
- **Deskripsi**: Jenis **transmisi** kendaraan yang mengontrol perpindahan gigi. Transmisi otomatis memudahkan pengemudi dalam mengemudi, sementara transmisi manual memberikan kontrol lebih.
- **Contoh**: Automatic, Manual.

#### 15. Horsepower
- **Deskripsi**: Mengukur **daya kuda** mesin kendaraan, yang mempengaruhi seberapa cepat kendaraan dapat bergerak. Semakin tinggi horsepower, semakin kuat kendaraan dalam akselerasi.
- **Contoh**: 697 hp @ 6000 rpm, 201 hp @ 4800 rpm.

#### 16. Torque
- **Deskripsi**: Menunjukkan **torsi** mesin yang mengukur kemampuan kendaraan dalam menghasilkan daya putar. Ini sangat penting untuk akselerasi kendaraan terutama pada kecepatan rendah dan untuk kendaraan yang membawa beban.
- **Contoh**: 663 ft-lbs. @ 2750 rpm, 221 ft-lbs. @ 4100 rpm.

#### 17. Highway Fuel Economy
- **Deskripsi**: Mengukur **penghematan bahan bakar** kendaraan saat berkendara di jalan raya (dalam miles per gallon atau mpg). Ini menunjukkan efisiensi kendaraan dalam kondisi jalan yang lebih stabil (kecepatan konstan).
- **Contoh**: 20 mpg, 37 mpg, 34 mpg.

### Load and Preview Dataset

Pada bagian ini, dataset mobil dimuat dari file CSV ke dalam DataFrame menggunakan pustaka pandas.

Setelah dataset dimuat, lima baris pertama dapat dilihat untuk memahami struktur dan isi dataset.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt1.PNG)

Output dari kode ini menunjukkan struktur dataset, dengan kolom-kolom seperti **Make**, **Model**, **Year**, **MSRP**, **Body Style**, dan **Horsepower** untuk setiap mobil.

### Data Summary and Information

Pada bagian ini, informasi dasar mengenai dataset akan ditampilkan, termasuk jenis kolom, jumlah nilai yang tidak kosong, dan tipe data pada setiap kolom. Informasi ini sangat penting untuk memahami karakteristik dataset dan untuk memutuskan langkah-langkah yang diperlukan untuk pembersihan data.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt33.PNG)

Dataset ini memiliki **1610 baris** dan **17 kolom**. Beberapa kolom seperti "Invoice Price", "Cylinders", "Horsepower", "Torque", dan "Highway Fuel Economy" memiliki nilai kosong (null). Sementara kolom lainnya memiliki nilai yang lengkap tanpa kekurangan data.

Mayoritas kolom adalah bertipe **object** (biasanya tipe data string), kecuali untuk kolom "index" dan "Year" yang bertipe **int64**.

---

### Cek Nilai Unik pada Setiap Kolom

Pada tahap ini, analisis akan dilakukan untuk memeriksa nilai unik pada setiap kolom dalam dataset. Proses ini penting untuk memahami jenis data di setiap kolom serta menentukan apakah terdapat kolom dengan jumlah nilai yang terlalu banyak atau terlalu sedikit. Langkah ini juga berguna untuk memahami variabilitas dan keunikan data di setiap kolom.

Jika jumlah nilai unik suatu kolom kurang dari atau sama dengan 12, daftar nilai unik tersebut akan ditampilkan. Namun, jika jumlah nilai unik lebih dari 12, hanya jumlah nilai unik yang akan ditampilkan.

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
### **Ubah Tipe Data**

Pada bagian ini, kolom **MSRP** dan **Used/New Price** akan dibersihkan dan dikonversi. Kolom tersebut awalnya berformat string (termasuk simbol mata uang dan koma sebagai pemisah ribuan), yang akan diubah menjadi tipe data numerik (float). Konversi ini penting agar analisis statistik dan perhitungan matematika pada data harga mobil dapat dilakukan.

#### **Langkah-Langkah yang Dilakukan**:
1. Menghapus simbol mata uang (`$`) dan tanda koma (`,`) dari kolom **MSRP** dan **Used/New Price** menggunakan fungsi `replace()`.
2. Mengonversi kolom yang telah dibersihkan ke dalam format angka desimal (float) agar data dapat digunakan untuk analisis lebih lanjut.

#### **Implementasi:**
Langkah ini dilakukan dengan metode berikut:
- Kolom **MSRP** dan **Used/New Price** dibersihkan dari simbol dan tanda baca, kemudian diubah menjadi tipe data float menggunakan `astype()`.

#### **Penjelasan Hasil Output:**
Setelah dilakukan pembersihan dan konversi pada kolom **MSRP** dan **Used/New Price**, diperoleh hasil berikut:
- Kolom **MSRP** dan **Used/New Price** sekarang memiliki tipe data `float64` yang memungkinkan dilakukan perhitungan numerik.
- Jumlah entri pada dataset tetap konsisten tanpa adanya kehilangan data.
- Semua kolom yang relevan kini memiliki format data yang tepat untuk analisis lebih lanjut.

---

### **Mengubah Tipe Data Kolom Horsepower dan Torque**

Kolom **Horsepower** dan **Torque** juga dikonversi dari string ke float agar data dapat dianalisis secara kuantitatif. Pada proses ini, tidak dilakukan penanganan nilai yang hilang; hanya tipe data yang diubah.

#### **Langkah-Langkah yang Dilakukan**:
1. Ekstraksi nilai numerik awal (3 karakter pertama) dari kolom **Horsepower** dan **Torque** menggunakan `str[:3]`.
2. Mengonversi nilai yang diekstraksi menjadi tipe data float menggunakan `astype()`.

#### **Implementasi:**
- Kolom **Horsepower** dan **Torque** diproses untuk memastikan data numerik dapat digunakan langsung dalam perhitungan.

#### **Penjelasan Hasil Output:**
- Kolom **Horsepower** dan **Torque** kini memiliki tipe data `float64`.
- Nilai-nilai numerik di kedua kolom telah berhasil diekstraksi dan dikonversi tanpa memengaruhi jumlah entri dalam dataset.
- Proses ini memastikan data siap untuk analisis tanpa adanya manipulasi terhadap nilai yang hilang.

---

### **Cek Statistik Deskriptif**

Pada tahap ini, statistik deskriptif dari kolom-kolom numerik dalam dataset diperiksa untuk memahami distribusi data. Informasi statistik mencakup ukuran penyebaran (mean, std, min, max) serta posisi kuartil (25%, 50%, 75%). Proses ini dilakukan menggunakan fungsi `describe()`.

#### **Langkah-Langkah yang Dilakukan**:
1. Memeriksa distribusi statistik deskriptif untuk kolom numerik menggunakan `describe()` pada dataset.
2. Menganalisis hasil yang diperoleh untuk memahami karakteristik data, seperti rentang nilai, rata-rata, dan sebaran.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt20.PNG)

#### **Penjelasan Hasil Output**

Berdasarkan hasil dari fungsi `describe()`, berikut adalah informasi statistik untuk kolom numerik pada dataset, yaitu **Year**, **MSRP**, **Used/New Price**, **Horsepower**, dan **Torque**:

#### **1. Kolom Year:**
- Data tahun berkisar antara **2023** hingga **2024**.
- **Rata-rata tahun** adalah **2023.45**, menunjukkan mayoritas mobil dalam dataset berasal dari tahun 2023.
- Variasi dalam kolom ini kecil, karena hanya mencakup dua tahun, yaitu 2023 dan 2024.

#### **2. Kolom MSRP dan Used/New Price:**
- Rata-rata harga mobil (MSRP dan Used/New Price) adalah sekitar **72.542 dolar**.
- Harga minimum adalah **15.980 dolar**, sedangkan harga maksimum mencapai **391.100 dolar**, menunjukkan variasi harga yang signifikan di antara mobil yang ada.
- Simpangan baku (std) yang tinggi (**54.903 dolar**) menunjukkan bahwa harga mobil memiliki sebaran yang lebar, mencerminkan adanya variasi besar dalam data.

#### **3. Kolom Horsepower dan Torque:**
- **Rata-rata tenaga kuda (Horsepower)** mobil adalah sekitar **345.62**, sedangkan **rata-rata torsi (Torque)** adalah sekitar **364.97**.
- **Nilai maksimum tenaga kuda** mencapai **831**, sementara **maksimum torsi** adalah **811**, menunjukkan adanya mobil dengan performa mesin yang sangat tinggi.
- Sebagian besar mobil memiliki tenag

---

### Cek Missing Value

Pada tahap ini, dilakukan pemeriksaan untuk memastikan tidak terdapat nilai anomali dalam dataset, seperti NaN, null, atau nilai hilang lainnya.

![out](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt5.png)

#### Hasil
- Kolom `index`, `Make`, `Model`, `Year`, `Trim`, `MSRP`, `Used/New Price`, `Body Size`, `Body Style`, `Engine Aspiration`, `Drivetrain`, dan `Transmission` tidak memiliki nilai yang hilang, karena jumlah nilai yang hilang pada kolom-kolom ini adalah **0**.
- Kolom `Invoice Price` memiliki **552 nilai yang hilang**.
- Kolom `Cylinders` memiliki **165 nilai yang hilang**.
- Kolom `Horsepower` memiliki **5 nilai yang hilang**.
- Kolom `Torque` memiliki **27 nilai yang hilang**.
- Kolom `Highway Fuel Economy` memiliki **424 nilai yang hilang**.

---

### Cek Duplikasi Data

Pada bagian ini, dilakukan pemeriksaan untuk memastikan apakah terdapat baris data yang duplikat dalam dataset. Proses ini penting untuk memastikan bahwa data yang digunakan dalam analisis bersih dari duplikasi yang dapat memengaruhi hasil analisis.

**Langkah-langkah Implementasi:**

1. Dataset diperiksa untuk mengetahui jumlah baris yang terduplikasi.
2. Jumlah baris duplikat dihitung dan ditampilkan sebagai hasil pemeriksaan.

**Hasil Pemeriksaan:**

Setelah pemeriksaan, ditemukan bahwa **tidak ada baris duplikat** dalam dataset ini. Hal ini menunjukkan bahwa data telah tersusun dengan baik dan bebas dari duplikasi, sehingga siap untuk analisis lebih lanjut.

---
### **Cek Outlier**

Pada tahap ini, outlier dalam dataset divisualisasikan menggunakan boxplot. Outlier dapat memengaruhi analisis data dan hasil statistik deskriptif, sehingga penting untuk mengidentifikasinya. Visualisasi dilakukan pada kolom **MSRP**, **Used/New Price**, **Horsepower**, dan **Torque**.

#### **Langkah-Langkah yang Dilakukan**:
1. Membuat boxplot untuk kolom-kolom numerik yang relevan menggunakan pustaka `seaborn` dan `matplotlib`.
2. Menampilkan distribusi data beserta outlier pada kolom **MSRP**, **Used/New Price**, **Horsepower**, dan **Torque**.

#### **Visualisasi:**
- Boxplot menampilkan distribusi data, termasuk nilai tengah, rentang antar-kuartil (IQR), dan potensi outlier.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt21.png)

#### **Hasil Visualisasi**

Setelah visualisasi dilakukan, berikut adalah hasil analisis:
- **Terlihat banyak outlier** pada kolom **MSRP** dan **Used/New Price**, yang menunjukkan adanya beberapa mobil dengan harga yang sangat tinggi dibandingkan dengan mobil lainnya.
- Untuk kolom **Horsepower** dan **Torque**, meskipun terdapat outlier, sebagian besar data terdistribusi secara merata dengan rentang yang lebih kecil dibandingkan kolom harga.
  
---

### **Cek Angka Outlier Sebenarnya**

Pada bagian ini, kuartil pertama (**Q1**), kuartil ketiga (**Q3**), dan rentang interkuartil (**IQR**) dihitung untuk kolom-kolom yang relevan, yaitu **MSRP**, **Used/New Price**, **Horsepower**, dan **Torque**. **IQR** digunakan untuk mendeteksi nilai-nilai yang berada di luar batas normal (outliers).

#### **Langkah-Langkah yang Dilakukan**:
1. **Menghitung Q1 dan Q3**:
   - Q1 adalah nilai pada posisi 25% dari data yang terurut.
   - Q3 adalah nilai pada posisi 75% dari data yang terurut.
2. **Menghitung Rentang Interkuartil (IQR)**:
   - IQR adalah selisih antara Q3 dan Q1.
3. **Menentukan Batas Normal**:
   - Batas bawah dihitung dengan rumus: `Q1 - 1.5 * IQR`.
   - Batas atas dihitung dengan rumus: `Q3 + 1.5 * IQR`.
4. **Mengidentifikasi Outliers**:
   - Nilai yang lebih kecil dari batas bawah atau lebih besar dari batas atas dianggap sebagai outliers.
5. **Menyimpan Hasil**:
   - Informasi tentang batas bawah, batas atas, jumlah outliers, dan contoh nilai outliers disimpan dalam bentuk tabel.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt22.PNG)

#### **Penjelasan Hasil Output**

Hasil analisis outliers menunjukkan bahwa beberapa kolom memiliki nilai-nilai yang berada di luar batas normal berdasarkan penghitungan **IQR**:

#### **Kolom MSRP dan Used/New Price**:
- **Jumlah Outliers**: 166.
- **Penjelasan**: Kolom ini memiliki banyak outliers, yang menunjukkan bahwa ada sejumlah mobil dengan harga jauh lebih tinggi dibandingkan dengan rentang harga yang lebih umum.
- **Contoh Outliers**: 242.000, 125.800, 127.800.

#### **Kolom Horsepower**:
- **Jumlah Outliers**: 36.
- **Penjelasan**: Outliers di kolom ini menunjukkan adanya mobil dengan tenaga kuda yang sangat tinggi. 
- **Contoh Outliers**: 697, 637, 630.

#### **Kolom Torque**:
- **Jumlah Outliers**: 17.
- **Penjelasan**: Beberapa mobil memiliki nilai torsi yang sangat tinggi, menunjukkan performa mesin yang jauh di atas rata-rata.
- **Contoh Outliers**: 718, 738.

#### **Kesimpulan**
Analisis ini memberikan gambaran yang lebih mendalam tentang distribusi data dan nilai-nilai yang berada di luar batas normal. Informasi ini berguna untuk langkah selanjutnya, seperti memutuskan apakah outliers perlu dihapus, ditransformasi, atau dipertahankan sesuai dengan tujuan analisis.

---

### **Cek Korelasi Setiap Fitur**

Pada bagian ini, **pairplot** digunakan untuk memvisualisasikan hubungan antara fitur-fitur numerik dalam dataset, yaitu:

- **MSRP** (Harga Eceran yang Disarankan)
- **Horsepower** (Tenaga Kuda)
- **Torque** (Torsi)
- **Engine Aspiration** (Jenis Aspirasinya, misalnya turbocharged)

Pairplot membantu memahami hubungan antar fitur numerik dan pola berbeda berdasarkan jenis mesin. Parameter `hue='Engine Aspiration'` digunakan untuk memberikan warna berbeda sesuai kategori jenis aspirasinya, sehingga pola antar kategori dapat terlihat lebih jelas.

### **Langkah-Langkah yang Dilakukan**:
1. **Pengaturan Ukuran Gambar**: Ukuran gambar disesuaikan untuk memastikan setiap hubungan antar fitur dapat terlihat dengan jelas.
2. **Pairplot**: Menggunakan pairplot untuk memvisualisasikan hubungan antar fitur numerik.
3. **Penambahan Warna Berdasarkan Engine Aspiration**: Memberikan warna berbeda pada data berdasarkan kategori jenis aspirasinya, seperti turbocharged, twin-turbo, dsb.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt23.png)

Hasilnya

#### **1. MSRP vs. Horsepower**
- **Korelasi positif**: Semakin tinggi tenaga kuda, semakin tinggi pula MSRP.
- Mobil dengan tenaga kuda tinggi cenderung memiliki harga yang lebih mahal.
- Terdapat outlier di sekitar MSRP 350.000 dengan tenaga kuda rendah, kemungkinan disebabkan oleh faktor lain seperti merk, jenis mobil, dan fitur tambahan.

#### **2. MSRP vs. Torque**
- **Korelasi positif, meskipun tidak sekuat hubungan dengan tenaga kuda**.
- Mobil dengan torsi lebih tinggi cenderung lebih mahal.
- Outlier juga terlihat di sekitar MSRP 350.000, yang menunjukkan bahwa torsi bukan satu-satunya faktor utama dalam penentuan harga.

#### **3. Horsepower vs. Torque**
- **Korelasi positif**: Mobil dengan tenaga kuda tinggi umumnya memiliki torsi tinggi.
- Beberapa outlier di sekitar 200 tenaga kuda menunjukkan bahwa ada mobil dengan tenaga kuda rendah tetapi memiliki torsi tinggi.

#### **4. Pengaruh Engine Aspiration**
- **Twin-Turbo**: Biasanya memiliki tenaga kuda dan torsi tinggi, serta harga (MSRP) yang lebih mahal.
- **Turbocharged**: Memiliki tenaga kuda dan torsi yang lebih tinggi dibandingkan Naturally Aspirated dan Supercharged.
- **Naturally Aspirated**: Tenaga kuda dan torsi lebih rendah, dengan harga yang juga lebih rendah.
- **Supercharged**: Tenaga kuda dan torsi tinggi, dengan harga relatif tinggi.
- **Electric Motor**: Memiliki tenaga kuda dan torsi tinggi, dengan harga yang juga relatif mahal.

#### **Kesimpulan**
- Secara keseluruhan, terdapat **korelasi positif** antara **MSRP**, **tenaga kuda**, dan **torsi**.
- Jenis **engine aspiration** memiliki pengaruh signifikan terhadap tenaga kuda, torsi, dan harga mobil.
- Data menunjukkan bahwa faktor lain, seperti merk, jenis mobil, dan fitur tambahan, juga berpengaruh pada harga mobil, selain tenaga kuda dan torsi.

---

### Visualisasi Rata-Rata MSRP Berdasarkan Variabel Kategorikal

Pada bagian ini, dilakukan visualisasi bar chart untuk menggambarkan rata-rata MSRP (Manufacturer's Suggested Retail Price) berdasarkan variabel-variabel kategorikal berikut:

- **Make** (Merek)
- **Body Size** (Ukuran Bodi)
- **Body Style** (Gaya Bodi)
- **Engine Aspiration** (Jenis Aspirasi Mesin)
- **Drivetrain** (Jenis Penggerak)
- **Transmission** (Jenis Transmisi)

Setiap bar chart dirancang untuk memberikan wawasan tentang bagaimana kategori tersebut memengaruhi rata-rata MSRP.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt24.png)
![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt25.png)
![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt26.png)
![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt27.png)
![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt28.png)

### 1. **Make vs MSRP**
Grafik ini menunjukkan rata-rata MSRP untuk berbagai merek mobil:

- **Aston Martin** dan **Bentley** memiliki MSRP rata-rata tertinggi, yaitu sekitar **\$230,011** dan **\$270,636**, mencerminkan eksklusivitas dan kemewahan.
- **Audi**, **BMW**, dan **Mercedes-Benz** berada di kisaran **\$69,264 hingga \$81,439**, yang merepresentasikan merek premium dengan kinerja tinggi.
- **Ford** dan **Nissan** memiliki MSRP lebih rendah (**\$43,019 hingga \$53,306**), mencerminkan fokus pada pasar umum.

**Kesimpulan**: Merek premium cenderung memiliki MSRP lebih tinggi, mencerminkan kualitas dan fitur mewah.

### 2. **Body Size vs MSRP**
Grafik ini menggambarkan rata-rata MSRP berdasarkan ukuran bodi mobil:

- **Large (Besar)**: MSRP tertinggi (**\$79,251.4**), mencerminkan kendaraan seperti SUV mewah dan truk besar.
- **Midsize (Sedang)**: MSRP rata-rata sekitar **\$71,788.7**, mencakup banyak sedan keluarga dan SUV.
- **Compact (Kecil)**: MSRP terendah (**\$48,650.3**), mencerminkan mobil kecil yang ekonomis.

**Kesimpulan**: Kendaraan dengan bodi besar cenderung lebih mahal karena ruang yang lebih luas dan fitur tambahan.

### 3. **Body Style vs MSRP**
Grafik ini menggambarkan rata-rata MSRP berdasarkan gaya bodi:

- **Convertible (Atap Terbuka)**: Rata-rata tertinggi (**\$13,498.3**), sering mewakili kendaraan mewah.
- **Coupe**: MSRP tinggi (**\$10,717.4**), mencerminkan kendaraan sporty dan mewah.
- **Minivan (Cargo & Passenger)**: MSRP terendah (**\$35,482 hingga \$37,305**), mencerminkan fokus pada transportasi keluarga atau barang.

**Kesimpulan**: Gaya bodi memengaruhi harga sesuai dengan fungsi dan target pasar. Convertible dan coupe memiliki harga tinggi, sedangkan minivan lebih ekonomis.

### 4. **Drivetrain vs MSRP**
Grafik ini menunjukkan rata-rata MSRP berdasarkan jenis penggerak:

- **AWD (All-Wheel Drive)**: MSRP tertinggi (**\$90,929.4**), mencerminkan kendaraan dengan performa tinggi untuk berbagai medan.
- **4WD (Four-Wheel Drive)**: MSRP kedua tertinggi (**\$62,320**), umum untuk kendaraan off-road.
- **RWD (Rear-Wheel Drive)**: MSRP sedang (**\$58,166**), sering ditemukan pada kendaraan sport.
- **FWD (Front-Wheel Drive)**: MSRP terendah (**\$33,734.1**), umum pada mobil penumpang kompak.

**Kesimpulan**: Kendaraan AWD dan 4WD cenderung lebih mahal karena kemampuan untuk menghadapi berbagai medan.

### 5. **Transmission vs MSRP**
Grafik ini membandingkan MSRP rata-rata berdasarkan jenis transmisi:

- **Automatic Transmission**: Rata-rata MSRP lebih tinggi (**\$73,339.1**) dibandingkan manual, mencerminkan kenyamanan dan teknologi modern.
- **Manual Transmission**: Rata-rata MSRP lebih rendah (**\$46,035.9**), mencerminkan kendaraan yang lebih ekonomis atau sporty.

**Kesimpulan**: Kendaraan dengan transmisi otomatis lebih diminati karena kenyamanan, meskipun memiliki harga lebih tinggi.

### **Keseluruhan**
Bar chart ini memberikan wawasan tentang bagaimana variabel-variabel kategorikal seperti **merek, ukuran bodi, gaya bodi, jenis penggerak, dan transmisi** memengaruhi rata-rata MSRP kendaraan. Kendaraan premium dan fitur canggih umumnya berkorelasi dengan MSRP yang lebih tinggi.

---
### Analisis Distribusi Kolom Numerik dalam Dataset Mobil

Visualisasi ini bertujuan untuk menunjukkan distribusi data dari setiap kolom numerik dalam dataset mobil melalui histogram dengan overlay KDE (Kernel Density Estimation). Selain itu, ditampilkan pula statistik deskriptif seperti mean (rata-rata), median, dan mode dalam grafik untuk membantu interpretasi data.

#### Langkah-Langkah:

1. **Kolom Numerik**: Distribusi dihasilkan untuk kolom berikut:
   - `MSRP` (Manufacturer's Suggested Retail Price)
   - `Used/New Price` (Harga Bekas/Baru)
   - `Horsepower` (Tenaga Kuda)
   - `Torque` (Torsi)

2. **Visualisasi**:
   - Histogram menggunakan `sns.histplot` dengan overlay KDE.
   - Garis vertikal untuk statistik deskriptif:
     - **Mean**: Garis putus-putus merah.
     - **Median**: Garis solid hijau.
     - **Mode**: Garis titik-titik oranye.
   - Setiap grafik dilengkapi dengan judul, label sumbu, legenda, dan grid untuk keterbacaan yang lebih baik.

![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt29.png)
![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt30.png)
![tabel](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt32.png)

#### 1. **Distribusi Harga (Used/New Price dan MSRP)**

- **Deskripsi**: Grafik ini menunjukkan pola distribusi harga kendaraan berdasarkan:
  - Harga Bekas/Baru (`Used/New Price`)
  - Harga Eceran yang Disarankan (`MSRP`)

- **Statistik**:
  - **Rata-rata (Mean)**: 72,542.03
  - **Median**: 55,945.00
  - **Modus**: 77,900.75

- **Interpretasi**:  
  Grafik memperlihatkan puncak distribusi di sekitar nilai modus, yang mewakili harga kendaraan paling umum. Rata-rata dan median memberikan informasi tambahan tentang lokasi sebaran harga kendaraan dalam dataset.

#### 2. **Distribusi Horsepower**

- **Deskripsi**: Grafik ini menunjukkan distribusi tenaga kuda (Horsepower) kendaraan dalam dataset.

- **Statistik**:
  - **Rata-rata (Mean)**: 345.62
  - **Median**: 325.00
  - **Modus**: 275.00

- **Interpretasi**:  
  Sebagian besar kendaraan memiliki tenaga kuda di sekitar nilai modus. Rata-rata dan median memberikan informasi tambahan tentang variasi tenaga kuda di seluruh dataset.
  
#### 3. **Distribusi Torque**

- **Deskripsi**: Grafik ini menunjukkan pola distribusi torsi kendaraan (Torque).

- **Statistik**:
  - **Rata-rata (Mean)**: 364.97
  - **Median**: 339.00
  - **Modus**: 260.00

- **Interpretasi**:  
  Sebagian besar kendaraan memiliki torsi mendekati nilai modus. Rata-rata dan median menunjukkan bahwa ada penyebaran data di sekitar nilai tersebut, dengan beberapa kendaraan memiliki torsi lebih tinggi atau lebih rendah.

#### **Kesimpulan**

Visualisasi distribusi ini memberikan wawasan penting tentang:

- Pola distribusi harga kendaraan (`Used/New Price` dan `MSRP`).
- Penyebaran tenaga kuda (`Horsepower`) dan torsi (`Torque`).
- Statistik deskriptif seperti rata-rata, median, dan modus yang membantu memahami karakteristik data.

Informasi ini sangat berguna untuk analisis lebih lanjut, seperti mengidentifikasi segmen pasar kendaraan atau menentukan tren harga berdasarkan fitur kendaraan.

---

## Data Preparation

### Penanganan Missing Value

Langkah ini menjelaskan proses membersihkan dataset dan menangani masalah nilai yang hilang (*missing values*), serta menyesuaikan format data jika diperlukan. Penanganan nilai hilang sangat penting untuk memastikan kualitas data dan hasil analisis yang lebih akurat.

#### Langkah-Langkah Penanganan Missing Value

#### 1. **Menghapus Kolom dengan Terlalu Banyak Missing Values**
Kolom yang memiliki terlalu banyak nilai yang hilang dapat memengaruhi kualitas analisis. Oleh karena itu, kolom berikut dihapus dari dataset karena memiliki jumlah nilai hilang yang signifikan:
- `Invoice Price`
- `Cylinders`
- `Highway Fuel Economy`

#### 2. **Mengisi Missing Value pada Kolom Numerik**
Beberapa kolom numerik, seperti:
- `Horsepower`
- `Torque`

Langkah yang dilakukan:
- Mengisi nilai hilang menggunakan rata-rata (*mean*) dari masing-masing kolom. Metode ini digunakan karena rata-rata memberikan pendekatan yang seimbang untuk mengisi data yang hilang tanpa terlalu memengaruhi distribusi data.

#### 3. **Pengecekan Ulang Missing Values**
Setelah proses penghapusan kolom dan pengisian nilai hilang, dilakukan pengecekan ulang untuk memastikan tidak ada lagi nilai yang hilang di dataset.

![miss](https://raw.githubusercontent.com/miqbaljaffar/MLT/main/mlt34.PNG)

#### Hasil Output

Setelah dilakukan langkah-langkah di atas, berikut hasilnya:
- Tidak ada lagi nilai hilang pada dataset.
- Semua kolom memiliki jumlah nilai hilang sebesar **0**, yang memastikan dataset bersih dan siap untuk analisis lebih lanjut.

#### Kesimpulan

Langkah ini memastikan bahwa:
- Dataset bersih dari nilai hilang yang dapat memengaruhi hasil analisis.
- Kolom dengan data yang kurang signifikan atau terlalu banyak nilai hilang telah dihapus.
- Nilai hilang pada kolom numerik diisi menggunakan metode yang sesuai (mean), sehingga distribusi data tetap terjaga.

Proses ini meningkatkan kualitas data dan mendukung hasil analisis yang lebih valid.

---

### Penanganan Outlier

Bagian ini membahas langkah-langkah untuk mendeteksi dan menangani outlier dalam kolom numerik yang relevan, yaitu:
- **MSRP**
- **Used/New Price**
- **Horsepower**
- **Torque**

Metode yang digunakan adalah *Winsorizing*, di mana nilai outlier diganti dengan batas bawah atau batas atas berdasarkan perhitungan rentang interkuartil (IQR). Hal ini bertujuan untuk menjaga distribusi data tetap konsisten tanpa menghapus informasi penting.

#### Langkah-Langkah Penanganan Outlier

#### 1. **Menghitung Kuartil dan Rentang Interkuartil**
- **Q1 (Kuartil Pertama):** Nilai di mana 25% data berada di bawahnya.
- **Q3 (Kuartil Ketiga):** Nilai di mana 75% data berada di bawahnya.
- **IQR (Rentang Interkuartil):** Selisih antara Q3 dan Q1.

#### 2. **Menentukan Batas Bawah dan Batas Atas**
- **Lower Bound (Batas Bawah):** `Q1 - 1.5 * IQR`
- **Upper Bound (Batas Atas):** `Q3 + 1.5 * IQR`

#### 3. **Mengganti Nilai Outlier (Winsorizing)**
- Nilai yang lebih besar dari batas atas diganti dengan nilai batas atas.
- Nilai yang lebih kecil dari batas bawah diganti dengan nilai batas bawah.

#### 4. **Visualisasi dan Statistik**
- Setelah proses Winsorizing, distribusi data diperiksa menggunakan boxplot untuk melihat perubahan.
- Statistik deskriptif diperiksa untuk memastikan data telah dibersihkan dari outliers ekstrem.

GAMBAR

#### Hasil Penanganan Outlier

#### **1. Kolom MSRP dan Used/New Price**
- Nilai maksimum yang sebelumnya sangat tinggi telah dikurangi menjadi **114.870**, membuat rentang harga lebih terkontrol.
- Nilai rata-rata tetap sama di sekitar **62.715**, menunjukkan konsistensi harga mobil.
- Rentang harga (*range*) menjadi lebih stabil dengan pengurangan nilai ekstrem.

#### **2. Kolom Horsepower dan Torque**
- Nilai ekstrem pada **tenaga kuda (Horsepower)** dan **torsi (Torque)** telah dikurangi menjadi:
  - **Horsepower (621)**
  - **Torque (715)**
- Nilai rata-rata kini sekitar:
  - **Horsepower (344.71)**
  - **Torque (364.63)**
- Distribusi data menjadi lebih merata, sehingga analisis tidak dipengaruhi oleh outliers yang sangat tinggi.

#### Kesimpulan
Setelah dilakukan Winsorizing:
- Dataset menjadi lebih bersih dan distribusi nilai pada kolom-kolom numerik lebih terkontrol.
- Outliers ekstrem berhasil ditangani tanpa kehilangan informasi utama.
- Boxplot dan statistik deskriptif menunjukkan bahwa rentang data telah dioptimalkan.

Penanganan ini penting untuk menjaga keakuratan analisis dan menghindari distorsi yang disebabkan oleh nilai-nilai ekstrem.

---

### Feature Encoding and Normalization

Bagian ini menjelaskan langkah-langkah untuk memproses dataset melalui **encoding variabel kategorikal** dan **normalisasi fitur numerik**. Tujuan dari proses ini adalah untuk memastikan data siap digunakan dalam model machine learning dengan skala yang konsisten dan format yang sesuai.

#### Langkah-Langkah Feature Encoding dan Normalisasi

#### 1. **Menghapus Kolom yang Tidak Diperlukan**
Beberapa kolom yang tidak relevan untuk model dihapus, termasuk:
- **index**: Tidak memiliki informasi signifikan.
- **Model, Year, Trim, Used/New Price**: Tidak diperlukan untuk analisis lebih lanjut.

#### 2. **One-Hot Encoding untuk Variabel Kategorikal**
- Variabel kategorikal seperti **Make** dan **Body Style** diubah menjadi format biner (dummy variables) menggunakan `pd.get_dummies()`.
- Setiap kategori unik direpresentasikan sebagai kolom biner.

#### 3. **Normalisasi Fitur Numerik**
Fitur numerik seperti **Horsepower** dan **Torque** dinormalisasi untuk memastikan setiap fitur memiliki:
- **Mean = 0**
- **Standar Deviasi = 1**

Langkah ini dilakukan dengan:
- Menginisialisasi `StandardScaler()`.
- Menerapkan normalisasi menggunakan `scaler.fit_transform()` pada kolom numerik yang ditentukan.

GAMBAR

#### Hasil Proses

Setelah encoding dan normalisasi, dataset memiliki:
1. **Kolom Numerik yang Dinormalisasi**
   - Contoh: Horsepower dan Torque telah diubah ke skala standar.

2. **Kolom Dummy untuk Variabel Kategorikal**
   - Contoh: Make_Aston Martin, Drivetrain_AWD, dan Transmission_automatic.

3. **Dataset yang Siap untuk Modeling**
   - Dataset terdiri dari **37 kolom**, mencakup kolom dummy dan fitur numerik yang telah dinormalisasi.
   - Cuplikan 5 baris pertama dataset dapat digunakan untuk verifikasi visual.

#### Kesimpulan
Proses **encoding variabel kategorikal** dan **normalisasi fitur numerik** menghasilkan dataset yang lebih siap untuk analisis lanjutan. Semua kolom telah diubah ke format yang kompatibel untuk model machine learning dengan skala yang seragam.

---
### Feature Importance using Decision Tree

Bagian ini bertujuan untuk mengevaluasi pentingnya setiap fitur dalam memengaruhi target variabel (MSRP) dengan menggunakan **Decision Tree Classifier**. Analisis ini membantu untuk mengidentifikasi fitur-fitur mana yang memiliki kontribusi paling besar terhadap prediksi target (MSRP).

#### Langkah-Langkah

#### 1. **Pemisahan Fitur (X) dan Target (y)**

- **X**: Semua kolom kecuali **MSRP**.
- **y**: Kolom target (**MSRP**), yang dikonversi menjadi integer untuk kompatibilitas dengan model Decision Tree.

#### 2. **Inisialisasi Model**

- Menggunakan **DecisionTreeClassifier** dengan parameter berikut:
  - **criterion='entropy'**: Untuk mengukur impurity dengan entropy.
  - **max_depth=10**: Membatasi kedalaman pohon untuk mencegah overfitting.
  - **random_state=15**: Agar hasil replikasi konsisten.

#### 3. **Melatih Model**

- Model dilatih pada dataset yang telah diproses menggunakan `dt.fit(X, y)`.

#### 4. **Menghitung dan Menampilkan Pentingnya Fitur**

- Mengambil nilai pentingnya fitur dari model Decision Tree yang telah dilatih melalui `dt.feature_importances_`.
- Membuat DataFrame untuk menampilkan nama fitur dan nilai pentingnya.
- Mengurutkan fitur berdasarkan nilai pentingnya secara menurun.

#### 5. **Tampilkan Tabel Pentingnya Fitur**

Setelah model dilatih, tabel yang menunjukkan fitur dan bobot pentingnya akan ditampilkan. Fitur yang memiliki nilai penting tinggi adalah fitur yang memiliki kontribusi besar terhadap prediksi target MSRP.

| Feature                | Importance (%) |
|------------------------|----------------|
| Horsepower_No          | 26.99%         |
| Torque_No              | 15.12%         |
| Make_Ford              | 13.32%         |
| ...                    | ...            |

#### Hasil Analisis

Tabel pentingnya fitur menunjukkan daftar fitur beserta nilai pentingnya. Beberapa fitur dengan nilai penting tertinggi adalah:
- **Horsepower** (26.99%)
- **Torque** (15.12%)
- **Make_Ford** (13.32%)

#### Interpretasi

- **Fitur numerik** seperti **Horsepower** dan **Torque** memiliki pengaruh terbesar terhadap target (MSRP).
- Beberapa **fitur kategorikal** seperti **Make_Ford** dan **Engine Aspiration_Naturally Aspirated** juga menunjukkan kontribusi yang signifikan.

#### Kesimpulan

Hasil analisis ini memberikan wawasan tentang fitur mana yang paling relevan untuk prediksi MSRP. Informasi ini dapat digunakan untuk **menyederhanakan model** atau **memberikan fokus pada fitur yang signifikan** dalam model machine learning.

---

### Split Data

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
   - **R²:** 0.89 (89%) – Model cukup baik dalam menjelaskan varians data.
   - **RMSE:** 8518.653482 – Tingginya nilai RMSE menunjukkan adanya kesalahan prediksi yang signifikan.
   - **MAE:** 6262.459047 – Menunjukkan rata-rata kesalahan absolut yang cukup besar.

2. **K-Nearest Neighbors (KNN)**
   - **R²:** 0.92 (92%) – KNN lebih baik dibandingkan regresi linier dalam menjelaskan varians data.
   - **RMSE:** 7019.412983 – RMSE lebih rendah dibandingkan regresi linier, menunjukkan prediksi yang lebih akurat.
   - **MAE:** 4566.369565 – Kesalahan absolut lebih kecil dibandingkan regresi linier.

### Perbandingan Antara Model

| **Model**               | **R² Train** | **R² Test** | **RMSE Train** | **RMSE Test** | **MAE Train** | **MAE Test** |
|-------------------------|--------------|-------------|----------------|---------------|---------------|--------------|
| **Regresi Linier**      | 0.878314     | 0.888066    | 8527.974118    | 8518.653482   | 6427.383169   | 6262.459047  |
| **K-Nearest Neighbors** | 0.927509     | 0.923998    | 6582.165008    | 7019.412983   | 4510.563043   | 4566.369565  |

---
### Visualisasi Hasil Evaluasi Model Terbaik

Visualisasi ini bertujuan untuk memeriksa kinerja model terbaik dalam memprediksi nilai MSRP pada data latih. Analisis dilakukan menggunakan scatter plot untuk menunjukkan hubungan antara nilai aktual dan prediksi MSRP.

#### Scatter Plot:

- **Sumbu x**: Nilai MSRP yang sebenarnya (actual).
- **Sumbu y**: Nilai MSRP yang diprediksi oleh model (predicted).
- **Titik biru**: Representasi pasangan data actual vs. predicted pada data latih.

#### Garis Prediksi Ideal:
- **Garis putus-putus merah**: Menunjukkan prediksi ideal di mana nilai actual dan predicted sepenuhnya sama.
- Semakin dekat titik biru ke garis merah, semakin baik prediksi model.

#### Komponen Visualisasi:
1. **Judul**: "Train Data: Predicted vs Actual".
2. **Label Sumbu**:
   - Sumbu x: "Actual MSRP".
   - Sumbu y: "Predicted MSRP".
3. **Legenda**:
   - "Train Data" untuk titik biru.
   - "Ideal Prediction" untuk garis merah.
4. **Gridlines**: Ditambahkan untuk mempermudah pembacaan grafik.

#### Hasil Visualisasi:

GAMBAR

1. **Korelasi Positif**:  
   Grafik menunjukkan korelasi positif yang kuat antara nilai aktual dan nilai prediksi, yang mengindikasikan bahwa model mampu memprediksi MSRP dengan baik.

2. **Penyimpangan**:  
   Beberapa titik biru berada jauh dari garis merah, menunjukkan bahwa model tidak selalu memberikan prediksi yang sempurna.

3. **Kinerja Model**:  
   Titik-titik yang dekat dengan garis merah menunjukkan performa prediksi yang baik pada sebagian besar data.

#### Kesimpulan:  
Visualisasi ini memberikan gambaran yang jelas tentang kemampuan model dalam memprediksi nilai MSRP. Penyimpangan yang kecil dari garis merah menunjukkan bahwa model bekerja cukup baik, meskipun ada beberapa kasus di mana prediksi meleset.

---

### Visualisasi Residuals (Train Data)

Plot residual digunakan untuk menganalisis kesalahan prediksi model (residual), yaitu selisih antara nilai aktual dan prediksi pada data latih. Visualisasi ini membantu mengidentifikasi pola kesalahan tertentu yang dapat diperbaiki.

#### Komponen Visualisasi:
1. **Residuals**:  
   Residual dihitung sebagai perbedaan antara nilai aktual dan prediksi. Plot menunjukkan:
   - **Residual Positif**: Ketika nilai aktual lebih besar dari prediksi.
   - **Residual Negatif**: Ketika nilai aktual lebih kecil dari prediksi.

2. **Garis Referensi Nol**:  
   Garis horizontal di y = 0 digunakan sebagai referensi untuk menunjukkan lokasi ideal di mana residual seharusnya nol.

3. **Pewarnaan Residual**:
   - Residual positif ditampilkan dalam warna hijau.
   - Residual negatif ditampilkan dalam warna oranye.

4. **Statistik Residual**:
   - **Mean Residual**: Nilai rata-rata residual mendekati nol menunjukkan prediksi tidak bias.
   - **Standard Deviation Residual (Std Residual)**: Memberikan gambaran tingkat kesalahan rata-rata.

5. **Lowess Line**:
   Garis merah di plot menunjukkan hubungan lokal antara residual dan nilai prediksi untuk membantu mengidentifikasi pola.

#### Hasil Visualisasi:

GAMBAR

1. **Pola Residual**:
   - Tidak ada tren yang jelas: Residual tersebar secara acak di sekitar garis nol.
   - **Homoskedastisitas**: Penyebaran residual konsisten di seluruh rentang nilai prediksi, menunjukkan varians kesalahan tetap (tidak ada pola bias).

2. **Distribusi Residual**:
   - Residual positif dan negatif tersebar merata, mengindikasikan bahwa model tidak secara sistematis melebih-lebihkan atau meremehkan prediksi.
   - Beberapa residual yang jauh dari garis nol dapat menunjukkan adanya outlier.

3. **Statistik Residual**:
   - **Mean Residual**: Mendekati nol, menunjukkan prediksi tidak bias.
   - **Std Residual**: Mengindikasikan tingkat kesalahan prediksi rata-rata.

#### Kesimpulan:
Visualisasi residual menunjukkan bahwa model menangkap hubungan linier dengan baik tanpa pola bias yang jelas. Penyebaran residual yang konsisten dan rata-rata mendekati nol menunjukkan performa model yang stabil.

---

## Kesimpulan Akhir

- **Model KNN** menunjukkan performa yang lebih baik dibandingkan **Regresi Linier** dalam memprediksi harga kendaraan (**MSRP**):
  - R² KNN lebih tinggi (92%) dibandingkan regresi linier (87%), menunjukkan bahwa KNN dapat menjelaskan lebih banyak variasi data.
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
   Berdasarkan analisis model dan hasil feature importance, faktor yang paling mempengaruhi harga kendaraan baru (MSRP) adalah **Torque_No** dan **Horsepower_No**, dengan kontribusi masing-masing sebesar 26.99% dan 15.12%. Selain itu, merek Ford juga memiliki pengaruh signifikan terhadap harga kendaraan.

2. **Bagaimana Hubungan Antara Jenis Kendaraan dan Harga (MSRP)?**
   - **Merek (Make):** Merek premium seperti Aston Martin, Bentley, Audi, BMW, dan Mercedes-Benz memiliki harga yang lebih tinggi. Sedangkan merek seperti Ford dan Nissan lebih terjangkau untuk pasar massal.
   - **Ukuran Bodi (Body Size):** Kendaraan besar (Large) memiliki harga tertinggi, sementara kendaraan kecil (Compact) lebih ekonomis.
   - **Gaya Bodi (Body Style):** Convertible dan coupe biasanya memiliki harga lebih tinggi, mencerminkan pasar kendaraan mewah dan sporty. Sebaliknya, minivan cenderung lebih murah.
   - **Jenis Penggerak (Drivetrain):** Kendaraan dengan penggerak AWD atau 4WD memiliki harga lebih tinggi, sementara FWD cenderung lebih murah.
   - **Jenis Transmisi (Transmission):** Transmisi otomatis umumnya lebih mahal daripada transmisi manual.

3. **Bagaimana Kinerja Prediksi Model Dibandingkan dengan Data Aktual?**
   Model KNN memberikan hasil yang sangat baik, dengan R² sebesar 0.92 pada data latih dan 0.92 pada data uji. Nilai RMSE dan MAE yang cukup tinggi menunjukkan adanya kesalahan prediksi pada beberapa kasus, namun secara keseluruhan model memberikan prediksi yang cukup akurat.

4. **Bagaimana Tren Residual Memberikan Wawasan Tentang Kelompok yang Kurang Terlayani?**
   - **Residual** menunjukkan distribusi yang acak dan tidak ada bias sistematis pada kelompok tertentu. Model relatif adil untuk sebagian besar data, namun outlier pada residual menunjukkan bahwa ada kasus yang mungkin kurang terlayani oleh model.
   - Penyebaran residual yang konsisten di sekitar garis nol (homoskedastisitas) mengindikasikan model tidak memiliki pola kesalahan yang jelas.

5. **Bagaimana Distribusi Harga Kendaraan Berpengaruh pada Strategi Harga?**
   - **Distribusi Harga:** Modus (114,870.00) menunjukkan harga kendaraan yang paling sering ditemukan. Strategi harga dapat difokuskan untuk segmen ini dengan penawaran yang kompetitif.
   - **Rentang Harga:** Rata-rata harga (mean: 62,715.93) dan median (55,945.00) menunjukkan adanya ketimpangan harga, dengan harga lebih tinggi untuk kendaraan premium dan harga lebih rendah untuk kendaraan massal.
     
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
