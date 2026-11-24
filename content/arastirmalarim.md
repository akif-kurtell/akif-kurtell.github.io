---
title: "Kararlı Eşleşmenin Matematiği: Gale-Shapley Algoritması ve Okul Yerleştirme"
date: 2026-11-24
draft: false
summary: "İki taraflı katı tercih sıralamalarında kararlı eşleşme kuramını, Gale-Shapley ertelemeli kabul mekanizmasını ve okul/üniversite yerleştirme uygulamalarındaki temel ince noktaları ele alan çalışma notu."
tags: ["matematik", "algoritmalar", "eslesme-teorisi", "mat231", "gale-shapley"]
---

> **Çalışma Dokümanı:** Bu yazıya temel oluşturan tam metni ve biçimsel detayları incelemek için [PDF'i Aç](/Gale-Shapley_Algoritması.pdf).

İki tarafın birbirine karşı katı tercih sıralamalarına sahip olduğu durumlarda nasıl "adil" ve bozulmaya dayanıklı bir eşleşme kurulur? İster üniversite kontenjanlarına aday yerleştirmekten ister iş piyasasındaki eşleşmelerden söz edelim, sezgisel görünen pek çok kural pratikte **kararsızlık** üretir: Bir adayın ve bir kurumun mevcut eşleşmelerinden vazgeçip birbirini tercih etmesi sistemi baştan aşağı sarsar.

1962 yılında **David Gale** ve **Lloyd Shapley** tarafından ortaya konan **Gale-Shapley Algoritması** (*Ertelemeli Kabul / Deferred Acceptance*), tam da bu sorunu matematiksel kesinlikle çözen temel yapı taşlarından biridir. Bu metin, **Galatasaray Üniversitesi MAT231** kapsamında hazırladığım *Application de l'Algorithme de Gale-Shapley à l'Affectation Scolaire et à l'Admission Universitaire* başlıklı çalışmamın temel kavramsal çerçevesini özetlemektedir.

## 1. Problem Kurulumu: İki Taraf, Tercih Listeleri ve Kararlılık

Modeli en yalın haliyle ele alalım: Ayrık iki kümemiz olsun; örneğin bir yanda adaylar/öğrenciler kümesi A, diğer yanda kurumlar/programlar kümesi K ve her k kurumunun belirli bir kontenjanı q_k (en az 1) bulunsun.

- A kümesindeki her a adayı, tercih edebileceği kurumları kendi içinde katı (berabere kalınmayan) bir sıraya dizer.
- K kümesindeki her k kurumu, başvurabilecek adayları kendi içinde katı bir öncelik sırasına dizer.

Bir eşleşmenin **kararlı (*stable*)** sayılması için şu iki koşulun sağlanması gerekir:

1. **Bireysel rasyonellik:** Hiçbir taraf, kabul edilemez bulduğu bir eşleşmeye zorlanmamalıdır.
2. **Engelleyici çift (*blocking pair*) olmaması:** Mevcut eşleşmesinde yer alan a adayı ve k kurumu, şu anki eşleşmelerine kıyasla **birbirini** kesin olarak tercih ediyorsa (a, k) bir engelleyici çift oluşturur. Böyle bir çift varsa sistem kararlı değildir; ikili resmi mekanizmanın dışında anlaşarak eşleşmeyi bozabilir.

## 2. Algoritma Nasıl Çalışır? (Ertelemeli Kabul)

Gale-Shapley algoritmasının en kritik özelliği, kararları **erken ve kesin** vermek yerine "geçici tutma ve erteleme" mantığıyla ilerlemesidir. Aday-önerili versiyonu adım adım şöyledir:

1. **Teklif Aşaması:** Henüz bir yere yerleştirilmemiş (veya mevcut geçici yerinden reddedilmiş) her aday, kendi tercih listesinde henüz teklif götürmediği **en yüksek sıradaki** kuruma başvurur.
2. **Geçici Değerlendirme:** Her kurum, o turda gelen yeni başvurular ile elinde halihazırda **geçici olarak tuttuğu** adayları kendi öncelik listesine göre değerlendirir.
3. **Ertelemeli Kabul ve Red:** Kurum, kendi kontenjanını (q_k) aşmayacak şekilde en iyi adayları **geçici olarak** yanında tutar; geri kalanları reddeder. Reddedilen adaylar bir sonraki adımda listedeki bir sonraki seçeneğe yönelir.
4. **Durma Koşulu:** Hiçbir yeni teklif yapılmadığında veya reddedilen adayların listesi tükendiğinde algoritma sonlanır ve geçici eşleşmeler kesinleşir.

Bu mekanizmanın neden her zaman sonlandığını görmek kolaydır: Her adımda en az bir aday, tercih listesinde daha önce denemediği bir kuruma başvurur. Aday ve kurum kümeleri sonlu olduğundan yapılabilecek toplam teklif sayısı da sonlu bir üst sınırla kısıtlıdır.

## 3. Temel Teoremler: Neden Bu Kadar Güçlü?

Gale-Shapley algoritmasını yalnızca pratik bir yordam olmaktan çıkarıp eşleşme teorisinin merkezine taşıyan üç temel sonuç vardır:

- **Kararlılık Garantisi:** Algoritma bittiğinde oluşan eşleşme **her zaman kararlıdır**. Diyelim ki a adayı, kendi eşleştiği kurumdan daha üstte yer alan bir k kurumunu istiyor. Algoritmanın işleyişi gereği a adayı, k kurumuna daha önce mutlaka başvurmuş olmalıdır. Eğer k kurumu a adayını reddettiyse veya sonradan bıraktıysa, bunun tek nedeni k kurumunun a adayından daha yüksek öncelikli adaylarla kontenjanını doldurmuş olmasıdır. Dolayısıyla k kurumu, a adayını kendi mevcut adaylarına tercih etmez; (a, k) bir engelleyici çift olamaz.
- **Taraf Asimetrisi (Öneren vs. Kabul Eden):** Adayların teklif götürdüğü versiyonda algoritma, kararlı eşleşmeler kümesi içinde adaylar açısından **en iyi (optimal)**, kurumlar açısından ise **en kötü** kararlı eşleşmeyi üretir. Roller tersine çevrildiğinde (kurumların teklif/kabul inisiyatifi aldığı durumda) tablo tam tersine döner.
- **Stratejik Davranış Sınırları:** Aday-önerili modelde adayların tercih sıralarını gizleyip manipüle etmesi genel olarak karşılıksız kalma veya daha kötü sonuç alma riski taşır; dürüst sıralama teorik olarak güçlü bir temel oluşturur.

## 4. Okul ve Üniversite Yerleştirmede Karşılaşılan İnce Noktalar

Gale-Shapley algoritması okul ve üniversite yerleştirme sistemlerine uyarlandığında kuramsal model ile sahadaki kurallar arasında dikkatli bir köprü kurmak gerekir:

- **Kontenjan ve Öncelik Kuralları:** Üniversite veya lise yerleştirmelerinde "tercih" kavramı çoğu zaman öğrenci tarafında tanımlanırken, kurum tarafındaki sıralama merkezi sınav puanı, yerleştirme kriterleri veya özel kurallarla belirlenir.
- **Bağlantı Kırma (*Tie-Breaking*):** Algoritma katı sıralamalar varsayar. Gerçek veride aynı puana veya aynı öncelik statüsüne sahip adaylar bulunduğunda, eşitliklerin nasıl bozulduğu (*tie-breaking*) hem adaleti hem de eşleşmenin yapısını etkiler.
- **Kısıtlar ve Gerçek Dünya Sapmaları:** Kontenjanların sabit olmadığı, özel kontenjanların bulunduğu veya merkezi sistem dışında kalan tercihlerin işin içine girdiği senaryolarda kararlılık ve optimalite özelliklerinin hangilerinin korunduğunu ayrıca analiz etmek gerekir.

## 5. Kapanış Notu

Gale-Shapley algoritması, kombinatoryal yapı ile iktisadi ve sosyal mekanizma tasarımının kesiştiği en zarif modellerden biridir. Basit bir "teklif et, geçici tut, gerekirse bırak" kuralının küresel ölçekte çakışmasız ve kararlı bir dengeye ulaşabilmesi, algoritmik düşünmenin en ikna edici örneklerinden birini sunar.

---

**Bağlantılar:** [PDF'i Aç](/Gale-Shapley_Algoritması.pdf)
