# Laporan Praktikum Machine Learning: Diagnosis Bias-Variance & CRISP-DM

Repositori ini berisi penyelesaian tugas praktikum Machine Learning mengenai pemetaan proyek nyata ke dalam kerangka kerja **CRISP-DM** serta analisis diagnosis **Bias-Variance** menggunakan algoritma **Decision Tree Classifier**.

---

## 1. Pemetaan Proyek Nyata ke CRISP-DM
**Studi Kasus:** Prediksi *Customer Churn* pada Industri Telekomunikasi (*Telco Customer Churn*).

Aktivitas konkret yang dilakukan pada 6 fase CRISP-DM:
1. **Business Understanding:** Menentukan tujuan bisnis untuk menekan tingkat *churn* pelanggan dan menetapkan metrik evaluasi utama seperti *F1-Score* dan *Recall*.
2. **Data Understanding:** Mengumpulkan data historis pelanggan (durasi berlangganan, jenis layanan, metode pembayaran, total tagihan) dan menganalisis distribusinya.
3. **Data Preparation:** Melakukan penanganan nilai kosong (*missing values*), *One-Hot Encoding* pada fitur kategorikal, dan penskalaan fitur.
4. **Modeling:** Melatih model klasifikasi *Decision Tree Classifier* dengan berbagai variasi kedalaman pohon (`max_depth`).
5. **Evaluation:** Mengevaluasi performa model menggunakan *learning curve* dan menganalisis kondisi *bias-variance* untuk menghindari *underfitting* atau *overfitting*.
6. **Deployment:** Mengintegrasikan model terbaik ke dalam sistem operasional perusahaan sebagai *early warning system* bagi tim *Customer Relationship Management* (CRM).

---

## 2. Praktikum 2: Diagnosis Bias-Variance (Decision Tree)

### Hasil Perhitungan Model Decision Tree

| max_depth | Train Score | Validation Score | Gap (Train - Val) | Diagnosis |
| :---: | :---: | :---: | :---: | :---: |
| **1** | 0.914 | 0.556 | 0.358 | Underfitting / High Bias |
| **4** | 0.998 | 0.649 | 0.349 | Good Fit (Kedalaman Optimal) |
| **None** | 1.000 | 0.649 | 0.351 | Overfitting / High Variance |

### Analisis Diagnosis:
1. **`max_depth = 1` (Underfitting / High Bias):**
   - Performa validasi paling rendah ($0.556$). Pohon keputusan terlalu dangkal sehingga gagal menangkap pola data dengan baik.
2. **`max_depth = 4` (Seimbang / Optimal):**
   - Memberikan skor validasi tertinggi ($0.649$) dengan skor *train* yang sangat tinggi ($0.998$). Model berada pada titik keseimbangan kompleksitas yang paling baik.
3. **`max_depth = None` (Overfitting / High Variance):**
   - Pohon keputusan tumbuh tanpa batas hingga menghafal seluruh data latih (skor *train* mencapai sempurna $1.000$), namun tidak memberikan peningkatan sama sekali pada skor validasi ($0.649$).
