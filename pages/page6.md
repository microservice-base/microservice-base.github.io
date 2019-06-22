---
layout: default
---
# Shop Projesi - Java Projesini Docker Konteyner Haline Getirmek


## docker image oluşturmak

Gradle yüklü olmalıdır.
```
git clone https://github.com/microservice-base/shop.git


cd shop/shop && ./gradlew build --refresh-dependencies && cd .. &&  cp shop/build/libs/*.jar container/docker/app.jar && cd container/docker/ && docker build -t image-shop:latest . && docker run -d --name project-shop -p 8001:8001 image-shop:latest

docker tag image-shop:latest keramiozsoy/image-shop:latest

docker push keramiozsoy/image-shop

```

_yay_
[back](https://microservice-base.github.io/)
