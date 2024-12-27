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

Tahapan dalam data preparation adalah sebagai berikut
1.	Data Preprocessing (Menggabungkan Data Buku dan Ratings) :
   Pada tahap ini data dari buku dan data ratings digabungkan menjadi satu dataset terpadu untuk mempermudah analisis dan pemrosesan selanjutnya.
2.	Analisis Missing Value :
Tahapan ini memeriksa apakah ada data yang hilang (missing values) dalam dataset, kemudian menangani nilai-nilai tersebut dengan metode tertentu seperti menghapus baris/kolom atau mengganti nilai yang hilang dengan rata-rata, median, atau nilai lain.
3.	Mengurutkan Data :
Di tahap ini dataset diurutkan berdasarkan satu atau lebih kolom (misalnya, ID pengguna atau judul buku) untuk memastikan keteraturan dan mempermudah akses data di langkah selanjutnya.
4.	Identifikasi Data Ganda :
Sebelum memprosees data lebih lajut, terlebih dahulu mendeteksi baris data yang duplikat dalam dataset untuk menghindari bias dalam analisis. Data ganda biasanya dihapus agar dataset tetap bersih.
5.	Konversi List :
Pada tahap ini, dilkukan perubahan data dari format tabular atau lain ke format daftar (list) jika diperlukan, misalnya untuk input ke algoritma atau fungsi tertentu yang membutuhkan format ini.
6.	Pembuatan Dictionary :
Tahapan ini membuat struktur dictionary (kamus) dari dataset untuk menyimpan data dalam format pasangan kunci-nilai. Misalnya, judul buku sebagai kunci dan informasi terkait sebagai nilainya.
7.	TF-IDF Vectorizer :
Pada tahap ini teks akan diubah menjadi representasi numerik menggunakan TF-IDF (Term Frequency-Inverse Document Frequency) untuk analisis lebih lanjut. Ini digunakan untuk merepresentasikan hubungan antara kata-kata dalam dokumen dan membantu dalam tugas seperti pencocokan teks atau pemrosesan bahasa alami (NLP).
	Tahapan ini dilakukan secara berurutan untuk memastikan data siap digunakan dalam model machine learning.


# Bab 5: Modeling
Pada tahap ini, kita akan membangun model Content-Based Filtering dengan menggunakan teknik cosine similarity.  Adapun tahapan pembuatan model meliputi:
1.	Pengolahan Data Awal :
Dataset disiapkan untuk merepresentasikan buku dalam bentuk matriks, di mana setiap baris merepresentasikan sebuah buku, dan setiap kolom adalah fitur yang mana dalam proyek ini adalah rating.
2.	Perhitungan Cosine Similarity :
Pada tahap ini Cosine similarity mengukur kesamaan antara dua vektor 
3.	Membangun Model Rekomendasi :
Setelah cosine similarity dihitung untuk setiap pasangan buku, model menghasilkan matriks kesamaan. Berdasarkan matriks ini, untuk setiap buku, dapat ditentukan buku lain dengan tingkat kesamaan tertinggi. Model ini nantinya akan sistem akan memberikan rekomendasi top-N buku yang paling mirip dengan buku yang sudah dipilih oleh pengguna.

Dalam model ini, parameter yang digunakan adalah : 
1. Cosine Similarity Matrix: Mengukur kesamaan antara fitur buku.
2. TF-IDF Matrix: Merepresentasikan fitur buku berbasis teks dalam format numerik.
3. K: Jumlah buku rekomendasi yang ingin dihasilkan (k=5 sebagai default).



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

Berdasrkan hasil matrik evaluasi ditemukan nilai MSE sebesar 0.0004271319090524664 dan RMSE sebesar 0.020667169836541877 menunjukkan tingkat kesalahan atau error dari model ini kecil dalam memprediksi kesamaan antar buku. Nilai MSE dan RMSE yang rendah menunjukkan model memiliki performa yang baik dalam memprediksi kesamaan buku.

Model yang telah dibuat ini memiliki tentunya berkesesuaian denngan Business Understanding yakni agar model ini dapat : 
1.	Bersifat Personalisasi: Sistem rekomendasi menganalisis preferensi atau riwayat pengguna berdasarkan buku yang pernah dibaca dan rating nya untuk menyarankan buku yang relevan.
2.	Meningkatkan Efisiensi: Dengan menyaring jutaan buku yang tersedia, sistem ini memudahkan pengguna menemukan buku yang sesuai tanpa harus mencarinya sendiri.
3.	Membantu Eksplorasi: Selain memberikan saran dari genre favorit pengguna, rekomendasi juga dapat memperkenalkan buku baru yang memiliki kesamaan tertentu dengan preferensi mereka, membantu memperluas cakrawala bacaan.
4.	Memberikan Pengalaman Pengguna yang Lebih Baik: Sistem ini meningkatkan kepuasan pengguna dengan menyediakan saran yang tepat dan relevan.

Model yang telah dibuat ini juga dapat memenuhhi tujuan :
1.	Membangun Sistem Rekomendasi Buku Berbasis Content-Based Filtering : 
Sistem ini dirancang untuk merekomendasikan buku kepada pengguna berdasarkan analisis kesamaan antara fitur buku, seperti judul dan rating.
2.	Menggunakan Fitur Buku (Judul dan Rating) untuk Menghitung Kesamaan Antar Buku
- Judul: Menggunakan teknik pemrosesan teks, seperti TF-IDF, untuk menganalisis kemiripan antara kata-kata dalam judul.
- Rating: Mempertimbangkan pola rating untuk memberikan bobot tambahan pada buku yang memiliki penilaian serupa atau disukai oleh pengguna serupa.
Dengan memanfaatkan kedua fitur ini, sistem mampu memberikan rekomendasi yang lebih akurat dan relevan bagi pengguna.


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

 

