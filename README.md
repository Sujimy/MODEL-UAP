# MODEL-UAP

1. Latar belakang
# Deskripsi Proyek

Proyek ini muncul dari kebutuhan untuk memahami lebih dalam bagaimana berbagai faktor memengaruhi performa akademik siswa. Di dunia pendidikan, salah satu tantangan utama adalah mengidentifikasi siswa yang membutuhkan bantuan tambahan sebelum mereka mengalami kegagalan akademik. Dalam konteks ini, data memiliki peran yang sangat penting. Data yang dikumpulkan dari berbagai aspek kehidupan siswa, seperti latar belakang keluarga, tingkat pendidikan orang tua, dan hasil ujian, dapat memberikan wawasan yang berharga tentang apa yang memengaruhi keberhasilan siswa. Dengan menganalisis data ini, institusi pendidikan dapat merancang program intervensi yang lebih terarah, efektif, dan berbasis bukti untuk meningkatkan hasil belajar siswa.

Dataset yang digunakan dalam proyek ini berisi **10.000 entri data siswa**, yang mencakup berbagai atribut seperti jenis kelamin, etnis, tingkat pendidikan orang tua, status makan siang, tingkat persiapan ujian, dan nilai dari berbagai mata pelajaran seperti matematika, membaca, menulis, dan ilmu pengetahuan. Data ini juga mencakup kolom nilai total dan predikat nilai akhir siswa (grade). Dengan ukuran dataset yang cukup besar, proyek ini memiliki kapasitas untuk melakukan analisis mendalam yang dapat menggambarkan pola umum dan anomali dalam performa akademik siswa.

Dengan memanfaatkan teknologi pembelajaran mesin, proyek ini dirancang tidak hanya untuk memprediksi nilai akhir siswa tetapi juga untuk mengidentifikasi pola-pola yang tersembunyi dalam data. Pola-pola ini dapat membantu pendidik memahami faktor-faktor yang paling signifikan dalam menentukan keberhasilan akademik siswa. Selain itu, model prediktif ini diharapkan dapat menjadi alat yang praktis untuk membantu administrator pendidikan membuat keputusan strategis yang lebih baik, seperti alokasi sumber daya dan perencanaan program dukungan siswa. Dalam era di mana keputusan berbasis data menjadi standar emas, kemampuan untuk memahami dan memanfaatkan data dengan cara yang efektif adalah langkah penting menuju pendidikan yang lebih baik.

Proyek ini juga bertujuan untuk mengintegrasikan teknologi modern ke dalam proses pendidikan dengan menyediakan alat berbasis web yang mudah diakses dan digunakan. Melalui aplikasi ini, pengguna dapat dengan mudah mengunggah data siswa, mendapatkan prediksi nilai, dan mengeksplorasi wawasan yang dihasilkan dari analisis data. Visualisasi interaktif akan membantu pengguna untuk memahami hasil analisis secara lebih intuitif, sehingga mereka dapat mengambil tindakan yang sesuai berdasarkan data tersebut. Aplikasi ini tidak hanya dirancang untuk mempermudah analisis data, tetapi juga untuk memberdayakan pendidik dalam membuat keputusan yang lebih informed dan berdampak positif pada siswa.

Secara keseluruhan, proyek ini merupakan langkah menuju pendidikan yang lebih terpersonalisasi dan berbasis data. Dengan menggabungkan pembelajaran mesin dan antarmuka pengguna yang intuitif, proyek ini memberikan solusi yang inovatif untuk tantangan yang dihadapi oleh sistem pendidikan modern. Melalui penerapan teknologi ini, diharapkan bahwa setiap siswa dapat diberikan kesempatan yang lebih besar untuk berhasil, terlepas dari latar belakang mereka, dan institusi pendidikan dapat meningkatkan kualitas layanan yang mereka berikan kepada masyarakat.

2.Deskripsi Model 
a. Random Forest
Model yang digunakan adalah Feedforward Neural Network (FNN) yang dibangun menggunakan library TensorFlow/Keras. Model ini dirancang untuk klasifikasi multikelas berdasarkan dataset Student Performance 10k. Dataset mencakup variabel seperti skor matematika, membaca, menulis, skor total, jenis kelamin, latar belakang etnis, dan tingkat pendidikan orang tua. Model ini menggunakan tiga lapisan:

Dense Layer: Dengan 128 neuron dan fungsi aktivasi ReLU.
Dropout Layer: Untuk mengurangi overfitting dengan tingkat dropout 30%.
Dense Layer: Dengan 64 neuron dan fungsi aktivasi ReLU.
Output Layer: Dengan fungsi aktivasi softmax untuk menghasilkan probabilitas setiap kelas.

Analisis Performa Model
Akurasi:
Akurasi pada data validasi mencapai 96.85%.
Akurasi yang tinggi menunjukkan bahwa model dapat menangkap pola dari data dengan baik.
Classification Report:
F1-Score untuk sebagian besar kelas berada di atas 0.90, menunjukkan keseimbangan antara presisi dan recall yang baik.
Namun, kelas "Fail" dan nilai NaN memiliki precision 0.00, yang disebabkan oleh kurangnya data yang memadai untuk kelas ini.
Confusion Matrix:
Sebagian besar prediksi berada di diagonal utama matriks, menunjukkan model secara konsisten memprediksi kelas yang benar.
Kesalahan utama terjadi antara kelas A dan B, serta kelas D, yang mungkin terjadi karena fitur data yang mirip.
Grafik Pelatihan:
Grafik menunjukkan peningkatan akurasi pelatihan dan validasi selama epoch.
Tidak ada indikasi overfitting yang signifikan, karena akurasi pelatihan dan validasi tetap sejalan.

b.Model FNN
Model yang digunakan dalam penelitian ini adalah Feedforward Neural Network (FNN), sebuah jenis jaringan saraf tiruan yang dirancang untuk menangkap hubungan non-linear dalam data. Model ini terdiri dari beberapa lapisan tersembunyi (hidden layers) dengan fungsi aktivasi Rectified Linear Unit (ReLU) untuk menangani non-linearitas, serta lapisan output dengan fungsi aktivasi softmax untuk mengakomodasi tugas klasifikasi multi-kelas. Model ini dirancang untuk memprediksi kolom target grade berdasarkan fitur-fitur yang tersedia dalam dataset Student_performance_10k.csv.

Arsitektur Model:

Input Layer: Dimensi masukan disesuaikan dengan jumlah fitur numerik dan kategori yang telah diproses sebelumnya.
Hidden Layers: Dua lapisan tersembunyi masing-masing terdiri dari 128 dan 64 neuron dengan fungsi aktivasi ReLU. Dropout dengan nilai 0.3 diterapkan pada setiap lapisan tersembunyi untuk mengurangi overfitting.
Output Layer: Lapisan output terdiri dari sejumlah neuron yang sesuai dengan jumlah kelas pada kolom grade, dengan fungsi aktivasi softmax untuk menghasilkan probabilitas.
Proses Pelatihan:

Optimizer: Adam, dipilih karena kecepatan konvergensinya yang baik pada dataset dengan karakteristik kompleks.
Loss Function: Sparse categorical crossentropy digunakan untuk menangani masalah klasifikasi multi-kelas.
Epochs: 30 iterasi dengan batch size 32.
Data Validation: Data dibagi menjadi 80% untuk pelatihan dan 20% untuk pengujian dengan stratifikasi untuk menjaga distribusi kelas.
Analisis Performansi:

Akurasi: Model mencapai akurasi 96.85% pada data pengujian, yang menunjukkan bahwa model mampu memprediksi kelas grade dengan tingkat keberhasilan yang sangat tinggi.
Confusion Matrix: Confusion matrix menunjukkan bahwa model sangat baik dalam mengklasifikasikan kelas utama seperti B dan C, namun terdapat sedikit kesalahan klasifikasi pada kelas dengan data yang lebih sedikit seperti D dan Fail.
Classification Report: Precision, recall, dan f1-score untuk sebagian besar kelas berada di atas 0.90, yang mengindikasikan performa yang seimbang dalam meminimalkan kesalahan positif palsu dan negatif palsu.
Kurva Akurasi: Grafik menunjukkan peningkatan akurasi pelatihan dan validasi selama iterasi, dengan kesenjangan kecil antara keduanya, yang menunjukkan bahwa model tidak mengalami overfitting.

3.hasil perbandingan model Feedforward Neural Network (FNN) dan Random Forest (RF) yang diuraikan dalam bentuk analisis dan tabel evaluasi metrik berdasarkan data.

1. Hasil Evaluasi Model
Feedforward Neural Network (FNN)

Akurasi Pengujian: 96.85%
Precision, Recall, dan F1-Score (rata-rata tertimbang):
Precision: 97%
Recall: 97%
F1-Score: 97%
Kinerja Berdasarkan Kelas:
Kelas B dan C memiliki performa tertinggi, sementara kelas Fail tidak terprediksi dengan baik karena keterbatasan data.
Random Forest (RF)

Akurasi Pengujian: ~94-95%
Precision, Recall, dan F1-Score (rata-rata tertimbang):
Precision: 95%
Recall: 95%
F1-Score: 95%
Kinerja Berdasarkan Kelas:
Hasil evaluasi cukup baik pada kelas mayoritas (B dan C), namun performa menurun pada kelas Fail dan D.

2. Grafik Performa
Grafik Akurasi FNN

Plot menunjukkan peningkatan akurasi selama 30 epoch dengan validasi akurasi stabil di ~97%.
Terdapat sedikit perbedaan (gap) antara akurasi pelatihan dan validasi, menunjukkan model tidak overfitting.
Confusion Matrix FNN

Kelas B: Prediksi sangat akurat dengan lebih dari 1.100 data terprediksi dengan benar.
Kelas D dan Fail: Beberapa prediksi salah, menunjukkan perlu lebih banyak data untuk meningkatkan akurasi.
Confusion Matrix RF

Kesalahan prediksi lebih banyak pada kelas minoritas (D dan Fail), namun secara keseluruhan menunjukkan hasil stabil pada kelas mayoritas.



