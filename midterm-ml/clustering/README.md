# Customer Segmentation: End-to-End Clustering Pipeline

## 📋 Project Overview
Project ini bertujuan untuk melakukan segmentasi pelanggan kartu kredit (*Customer Clustering*) menggunakan algoritma Unsupervised Machine Learning. Dengan memahami pola perilaku penggunaan kartu, kita dapat mengelompokkan nasabah menjadi beberapa segmen strategis untuk keperluan pemasaran yang lebih efektif.

Pipeline dibangun secara *end-to-end* mencakup:
1. **Advanced Preprocessing** (Handling Missing Values, Log Transformation, Scaling).
2. **Dimensionality Reduction** (PCA) untuk visualisasi.
3. **Modeling** (K-Means sebagai model utama, dibandingkan dengan Hierarchical Clustering & DBSCAN).
4. **Business Interpretation** (Profiling karakteristik cluster).

## 🛠️ Tech Stack
* **Language:** Python
* **Data Processing:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn (KMeans, DBSCAN, AgglomerativeClustering, PCA)

## 📊 Experimental Results

### 1. Determination of K (Elbow Method)
Berdasarkan analisis Elbow Method, penurunan inersia mulai melandai secara signifikan pada **K=4**. Oleh karena itu, kami memutuskan untuk membagi nasabah menjadi 4 kelompok.

### 2. Cluster Profiling (Business Insight)
Berdasarkan rata-rata penggunaan kartu kredit, berikut adalah 4 persona nasabah yang ditemukan:

| Cluster ID | Nama Segmen | Karakteristik Utama | Rekomendasi Bisnis |
| :--- | :--- | :--- | :--- |
| **Cluster 2** | **The VIP / Big Spenders** | `PURCHASES` Sangat Tinggi, Limit Besar. | Tawarkan program loyalty premium & upgrade limit. |
| **Cluster 1** | **Cash Pullers** | `CASH_ADVANCE` (Tarik Tunai) Sangat Tinggi, Belanja Rendah. | Monitoring risiko kredit, tawarkan cicilan tetap. |
| **Cluster 3** | **Careful Users** | `PRC_FULL_PAYMENT` Tinggi, Saldo Rendah. | Nasabah sehat. Tawarkan promo untuk menaikkan volume belanja. |
| **Cluster 0** | **Low Activity** | Semua aktivitas transaksi rendah. | Perlu program re-aktivasi / promo pengguna pasif. |

### 3. Model Comparison
* **K-Means (Selected):** Memberikan segmentasi yang paling seimbang dan mudah diinterpretasikan secara bisnis. (Silhouette Score: ~0.22).
* **Hierarchical Clustering:** Menghasilkan struktur dendrogram yang mengonfirmasi validitas 4 cluster, namun lebih lambat secara komputasi.
* **DBSCAN:** Kurang efektif untuk data dataset ini karena densitas data keuangan yang sangat bervariasi (menghasilkan terlalu banyak noise).

## 🚀 How to Run
1. Clone repository ini.
2. Download dataset `clusteringmidterm.csv`.
3. Jalankan notebook `Midterm_Clustering.ipynb`.
