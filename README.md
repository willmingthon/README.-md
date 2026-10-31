# Proyek Klasifikasi Gambar: Intel Image Classification

## Informasi Proyek

Proyek ini membangun model klasifikasi gambar menggunakan dataset Intel Image Classification dengan pendekatan Convolutional Neural Network (CNN) dan Transfer Learning MobileNetV2. Dataset dibagi secara manual menjadi training, validation, dan testing set. Model kemudian dikonversi ke format SavedModel, TensorFlow Lite, dan TensorFlow.js sesuai kriteria submission Dicoding.

**Nama:** Yose Willmingthon Simanjuntak

**Dataset:** Intel Image Classification

**Sumber Dataset:**
https://www.kaggle.com/datasets/puneet6060/intel-image-classification

## Deskripsi Dataset

Dataset Intel Image Classification merupakan dataset klasifikasi citra yang berisi gambar pemandangan alam dan lingkungan yang terbagi ke dalam enam kelas:

- Buildings
- Forest
- Glacier
- Mountain
- Sea
- Street

Dataset terdiri dari sekitar 25.000 gambar RGB.

## Data Preparation

Pada proyek ini dilakukan beberapa tahapan persiapan data:

1. Menggabungkan seluruh data dari folder train dan test bawaan dataset.
2. Melakukan pembagian dataset secara manual menggunakan train_test_split.
3. Membagi dataset menjadi:
   - Training Set : 70%
   - Validation Set : 15%
   - Test Set : 15%
4. Melakukan preprocessing dengan mengubah ukuran gambar menjadi 224x224 piksel.
5. Melakukan normalisasi piksel menggunakan rescale 1/255.
6. Menerapkan data augmentation pada data training:
   - Random Rotation
   - Horizontal Flip
   - Zoom

## Arsitektur Model

Model dibangun menggunakan TensorFlow dan Keras dengan kombinasi:

- Sequential Model
- Conv2D
- MaxPooling2D
- MobileNetV2 (Transfer Learning)
- GlobalAveragePooling2D
- Dense Layer
- Dropout Layer

Struktur utama model:

- Conv2D(32)
- MaxPooling2D
- MobileNetV2
- GlobalAveragePooling2D
- Dense(256)
- Dropout(0.5)
- Dense(6, Softmax)

## Callback

Model menggunakan callback:

- EarlyStopping
- ReduceLROnPlateau
- ModelCheckpoint

## Hasil Pelatihan

Hasil terbaik yang diperoleh:

- Training Accuracy : 92.06%
- Validation Accuracy : 91.42%
- Testing Accuracy : 90.90%

Model berhasil melampaui target minimum akurasi 85% sesuai kriteria submission.

## Visualisasi

Notebook menampilkan:

- Distribusi dataset
- Contoh gambar dataset
- Grafik Accuracy
- Grafik Loss
- Classification Report
- Confusion Matrix

## Inference

Model berhasil melakukan prediksi pada gambar baru.

Contoh hasil inferensi:

- Predicted Class : buildings
- Confidence : 99.72%

## Format Model yang Dihasilkan

### SavedModel

```text
saved_model/
├── saved_model.pb
└── variables/
```

### TensorFlow Lite

```text
model.tflite
label.txt
```

### TensorFlow.js

```text
tfjs_model/
├── model.json
└── group1-shard1of1.bin
```

## Requirements

Dependency proyek tersedia pada file:

```text
requirements.txt
```

## Cara Menjalankan Project

1. Install dependency:

```bash
pip install -r requirements.txt
```

2. Jalankan notebook:

```text
notebook.ipynb
```

3. Training model.

4. Lakukan evaluasi model.

5. Jalankan proses inferensi.

## Struktur Submission

```text
submission/
├── notebook.ipynb
├── README.md
├── requirements.txt
│
├── saved_model/
│   ├── saved_model.pb
│   └── variables/
│
├── tflite/
│   ├── model.tflite
│   └── label.txt
│
└── tfjs_model/
    ├── model.json
    └── group1-shard1of1.bin
```
