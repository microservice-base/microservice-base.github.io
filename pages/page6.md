---
layout: default
---
# Shop Projesi - Java Projesini Docker Konteyner Haline Getirmek


## docker image oluşturmak

Gradle yüklü olmalıdır.
```
git clone https://github.com/microservice-base/shop.git


cd shop/shop && ./gradlew build --refresh-dependencies && cp build/libs/*.jar ./container/docker/app.jar && cd container/docker/ && docker build -t image-shop:v1 . && docker run -d --name project-shop -p 8001:8001 image-shop:v1

docker ps

docker exec -it shopproject /bin/sh

```

_yay_
[back](https://microservice-base.github.io/)
