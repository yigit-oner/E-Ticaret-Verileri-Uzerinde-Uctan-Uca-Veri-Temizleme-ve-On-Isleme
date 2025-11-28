# E-Ticaret-Verileri-Uzerinde-Uctan-Uca-Veri-Temizleme-ve-On-Isleme
Ham e-ticaret verisini analiz ve makine öğrenmesi modelleri için hazırladığım kapsamlı veri temizleme projem. Hatalı sütun birleştirme, metin formatlama, para birimi dönüşümü, aykırı değer tespiti ve standartlaştırma adımlarını içerir.

Bu projede, analize uygun olmayan, "kirli" bir veri setini (bozuk_veri.csv) ele alarak, onu baştan sona temizledim ve standartlaştırdım. Amacım, veriyi sadece anlaşılır kılmak değil, aynı zamanda Makine Öğrenmesi (Machine Learning) modellerinin doğru çalışabilmesi için sağlam bir temel oluşturmaktı.

Projenin Amacı
Veri Kalitesini Artırmak: Hatalı girilmiş, yanlış formatlanmış veya anlamsız değerleri düzeltmek.

Standartlaştırma: Metinsel verileri (Şehir, Kategori, Ödeme Yöntemi) tek tip hale getirmek.

Makine Öğrenmesine Hazırlık: Sayısal ve tarihsel değişkenleri doğru veri tiplerine çevirerek modelleme için temel oluşturmak.

İzlediğim Adımlar ve Uyguladığım Teknikler
Proje boyunca karşılaştığım temel sorunlar ve bu sorunlara yönelik geliştirdiğim çözümler aşağıdadır:

1. Veri Yapısı Sorunlarının Çözümü (Hatalı Sütun Başlıkları)

Veriyi yüklediğimde, sütun başlıklarının ve ilk satır verilerinin birbiriyle karışmış olduğunu gördüm. İlk olarak sütun adlarını okunaklı hale getirdim: tüm sütun adlarını küçük harfe çevirdim ve başlarındaki/sonlarındaki boşlukları temizledim.

2. Sayısal Veri Formatlama ve Dönüşüm

Fiyat Temizliği: fiyat sütununda hem "$" hem de " TL" gibi para birimi simgeleri vardı. Bu simgeleri manuel olarak temizledim.

Hata Yönetimi: Temizleme sonrasında, hala sayıya dönüşemeyen değerleri otomatik olarak NaN (boş değer) olarak işaretlemek için Pandas'ın pd.to_numeric fonksiyonunu errors='coerce' parametresiyle kullandım. Bu, programın çökmesini önledi.

3. Kategorik Veri Standartlaştırma

Şehir Düzeltme: sehir sütununda 'ist', 'izmir', 'Izmir' gibi farklı yazım şekilleri mevcuttu. Bu verileri 'İstanbul' ve 'İzmir' gibi standart isimlerle güncelledim.

Metin Düzenleme: odeme_yontemi ve kategori sütunlarındaki fazla boşlukları temizledim ve büyük/küçük harf tutarsızlıklarını giderdim. Özellikle ödeme yöntemlerini 'Kredi Kartı' başlığı altında birleştirdim.

Kategori Büyütme: kategori sütunundaki tüm değerleri büyük harfe çevirerek tek tip bir görünüm elde ettim.

4. Tarih ve Aykırı Değer Tespiti

Tarih Dönüşümü: tarih sütununu analiz edilebilir format olan datetime tipine çevirdim.

Fiyat Aykırı Değerleri: fiyat sütunundaki negatif (0 TL altındaki) fiyatları veri setinden tamamen çıkardım.

Yaş Aykırı Değerleri: yas sütunundaki negatif veya 100'den büyük mantıksız yaş değerlerini NaN olarak işaretledim. Bu, modelleme aşamasında bu değerleri ortalama veya medyan ile doldurmaya hazırlanmak için kritik bir adımdı.
