---
layout: default
---
# Shop Projesi - h2 db kullanilmasi

> https://github.com/microservice-base/shop

**build.gradle**

```groovy
dependencies{

runtimeOnly('com.h2database:h2')

}
```

**application.properties**

```
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=sa
spring.datasource.driver-class-name=org.h2.Driver
```
