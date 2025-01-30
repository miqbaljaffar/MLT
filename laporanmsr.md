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

Untuk memahami struktur data dari dataset yang digunakan, langkah pertama adalah menampilkan beberapa baris awal dari dataset. Dengan menampilkan data awal ini, kita bisa mendapatkan gambaran mengenai isi dan format data yang ada.

### Menampilkan Beberapa Baris Awal Dataset

Untuk menampilkan beberapa baris pertama dari dataset, kita bisa menggunakan fungsi `head()`. Fungsi ini akan mengembalikan sejumlah baris pertama dari dataset (secara default, biasanya 5 baris). Hal ini memungkinkan kita melihat contoh data yang ada dalam dataset.

Contohnya, kita dapat menampilkan preview dataset dengan menggunakan kode berikut:
1. Menggunakan fungsi `head()` pada dataset yang bernama `mobile_data` untuk menampilkan beberapa baris pertama dari dataset.
2. Output yang dihasilkan akan menampilkan beberapa baris awal dari dataset untuk memudahkan pemahaman struktur dan jenis data yang ada.

### Struktur Dataset

Setelah menampilkan preview dataset, kita dapat mengamati struktur dan kolom-kolom yang ada dalam dataset. Berikut adalah deskripsi dari beberapa kolom utama yang terdapat dalam dataset:

- **Product Name**: Kolom ini menyimpan nama produk ponsel yang ada dalam dataset.
- **Actual Price**: Kolom ini menyimpan harga asli dari produk sebelum ada diskon yang diterapkan.
- **Discount Price**: Kolom ini menyimpan harga produk setelah diskon diberikan.
- **Stars**: Kolom ini menyimpan rating dalam bentuk bintang yang diberikan oleh pengguna untuk produk tersebut.
- **Rating**: Kolom ini berisi jumlah total penilaian yang diberikan oleh pengguna untuk produk tersebut.
- **Reviews**: Kolom ini berisi jumlah ulasan yang diberikan oleh pengguna mengenai produk ponsel tersebut.
- **RAM (GB)**: Kolom ini menyimpan kapasitas RAM dalam gigabyte yang dimiliki oleh ponsel.
- **Storage (GB)**: Kolom ini menyimpan kapasitas penyimpanan dalam gigabyte yang dimiliki oleh ponsel.
- **Display Size (inch)**: Kolom ini berisi ukuran layar ponsel dalam satuan inci.
- **Camera**: Kolom ini berisi informasi terkait spesifikasi kamera yang dimiliki oleh ponsel.
- **Description**: Kolom ini berisi deskripsi singkat mengenai produk ponsel.
- **Link**: Kolom ini berisi tautan menuju halaman produk di Flipkart yang bisa digunakan untuk melihat detail lebih lanjut tentang produk tersebut.

Sumber dataset: [Mobiles Dataset](https://www.kaggle.com/datasets/mrmars1010/filpkart-mobiles)

### Mengganti Nilai "NIL" dengan NaN

Beberapa kolom dalam dataset memiliki nilai "NIL" yang digunakan untuk menandakan bahwa data tersebut kosong atau tidak tersedia. Untuk mempermudah penanganan nilai yang hilang, nilai "NIL" diganti dengan `NaN` menggunakan fungsi `replace()` dari Pandas.

Tujuan dari langkah ini adalah untuk mengganti nilai yang tidak relevan (seperti "NIL") dengan nilai yang dapat dikenali secara lebih mudah oleh Pandas sebagai data yang hilang (missing values). Dengan mengganti nilai "NIL" dengan `NaN`, kita dapat menangani nilai yang hilang dengan lebih efektif dalam analisis data selanjutnya.

Setelah mengganti nilai "NIL", dataset akan terlihat lebih konsisten dan siap untuk pemrosesan lebih lanjut.

### Menampilkan Informasi Dataset

Untuk memahami lebih lanjut tentang struktur dataset, jumlah entri, jumlah kolom, dan tipe data yang digunakan, kita dapat menggunakan fungsi `info()`. Fungsi ini memberikan informasi umum mengenai dataset, termasuk jumlah total entri (baris), jumlah kolom, tipe data tiap kolom, serta jumlah nilai yang tidak kosong (non-null count).

Berikut adalah cara untuk menampilkan informasi dataset:

1. Fungsi `info()` digunakan untuk menampilkan informasi umum tentang dataset.
2. Output dari fungsi ini mencakup jumlah total entri (984 entri), jumlah kolom (12 kolom), tipe data dari masing-masing kolom (seperti `object`, `float64`), serta jumlah nilai yang tidak kosong pada tiap kolom.

Berdasarkan hasil output, kita dapat mengamati beberapa hal berikut:
- Dataset memiliki 984 entri dan 12 kolom.
- Sebagian besar kolom bertipe `object` (misalnya, kolom yang berisi string), dan ada dua kolom yang bertipe numerik (`Stars` dan `Display Size (inch)`).
- Beberapa kolom memiliki nilai yang hilang, seperti kolom `Camera`, yang memiliki 76 nilai yang hilang dan perlu penanganan lebih lanjut pada tahap pembersihan data.

### Mengonversi Tipe Data Numerik

Kolom-kolom tertentu, seperti `Storage (GB)`, `RAM (GB)`, dan `Camera`, memiliki tipe data yang tidak sesuai untuk analisis numerik. Oleh karena itu, kita perlu mengonversi kolom-kolom ini ke tipe data numerik agar dapat digunakan dalam analisis lebih lanjut.

- Kolom `Storage (GB)` dan `RAM (GB)` yang awalnya bertipe `object` perlu dikonversi menjadi tipe numerik.
- Kolom `Camera` berisi angka yang disertai teks, sehingga kita perlu mengekstrak angka-angka tersebut dan mengonversinya menjadi tipe `float`.

Langkah-langkah untuk mengonversi tipe data adalah sebagai berikut:
1. Kolom `Storage (GB)` dan `RAM (GB)` dikonversi menggunakan fungsi `pd.to_numeric()`.
2. Kolom `Camera` dikonversi dengan mengekstrak angka menggunakan fungsi `str.extract()` dan mengonversinya ke tipe `float`.

Dengan langkah ini, kolom-kolom yang terkait dengan kapasitas penyimpanan, RAM, dan kamera kini dapat dianalisis secara numerik.

### Pengecekan Data Duplikat

Setelah pembersihan data, langkah selanjutnya adalah memeriksa apakah ada baris data yang duplikat dalam dataset. Data duplikat dapat mempengaruhi hasil analisis, sehingga perlu diidentifikasi dan dihapus jika diperlukan.

Untuk memeriksa jumlah baris yang duplikat, kita dapat menggunakan fungsi `duplicated()` yang akan mengembalikan nilai boolean untuk setiap baris yang duplikat. Dengan menjumlahkan hasilnya, kita dapat mengetahui jumlah baris yang duplikat.

Berdasarkan pengecekan yang dilakukan, hasil menunjukkan bahwa tidak ada baris data yang duplikat dalam dataset, sehingga kita tidak perlu melakukan penghapusan duplikat.

### Mengecek Missing Values

Langkah pertama dalam pembersihan data adalah untuk mengidentifikasi kolom mana saja yang memiliki nilai kosong (missing values). Hal ini penting dilakukan untuk mengetahui apakah ada data yang hilang dan memutuskan bagaimana cara menanganinya.

Untuk mengecek missing values dalam dataset, kita menggunakan fungsi `isnull()` yang akan mengembalikan nilai boolean untuk setiap nilai di dalam dataset, di mana `True` berarti nilai tersebut kosong (missing). Kemudian, kita menggunakan fungsi `sum()` untuk menghitung jumlah nilai kosong pada setiap kolom.

Output dari pengecekan missing values menunjukkan bahwa beberapa kolom memiliki nilai kosong, yaitu:

- Kolom **Actual price** memiliki 54 nilai kosong.
- Kolom **RAM (GB)** memiliki 161 nilai kosong.
- Kolom **Storage (GB)** memiliki 109 nilai kosong.
- Kolom **Camera** memiliki 76 nilai kosong.
- Kolom lainnya tidak memiliki missing values.

Dengan informasi ini, kita dapat memutuskan langkah selanjutnya dalam menangani nilai yang hilang.

### Menghapus Baris dengan Missing Values

Karena dataset ini berisi data produk nyata dari pasar, baris dengan missing values tidak dapat diisi dengan nilai rata-rata atau median. Oleh karena itu, langkah yang diambil adalah menghapus semua baris yang memiliki missing values.

Untuk menghapus baris yang mengandung missing values, kita menggunakan fungsi `dropna()`. Fungsi ini akan menghapus baris yang memiliki nilai kosong pada salah satu kolom.

Setelah menghapus baris dengan missing values, kita dapat memeriksa kembali apakah masih ada nilai yang hilang dengan menjalankan fungsi pengecekan missing values. Hasil pengecekan menunjukkan bahwa kini semua kolom dalam dataset tidak memiliki missing values.

### Memastikan Harga dalam Format Numerik

Beberapa kolom, seperti **Actual Price** dan **Discount Price**, mengandung simbol mata uang (₹) dan tanda koma (,). Agar kolom-kolom ini dapat digunakan dalam analisis numerik, simbol-simbol tersebut perlu dihapus.

Untuk memastikan harga dalam format numerik, kita menggunakan fungsi `replace()` dengan parameter regex untuk menghapus simbol mata uang dan tanda koma. Setelah itu, kita mengonversi kolom-kolom tersebut ke tipe data numerik (`float`) agar dapat digunakan dalam analisis statistik.

### Menangani Karakter dalam Kolom Rating dan Reviews

Kolom **Rating** dan **Reviews** mengandung karakter selain angka, seperti teks tambahan atau simbol. Untuk memastikan bahwa hanya angka yang diambil dan digunakan dalam analisis statistik, kita menggunakan Regular Expressions (regex) untuk mengekstrak angka-angka yang ada dalam kolom tersebut.

### Mengecek Tipe Data Setiap Kolom

Setelah melakukan pembersihan data, kita perlu memastikan bahwa tipe data setiap kolom sudah sesuai. Untuk itu, kita menggunakan fungsi `info()` yang memberikan informasi tentang jumlah entri non-null dan tipe data dari setiap kolom.

Berdasarkan hasil pengecekan tipe data, kita dapat melihat bahwa dataset kini memiliki 734 entri, dan tipe data dari kolom-kolom yang relevan telah berubah menjadi lebih sesuai. Sebagai contoh, kolom **Actual price** dan **Discount price** telah dikonversi ke tipe data `float64`, dan kolom **Rating** serta **Reviews** telah diperbaiki untuk hanya mengandung angka.

### Menampilkan Statistik Deskriptif

Langkah pertama dalam analisis data adalah mendapatkan ringkasan statistik dari kolom numerik dalam dataset. Statistik deskriptif memberikan gambaran umum tentang distribusi nilai dalam dataset, seperti rata-rata, nilai minimum, nilai maksimum, dan variasi antar nilai.

Untuk menampilkan statistik deskriptif, kita dapat menggunakan fungsi `describe()`. Fungsi ini akan memberikan informasi ringkas tentang kolom numerik dalam dataset.

Hasil statistik deskriptif pada dataset ini menunjukkan beberapa informasi penting sebagai berikut:

#### Harga Ponsel
- **Harga asli rata-rata**: ₹26,925, dengan **harga minimum** ₹1,899 dan **harga maksimum** ₹149,999.
- **Harga setelah diskon rata-rata**: ₹21,183, dengan nilai minimum ₹1,348.

#### Rating dan Ulasan
- **Rata-rata rating (Stars)**: 4.27, dengan rentang rating antara 3.5 dan 4.7.
- **Jumlah ulasan** tidak ditampilkan karena data ulasan sudah dibersihkan.

#### Spesifikasi Teknis
- **Ukuran layar rata-rata**: 6.63 inci, dengan nilai minimum 1.32 inci (nilai ini mungkin merupakan anomali data).
- **Resolusi kamera rata-rata**: 45.71 MP, dengan maksimum mencapai 200 MP.
- Variasi yang besar pada kolom **RAM** dan **Storage** menunjukkan kemungkinan kesalahan input atau ada produk dengan spesifikasi yang tidak umum (seperti perangkat keras untuk server yang termasuk dalam dataset).

### Mengecek Jumlah Nilai Unik dalam Setiap Kolom

Pengecekan jumlah nilai unik dalam setiap kolom bertujuan untuk memahami karakteristik data dalam kolom-kolom tersebut. Nilai unik memberikan gambaran tentang keragaman data dan membantu kita mengidentifikasi apakah ada data yang sangat terstandardisasi atau memiliki variasi yang tinggi.

Untuk melakukan pengecekan jumlah nilai unik pada setiap kolom, kita menggunakan fungsi `np.unique()` untuk mendapatkan daftar nilai unik pada setiap kolom dan kemudian menghitung jumlahnya. Kolom dengan nilai unik yang jumlahnya lebih kecil atau sama dengan 12 akan dicetak bersama dengan daftar nilai uniknya, sedangkan kolom dengan nilai unik lebih dari 12 hanya akan menampilkan jumlah nilai uniknya.

Hasil analisis menunjukkan beberapa temuan berikut:

- **Product Name**: 500 nilai unik, menunjukkan bahwa dataset ini mencakup berbagai macam produk ponsel.
- **Actual Price**: 89 nilai unik, rentang harga ponsel yang lebih ringkas setelah data yang tidak lengkap dihapus.
- **Discount Price**: 244 nilai unik, menunjukkan variasi diskon yang masih cukup bervariasi.
- **Stars**: 12 nilai unik, yaitu rentang rating bintang yang diberikan produk (3.5, 3.6, 3.8, 3.9, 4.0, 4.1, 4.2, 4.3, 4.4, 4.5, 4.6, 4.7).
- **Rating**: 265 nilai unik, yang menunjukkan adanya banyak variasi dalam jumlah rating.
- **Reviews**: 214 nilai unik, yang menunjukkan variasi dalam jumlah ulasan yang diberikan oleh pengguna.
- **RAM (GB)**: 9 nilai unik, dengan nilai yang meliputi kapasitas RAM dari 2 GB hingga 46875 GB. Nilai 46875 GB kemungkinan adalah kesalahan input.
- **Storage (GB)**: 6 nilai unik, dengan variasi kapasitas penyimpanan seperti 32 GB, 64 GB, 128 GB, 256 GB, dan 512 GB.
- **Display Size (inch)**: 33 nilai unik, menunjukkan variasi ukuran layar produk ponsel.
- **Camera**: 13 nilai unik, menunjukkan berbagai variasi resolusi kamera.
- **Description**: 333 nilai unik, menunjukkan bahwa sebagian besar produk memiliki deskripsi yang berbeda-beda.
- **Link**: 734 nilai unik, karena setiap produk memiliki tautan unik menuju halaman produk.

#### Anomali yang Perlu Diperiksa
- **RAM sebesar 46875 GB** kemungkinan merupakan kesalahan input yang perlu diperbaiki.

### Menghapus Anomali pada Kolom RAM (GB)

Untuk membersihkan dataset dari anomali data, kita perlu memfilter dataset dengan hanya menyertakan baris yang tidak memiliki nilai RAM sebesar 46875 GB. Nilai ini jelas merupakan kesalahan input, dan kita tidak ingin memasukkan data yang tidak valid dalam analisis lebih lanjut.

Untuk melakukan ini, kita dapat memfilter dataset dengan menghapus baris yang memiliki nilai RAM sebesar 46875 GB. Hasilnya, dataset baru akan berisi data yang lebih bersih dan valid.

---

### Univariat Exploratory Data Analysis (EDA)

#### Visualisasi Distribusi Harga Setelah Diskon

Langkah pertama adalah visualisasi distribusi harga setelah diskon dalam dataset. Visualisasi ini membantu untuk memahami bagaimana harga produk tersebar setelah mendapatkan potongan harga.

Dengan menggunakan histogram, kita dapat menampilkan distribusi harga setelah diskon dengan beberapa parameter tambahan untuk memperjelas distribusinya, seperti menambahkan kurva KDE (Kernel Density Estimation) untuk memperkirakan distribusi data secara halus.

Hasil visualisasi menunjukkan bahwa distribusi harga setelah diskon cenderung ke kanan (right-skewed), yang berarti sebagian besar produk terjual dengan harga lebih rendah, namun ada beberapa produk dengan harga jauh lebih tinggi.

##### Kesimpulan:
- Grafik menunjukkan distribusi harga setelah diskon yang memiliki ekor panjang di sisi kanan.
- Sebagian besar produk terjual di kisaran harga yang lebih rendah, dengan harga berkisar dari sekitar ₹0 hingga lebih dari ₹120,000.
- Median harga setelah diskon berada di sekitar ₹20,000, menunjukkan bahwa mayoritas produk berada pada harga ini.
- Ada beberapa puncak dalam distribusi harga, yang mungkin mencerminkan kategori produk dengan harga yang berbeda.
- Ekor panjang pada grafik menunjukkan adanya beberapa produk yang dijual dengan harga sangat tinggi.
- Kurva KDE yang ditambahkan memberikan estimasi distribusi normal, namun bentuk kurva ini tidak mengikuti distribusi data dengan baik, yang menunjukkan bahwa distribusi harga setelah diskon tidak normal.

---

#### Visualisasi Distribusi Rating Produk

Selanjutnya, visualisasi dilakukan untuk menampilkan distribusi rating produk yang diberikan oleh pengguna. Diagram batang (bar plot) digunakan untuk menghitung jumlah produk yang memiliki rating tertentu. Grafik ini memberikan informasi yang jelas tentang seberapa banyak produk yang mendapat rating dalam rentang nilai tertentu.

##### Kesimpulan:
- Grafik menunjukkan bahwa sebagian besar produk memiliki rating di atas 4.0.
- Ada lonjakan yang signifikan pada rating 4.2, menunjukkan bahwa rating ini paling sering diberikan pada produk.
- Rating produk cenderung menurun secara bertahap setelah rating 4.2.
- Sangat sedikit produk yang memiliki rating di bawah 4.0, yang menunjukkan bahwa mayoritas produk mendapat penilaian baik dari pengguna.

---

#### Visualisasi Distribusi RAM pada Produk

Untuk memahami spesifikasi perangkat lebih lanjut, visualisasi distribusi RAM juga dilakukan. Diagram batang digunakan untuk menampilkan jumlah produk berdasarkan kapasitas RAM yang dimiliki. Ini membantu untuk melihat variasi kapasitas RAM yang ada dalam dataset dan memahami preferensi konsumen terhadap konfigurasi RAM.

##### Kesimpulan:
- Mayoritas perangkat memiliki **RAM 8GB**, dengan sekitar 330 perangkat.
- Perangkat dengan **RAM 4GB** menduduki posisi kedua dengan sekitar 140 perangkat.
- Perangkat dengan **RAM 12GB** dan **RAM 6GB** memiliki jumlah yang hampir sama, sekitar 110 perangkat.
- Perangkat dengan RAM lebih besar, seperti **16GB** dan **32GB**, relatif sedikit dalam dataset ini.

##### Interpretasi:
- RAM 8GB adalah konfigurasi yang paling umum digunakan dalam perangkat yang dianalisis.
- Ada juga sejumlah perangkat dengan RAM lebih rendah (4GB) dan RAM lebih tinggi (12GB, 6GB), yang menunjukkan variasi dalam kebutuhan konsumen terhadap kapasitas RAM.
- Perangkat dengan RAM lebih tinggi (16GB dan 32GB) adalah minoritas, yang kemungkinan disebabkan oleh harga yang lebih mahal atau kebutuhan spesifik dari produk tersebut.

---
### Multivariat EDA (Exploratory Data Analysis)

#### Korelasi antara Harga dan Rating

Untuk menganalisis hubungan antara harga diskon (Discount Price) dan rating produk (Stars), digunakan **scatter plot**. Scatter plot ini digunakan untuk mengidentifikasi apakah terdapat pola atau hubungan antara dua variabel ini.

Dalam visualisasi ini:
- Sumbu X mewakili harga diskon produk (Discount Price).
- Sumbu Y mewakili rating produk (Stars).

##### Kesimpulan:
- Tidak ada korelasi yang jelas antara harga produk dan rating.
- Banyak produk dengan harga yang bervariasi memiliki rating yang serupa, terutama di kisaran 4.0 hingga 4.6 bintang.
- Beberapa produk dengan harga tinggi (lebih dari ₹60,000) memiliki rating yang lebih tinggi (di atas 4.5), tetapi ada juga yang memiliki rating lebih rendah (di bawah 4.2).
- Ada beberapa produk dengan harga rendah (di bawah ₹20,000) yang memiliki rating tinggi (di atas 4.5), meskipun sebagian besar produk dengan harga tersebut memiliki rating yang lebih rendah (di bawah 4.0).

#### Distribusi Harga Berdasarkan Kapasitas RAM

Selanjutnya, untuk menganalisis bagaimana harga produk terdistribusi berdasarkan kapasitas RAM, digunakan **box plot**. Box plot ini menggambarkan distribusi harga dalam berbagai kategori RAM (dalam GB).

##### Kesimpulan:
- **Korelasi Positif:** Terdapat korelasi positif yang jelas antara kapasitas RAM dan harga. Semakin besar kapasitas RAM, semakin tinggi harga produk.
- **Rentang Harga:** Produk dengan kapasitas RAM yang lebih rendah (misalnya 2GB) cenderung memiliki harga lebih rendah, sementara produk dengan RAM tinggi (misalnya 16GB) memiliki harga yang lebih tinggi.
- **Outlier:** Beberapa kategori RAM, seperti 16GB dan 32GB, memiliki nilai outlier, yaitu harga yang jauh lebih tinggi dibandingkan produk lainnya dalam kategori yang sama.
- **Variasi Harga:** Terdapat variasi harga yang signifikan pada produk dengan kapasitas RAM tinggi (16GB, 32GB). Ini menunjukkan bahwa produk dengan RAM besar mungkin memiliki rentang harga yang lebih luas tergantung pada spesifikasi lainnya, seperti merek atau fitur tambahan.

#### Perbandingan Harga Berdasarkan Brand

Brand dari produk ponsel diekstrak dari nama produk dengan mengambil kata pertama sebagai nama brand. Kemudian, digunakan **box plot** untuk membandingkan distribusi harga berdasarkan brand.

##### Langkah Ekstraksi Brand:
- Brand diekstrak dari kolom "Product Name" dengan mengambil kata pertama dari setiap nama produk sebagai nama brand.

##### Visualisasi:
- **Sumbu X** menunjukkan brand handphone.
- **Sumbu Y** menunjukkan harga setelah diskon (Discount Price).
- Setiap kotak dalam box plot menunjukkan distribusi harga untuk masing-masing brand, dengan nilai median, kuartil pertama, dan kuartil ketiga, serta outlier yang terdeteksi.

##### Hasil:
- Ada beberapa brand dengan harga yang lebih tinggi dan terdapat outlier dengan harga yang sangat tinggi dibandingkan produk lainnya.
- Brand seperti **OnePlus**, **Google**, dan **Samsung** menunjukkan rentang harga yang lebih tinggi, dengan beberapa produk melebihi ₹50,000.
- **Micromax** dan **Nokia** memiliki rentang harga yang lebih rendah, dengan sebagian besar produk mereka dijual di kisaran harga yang lebih terjangkau.

##### Interpretasi:
- Grafik ini menunjukkan bahwa harga handphone sangat bervariasi di antara brand yang ada.
- Beberapa brand besar, seperti **OnePlus**, **Google**, dan **Samsung**, cenderung menawarkan produk dengan harga yang lebih tinggi.
- Brand lain seperti **Micromax** dan **Nokia** memiliki harga yang lebih terjangkau, menunjukkan segmen pasar yang berbeda.
- Adanya outlier dalam setiap brand menunjukkan bahwa beberapa produk dari setiap brand memiliki harga yang jauh lebih tinggi atau lebih rendah dari rata-rata produk dalam kategori tersebut.

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
