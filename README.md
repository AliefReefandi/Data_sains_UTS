# Data_sains_UTS

[![Buka di Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AliefReefandi/Data_sains_UTS/blob/main/UTS_DATA_SAINS_PLANE.ipynb)

**Analisis dan pemodelan keterlambatan penerbangan dari Houston tahun 2011.** Proyek Ujian Tengah Semester (UTS) mata kuliah Data Sains.

▶️ **Buka langsung di Google Colab:** https://colab.research.google.com/github/AliefReefandi/Data_sains_UTS/blob/main/UTS_DATA_SAINS_PLANE.ipynb

---

## Tentang Proyek

Keterlambatan penerbangan merugikan penumpang, maskapai, dan bandara. Proyek ini mengolah **227.496 data penerbangan** yang berangkat dari dua bandara di Houston, yaitu IAH (George Bush Intercontinental) dan HOU (William P. Hobby), selama tahun 2011. Tujuannya ada dua:

1. Memahami pola keterlambatan penerbangan melalui pembersihan data, analisis eksploratif (EDA), dan analisis korelasi.
2. Membangun model untuk **mengklasifikasikan**, **memprediksi**, dan **mengelompokkan** keterlambatan penerbangan, lalu mengevaluasi dan men-*deploy* model tersebut.

Seluruh pengerjaan ada dalam satu notebook: [`UTS_DATA_SAINS_PLANE.ipynb`](UTS_DATA_SAINS_PLANE.ipynb).

## Pemetaan Capaian Pembelajaran (CLO)

| CLO | Kriteria | Bagian di Notebook |
|---|---|---|
| **CLO 1** – Analisis permasalahan dan penerapan keterampilan & perangkat | Latar belakang, rumusan masalah, tujuan, dan perangkat | Pendahuluan |
| | Struktur data | Step 1 – Data Understanding |
| | Pre-processing (cleaning, validasi, imputasi) | Step 2 – Data Quality Assessment, Step 3 – Data Cleaning |
| | EDA Q1, Q2, Q3 | Step 4 – Data Analysis, EDA Q1–Q3 |
| | Korelasi dan data yang digunakan | Analisis Korelasi Antarvariabel Numerik |
| **CLO 2** – Pembangunan model serta evaluasi & deployment | Klasifikasi | Step 5.1 |
| | Prediksi (regresi) | Step 5.2 |
| | Pengelompokan (clustering) | Step 5.3 |
| | Evaluasi model | Step 5.4 |
| | Deployment | Step 6 |

## Alur Pengerjaan

1. **Data Understanding:** memuat data, struktur 21 kolom, tipe data, missing values, dan status penerbangan.
2. **Data Quality Assessment:** rentang nilai, kategori, validitas tanggal, format waktu HHMM, dan konsistensi durasi.
3. **Data Cleaning:** analisis missing values berdasarkan status penerbangan, deteksi outlier dengan IQR, konsistensi, validitas, duplikasi, dan keputusan imputasi.
4. **Data Analysis:** volume dan keterlambatan berdasarkan maskapai, bulan, hari, rute, dan bandara asal.
5. **EDA dan Korelasi:**
   - **Q1:** distribusi keterlambatan.
   - **Q2:** hubungan keterlambatan keberangkatan dan kedatangan.
   - **Q3:** hubungan jarak dan durasi penerbangan.
   - Heatmap korelasi Pearson antarvariabel numerik.
6. **Pemodelan:**
   - **Klasifikasi:** memprediksi apakah penerbangan terlambat lebih dari 15 menit, dengan Logistic Regression dan Random Forest.
   - **Prediksi (regresi):** memprediksi berapa menit keterlambatan kedatangan, dengan Linear Regression dan Random Forest dibandingkan terhadap baseline.
   - **Pengelompokan:** segmentasi bandara tujuan dengan K-Means, Elbow Method, Silhouette Score, dan visualisasi PCA.
7. **Deployment:** model disimpan dengan `joblib`, dipakai melalui fungsi `prediksi_penerbangan()`, dan dapat dicoba lewat form interaktif `ipywidgets`.

## Ringkasan Hasil

| Analisis | Hasil Utama |
|---|---|
| Kualitas data | 227.496 baris dan 21 kolom tanpa duplikasi. Missing values hanya ada pada penerbangan yang dibatalkan atau dialihkan, sehingga dipertahankan tanpa imputasi. |
| EDA Q1 | Distribusi keterlambatan miring ke kanan. Rata-rata keterlambatan keberangkatan 9,44 menit dan kedatangan 7,09 menit. |
| EDA Q2 | Keterlambatan keberangkatan dan kedatangan berkorelasi sangat kuat (Pearson 0,93). |
| EDA Q3 | Jarak dan durasi penerbangan berkorelasi sangat kuat (Pearson 0,98). |
| Klasifikasi | Model terbaik **Random Forest**: ROC-AUC 0,67 dan Recall 62%, hanya dari informasi jadwal sebelum berangkat. |
| Prediksi | Model terbaik **Linear Regression**: R² 0,93 dan MAE 5,9 menit, dengan RMSE 28% lebih baik daripada baseline. |
| Pengelompokan | **K-Means (k = 3)** membagi 112 bandara tujuan menjadi rute tepat waktu, rute rawan terlambat, dan rute padat jarak dekat-menengah. |

## Cara Menjalankan

1. Klik tombol **Open in Colab** di atas.
2. Jalankan seluruh sel lewat menu **Runtime → Run all**.
3. Selesai. Notebook otomatis mengunduh dataset [`archive.zip`](archive.zip) dari repository ini, mengekstrak `hflights.csv`, lalu menjalankan seluruh analisis dan pemodelan. **Tidak perlu meng-upload file apa pun.**
4. Setelah seluruh sel selesai, model tersimpan di folder `models/` dan form prediksi interaktif dapat dicoba di bagian **Step 6 – Deployment**.

> Dataset yang digunakan adalah **hflights**, yaitu data penerbangan dari Houston tahun 2011. Dataset ini juga tersedia sebagai paket R [`hflights`](https://cran.r-project.org/package=hflights).

## Perangkat yang Digunakan

| Perangkat | Fungsi |
|---|---|
| Python 3 dan Google Colab | Bahasa pemrograman dan lingkungan menjalankan notebook |
| pandas, NumPy | Pengolahan dan manipulasi data |
| Matplotlib, Seaborn | Visualisasi data |
| scikit-learn | Preprocessing, pemodelan, dan evaluasi model |
| joblib, ipywidgets | Penyimpanan model dan form prediksi interaktif (deployment) |

## Struktur Repository

```
Data_sains_UTS/
├── README.md                    # Penjelasan proyek (file ini)
├── UTS_DATA_SAINS_PLANE.ipynb   # Notebook analisis dan pemodelan
└── archive.zip                  # Dataset hflights.csv (diunduh otomatis oleh notebook)
```
