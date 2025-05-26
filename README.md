# 🧠 Stroke Prediction using Logistic Regression

Proyek ini bertujuan untuk membangun model machine learning yang dapat memprediksi kemungkinan terjadinya **stroke** berdasarkan data demografis dan medis seseorang. Model baseline yang digunakan adalah **Logistic Regression**, dengan berbagai teknik preprocessing untuk meningkatkan akurasi dan generalisasi.

---

## 📁 Dataset

Dataset berisi informasi personal dan medis dari pasien, dengan kolom-kolom sebagai berikut:

| Kolom             | Deskripsi                                            |
|------------------|-----------------------------------------------------|
| `id`              | ID unik setiap individu                             |
| `gender`          | Jenis kelamin                                       |
| `age`             | Umur pasien                                         |
| `hypertension`    | Riwayat tekanan darah tinggi (0 = Tidak, 1 = Ya)    |
| `heart_disease`   | Riwayat penyakit jantung (0 = Tidak, 1 = Ya)        |
| `ever_married`    | Pernah menikah atau tidak                           |
| `work_type`       | Jenis pekerjaan                                     |
| `Residence_type`  | Tinggal di area urban atau rural                    |
| `avg_glucose_level` | Rata-rata kadar glukosa dalam darah              |
| `bmi`             | Body Mass Index (BMI)                               |
| `smoking_status`  | Status merokok                                      |
| `stroke`          | Target (0 = Tidak Stroke, 1 = Stroke)               |

---

## 🧪 Model yang Digunakan

- **Logistic Regression** dari `scikit-learn` sebagai model baseline.
- Fitur kategorikal diencode menggunakan `LabelEncoder`.
- Fitur numerik seperti `age`, `avg_glucose_level`, dan `bmi` di-*scale* dengan `StandardScaler`.
- Masalah **kelas tidak seimbang** (class imbalance) diatasi dengan:
  - Menambahkan parameter `class_weight='balanced'`
  - (Opsional) menggunakan teknik **SMOTE** untuk oversampling

---

## 🧰 Tahapan Analisis

1. **Data Cleaning**
   - Mengatasi missing values
2. **Encoding**
   - Konversi fitur kategorikal menjadi numerik dengan `LabelEncoder`
3. **Scaling**
   - Menormalkan fitur numerik agar setara dengan `StandardScaler`
4. **Split Data**
   - `train_test_split` (80% train, 20% test)
5. **Training**
   - Logistic Regression dengan `class_weight='balanced'`, `max_iter=1000`
6. **Evaluasi**
   - Menggunakan `confusion_matrix` dan `classification_report`

---

## 🧠 Hasil Evaluasi Model (Sebelum Balancing & Scaling)

Confusion Matrix:
[[929   0]
 [ 53   0]]

Classification Report:
              precision    recall  f1-score   support
           0       0.95      1.00      0.97       929
           1       0.00      0.00      0.00        53

    accuracy                           0.95       982
   macro avg       0.47      0.50      0.49       982
weighted avg       0.89      0.95      0.92       982