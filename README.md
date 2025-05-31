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
- **Jumlah Data**: 1338 baris, 6 fitur input, 1 target (`charges`)
- **Fitur / Kolom**:
  - `age`: usia pasien
  - `sex`: jenis kelamin (`male`, `female`)
  - `bmi`: Body Mass Index
  - `children`: jumlah anak yang ditanggung
  - `smoker`: apakah pasien perokok (`yes`, `no`)
  - `region`: wilayah tempat tinggal (`northeast`, `southeast`, dll)
  - `charges`: biaya pengobatan (target regresi)
- **Kondisi Data**:
  - Missing Values: Tidak ditemukan missing value pada seluruh kolom `(df.isnull().sum()` menunjukkan nol untuk semua fitur).
  - Statistik Ringkasan (berdasarkan `df.describe()`):
    - `age`: mean 39.2, min 18, max 64
    - `bmi`: mean 30.66, min 15.96, max 53.13
    - `children`: mean 1.09, min 0, max 5
    - `charges`: mean $13,270, min $1,121, max $63,770

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

### 🔍 Model yang Digunakan dan Cara Kerja:
1. **Linear Regression**
   - Mencari hubungan linier antara fitur dan target dengan meminimalkan fungsi error (ordinary least squares).
   - Default parameter dari `sklearn.linear_model.LinearRegression`
3. **Random Forest Regressor**
   - Membuat banyak pohon keputusan (decision trees) pada subset acak data.
   - Prediksi akhir dihitung sebagai rata-rata dari semua pohon.
   - Mengurangi overfitting dan baik untuk data non-linear.
   - Parameter: `n_estimators=100`, `max_depth=10`, `random_state=42`.
5. **XGBoost Regressor**
   - Model boosting yang membangun pohon secara berurutan.
   - Tiap pohon baru memperbaiki kesalahan dari pohon sebelumnya dengan mengoptimasi fungsi loss.
   - Parameter: `n_estimators=100`, `learning_rate=0.1`, `random_state=42`.

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
