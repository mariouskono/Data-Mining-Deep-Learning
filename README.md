# 🧠 Data Mining & Deep Learning Projects

**Author:** Bertnardo Mario Uskono

**Institution:** Universitas Bhayangkara Jakarta Raya

**Focus Area:** Data Science & Deep Learning

---

## 📘 Deskripsi Umum

Repositori ini berisi dua proyek utama yang mengintegrasikan **teknik Data Mining** dan **Deep Learning** untuk menyelesaikan dua permasalahan berbeda di dunia nyata:

1. **Segmentasi pelanggan dan prediksi skor belanja e-commerce.**
2. **Deteksi anomali (fraud) pada transaksi kartu kredit.**

Kedua proyek ini menunjukkan bagaimana pendekatan *unsupervised learning* (clustering dan anomaly detection) dapat dikombinasikan dengan *deep learning models* untuk meningkatkan performa prediksi dan pemahaman terhadap data.

---

## 📂 Struktur Repositori

```
📦 DataMining-DeepLearning-Projects
├── Bertnardo Mario Uskono - Project 1 DM-DL.ipynb   # Segmentasi Pelanggan & Prediksi Skor Belanja
├── Bertnardo Mario Uskono - Project 2 DM-DL.ipynb   # Deteksi Anomali Transaksi Kartu Kredit
├── README.md                                        # Dokumentasi proyek
```

---

## 🧩 Project 1 – Segmentasi Pelanggan & Prediksi Skor Belanja

**Dataset:** [Mall Customer Segmentation Data – Kaggle](https://www.kaggle.com/datasets)

**Tujuan:** Mengintegrasikan *clustering* (Data Mining) dan *Deep Learning Regression* untuk memahami perilaku dan memprediksi skor belanja pelanggan.

### 🔍 Ringkasan Tahapan

1. **Data Collection & Exploration**
   Dataset bersih tanpa missing values. Variabel `Gender` di-encode numerik, dan korelasi fitur menunjukkan potensi segmentasi berdasarkan pendapatan dan skor belanja.

2. **Clustering (K-Means)**

   * Metode: K-Means
   * Optimal cluster: **5 cluster** (berdasarkan *Elbow Method* dan *Silhouette Score*)
   * Hasil: Segmentasi pelanggan berdasarkan usia, pendapatan, dan skor belanja.

3. **Visualisasi Segmentasi**
   Scatter plot dan analisis mean tiap cluster menunjukkan karakteristik pelanggan di setiap segmen (mis. “High Income, High Spender”, “Low Income, Moderate Spender”, dsb).

4. **Feature Engineering untuk Deep Learning**
   Fitur digunakan: `Age`, `Annual Income`, `Gender_encoded`, `Cluster`.
   Target: `Spending Score`.

5. **Deep Learning Model**

   * Arsitektur: Neural Network *Sequential* (Dense + Dropout)
   * Optimizer: Adam
   * Loss: MSE
   * Metric: MAE
   * Callbacks: EarlyStopping & ReduceLROnPlateau

6. **Hasil Evaluasi**

   * Test MAE ≈ **6.08**
   * R² Score ≈ **0.8742**
   * Model mampu memprediksi skor belanja dengan akurasi tinggi dan stabilitas baik.

7. **Analisis Perbandingan**
   Menambahkan fitur cluster meningkatkan R² secara signifikan → membuktikan bahwa informasi segmentasi dari Data Mining membantu model Deep Learning memahami perilaku belanja lebih baik.

### ✅ Kesimpulan

Kombinasi **K-Means Clustering** dan **Deep Learning Regression** terbukti efektif untuk memahami perilaku konsumen dan memprediksi skor belanja. Pendekatan ini dapat diadaptasi untuk strategi pemasaran berbasis data.

---

## 💳 Project 2 – Deteksi Anomali Transaksi Kartu Kredit

**Dataset:** [Credit Card Fraud Detection – Kaggle](https://www.kaggle.com/datasets)

**Tujuan:** Mendeteksi transaksi penipuan dengan memanfaatkan *Anomaly Detection* (Isolation Forest) dan *Deep Learning Binary Classification.*

### 🔍 Ringkasan Tahapan

1. **Data Exploration & Preprocessing**

   * Identifikasi kelas fraud yang sangat tidak seimbang (~0.393%).
   * Penskalaan fitur `Time` dan `Amount` menggunakan **RobustScaler**.
   * Visualisasi distribusi transaksi, korelasi, dan anomali awal.

2. **Data Mining – Isolation Forest**

   * Teknik: Unsupervised anomaly detection
   * Precision ≈ **81.82%**, Recall ≈ **20.93%**
   * Hasil digunakan untuk membuat fitur baru: `Anomaly_Score`, `Risk_Segment`, dan *feature interaction*.

3. **Handling Imbalanced Data**

   * Teknik: **Random OverSampler**
   * Pembagian data: Stratified Train/Val/Test Split
   * Penskalaan ulang fitur menggunakan **StandardScaler**.

4. **Deep Learning Model**

   * Arsitektur: Dense + Batch Normalization + Dropout + L2 Regularization
   * Loss: Binary Crossentropy
   * Metrics: Accuracy, Precision, Recall
   * Optimizer: Adam
   * Callbacks: EarlyStopping & ReduceLROnPlateau
   * Bobot kelas (*class weight*) digunakan agar kelas fraud lebih diprioritaskan.

5. **Evaluasi Model**

   * Recall: **1.0000** (semua kasus fraud terdeteksi)
   * Precision: **0.4595**
   * ROC-AUC: **0.9997**
   * PR-AUC: **0.8845**
   * Model sangat baik dalam mengenali fraud, meski masih menghasilkan false positive.

6. **Perbandingan Model**

   * **Random Forest** & **XGBoost** dibandingkan dengan model DL.
   * Model tradisional memiliki Precision & F1 yang lebih seimbang, namun DL unggul di Recall.
   * Pilihan model tergantung pada kebutuhan bisnis (minimalkan false negative atau false positive).

7. **Implementasi Real-Time Prediction**

   * Fungsi prediksi transaksi baru dibuat, menghasilkan skor probabilitas fraud, level risiko, dan rekomendasi tindakan.

### ✅ Kesimpulan

Model Deep Learning yang diperkaya oleh *Anomaly Features* dari Isolation Forest mencapai **Recall sempurna** dan ROC-AUC hampir **1.0**, menunjukkan performa yang sangat baik untuk sistem deteksi fraud.
Namun, trade-off Precision perlu disesuaikan dengan konteks bisnis melalui pengaturan threshold dan kebijakan risiko.

---

## ⚙️ Teknologi yang Digunakan

* **Python 3.10+**
* **Google Colab**
* **TensorFlow / Keras**
* **Scikit-learn**
* **Pandas, NumPy, Matplotlib, Seaborn**
* **Imbalanced-learn**
* **Isolation Forest / K-Means**
* **RandomForest, XGBoost**

---

## 🧭 Insight & Pembelajaran

* Integrasi **Data Mining → Deep Learning** meningkatkan performa prediksi secara signifikan.
* Fitur hasil *unsupervised learning* (cluster atau anomaly score) memberikan konteks struktural tambahan pada model DL.
* Penanganan **data imbalance** dan penggunaan **class weights** sangat krusial pada kasus deteksi fraud.
* Evaluasi tidak cukup hanya dengan akurasi — **Precision, Recall, ROC-AUC**, dan **PR-AUC** memberikan gambaran lebih utuh.

---

## 📜 Lisensi

Proyek ini dibuat untuk tujuan akademik dan pembelajaran.
Diperbolehkan untuk digunakan dan dikembangkan kembali dengan mencantumkan sumber:

**© 2025 Bertnardo Mario Uskono**
