---
layout: default
---
# Shop Projesi - Java Projesine Prometheus Entegre edelim.

> https://prometheus.io

Shop projesinin Actuator modülü ekleyerek bazı bilgilere ulaşımı sağlamıştık.


``
	buraya prometheus ile ilgili biraz bilgi ekleyeceğim.
``

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

> https://prometheus.io/docs/introduction/first_steps/#using-the-expression-browser
> https://prometheus.io/docs/prometheus/latest/configuration/configuration/


Aşağıdaki gösterim ile prometheus üzerinden bakıldığında isminin ne olacağı ve hangi url üzerinden bilgilere ulaşacağı,
ne kadar sürede Shop projesine ait son bilgilerin tekrar çekileceği mevcuttur.

**prometheus.yml**

```
- job_name: 'project-shop-prometheus'
    metrics_path: '/shop/actuator/prometheus'
    scrape_interval: 5s
    static_configs:
    - targets: ['CONTAINER_IP:8001']
```

Testtimize geçelim.

Prometheus un docker ile konteynerleştirilmiş hali ile çalışabiliriz.

```
docker pull prom/prometheus

docker run -d --name=prometheus-test -p 9090:9090 prom/prometheus --config.file=/etc/prometheus/prometheus.yml

open browser http://localhost:9090
             http://localhost:9090/targets
	     
docker stop prometheus-test
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
docker run -d --name project-shop -v volumeprometheus:/prometheusfiles -p 8001:8001 keramiozsoy/image-shop:latest

```

prometheus.yml içinde **CONTAINER_IP** doldurmalıyız. Konteynerler dinamik olarak ip aldığından bu durumu
bir kaç küçük adım ile çözelim.

```
docker exec -it project-shop /bin/sh

container_ip=$(awk 'END{print $1}' /etc/hosts)

echo $container_ip

sed -i "s/CONTAINER_IP/$container_ip/g" prometheusfiles/prometheus.yml

cat prometheusfiles/prometheus.yml

exit
```

Eğer Shop projesini konteyner ile çalıştırmayıp host makine üzerinden doğrudan çalıştırmış olsaydık **CONTAINER_IP** host ip bilgisini yazmalıydık.

Prometheus u oluşturduğumuz volume verisini okuyarak yeniden çalıştıralım.

```
docker run -d --name prometheus -v volumeprometheus:/prometheusfiles -p 9090:9090 prom/prometheus --config.file=/prometheusfiles/prometheus.yml

open browser http://localhost:9090/targets
```

Şimdi prometheus tarafındaki metrikleri inceleyelim.

http://localhost:9090/graph

Açılan sayfada **execute** butonu yanından ismi **up** olan metrik seçip execute butonuna basalım.
**graph** bölümüne geçelim.

**spring-actuator-project-shop** isimli metriği inceleyeceğiz. Projemizin hangi anlarda çalışıp çalışmadığını görelim.
20 sn aralıklar ile aşağıdaki komutları çalıştıralım.
```
docker restart project-shop
docker restart project-shop
docker restart project-shop
```

Şimdi tekrar 
http://localhost:9090/graph bölümünde projemizin çalıştığı ve çalışmadığı anları görebiliriz.

Bu tarz bir çok metrik bilgisini inceleyebiliriz.

Bunların dışında prometheus bir service discovery özelliği de görmektedir. Bağlantı kurulabilen uygulamaları görebilmek için
kullanabiliriz.

```
- http://localhost:9090/service-discovery
```

Daha sonra bu grafikleri daha güzel görebilmek için https://grafana.com dan yardım alacağız.






