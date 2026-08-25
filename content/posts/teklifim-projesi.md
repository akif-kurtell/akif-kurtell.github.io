---
title: "Django ile İlk Web Geliştirme Deneyimi: Teklifim Projesi"
date: 2026-08-26
draft: false
tags: ["Python", "Django", "Web Geliştirme", "Deneyim", "Projeler"]
summary: "Lisans 1. sınıfta yapay zeka araçlarından faydalanarak geliştirdiğimiz, düzenli mentorluk görüşmeleriyle kod hakimiyeti kazandığımız ilk web platformu projemin detayları."
---

Lisans 1. sınıfta aldığımız *Bilgisayar Programlama II* dersi kapsamında ekip arkadaşlarımla birlikte hayata geçirdiğimiz **Teklifim**, ilk kapsamlı web sitesi geliştirme deneyimim oldu.

Proje, temel olarak bir **Tersine Pazar Yeri (Reverse Marketplace)** modeline dayanıyor. Klasik e-ticaret sitelerindeki satıcının ürün listelediği yapının aksine; bu modelde kullanıcılar bir talep (ilan) açıyor, hizmet veya ürün sağlayıcılar ise bu talebe özel teklifler sunuyor.

---

### Geliştirme Metodolojisi ve Değerlendirme Süreci

Geliştirme aşamasında modern araçlardan ve yapay zeka destekli kodlama yöntemlerinden sıkça faydalandık. Ancak sürecin en öğretici kısmı, bu kodları projeye dahil ederken taşıdığımız sorumluluktu. İki haftada bir gerçekleşen mentorluk görüşmelerinde, projede yer alan her kod bloğunun işlevini ve mantığını detaylı şekilde açıklayabilmemiz gerekiyordu.

Ders kapsamında iki yönlü bir değerlendirme kriteri bulunuyordu:
* **Grup Performansı:** Taahhüt edilen modüllerin ve arayüz akışının hatasız bir şekilde çalışması.
* **Bireysel Performans:** Rastgele seçilen kod blokları üzerinden mantıksal kavrayışın ve teorik altyapının sorgulanması.

Başlangıçta terminal hatalarını çözmek, modüller arasındaki bağımlılıkları yönetmek ve Django'nun mimarisine adapte olmak zorlayıcıydı. Bireysel değerlendirmelerde ise özellikle üzerinde daha az durduğumuz detayların sorulması, sonraki haftalarda kod tabanına daha kapsamlı ve titiz yaklaşmamızı sağladı. Düzenli geri bildirimler sayesinde hataları daha sistematik ayıklamayı ve arka plandaki çalışma mantığını kavramayı başardık.

---

### İlk Geliştirme Deneyimi ve Kazanımlar

Bu süreç, bir web uygulamasının sıfırdan nasıl ayağa kaldırıldığını görmemi sağladı. Hataları analiz edip düzeltmenin, yapılan değişikliklerin anında tarayıcıya yansımasının ve veritabanı yönetiminin pratik tarafı oldukça eğiticiydi.

Özellikle Django'nun yerleşik **Admin Paneli** sayesinde test kullanıcıları tanımlamak, yetkilendirmeleri yönetmek ve veritabanı tabloları üzerindeki ilişkileri doğrudan manipüle edebilmek, backend mimarisinin işleyişini somutlaştırmama yardımcı oldu.

---

### Teknik Yapı

* **Backend:** Python, Django (MVT mimarisi ve yerleşik kimlik doğrulama sistemi)
* **Frontend:** HTML, CSS, JavaScript
* **Veritabanı:** SQLite (İlanlar, kullanıcılar ve teklifler arasındaki ilişkisel veri modelleri)

Veritabanı düzeyinde bir ilana birden fazla teklif atanabilmesi (`ForeignKey`), teklif durumlarının (`Beklemede`, `Kabul Edildi`, `Reddedildi`) yönetimi ve kabul edilen teklif doğrultusunda diğer kayıtların durumunun güncellenmesi gibi iş mantıkları kurgulandı.

---

### Sonuç

Teklifim projesi; yalnızca çalışan bir kod üretmenin değil, kullanılan araçların mantığına hakim olmanın, metodolojik hata ayıklamanın ve bir projeyi baştan sona yönetmenin önemini gösteren değerli bir tecrübe oldu.

Projenin kaynak kodlarını incelemek isterseniz GitHub reposuna göz atabilirsiniz:

👉 **[Teklifim GitHub Reposu](https://github.com/akif-kurtell/teklifim12)**