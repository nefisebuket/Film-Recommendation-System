# 🎬 Film Öneri Sistemi (Movie Recommendation System)

> **ℹ️ Proje Notu:** Bu çalışma, **Temmuz 2024** tarihinde Bilecik Şeyh Edebali Üniversitesi Bilgisayar Mühendisliği Bölümü **Proje-II** dersi kapsamında tamamlanmıştır.

Bu proje; MovieLens veri seti üzerinde klasik **İşbirlikçi Filtreleme (Collaborative Filtering)** yöntemleri ile **Derin Öğrenme (Deep Learning / Yapay Sinir Ağları)** modellerini uygulayan, kullanıcı tercihlerini modelleyerek puan tahmini yapan ve yöntemlerin performanslarını karşılaştıran bir çalışmadır.

---

## 📌 Proje Özeti ve Kapsam

- **Ürün Tabanlı İşbirlikçi Filtreleme (Item-Based CF):** Filmler arasındaki Pearson korelasyonu hesaplanarak ağırlıklı ortalama ile tahmin yapılması.
- **Kullanıcı Tabanlı İşbirlikçi Filtreleme (User-Based CF):** Kullanıcılar arası Kosinüs benzerliği matrisi çıkarılarak benzer kullanıcı profillerine göre puan tahmini yapılması.
- **Derin Öğrenme Modeli (Deep Learning - MLP Regresyon):** `userId` ve `movieId` girdileri üzerinden yapay sinir ağı kurularak regresyon tahmini yapılması.

---

## 📊 Veri Seti ve Ön İşleme

- **Veri Kümesi:** MovieLens Latest Small (100K)
- **Filtreleme:** Seyrekliği azaltmak ve tutarlılığı artırmak için 100'ün altında oy alan filmler elenmiştir.
- **Son Durum:** 134 film, 597 kullanıcı ve 19.788 derecelendirme.

---

## ⚙️ Model Mimarisi (Derin Öğrenme)

- **Girdi:** `userId`, `movieId` (`MinMaxScaler` ile normalize edilmiştir)
- **Katmanlar:** 3 adet `Dense(16, activation='relu')` ve aralarda `Dropout(0.5)`
- **Çıkış:** `Dense(1)` (Puan regresyonu, 0-5 aralığı)
- **Optimizasyon:** Adam, Loss: MSE, Epoch: 20, Batch Size: 16

---

## 📈 Karşılaştırma Sonuçları (MAE)

| Yöntem | Kapsam | MAE Değeri |
| :--- | :--- | :---: |
| **Ürün Tabanlı Filtreleme** | En benzer 10 film & seçili kullanıcılar | **~0.50 - 0.57** |
| **Derin Öğrenme Modeli** | Ürün tabanlı alt kümede | **~0.45** |
| **Kullanıcı Tabanlı Filtreleme** | En benzer kullanıcı & 10 ortak film | **~0.48 - 0.77** |
| **Derin Öğrenme Modeli** | Kullanıcı tabanlı alt kümede | **~0.56 - 0.90** |
| **Derin Öğrenme Modeli** | Test veri seti geneli (3.958 test örneği) | **0.728** |

---

## 🚀 Kurulum ve Çalıştırma

1. **Repoyu klonlayın:**
   ```bash
   git clone [https://github.com/nefisebuket/Film-Recommendation-System.git](https://github.com/nefisebuket/Film-Recommendation-System.git)
   cd Film-Recommendation-System
