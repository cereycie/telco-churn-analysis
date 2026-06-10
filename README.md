# Analisis Churn Pelanggan Telekomunikasi

Notebook ini dibuat sebagai bagian dari selection task **Portfolio Program Machine Learning and Operations** Sisters in Tech (SISTECH) 2026 oleh RISTEK Fasilkom UI.

Dataset yang digunakan adalah IBM Telecom Customer Attrition Dataset, berisi data 7.043 pelanggan dengan 21 atribut mulai dari demografi, jenis layanan yang dilangganan, pola pembayaran, hingga status churn.

---

## Struktur Folder

```
telco-cust/
├── notebook.ipynb
└── telco_cust_dataset.csv
```

Tidak ada dependency eksternal selain file CSV yang sudah ada di folder yang sama. Clone repo lalu jalankan notebook langsung dari folder tersebut.

---

## Cara Menjalankan

**Prasyarat:**
- Python 3.8 ke atas
- Jupyter Notebook atau JupyterLab

**Install library yang dibutuhkan:**

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

**Jalankan notebook:**

```bash
jupyter notebook notebook.ipynb
```

Atau buka lewat JupyterLab:

```bash
jupyter lab
```

Pastikan notebook dibuka dari folder yang sama dengan `telco_cust_dataset.csv`. Semua cell bisa langsung dirun dari atas ke bawah tanpa perlu mengubah apapun.

---

## Isi Notebook

### 1. Alasan Pemilihan Dataset
Penjelasan mengapa dataset Telco Customer dipilih dari tiga opsi yang tersedia, dilihat dari relevansi bisnis dan kesesuaian dengan konteks MLOps.

### 2. Eksplorasi Data

**Profiling & Kualitas Data**
Pemeriksaan dimensi, tipe data, dan diagnosis kualitas. Ditemukan satu anomali: kolom `TotalCharges` tersimpan sebagai string dan punya 11 nilai kosong pada baris dengan `tenure = 0`.

**Analisis Univariat**
Distribusi setiap variabel secara individual. Target variabel (`Churn`) tidak seimbang: 73.5% pelanggan tidak churn dan 26.5% churn.

**Analisis Bivariat**
Hubungan antara masing-masing fitur dengan variabel target. Beberapa temuan awal: tipe kontrak dan layanan internet punya perbedaan churn rate yang cukup mencolok antar kategorinya.

**Analisis Multivariat**
Heatmap korelasi antar variabel numerik, heatmap churn rate untuk kombinasi dua variabel kategorik, dan scatter plot tiga variabel sekaligus.

### 3. Insights & Temuan Utama

Lima temuan utama dari eksplorasi data:

| Temuan | Churn Rate |
|--------|------------|
| Kontrak month-to-month | 42.7% |
| Fiber optic tanpa layanan keamanan | 54.6% |
| Pelanggan baru (0-12 bulan) | 47.7% |
| Pengguna electronic check | 45.3% |
| Senior citizen + kontrak bulanan | ~55% |

Selain eksplorasi, notebook juga mencakup pemodelan sederhana menggunakan **Random Forest** untuk melihat fitur mana yang paling berpengaruh terhadap churn. Model mencapai ROC-AUC 0.81 dengan `tenure`, `MonthlyCharges`, `TotalCharges`, dan `Contract` sebagai fitur paling penting.

### 4. Refleksi
Pembahasan proses kerja dari awal sampai akhir, keterbatasan pendekatan yang digunakan, dan arah pengembangan selanjutnya kalau analisis ini dilanjutkan.

---

## Library yang Digunakan

| Library | Kegunaan |
|---------|----------|
| `pandas` | Manipulasi dan eksplorasi data tabular |
| `numpy` | Operasi numerik |
| `matplotlib` | Visualisasi dasar |
| `seaborn` | Visualisasi statistik |
| `scikit-learn` | Preprocessing, pemodelan, dan evaluasi |
| `scipy` | Analisis statistik tambahan |

---

## Dataset

Berisi informasi pelanggan sebuah perusahaan telekomunikasi fiktif, termasuk layanan yang dilangganan, informasi akun, dan apakah pelanggan tersebut berhenti berlangganan (churn) dalam satu bulan terakhir.

---

*Sisters in Tech by RISTEK Fasilkom UI 2026*
