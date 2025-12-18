# CNN Görüntü Sınıflandırma (Ayakkabı vs Bot)

Bu projede ayakkabı ve bot sınıflarını ayırt etmek için aynı veri seti üzerinde
üç farklı Convolutional Neural Network (CNN) yaklaşımı uygulanmış ve
performansları karşılaştırılmıştır.

---

## Veri Seti

- Sınıflar: `ayakkabi`, `bot`
- Gerçek ortamda çekilmiş görüntüler
- Farklı açı ve ışık koşulları içerir
- Görseller eğitim öncesinde normalize edilmiştir
- Hazır veri seti kullanılmamıştır

---

## Model 1 — Transfer Learning (Fine-Tuning)

Önceden eğitilmiş bir CNN mimarisi kullanılmış ve fine-tuning uygulanmıştır.
Amaç, küçük veri setlerinde güçlü özellik çıkarımı sağlamaktır.

### Eğitim Süreci Grafikleri

**Eğitim & Doğrulama Accuracy**

<img width="855" height="393" alt="image" src="https://github.com/user-attachments/assets/b49d70fd-6bfe-4542-b6a6-21f3605fa562" />

** **

**Eğitim & Doğrulama Loss**

<img width="846" height="393" alt="image" src="https://github.com/user-attachments/assets/69568e27-3cd2-4589-8e9c-b483aa21f447" />

### Sonuçlar
- Validation Accuracy: **%97.92**
- Test Accuracy: **%100**
- Test Loss: **0.011**

**Yorum:**  
Grafikler incelendiğinde modelin ilk epoch’larda hızlı şekilde öğrendiği,
ilerleyen epoch’larda hem eğitim hem doğrulama doğruluğunun stabil şekilde
yüksek kaldığı görülmektedir. Validation loss değerinin düşük olması, modelin
genelleme başarısının güçlü olduğunu göstermektedir.

---

## Model 2 — Basit CNN (Sıfırdan Eğitilen)

Bu modelde klasik CNN mimarisi sıfırdan oluşturulmuş ve eğitilmiştir.
Amaç, daha sade bir yapı ile performans elde etmektir.

### Eğitim Süreci Grafikleri

**Eğitim & Doğrulama Accuracy**

<img width="855" height="393" alt="image" src="https://github.com/user-attachments/assets/550d38a0-3596-400d-a2a7-e187d6b9e399" />

** **
**Eğitim & Doğrulama Loss**

<img width="846" height="393" alt="image" src="https://github.com/user-attachments/assets/da1166eb-e067-449f-8b6b-0c93be2ca585" />


### Sonuçlar
- Training Accuracy: **%98+**
- Validation Accuracy: **%89.58**

**Yorum:**  
Eğitim doğruluğu sürekli artarken doğrulama doğruluğunda dalgalanmalar
gözlemlenmiştir. Validation loss’un artış göstermesi, modelin bazı epoch’larda
overfitting eğilimine girdiğini göstermektedir.

---

## Model 3 — Geliştirilmiş CNN (Augmentation + Optimizasyon)

Bu modelde veri artırımı, Batch Normalization ve Global Average Pooling gibi
ileri teknikler kullanılmıştır. Farklı hiperparametre kombinasyonları denenmiştir.

### Eğitim Süreci Grafikleri (En İyi Deney)

**Eğitim & Doğrulama Accuracy**

<img width="855" height="393" alt="image" src="https://github.com/user-attachments/assets/14a79c53-01df-4da8-8ea3-c6770c558c14" />

** **
**Eğitim & Doğrulama Loss**

<img width="846" height="393" alt="image" src="https://github.com/user-attachments/assets/4264e6e9-a156-4456-99fc-6f293da2e392" />


### Deney Sonuçları

| Deney | Batch | Filtreler | Dropout | LR | Augmentation | Test Accuracy |
|------|-------|-----------|---------|----|--------------|---------------|
| 1 | 32 | 48-96-192 | 0.30 | 0.0010 | Evet | **93.75%** |
| 2 | 32 | 32-64-128-128 | 0.35 | 0.0007 | Evet | **93.75%** |
| 3 | 64 | 64-128-256 | 0.45 | 0.0010 | Evet | 83.33% |
| 4 | 64 | 64-128-256 | 0.40 | 0.0005 | Evet | 62.50% |
| 5 | 32 | 40-80-160 | 0.25 | 0.0010 | Evet | 62.50% |

**Yorum:**  
Grafiklerde doğrulama doğruluğunun epoch’lar arasında dalgalandığı,
buna rağmen genel performansın yüksek olduğu görülmektedir.
Hiperparametre seçiminin model başarısını ciddi şekilde etkilediği
açıkça gözlemlenmiştir.

---

## Genel Karşılaştırma

| Model | Yaklaşım | En İyi Performans |
|------|----------|------------------|
| Model 1 | Transfer Learning | **%100 Test Accuracy** |
| Model 2 | Basit CNN | %89.58 Validation Accuracy |
| Model 3 | Geliştirilmiş CNN | **%93.75 Test Accuracy** |

---

## Sonuç

- Transfer learning kullanılan **Model 1**, test setinde en yüksek başarıyı sağlamıştır.
- **Model 2**, basit yapısına rağmen iyi sonuçlar üretmiş ancak overfitting eğilimi göstermiştir.
- **Model 3**, veri artırımı ve mimari iyileştirmelerle daha dengeli ve güvenilir bir performans sunmuştur.

Bu çalışma, CNN mimarisinde kullanılan farklı yaklaşımların performans üzerindeki
etkisini karşılaştırmalı olarak ortaya koymaktadır.

---

