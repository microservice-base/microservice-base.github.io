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

Spring Framework anotasyonu olan TestEntityManager, ile Java dilinin Java Persistence Api sini kullanarak 
kayıt işlemleri basitçe gerçekleştirdik.

Sonraki adımlarda kendi DAO sınıfımız ile bu işlemlerin yapılabilirliğini kontrol ettik.

_yay_
[back](https://microservice-base.github.io/)

