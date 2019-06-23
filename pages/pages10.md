---
layout: default
---
# Shop Projesi - Java Projesine Prometheus Entegre edelim.

> https://prometheus.io

Shop projesinin Actuator modülü ekleyerek bazı bilgilere ulaşımı sağlamıştık.

Shop projesinin Prometheus tarafından dinlenilecek url bilgisini açmak için değişiklikleri uygulayalım.

Shop projesi gradle projesi olduğu için bağımlıkları ekleyelim.

**build.gradle**

```groovy
dependencies {
	implementation("io.micrometer:micrometer-registry-prometheus")
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

