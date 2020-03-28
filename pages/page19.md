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

#### H2 Web Dashboard 
spring.h2.console.enabled=true
spring.h2.console.path=/h2

#### DB
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=sa
spring.datasource.driver-class-name=org.h2.Driver

```


Run **shop application** 

```
open localhost:8001/shop/h2
```

