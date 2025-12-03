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
- 💡 **Penjelasan:** Digunakan untuk memfilter `Student-Faculty Ratio` yang kurang atau sama dengan 40


# 🎯 Hasil data yang didapat:
1. Line Plot (Show full and part time undergraduate in different state)
<img width="998" height="729" alt="1" src="https://github.com/user-attachments/assets/81bfa89a-b0e8-4833-8eae-b0834678c23d" />

2. Histogram (Show acceptance rate for each university)
<img width="998" height="729" alt="2" src="https://github.com/user-attachments/assets/9332ccca-260b-49ff-9d97-5bf1568bb33d" />

3. Bar Chart (Show total cost of each State)
<img width="998" height="729" alt="3" src="https://github.com/user-attachments/assets/bcc30a5f-6c73-4e5a-b4b1-aff9536d5c56" />

4. Box Plot (Show total cost (in and out) for both college type (public and private))
<img width="998" height="729" alt="4" src="https://github.com/user-attachments/assets/bc803350-415f-486d-9013-16e158dc3762" />

5. Scatter Plot (Show comparison between enrolled rate and graduation rate)
<img width="998" height="729" alt="5" src="https://github.com/user-attachments/assets/b43a85b7-ff78-4087-b1c4-371b51a4784e" />

6. Scatter Plot (Show comparison between graduation rate and top 10% new student)
<img width="998" height="729" alt="6" src="https://github.com/user-attachments/assets/363be777-64c1-4499-9a19-c753ea6e0c6f" />

7. Scatter Plot (Show comparison between acceptance rate and top 25% new student)
<img width="998" height="729" alt="7" src="https://github.com/user-attachments/assets/84b4dd39-a92a-4471-8bf6-43006898f958" />

8. Scatter Plot (Show comparison between student faculty ratio and graduation rate)
<img width="998" height="729" alt="8" src="https://github.com/user-attachments/assets/794e71c8-083a-4f35-b5d6-11cfd3bf6be4" />
