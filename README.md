# 😷 Yüz Maskesi Tespit Sistemi

Derin öğrenme tabanlı, gerçek zamanlı yüz maskesi tespit uygulaması. Python ve TensorFlow/Keras kullanılarak geliştirilmiş bir CNN modeli ile bireylerin maske takıp takmadığını yüksek doğrulukla sınıflandırır.

---

## 📌 Proje Açıklaması

Bu proje; toplu taşıma, ofis ve kamusal alanlarda maske kullanımını otomatik olarak denetlemek amacıyla geliştirilmiştir. Model, **"Maskeli"** ve **"Maskesiz"** olmak üzere iki sınıf üzerinde eğitilmiş olup kullanıcı dostu bir GUI arayüzüne sahiptir.

### ✨ Özellikler

- 🔍 Görüntüden maske tespiti (dosya seçimi veya kamera)
- 🧠 CNN tabanlı derin öğrenme modeli
- 📊 %95+ doğruluk oranı
- 🖥️ Tkinter tabanlı kullanıcı arayüzü (GUI)
- 💾 Eğitilen modelin `.h5` formatında kaydedilmesi
- 📈 Eğitim süreci görselleştirme (accuracy & loss grafikleri)

---

## 📁 Proje Yapısı

```
mask-detection/
│
├── main.py           # Model eğitimi, değerlendirme ve görselleştirme
├── gui.py            # Tkinter tabanlı kullanıcı arayüzü
├── mask_model.h5     # Eğitilmiş model dosyası
├── requirements.txt  # Gerekli kütüphaneler
├── README.md
│
└── mask-dataset/
    └── data/
        ├── maskeli/      # Maske takan yüz görüntüleri
        └── maskesiz/     # Maske takmayan yüz görüntüleri
```

---

## ⚙️ Kurulum & Gereksinimler

### Gerekli Python Sürümü
```
Python 3.8+
```

### Kütüphanelerin Kurulumu

```bash
pip install -r requirements.txt
```

### `requirements.txt` İçeriği

```
tensorflow>=2.10.0
opencv-python
numpy
matplotlib
scikit-learn
Pillow
```

---

## 🚀 Kullanım Talimatları

### 1. Modeli Eğit

Veri setini `mask-dataset/data/` klasörüne yerleştirdikten sonra:

```bash
python main.py
```

Bu adımda:
- Veri ön işleme yapılır (yeniden boyutlandırma, normalizasyon, one-hot encoding)
- CNN modeli eğitilir (EarlyStopping ile)
- Doğruluk ve kayıp grafikleri görüntülenir
- Confusion matrix ve classification report oluşturulur
- Model `mask_model.h5` olarak kaydedilir

### 2. GUI Arayüzünü Başlat

```bash
python gui.py
```

- **"Resim Seç"** butonuna tıklayın
- `.jpg`, `.jpeg` veya `.png` formatında bir görüntü seçin
- Model, görüntüyü analiz edip sonucu güven yüzdesiyle ekranda gösterir

---

## 🧠 Model Mimarisi

Model, üç evrişimli bloktan oluşan bir CNN mimarisi kullanmaktadır:

| Katman | Tür | Detay |
|--------|-----|-------|
| Conv2D + ReLU | Evrişim | 32 filtre, 3x3 kernel |
| MaxPooling2D | Havuzlama | 2x2 |
| Conv2D + ReLU | Evrişim | 64 filtre, 3x3 kernel |
| MaxPooling2D | Havuzlama | 2x2 |
| Conv2D + ReLU | Evrişim | 128 filtre, 3x3 kernel |
| MaxPooling2D | Havuzlama | 2x2 |
| Flatten | Düzleştirme | - |
| Dropout | Düzenlileştirme | %50 oranında |
| Dense + ReLU | Tam Bağlı | 128 nöron |
| Dense + Softmax | Çıkış | 2 sınıf |

**Derleme Parametreleri:**
- Optimizer: `Adam`
- Kayıp Fonksiyonu: `Categorical Crossentropy`
- Metrik: `Accuracy`

---

## 📊 Model Sonuçları

| Aşama | Doğruluk |
|-------|----------|
| Eğitim | %97 |
| Doğrulama | %95.5 |
| Test | %95 |

### Classification Report

| Sınıf | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| Maskesiz | 0.95 | 0.96 | 0.96 |
| Maskeli | 0.96 | 0.95 | 0.95 |
| **Genel** | **0.96** | **0.95** | **0.95** |

### Confusion Matrix

|  | Tahmin: Maskesiz | Tahmin: Maskeli |
|--|-----------------|----------------|
| **Gerçek: Maskesiz** | 747 ✅ | 32 ❌ |
| **Gerçek: Maskeli** | 36 ❌ | 696 ✅ |

> EarlyStopping ile eğitim 7 epoch'tan sonra durdurulmuş, en iyi ağırlıklar 4. epoch'tan alınmıştır.

---

## 🛠️ Kullanılan Teknolojiler

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10+-orange?logo=tensorflow)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green?logo=opencv)
![Keras](https://img.shields.io/badge/Keras-API-red?logo=keras)

- **TensorFlow / Keras** — Model oluşturma ve eğitim
- **OpenCV** — Görüntü okuma ve işleme
- **NumPy** — Sayısal işlemler
- **Matplotlib** — Görselleştirme
- **Scikit-learn** — Veri bölme ve metrikler
- **Tkinter + Pillow** — Kullanıcı arayüzü

---

## 📄 Lisans

Bu proje eğitim amaçlı geliştirilmiştir.
