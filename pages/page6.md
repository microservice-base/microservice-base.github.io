---
layout: default
---
# Shop Projesi - Java Projesini Docker Konteyner Haline Getirmek


## docker image oluşturmak

Gradle yüklü olmalıdır.
```
$ git clone https://github.com/microservice-base/shop.git

$ cd shop 

$ docker build --no-cache  -t image-shop  -f container/docker/Dockerfile .

$ docker run -d --name project-shop -p 8001:8001 image-shop:latest .       #check can able to create container

$ docker tag image-shop:latest keramiozsoy/image-shop:latest

$ docker push keramiozsoy/image-shop

```

_yay_
[back](https://microservice-base.github.io/)
