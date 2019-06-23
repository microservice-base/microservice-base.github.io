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

Prometheus un docker ile konteynerleştirilmiş hali ile çalışabiliriz.

```
docker pull prom/prometheus

docker run -d --name=prometheus -p 9090:9090 prom/prometheus --config.file=/etc/prometheus/prometheus.yml

open browser http://localhost:9090
             http://localhost:9090/targets
```

Prometheus arayüzüne ulaştık.

Prometheus un, Shop projemize özel hazırladığımız prometheus.yml dosyasını 
docker tarafından sağanan docker volume üzerinden çözebiliriz.

```
docker volume create volumeprometheus
```

Shop projemizi çalıştırırken bu **volume**  parametre olarak  geçildiğinde dosya farklı konteynerler tarafından okunabilicek.

Shop projemizi çalıştıralım.

```
docker run -d --name project-shop -v volumeprometheus:/prometheusfiles -p 8001:8001 image-shop:latest

```

prometheus.yml içinde **CONTAINER_IP** doldurmalıyız. Konteynerler dinamik olarak ip aldığından bu durumu
bir kaç küçük adım ile çözelim.

```
docker exec -it project-shop /bin/sh

container_ip=$(awk 'END{print $1}' /etc/hosts)

sed -i "s/CONTAINER_IP/$container_ip/g" prometheusfiles/prometheus.yml

cat prometheusfiles/prometheus.yml

exit
```

Eğer Shop projesini konteyner ile çalıştırmayıp host makine üzerinden doğrudan çalıştırmış olsaydık **CONTAINER_IP** host ip bilgisini yazmlıydık.
