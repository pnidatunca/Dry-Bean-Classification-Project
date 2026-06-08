# Kuru Fasulye Sınıflandırma Projesi (Dry Bean Classification)

Bu proje, makine öğrenmesi tekniklerini kullanarak 7 farklı kuru fasulye türünü (Barbunya, Bombay, Çalı, Dermason, Horoz, Şeker, Sıra) sadece morfolojik ve geometrik özelliklerine bakarak yüksek doğrulukla sınıflandırmayı amaçlamaktadır.

## Proje Özeti ve Başarı Tablosu

Proje geliştirilirken veri ön işleme, özellik mühendisliği (feature engineering) ve algoritma optimizasyonlarına büyük önem verilmiş; literatürde referans alınan çalışmanın (Köklü & Özkan, 2020) başarı skoru net bir farkla geride bırakılmıştır.

- **Kullanılan Algoritma:** Destek Vektör Makineleri (SVM) - RBF Kernel
- **Referans Makale Doğruluğu:** %93.13
- **Bu Projenin Doğruluğu:** **%96.14** 
- **Ortalama F1-Skoru:** 0.97

## Temel Adımlar

Yüksek başarı oranına ulaşmak için projede şu stratejiler uygulanmıştır:

1. **Aykırı Değer Temizliği (IQR):** Modelin ezber yapmasını (overfitting) engellemek adına, verinin %14'ünü oluşturan 1.968 gürültülü örnek IQR algoritması ile temizlenmiştir.
2. **Özellik Mühendisliği (Feature Engineering):** Türlerin birbirine benzeyen (örtüşen) fiziksel yapılarını ayırmak için mevcut 2D ölçümlerden `Shape_Complexity` ve `Pseudo_Volume` (3 Boyutlu Elipsoid Hacim) gibi yeni matematiksel özellikler türetilmiştir.
3. **Sınıf Dengesizliği Çözümü:** En çok örneğe sahip Dermason (3.546) ile en aza sahip Bombay (522) arasındaki sayısal uçurumun yarattığı taraflılık (bias), SVM algoritmasındaki `class_weight='balanced'` parametresi ile matematiksel olarak giderilmiştir.
4. **Veri Sızıntısını Önleme:** StandardScaler ölçeklendirmesi, Data Leakage riskini sıfıra indirmek adına sadece eğitim (Train) setine *fit* edilmiştir.

## Karmaşıklık Matrisi Özeti
 Modelimiz, azınlık sınıfı olan Bombay'ı %100 kusursuz ayırmayı başarmış olup; morfolojik olarak doğada birbirine en çok benzeyen Dermason ve Sıra türleri arasındaki ince sınırı bile yüksek bir tutarlılıkla öğrenmiştir. Görsel detaylara reports/figures klasöründen ulaşabilirsiniz.
 
##  Referanslar

* **Referans Makale:** Koklu, M., & Ozkan, I. A. (2020). *Multiclass classification of dry beans using computer vision and machine learning techniques.* Computers and Electronics in Agriculture, 174, 105507.
* **Veri Seti:** [UCI Machine Learning Repository - Dry Bean Dataset](https://archive.ics.uci.edu/dataset/602/dry+bean+dataset)
