# Prediksi Produksi Tanaman Menggunakan Machine Learning

Proyek ini bertujuan untuk memprediksi hasil produksi tanaman berdasarkan data pertanian menggunakan pendekatan machine learning. Sistem ini memanfaatkan beberapa faktor seperti luas lahan, curah hujan, pupuk, pestisida, suhu, jenis tanaman, dan musim untuk menghasilkan prediksi produksi yang lebih akurat.

Dalam proyek ini digunakan tiga algoritma utama yaitu Decision Tree Regressor, Random Forest Regressor, dan XGBoost Regressor. Setelah dilakukan evaluasi dan hyperparameter tuning, XGBoost menjadi model dengan performa terbaik berdasarkan nilai R² Score.

---

##  Dataset

Dataset yang digunakan merupakan data pertanian yang berisi berbagai faktor yang mempengaruhi hasil produksi tanaman. Setiap baris data merepresentasikan kondisi pertanian tertentu yang akan digunakan untuk memprediksi nilai Production sebagai target utama.

Fitur yang digunakan dalam dataset antara lain:

- Area (luas lahan)
- Annual_Rainfall (curah hujan tahunan)
- Fertilizer (jumlah pupuk)
- Pesticide (jumlah pestisida)
- Avg_Temperature (suhu rata-rata)
- Max_Temperature (suhu maksimum)
- Min_Temperature (suhu minimum)
- Crop (jenis tanaman)
- Season (musim tanam)
- Production (target hasil produksi)

---

##  Data Understanding & Preprocessing

Pada tahap awal, dataset dibaca menggunakan pandas dengan pemisah “;”. Setelah itu dilakukan pengecekan struktur data untuk memastikan semua kolom memiliki tipe data yang sesuai.

Beberapa kolom numerik memiliki format tidak konsisten seperti penggunaan titik dan koma sehingga perlu dilakukan pembersihan agar dapat dikonversi menjadi format numerik yang valid. Nilai yang hilang kemudian diisi menggunakan median agar tidak mempengaruhi distribusi data secara signifikan.

Selanjutnya dilakukan proses penanganan outlier menggunakan metode Interquartile Range (IQR). Outlier tidak dihapus, tetapi ditangani menggunakan metode capping dan flooring agar data tetap stabil.

- Encoding data kategorikal dilakukan sebagai berikut:
  - Label Encoding → Crop
  - One-Hot Encoding → Season
- Fitur yang tidak digunakan dihapus:
  - Crop_Year
  - State
  - Yield

---

##  Exploratory Data Analysis (EDA)

Untuk memahami karakteristik data, dilakukan analisis visual menggunakan beberapa metode. Histogram digunakan untuk melihat distribusi data, boxplot digunakan untuk mendeteksi outlier, dan heatmap korelasi digunakan untuk melihat hubungan antar fitur.

Dari hasil analisis terlihat bahwa beberapa fitur memiliki hubungan terhadap variabel Production sehingga dapat membantu dalam proses pemodelan.

---

##  Pembangunan Model Machine Learning

Pada tahap ini dataset dibagi menjadi beberapa skenario training dan testing yaitu 90:10, 80:20, dan 70:30 untuk membandingkan performa model.

Model yang digunakan dalam proyek ini adalah:

- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor

Setiap model dievaluasi menggunakan metrik MAE, MSE, RMSE, dan R² Score. Dari hasil pengujian, XGBoost menunjukkan performa terbaik dibandingkan model lainnya.

---

##  Hyperparameter Tuning

Untuk meningkatkan performa model XGBoost, dilakukan hyperparameter tuning menggunakan RandomizedSearchCV. Parameter yang dioptimasi meliputi jumlah estimator, learning rate, max depth, subsample, colsample_bytree, dan gamma.

Hasil tuning menunjukkan peningkatan performa model dibandingkan sebelum tuning.

---

##  Prediksi (Inference)

Model yang sudah dilatih kemudian digunakan untuk memprediksi data baru. Data input juga melalui proses preprocessing yang sama seperti data training agar hasil prediksi tetap konsisten.

Fitur yang digunakan untuk prediksi meliputi:
- Crop
- Season
- Area
- Annual_Rainfall
- Fertilizer
- Pesticide
- Avg_Temperature
- Max_Temperature
- Min_Temperature

Output dari model adalah nilai prediksi Production.

---

## Model Saving

Model terbaik disimpan menggunakan library joblib dalam format `.pkl`. File ini berisi model XGBoost terbaik, label encoder untuk Crop, serta daftar fitur yang digunakan saat training.

---

##  Instalasi Library

Sebelum menjalankan proyek, pastikan semua library berikut sudah diinstall:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost joblib
