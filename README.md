# Perbandingan Analisis ANN dan Random Forest dalam Prediksi Harga Rumah

Project ini membahas penggunaan **Artificial Neural Network (ANN)** dan **Random Forest** untuk memprediksi harga rumah berdasarkan data karakteristik rumah.

Selain membangun kedua model, project ini juga melakukan beberapa tahap preprocessing seperti penanganan missing value, outlier, one-hot encoding, normalisasi, dan transformasi log pada target. Hasil dari kedua model kemudian dibandingkan menggunakan beberapa metrik evaluasi.

## Dataset

Dataset yang digunakan adalah `train.csv` dengan target prediksi:

* `SalePrice` — harga jual rumah

Sebelum masuk ke tahap pemodelan, data melalui beberapa proses preprocessing agar lebih siap digunakan oleh model machine learning.

## Preprocessing

Tahapan preprocessing yang dilakukan:

1. Menghapus kolom `Id`
2. Mengecek data duplikat
3. Menangani missing value
4. Melakukan outlier capping menggunakan metode **IQR**
5. Mengubah data kategorikal menggunakan **One-Hot Encoding**
6. Memisahkan fitur dan target
7. Membagi data menjadi data training dan testing dengan rasio 80:20
8. Melakukan **StandardScaler** untuk normalisasi fitur
9. Melakukan **log transformation** pada target untuk proses training ANN

## Model yang Digunakan

### 1. Artificial Neural Network (ANN)

Model ANN dibuat menggunakan TensorFlow/Keras dengan beberapa hidden layer:

* Dense 256 neuron
* Dense 128 neuron
* Dense 64 neuron
* Dense 32 neuron
* ReLU activation
* Batch Normalization
* Dropout
* Adam optimizer
* Loss: MSE

Training menggunakan **Early Stopping** untuk membantu menghentikan proses ketika performa validasi tidak lagi membaik.

### 2. Random Forest

Model kedua menggunakan `RandomForestRegressor` dengan konfigurasi:

* `n_estimators = 300`
* `max_depth = None`
* `min_samples_split = 2`
* `min_samples_leaf = 1`
* `random_state = 42`

Model ini digunakan sebagai pembanding terhadap performa ANN dalam melakukan prediksi harga rumah.

## Evaluasi

Kedua model dievaluasi menggunakan:

* **MSE (Mean Squared Error)**
* **RMSE (Root Mean Squared Error)**
* **R² Score**

Selain nilai evaluasi, project ini juga menampilkan perbandingan antara harga aktual dan harga hasil prediksi melalui scatter plot.

Terdapat juga pengecekan performa pada data training dan testing untuk melihat apakah terdapat indikasi **overfitting** pada masing-masing model.

## Alur Project

```text
Dataset
   ↓
Data Cleaning
   ↓
Missing Value Handling
   ↓
Outlier Capping
   ↓
One-Hot Encoding
   ↓
Train-Test Split
   ↓
Feature Scaling
   ↓
      ┌───────────────┐
      │               │
     ANN       Random Forest
      │               │
      └───────┬───────┘
              ↓
       Evaluasi Model
              ↓
       Perbandingan Hasil
```

## Tools & Libraries

Project ini dibuat menggunakan Python dengan beberapa library:

* Python
* Pandas
* NumPy
* Scikit-learn
* TensorFlow / Keras
* Matplotlib
* Seaborn

## Project Structure

```text
.
├── train.csv
├── Source_Code_Final_Project.ipynb
└── README.md
```

## Tujuan Project

Project ini dibuat untuk melihat bagaimana dua pendekatan machine learning yang berbeda dapat digunakan untuk kasus **prediksi harga rumah**, sekaligus memahami perbedaan proses dan hasil yang diberikan oleh ANN dan Random Forest.

## Team

**Kelompok 6 — Sains Data 2024B**
* Jeika Antama Syalom Tarigan
* Alifiyanti Putri Nur Azizah
* Muhammad Zikri Widiandra
* Astrid Septya Regita Pramesty
