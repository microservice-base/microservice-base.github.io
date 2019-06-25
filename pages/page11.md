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

```

Kendimize ait dashboard ekranları tasarlayabiliriz. Prometheus tarafında okunabilen şu metrik isimlerini
kullanarak bir ekran tasarlayabiliriz.

```
new dashboard

query
process_cpu_usage

query
jvm_memory_used_bytes
```

**Grafana** için daha önceden oluşturulup kurum veya kişilerce yayınlanan grafiklerin bir marketi mevcuttur.

Shop projesi, **Prometheus** entegrasyonu yapılırken alt katmanda **micrometer.io** kullandığından bahsetmiştik.

```
- https://micrometer.io/docs/registry/prometheus
```

**Grafana Dashboard** bölümündeki grafiği kullabiliriz.

```
- https://grafana.com/dashboards/4701
veya
- https://grafana.com/dashboards/6756
```

Grafana yı açıyoruz. Import bölümünden **6756** yazarak ve **project-shop-prometheus** seçip kapatıyoruz.

![Grafana](/images/project-shop-grafana.png)


