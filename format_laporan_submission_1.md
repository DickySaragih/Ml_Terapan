# Laporan Proyek Machine Learning - Dicky Candid Saragih

## Domain Proyek
Proyek ini berfokus pada penerapan analitik prediktif dalam sektor pendidikan untuk memahami bagaimana faktor-faktor demografis memengaruhi performa akademik siswa. Data yang dianalisis mencakup informasi seperti jenis kelamin, latar belakang etnis, tingkat pendidikan orang tua, serta hasil nilai ujian pada mata pelajaran matematika, membaca, dan menulis.
Melalui pendekatan ini, proyek bertujuan mengidentifikasi kesenjangan hasil belajar yang mungkin timbul akibat perbedaan demografis. Misalnya, apakah terdapat ketimpangan performa antara siswa laki-laki dan perempuan, kelompok etnis tertentu, atau siswa dengan latar belakang keluarga berpendidikan rendah. Dengan memahami pola-pola ini, model prediktif dapat dikembangkan untuk memproyeksikan performa akademik dan mendukung kebijakan pendidikan yang lebih inklusif dan berbasis data.

## Business Understanding
Dalam sistem pendidikan, kesenjangan hasil belajar antar siswa seringkali disebabkan oleh faktor-faktor yang tidak sepenuhnya akademik, melainkan juga berasal dari latar belakang demografis siswa itu sendiri. Tanpa pemahaman mendalam terhadap pengaruh variabel seperti gender, etnis, dan tingkat pendidikan orang tua, institusi pendidikan mungkin kesulitan dalam menerapkan strategi pembelajaran yang efektif dan adil.
Proyek ini bertujuan untuk memberikan pemahaman berbasis data tentang bagaimana karakteristik demografis siswa berkorelasi dengan pencapaian akademik mereka. Dengan informasi ini, pengambil kebijakan pendidikan, guru, dan manajemen sekolah dapat mengambil tindakan yang lebih tepat sasaran — baik untuk intervensi, pengembangan kurikulum, maupun perencanaan program dukungan belajar.

### Problem Statements
1. Apakah terdapat perbedaan signifikan dalam skor matematika, membaca, dan menulis berdasarkan jenis kelamin siswa?
2. Bagaimana pengaruh latar belakang etnis siswa terhadap performa akademik mereka?
3.Seberapa besar pengaruh tingkat pendidikan orang tua terhadap capaian nilai akademik siswa?

### Goals
1. Mengidentifikasi fitur demografis yang paling memengaruhi skor akademik siswa.
2. Menyediakan insight berbasis data terkait kesenjangan performa akademik berdasarkan latar belakang siswa.
3. Membangun model prediktif untuk memperkirakan nilai siswa berdasarkan data demografis dan hasil ujian lainnya.
4. Mendukung pengembangan strategi pembelajaran yang lebih inklusif dan responsif terhadap kebutuhan siswa yang beragam.

### Solution statements
1. Melakukan eksplorasi dan visualisasi data untuk menemukan pola dan hubungan antara variabel demografis dan skor ujian siswa.
2. Menggunakan teknik machine learning, seperti regresi linier atau pohon keputusan, untuk membangun model prediktif terhadap nilai akademik siswa.
3. Menerapkan teknik evaluasi model seperti MAE, RMSE, dan R² untuk menilai akurasi model yang dibangun.
4. Memberikan rekomendasi kebijakan berbasis hasil analisis untuk meningkatkan keadilan dan efektivitas dalam pembelajaran siswa.

## Data Understanding
Dataset terdiri dari data nilai ujian siswa (matematika, membaca, menulis), informasi demografis (tingkat pendidikan orang tua, jenis kelamin, jenis makan siang), dan informasi tentang partisipasi dalam kursus persiapan ujian. Dataset ini memiliki:
- 1000 baris dan 8 kolom.
- data tidak memiliki duplikat
- Tautan dataset [Data_siswa](https://github.com/DickySaragih/Ml_Terapan/blob/main/Data_siswa.csv).
sebelum dilakukannya proses pemodelan data terlebih dahulu dibersihkan pada proses cleaning data agar beberapa nilai hilang yang ditangani dengan imputasi menggunakan nilai mean untuk kolom numerik.  Jumlah data duplikat ditemukan dan telah dihapus.
sumber atau tautan untuk mengunduh dataset.

### Variabel-variabel pada Data_siswa dataset adalah sebagai berikut:
- 'gender': Jenis kelamin siswa (kategorikal)
- 'race/ethnicity': Ras atau etnis siswa (kategorikal)
- 'parental level of education': Tingkat pendidikan orang tua (kategorikal)
- 'lunch': Jenis makan siang (kategorikal)
- 'test preparation course': Partisipasi dalam kursus persiapan ujian (kategorikal)
- 'math score', 'reading score', 'writing score': Nilai ujian masing-masing mata pelajaran (numerik)
- 'Reading score' : skor nilai membaca
- 'Writing score' : skor nilai menulis
- 'nilai_akhir': Nilai akhir siswa (numerik) - variabel target


## Data Preparation
 tahapan penting yang dilakukan pada data preparation.
1. Dilakukan *data cleaning* untuk menangani *missing values* pada data numerik dengan menggunakan *SimpleImputer* berstrategi *mean*.  Data duplikat juga diidentifikasi dan dihapus.  Selanjutnya, tipe data diperiksa dan diubah jika diperlukan. Tahapan ini bertujuan untuk memastikan kualitas data yang akan digunakan dalam pemodelan.
2. Dilakukan proses transformasi fitur.  Variabel kategorikal, seperti jenis kelamin, persiapan ujian, dan jenis makan siang, diubah menjadi representasi numerik menggunakan *label encoding*.  Kolom kategorikal lainnya yang memiliki lebih dari dua kategori unik, seperti ras/etnis dan tingkat pendidikan orang tua, diubah menggunakan *one-hot encoding* untuk menghindari penciptaan urutan semu antar kategori.
3. Ketiga, data dibagi menjadi fitur (X) dan target (y), dengan 'math score' sebagai variabel target yang akan diprediksi.  Data kemudian dibagi menjadi data latih (80%) dan data uji (20%) menggunakan fungsi `train_test_split`. Pembagian data ini penting untuk mengevaluasi kinerja model pada data yang belum pernah dilihat sebelumnya.  Seluruh tahapan ini bertujuan untuk mempersiapkan data agar sesuai dengan kebutuhan algoritma *machine learning* dan menghasilkan model yang akurat dan andal dalam memprediksi nilai matematika siswa.

## Modeling
Dua model regresi digunakan: Linear Regression dan Decision Tree Regressor.
**1. model 1: Linear Regression**
Pembahasan cara kerja.
Regresi linear adalah model statistik yang digunakan untuk memodelkan hubungan linear antara satu variabel dependen (variabel target) dan satu atau lebih variabel independen (variabel prediktor).  Model ini bekerja dengan mencari garis lurus (atau bidang dalam kasus multivariabel) yang paling tepat merepresentasikan hubungan antara variabel-variabel tersebut.  Garis ini ditentukan oleh koefisien regresi dan *intercept*. Koefisien regresi menunjukkan pengaruh perubahan satu unit variabel independen terhadap variabel dependen, sementara *intercept* menunjukkan nilai variabel dependen ketika semua variabel independen bernilai nol.  Dalam implementasi kode, model dilatih dengan data latih (X_train, y_train) untuk menemukan koefisien dan *intercept* yang optimal yang meminimalkan kesalahan prediksi pada data latih.  Kemudian, model tersebut digunakan untuk memprediksi nilai variabel dependen pada data uji (X_test).

**Pembahasan parameter.**
Model `LinearRegression` di scikit-learn memiliki beberapa parameter, meskipun dalam kode yang diberikan tidak ada parameter yang diubah dari nilai defaultnya. Beberapa parameter penting antara lain:
* `fit_intercept`: Parameter boolean yang menentukan apakah model harus memperkirakan intercept atau tidak. Nilai defaultnya adalah `True`.
* `normalize`: Parameter boolean yang menentukan apakah variabel independen akan dinormalisasi sebelum pemodelan. Nilai defaultnya adalah `False`.  Sebaiknya gunakan `StandardScaler` untuk normalisasi.
* `copy_X`: Parameter boolean yang menentukan apakah variabel independen akan disalin sebelum pemodelan. Nilai defaultnya adalah `True`.
* `n_jobs`: Parameter integer yang menentukan jumlah prosesor yang akan digunakan dalam pemodelan. Nilai defaultnya adalah `None`.

**Kelebihan/kekurangan**
Kelebihan:
* Sederhana dan mudah diinterpretasi.
* Menghasilkan model yang mudah dipahami dan dijelaskan.
* Cepat dalam pelatihan dan prediksi.

Kekurangan:
* Mengasumsikan hubungan linear antara variabel, yang mungkin tidak selalu berlaku untuk semua data.
* Sensitif terhadap *outlier*.
* Kinerja model dapat terbatas jika terdapat hubungan non-linear antara variabel.

**2. model 2 : Decision Tree Regressor**
Pembahasan cara kerja.
Decision Tree Regressor adalah model yang membangun pohon keputusan untuk memprediksi nilai numerik.  Pohon keputusan terdiri dari serangkaian node, cabang, dan daun. Node internal merepresentasikan fitur (variabel independen) yang digunakan untuk membuat keputusan, cabang merepresentasikan nilai-nilai yang mungkin dari fitur tersebut, dan daun merepresentasikan nilai prediksi untuk variabel dependen. Model ini bekerja dengan merekursif membagi dataset berdasarkan fitur yang paling informatif (fitur yang meminimalkan ketidakmurnian), sehingga membentuk struktur pohon yang menyerupai struktur keputusan. Pada proses prediksi, data baru mengikuti jalur pohon keputusan berdasarkan nilai fitur-fiturnya hingga mencapai daun, dan nilai di daun tersebut merupakan nilai prediksi yang dihasilkan.

**Pembahasan parameter.**
* `random_state`:  Digunakan untuk mengontrol keacakan pada saat pembangunan pohon keputusan. Parameter ini penting untuk memastikan bahwa model dapat direproduksi. 
Beberapa parameter lainnya yang dapat diubah antara lain:
* `max_depth`: Batasan kedalaman maksimum dari pohon. 
* `min_samples_split`: Jumlah minimum sampel yang dibutuhkan untuk membagi node internal.
* `min_samples_leaf`: Jumlah minimum sampel yang dibutuhkan untuk berada di sebuah daun.
* `max_features`: Jumlah fitur yang dipertimbangkan untuk setiap pemisahan.

**Kelebihan/kekurangan**
Kelebihan:
* Mudah diinterpretasi.
* Dapat menangani variabel kategorikal dan numerik.
* Relatif robust terhadap *outlier*.
* Tidak membutuhkan normalisasi data.

Kekurangan:
* Rentan terhadap *overfitting*, terutama pada pohon yang dalam.
* Performa dapat tidak stabil jika data berubah.
* Dapat menghasilkan pohon yang kompleks dan sulit diinterpretasi jika kedalamannya terlalu besar.

## Evaluation
**Matrik Evaluasi**
Pada proyek prediksi nilai matematika siswa ini, matriks evaluasi berperan krusial dalam mengukur performa model *machine learning*.  Meskipun dalam kode yang diberikan tidak secara eksplisit didefinisikan matriks evaluasi dalam bentuk tabel,  metrik evaluasi seperti *Mean Absolute Error* (MAE), *Mean Squared Error* (MSE), *Root Mean Squared Error* (RMSE), dan *R-squared* telah digunakan untuk mengevaluasi model *Linear Regression* dan *Decision Tree Regressor*.  Metrik-metrik ini secara implisit membentuk dasar untuk matriks evaluasi.  Setiap metrik tersebut mengukur aspek berbeda dari akurasi dan ketepatan model. MAE menunjukkan kesalahan absolut rata-rata, MSE dan RMSE mengukur kesalahan kuadrat rata-rata (RMSE dalam satuan variabel target), sementara R-squared mengindikasikan proporsi variabilitas data yang dijelaskan oleh model.

**Evaluasi Proses Analisis**
Proses analisis data eksploratif (EDA) telah dilakukan secara sistematis untuk menjawab pernyataan masalah utama dalam proyek ini, yaitu:
1. Apakah terdapat perbedaan signifikan dalam skor matematika, membaca, dan menulis berdasarkan jenis kelamin siswa?
2. Bagaimana pengaruh latar belakang etnis siswa terhadap performa akademik mereka?
3.Seberapa besar pengaruh tingkat pendidikan orang tua terhadap capaian nilai akademik siswa?
Melalui penerapan uji statistik dan visualisasi data, ketiga pertanyaan tersebut telah berhasil dijawab secara menyeluruh. Teknik yang digunakan meliputi:
Independent t-test untuk menguji perbedaan skor akademik antara gender.
One-Way ANOVA untuk menguji perbedaan skor berdasarkan etnis dan tingkat pendidikan orang tua.
Boxplot dan Violin Plot untuk memperkuat interpretasi dan pemahaman hasil statistik.

**Pencapaian dalam Goals**
Tujuan utama dari analisis ini adalah:
Mengidentifikasi faktor demografis yang memengaruhi performa akademik siswa.
Menyediakan dasar bagi pengambilan kebijakan pendidikan yang lebih inklusif dan berbasis data.
Hasil analisis menunjukkan bahwa:
1. Terdapat perbedaan signifikan dalam skor akademik antara gender tertentu pada mata pelajaran tertentu.
2. Etnisitas menunjukkan pengaruh signifikan terhadap skor matematika, yang mengindikasikan adanya perbedaan capaian akademik antar kelompok etnis.
3. Tingkat pendidikan orang tua juga memiliki korelasi terhadap performa anak, yang dapat dimanfaatkan untuk merancang strategi dukungan akademik yang lebih tepat sasaran.
Dengan demikian, semua tujuan penelitian telah tercapai secara menyeluruh dan terukur.

**Dampak Solusi yang Diberikan**
Solusi dan insight yang diperoleh dari hasil analisis ini berpotensi memberikan dampak yang signifikan, di antaranya:
1. Memberikan evidence-based insight bagi institusi pendidikan dalam menyusun program pembelajaran atau intervensi akademik.
2. Menyoroti pentingnya mempertimbangkan faktor demografis seperti gender, etnis, dan latar belakang orang tua dalam menyusun kebijakan pendidikan yang adil dan merata.
3. Membantu pengambil keputusan dalam pendidikan untuk merancang kebijakan yang lebih inklusif, misalnya dengan menyediakan dukungan belajar tambahan untuk kelompok yang lebih rentan secara akademik.

Solusi yang dihasilkan tidak hanya menjawab permasalahan secara akademik, namun juga relevan dalam konteks sosial dan kebijakan pendidikan.

**Kesimpulan**
Berdasarkan evaluasi yang telah dilakukan, dapat disimpulkan bahwa proses analisis telah dilaksanakan dengan baik, sesuai dengan pernyataan masalah dan tujuan penelitian. Analisis yang dilakukan tidak hanya bersifat deskriptif, tetapi juga menghasilkan temuan yang dapat dijadikan dasar pertimbangan strategis dalam peningkatan kualitas dan keadilan pendidikan. Proyek ini berhasil menunjukkan bahwa pendekatan analitik berbasis data dapat memberikan kontribusi nyata dalam menyusun kebijakan pendidikan yang lebih inklusif dan berdampak.
