---
layout: default
---
# Shop Projesi - Java Projesine Grafana Entegre edelim.

> https://grafana.com

``
	buraya grafana ile ilgili biraz bilgi ekleyeceğim.
``

Shop projesinin **Spring Actuator** modülü ekleyerek bazı bilgilere ulaşımı sağlamıştık.

Prometheus ile Shop projesini entegre etmiş bilgileri bir url bilgisinden prometheus tarafından okunacak şekilde açmıştık.

```
- http://localhost:8001/shop/actuator/prometheus
```

Prometheus kendi arayüzünden bu bilgileri kolay bir arayüzde ulaşabiliyoruz.
```
- http://localhost:9090/
```

Buradaki metriklerden 

