# README.-md
# Image Classification Project - Intel Image Classification

## Deskripsi

Proyek ini merupakan implementasi Deep Learning untuk klasifikasi gambar menggunakan TensorFlow dan Keras. Model dilatih untuk mengklasifikasikan gambar ke dalam enam kategori menggunakan dataset Intel Image Classification.

Proyek dibuat sebagai submission kelas Belajar Pengembangan Machine Learning.

---

## Dataset

Dataset yang digunakan:

**Intel Image Classification**

Jumlah kelas:

1. Buildings
2. Forest
3. Glacier
4. Mountain
5. Sea
6. Street

Dataset memiliki lebih dari 10.000 gambar sehingga memenuhi persyaratan proyek.

---

## Struktur Proyek

```text
submission/
│
├── Submision_akhir_Yose.ipynb
├── tfjs_model.ipynb
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

---

## Notebook

### 1. Submision_akhir_Yose.ipynb

Notebook utama untuk proses machine learning.

Tahapan yang dilakukan:

- Import library
- Load dataset
- Data preprocessing
- Data augmentation
- Pembagian Train, Validation, dan Test Set
- Training model CNN
- Transfer Learning menggunakan MobileNetV2
- Evaluasi model
- Plot Accuracy dan Loss
- Classification Report
- Confusion Matrix
- Simpan model Keras
- Konversi ke TensorFlow Lite
- Inferensi model TensorFlow Lite

Output yang dihasilkan:

- Model Keras (.keras)
- SavedModel
- TensorFlow Lite (.tflite)

---

### 2. tfjs_model.ipynb

Notebook untuk konversi model ke TensorFlow.js.

Tahapan yang dilakukan:

- Load model hasil training
- Menghapus layer data augmentation untuk deployment
- Konversi model ke format TensorFlow.js
- Verifikasi hasil konversi

Output yang dihasilkan:

```text
tfjs_model/
├── model.json
└── group1-shard1of1.bin
```

---

## Arsitektur Model

Model menggunakan:

- TensorFlow
- Keras
- MobileNetV2
- GlobalAveragePooling2D
- Dense Layer
- Dropout
- Softmax Output Layer

Struktur utama:

```text
Input (224x224x3)
        ↓
Rescaling
        ↓
MobileNetV2
        ↓
GlobalAveragePooling2D
        ↓
Dense(256, ReLU)
        ↓
Dropout
        ↓
Dense(6, Softmax)
```

---

## Format Model

### SavedModel

```text
saved_model/
├── saved_model.pb
└── variables/
```

### TensorFlow Lite

```text
tflite/
├── model.tflite
└── label.txt
```

### TensorFlow.js

```text
tfjs_model/
├── model.json
└── group1-shard1of1.bin
```

---

## Cara Menjalankan

### Menjalankan Notebook

```bash
jupyter notebook
```

Buka:

```text
Submision_akhir_Yose.ipynb
```

atau

```text
tfjs_model.ipynb
```

---

## Inference TensorFlow Lite

Notebook utama menyertakan proses inferensi menggunakan model TensorFlow Lite sebagai bukti implementasi model setelah deployment.

---

## Author

Yose Willmingthon Simanjuntak
