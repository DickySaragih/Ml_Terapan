# Laporan Proyek Machine Learning - Nama Anda

## Domain Proyek

Program makan siang gratis yang dicanangkan pemerintah menjadi topik hangat di tengah masyarakat, memunculkan beragam penilaian. Sebagian masyarakat menyambutnya dengan antusias, menilai program ini sebagai langkah nyata untuk mengurangi angka stunting, meningkatkan konsentrasi belajar siswa, serta membantu keluarga yang kurang mampu dalam memenuhi kebutuhan gizi anak-anak mereka. Mereka melihat program ini sebagai bentuk perhatian negara terhadap masa depan generasi muda. Namun, di sisi lain, tidak sedikit yang menyampaikan kekhawatiran. Sebagian masyarakat mempertanyakan kesiapan pemerintah dalam menyediakan anggaran yang sangat besar, mengingat banyak sektor lain yang juga membutuhkan perhatian. Ada pula yang meragukan efektivitas distribusi makanan ke seluruh wilayah, terutama daerah terpencil, serta munculnya kekhawatiran akan potensi penyalahgunaan dana. Di tengah harapan dan kecemasan itu, masyarakat berharap program ini tidak hanya menjadi janji, melainkan benar-benar diimplementasikan dengan perencanaan yang matang, transparansi, dan pengawasan yang ketat agar tujuannya dapat tercapai dengan adil dan merata.

**Rubrik/Kriteria Tambahan (Opsional)**:
  Format Referensi: [Judul Referensi](https://link.springer.com/chapter/10.1007/978-3-031-58953-9_20) 

## Business Understanding
1. Import Library
Mengimpor library yang diperlukan untuk proses klasifikasi, preprocessing teks, dan visualisasi.

2. Load Dataset

3. Preprocessing Teks
a. Cleaning Text: Membersihkan teks dari noise seperti mention, hashtag, URL, angka, tanda baca, dan karakter khusus.
b. Case Folding: Mengubah teks menjadi huruf kecil.
c. Tokenizing Text: Memecah teks menjadi token-token (kata).
d. Filtering Text: Menghapus stopwords dan kata-kata yang tidak relevan dari token-token.
e. Stemming Text: Mengubah kata-kata menjadi bentuk dasarnya (stemming).
f. Slangwords Handling: Mengganti kata-kata gaul dengan kata-kata standar.
g. Menggabungkan token-token kembali menjadi kalimat.Memuat dataset dari URL yang disediakan.

4. Pelabelan Sentimen
Menggunakan lexicon Indonesia (positive.tsv dan negative.tsv) untuk memberikan label sentimen (positif atau negatif) pada setiap teks.
Menghitung skor polaritas untuk setiap kalimat.
Menetapkan label 'positive' jika score > 0 dan 'negative' jika score <= 0.

5. Eksplorasi Label
a. Visualisasi Distribusi Label: Menampilkan distribusi sentimen (positif dan negatif) dalam bentuk pie chart.
b. Word Cloud: Menampilkan word cloud dari seluruh teks untuk melihat kata-kata yang sering muncul.
c. Word Cloud Positif dan Negatif: Menampilkan word cloud terpisah untuk kata-kata yang muncul dalam teks dengan sentimen positif dan negatif.

6. Data Splitting dan Ekstraksi Fitur
a. Memisahkan data menjadi fitur (teks) dan label (sentimen).
b. Ekstraksi Fitur dengan TF-IDF: Mengubah teks menjadi vektor numerik menggunakan TF-IDF.
c. Data Splitting: Membagi data menjadi data training dan testing.

7. Training Model
Melatih model Logistic Regression menggunakan data training.

8. Evaluasi Model
a. Evaluasi pada data training: Menghitung akurasi dan classification report pada data training.
b. Evaluasi pada data testing: Menghitung akurasi, classification report dan confusion matrix pada data testing.

9. Prediksi Sentimen
Membuat fungsi predict_sentiment untuk memprediksi sentimen dari teks baru.
Fungsi ini melakukan preprocessing teks yang sama seperti pada data training dan menggunakan model yang telah dilatih untuk melakukan prediksi.

10. Contoh Penggunaan
Meminta input teks dari pengguna, memprediksi sentimen teks tersebut, dan menampilkan hasilnya.

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Bagaimana hasil pengujian Sentimen pada tanggapan komentar Negatif dan Positif pada postingan youtube Feri irwandi terkait program Makan siang geratis
- Apa yang menjadi solusi untuk memperoleh akurasi yang baik dalam memprediksi hasil proses klasifikasi yang dibuat?

### Goals

# - Jawaban pertanyaan 1
- Berdasarkan pie chart yang ditampilkan, program ini menunjukkan kemampuan dalam mengelola hasil komentar, dengan persentase 19,5% komentar positif dari pie chart komentar dikategorikan positif dan 80,5 komentar negatif dari pie chart dikategorikan negatif.  Hal ini menunjukkan bahwa program mampu memilah sentimen positif dan negatif dengan cukup baik, namun perlu diingat bahwa akurasi ini bergantung pada data yang digunakan dan metode yang diterapkan.  Evaluasi lebih lanjut, seperti confusion matrix dan  *classification report*,  dapat memberikan informasi lebih detail terkait performa program dalam mengklasifikasikan komentar negatif dan positif.

# - Jawaban pernyataan masalah 2
1. Kualitas Data Latih:
- Pastikan data latih berukuran cukup besar dan representatif terhadap data yang akan diprediksi.
- Bersihkan data latih dari noise dan kesalahan pelabelan.  Data yang salah label akan sangat memengaruhi model. Periksa kembali dan perbaiki label yang tidak sesuai.
- Gunakan data latih yang seimbang (balanced dataset) antara kelas positif dan negatif. Jika jumlah data positif dan negatif sangat berbeda, model mungkin bias ke kelas yang mayoritas.  Pertimbangkan teknik oversampling atau undersampling untuk menyeimbangkan dataset.

2. Preprocessing yang Lebih Baik:
- Eksplorasi teknik preprocessing tambahan. Contohnya:
- **Normalisasi:** Mengubah kata-kata menjadi bentuk baku.
- **Lematisasi:** Mengubah kata ke bentuk lemma (bentuk dasar kata).  Perhatikan perbedaan antara stemming dan lemmatization. Lemmatization biasanya lebih baik.
- **Penghapusan karakter khusus yang lebih komprehensif.**  Bersihkan teks dari emoticon, karakter aneh, atau gabungan huruf-angka yang tidak penting.
- **Penanganan angka:** Jika angka penting, pertimbangkan untuk mengubahnya menjadi kata (misalnya, "1000" menjadi "seribu"). Atau, jika angka tidak penting, hapuslah.
- **Menambahkan kata-kata slang yang belum ada di kamus slangwords.** Perbarui kamus slangwords Anda secara berkala.
- **Tokenizer yang lebih baik:** Pertimbangkan tokenizer yang dapat membedakan entitas dan frasa penting, misal spaCy atau Standford CoreNLP (perlu instalasi tambahan).

3. Lexicon yang Lebih Komprehensif:
- Gunakan lexicon sentimen Indonesia yang lebih lengkap dan akurat. Lexicon yang Anda gunakan mungkin masih terbatas.  Pertimbangkan untuk menggunakan lexicon yang lebih besar dan diperbarui.
- Anda dapat menambahkan lexicon sentimen custom yang spesifik untuk domain permasalahan Anda. Jika Anda memprediksi sentimen review film, tambahkan kata-kata yang relevan dengan film.
- Jika mungkin, gunakan kombinasi lexicon dan pendekatan deep learning.

4. Teknik Feature Engineering:
- Gunakan teknik feature engineering yang lebih canggih daripada hanya TF-IDF.  Anda bisa menggunakan word embeddings (Word2Vec, GloVe, FastText), atau model deep learning yang dapat menangkap konteks kalimat dengan lebih baik.
- Ekstraksi fitur tambahan seperti panjang kalimat, jumlah kata, atau fitur linguistik lainnya mungkin bermanfaat.

5. Algoritma yang Lebih Sesuai:
- Coba algoritma klasifikasi lain selain Logistic Regression.  Algoritma seperti Support Vector Machine (SVM), Naive Bayes, atau model deep learning (RNN, LSTM, transformers) mungkin berkinerja lebih baik.
- Lakukan tuning hyperparameter untuk algoritma yang Anda pilih.

6. Validasi silang (Cross-validation):
- Gunakan teknik validasi silang seperti k-fold cross-validation untuk evaluasi model yang lebih robust dan mengurangi kemungkinan overfitting.

7. Ensemble Methods:
- Gabungkan prediksi dari beberapa model (ensemble methods) untuk meningkatkan akurasi.


**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Statement” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

  ### Solution statements
    - Mengajukan 2 atau lebih solution statement. Misalnya, menggunakan dua atau lebih algoritma untuk mencapai solusi yang diinginkan atau melakukan improvement pada baseline model dengan hyperparameter tuning.
    - Solusi yang diberikan harus dapat terukur dengan metrik evaluasi.

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai data yang Anda gunakan dalam proyek. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

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

