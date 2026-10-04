
> [!NOTE] Algoritma Machine Learning
> ### 1. Supervised Learning (Pembelajaran Terawasi)
> Algoritma dalam kelompok ini belajar dari data yang sudah memiliki label atau kunci jawaban. Tugasnya adalah mencari pola antara _input_ (fitur) dan _output_ (target).
> >**Klasifikasi (Memprediksi Kategori/Label)**
>   - **K-Nearest Neighbors (KNN)**: Memprediksi label data baru berdasarkan mayoritas label dari _K_ tetangga terdekatnya.
> - **Logistic Regression**: Memprediksi probabilitas terjadinya suatu kejadian (misal: Ya/Tidak, Spambot/Bukan).
> - **Decision Tree**: Membagi data menggunakan alur keputusan berbentuk pohon (_if-else_ bercabang).
> - **Random Forest**: Menggabungkan hasil prediksi dari puluhan hingga ratusan _Decision Tree_ agar hasilnya lebih akurat.
> - **Support Vector Machine (SVM)**: Mencari garis pemisah (_hyperplane_) terbaik untuk memisahkan dua atau lebih kelompok data.
> - **Naive Bayes**: Memprediksi kelas berdasarkan kalkulasi probabilitas Teorema Bayes (sangat sering untuk analisis teks).
- **Regresi (Memprediksi Angka Kontinu/Nol-Desimal)**
    - **Linear Regression**: Mencari garis lurus terbaik yang menggambarkan hubungan antara variabel _input_ dan angka yang ingin diprediksi (misal: prediksi harga rumah).
        
    - **Polynomial Regression**: Pengembangan _Linear Regression_ untuk data yang memiliki pola kurva/lengkung.
        
    - **Ridge & Lasso Regression**: Versi _Linear Regression_ yang dilengkapi teknik pencegah _overfitting_ (penalti/regulerisasi).

### 2. Unsupervised Learning (Pembelajaran Tanpa Pengawasan)

Algoritma ini bekerja pada data yang tidak memiliki label atau kunci jawaban. Tugasnya adalah menemukan struktur tersembunyi atau kelompok alami dari data tersebut.

- **Clustering (Pengelompokan Data)**
    
    - **K-Means Clustering**: Mengelompokkan data menjadi _K_ kelompok berdasarkan jarak terdekat ke pusat kelompok (_centroid_).
        
    - **Hierarchical Clustering**: Mengelompokkan data secara bertingkat membentuk struktur pohon keluarga (_dendrogram_).
        
    - **DBSCAN**: Mengelompokkan data berdasarkan kerapatan titik data, sangat bagus untuk mendeteksi _outlier_ (data aneh).
        
- **Dimensionality Reduction (Pengurangan Dimensi/Fitur)**
    
    - **Principal Component Analysis (PCA)**: Menyederhanakan data yang memiliki sangat banyak kolom (_fitur_) tanpa kehilangan informasi pentingnya.
        
    - **t-SNE / UMAP**: Algoritma pengurangan dimensi yang sering digunakan untuk visualisasi data kompleks ke dalam grafik 2D atau 3D.
        

### 3. Ensemble & Advanced Learning (Tingkat Lanjut)

Algoritma yang menggabungkan beberapa model kecil untuk menghasilkan prediksi super presisi.

- **Gradient Boosting Algorithms**
    
    - **XGBoost, LightGBM, CatBoost**: Variasi algoritma _boosting_ yang sangat populer dan sering memenangkan kompetisi _data science_. Cara kerjanya adalah memperbaiki kesalahan prediksi dari pohon keputusan sebelumnya secara bertahap.
        

### 4. Reinforcement Learning (Pembelajaran Berbasis Penghargaan)

Algoritma yang belajar melalui metode _trial-and-error_. Agen (program) bertindak di dalam lingkungan tertentu untuk memaksimalkan _reward_ (hadiah) dan meminimalkan _penalty_ (hukuman).

- **Q-Learning**: Algoritma dasar untuk menentukan aksi terbaik di setiap kondisi tertentu.
    
- **Deep Q-Network (DQN)**: Menggabungkan _Q-Learning_ dengan _Neural Network_ (banyak digunakan pada AI game dan robotika).
    

### 5. Deep Learning (Jaringan Saraf Tiruan)

Sub-bidang _Machine Learning_ yang menggunakan arsitektur berlapis (_Artificial Neural Network_) untuk memproses data berukuran raksasa seperti gambar, suara, dan teks.

- **Artificial Neural Network (ANN)**: Fondasi dasar jaringan saraf tiruan.
    
- **Convolutional Neural Network (CNN)**: Khusus untuk pemrosesan gambar dan video (_Computer Vision_).
    
- **Recurrent Neural Network (RNN) & LSTM**: Khusus untuk pemrosesan data berurutan (_Time-Series_ dan Bahasa/NLP).
    
- **Transformer**: Arsitektur modern di balik model bahasa besar (_Large Language Models_) seperti ChatGPT dan Gemini.
