#### **Project Summary**

  * **Goal:** Mendeteksi transaksi penipuan (Fraud) dari dataset yang sangat *imbalanced* (hanya 3.5% fraud).
  * **Pipeline:**
    1.  **Preprocessing:** Menggunakan `Polars` untuk efisiensi memori, mengisi missing value dengan marker khusus (-1), dan Time Engineering (mengubah detik menjadi Jam/Hari).
    2.  **Splitting:** Time-Series Split (80% awal untuk train, 20% akhir untuk validasi) untuk mencegah kebocoran data masa depan.
    3.  **Modeling:** Membandingkan LightGBM vs Neural Network (PyTorch).

#### **Hasil Eksperimen (Benchmark)**

| Model | AUC Score | Waktu Training | Kesimpulan |
| :--- | :--- | :--- | :--- |
| **LightGBM** | **0.9135** | \~2 Menit | **Sangat Baik.** Mampu menangani *missing values* dan data kategorikal secara native. Sangat efisien. |
| **Deep Learning (MLP)** | 0.8684 | \~10 Menit | **Cukup Baik.** Namun kalah akurat dibanding Tree-based model untuk data tabular ini. Membutuhkan scaling data yang ketat. |

**Kesimpulan Akhir:**
Model **LightGBM** dipilih sebagai model final karena memberikan performa AUC tertinggi, training time tercepat, dan penggunaan memori yang lebih efisien dibandingkan arsitektur Deep Learning untuk dataset transaksi ini.
