# UTS Machine Learning - Linear & Logistic Regression

---

## 👤 Identitas Mahasiswa

* **Nama**   : Virgian Nanda Refaldi
* **NIM**    : 241011402646
* **Kelas**  : Reg C (sabtu)
* **RANDOM_STATE** : 46

---

## 📂 Struktur Repositori

```text
uts-machine-learning-241011402646/
├── README.md            # Dokumentasi proyek, identitas, dan ringkasan hasil
├── tugas_UTS.ipynb      # Notebook pengerjaan tugas utama (sudah di-Run All)
├── Ads_Data.csv         # Dataset untuk Bagian A (Linear Regression)
└── Email_Data.csv       # Dataset untuk Bagian B (Logistic Regression)
```

---

## 📊 Ringkasan Hasil Eksperimen

### Bagian A – Linear Regression (Ads_Data.csv)

Eksperimen menganalisis pengaruh **Biaya Iklan** terhadap **Penjualan** menggunakan Normal Equation dan Gradient Descent.

* **Persamaan Model Regresi**:
  $$\hat{y} = 28.4656 + 9.0222 \cdot X$$
  * **Intercept ($b$)**: `28.4656`
  * **Koefisien ($m$)**: `9.0222`
* **Hasil Evaluasi Model (Data Testing)**:
  * **MAE**  : `2.7904`
  * **MSE**  : `13.1982`
  * **RMSE** : `3.6329`
  * **$R^2$ Score** : `0.9863` ($98.63\%$)
* **Eksperimen Learning Rate (GD)**:
  * `0.001`: Terlalu lambat konvergen.
  * `0.02` : Konvergen optimal dan memberikan hasil identik dengan Normal Equation.
  * `0.1`  : Divergen (meledak/overflow).

---

### Bagian B – Logistic Regression (Email_Data.csv)

Eksperimen mengklasifikasikan email **Spam (1)** dan **Bukan Spam (0)** berdasarkan fitur **Jumlah Link** dan **Jumlah Kata Promo**.

* **Persamaan Logit**:
  $$P(\text{Spam}) = \sigma(-10.4080 + 0.8670 \cdot \text{JumlahLink} + 0.8944 \cdot \text{KataPromo})$$
* **Eksperimen Threshold**:

| Threshold | Accuracy | Precision | Recall | F1-Score | FP | FN |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| `0.3` | 0.7333 | 0.7500 | 0.7500 | 0.7500 | 2 | 2 |
| `0.5` | 0.8000 | 0.8571 | 0.7500 | 0.8000 | 1 | 2 |
| **`0.7` (Dipilih)** | **0.8667** | **1.0000** | **0.7500** | **0.8571** | **0** | **2** |

> **Catatan Pemilihan Threshold**: Threshold `0.7` dipilih untuk memastikan **Precision = 1.0000** (False Positive = 0), sehingga meminimalkan risiko email penting pengguna salah masuk ke folder spam.

---

## 🧠 Ringkasan Pemahaman Konsep (Bagian C)

1. **Logistic Regression sebagai Klasifikasi**: Disebut klasifikasi karena tujuannya memprediksi label kategori diskrit. Fungsi **sigmoid** memetakan output linier kontinu ke rentang probabilitas $(0, 1)$.
2. **Normal Equation vs Gradient Descent**: Normal Equation menyelesaikan parameter secara langsung/analitis ($O(n^3)$), sedangkan Gradient Descent secara bertahap (iteratif). Gradient descent lebih efisien untuk dataset berskala sangat besar.
3. **Overfitting & Data Testing**: Evaluasi pada data testing menguji kemampuan generalisasi model pada data yang belum pernah dilihat. Overfitting terjadi ketika model menghafal pola data training hingga berkinerja buruk pada data testing.
4. **MSE vs Log Loss**: MSE digunakan pada Linear Regression karena output berupa variabel kontinu. Logistic Regression menggunakan Log Loss untuk menjaga fungsi biaya tetap cembung (*convex*) sehingga mudah dioptimasi.
5. **Variasi Hasil**: Hasil angka berbeda-beda antar mahasiswa karena penggunaan `RANDOM_STATE` berbasis 2 digit NIM terakhir yang menyebabkan pembagian indeks *train-test split* bervariasi.

---

## 💻 Cara Menjalankan Notebook

1. **Clone Repositori**:
   ```bash
   git clone https://github.com/USERNAME_ANDA/uts-machine-learning-241011402646.git
   cd uts-machine-learning-241011402646
   ```

2. **Jalankan via VS Code atau Jupyter Notebook**:
   * Buka folder di Visual Studio Code.
   * Pastikan library bawaan telah terinstall:
     ```bash
     pip install pandas numpy matplotlib
     ```
   * Buka file `tugas_UTS.ipynb`.
   * Pilih Kernel Python yang aktif dan jalankan seluruh sel dengan menekan tombol **Run All**.