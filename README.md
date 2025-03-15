# **Bank Transaction Analysis **
📊 **Clustering & Klasifikasi Data Transaksi Bank**  

## **📌 Deskripsi Proyek**  
Proyek ini bertujuan untuk melakukan **clustering** dan **klasifikasi** pada data transaksi bank guna mencari **pola unik dalam transaksi**. Clustering digunakan untuk mengelompokkan transaksi berdasarkan pola tertentu dengan menggunakan model K-means, sedangkan klasifikasi dilakukan menggunakan dua model, yaitu **K-Nearest Neighbors (KNN) dan Random Forest (RF)**, untuk dibandingkan performanya.  

# SEKLIAS TENTANG DATASET
Dataset ini memberikan wawasan mendalam tentang perilaku transaksi dan pola aktivitas keuangan, yang ideal untuk mengeksplorasi deteksi penipuan dan identifikasi anomali. Dataset ini berisi 2.512 sampel data transaksi, mencakup berbagai atribut transaksi, demografi pelanggan, dan pola penggunaan. Setiap entri memberikan wawasan komprehensif tentang perilaku transaksi, memungkinkan analisis untuk keamanan keuangan dan aplikasi deteksi penipuan.

Fitur Utama:    

1. **TransactionID**: Pengenal alfanumerik unik untuk setiap transaksi

2. **AccountID**: Pengenal unik untuk setiap akun, dengan beberapa transaksi per akun.
3. **TransactionAmount**: Nilai moneter dari setiap transaksi, mencakup pengeluaran sehari-hari hingga pembelian dalam jumlah besar.

4. **TransactionDate**: Stempel waktu dari setiap transaksi, mencatat tanggal dan waktu transaksi.

5. **TransactionType**: Kolom kategorikal yang menunjukkan jenis transaksi, yaitu 'Kredit' atau 'Debit'.
6. **Location**: Lokasi geografis tempat transaksi terjadi, direpresentasikan dengan nama kota di AS.
7. **DeviceID**: Pengenal alfanumerik untuk perangkat yang digunakan dalam transaksi.
8. **IP Address**: Alamat IPv4 yang terkait dengan transaksi, dengan perubahan sesekali untuk beberapa akun.
9. **MerchantID**: Pengenal unik untuk pedagang, menunjukkan pedagang yang sering digunakan dan pedagang yang tidak biasa untuk setiap akun.
10. **AccountBalance**: Saldo akun setelah transaksi, dengan korelasi logis berdasarkan jenis dan jumlah transaksi.
11. **PreviousTransactionDate**: Stempel waktu dari transaksi sebelumnya untuk akun tersebut, membantu dalam menghitung frekuensi transaksi.
12. **Channel**: Saluran yang digunakan untuk melakukan transaksi (misalnya, Online, ATM, Cabang).
13. **CustomerAge**: Usia pemegang akun, dengan pengelompokan logis berdasarkan pekerjaan.
14. **CustomerOccupation**: Pekerjaan pemegang akun (misalnya, Dokter, Insinyur, Mahasiswa, Pensiunan), yang mencerminkan pola pendapatan.
15. **TransactionDuration**: Durasi transaksi dalam hitungan detik, bervariasi berdasarkan jenis transaksi.
16. **LoginAttempts**: Jumlah upaya login sebelum transaksi, dengan nilai yang lebih tinggi dapat menunjukkan potensi anomali.

---

## **📂 Struktur Folder**  
```
📁 bank-transaction-analysis
│── 📄 classification_bank_transactions.ipynb
│── 📄 clustering_bank_transactions.ipynb
│── 📄 README.md         
│── 📄 requirements.txt  
```

---

## **🛠 Teknologi yang Digunakan**  
- **Python** (Pandas, Scikit-Learn, Matplotlib, Seaborn)  
- **Jupyter Notebook** untuk eksplorasi data  
- **Machine Learning** (K-Means untuk clustering, KNN & Random Forest untuk klasifikasi)  

---

## **📊 Hasil Analisis**  
- **Clustering:** Mengelompokkan transaksi berdasarkan pola tertentu
      - # Analisis Karakteristik Cluster dari Model KMeans
   
   Berikut adalah analisis karakteristik untuk setiap cluster yang dihasilkan dari model KMeans.
   
   1. Cluster 0: "Kelompok Pensiunan (Retired)"
       - TransactionAmount: Rata-rata transaksi $294.53, dengan median $213.33, menunjukkan transaksi cenderung kecil hingga menengah.
       - CustomerAge: Rata-rata 65 tahun, dengan rentang usia 51-80 tahun, menunjukkan mayoritas pelanggan adalah lansia.
       - AccountBalance: $4,542 rata-rata, cukup tinggi, menunjukkan mereka memiliki saldo yang relatif stabil.
       - LoginAttempts: Rata-rata 1.12, menunjukkan pengguna jarang mengalami kesulitan login.
       - Kesimpulan: Klaster ini mencerminkan pensiunan dengan saldo cukup tinggi, melakukan transaksi menengah, dan jarang mengalami masalah login.
   2. Cluster 2: "Kelompok Mahasiswa (Student)"
       - TransactionAmount: Rata-rata transaksi $313.22, sedikit lebih tinggi dari Cluster 0.
       - CustomerAge: Rata-rata 23 tahun, dengan rentang usia 18-28 tahun, cocok dengan profil mahasiswa.
       - AccountBalance: $1,570, menunjukkan saldo cenderung lebih rendah dibanding klaster lain.
       - LoginAttempts: Rata-rata 1.11, menunjukkan mereka cukup terbiasa dengan sistem.
       - Kesimpulan: Klaster ini mencerminkan mahasiswa dengan saldo rendah, tetapi masih melakukan transaksi aktif.
   3. Cluster 3: "Kelompok Profesional Muda (Engineer)"
       - TransactionAmount: Rata-rata transaksi $289.04, sedikit lebih rendah dari klaster lain.
       - CustomerAge: Rata-rata 42 tahun, dengan rentang 26-60 tahun, menunjukkan profesional muda hingga paruh baya.
       - AccountBalance: $5,486, lebih tinggi dari mahasiswa dan pensiunan, menunjukkan stabilitas finansial lebih baik.
       - LoginAttempts: Rata-rata 1.12, cukup stabil.
       - Kesimpulan: Klaster ini mencerminkan profesional muda dengan saldo lebih tinggi, tetapi transaksi cenderung moderat.
   
   4. Cluster 3: "Kelompok Profesional Senior (Doctor)"
       - TransactionAmount: Rata-rata transaksi $292.70, mirip dengan klaster lain
       - CustomerAge: Rata-rata 49 tahun, dengan rentang 29-70 tahun, menunjukkan profesional dengan pengalaman lebih senior.
       - AccountBalance: $8,978, tertinggi dibanding klaster lain, menunjukkan kestabilan finansial yang kuat.
       - LoginAttempts: Rata-rata 1.15, sedikit lebih tinggi, mungkin karena aktivitas login lebih sering.
       - Kesimpulan: Klaster ini mencerminkan profesional senior dengan saldo tinggi, sering bertransaksi, dan lebih aktif secara digital.
     
      
- **Klasifikasi:** Memprediksi kategori transaksi menggunakan **KNN dan RF**, serta membandingkan performa kedua model
     # **1. Performa Model K-Nearest Neighbors (KNN)**
   
   ### Akurasi KNN: 74.16%
   ### Precision & Recall:
     
     * Kelas 0 & 1 memiliki recall tinggi (0.92), artinya model mampu mengidentifikasi banyak instance dari kelas ini dengan baik.
     
     * Kelas 2 & 3 memiliki recall lebih rendah (0.61 & 0.52), menunjukkan model masih kesulitan dalam mengenali instance dari kelas tersebut.
   
   ### Confusion Matrix:
   
   * Model banyak melakukan kesalahan pada kelas 2 dan 3, yang menyebabkan f1-score lebih rendah.
   
   ## Kesimpulan KNN:
   
   KNN bekerja cukup baik, tetapi kurang optimal dalam membedakan kelas 2 dan 3.
   
   Akurasi cukup baik (74%), tetapi masih ada overlap antar kelas, terutama pada kelas yang memiliki distribusi mirip.
   
   
   # **2. Performa Model Random Forest (RF)**
   
   ### Akurasi RF: 81.31% (lebih tinggi dibanding KNN!)
   ### Precision & Recall:
   * Kelas 1 memiliki performa hampir sempurna (precision = 0.98, recall = 0.99), yang berarti model hampir selalu mengklasifikasikan kelas ini dengan benar.
   * Kelas 3 masih memiliki recall rendah (0.63), tetapi lebih baik dibanding KNN.
   Confusion Matrix:
   Kesalahan klasifikasi berkurang dibanding KNN, terutama pada kelas 2 dan 3.
   
   ## Kesimpulan Random Forest:
   
   * Performa lebih baik dibanding KNN karena mampu menangani ketidakseimbangan data dan fitur yang lebih kompleks.
   * Model lebih akurat dalam membedakan kelas yang memiliki distribusi mirip, sehingga akurasi meningkat menjadi 81%.
   * Random Forest lebih stabil dan tidak terlalu sensitif terhadap skala fitur, sehingga lebih cocok untuk dataset ini.
 
   # **Perbandingan Hasil Evaluasi Sebelum & Setelah Tuning**

 Model	Random Forest

 Akurasi Sebelum Tuning	            : 81.31%

 Akurasi Setelah Tuning	            : 82.31%

 Peningkatan	                      		+1%

 ## Perbandingan Confusion Matrix
  - Kesalahan klasifikasi pada kelas 0 dan 2 berkurang, menunjukkan model lebih baik mengenali kelas tersebut.
  - Kelas 3 masih memiliki banyak kesalahan klasifikasi (35 salah ke kelas 2) → Recall untuk kelas 3 masih rendah.


## Perbandingan Precision & Recall

  - Recall untuk kelas 0 & 2 meningkat, yang berarti model lebih baik dalam mengenali instance yang benar.
  - Recall untuk kelas 3 menurun (0.63 → 0.58), artinya model masih kesulitan dalam mengklasifikasikan kelas ini.

# Identifikasi Kelemahan Model
1. Precision & Recall untuk kelas 3 masih kurang stabil

  - Model masih sering salah mengklasifikasikan kelas 3 ke kelas lain.
  - Bisa jadi karena distribusi data kelas 3 yang mirip dengan kelas lain.
  
2. Potensi Overfitting Berkurang Setelah Tuning

  - Dengan max_depth=10, model lebih simpel dan tidak terlalu overfit pada data training.

# Rekomendasi Tindakan Lanjutan

1. Menggunakan Teknik Resampling (SMOTE atau Undersampling)

  Jika kelas 3 memiliki jumlah data lebih sedikit, bisa dicoba oversampling atau SMOTE untuk menyeimbangkan distribusi.

2. Mencoba Model Lain (XGBoost atau LightGBM)

  Jika ingin hasil lebih optimal, bisa diuji model berbasis Gradient Boosting seperti XGBoost atau LightGBM.

3. Feature Engineering

  Analisis fitur lebih dalam, apakah ada fitur yang terlalu dominan atau tidak berkontribusi dalam klasifikasi.
---

## **📦 Cara Menjalankan Proyek**  
1. Clone repo ini:  
   ```sh
   git clone https://github.com/username/bank-transaction-analysis.git
   cd bank-transaction-analysis
   ```
2. Install dependencies:  
   ```sh
   pip install -r requirements.txt
   ```
3. Jalankan Jupyter Notebook:  
   ```sh
   jupyter notebook
   ```
4. Buka file **`clustering_bank_transaction.ipynb`** untuk clustering dan **`classification_bank_transactions.ipynb`** untuk klasifikasi, lalu jalankan selnya.  

---

## **📥 Dataset**  
📌 Kamu bisa mendownloadnya di sini:  
🔗 https://www.kaggle.com/datasets/valakhorasani/bank-transaction-dataset-for-fraud-detection/data

---

## **✍ Kontribusi & Lisensi**  
💡 Silakan fork dan kontribusi! Proyek ini menggunakan lisensi **MIT**.  

