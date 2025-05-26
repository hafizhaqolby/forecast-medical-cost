# Prediksi Biaya Medis Berdasarkan Profil Pasien 🩺📊

Proyek ini bertujuan membangun model regresi untuk memprediksi biaya medis pasien berdasarkan data profil seperti usia, jenis kelamin, status perokok, BMI, dan wilayah tempat tinggal.

---

## 🧠 Problem Domain

Biaya medis merupakan komponen penting dalam perencanaan keuangan personal maupun institusi kesehatan. Dengan memprediksi biaya medis secara akurat berdasarkan data profil pasien, rumah sakit atau perusahaan asuransi dapat mengelola risiko dan alokasi dana dengan lebih efisien.

Dataset yang digunakan adalah [Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance) dari Kaggle, yang berisi 1338 data pasien dan biaya medis masing-masing.

---

## 🎯 Business Understanding

### Problem Statement

Bagaimana memprediksi biaya medis pasien berdasarkan data demografis dan gaya hidup?

### Goals

Membangun model regresi yang mampu memprediksi nilai `charges` dengan akurasi tinggi.

### Solution Statement

Beberapa pendekatan model regresi digunakan:
- Linear Regression (baseline)
- Random Forest Regressor
- XGBoost Regressor

Model terbaik dipilih berdasarkan metrik evaluasi: MAE, RMSE, dan R².

---

## 📊 Hasil Evaluasi Model

Tiga model telah diuji dan dibandingkan:

### 🔹 Linear Regression
- MAE : 4181.19  
- RMSE: 5796.28  
- R²  : 0.7836

### 🔹 Random Forest Regressor
- MAE : 2554.38  
- RMSE: 4581.11  
- R²  : 0.8648

### 🔹 XGBoost Regressor
- MAE : 2567.38  
- RMSE: 4595.68  
- R²  : 0.8640

### ✅ Model Terbaik: Random Forest

Random Forest memberikan akurasi terbaik dengan error paling rendah dan nilai R² tertinggi, menjadikannya pilihan utama untuk model akhir dalam proyek ini.

---

## 📁 Struktur Proyek

```bash
├── submission_model.ipynb   # Notebook dengan kode & dokumentasi
├── submission_model.py      # Script Python bersih
├── README.md                # Laporan proyek
└── insurance.csv            # Dataset
```
