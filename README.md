# faceMaskDetector
#  Yüz Maskesi Tespit Sistemi

Derin öğrenme tabanlı, gerçek zamanlı yüz maskesi tespit uygulaması. Python ve TensorFlow/Keras kullanılarak geliştirilmiş bir CNN modeli ile bireylerin maske takıp takmadığını yüksek doğrulukla sınıflandırır.

---

##  Proje Açıklaması

Bu proje; toplu taşıma, ofis ve kamusal alanlarda maske kullanımını otomatik olarak denetlemek amacıyla geliştirilmiştir. Model, **"Maskeli"** ve **"Maskesiz"** olmak üzere iki sınıf üzerinde eğitilmiş olup kullanıcı dostu bir GUI arayüzüne sahiptir.

###  Özellikler
-  Görüntüden maske tespiti (dosya seçimi veya kamera)
-  CNN tabanlı derin öğrenme modeli
-  %95+ doğruluk oranı
-  Tkinter tabanlı kullanıcı arayüzü (GUI)
-  Eğitilen modelin `.h5` formatında kaydedilmesi
-  Eğitim süreci görselleştirme (accuracy & loss grafikleri)

---

##  Kurulum & Gereksinimler

### Gerekli Python Sürümü
Python 3.8+

### Kütüphanelerin Kurulumu
pip install tensorflow opencv-python numpy matplotlib scikit-learn Pillow

---

##  Kullanım Talimatları

### 1. Modeli Eğit
python main.py

### 2. GUI Arayüzünü Başlat
python gui.py

---

##  Model Mimarisi

| Katman | Tür | Detay |
|--------|-----|-------|
| Conv2D + ReLU | Evrişim | 32 filtre, 3x3 kernel |
| MaxPooling2D | Havuzlama | 2x2 |
| Conv2D + ReLU | Evrişim | 64 filtre, 3x3 kernel |
| MaxPooling2D | Havuzlama | 2x2 |
| Conv2D + ReLU | Evrişim | 128 filtre, 3x3 kernel |
| MaxPooling2D | Havuzlama | 2x2 |
| Flatten | Düzleştirme | - |
| Dropout | Düzenlileştirme | %50 |
| Dense + ReLU | Tam Bağlı | 128 nöron |
| Dense + Softmax | Çıkış | 2 sınıf |

**Optimizer:** Adam | **Kayıp:** Categorical Crossentropy | **Metrik:** Accuracy

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

### Confusion Matrix

|  | Tahmin: Maskesiz | Tahmin: Maskeli |
|--|-----------------|----------------|
| **Gerçek: Maskesiz** | 747 ✅ | 32 ❌ |
| **Gerçek: Maskeli** | 36 ❌ | 696 ✅ |

---

##  Kullanılan Teknolojiler

- **TensorFlow / Keras** — Model oluşturma ve eğitim
- **OpenCV** — Görüntü okuma ve işleme
- **NumPy** — Sayısal işlemler
- **Matplotlib** — Görselleştirme
- **Scikit-learn** — Veri bölme ve metrikler
- **Tkinter + Pillow** — Kullanıcı arayüzü

---

##  Lisans
Bu proje eğitim amaçlı geliştirilmiştir.
