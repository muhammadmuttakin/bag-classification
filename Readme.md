# 🧠📸 Dokumentasi Implementasi VGG16 dengan Dataset 15.000 Gambar

![Model](https://img.shields.io/badge/Model-VGG16-blue.svg)
![Dataset](https://img.shields.io/badge/Dataset-15.000%20Gambar-lightgrey.svg)
![Split](https://img.shields.io/badge/Train%2FVal%2FTest-80%2F10%2F10-green.svg)
![Framework](https://img.shields.io/badge/Framework-Keras%20%2B%20TensorFlow-orange.svg)

---

## 📝 Deskripsi

Implementasi ini menggunakan model **VGG16** untuk tugas **klasifikasi gambar**. Dataset terdiri dari **15.000 gambar**, yang dibagi menjadi:

- **Training**: 80%
- **Validation**: 10%
- **Testing**: 10%

Pembagian ini bertujuan untuk memastikan model dapat belajar dengan baik dan dievaluasi pada data yang belum pernah dilihat sebelumnya.

---

## ⚙️ Langkah-langkah Implementasi

### 1. 🗂️ Persiapan Dataset

Dataset harus disusun dalam tiga direktori utama:

dataset/
├── train/
│ ├── class1/
│ ├── class2/
│ └── ...
├── validation/
│ ├── class1/
│ ├── class2/
│ └── ...
└── test/
├── class1/
├── class2/
└── ...


> 📌 *Pastikan setiap folder berisi gambar yang telah dikelompokkan sesuai dengan kelasnya.*

---

### 2. 🧼 Preprocessing Data

Gunakan `ImageDataGenerator` dari **Keras** untuk preprocessing:

- **Normalisasi**: Semua gambar dinormalisasi ke [0, 1] (`rescale=1./255`).
- **Augmentasi Data**: Untuk data training saja (rotasi, pergeseran, zoom, flipping horizontal).
- **Validasi dan Test**: Hanya normalisasi, tanpa augmentasi.

---

### 3. 🔁 Membuat Data Generators

Data generators bertugas untuk:

- Memuat gambar dari direktori.
- Mengubah ukuran gambar menjadi **224x224** (ukuran input standar untuk VGG16).
- Menghasilkan batch gambar secara efisien.
- Menyesuaikan format data ke **categorical** (klasifikasi multi-kelas).

---

### 4. 📊 Pembagian Dataset

| Jenis Data | Persentase | Fungsi                        |
|------------|------------|-------------------------------|
| Training   | 80%        | Melatih model                 |
| Validation | 10%        | Tuning dan pemantauan         |
| Testing    | 10%        | Evaluasi akhir                |

---

### 5. 🧪 Penggunaan Generator pada Model

Generator digunakan saat proses:

- **Pelatihan** dengan `model.fit(...)`
- **Validasi** otomatis saat pelatihan
- **Evaluasi akhir** dengan `model.evaluate(...)`

Penggunaan generator memberikan keuntungan:

- Efisiensi memori.
- Dukungan untuk dataset berukuran besar.
- Data dibaca secara batch dan real-time.

---

## ✅ Kesimpulan

Dengan pendekatan ini, model **VGG16** dapat dilatih dan diuji secara **optimal**, efisien, dan siap untuk digunakan dalam skenario klasifikasi gambar berskala besar.

---

> 🚀 *Selanjutnya, model dapat di-save menggunakan `model.save()` dan di-deploy untuk prediksi real-time atau integrasi aplikasi.*
