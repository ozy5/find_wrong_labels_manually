# find_wrong_labels_manually
Daha önce labellanmış bir datasetin temizliği yapılırken dikkat edilmesi gereken hususlar.


## Datasette bulunan hata türlerinin model eğitimine etkisi

### !!!!!!!!!!!!! Yanlış Label:
Yanlış labellanmış (drone yerine helikopter, kuş yerine uçak...) resimlerin datasette bulunması, modelin kendini eğitirken en büyük engel sayılabilir ve modelin gerçek performansının ölçülememesine yol açar.\
\
Yanlış label örneği:\
![Yanlış label](negatif/yanlış_label/yanlış_labellanmış_resimler_4.jpg "Yanlış label")

### !!!!!!!!!!! Eksik Label
Eksik labellar, model doğru tahmin yapmasına rağmen ona yanlış yaptığını düşündürüp modelin performansını oldukça düşürmekte ve modelin gerçek performansının ölçülememesine yol açmakta.\
\
Eksik label örneği:\
![Eksik Label](negatif/eksik_label/eksik_labellanmış_resimler_3.jpg "Eksik Label")

### !!!!!!!!! Geniş label
Olması gerekenden daha geniş labellar, gerçek resimle alan farkının ne kadar büyük olmasına bağlı olarak modelin daha isabetli tahminler yapmasını çok zorlaştırmakta ve özellikle mAP 0.5-0.95 değerini olduğundan daha düşük göstermekte.\
\
Geniş label örneği:\
![Geniş label](negatif/geniş_annotation/büyük_labellanmış_resimler_4.jpg "Geniş label")
IoU değeri (kesişim alanı bölü birleşim alanı) KESİNLİKLE 0.5 altına düşmemeli.\
Yani yapılabilecek en iyi tahmin ile resimdeki label arasındaki IoU oranı 0.5 den yüksek olmalı.\
\
Örnek IoU değerleri:\
![IoU değeri örnekleri](IoU_örnekleri/IoU_sample_2.png "IoU değeri örnekleri").
![IoU değeri örnekleri](IoU_örnekleri/IoU_sample_1.png "IoU değeri örnekleri").
![IoU değeri örnekleri](IoU_örnekleri/IoU_sample_3.png "IoU değeri örnekleri").
### !!!!! Ayırt etmesi zor
Eğer bir insan label'a baktığında kuş mu, uçak mı, drone mu yoksa süperman mi ayırt etmekte çok zorlanıyorsa ve "Bu yüksek ihtimalle drone'dur ya" diyemiyorsa, bu tarz labellar modelin sınıflar arası ayrım yapabilme yeteneğini azaltmakta.\
Not: Eğer yapılan modeldeki asıl amaç bir sınıfı öncelikli olarak tespit etmekse ve bu sınıf olduğundan emin olunamayan labellar bulunuyorsa bunlar datasete dahil edilebilir.\
\
Ayırt etmesi zor label örneği:\
![Ayırt etmesi zor label](negatif/ayırt_etmesi_zor/karıştırılabilecek_fazla_zor_resimler_9.jpg "Ayırt etmesi zor label")

### !!!! Fazla karışık
Bu tarz resimler eğer tamamen doğru labellanmışsa amacına bağlı olarak modeli biraz geliştirebileceği gibi, modelin çoğunlukla karşılaşacağı senaryolarda performansını ve confidence'ını azaltır.\
Not: Bu aşamada modelin karşılaşacağı senaryoların kompleks olup olmayacağı önem taşır.\
\
Fazla karışık label örneği:\
![Fazla karışık label](negatif/fazla_karışık/karışık.jpg "Fazla karışık label")

### !! Çok sentetik resimler
Eğer yapay olarak oluşturulmuş resim örnekleri, gerçekten uzaklaşmışsa ve modelin karşılaşacağı senaryolardan farklı gözüküyorsa datasete tercihen konulmamalıdır.\
\
Çok sentetik resim örneği:\
![Çok sentetik resim](negatif/çok_yapay_label/fazla_sentetik_resimler_4.jpg "Çok sentetik resim")









