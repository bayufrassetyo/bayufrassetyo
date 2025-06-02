# 📊 Breast Cancer Classification Project - Bayu Frassetyo Wibowo



## 🧠 Disusun oleh Bayu Frassetyo Wibowo

Ini adalah proyek pertama dalam klasifikasi data untuk memenuhi submission Dicoding. Proyek ini membangun model machine learning yang dapat mengklasifikasikan apakah sampel tumor payudara bersifat ganas (malignant) atau jinak (benign) berdasarkan fitur yang diukur dari citra mikroskopik.



![Gambar Ilustrasi](https://drive.google.com/uc?export=view&id=1iEly0sw8Pp6lG16uJ-sK1c9P-i0OMm1_)

## **Domain Proyek**



**Bidang**: Kesehatan (Onkologi)



**Fokus**: Deteksi Dini Kanker Payudara Berbasis Machine Learning



### **Latar Belakang**



Kanker payudara merupakan jenis kanker yang paling umum terjadi pada wanita di seluruh dunia. Menurut Organisasi Kesehatan Dunia (WHO), pada tahun 2020 terdapat lebih dari 2,3 juta kasus baru kanker payudara dan 685.000 kematian akibat kanker ini secara global. Deteksi dini sangat penting karena dapat secara signifikan meningkatkan peluang kesembuhan dan menurunkan tingkat kematian.



Salah satu metode diagnosis kanker payudara adalah dengan menganalisis karakteristik sel dari jaringan tumor menggunakan mikroskop. Namun, metode ini sangat bergantung pada keahlian patolog dan rawan terhadap subjektivitas manusia, sehingga berisiko menimbulkan kesalahan diagnosis.



Oleh karena itu, diperlukan sebuah sistem pendukung keputusan berbasis machine learning yang dapat membantu tenaga medis dalam mendiagnosis kanker payudara secara lebih objektif dan efisien. Proyek ini bertujuan untuk mengembangkan model klasifikasi yang mampu membedakan antara tumor ganas (malignant) dan jinak (benign) berdasarkan fitur-fitur statistik dari citra mikroskopik sel.



![Gambar Ilustrasi](https://drive.google.com/uc?export=view&id=1qtKx2WhnvBBJIRddzVC2MiGeMkkYcyV-)



**Referensi**:



* [WHO Breast Cancer Fact Sheet](https://www.who.int/news-room/fact-sheets/detail/breast-cancer)

* [GLOBOCAN 2020 - Global Cancer Observatory](https://gco.iarc.fr/today/data/factsheets/cancers/20-Breast-fact-sheet.pdf)



## Business Understanding



**Karakteristik Bisnis**



Proyek ini ditujukan untuk membantu institusi kesehatan seperti rumah sakit, laboratorium patologi, atau layanan kesehatan berbasis teknologi dalam menganalisis hasil biopsi jaringan payudara. Tujuannya adalah menyediakan sistem pendukung keputusan berbasis machine learning yang dapat digunakan oleh tenaga medis untuk meningkatkan akurasi dan efisiensi diagnosis awal kanker payudara.



* Rumah sakit atau laboratorium yang menganalisis hasil biopsi payudara.



* Layanan diagnosa medis berbasis teknologi AI untuk mendukung diagnosis awal kanker payudara.



**Problem Statement**



1. **Fitur apa yang paling berpengaruh** dalam membedakan tumor ganas dan jinak?



2. **Bagaimana menyiapkan data medis** agar akurat dan siap digunakan untuk klasifikasi?



3. **Algoritma machine learning apa yang paling tepat** untuk digunakan dalam kasus klasifikasi seperti ini?



**Goals**



* Mengidentifikasi fitur-fitur utama yang mempengaruhi diagnosis kanker payudara.



* Melakukan pembersihan dan transformasi data medis agar sesuai untuk input model.



* Membangun dan mengevaluasi model klasifikasi yang mampu membedakan antara tumor ganas dan jinak dengan **akurasi minimal 95%**.



* Menyediakan solusi yang dapat diintegrasikan ke dalam sistem diagnosis berbasis teknologi.



**Solution Statement**



Untuk mencapai tujuan di atas, pendekatan yang diambil dalam proyek ini meliputi beberapa solusi terukur:



1. **Baseline Model**



* Algoritma awal yang digunakan adalah **K-Nearest Neighbor (KNN)** karena kesederhanaannya dan efektivitas awal dalam data yang relatif kecil.



* Model ini akan memberikan **tolak ukur awal** (baseline) performa klasifikasi.



2. **Model Improvement**



* Dilakukan pengembangan model dengan algoritma lain seperti:



* **Random Forest (RF)** – karena kemampuannya dalam menangani fitur yang kompleks dan mencegah overfitting.



* **AdaBoost** – sebagai metode ensemble yang dapat meningkatkan akurasi dengan menggabungkan banyak model lemah.



* Setiap model akan dievaluasi berdasarkan **metrik akurasi, precision, recall, dan F1-score**.



* **Hyperparameter tuning** dilakukan menggunakan Grid Search untuk meningkatkan performa masing-masing model.



3. **Model Selection**



* Model terbaik akan dipilih berdasarkan **metrik evaluasi utama**, yaitu:



* **F1-Score** sebagai indikator utama karena seimbang antara precision dan recall, penting untuk data medis yang memiliki risiko tinggi akibat false negative.



* **Akurasi minimal target sebesar 95%** ditetapkan sebagai syarat agar model layak digunakan dalam konteks klinis.



# **Data Understanding**



**Deskripsi Dataset**



Dataset yang digunakan adalah **Breast Cancer Wisconsin (Diagnostic) Dataset** yang tersedia secara publik di UCI Machine Learning Repository.



* **Sumber Dataset**:

[UCI Machine Learning Repository - Breast Cancer Wisconsin](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29)



* **Jumlah Sampel**: 569 observasi



* **Jumlah Fitur**: 32 fitur numerik



* - Dataset awal terdiri dari 32 kolom, yaitu:



	- 1 kolom ID pasien (id) – digunakan sebagai identifikasi unik dan tidak relevan untuk pemodelan



	- 1 kolom target (diagnosis)



	- 30 kolom fitur numerik hasil ekstraksi gambar



* **Target**: Diagnosis (M = Malignant / Ganas, B = Benign / Jinak)



**Distribusi Label (Diagnosis)**



* Benign (Jinak): 357 sampel (62.7%)



* Malignant (Ganas): 212 sampel (37.3%)



Dataset ini cukup seimbang, namun tetap penting memperhatikan metrik seperti precision dan recall dalam evaluasi model untuk menghindari dampak dari prediksi yang salah pada kasus medis.



**Pemeriksaan Missing Value**



* Tidak ditemukan nilai kosong (missing values) dalam dataset. Semua fitur memiliki nilai valid, sehingga tidak diperlukan proses imputasi data.



**Daftar Fitur dan Deskripsi**



Setiap fitur dalam dataset adalah hasil ekstraksi statistik dari gambar digital mikroskopik inti sel. Ada 10 jenis pengukuran, masing-masing dihitung dalam 3 bentuk: mean, standard error, dan nilai terburuk (worst).



Berikut beberapa contoh fitur penting:



| Fitur | Deskripsi Singkat |

| ------------------------ | ----------------------------------------------------------- |

| radius\_mean | Rata-rata jarak dari pusat ke batas tumor |

| texture\_mean | Variasi tingkat abu-abu pada citra |

| perimeter\_mean | Keliling tumor |

| area\_mean | Luas permukaan tumor |

| smoothness\_mean | Tingkat keseragaman batas tumor |

| compactness\_mean | Tingkat kepadatan (perbandingan antara perimeter² dan area) |

| concavity\_mean | Derajat cekungan kontur tumor |

| symmetry\_mean | Simetri bentuk tumor |

| fractal\_dimension\_mean | Kompleksitas permukaan tumor |



Daftar lengkap fitur terdiri dari 30 kolom, yaitu hasil dari:



\[*mean, standard error, worst] × \[radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension*].



ini kelengkapan hasil datanya :



| Fitur | Deskripsi Singkat |

| ----------------------------- | ------------------------------------------------------- |

| **diagnosis** | Label target: 1 = ganas (malignant), 0 = jinak (benign) |

| **radius\_mean** | Rata-rata jarak dari pusat ke batas tumor |

| **texture\_mean** | Variasi tingkat keabuan pada citra |

| **perimeter\_mean** | Keliling rata-rata tumor |

| **area\_mean** | Luas permukaan rata-rata tumor |

| **smoothness\_mean** | Keseragaman kontur tepi rata-rata |

| **compactness\_mean** | Kepadatan rata-rata (perimeter² / area - 1) |

| **concavity\_mean** | Rata-rata cekungan pada kontur tumor |

| **concave\_points\_mean** | Rata-rata jumlah titik cekung di kontur |

| **symmetry\_mean** | Tingkat simetri bentuk tumor rata-rata |

| **fractal\_dimension\_mean** | Rata-rata kompleksitas kontur (fraktal dimensi) |

| **radius\_se** | Standar deviasi radius |

| **texture\_se** | Standar deviasi tekstur |

| **perimeter\_se** | Standar deviasi perimeter |

| **area\_se** | Standar deviasi area |

| **smoothness\_se** | Standar deviasi smoothness |

| **compactness\_se** | Standar deviasi compactness |

| **concavity\_se** | Standar deviasi concavity |

| **concave\_points\_se** | Standar deviasi concave points |

| **symmetry\_se** | Standar deviasi symmetry |

| **fractal\_dimension\_se** | Standar deviasi fractal dimension |

| **radius\_worst** | Nilai radius terbesar dari pengukuran |

| **texture\_worst** | Nilai tekstur terbesar dari pengukuran |

| **perimeter\_worst** | Nilai perimeter terbesar dari pengukuran |

| **area\_worst** | Nilai area terbesar dari pengukuran |

| **smoothness\_worst** | Nilai smoothness terbesar dari pengukuran |

| **compactness\_worst** | Nilai compactness terbesar dari pengukuran |

| **concavity\_worst** | Nilai concavity terbesar dari pengukuran |

| **concave\_points\_worst** | Nilai concave points terbesar dari pengukuran |

| **symmetry\_worst** | Nilai symmetry terbesar dari pengukuran |

| **fractal\_dimension\_worst** | Nilai fractal dimension terbesar dari pengukuran |



## **Visualisasi Data (EDA - Exploratory Data Analysis)**



Beberapa teknik visualisasi yang digunakan untuk memahami data antara lain:



* 📊 **Histogram Fitur**



Menampilkan distribusi fitur seperti radius\_mean, texture\_mean, dan area\_mean untuk melihat apakah data berdistribusi normal atau miring ke salah satu sisi.



![Histogram radius mean](https://drive.google.com/uc?export=view&id=17JW_uaJrkXpZwpIvc5R2BHECf_gAOFgy)



![Histogram texture mean](https://drive.google.com/uc?export=view&id=1U2arFsLvg9hZZ9l-HlUPh7je1Ww5P4rW)



![Histogram area mean](https://drive.google.com/uc?export=view&id=1Z4bvt6wKjVRsOk7RgNmudNAEEFsO2azT)



* 🔥 **Heatmap Korelasi**



Korelasi antar fitur divisualisasikan menggunakan heatmap (misalnya dengan seaborn.heatmap). Ditemukan bahwa fitur radius\_mean, perimeter\_mean, dan area\_mean memiliki korelasi tinggi dengan diagnosis dan juga saling berkorelasi.



![Heatmap Korelasi](https://drive.google.com/uc?export=view&id=1B66Zq-UxXhLE8XkSZWEjsPPlg0NGHQqq)



* 🎯 **Boxplot Diagnosis vs. Fitur**



Visualisasi seperti boxplot radius\_mean terhadap label diagnosis menunjukkan perbedaan distribusi yang jelas antara tumor jinak dan ganas, mengindikasikan bahwa fitur ini sangat diskriminatif.



![Boxplot Diagnosis vs. Fitur](https://drive.google.com/uc?export=view&id=1yuAIBGRi6vPmnnmt7VxEKeQylRRO4DvG)



Sebelum membangun model machine learning, diperlukan beberapa tahap **preprocessing** untuk memastikan bahwa data dalam kondisi optimal. Tahapan ini bertujuan untuk:



* Menghindari bias karena perbedaan skala fitur.



* Mengubah data kategori menjadi numerik.



* Memastikan model dapat belajar dengan baik tanpa gangguan teknis dari data mentah.



Berikut adalah langkah-langkah data preparation yang dilakukan:



**1. Label Encoding**



**Deskripsi**:



Target variabel Diagnosis yang semula dalam bentuk kategorikal (M = Malignant / B = Benign) dikonversi menjadi nilai numerik.



**Langkah**:



M (Malignant) → 1



B (Benign) → 0



**Alasan**:



Sebagian besar algoritma machine learning hanya dapat bekerja dengan data numerik. Oleh karena itu, label kategorikal perlu dikonversi agar bisa digunakan sebagai **target klasifikasi**.



![Boxplot Diagnosis vs. Fitur](https://drive.google.com/uc?export=view&id=1Co_qWE1sSj08VL5iMmvNkUJBgpE5VOwE)



2. **Fitur dan Target Splitting**



**Deskripsi**:



Data dipisahkan menjadi dua bagian utama:



* **Fitur (X**): Terdiri dari 31 kolom numerik yang merepresentasikan karakteristik dari tumor, seperti ukuran, tekstur, dan bentuk. Fitur-fitur ini digunakan sebagai input untuk model.



* **Target (y)**: Label diagnosis, di mana 0 menunjukkan tumor jinak (**benign**) dan 1 menunjukkan tumor ganas (**malignant**).



**Alasan**:



Pemisahan ini penting untuk memastikan bahwa proses pelatihan model hanya menggunakan informasi dari fitur input tanpa akses ke label target. Hal ini mencegah **data leakage** yang dapat menyebabkan model overfitting atau hasil evaluasi yang tidak valid.



![Boxplot Diagnosis vs. Fitur](https://drive.google.com/uc?export=view&id=1pPXFSWnAKPAr9bqA9OUeBsxBS0xOeOLO)



3. **Normalisasi (Standardisasi)**



**Deskripsi**:



Semua fitur numerik dinormalisasi menggunakan **StandardScaler**, yang mengubah nilai menjadi distribusi dengan rata-rata 0 dan standar deviasi 1.



Alasan:



Beberapa algoritma seperti **K-Nearest Neighbors (KNN)** dan **AdaBoost** sangat sensitif terhadap skala fitur. Jika data tidak distandarisasi, fitur dengan skala besar dapat mendominasi dan menyebabkan model bias terhadap fitur tersebut.



Contoh:



* radius\_mean memiliki nilai antara 6.98–28.11,



* sedangkan fractal\_dimension\_mean hanya berkisar 0.04996(0,05)–0.09744(0,01).



Tanpa normalisasi, model bisa salah menganggap radius\_mean lebih penting hanya karena skalanya lebih besar. Meskipun keduanya bisa sama-sama relevan secara prediktif.



4. **Train-Test Split**



**Deskripsi**:



Data dibagi menjadi:



* **80% data latih (training)** untuk membangun dan melatih model.



* **20% data uji (testing)** untuk menguji generalisasi model.



**Alasan**:



Pembagian ini bertujuan untuk **mengevaluasi performa model pada data yang belum pernah dilihat sebelumnya**, guna menghindari overfitting.



Parameter:



* test\_size=0.2



* random\_state=42 (untuk reprodusibilitas hasil)



# **Modeling**



Dalam tahap ini, tiga algoritma machine learning digunakan untuk menyelesaikan masalah klasifikasi tumor ganas (malignant) dan jinak (benign). Masing-masing model diuji menggunakan data yang telah dipersiapkan dan dievaluasi menggunakan metrik akurasi, precision, recall, dan F1-score.



**Algoritma yang Digunakan**



1. **K-Nearest Neighbor (KNN)**



**Deskripsi**:



KNN adalah algoritma berbasis jarak yang mengklasifikasikan data berdasarkan mayoritas kelas dari tetangga terdekatnya.



**Hyperparameter yang dituning**:



* n\_neighbors = 5 (terbaik berdasarkan Grid Search)



**Kelebihan**:



* Mudah dipahami dan diimplementasikan.



* Cocok untuk dataset kecil atau sedang.



**Kekurangan**:



* Sensitif terhadap **skala fitur** (perlu normalisasi).



* Kurang efisien untuk dataset besar karena perlu menghitung jarak untuk setiap prediksi.



* Rentan terhadap **outlier**.



2. **Random Forest**



**Deskripsi**:



Random Forest adalah algoritma ensemble yang membangun banyak pohon keputusan dan menggabungkan hasilnya (voting mayoritas) untuk prediksi.



**Hyperparameter yang dituning**:



* n\_estimators = 100



* max\_depth = 5



**Kelebihan**:



* **Stabil terhadap overfitting**, terutama pada dataset yang memiliki banyak fitur.



* Dapat mengukur pentingnya fitur (feature importance).



* Performa baik secara umum tanpa banyak tuning.



**Kekurangan**:



Training lebih lambat dibanding model sederhana seperti KNN.



Kurang interpretatif dibandingkan pohon keputusan tunggal.



3. **AdaBoost**



**Deskripsi**:



AdaBoost adalah metode boosting yang menggabungkan beberapa model lemah (weak learners), biasanya decision stumps, untuk membuat model yang lebih kuat.



**Hyperparameter yang dituning**:



* n\_estimators = 50



* learning\_rate = 1.0



**Kelebihan**:



* Meningkatkan akurasi dengan menggabungkan banyak model lemah.



* Cenderung lebih akurat dibandingkan model tunggal jika disetel dengan baik.



**Kekurangan**:



* Sensitif terhadap data outlier dan noise.



* Memerlukan proses tuning untuk menghindari overfitting atau underfitting.



4. **Pemilihan Model Terbaik**



Berdasarkan hasil evaluasi pada data uji, **Random Forest** memberikan performa terbaik secara keseluruhan, terutama pada metrik **F1-Score**, yang menjadi fokus utama dalam masalah klasifikasi medis (karena menjaga keseimbangan antara precision dan recall sangat penting dalam konteks diagnosis penyakit).



**Alasan pemilihan**:



* **Akurasi tinggi (> 96%)** pada data uji.



* **F1-Score tertinggi** dibanding dua model lainnya.



* **Lebih stabil** terhadap variasi data dan tidak terlalu sensitif terhadap outlier.



* Memiliki kemampuan **feature importance**, yang membantu dalam interpretasi medis (misalnya fitur radius\_mean dan area\_mean terbukti paling berkontribusi).



**Hyperparameter Tuning (Grid Search)**

Parameter yang dituning:



| Model | Best Params |

| -------- | -------------------------------------- |

| KNN | `n_neighbors: 5` |

| RF | `n_estimators: 100, max_depth: 5` |

| AdaBoost | `n_estimators: 50, learning_rate: 1.0` |



# **Evaluation**



Evaluasi model dilakukan untuk mengukur seberapa baik performa model dalam mengklasifikasikan tumor sebagai ganas atau jinak. Karena ini adalah kasus klasifikasi medis, kita perlu lebih dari sekadar akurasi. Metrik seperti precision, recall, dan F1-Score menjadi sangat penting untuk memastikan prediksi yang tidak bias dan minim risiko kesalahan fatal, terutama false negative (ganas diprediksi jinak).



**Metrik Evaluasi**



1. **Accuracy**



Mengukur seberapa besar proporsi prediksi model yang benar secara keseluruhan.



**Rumus**:



Accuracy = (TP + TN) / (TP + TN + FP + FN)

= (40 + 70) / (40 + 70 + 1 + 3)

= 110 / 114 ≈ 96.5%



2. **Precision**



Mengukur seberapa banyak prediksi positif (ganas) yang benar-benar benar.



**Rumus**:



Precision = TP / (TP + FP)

= 40 / (40 + 1)

= 40 / 41 ≈ 0.9756 → **97.6%**



Penting dalam konteks di mana false positive perlu ditekan (agar tidak terlalu banyak pasien sehat yang salah didiagnosis kanker).



3. **Recall (Sensitivity)**



Mengukur seberapa banyak kasus kanker ganas yang berhasil dideteksi oleh model.



**Rumus**:



Recall = TP / (TP + FN)

= 40 / (40 + 3)

= 40 / 43 ≈ 0.9302 → **93.0%**



Penting dalam konteks medis agar tidak ada kasus kanker yang luput (false negative rendah).



4. **F1-Score**



Rata-rata harmonis dari precision dan recall. Cocok ketika kedua metrik ini penting untuk diseimbangkan.



**Rumus**:



**F1-Score**



F1-Score = 2 × Precision × Recall / Precision + Recall = 2 × 0.9756 × 0.9302 / 0.9756 + 0.9302 ≈ 0.9527 ( 95.3% )



5. **Confusion Matrix**



Menyediakan informasi detail tentang jumlah prediksi yang benar/salah untuk tiap kelas (ganas dan jinak).



Hasil Evaluasi Model Terbaik (Random Forest)

Setelah dilakukan training dan evaluasi, model Random Forest menghasilkan performa terbaik pada data uji sebagai berikut:



| Metrik | Nilai (%) |

| --------- | --------- |

| Accuracy | **96.5%** |

| Precision | **97.6%** |

| Recall | **93.0%** |

| F1-Score | **95.3%** |



* Confusion Matrix:



<pre> [[70 1]

[ 3 40]]</pre>



Artinya:



1. **\[70 1]** (Baris pertama, untuk kelas Benign):



* **70**: Jumlah sampel **Benign** (jinak) yang diprediksi dengan benar sebagai **Benign**.



* **1**: Jumlah sampel **Benign** (jinak) yang salah diprediksi sebagai **Malignant** (ganas).



2. **\[3 40]** (Baris kedua, untuk kelas **Malignant**):



* **3**: Jumlah sampel **Malignant** (ganas) yang salah diprediksi sebagai **Benign** (jinak).



* **40**: Jumlah sampel **Malignant** (ganas) yang diprediksi dengan benar sebagai **Malignant**.



**Evaluasi Performa Berdasarkan Confusion Matrix**



1. **True Positives** (TP): 40 (Malignant yang benar-benar diprediksi Malignant)



2. **True Negatives** (TN): 70 (Benign yang benar-benar diprediksi Benign)



3. **False Positives** (FP): 1 (Benign yang salah diprediksi sebagai Malignant)



4. **False Negatives** (FN): 3 (Malignant yang salah diprediksi sebagai Benign)



**Interpretasi**



1. **Accuracy**: Model memberikan 96.5% akurasi pada data uji.



2. **Precision** untuk kelas **Malignant** (1): Model memprediksi **97.6%** dari semua prediksi **Malignant** dengan benar.



3. **Recall** untuk kelas **Malignant** (1): Model dapat mendeteksi **93.0%** dari semua tumor ganas yang sebenarnya.



4. **F1-Score** untuk kelas **Malignant** (1): Kombinasi precision dan recall menghasilkan **95.3%**.



Nilai **akurat dan stabil** ini menunjukkan bahwa Random Forest merupakan model yang andal dan layak digunakan dalam konteks klasifikasi medis seperti ini.

