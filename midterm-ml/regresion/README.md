# YearPredictionMSD: End-to-End Regression Pipeline

## 📌 Project Overview
Repository ini berisi implementasi pipeline Machine Learning dan Deep Learning secara *end-to-end* untuk memprediksi tahun rilis lagu berdasarkan fitur audio (timbre features). Proyek ini dikerjakan sebagai tugas Ujian Tengah Semester (UTS) mata kuliah Machine Learning & Deep Learning.

Tujuan utama adalah membandingkan performa model Regresi Linear klasik, Ensemble Learning (XGBoost), dan Arsitektur Neural Network (Deep Learning) pada dataset yang memiliki dimensi fitur tinggi dan jumlah sampel besar (>500k data).

## 🛠️ Metodologi

### 1. Data Preprocessing
Dataset awal tidak memiliki header dan terdiri dari 90 fitur numerik + 1 target (Year). Langkah yang dilakukan:
* **Data Cleaning:** Menangani *missing values* dan memastikan konsistensi tipe data.
* **Feature Scaling:** Menggunakan `StandardScaler` untuk menormalisasi 90 fitur audio agar memiliki distribusi rata-rata 0 dan deviasi standar 1 (krusial untuk Deep Learning).
* **Data Splitting:** 80% Training, 20% Testing.

### 2. Model Architecture
Kami menguji tiga pendekatan berbeda:

* **Baseline:** Linear Regression.
* **Machine Learning (Advanced):** XGBoost Regressor (Histogram-based method untuk efisiensi data besar).
* **Deep Learning:** Multi-Layer Perceptron (MLP) dengan arsitektur:
    * Input Layer: 90 Neurons
    * Hidden Layers: 256 (ReLU) -> 128 (ReLU) -> 64 (ReLU)
    * Regularization: BatchNormalization & Dropout (0.3) untuk mencegah overfitting.
    * Optimizer: Adam | Loss: MSE.

## 📊 Hasil & Evaluasi (Performance Metrics)

Evaluasi dilakukan menggunakan data Test (20% hold-out). Berikut adalah perbandingan performa model:

| Model | RMSE (Lower is Better) | R² Score (Higher is Better) | Keterangan |
| :--- | :--- | :--- | :--- |
| **Linear Regression** | 9.5233 | 0.2380 | Baseline Model |
| **XGBoost Regressor** | 9.0050 | 0.3187 | Peningkatan signifikan vs Baseline |
| **Deep Learning (MLP)** | **8.7619** | **0.3550** | **Best Model** 🏆 |

**Kesimpulan:**
Deep Learning terbukti menjadi model terbaik dengan R² Score tertinggi (**0.3550**) dan error terendah. Hal ini menunjukkan bahwa Neural Network mampu menangkap pola non-linear yang kompleks pada fitur audio yang tidak dapat ditangkap sepenuhnya oleh model linear maupun tree-based standard.

## 📈 Visualisasi Hasil
![Actual vs Predicted](link_gambar_scatter_plot_kamu_disini.png)
*Scatter plot menunjukkan prediksi model cukup akurat untuk rentang tahun 1990-2010, namun memiliki bias pada tahun-tahun tua akibat ketidakseimbangan dataset.*

## 📂 Struktur Repository
* `train_clean.csv` & `test_clean.csv`: Dataset hasil preprocessing.
* `Midterm_Machine_Learning.ipynb`: Notebook eksperimen model ML (Linear & XGBoost).
* `Midterm_Deep_Learning.ipynb`: Notebook eksperimen model DL (TensorFlow/Keras).
* `best_model_dl.keras`: File model Deep Learning terbaik yang disimpan.
