# Dokumentasi Implementasi VGG16 dengan Dataset 15.000 Gambar

## Deskripsi

Pada implementasi ini, kita menggunakan model **VGG16** untuk melakukan klasifikasi gambar. Dataset yang digunakan terdiri dari 15.000 gambar yang dibagi menjadi tiga bagian utama: **Training (80%)**, **Validation (10%)**, dan **Test (10%)**. Pembagian dataset ini bertujuan untuk memastikan model dapat belajar dengan baik dan dapat dievaluasi pada data yang tidak terlihat sebelumnya.

## Langkah-langkah Implementasi

### 1. Persiapan Dataset

Dataset harus disusun dalam tiga direktori utama yang mewakili masing-masing bagian: training, validation, dan testing. Setiap folder ini berisi subfolder yang sesuai dengan kelas gambar dalam dataset. Struktur direktori yang diinginkan adalah sebagai berikut:


Pastikan setiap folder berisi gambar yang telah dikelompokkan sesuai dengan kelasnya.

### 2. Preprocessing Data

Untuk mempersiapkan data sebelum digunakan pada model VGG16, kita menggunakan **ImageDataGenerator** dari Keras. Preprocessing data ini meliputi:

- **Normalisasi**: Semua gambar akan dinormalisasi dengan cara membagi nilai pixel dengan 255 (rescale), yang mengubah nilai pixel menjadi rentang [0, 1].
- **Augmentasi Data**: Augmentasi data dilakukan pada data training untuk meningkatkan variasi data yang digunakan dalam pelatihan. Augmentasi ini dapat mencakup rotasi, pergeseran, zoom, dan flipping horizontal. Hal ini membantu model dalam generalisasi yang lebih baik terhadap data baru.
- **Validasi dan Test**: Data validasi dan test hanya dinormalisasi tanpa augmentasi karena tujuannya adalah untuk mengevaluasi kinerja model pada data yang tidak dilatih.

### 3. Membuat Data Generators

Setelah melakukan preprocessing, langkah selanjutnya adalah membuat **data generators** untuk masing-masing bagian dataset (training, validation, dan testing). Data generators ini bertanggung jawab untuk:

- Memuat gambar dari direktori yang telah ditentukan.
- Mengubah ukuran gambar agar sesuai dengan ukuran input yang diinginkan oleh model (misalnya 224x224 untuk VGG16).
- Menghasilkan batch data yang siap untuk diproses oleh model.
- Menyediakan data dalam format yang sesuai dengan mode klasifikasi yang dipilih, yaitu **categorical** untuk klasifikasi multi-kelas.

### 4. Pembagian Dataset

Dataset akan dibagi menjadi tiga bagian dengan proporsi sebagai berikut:
- **80% untuk data training**: Digunakan untuk melatih model.
- **10% untuk data validation**: Digunakan untuk memantau kinerja model selama pelatihan dan melakukan tuning hyperparameter.
- **10% untuk data testing**: Digunakan untuk evaluasi akhir model setelah pelatihan selesai.

### 5. Penggunaan Data Generators dalam Model

Setelah generator dibuat, mereka akan digunakan dalam proses pelatihan dan evaluasi model. Generator akan menyediakan data secara batch, memastikan penggunaan memori yang efisien dan memungkinkan pelatihan model dengan ukuran dataset yang besar.

Dengan pendekatan ini, model dapat dilatih dan dievaluasi dengan cara yang efisien dan efektif, memastikan hasil yang optimal pada data yang belum pernah dilihat sebelumnya.

