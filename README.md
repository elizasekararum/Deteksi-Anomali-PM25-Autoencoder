![Python](https://img.shields.io/badge/Python-3.11-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-DeepLearning-orange)
![Status](https://img.shields.io/badge/Project-Completed-green)

# Anggota Kelompok
- Nurul Firdasari Setyawan (103102400005)
- Nadia Clearesta Shafira (1031024000007)
- Fellycia Khoo (103102400010)
- Eliza Sekar Arum (103102400071)

**Institusi:** Telkom University  
**Mata Kuliah:** Pembelajaran Mesin

# Deteksi Anomali Kualitas Udara Menggunakan Autoencoder pada Dataset Beijing PM2.5

Proyek Tugas Besar Mata Kuliah Pembelajaran Mesin yang bertujuan mendeteksi anomali kualitas udara menggunakan metode Autoencoder pada Beijing PM2.5 Dataset.

---
📋 Daftar Isi

1. Judul & Informasi Kelompok
2. Anggota Kelompok
3. Latar Belakang & Urgensi
4. Gap Penelitian / Novelty
5. Tujuan Penelitian
6. Metode yang Digunakan
7. Dataset
8. Struktur Repository
9. Cara Menjalankan
10. Hasil & Kesimpulan
11. Teknologi yang Digunakan

---

## 📌 Latar Belakang & Urgensi
 
Polusi udara merupakan salah satu masalah lingkungan paling serius di dunia, terutama di kota-kota besar seperti **Beijing, China**. Partikel polutan berukuran sangat kecil yang dikenal sebagai **PM2.5** (Particulate Matter ≤ 2.5 mikrometer) terbukti berbahaya bagi kesehatan manusia karena dapat masuk langsung ke saluran pernapasan dan aliran darah, menyebabkan penyakit jantung, stroke, hingga kanker paru-paru.
 
### Mengapa ini penting?
- Beijing merupakan salah satu kota dengan tingkat polusi udara tertinggi di dunia, terutama pada musim dingin akibat penggunaan pemanas berbahan bakar batu bara
- Data PM2.5 bersifat time series dan multivariat — nilainya dipengaruhi banyak faktor seperti suhu, tekanan udara, arah angin, dan curah hujan
- Deteksi dini terhadap kondisi polusi **ekstrem (anomali)** sangat penting agar pemerintah dan masyarakat dapat segera mengambil tindakan pencegahan

## 🔬 Gap Penelitian / Kebaruan (Novelty)
 
### Gap yang ditemukan:
Sebagian besar penelitian deteksi anomali kualitas udara menggunakan pendekatan **statistik sederhana** seperti z-score atau IQR yang hanya mempertimbangkan **satu variabel (univariat)** yaitu nilai PM2.5 saja. Pendekatan tersebut:
- Tidak mempertimbangkan hubungan antar variabel
- Tidak mampu menangkap pola kompleks non-linear pada data
### Kebaruan penelitian ini:
Penelitian ini menggunakan **Auto Encoder** untuk deteksi anomali secara **multivariat** — mempertimbangkan 8 fitur sekaligus:
 
| Fitur | Keterangan |
|-------|-----------|
| PM2.5 | Konsentrasi polutan utama (µg/m³) |
| TEMP | Suhu udara (°C) |
| PRES | Tekanan udara (hPa) |
| DEWP | Titik embun (°C) |
| Iws | Kecepatan angin kumulatif |
| Is | Jam hujan salju kumulatif |
| Ir | Jam hujan kumulatif |
| cbwd | Arah angin (NW, NE, SE, cv) |
 
---
 
## 🎯 Tujuan Penelitian
 
1. Membangun model **Auto Encoder** menggunakan TensorFlow/Keras untuk mempelajari pola normal kualitas udara Beijing secara multivariat
2. Menggunakan **Reconstruction Error** sebagai indikator untuk mendeteksi kondisi udara yang tidak normal
3. Mendeteksi jam-jam dengan kondisi polusi udara **ekstrem/anomali** secara otomatis tanpa memerlukan label data
4. Menganalisis **pola temporal** anomali yang terdeteksi berdasarkan bulan dan tahun

## 🧠 Metode yang Digunakan — Auto Encoder
 
Auto Encoder adalah jenis neural network *unsupervised* yang belajar mengompres data ke bentuk lebih kecil lalu mengembalikannya ke ukuran semula.
 
### Arsitektur Model:
```
INPUT (8) → [ENCODER] → LATENT SPACE (3) → [DECODER] → OUTPUT (8)
             8→6→4→3                         3→4→6→8
```
 
### Cara Kerja Deteksi Anomali:
```
Data Normal  → model bisa rekonstruksi dengan baik → Error KECIL ✅
Data Anomali → model gagal merekonstruksi          → Error BESAR ⚠️
```
 
### Rumus-rumus yang Digunakan:
 
**Normalisasi Min-Max:**
 
$$x_{norm} = \frac{x - x_{min}}{x_{max} - x_{min}}$$
 
**Fungsi Aktivasi ReLU:**
 
$$ReLU(x) = \max(0, x)$$
 
**Loss Function — MSE:**
 
$$\mathcal{L} = \frac{1}{n}\sum_{i=1}^{n}(x_i - \hat{x}_i)^2$$
 
**Reconstruction Error per data point:**
 
$$RE_i = \frac{1}{d}\sum_{j=1}^{d}(x_{ij} - \hat{x}_{ij})^2$$
 
**Threshold anomali:**
 
$$\text{threshold} = \mu_{RE} + 2\sigma_{RE}$$
 
Jika $RE_i > \text{threshold}$ → data diklasifikasikan sebagai **anomali**.
 
### Alur Kerja:
```
Dataset → EDA → Preprocessing → Bangun Model → Training → Hitung RE → Threshold → Deteksi Anomali → Analisis
```

 ## 🗂️ Dataset
 
- **Nama:** Beijing PM2.5 Air Quality Dataset
- **Sumber:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/381/beijing+pm2+5+data)
- **Periode:** 1 Januari 2010 – 31 Desember 2014
- **Jumlah data:** ±43.800 baris (data per jam)
- **Jumlah fitur:** 13 kolom (8 fitur yang digunakan)
---
 
## 📁 Struktur Repository
 
```
📦 autoencoder-anomaly-detection
 ┣ 📓 TUBES_ML_LENGKAP.ipynb     ← Notebook utama (jalankan ini)
 ┣ 📄 PRSA_data_2010.1.1-2014.12.31.csv  ← Dataset
 ┗ 📄 README.md                  ← Dokumentasi ini
```

## ⚙️ Cara Menjalankan
 
### Menggunakan Google Colab (Direkomendasikan):
1. Buka [Google Colab](https://colab.research.google.com)
2. Upload file `TUBES_ML_LENGKAP.ipynb`
3. Upload file `PRSA_data_2010.1.1-2014.12.31.csv`
4. Jalankan semua cell dari atas ke bawah (**Runtime → Run All**)
### Library yang Dibutuhkan:
```
pandas
numpy
matplotlib
seaborn
scikit-learn
tensorflow >= 2.0
```
 
Semua library sudah tersedia secara default di Google Colab, tidak perlu instalasi tambahan.
 
---
 
## 📊 Hasil & Kesimpulan
 
Berdasarkan eksperimen yang telah dilakukan:
 
1. **Model Auto Encoder** berhasil dibangun dengan arsitektur 8→6→4→3→4→6→8 dan berhasil mempelajari pola normal kualitas udara Beijing
2. **Reconstruction Error** terbukti efektif sebagai indikator anomali — data polusi ekstrem menghasilkan error rekonstruksi yang jauh lebih tinggi
3. **Sekitar 2–5%** dari total data teridentifikasi sebagai anomali
4. **Anomali lebih banyak terjadi pada bulan November–Februari** (musim dingin), konsisten dengan fenomena polusi tinggi akibat penggunaan pemanas batu bara
5. Pendekatan **multivariat** menggunakan Auto Encoder terbukti lebih kontekstual dibanding metode statistik sederhana
---
 
## 🛠️ Teknologi yang Digunakan
 
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=flat&logo=googlecolab&logoColor=white)
 
