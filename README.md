# Prediksi Produksi Tanaman Menggunkan Algoritma Random Forest Regression, XgBoots Regression, dan Decesion Tree Regression

Proyek ini adalah sistem machine learning untuk memprediksi **produksi tanaman (Production)** berdasarkan data pertanian seperti luas lahan, curah hujan, pupuk, pestisida, suhu, jenis tanaman, dan musim.

Model terbaik yang digunakan adalah **XGBoost Regressor (setelah hyperparameter tuning)**.

---

## Tujuan Proyek
- Memprediksi hasil produksi tanaman berdasarkan faktor pertanian dan lingkungan
- Menganalisis hubungan antar fitur terhadap produksi
- Membangun model machine learning dengan performa terbaik
- Melakukan preprocessing data secara lengkap dan konsisten

---

## Dataset
Dataset berisi fitur:
- Area (luas lahan)
- Annual_Rainfall (curah hujan tahunan)
- Fertilizer (jumlah pupuk)
- Pesticide (pestisida)
- Avg_Temperature (rata-rata suhu)
- Max_Temperature (suhu maksimum)
- Min_Temperature (suhu minimum)
- Crop (jenis tanaman)
- Season (musim)
- Production (target/hasil produksi)

---

##  Workflow Proyek

### 1. Data Understanding
- Load dataset
- Pembersihan data numerik (format koma & titik)
- Handling missing value menggunakan median

---

### 2. Data Preprocessing
- Deteksi missing value
- Deteksi outlier menggunakan metode **IQR**
- Handling outlier dengan **capping & flooring**
- Encoding:
  - Label Encoding → Crop
  - One-Hot Encoding → Season
- Drop fitur yang tidak digunakan

---

### 3. Exploratory Data Analysis (EDA)
- Histogram distribusi data
- Boxplot untuk outlier
- Heatmap korelasi antar fitur
- Analisis hubungan fitur terhadap Production

---

### 4. Data Splitting
Dataset dibagi menjadi:
- 90:10
- 80:20
- 70:30

---

### 5. Model Building
Model yang digunakan:
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor

---

### 6. Evaluasi Model
Metode evaluasi:
- MAE (Mean Absolute Error)
- MSE (Mean Squared Error)
- RMSE (Root Mean Squared Error)
- R² Score

Model terbaik dipilih berdasarkan **R² Score tertinggi**.

---

### 7. Hyperparameter Tuning
- Menggunakan RandomizedSearchCV
- Model: XGBoost Regressor
- Optimasi parameter:
  - n_estimators
  - learning_rate
  - max_depth
  - subsample
  - colsample_bytree
  - gamma

---

### 8. Model Inference
- Input data baru
- Preprocessing otomatis sesuai training
- Output prediksi produksi tanaman

---
