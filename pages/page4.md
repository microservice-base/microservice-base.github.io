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


## DAO Katmanı 

Veritabanına ulaşıp  kayıt ekleme, kayıt silme, kayıt bulma gibi işlemlerin yapılmasını sağlayan katmandır.


- https://github.com/microservice-base/shop/blob/master/shop/src/test/java/test/com/shop/product/dao/ProductDAOTest.java

Sınıfımızın başında veritabanı işlemlerini yapabilmemiz için Spring Framework anotasyonu olan **@DataJpaTest** mevcuttur.

Bu test dosyasını çalıştırdığımızda ;

Spring Framework anotasyonu olan **@TestEntityManager**, ile Java dilinin Java Persistence Api sini kullanarak 
kayıt işlemleri basitçe gerçekleştirdik. DAO yu test etmek için entitiymanager ile sahte kayıtlar(mock) oluşturmuş olduk.

Sonraki adımlarda kendi DAO sınıfımızın metotları ile bu işlemlerin yapılabilirliğini kontrol ettik.

DAO sınıfımıza ait metotların sonuçlarını kontrol ederek testimizi çalıştırmış oluyoruz


## Servis Katmanı

DAO katmanı işlemlerini kullanabilmek için çağırdığımızı metotların bulunduğu katmandır.

- https://github.com/microservice-base/shop/blob/master/shop/src/test/java/test/com/shop/product/service/impl/ProductBusinessServiceImplTest.java

Sınıfımızın başında Spring Framework anotasyonu olan **@SpringBootTest** mevcuttur.

Bu test dosyası çalıştırıldığında ;

DAO sınıfımızdaki metotlar bizim sahte(mock) objelerimiz olacak şekilde kullanıyoruz.

Servis sınıfımızın metotlarını çağırıp test ediyoruz.

Servis sınıfımızın metotlarının sonçlarını beklediğimiz sonuçlar ile karşılaştırıp testimizi çalıştırmış oluyoruz.

## Api Katmanı

Projeye gelen ve giden isteklere karşılık sağlayacak metotların olduğu sınıflardır.



_yay_
[back](https://microservice-base.github.io/)

