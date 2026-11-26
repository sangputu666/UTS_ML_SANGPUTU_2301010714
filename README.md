
# Prediksi Total Pengeluaran Wisatawan Nusantara & Mancanegara
### Implementasi Supervised Machine Learning Menggunakan Metode Regresi

## 📌 Deskripsi Proyek

Proyek ini merupakan implementasi **Supervised Machine Learning dengan pendekatan Regresi** untuk memprediksi total pengeluaran wisatawan nusantara dan mancanegara berdasarkan profil perjalanan, karakteristik destinasi wisata, biaya akomodasi, serta kategori asal wisatawan.

Prediksi dilakukan menggunakan beberapa algoritma regresi untuk mengetahui model yang memiliki performa terbaik dalam memperkirakan total pengeluaran wisatawan dalam satuan Rupiah (IDR).

Proyek ini dibuat sebagai bagian dari pemenuhan tugas **Ujian Tengah Semester (UTS) Mata Kuliah Machine Learning — Jalur B (Regresi).**

## 👤 Identitas Penulis

| Keterangan | Informasi |
|---|---|
| Nama | [SANG PUTU SANDYANA JAYA] |
| NIM | [2301010714] |
| Kelas | [XX] |
| Mata Kuliah | Machine Learning |
| Jenis Tugas | UTS Jalur B — Regresi |

## 🎯 Tujuan Proyek

Tujuan dari proyek ini adalah:

1. Memahami karakteristik dataset pariwisata melalui Exploratory Data Analysis (EDA).
2. Melakukan preprocessing terhadap data numerik dan kategorik.
3. Membangun model Machine Learning menggunakan algoritma regresi.
4. Membandingkan performa beberapa algoritma regresi.
5. Mengidentifikasi faktor-faktor yang memengaruhi total pengeluaran wisatawan.
6. Menentukan model terbaik berdasarkan hasil evaluasi.

## 📊 Dataset

https://www.kaggle.com/datasets/luthfimuthathohirin/indonesia-pariwisata-super-prioritas-dpsp

### Variabel Target (Y)

| Variabel | Keterangan |
|---|---|
| `total_tourist_spending_idr` | Total pengeluaran wisatawan dalam Rupiah (IDR) |

### Fitur Prediktor (X)

Fitur yang digunakan dalam proses pemodelan terdiri dari:

**1. Fitur Numerik**
- `trip_duration_days`
- `hotel_room_rate_per_night_idr`
- `travel_party_size`
- `distance_from_origin_km`
- `local_experience_count`
- Dan fitur numerik lainnya yang tersedia pada dataset.

**2. Fitur Kategorik dan Biner**
- `tourist_origin_category`
- `destination_province`
- `accommodation_type`
- `travel_purpose`
- `is_super_priority_destination`
- Dan fitur kategorik lainnya yang relevan.

## ⚙️ Metodologi dan Alur Pengerjaan

Proyek ini menggunakan tahapan Machine Learning sebagai berikut:

### 1. Exploratory Data Analysis (EDA)

Tahap analisis awal untuk memahami karakteristik dataset, meliputi:
- Pemeriksaan dimensi dan struktur dataset.
- Pemeriksaan tipe data.
- Identifikasi missing values.
- Pemeriksaan data duplikat.
- Analisis distribusi variabel target.
- Analisis korelasi antar fitur numerik.
- Visualisasi hubungan fitur terhadap target.

### 2. Data Preprocessing

Tahap persiapan data sebelum proses pemodelan, meliputi:
- Menghapus kolom ID dan metadata yang tidak relevan.
- Menghindari data leakage dengan menghapus fitur turunan target.
- Membagi dataset menggunakan Train-Test Split dengan rasio 80:20.
- Menggunakan `random_state=714`.
- Melakukan standardisasi fitur numerik menggunakan `StandardScaler`.
- Melakukan encoding fitur kategorik menggunakan `OneHotEncoder`.
- Menggabungkan proses preprocessing menggunakan `ColumnTransformer` dan `Pipeline`.

### 3. Modeling

Algoritma regresi yang digunakan dalam penelitian ini adalah:

| Algoritma | Keterangan |
|---|---|
| Linear Regression | Model baseline untuk memprediksi hubungan linear antar variabel. |
| Ridge Regression | Regresi linear dengan regularisasi L2 untuk mengurangi overfitting. |
| Random Forest Regressor | Algoritma ensemble berbasis kumpulan decision tree untuk menangkap hubungan non-linear. |

### 4. Cross Validation

Evaluasi stabilitas model dilakukan menggunakan **5-Fold Cross Validation** untuk mengetahui konsistensi performa model pada beberapa pembagian data.

### 5. Model Evaluation

Evaluasi performa model dilakukan menggunakan tiga metrik:

| Metrik | Keterangan |
|---|---|
| MAE (Mean Absolute Error) | Mengukur rata-rata kesalahan absolut prediksi dalam Rupiah. |
| RMSE (Root Mean Squared Error) | Mengukur kesalahan prediksi dengan memberikan penalti lebih besar pada kesalahan ekstrem. |
| R² Score | Mengukur kemampuan model dalam menjelaskan variasi total pengeluaran wisatawan. |

## 📈 Hasil dan Evaluasi Model

Berikut merupakan tabel perbandingan performa model berdasarkan hasil pengujian pada data test.

| Model | MAE (IDR) | RMSE (IDR) | R² Score |
|---|---:|---:|---:|
| Linear Regression | Rp - | Rp - | - |
| Ridge Regression (α = 1.0) | Rp - | Rp - | - |
| Random Forest Regressor | Rp - | Rp - | - |

> **Catatan:** Nilai evaluasi di atas perlu diperbarui berdasarkan hasil akhir eksekusi notebook.

### Key Insights

Berdasarkan analisis korelasi terhadap dataset, diperoleh beberapa temuan utama:

1. **Durasi Kunjungan (`trip_duration_days`)**

   Memiliki korelasi positif sebesar `r = 0.8342` terhadap total pengeluaran wisatawan. Hal ini menunjukkan bahwa semakin lama durasi perjalanan, pengeluaran wisatawan cenderung semakin tinggi.

2. **Tarif Akomodasi (`hotel_room_rate_per_night_idr`)**

   Memiliki korelasi positif sebesar `r = 0.5279`. Hal ini menunjukkan bahwa tarif akomodasi memiliki hubungan positif dengan total pengeluaran wisatawan.

3. **Ukuran Rombongan (`travel_party_size`)**

   Memiliki korelasi negatif sebesar `r = -0.4362` terhadap pengeluaran per unit perjalanan berdasarkan hasil analisis dataset.

## 📊 Visualisasi

Hasil Exploratory Data Analysis dan evaluasi model disimpan dalam folder `reports/`.

Visualisasi yang dihasilkan meliputi:

| File | Deskripsi |
|---|---|
| `01_distribusi_target.png` | Distribusi total pengeluaran wisatawan. |
| `02_distribusi_numerik.png` | Histogram distribusi fitur numerik. |
| `03_heatmap_korelasi.png` | Heatmap korelasi antar fitur numerik. |
| `04_hubungan_fitur_target.png` | Hubungan fitur utama terhadap variabel target. |
| `05_evaluasi_model.png` | Grafik aktual vs prediksi dan distribusi residual. |

## 📁 Struktur Repository

```text
.
├── data/
│   └── dataset_pariwisata.csv
│
├── notebooks/
│   └── UTS_ML_Jalur_B_Regresi.ipynb
│
├── reports/
│   ├── 01_distribusi_target.png
│   ├── 02_distribusi_numerik.png
│   ├── 03_heatmap_korelasi.png
│   ├── 04_hubungan_fitur_target.png
│   └── 05_evaluasi_model.png
│
├── requirements.txt
└── README.md
```

## 🛠️ Teknologi dan Library

Proyek ini dikembangkan menggunakan bahasa pemrograman Python dengan beberapa library berikut:

- **Python** — Bahasa pemrograman utama.
- **Pandas** — Manipulasi dan pengolahan data.
- **NumPy** — Operasi numerik dan komputasi.
- **Matplotlib** — Visualisasi data.
- **Seaborn** — Visualisasi statistik.
- **Scikit-learn** — Preprocessing, pemodelan, cross-validation, dan evaluasi.
- **Jupyter Notebook** — Lingkungan pengembangan dan analisis.

## 🚀 Instalasi dan Cara Menjalankan

### 1. Clone Repository

```bash
git clone https://github.com/username/nama-repositori.git
```

### 2. Masuk ke Folder Repository

```bash
cd nama-repositori
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Jalankan Jupyter Notebook

```bash
jupyter notebook
```

### 5. Jalankan Notebook

Buka file berikut:

```text
notebooks/UTS_ML_Jalur_B_Regresi.ipynb
```

Jalankan seluruh cell secara berurutan menggunakan menu **Run All**.

Notebook juga dapat dijalankan melalui Visual Studio Code atau Google Colab.

## 📦 Requirements

Library yang dibutuhkan dalam proyek ini:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

## 📝 Kesimpulan

Proyek ini menerapkan metode Supervised Machine Learning dengan pendekatan regresi untuk memprediksi total pengeluaran wisatawan nusantara dan mancanegara.

Tiga algoritma yang digunakan adalah Linear Regression, Ridge Regression, dan Random Forest Regressor. Performa setiap model dibandingkan menggunakan MAE, RMSE, dan R² Score untuk menentukan model dengan kemampuan prediksi terbaik.

Melalui proyek ini, diharapkan dapat diketahui faktor-faktor yang berhubungan dengan pengeluaran wisatawan sehingga hasil prediksi dapat menjadi salah satu bahan pertimbangan dalam perencanaan dan pengembangan sektor pariwisata.

## 📄 Lisensi

Proyek ini dibuat untuk keperluan akademik sebagai pemenuhan tugas Ujian Tengah Semester (UTS) Mata Kuliah Machine Learning.

## 📄 Pernyataan penggunaan AI

Dalam pengerjaan proyek ini, saya menggunakan ChatGPT sebagai alat bantu untuk memahami konsep Machine Learning, menyusun tahapan pengerjaan, membantu penulisan kode Python, memahami hasil evaluasi model, serta mempersiapkan materi presentasi.

Pemeriksaan hasil dilakukan dengan menjalankan kode pada Google Colab, memeriksa output yang dihasilkan, dan mempelajari fungsi serta tujuan setiap tahapan pengerjaan.

Penggunaan AI bertujuan membantu proses pembelajaran dan tidak menggantikan tanggung jawab saya dalam memahami serta menjelaskan hasil proyek.
---

<p align="center">
  <b>Machine Learning — UTS Jalur B (Regresi)</b><br>
  Prediksi Total Pengeluaran Wisatawan Nusantara & Mancanegara
</p>
