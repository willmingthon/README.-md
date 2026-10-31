# Proyek Klasifikasi Gambar

## Deskripsi Proyek

Proyek ini merupakan implementasi klasifikasi gambar menggunakan TensorFlow dan Keras untuk mengidentifikasi enam kategori pemandangan pada dataset Intel Image Classification.

Model dibangun menggunakan kombinasi Transfer Learning MobileNetV2 dan Convolutional Neural Network (CNN) yang memenuhi kriteria penggunaan:

- Sequential Model
- Conv2D Layer
- MaxPooling2D Layer
- GlobalAveragePooling2D
- Dense Layer
- Dropout Layer

---

# Dataset

Dataset yang digunakan:

**Intel Image Classification**

Kelas yang digunakan:

1. Buildings
2. Forest
3. Glacier
4. Mountain
5. Sea
6. Street

Total kelas:

```text
6 Kelas
```

---

# Data Preparation

Dataset asli menyediakan folder:

```text
seg_train
seg_test
```

Untuk memenuhi ketentuan proyek, seluruh dataset terlebih dahulu digabungkan menjadi satu dataset kemudian dilakukan pembagian data secara mandiri menggunakan train_test_split.

## Data Splitting

Proporsi data:

```text
Training Set   : 70%
Validation Set : 15%
Test Set       : 15%
```

Pembagian dilakukan menggunakan:

```python
train_test_split(
    stratify=label,
    random_state=42
)
```

---

# Preprocessing

Semua gambar diproses dengan:

```text
Ukuran gambar : 224 x 224 piksel
Color Mode    : RGB
```

Normalisasi dilakukan menggunakan:

```python
ImageDataGenerator(
    rescale=1./255
)
```

---

# Arsitektur Model

Model dibangun menggunakan Sequential Model dengan struktur:

```text
Input
↓
MobileNetV2 (ImageNet Pretrained)
↓
Conv2D (8 Filter, Kernel 1x1)
↓
MaxPooling2D
↓
GlobalAveragePooling2D
↓
Dense (256)
↓
Dropout (0.5)
↓
Dense (6, Softmax)
```

Layer yang digunakan:

- MobileNetV2
- Conv2D
- MaxPooling2D
- GlobalAveragePooling2D
- Dense
- Dropout

---

# Konfigurasi Training

## Optimizer

```text
Adam
```

## Learning Rate

```text
0.0001
```

## Loss Function

```text
Categorical Crossentropy
```

## Metric

```text
Accuracy
```

---

# Callback

Model dilatih menggunakan beberapa callback:

### EarlyStopping

Menghentikan training jika performa validasi tidak meningkat.

### ReduceLROnPlateau

Menurunkan learning rate secara otomatis ketika proses training stagnan.

### ModelCheckpoint

Menyimpan model terbaik berdasarkan validation accuracy.

---

# Hasil Training

Model menghasilkan performa sebagai berikut:

```text
Training Accuracy   : 92.22%
Validation Accuracy : 91.19%
Testing Accuracy    : 91.

47%
```

Hasil tersebut menunjukkan bahwa model berhasil melampaui target minimum akurasi 85%.

---

# Classification Report

Performa setiap kelas:

| Kelas | Precision |
|---------|---------|
| Buildings | 0.90 |
| Forest | 0.99 |
| Glacier | 0.84 |
| Mountain | 0.89 |
| Sea | 0.93 |
| Street | 0.94 |

Ringkasan evaluasi:

```text
Overall Accuracy : 91%
Macro Average    : 92%
Weighted Average : 91%
```

---

# Visualisasi Evaluasi

Notebook menampilkan visualisasi:

- Training Accuracy vs Validation Accuracy
- Training Loss vs Validation Loss
- Classification Report
- Confusion Matrix

Visualisasi digunakan untuk menganalisis proses pembelajaran model dan mendeteksi overfitting maupun underfitting.

---

# Inference

Model mampu melakukan prediksi terhadap gambar baru dan menghasilkan:

```text
Predicted Label
Confidence Score
```

---

# Model Export

Model diekspor ke beberapa format deployment.

## SavedModel

```text
saved_model/
├── saved_model.pb
├── assets/
└── variables/
```

---

## TensorFlow Lite

```text
tflite/
├── model.tflite
└── label.txt
```

Isi label:

```text
buildings
forest
glacier
mountain
sea
street
```

---

## TensorFlow.js

```text
tfjs_model/
├── model.json
└── group1-shard1of1.bin
```

---

# Requirements

Semua dependency tersedia pada file:

```text
requirements.txt
```

Instalasi:

```bash
pip install -r requirements.txt
```

---

# Struktur Submission

```text
submission/
│
├── notebook.ipynb
├── tfjs_model.ipynb
├── README.md
├── requirements.txt
│
├── saved_model/
│   ├── saved_model.pb
│   ├── assets/
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

---

# Teknologi yang Digunakan

- Python
- TensorFlow 2.15.0
- TensorFlow.js 4.22.0
- MobileNetV2
- NumPy
- Pandas
- Matplotlib
- Scikit-Learn
- Pillow
- KaggleHub

---

# Author

Yose Willmingthon Simanjuntak
