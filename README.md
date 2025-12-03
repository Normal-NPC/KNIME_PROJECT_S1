# 📖 KNIME Workflow: University Dataset Analysis

## 🙋‍♂️ Introduction
Hari ini, saya memodifikasi dataset yang berisi data universitas. Tujuan dari analisis ini adalah:
* **Data Cleaning:** Membersihkan data (*remove missing value* & *renaming*).
* **Calculation:** Menghitung nilai-nilai baru untuk keperluan visualisasi.
* **Grouping:** Melakukan pengelompokan data untuk visualisasi tertentu.
* **Data Transformation:** Mengubah tipe data, seperti `CollegeType` dari angka (*number*) menjadi teks (*string*) agar lebih mudah dibaca.

## ⚙️ Workflow dan Fungsi Node

### 1️⃣ CSV Reader
- 💭 **Fungsi:** Membaca file `Universities.csv`.
- 💡 **Penjelasan:** Node ini berfungsi untuk mengimpor seluruh dataset universitas ke dalam workflow KNIME agar siap diproses.

### 2️⃣ Missing Value
- 💭 **Fungsi:** Menangani data yang kosong (*missing value*).
- 💡 **Penjelasan:** Saya memilih untuk menghapus baris yang memiliki *missing value* daripada mengisinya dengan nilai default (seperti "0" atau rata-rata). Hal ini dilakukan karena variabel vital seperti "nilai siswa" atau "biaya kuliah" sangat spesifik untuk setiap universitas. Mengisinya dengan angka asumsi (imputasi) dapat menyebabkan bias dan merusak akurasi analisis data secara keseluruhan.

### 3️⃣ Column Renamer
- 💭 **Fungsi:** Mengubah nama kolom (*rename*).
- 💡 **Penjelasan:** Mengubah nama-nama kolom yang sebelumnya ambigu atau sulit dimengerti menjadi nama yang lebih deskriptif dan jelas.

### 4️⃣ Rule Engine
- 💭 **Fungsi:** Memodifikasi nilai dalam kolom berdasarkan logika/aturan tertentu.
- 💡 **Penjelasan:** Digunakan untuk mengubah nilai pada kolom `CollegeType` agar lebih informatif. Nilai angka diubah menjadi teks: **1** menjadi "Public" dan **2** menjadi "Private".

### 5️⃣ Math Formula
- 💭 **Fungsi:** Melakukan perhitungan matematis untuk membuat kolom baru.
- 💡 **Penjelasan:** Digunakan untuk menghitung metrik baru yang tidak ada di data mentah, seperti `Acceptance_Rate`, `Enroled_Rate`, `Total_InState`, dan `Total_OutState`.

### 6️⃣ Color Manager
- 💭 **Fungsi:** Memberikan kode warna pada data berdasarkan kategori tertentu.
- 💡 **Penjelasan:** Digunakan untuk membedakan warna berdasarkan `CollegeType` (Public vs Private). Ini akan sangat membantu saat memvisualisasikan data, terutama pada **Scatter Plot**.

### 7️⃣ Joiner
- 💭 **Fungsi:** Menggabungkan data dari dua percabangan node yang berbeda.
- 💡 **Penjelasan:** Digunakan untuk menyatukan kembali kolom-kolom hasil perhitungan (*Math Formula*) yang terpisah, sekaligus memastikan hanya data yang relevan yang diteruskan untuk visualisasi akhir.

### 8️⃣ Row Filter
- 💭 **Fungsi:** Menyaring baris data (*row*) yang memenuhi kriteria tertentu.
- 💡 **Penjelasan:** Digunakan untuk memfilter universitas berdasarkan rasio mahasiswa dan fakultas (*Student-Faculty Ratio*), misalnya hanya menampilkan universitas dengan rasio ~40.
