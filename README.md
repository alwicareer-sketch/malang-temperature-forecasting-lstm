# Peramalan Suhu Udara di Kabupaten Malang Menggunakan Long Short-Term Memory (LSTM)

Repositori ini berisi implementasi penelitian skripsi saya yang berfokus pada prediksi suhu udara harian (Minimum, Maksimum, dan Rata-rata) di wilayah Kabupaten Malang menggunakan pendekatan Deep Learning dengan arsitektur **Long Short-Term Memory (LSTM)**.

## 📌 Ringkasan Proyek
Perubahan suhu udara yang fluktuatif berdampak signifikan pada sektor pertanian di Kabupaten Malang. Penelitian ini bertujuan untuk membangun model peramalan yang akurat guna memberikan informasi preventif bagi masyarakat dan pemerintah setempat. Data yang digunakan bersumber dari **BMKG** untuk periode 1 Januari 2021 hingga 31 Desember 2024.

## 🚀 Tahapan Penelitian
1. **Persiapan Data:** Menggunakan data suhu udara harian sebanyak 1.461 baris.
2. **Preprocessing:** * **Data Cleaning:** Penanganan *missing value* menggunakan metode **Interpolasi Linier**.
    * **Normalisasi:** Transformasi data ke skala [0,1] menggunakan **Min-Max Scaling**.
    * **Segmentasi:** Pembentukan *data window* dengan *timestep* 30 hari untuk memprediksi hari berikutnya.
    * **Partisi Data:** Pembagian data menjadi 80% Training (1 Jan 2021 - 12 Apr 2024) dan 20% Testing (13 Apr 2024 - 31 Des 2024).
3. **Pemodelan:** Konstruksi model LSTM Sequential dengan optimasi **RMSProp**.
4. **Evaluasi:** Pengujian akurasi menggunakan metrik **RMSE** dan **MAPE**.

## ⚙️ Konfigurasi Model Terbaik
Berdasarkan hasil pengujian parameter, arsitektur paling optimal diperoleh dengan konfigurasi:
* **Layers:** 4 Layer (2 LSTM Layers, 1 Dropout Layer, 1 Dense Layer)
* **Hidden Neurons:** 50 unit
* **Batch Size:** 16
* **Epochs:** 200
* **Optimizer:** RMSProp
* **Activation Function:** Tanh & Sigmoid

## 📊 Hasil Evaluasi
Model ini menunjukkan tingkat akurasi yang sangat baik dengan hasil sebagai berikut:

| Variabel Suhu | RMSE | MAPE (%) | Keterangan |
| :--- | :---: | :---: | :--- |
| **Suhu Minimum** | 1.04 | 4.14% | Sangat Akurat |
| **Suhu Maksimum** | 1.00 | 2.66% | Sangat Akurat |
| **Suhu Rata-rata** | 0.69 | 2.16% | Sangat Akurat |

*Hasil peramalan untuk 59 hari ke depan menunjukkan tren peningkatan suhu secara bertahap yang mencerminkan transisi musiman.*

## 🛠️ Tech Stack
* **Language:** Python
* **Library Utama:** TensorFlow/Keras, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn.
* **Tools:** Google Colab.

## 💡 Research Insights
Berdasarkan hasil analisis data dan pemodelan dalam penelitian ini, terdapat beberapa temuan kunci:

* **Kemampuan Prediksi Deep Learning:** Penggunaan arsitektur LSTM terbukti sangat efektif untuk data meteorologi di Kabupaten Malang, mencapai tingkat kesalahan (MAPE) di bawah 5%, yang dikategorikan sebagai model "Sangat Akurat".
* **Tren Kenaikan Suhu:** Hasil peramalan 59 hari ke depan menunjukkan tren kenaikan suhu bertahap pada variabel minimum, maksimum, dan rata-rata. Hal ini mengindikasikan transisi musim serta potensi pengaruh fenomena iklim regional.
* **Analisis Fluktuasi Harian:** Meskipun model mampu menangkap tren besar dan pola musiman dengan baik, terdapat tantangan dalam menangkap fluktuasi harian yang sangat dinamis jika hanya menggunakan fitur suhu saja.
* **Dampak Sektoral:** Prediksi tren kenaikan suhu ini memberikan *insight* penting bagi sektor pertanian di Malang (sebagai lumbung pangan) untuk mengantisipasi gangguan proses fotosintesis dan risiko kekeringan pada tanaman padi.
* **Fenomena Lokal:** Hasil penelitian selaras dengan pola iklim Jawa Timur, di mana periode Januari-Februari menunjukkan transisi suhu yang dapat dipengaruhi oleh anomali cuaca global seperti El Niño.


