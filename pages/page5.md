---
layout: default
---
# Shop - Java Projesine Swagger Entegrasyonu

Shop projesine ait dışarı açılan servisleri güzel bir arayüz ile dışarı açmak istiyoruz.

- https://swagger.io/
- http://springfox.github.io/springfox/

Shop projemiz bir java projesi olduğu için **springfox** projesi bizim işimizi görüyor.

Projemiz gradle projesi olduğu için bu projeyi bir kütüphane olarak projemize eklemek için yapacağımız değişiklikler.

	build.gradle

```groovy
dependencies
	implementation("io.springfox:springfox-swagger2:2.9.2")
	implementation("io.springfox:springfox-swagger-ui:2.9.2") // only for swagger-ui.html
}
```


- https://github.com/microservice-base/shop/blob/master/shop/src/main/java/com/shop/config/SwaggerConfig.java

Buradaki sınıf ile web servislerimizin bulunduğu sınıfı ( ProductApi ) belirtiyoruz.

Projemizi çalıştırdığımızda 

- http://localhost:8001/shop/swagger-ui.html

- /swagger-resources
- /swagger-resources/configuration/security
- /swagger-resources/configuration/ui
