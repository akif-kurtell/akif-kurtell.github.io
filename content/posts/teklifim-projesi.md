---
title: "Django ile İlk Web Sitem: Teklifim Projesi ve Yaşadıklarımız"
date: 2026-08-26
draft: false
tags: ["Python", "Django", "Web Geliştirme", "Deneyim", "Projeler"]
summary: "Lisans 1. sınıfta yapay zeka ile kod yazıp iki haftada bir hocamızın karşısında ter döktüğümüz, hatalarla boğuşup sonunda çalışan bir tersine pazar yeri çıkardığımız ilk web geliştirme serüvenim."
---

Üniversitede lisans 1. sınıfta aldığımız *Bilgisayar Programlama II* dersi kapsamında ekip arkadaşlarımla birlikte hayata geçirdiğimiz **Teklifim**, benim ilk web sitesi geliştirme deneyimimdi.

Projenin temel mantığı **Tersine Pazar Yeri (Reverse Marketplace)** üzerine kuruluydu. Yani klasik e-ticaret sitelerindeki gibi satıcı ürün koyup alıcı seçmiyor; ihtiyacı olan kullanıcı bir talep (ilan) açıyor, hizmet veya ürün sağlayıcılar da bu ilana özel teklifler sunuyordu. Fikir çok güzeldi ama işin mutfağına girince süreç bizim için tam bir maceraya dönüştü.

---

### Yapay Zeka ile Kod Yazıp Bu Kodlardan Sorumlu Olmak

Açık konuşmak gerekirse geliştirme sürecinde epey zorlandık. Kodların büyük bir kısmını yapay zekaya yazdırıyorduk ama işin asıl zor kısmı burada başlıyordu: İki haftada bir mentör hocamızla düzenli görüşmelerimiz vardı ve yapay zekaya yazdırdığımız her satır kodun ne işe yaradığını ezbere değil, mantığıyla bilmekten sorumluyduk.

Değerlendirme sistemi iki aşamalıydı:
1. **Grup Puanlaması:** O hafta taahhüt ettiğimiz özelliklerin ekranda hatasız ve tıkır tıkır çalışması gerekiyordu.
2. **Bireysel Puanlama:** Hocamız projeden rastgele bir kod satırını açıp *"Bu burada ne yapıyor, mantığı ne?"* diye soruyordu.

İlk etapta bu çalışma temposuna alışmak bizim için çok zor oldu. Terminalde sürekli kırmızı hata mesajlarıyla karşılaşıyor, bir yeri düzeltirken başka bir yeri bozuyorduk. Fakat zaman geçtikçe sistemi, Django'nun mantığını ve veritabanı ilişkilerini yavaş yavaş kavramaya başladık.

Tabii bireysel puanlama kısmı her zaman istediğimiz gibi gitmiyordu. Murphy Kanunları devredeydi: Projede nereye çok çalışıp hazırlandıysak hocamız orayı hiç sormuyor; *"Burayı sormaz herhalde"* diye üstünkörü geçtiğimiz neredeyse her satırı nokta atışı bulup soruyordu! Her görüşmenin sonunda da hocamız bize esprili bir şekilde her zamankinden daha çok çalışmamız gerektiği yönünde telkinlerde bulunuyordu.

---

### Kodları Kurcalamak ve İlk Başarı Hissi

Tüm bu stresin ve zorlukların yanında, bir şeyler üretmenin keyfini ilk kez bu kadar net hissettim. Kodları kurcalamak, saatlerce uğraştıran bir hatayı çözüp tarayıcıyı yenilediğinde anında düzeldiğini görmek inanılmaz tatmin ediciydi.

Özellikle Django'nun yerleşik **Admin Paneli** ile oynamak favori aktivitem haline gelmişti. Kendi elimle test kullanıcıları açıyor, sonra admin panelinden o kullanıcıları silip rolleriyle oynuyor, veritabanına doğrudan müdahale edebilmenin rahatlığını yaşıyordum.

---

### Sistemde Neler Kullandık?

* **Backend:** Python, Django (MVT yapısı ve yerleşik auth mekanizması)
* **Frontend:** HTML, CSS, JavaScript
* **Veritabanı:** SQLite (İlanlar, kullanıcılar ve teklifler arasındaki ilişkisel tablolar)

Veritabanı tarafında bir ilana birden fazla teklifin gelebilmesi (`ForeignKey`), teklifin durumunun (`Beklemede`, `Kabul Edildi`, `Reddedildi`) güncellenmesi ve kabul edilen teklif dışındakilerin elenmesi gibi iş mantıklarını kurguladık.

---

### Sonuç

Teklifim projesi, kod yazmanın sadece klavyeye basmaktan ibaret olmadığını; asıl meselenin mantığı kavramak, sistemli hata ayıklamak ve ne yaptığını bilmek olduğunu bana öğreten ilk ve en unutulmaz tecrübem oldu.

Projenin kaynak kodlarına ve neler yaptığımıza göz atmak isterseniz GitHub reposunu aşağıya bırakıyorum:

👉 **[Teklifim GitHub Reposu](https://github.com/akif-kurtell/teklifim12)**