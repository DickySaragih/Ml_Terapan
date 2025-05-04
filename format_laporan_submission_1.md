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
Dataset terdiri dari data nilai ujian siswa (matematika, membaca, menulis), informasi demografis (tingkat pendidikan orang tua, jenis kelamin, jenis makan siang), dan informasi tentang partisipasi dalam kursus persiapan ujian. Dataset ini memiliki 1000 baris dan 8 kolom. sebelum dilakukannya proses pemodelan data terlebih dahulu dibersihkan pada proses cleaning data agar beberapa nilai hilang yang ditangani dengan imputasi menggunakan nilai mean untuk kolom numerik.  Jumlah data duplikat ditemukan dan telah dihapus.
sumber atau tautan untuk mengunduh dataset. Contoh: [Data_siswa](https://github.com/DickySaragih/Ml_Terapan/blob/main/Data_siswa.csv).

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- 'gender': Jenis kelamin siswa (kategorikal)
- 'race/ethnicity': Ras atau etnis siswa (kategorikal)
- 'parental level of education': Tingkat pendidikan orang tua (kategorikal)
- 'lunch': Jenis makan siang (kategorikal)
- 'test preparation course': Partisipasi dalam kursus persiapan ujian (kategorikal)
- 'math score', 'reading score', 'writing score': Nilai ujian masing-masing mata pelajaran (numerik)
- 'nilai_akhir': Nilai akhir siswa (numerik) - variabel target

## Data Preparation
 tahapan penting yang dilakukan pada data preparation.
 1. Dilakukan *data cleaning* untuk menangani *missing values* pada data numerik dengan menggunakan *SimpleImputer* berstrategi *mean*.  Data duplikat juga diidentifikasi dan dihapus.  Selanjutnya, tipe data diperiksa dan diubah jika diperlukan. Tahapan ini bertujuan untuk memastikan kualitas data yang akan digunakan dalam pemodelan.
2. Dilakukan proses transformasi fitur.  Variabel kategorikal, seperti jenis kelamin, persiapan ujian, dan jenis makan siang, diubah menjadi representasi numerik menggunakan *label encoding*.  Kolom kategorikal lainnya yang memiliki lebih dari dua kategori unik, seperti ras/etnis dan tingkat pendidikan orang tua, diubah menggunakan *one-hot encoding* untuk menghindari penciptaan urutan semu antar kategori.
3. Ketiga, data dibagi menjadi fitur (X) dan target (y), dengan 'math score' sebagai variabel target yang akan diprediksi.  Data kemudian dibagi menjadi data latih (80%) dan data uji (20%) menggunakan fungsi `train_test_split`. Pembagian data ini penting untuk mengevaluasi kinerja model pada data yang belum pernah dilihat sebelumnya.  Seluruh tahapan ini bertujuan untuk mempersiapkan data agar sesuai dengan kebutuhan algoritma *machine learning* dan menghasilkan model yang akurat dan andal dalam memprediksi nilai matematika siswa.

## Modeling
Dua model regresi digunakan: Linear Regression dan Decision Tree Regressor.
1. Model Regresi Linier
- Model: LinearRegression() dari sklearn.linear_model
- Parameter: Tidak ada parameter yang diubah secara eksplisit. Model menggunakan pengaturan default.
- Proses: Model dilatih dengan data training (X_train, y_train) dan digunakan untuk memprediksi nilai akhir pada data testing (X_test).  Hasil prediksi disimpan dalam variabel y_pred_lr.
2. Model Decision Tree Regressor
- Model: DecisionTreeRegressor(max_depth=5, random_state=42) dari sklearn.tree
- Parameter:
- max_depth=5: Kedalaman maksimum pohon keputusan dibatasi hingga 5 level.  Ini bertujuan untuk mencegah overfitting, di mana model terlalu kompleks dan mempelajari noise pada data training sehingga kinerjanya buruk pada data testing.
- random_state=42: Digunakan untuk memastikan hasil yang konsisten setiap kali kode dijalankan. Menentukan random seed untuk algoritma Decision Tree.
- Proses: Model dilatih dengan data training dan digunakan untuk memprediksi nilai akhir pada data testing. Hasil prediksi disimpan dalam variabel y_pred_dt.

## Evaluation
Evaluasi data dilakukan secara komprehensif, mulai dari pembersihan data yang meliputi penanganan nilai hilang dan duplikat, hingga persiapan data dengan melakukan *encoding* untuk variabel kategorikal dan pembagian data latih-uji.  Analisis data eksploratif dilakukan untuk mengidentifikasi perbedaan skor berdasarkan gender, pengaruh etnisitas dan tingkat pendidikan orang tua terhadap skor matematika, dengan menggunakan uji-t dan ANOVA, serta visualisasi data.  Selanjutnya, dua model regresi, yaitu regresi linear dan *decision tree*, dibangun dan dievaluasi menggunakan metrik MAE, MSE, RMSE, dan R-squared untuk menentukan model terbaik. Terakhir, visualisasi korelasi antar fitur dengan skor matematika memberikan wawasan tambahan tentang faktor-faktor yang mempengaruhi prestasi belajar. Keseluruhan proses ini bertujuan untuk membangun model prediktif yang akurat dan memberikan pemahaman mendalam tentang faktor-faktor yang mempengaruhi skor matematika siswa.

- Adapaun saran agar hasil yang diperoleh lebih baik lagi seperti berikut:
1. Analisis lebih dalam: Jelajahi interaksi antar fitur demografis (misalnya, pengaruh tingkat pendidikan orang tua pada perbedaan gender).
2. Variabel lain: Pertimbangkan variabel lain seperti jam belajar, kebiasaan membaca, atau akses internet yang mungkin berpengaruh terhadap skor akademik.
3. Optimasi model: Lakukan optimasi hyperparameter pada model regresi yang dipilih, serta eksplorasi model lain (misalnya, Random Forest, SVM).
4. Cross-validation: Gunakan cross-validation untuk evaluasi model yang lebih robust.
5. Interpretasi hasil: Berikan interpretasi hasil yang lebih detail dan spesifik, menghubungkan temuan dengan strategi pembelajaran yang konkret.
6. Visualisasi: Pertimbangkan visualisasi tambahan untuk menunjukkan interaksi antar variabel dan hasil prediksi model.
7. Feature Importance:  Analisis feature importance dari model yang sudah dibuat untuk memahami fitur yang paling berpengaruh pada model.
8. Robustness Check: Cek kualitas model dengan menggunakan data baru atau melakukan simulasi perubahan pada data.


