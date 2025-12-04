# Fraud Detection System: End-to-End Machine Learning & Deep Learning Pipeline

## 📋 Project Overview
Project ini bertujuan untuk mendeteksi transaksi penipuan (*fraud detection*) pada dataset transaksi keuangan skala besar. Tantangan utama dataset ini adalah ukuran data yang besar (590k+ baris) dan ketidakseimbangan kelas (*class imbalance*) dimana hanya 3.5% transaksi yang merupakan fraud.

Pipeline dibangun secara *end-to-end* mencakup:
1. **Data Preprocessing** (Polars, Handling Missing Values, Time Engineering).
2. **Machine Learning Model** (LightGBM).
3. **Deep Learning Model** (Neural Network dengan PyTorch).
4. **Evaluation & Comparison**.

## 🛠️ Tech Stack
* **Language:** Python
* **Data Processing:** Polars (High Performance), Pandas, NumPy
* **Machine Learning:** LightGBM (Gradient Boosting)
* **Deep Learning:** PyTorch
* **Environment:** Google Colab

## 📊 Experimental Results

Kami membandingkan performa dua pendekatan model:

| Model | Type | AUC Score (Validation) | Training Time | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **LightGBM** | Machine Learning | **0.9135** | ~2 Menit | **Best Model.** Sangat efisien menangani data tabular dan missing values. |
| **Simple Neural Network** | Deep Learning | 0.8684 | ~10 Menit | Dilatih menggunakan *Balanced Sub-sampling* (50k data) dikarenakan limitasi memori (RAM). |

**Analisis:**
Model **LightGBM** terbukti lebih unggul untuk kasus ini. Deep Learning memiliki potensi, namun membutuhkan *resource* komputasi yang jauh lebih besar dan *feature engineering* yang lebih kompleks (seperti Embedding) untuk mengalahkan performa *Tree-based model* pada data tabular.

## 🚀 How to Run
1. Clone repository ini.
2. Download dataset IEEE-CIS Fraud Detection.
3. Jalankan notebook `Midterm_Fraud_Detection.ipynb`.
   * **Note:** Pastikan Runtime memiliki RAM minimal 12GB. Jika menggunakan Google Colab Free Tier, script menggunakan strategi *Low Memory Management* (Estafet Loading) agar tidak crash.

## 📂 Submission Files
* `Midterm_Fraud_Detection.ipynb`: Source code lengkap (EDA, Preprocessing, Modeling).
* `submission_final.csv`: Hasil prediksi probabilitas fraud pada data test.
