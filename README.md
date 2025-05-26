# forecast-medical-cost
## Prediksi Biaya Medis Berdasarkan Data Profil Pasien Menggunakan Regresi Machine Learning
### 📘 1. Domain Proyek
- **Latar Belakang**  
  Biaya pelayanan kesehatan terus meningkat dari tahun ke tahun. Salah satu tantangan besar yang dihadapi oleh perusahaan asuransi dan penyedia layanan kesehatan adalah bagaimana memperkirakan biaya pengobatan pasien secara akurat berdasarkan data profil pasien. Prediksi yang akurat dapat membantu:
  - Penentuan premi asuransi yang adil dan sesuai risiko
  - Optimalisasi anggaran pelayanan kesehatan
  - Deteksi pola risiko kesehatan masyarakat
- **Mengapa Masalah Ini Penting**  
  Penetapan biaya medis yang akurat adalah fondasi dari sistem asuransi yang berkelanjutan. Tanpa pendekatan prediktif, perusahaan asuransi bisa mengalami kerugian akibat klaim berlebih atau justru membebani pelanggan dengan premi yang terlalu tinggi.
  
### 💼 2. Business Understanding
- **Problem Statement**  
  Bagaimana memprediksi biaya medis seseorang berdasarkan usia, BMI, jenis kelamin, status merokok, jumlah anak, dan wilayah tempat tinggal?
 - **Goals**  
   Mengembangkan model machine learning yang dapat memprediksi biaya medis secara akurat berdasarkan data profil pasien.
  - **Solution Statement**
    1. Baseline model: Linear Regression sebagai model awal.
    2. Alternative model: Random Forest dan XGBoost Regressor untuk mengeksplorasi akurasi yang lebih tinggi.
    3. Improvement: Hyperparameter tuning pada model terbaik untuk meningkatkan performa prediksi.  
    Metrik evaluasi yang digunakan:
    - MAE (Mean Absolute Error)
    - RMSE (Root Mean Squared Error)
    - R² Score

### 📊 3. Data Understanding
- **Sumber Data**: [Medical Cost Personal Datasets](https://www.kaggle.com/datasets/mirichoi0218/insurance)
- **Jumlah Data**: 1338 baris, 7 fitur input, 1 target (`charges`)
- **Fitur / Kolom**
  + `age`: usia pasien (numerik)
  + `sex`: jenis kelamin (kategorikal)
  + `bmi`: body mass index (numerik)
  + `children`: jumlah anak (numerik)
  + `smoker`: apakah pasien merokok (kategorikal: yes/no)
  + `region`: lokasi geografis (kategorikal)
  + `charges`: biaya pengobatan (target)

