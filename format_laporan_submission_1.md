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
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

