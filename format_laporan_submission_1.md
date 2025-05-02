# Laporan Proyek Machine Learning - Dicky Candid Saragih

## Domain Proyek
Pada proses ini pengembangan model prediktif untuk memperkirakan nilai akhir siswa.  Model ini memanfaatkan data berupa nilai ujian (matematika, membaca, menulis), informasi demografis (tingkat pendidikan orang tua, jenis kelamin), dan faktor lain seperti jenis makan siang serta partisipasi dalam kursus persiapan ujian.  Tujuan utama adalah mengidentifikasi siswa yang memerlukan bantuan tambahan dan memahami faktor-faktor yang memengaruhi prestasi akademik.  Proses ini melibatkan beberapa tahapan, mulai dari persiapan data yang mencakup transformasi fitur kategorikal (one-hot encoding dan TF-IDF untuk data teks), pembagian data latih dan uji, hingga pembangunan dan evaluasi model regresi (regresi linier dan decision tree).  Evaluasi model menggunakan metrik R-squared dan RMSE untuk mengukur akurasi prediksi.  Visualisasi data berupa heatmap korelasi digunakan untuk memahami hubungan antar variabel dan kontribusi masing-masing terhadap nilai akhir siswa.

## Business Understanding

### Problem Statements
1. Bagaimana memprediksi nilai akhir siswa secara akurat berdasarkan faktor-faktor seperti nilai ujian, latar belakang demografis, dan partisipasi dalam program persiapan ujian?
2. Faktor-faktor apa yang paling berpengaruh terhadap nilai akhir siswa?
3. Bagaimana model prediksi ini dapat digunakan untuk mengidentifikasi siswa yang memerlukan intervensi atau bantuan tambahan?

### Goals
1. Mengembangkan model prediktif yang dapat memperkirakan nilai akhir siswa dengan akurasi yang tinggi.
2. Mengidentifikasi faktor-faktor kunci yang berkontribusi pada nilai akhir siswa.
3. Memberikan rekomendasi untuk intervensi atau dukungan kepada siswa yang berisiko rendah dalam prestasi akademik.

### Solution statements
1Mengembangkan model machine learning regresi (Linear Regression dan Decision Tree Regressor) untuk memprediksi nilai akhir siswa berdasarkan data demografis, nilai ujian, dan partisipasi dalam kursus persiapan ujian.  Model ini akan dievaluasi menggunakan metrik R-squared dan RMSE.  Hasilnya akan digunakan untuk mengidentifikasi siswa yang memerlukan perhatian khusus dan untuk memahami faktor-faktor yang paling berpengaruh terhadap nilai akademik.

## Data Understanding
Dataset terdiri dari data nilai ujian siswa (matematika, membaca, menulis), informasi demografis (tingkat pendidikan orang tua, jenis kelamin, jenis makan siang), dan informasi tentang partisipasi dalam kursus persiapan ujian.  Variabel target adalah 'nilai_akhir', yang dihitung sebagai rata-rata dari tiga nilai ujian.
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
1. Membuat kolom 'nilai_akhir' sebagai rata-rata dari 'math score', 'reading score', dan 'writing score'.
2. Mengubah kolom 'parental level of education' menjadi representasi numerik menggunakan TF-IDF.
3. Melakukan one-hot encoding untuk variabel kategorikal lainnya.
4. Membagi dataset menjadi data training dan data testing.

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
1. Model dievaluasi menggunakan dua metrik utama: R-squared (R2) dan Root Mean Squared Error (RMSE).
R-squared menunjukkan proporsi variabilitas dalam variabel dependen (nilai akhir) yang dijelaskan oleh model. Nilai R2 yang mendekati 1 mengindikasikan bahwa model mampu menjelaskan sebagian besar variabilitas data, sedangkan nilai yang mendekati 0 menunjukkan bahwa model kurang baik dalam menjelaskan variabilitas data.
RMSE mengukur rata-rata perbedaan antara nilai prediksi dan nilai sebenarnya. Nilai RMSE yang rendah menunjukkan bahwa model menghasilkan prediksi yang akurat, sedangkan nilai RMSE yang tinggi mengindikasikan bahwa model memiliki tingkat kesalahan prediksi yang besar.

2. Berdasarkan hasil evaluasi model yang telah dilakukan, diperoleh bahwa model Regresi Linier dan Decision Tree Regressor menunjukkan performa prediksi yang sangat baik dalam memperkirakan nilai akhir siswa. Model Regresi Linier menghasilkan nilai R² sebesar 1.0, yang berarti model ini mampu menjelaskan 100% variabilitas dari data nilai akhir siswa. Selain itu, nilai Root Mean Squared Error (RMSE) yang sangat kecil, yaitu 1.7735568706636565e-14, mengindikasikan bahwa rata-rata kesalahan prediksi model hampir tidak ada. Hal ini menunjukkan bahwa model sangat akurat dalam memetakan hubungan antara fitur dan nilai akhir, meskipun kondisi ini juga bisa mengindikasikan overfitting terhadap data yang digunakan. Sementara itu, model Decision Tree Regressor juga menunjukkan performa yang sangat baik dengan nilai R² sebesar 0.9677026312392458 dan RMSE sebesar 2.631249903298834. Artinya, model ini mampu menjelaskan sekitar 96.77% variabilitas dalam nilai akhir siswa, dengan rata-rata kesalahan prediksi sekitar 2.63 poin. Meskipun tidak seakurat regresi linier, model ini memberikan hasil yang lebih realistis dan mungkin lebih andal untuk data baru yang lebih beragam.
Secara keseluruhan, kedua model menunjukkan bahwa fitur-fitur yang digunakan dalam dataset memiliki hubungan yang kuat dengan nilai akhir siswa. Namun, model regresi linier memberikan hasil prediksi yang lebih presisi pada data ini. Untuk meningkatkan keandalan dan generalisasi model, disarankan dilakukan evaluasi lebih lanjut dengan data uji tambahan atau metode validasi silang, serta identifikasi faktor-faktor yang paling signifikan melalui analisis fitur lanjutan.
