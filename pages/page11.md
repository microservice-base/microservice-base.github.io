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

Buradaki metriklerden yardım alarak da grafana üzerinde güzel grafikler halinde projemize ait bilgileri göreceğiz.

```
docker run -d --name=grafana -p 3000:3000 grafana/grafana

open http://localhost:3000

admin admin


add datasource 

prometheus

name : project-shop-prometheus
url  : http://localhost:9090  -- prometheus url
access : browser
save & test

new dashboard

query



