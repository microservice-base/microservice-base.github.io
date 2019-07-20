---
layout: default
---
# Basket Projesi - Go  Projesini Docker Konteyner Haline Getirmek


## docker image oluşturmak


```
$ git clone https://github.com/microservice-base/basket.git

$ cd basket

$ docker build --no-cache -t image-basket -f container/docker/Dockerfile .

$ docker run -d --name app-basket -p 8002:8002 image-basket


$ docker tag image-basket:latest keramiozsoy/image-basket:latest

$ docker push keramiozsoy/image-basket

```

_yay_
[back](https://microservice-base.github.io/)


