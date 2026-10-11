# Crop Recommendation - Klasifikasi Rekomendasi Tanaman

Proyek machine learning untuk merekomendasikan **jenis tanaman** yang paling cocok berdasarkan kondisi tanah (N, P, K, pH) dan cuaca (suhu, kelembapan, curah hujan) menggunakan algoritma **klasifikasi multikelas**.

## Dataset

- **File:** `Crop_recommendation.csv`
- **Jumlah data:** 2.200 baris, 8 kolom
- **Jumlah kelas:** 22 jenis tanaman (masing-masing 100 data, seimbang)
- **Kualitas data:** tidak ada missing value dan tidak ada duplikat

| Kolom | Keterangan | Tipe |
|---|---|---|
| `N` | Kandungan Nitrogen dalam tanah | Fitur |
| `P` | Kandungan Fosfor dalam tanah | Fitur |
| `K` | Kandungan Kalium dalam tanah | Fitur |
| `temperature` | Suhu (°C) | Fitur |
| `humidity` | Kelembapan relatif (%) | Fitur |
| `ph` | Tingkat keasaman tanah | Fitur |
| `rainfall` | Curah hujan (mm) | Fitur |
| `label` | Jenis tanaman yang direkomendasikan | Target |

## 📁 Struktur Proyek

```
.
├── Crop_recommendation.csv
├── crop_classification.ipynb
├── README.md
├── model_crop_rf.pkl        # dihasilkan setelah notebook dijalankan
└── label_encoder.pkl        # dihasilkan setelah notebook dijalankan
```

## ⚙️ Instalasi

1. Pastikan Python 3.9+ sudah terpasang.
2. (Opsional) Buat virtual environment:
```bash
   python -m venv venv
   venv\Scripts\activate        # Windows
   source venv/bin/activate     # macOS / Linux
```
3. Install dependensi:
```bash
   pip install pandas numpy matplotlib seaborn scikit-learn joblib ipykernel
```

## ▶️ Cara Menjalankan

1. Buka folder proyek di **Visual Studio Code** (ekstensi *Python* dan *Jupyter* harus terpasang).
2. Buka `crop_classification.ipynb`.
3. Pilih kernel Python di kanan atas.
4. Klik **Run All** atau jalankan cell satu per satu dari atas ke bawah.

## 🔬 Alur Pengerjaan

1. **Load data** dan eksplorasi (EDA): info data, statistik, distribusi, outlier, korelasi
2. **Preprocessing**: label encoding dan split data 80:20 (stratified)
3. **Pemodelan**: perbandingan 7 algoritma dengan 5-fold cross-validation
   - Logistic Regression, KNN, SVM, Naive Bayes, Decision Tree, Random Forest, Gradient Boosting
4. **Hyperparameter tuning** Random Forest dengan `GridSearchCV`
5. **Evaluasi**: akurasi, classification report, confusion matrix, feature importance
6. **Prediksi** data baru dan **penyimpanan model**

## Hasil

| Metrik | Nilai |
|---|---|
| Akurasi data uji (Random Forest tuned) | ± 99% |

> Hasil dapat berbeda tipis tergantung versi library dan lingkungan.

## Catatan

- Scaling dilakukan di dalam `Pipeline` agar tidak terjadi *data leakage*.
- Akurasi yang sangat tinggi sebagian disebabkan dataset yang bersih dan kelas yang mudah dipisahkan. Performa pada data lapangan sungguhan bisa lebih rendah.

## Pengembangan Lanjutan

- Membuat aplikasi web sederhana (Streamlit / Flask) untuk input kondisi lahan dan menampilkan rekomendasi
- Menguji model dengan data lapangan nyata
- Mencoba XGBoost atau LightGBM

## Penulis

Muhammad Salman Alfarisiy (241011401776).