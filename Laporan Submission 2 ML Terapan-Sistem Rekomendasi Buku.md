# Laporan Proyek ML Terapan-Sistem-Rekomendasi-Buku

# Bab 1: Domain Proyek
Domain dari proyek ini adalah sistem rekomendasi yang sering diperlukan bagi para pencinta buku yakni rekomendasi buku. Seiring dengan berkembangnya digitalisasi dan platform pembelian buku online, sistem rekomendasi memainkan peran yang sangat penting dalam membantu pengguna menemukan buku yang sesuai dengan minat dan preferensi mereka. Dalam konteks ini, sistem rekomendasi berbasis Content-Based Filtering menjadi sangat relevan karena ia menganalisis fitur-fitur konten buku seperti judul, genre, dan deskripsi untuk memberikan rekomendasi kepada pengguna. Content-Based Filtering adalah metode di mana sistem merekomendasikan item (buku dalam hal ini) dengan membandingkan konten dari item yang telah dikonsumsi oleh pengguna sebelumnya dengan item-item lainnya yang belum dikonsumsi. Dengan menganalisis teks atau metadata buku, model ini dapat mengidentifikasi pola minat pengguna. Proyek ini bertujuan untuk membangun sistem rekomendasi buku yang menggunakan teknik Content-Based Filtering untuk membantu pengguna menemukan buku berdasarkan kesamaan konten buku yang mereka minati.

#Bab 2: Business Understanding
Problem Statements (Pernyataan Masalah)
1.	Bagaimana rekomendasi buku dapat membantu pengguna menemukan buku yang sesuai dengan minat mereka?
2.	Bagaimana cara kerja Content-Based Filtering dalam merekomendasikan buku kepada pengguna?	

Goals (Tujuan)
1.	Membangun sistem rekomendasi buku berbasis Content-Based Filtering menggunakan dataset Goodbooks-10k.
2.	Menggunakan berbagai fitur buku seperti judul, genre, dan deskripsi untuk menghitung kesamaan antar buku.

# Bab 3: Data Understanding
Dataset yang digunakan dalam proyek ini adalah Goodbooks-10k yang diounduh dari https://www.kaggle.com/datasets/zygmunt/goodbooks-10k  sebuah dataset besar yang berisi informasi tentang buku yang telah diulas oleh pengguna di platform Goodreads. Dataset ini terdiri dari sekitar 10.000 buku dengan berbagai fitur terkait.
Fitur dalam dataset ini mencakup:
- book_id: ID unik untuk setiap buku.
- title: Judul buku.
- author: Penulis buku.
- year: Tahun rilis buku.
- genre: Genre atau kategori buku (misalnya, fiksi, non-fiksi, misteri, dll.).
- description: Deskripsi singkat tentang buku.
- average_rating: Rating rata-rata buku dari pengguna.
- num_ratings: Jumlah rating yang diberikan oleh pengguna.
	Dari dataset ini, kita akan fokus pada fitur title, genre, dan description untuk membangun model rekomendasi berbasis konten. Data ini akan diproses dan dipersiapkan untuk membuat model rekomendasi.

Kondisi Data
- Dataset berisi informasi yang cukup lengkap tentang buku, namun mungkin ada beberapa nilai yang hilang, seperti yang ada di kolom deskripsi atau rating.
- Data perlu dibersihkan dan disiapkan sebelum dapat digunakan untuk membangun model rekomendasi.

# Bab 4: Data Preparation
Pada tahap Data Preparation, data yang diperoleh dari Goodbooks-10k perlu dipersiapkan dengan beberapa langkah berikut:
1.	Penanganan Data yang Hilang: 
  Beberapa fitur mungkin memiliki nilai yang hilang, seperti deskripsi atau rating. Oleh karena itu, kita harus menangani nilai yang hilang, baik dengan cara menghapus baris yang memiliki nilai hilang atau menggantinya dengan nilai default (misalnya, menggunakan "kosong" untuk deskripsi yang hilang).
2.	Eksplorasi Data dan Analisis Univariate: 
  Analisis dilakukan untuk memeriksa distribusi fitur tunggal (misalnya, distribusi rating buku atau tahun rilis buku) untuk memastikan data terdistribusi dengan baik.
3.	Analisis Multivariate: 
  Analisis dilakukan untuk memahami hubungan antara beberapa fitur (misalnya, genre dan rating) untuk melihat pola atau korelasi yang ada.
4.	Praproses Teks: 
  Fitur deskripsi buku akan diproses dengan menggunakan TF-IDF (Term Frequency-Inverse Document Frequency) untuk mengonversi teks menjadi representasi numerik yang dapat digunakan oleh model.
5.	Penggabungan dan Transformasi Data: 
  Semua fitur yang diperlukan (title, genre, deskripsi) digabungkan menjadi satu dataset yang siap untuk digunakan dalam model.

#Bab 5: Modeling
Pada tahap ini, kita akan membangun model Content-Based Filtering. Langkah-langkahnya meliputi:
1.	Vectorization:
  Kita akan menggunakan teknik TF-IDF untuk mengonversi teks (judul dan deskripsi) menjadi representasi vektorisasi.
2.	Penghitungan Similaritas:
  Kita akan menggunakan cosine similarity untuk menghitung kesamaan antara buku-buku berdasarkan fitur deskripsi dan genre.
3.	Rekomendasi Buku:
  Berdasarkan kesamaan antara buku-buku, sistem akan memberikan rekomendasi top-N buku yang paling mirip dengan buku yang sudah dipilih oleh pengguna.
4.	Pembuatan Model:
  Penggunaan model berbasis Content-Based Filtering dengan parameter TF-IDF dan cosine similarity untuk menghitung skor kesamaan antar buku.

# Bab 6: Evaluation
Pada tahap ini, kita akan mengevaluasi kinerja model dengan menggunakan F1-Score. beberapa metrik evaluasi yang relevan. Metrik F1-Score, yang menggabungkan precision dan recall akan memberikan gambaran yang lebih seimbang.

 # Penutup
Dengan menggunakan teknik Content-Based Filtering dan evaluasi dengan F1-Score, proyek ini bertujuan untuk memberikan rekomendasi buku yang relevan bagi pengguna berdasarkan fitur konten buku. Dengan demikian, proyek ini dapat membantu meningkatkan pengalaman pengguna dalam menemukan buku yang mereka sukai.
 


