# CNN Image Classification – Ayakkabı vs Bot

## Veri Seti
- Sınıflar: ayakkabi, bot
- Görseller tarafımdan telefon kamerası ile çekilmiştir
- Farklı açı, ışık ve arka planlarda elde edilmiştir
- Görüntüler 128x128 boyutuna getirilmiştir
- Hazır veri seti kullanılmamıştır

## Model 1 – Transfer Learning (ResNet50)
- ImageNet ön eğitimli ResNet50 kullanılmıştır
- Fine-tuning uygulanmıştır
- Test Accuracy: %88.23

## Model 2 – Basit CNN (CIFAR-10 tarzı)
- Sıfırdan eğitilmiş klasik CNN mimarisi
- Conv2D + MaxPooling katmanları
- Test Accuracy: %91.17

## Model 3 – Geliştirilmiş CNN
- Hiperparametre optimizasyonu yapılmıştır
- ImageDataGenerator ile veri artırımı uygulanmıştır
- BatchNormalization ve GlobalAveragePooling kullanılmıştır
- En iyi Test Accuracy: %93.75

## Kullanılan Kütüphaneler
- TensorFlow / Keras
- NumPy
- Matplotlib
