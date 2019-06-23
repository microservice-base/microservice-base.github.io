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
   - prometheus: {
      href: "http://localhost:8001/shop/actuator/prometheus",
      templated: false
    }
  }
}
```

Shop projesine prometheus.yml adıyla bir dosya ekledim. Bu dosya prometheus bizden bilgi çekerken ihtiyacı olan formattır.

Örnek kullanımı burada mevcuttur.

> https://prometheus.io/docs/prometheus/latest/configuration/configuration/


Aşağıdaki gösterim ile prometheus üzerinden bakıldığında isminin ne olacağı ve hangi url üzerinden bilgilere ulaşacağı,
ne kadar sürede Shop projesine ait son bilgilerin tekrar çekileceği mevcuttur.

**prometheus.yml**

```
- job_name: 'spring-actuator'
    metrics_path: '/shop/actuator/prometheus'
    scrape_interval: 5s
    static_configs:
    - targets: ['CONTAINER_IP:8001']
```

Testtimize geçelim.

Prometheus un docker ile konteyneleştirilmiş hali ile çalışabiliriz.





