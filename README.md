# 🩺 Prediksi Biaya Medis Berdasarkan Profil Pasien

Proyek ini bertujuan membangun model regresi untuk memprediksi biaya medis pasien berdasarkan data profil seperti usia, jenis kelamin, status merokok, BMI, jumlah anak, dan wilayah tempat tinggal.

Dengan prediksi yang akurat, rumah sakit dan perusahaan asuransi dapat mengelola biaya dan risiko secara lebih efisien dan proaktif.

---

## 🧠 Problem Domain

Biaya pengobatan dapat sangat bervariasi antar individu. Mengetahui prediksi biaya medis berdasarkan faktor demografis dan gaya hidup pasien dapat membantu penyedia layanan kesehatan dalam:

- Perencanaan anggaran
- Penentuan premi asuransi
- Penyuluhan kesehatan preventif

Dataset yang digunakan adalah [Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance) dari Kaggle, berisi 1338 data pasien dan biaya medis masing-masing.

---

## 🎯 Business Understanding

### 📌 Problem Statement

Bagaimana memprediksi biaya medis (`charges`) berdasarkan fitur profil pasien seperti usia, jenis kelamin, status merokok, dan lainnya?

### 🎯 Goals

Membangun model machine learning regresi yang dapat memprediksi biaya medis dengan akurasi tinggi dan error serendah mungkin.

### 💡 Solution Statement

Beberapa pendekatan model regresi digunakan dan dibandingkan performanya:

- **Linear Regression** – sebagai baseline model
- **Random Forest Regressor**
- **XGBoost Regressor**

Model terbaik dipilih berdasarkan evaluasi terhadap metrik MAE, RMSE, dan R².

---

## 📊 Data Understanding

- **Sumber Data**: [Medical Cost Personal Dataset (Kaggle)](https://www.kaggle.com/datasets/mirichoi0218/insurance)
- **Jumlah Data**: 1338 baris, 7 fitur input, 1 target (`charges`)
- **Fitur / Kolom**:
  - `age`: usia pasien
  - `sex`: jenis kelamin (`male`, `female`)
  - `bmi`: Body Mass Index
  - `children`: jumlah anak yang ditanggung
  - `smoker`: apakah pasien perokok (`yes`, `no`)
  - `region`: wilayah tempat tinggal (`northeast`, `southeast`, dll)
  - `charges`: biaya pengobatan (target regresi)

---

## 🧹 Data Preparation

### 🔧 Langkah-Langkah:
1. One-Hot Encoding pada fitur kategorikal (`sex`, `smoker`, `region`)
2. Tidak dilakukan scaling karena model tree-based (Random Forest & XGBoost) tidak memerlukannya
3. Split data menjadi Training dan Testing (80:20)

### 📝 Alasan:
- **Encoding** diperlukan karena model ML tidak dapat bekerja dengan string/kategori langsung.
- **Split data** dilakukan agar model dapat diuji kemampuannya terhadap data baru (generalization).

---

## 🤖 Modeling

### 🔍 Model yang Digunakan:
1. **Linear Regression**
   - Default parameter dari `sklearn.linear_model.LinearRegression`
2. **Random Forest Regressor**
   - Estimators: `n_estimators=100`
   - Depth dibatasi otomatis oleh data
3. **XGBoost Regressor**
   - Estimators: `n_estimators=100`
   - Learning rate: `0.1`
   - Max depth: `3`
   - Booster: `'gbtree'`

### ⚙️ Alasan Pemilihan Model:
- **Linear Regression** digunakan sebagai baseline karena mudah dipahami.
- **Random Forest** dan **XGBoost** dipilih karena kemampuannya menangani data non-linear dan interaksi fitur kompleks.

---

## 📈 Hasil Evaluasi Model

| Model               | MAE     | RMSE    | R²     |
|--------------------|---------|---------|--------|
| Linear Regression  | 4181.19 | 5796.28 | 0.7836 |
| Random Forest      | 2554.38 | 4581.11 | 0.8648 |
| XGBoost            | 2567.38 | 4595.68 | 0.8640 |

### ✅ Model Terbaik: **Random Forest Regressor**

Model ini menunjukkan error paling rendah dan skor R² tertinggi, yang berarti mampu menjelaskan variasi data target dengan lebih baik dibanding model lainnya.

---

## 📁 Struktur Proyek

```bash
.
├── submission_model.ipynb   # Notebook dengan dokumentasi dan visualisasi
├── submission_model.py      # Script Python bersih untuk deployment
├── README.md                # Laporan proyek ini
└── insurance.csv            # Dataset dari Kaggle
