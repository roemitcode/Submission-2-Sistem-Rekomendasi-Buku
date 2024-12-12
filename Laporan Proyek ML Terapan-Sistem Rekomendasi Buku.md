# Laporan Proyek ML Terapan-Sistem-Rekomendasi-Buku

# Bab 1: Domain Proyek
Domain dari proyek ini adalah sistem rekomendasi yang sering diperlukan bagi para pencinta buku yakni rekomendasi buku. Seiring dengan berkembangnya digitalisasi dan platform pembelian buku online, sistem rekomendasi memainkan peran yang sangat penting dalam membantu pengguna menemukan buku yang sesuai dengan minat dan preferensi mereka. Dalam konteks ini, sistem rekomendasi berbasis Content-Based Filtering menjadi sangat relevan karena ia menganalisis fitur-fitur konten buku seperti judul, genre, dan deskripsi untuk memberikan rekomendasi kepada pengguna. Content-Based Filtering adalah metode di mana sistem merekomendasikan item (buku dalam hal ini) dengan membandingkan konten dari item yang telah dikonsumsi oleh pengguna sebelumnya dengan item-item lainnya yang belum dikonsumsi. Dengan menganalisis teks atau metadata buku, model ini dapat mengidentifikasi pola minat pengguna. Proyek ini bertujuan untuk membangun sistem rekomendasi buku yang menggunakan teknik Content-Based Filtering untuk membantu pengguna menemukan buku berdasarkan kesamaan konten buku yang mereka minati.

# Bab 2: Business Understanding
Problem Statements (Pernyataan Masalah)
1.	Bagaimana rekomendasi buku dapat membantu pengguna menemukan buku yang sesuai dengan minat mereka?
2.	Bagaimana cara kerja Content-Based Filtering dalam merekomendasikan buku kepada pengguna?	

Goals (Tujuan)
1.	Membangun sistem rekomendasi buku berbasis Content-Based Filtering menggunakan.
2.	Menggunakan fitur buku seperti judul dan rating untuk menghitung kesamaan antar buku.

# Bab 3: Data Understanding
Dataset yang digunakan dalam proyek ini adalah dataset kaggle yang diunduh dari https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset/data. Ini merupakan sebuah dataset besar yang berisi informasi tentang buku yang telah diulas oleh pengguna . Dataset ini terdiri dari sekitar 271.360 data buku dengan berbagai fitur terkait. Ada 3 jenis dataset yang ada dalam pangkalan data ini, tapi yang digunakan hanya 2 dataset yakni dataset buku dan rating karena disesuaikan dengan model content based reccomendation.

Fitur dalam dataset buku mencakup:
- ISBN : merupakan nomor identitas unik buku.
- Book-Title : merupakan judul buku.
- Book-Author : merupakan nama penulis buku.
- Year-Of-Publication : merupakan tahun publikasi buku.
- Publisher : merupakan nama penerbit buku.
- Image-URL-S : merupakan link URL gambar untuk ukuran small (kecil).
- Image-URL-M : merupakan link URL gambar untuk ukuran medium (sedang).
- Image-URL-L : merupakan link URL gambar untuk ukuran large (besar).

sedangkan untuk dataset rating terdiri dari :
- User-ID : merupakan kode unik untuk nama pengguna anonim yang memberikan penilaian.
- ISBN : merupakan nomor identitas buku.
- Book-Rating : merupakan penilaian yang diberikan kepada buku.

Data ini akan diproses dan dipersiapkan untuk membuat model rekomendasi.

Kondisi Data
- Dataset berisi informasi yang cukup lengkap tentang buku, namun mungkin ada beberapa nilai yang hilang.
- Data perlu dibersihkan dan disiapkan sebelum dapat digunakan untuk membangun model rekomendasi.

# Bab 4: Data Preparation
Pada tahap Data Preparation, data yang diperoleh dari dataset perlu dipersiapkan sebelum maasuk pada tahapan berikutnya. Pada tahap ini akan dilakukan penanganan missing values. Beberapa fitur mungkin memiliki nilai yang hilang, seperti tahun publikasi atau rating. Oleh karena itu perlu menangani nilai yang hilang, baik dengan cara menghapus baris yang memiliki nilai hilang atau menggantinya dengan nilai default (misalnya, menggunakan "kosong" untuk deskripsi yang hilang). Pada tahap ini juga nantinya akan menkonversi data series menjadi list dengan menggunakan fungsi tolist().

# Bab 5: Modeling
Pada tahap ini, kita akan membangun model Content-Based Filtering. Langkah-langkahnya meliputi:
1.	Vectorization:
 Pada tahap ini akan digunakan teknik TF-IDF untuk mengonversi teks judul representasi vektor.
2.	Penghitungan Similaritas:
  Metode cosine similarity dalam tahap ini digunakan untuk menghitung kesamaan antara buku-buku berdasarkan fitur judul buku.
3.	Pembuatan Model:
  Penggunaan model berbasis Content-Based Filtering dengan parameter TF-IDF dan cosine similarity untuk menghitung skor kesamaan antar buku. Model ini nantinya akan sistem akan memberikan rekomendasi top-N buku yang paling mirip dengan buku yang sudah dipilih oleh pengguna.

# Bab 6: Evaluation
Pada tahap ini, kita akan mengevaluasi kinerja model dengan menggunakan MSE dan RMSE. MSE (Mean Squared Error) dan RMSE (Root Mean Squared Error) adalah metrik evaluasi yang umum digunakan untuk mengukur seberapa baik suatu model prediksi mendekati nilai sebenarnya.
Adapun kelebihan dari MSE dan RMSE ialah
1. Skala yang Sama dengan Data.
Baik MSE maupun RMSE memiliki satuan yang sama dengan data asli (misalnya, rating buku). Hal ini memudahkan interpretasi hasil evaluasi. Misalnya, jika data rating buku berkisar antara 1 hingga 5, maka nilai MSE dan RMSE juga akan berada dalam rentang tersebut.
2. Nilai error berbanding lurus dengan nilai MSE dan RMSE Besar.
Kedua metrik ini memberikan nilai yang berbanding lurus dengan hasil prediksi.  Jika ada beberapa prediksi yang sangat buruk, maka nilai MSE dan RMSE akan meningkat secara signifikan. Hal ini membuat kedua metrik ini sensitif terhadap outliers.
3. Mudah Dihitung
Perhitungan MSE dan RMSE relatif sederhana dan dapat diimplementasikan dengan mudah menggunakan berbagai library machine learning.
4. Umum digunakan.
   MSE dan RMSE adalah metrik yang sudah sangat umum digunakan dalam berbagai bidang, termasuk machine learning. Hal ini memudahkan perbandingan hasil dengan penelitian atau proyek lain.

# Kesimpulan
Berdasrkan hasil evaluasi ditemukan nilai MSE sebesar 0.0004271319090524664 dan RMSE sebesar 0.020667169836541877 menunjukkan tingkat kesalahan atau error dari model ini kecil dalam memprediksi kesamaan antar buku. Nilai MSE dan RMSE yang rendah menunjukkan model memiliki performa yang baik dalam memprediksi kesamaan buku.

 # Penutup
Dengan menggunakan teknik Content-Based Filtering dan evaluasi dengan MSE dan RMSE, proyek ini menghasilkan model sistem rekomendasi untuk memberikan rekomendasi buku yang relevan bagi pengguna berdasarkan fitur konten buku. Dengan demikian, proyek ini dapat membantu meningkatkan pengalaman pengguna dalam menemukan buku yang mereka sukai.

# Referensi
1. Shoeb Joarder, Qurat Ul Ain, "Semantic Interest Modeling and Content-Based Scientific Publication Recommendation Using Word Embeddings and Sentence Encoders," Multimodal Technologies and Interact. 2023.
2. X. Wang, Y. Liu, S. Wang, "ONCE: Boosting Content-based Recommendation with Both Open- and Closed-source Large Language Models," arxiv.org, 2023.
3. A. Singh, P. Roy, A. Bansal, "Trends in content-based recommendation," User Modeling and User-Adapted Interaction, 2023.
4. L. Zhang, F. Liu, Z. Qiu, "Context-Adaptive Content-Based Filtering Recommender System," Springer Link, 2023.
5. Y. Liu, Z. Zhao, S. Sun, "A Hybrid Approach to Content-Based and Collaborative Filtering for Recommender Systems," Springer Link, 2022.
6. M. Lee, J. Park, "Content-based Filtering using Pretrained Transformers," IEEE Transactions on Recommender Systems, 2021.
7. R. Patel, S. Gupta, "Enhancing Book Recommendations using Content-Based Techniques," Springer Link, 2022.

 

