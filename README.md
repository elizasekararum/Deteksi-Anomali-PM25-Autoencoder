![Python](https://img.shields.io/badge/Python-3.11-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-DeepLearning-orange)
![Status](https://img.shields.io/badge/Project-Completed-green)

# Anggota Kelompok
- Nurul Firdasari Setyawan (103102400005)
- Nadia Clearesta Shafira (1031024000007)
- Fellycia Khoo (103102400010)
- Eliza Sekar Arum (103102400071)

# Mata Kuliah

Pembelajaran Mesin
# Deteksi Anomali Kualitas Udara Menggunakan Autoencoder pada Dataset Beijing PM2.5

Proyek Tugas Besar Mata Kuliah Pembelajaran Mesin yang bertujuan mendeteksi anomali kualitas udara menggunakan metode Autoencoder pada Beijing PM2.5 Dataset.

---
## Daftar Isi

- [Latar Belakang](#latar-belakang)
- [Dataset](#dataset)
- [Tujuan](#tujuan)
- [Metode](#metode)
- [Analisa Hasil](#analisa hasil)
- [Kesimpulan](#kesimpulan)

---

# Latar Belakang

Polusi udara merupakan salah satu permasalahan lingkungan yang berdampak terhadap kesehatan manusia. Salah satu indikator kualitas udara yang sering digunakan adalah PM2.5.

Dengan memanfaatkan teknik Deep Learning, khususnya Autoencoder, penelitian ini bertujuan mendeteksi data anomali yang menunjukkan kondisi kualitas udara tidak normal.

---

# Dataset

Dataset yang digunakan:

* Beijing PM2.5 Dataset
* Periode: 2010–2014
* File: PRSA_data_2010.1.1-2014.12.31.csv

---

# Tujuan

* Menganalisis distribusi PM2.5
* Melakukan preprocessing data
* Melatih model Autoencoder
* Mendeteksi anomali kualitas udara
* Menganalisis reconstruction error

---

# Metode

Metode yang digunakan:

* Data Cleaning
* Exploratory Data Analysis (EDA)
* Feature Encoding
* Normalisasi Data
* Autoencoder
* Anomaly Detection

---

# Tahapan Penelitian

1. Import Library
2. Load Dataset
3. Data Cleaning
4. EDA
5. Encoding CBWD
6. Scaling Data
7. Training Autoencoder
8. Menghitung Reconstruction Error
9. Menentukan Threshold
10. Deteksi Anomali

---

# Analisa Hasil

Berdasarkan hasil eksplorasi data, konsentrasi PM2.5 pada dataset Beijing menunjukkan distribusi yang tidak merata dan memiliki beberapa nilai ekstrem. Hal ini mengindikasikan adanya periode tertentu dengan tingkat polusi udara yang jauh lebih tinggi dibandingkan kondisi normal.

Model Autoencoder kemudian dilatih untuk mempelajari pola normal dari data kualitas udara. Setelah proses pelatihan selesai, reconstruction error dihitung untuk setiap data. Sebagian besar data memiliki nilai error yang rendah, yang menunjukkan bahwa model mampu merekonstruksi pola normal dengan baik.

Data yang memiliki reconstruction error melebihi threshold dikategorikan sebagai anomali. Hasil visualisasi menunjukkan bahwa titik-titik anomali umumnya muncul pada kondisi dengan konsentrasi PM2.5 yang sangat tinggi atau berbeda signifikan dari pola umum data.

Secara keseluruhan, Autoencoder berhasil digunakan untuk mendeteksi data kualitas udara yang tidak normal tanpa memerlukan label anomali pada proses pelatihannya.

# Kesimpulan

Berdasarkan penelitian yang telah dilakukan, dapat disimpulkan bahwa metode Autoencoder mampu digunakan untuk mendeteksi anomali pada data kualitas udara Beijing PM2.5. Proses preprocessing yang meliputi penanganan missing value, encoding variabel kategorikal, dan normalisasi data berhasil mempersiapkan data untuk proses pelatihan model.

Hasil analisis menunjukkan bahwa Autoencoder dapat mempelajari karakteristik data normal dengan baik, yang ditunjukkan oleh rendahnya reconstruction error pada sebagian besar data. Dengan menggunakan threshold tertentu, model mampu mengidentifikasi sejumlah data yang memiliki pola berbeda dari kondisi normal dan mengelompokkannya sebagai anomali.

Deteksi anomali yang dihasilkan dapat digunakan sebagai indikator awal untuk mengenali kondisi polusi udara ekstrem. Oleh karena itu, metode Autoencoder memiliki potensi yang baik untuk diterapkan dalam sistem pemantauan kualitas udara secara otomatis, terutama pada kasus yang tidak memiliki label data anomali.
