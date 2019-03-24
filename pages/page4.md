---
layout: default
---
# Shop Projesi

- https://github.com/microservice-base/shop


Ürün kayıt bilgilerine ulaşabileceğimiz projedir.

Kullanılan Teknolojiler
- Java 
- Spring Boot (Spring Framework)
- Gradle
- H2 in memory db
- Mockito


Yazdığımız test sınıflarını inceleyelim.

Uygulamamızın katmanları bazı katmanları mevcuttur.
- Api Katmanı
- Servis Katmanı
- DAO katmanı


DAO Katmanı 

Veritabanına ulaşıp  kayıt ekleme, kayıt silme, kayıt bulma gibi işlemlerin yapılmasını sağlayan katmandır.


- https://github.com/microservice-base/shop/blob/master/shop/src/test/java/test/com/shop/product/dao/ProductDAOTest.java

Bu test dosyasını çalıştırdığımız anda;

Spring Framework anotasyonu olan TestEntityManager, ile Java dilinin Java Persistence Api sini kullanarak 
kayıt işlemleri basitçe gerçekleştirdik. DAO yu test etmek için entitiymanager ile sahte kayıtlar(mock) oluşturmuş olduk.

Sonraki adımlarda kendi DAO sınıfımızın metotları ile bu işlemlerin yapılabilirliğini kontrol ettik.

DAO sınıfımıza ait metotların sonuçlarını kontrol ederek testimizi çalıştırmış olduk.

_yay_
[back](https://microservice-base.github.io/)

