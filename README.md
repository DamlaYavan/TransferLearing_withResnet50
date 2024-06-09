# TransferLearing_withResnet50
Bu proje, veri setindeki 16 farklı çiçek sınıfını sınıflandırmak amacıyla yapılmıştır. Bu amaç doğrultusunda, önceden eğitilmiş bir ResNet50 modeli kullanılarak transfer öğrenme tekniği uygulanmıştır. Modelin eğitimi ve doğrulaması için TensorFlow ve Keras kütüphaneleri kullanılmıştır

- ## Veri Seti
Veri seti:  https://www.kaggle.com/datasets/l3llff/flowers/data
Proje, flowers adlı bir veri seti kullanılarak gerçekleştirilmiştir. Bu veri seti, 16 farklı çiçek sınıfına ait resimlerden oluşmaktadır. Her sınıf, farklı sayıda görüntü içermekte olup, bu görüntüler eğitim ve doğrulama seti olarak ikiye ayrılmıştır.Toplam görüntü sayısı 15740 dır.
Sınıflar şunlardır: astilbe, bellflowe , black_eyed_susan , calendula , california_poppy,  carnation , common_daisy, coreopsis , daffodil , dandelion , iris, magnolia , rose , sunflower, tulip , water_lily 

- ## One-Hot Kodlama
Modelimizin eğitimi öncesinde, veri setimizin etiketlerini one-hot kodlama yöntemiyle dönüştürdük. Bu işlem, sınıfların kategorik verilerden sayısal verilere dönüştürülmesini sağlar ve sınıflandırma modellerinin etiketleri daha kolay işlemesine yardımcı olur.
Etiketlerin One-Hot Kodlanması:
One-Hot Kodlama Fonksiyonu: one_hot_encode fonksiyonu, görüntü ve etiketleri alır ve etiketleri one-hot kodlamaya dönüştürür.
Map Fonksiyonu ile Dönüşüm: Eğitim ve doğrulama veri setleri, map fonksiyonu kullanılarak one-hot kodlamaya tabi tutulur.

## RESNET50
ResNet50 (Residual Networks): Derin öğrenme modelleri arasında önemli bir yer tutan ve 50 katmandan oluşan bir yapıdır. Microsoft Research tarafından geliştirilmiş ve ImageNet yarışmasında büyük başarı elde etmiştir. ResNet, özellikle derin sinir ağlarının eğitiminde karşılaşılan "vanishing gradient" (kaybolan gradyan) problemini çözmeyi hedefler.
ResNet50'nin Özellikleri
Derinlik: 50 katmanlı derin bir yapıya sahiptir, bu sayede karmaşık özellikleri öğrenme kapasitesi yüksektir.
Residual (Artık) Bağlantılar: Modelin anahtar özelliklerinden biridir. Bu bağlantılar, katmanlar arasında atlamalar yaparak bilgi akışını kolaylaştırır ve kaybolan gradyan problemini azaltır. Bu sayede daha derin ağların eğitimi mümkün hale gelir.
Önceden Eğitilmiş Ağırlıklar: Model, geniş bir veri seti olan ImageNet üzerinde önceden eğitilmiş ağırlıkları içerir. Bu durum, modelin farklı veri setlerinde kullanılmasını ve transfer öğrenme yoluyla hızlıca adapte olmasını sağlar.
Kullanım Alanları
Görüntü Sınıflandırma: Farklı nesne ve kategorileri tanımlamada kullanılır.
Nesne Tespiti: Görüntü içindeki nesneleri belirler ve sınıflandırır.
Segmentasyon: Görüntülerin belirli bölümlerini ayırt eder.
Görüntü Tanıma ve Analizi: Medikal görüntülerde anomali tespiti gibi alanlarda yaygın kullanılır.


## Modelin Derlenmesi ve Eğitilmesi 
Optimizasyon Algoritması:
Adam optimizasyon algoritması kullanılmıştır. Bu algoritma, öğrenme oranını dinamik olarak ayarlayarak hızlı ve etkili bir eğitim süreci sağlar. Öğrenme oranı 0.001 olarak belirlenmiştir.

Kayıp Fonksiyonu:
Categorical Crossentropy kayıp fonksiyonu kullanılmıştır. Bu fonksiyon, çok sınıflı sınıflandırma problemlerinde yaygın olarak kullanılır ve modelin tahminlerinin doğruluğunu ölçer.

Performans Metrikleri:
Modelin performansını değerlendirmek için accuracy metriği kullanılmıştır. Bu metrik, modelin doğruluğunu hesaplar ve eğitim süreci boyunca modelin başarımını izlemeye olanak tanır.

 Model, yapılandırıldıktan ve derlendikten sonra eğitim sürecine geçilir. Eğitim sırasında model, eğitim veri seti üzerinde 50 epoch boyunca eğitilmiştir. Her epoch'ta model, veri setindeki tüm örnekleri gözden geçirir ve ağırlıklarını güncelleyerek hata oranını azaltmaya çalışır. 

# SONUÇLAR
Modelin eğitimi sonucunda elde edilen sonuçlar aşağıdaki gibidir:

Epoch sayısı arttıkça, eğitim ve doğrulama veri setlerindeki doğruluk oranları artmıştır.
İlk epoch'ta eğitim doğruluğu %71.85 iken, son epoch'ta %97.04'e yükselmiştir.
Doğrulama doğruluğu ise ilk epoch'ta %84.50 iken, son epoch'ta %90.63'e yükselmiştir.
Kayıp değerleri de eğitim süreci boyunca azalmıştır.
Bu sonuçlar, modelin çiçek sınıflarını doğru bir şekilde tanımlayabildiğini ve genelleme yeteneğinin yüksek olduğunu göstermektedir. Ancak, modelin bazı epoch'larda aşırı uydurma (overfitting) eğilimi gösterdiği görülmektedir. Bu durum, modelin daha fazla veriyle eğitilerek veya modelin karmaşıklığının azaltılarak düzeltilebilir.

![ eğitim ve doğrulama kaybı ](![image](https://github.com/DamlaYavan/TransferLearing_withResnet50/assets/116723754/38f78e86-6cac-4fce-b3c1-24e14dac1287)
")

