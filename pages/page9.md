---
layout: default
---
# Shop Projesi - Java Projesine Spring Boot Actuator Modülü Entegrasyonu

Shop projesinin  sağlık durumunu yani çalışıp çalışmadığını görebilmek, anlık metriklerine ulaşabilmek ve sürekli denetleyebilmek için HTTP üzerinden bu bilgileri dışarı açmak istiyoruz ki bu bilgilere ulaşabilelim.

Spring Boot ile yazılmış projemize Actuator modülü ekleyerek isteklerimiz gerçekleştirebiliriz.


> https://github.com/spring-projects/spring-boot/tree/master/spring-boot-project/spring-boot-actuator

Spring Boot Actuator modülü temelinde http://micrometer.io kullanmaktadır. Projenin tüm metrik bilgilerin toplayop Spring Boot Actuator tarafından sunulmasını sağlayan Micrometer, doğrudan projeye eklenip bir kaç kod eklemesinden sonra da çalıştırılabilir. Biz bunlarla uğraşmadan spring boot actutor bize sağladığı yapıyı kolaylıkla kullanıyoruz.

Projemiz **gradle** projesi olduğu için bu projeyi bir kütüphane olarak projemize eklemek için yapacağımız değişiklikler.


**build.gradle**

```groovy
dependencies {
	implementation("org.springframework.boot:spring-boot-starter-actuator")
}
```
Projemizi çalıştırdığımızda şu çıktıyı alıyoruz.

- http://localhost:8001/shop/actuator


```json
{
  _links: {
    self: {
      href: "http://localhost:8001/shop/actuator",
      templated: false
    },
    health: {
      href: "http://localhost:8001/shop/actuator/health",
      templated: false
    },
    info: {
      href: "http://localhost:8001/shop/actuator/info",
      templated: false
    }
  }
}

```

Projemiz **application.properties** dosyasına aşağıdaki eklemeyi servis ile aynı isimde olacak şekilde info. ile başlayarak yaparsak,  /info üzerinden bilgileri paylaşabiliriz.

**application.properties**
```properties
info.app.name=@project.name@
info.app.description=@project.description@
info.app.version=@project.version@
info.app.encoding=@project.build.sourceEncoding@
info.app.java.version=@java.version@
```

Projemiz **application.properties** dosyasına aşağıdaki eklemeyi yaparsak çok daha fazla ulaşılabilecek servisi gözlemleyebiliriz. (/metrics için bu ekleme yapılmalıdır.)

**application.properties**
```properties
management.endpoints.web.exposure.include=*
``` 


Bunların dışında eğer projemizi bir HTTP isteği yardımı ile kapatmak istersek şu şekilde yapabiliriz.
Ben bu projeye eklemedim. Eğer eklerseniz Spring Security yardımı ile hangi kullanıcı rollerine sahip kullanıcılar örneğin admin bu actuator ile açılmış olan servislere istek atıp kullanabileceğini belirleyebilirsiniz.

HTTP servisilerin hangi bilgileri vereceğini, örneğin projenin bulunduğu disk üzerindeki bilgileri paylaşmak için Spring tarafından sağlanan DiskSpaceHealthIndicator mevcuttur. Örnekler çoğaltılabilir hatta custom sınıf ve metotlar eklenbilmektedir.
